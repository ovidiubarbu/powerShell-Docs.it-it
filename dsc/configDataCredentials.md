---
title: Opzioni delle credenziali nei dati di configurazione
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: a750fb208e73ce2ebffb2fa86a55c825169d8ad8

---

# Opzioni delle credenziali nei dati di configurazione
>Si applica a: Windows PowerShell 5.0

## Password di testo normale e utenti di dominio

Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.
Inoltre, DSC genera un avviso quando si usano credenziali di dominio.
Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

## Gestione delle credenziali in DSC

Le risorse di configurazione DSC vengono eseguite come `Local System` per impostazione predefinita.
Tuttavia, per alcune risorse è necessaria una credenziale, ad esempio quando la risorsa `Package` deve installare software nell'ambito di un account utente specifico.

Le risorse delle versioni precedenti usano un nome di proprietà `Credential` hardcoded per gestire questo caso.
In WMF 5.0 è stata aggiunta una proprietà `PsDscRunAsCredential` automatica per tutte le risorse. Per informazioni sull'uso di `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).
Le risorse più recenti e quelle personalizzate possono usare questa proprietà automatica invece di creare una proprietà personalizzata per le credenziali.

*Si noti che la progettazione di alcune risorse prevede l'uso di più credenziali per un motivo specifico e tali risorse hanno proprietà delle credenziali proprie.*

Per trovare le proprietà delle credenziali disponibili in una risorsa, usare `Get-DscResource -Name ResourceName -Syntax` o Intellisense in ISE (`CTRL+SPACE`).

```PowerShell
PS C:\> Get-DscResource -Name Group -Syntax
Group [String] #ResourceName
{
    GroupName = [string]
    [Credential = [PSCredential]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Members = [string[]]]
    [MembersToExclude = [string[]]]
    [MembersToInclude = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
}
```

Questo esempio usa una risorsa [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.
La risorsa può creare gruppi locali e aggiungere o rimuovere membri.
Accetta sia la proprietà `Credential` sia la proprietà `PsDscRunAsCredential` automatica.
Tuttavia, la risorsa usa solo la proprietà `Credential`.
Per altre informazioni su `PsDscRunAsCredential`, vedere [Note sulla versione di WMF](https://msdn.microsoft.com/en-us/powershell/wmf/dsc_runas).

## Esempio: proprietà Credential della risorsa Group

Poiché DSC viene eseguito in `Local System`, ha già le autorizzazioni necessarie per modificare gruppi e utenti locali.
Se il membro aggiunto è un account locale, non è necessaria alcuna credenziale.
Se la risorsa `Group` aggiunge un account di dominio al gruppo locale, è necessaria una credenziale.

Le query anonime in Active Directory non sono consentite.
La proprietà `Credential` della risorsa `Group` corrisponde all'account di dominio usato per eseguire query in Active Directory.
Per quasi tutti gli scopi può trattarsi di un account utente generico, perché per impostazione predefinita gli utenti possono *leggere* la maggior parte degli oggetti in Active Directory.

## Configurazione di esempio

Il codice di esempio seguente usa DSC per immettere un utente di dominio in un gruppo locale:

```PowerShell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred
```

Questo codice genera un messaggio di errore e uno di avviso:

```
ConvertTo-MOFInstance : System.InvalidOperationException error processing
property 'Credential' OF TYPE 'Group': Converting and storing encrypted
passwords as plain text is not recommended. For more information on securing
credentials in MOF file, please refer to MSDN blog:
http://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:297 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance

WARNING: It is not recommended to use domain credential for node 'localhost'.
In order to suppress the warning, you can add a property named
'PSDscAllowDomainUser' with a value of $true to your DSC configuration data
for node 'localhost'.
```

Questo esempio include due problemi:
1.  Un errore indica che le password di testo semplice non sono consigliate
2.  Un avviso sconsiglia l'uso di una credenziale di dominio

## PsDscAllowPlainTextPassword

Il primo messaggio di errore contiene un URL con la documentazione.
Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e un certificato.
Per altre informazioni sui certificati e su DSC, [leggere questo post](http://aka.ms/certs4dsc).

Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:

```PowerShell
Configuration DomainCredentialExample
{
    param
    (
        [PSCredential] $DomainCredential
    )
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $DomainCredential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowPlainTextPassword = $true
        }
    )
}

$cred = Get-Credential -UserName contoso\genericuser -Message "Password please"
DomainCredentialExample -DomainCredential $cred -ConfigurationData $cd
```

*Si noti che `NodeName` non può essere un asterisco, ma è obbligatorio un nome di nodo specifico.*

**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**

## Credenziali di dominio

Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.
L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.

**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**

Se la proprietà `Username` della credenziale contiene un carattere "\'" o "@", DSC la considera un account di dominio.
Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.

## PSDscAllowDomainUser

Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.
In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:

```PowerShell
$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            # PSDscAllowPlainTextPassword = $true
            CertificateFile = "C:\PublicKeys\server1.cer"
        }
    )
}
```

Lo script di configurazione genera ora il file MOF senza errori o avvisi.




<!--HONumber=Aug16_HO3-->


