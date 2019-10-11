---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Opzioni delle credenziali nei dati di configurazione
ms.openlocfilehash: 660c3643f7eb2e9ccb91bd992747fb9d5da0ccdb
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954538"
---
# <a name="credentials-options-in-configuration-data"></a>Opzioni delle credenziali nei dati di configurazione

>Si applica a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Password di testo normale e utenti di dominio

Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.
Inoltre, DSC genera un avviso quando si usano credenziali di dominio.
Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:

- **PsDscAllowPlainTextPassword**
- **PsDscAllowDomainUser**

> [!NOTE]
> L'archiviazione o la trasmissione di password di testo normale non crittografata in genere non è protetta. È consigliabile proteggere le credenziali tramite le tecniche illustrate più avanti in questo argomento.
> Il servizio Automation DSC di Azure consente di gestire centralmente le credenziali da compilare nelle configurazioni e archiviare in modo sicuro.
> Per informazioni, vedere: [Compilazione di configurazioni DSC/Asset credenziali](/azure/automation/automation-dsc-compile#credential-assets)

## <a name="handling-credentials-in-dsc"></a>Gestione delle credenziali in DSC

Le risorse di configurazione DSC vengono eseguite come `Local System` per impostazione predefinita.
Tuttavia, per alcune risorse è necessaria una credenziale, ad esempio quando la risorsa `Package` deve installare software nell'ambito di un account utente specifico.

Le risorse delle versioni precedenti usano un nome di proprietà `Credential` hardcoded per gestire questo caso.
In WMF 5.0 è stata aggiunta una proprietà `PsDscRunAsCredential` automatica per tutte le risorse.
Per informazioni sull'uso di `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).
Le risorse più recenti e quelle personalizzate possono usare questa proprietà automatica invece di creare una proprietà personalizzata per le credenziali.

> [!NOTE]
> La progettazione di alcune risorse prevede l'uso di più credenziali per un motivo specifico e tali risorse hanno proprietà delle credenziali proprie.

Per trovare le proprietà delle credenziali disponibili in una risorsa, usare `Get-DscResource -Name ResourceName -Syntax` o Intellisense in ISE (`CTRL+SPACE`).

```powershell
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

Questo esempio usa una risorsa [Group](../resources/resources.md), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.
La risorsa può creare gruppi locali e aggiungere o rimuovere membri.
Accetta sia la proprietà `Credential` sia la proprietà `PsDscRunAsCredential` automatica.
Tuttavia, la risorsa usa solo la proprietà `Credential`.

Per altre informazioni sulla proprietà `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).

## <a name="example-the-group-resource-credential-property"></a>Esempio: proprietà Credential della risorsa Group

Poiché DSC viene eseguito in `Local System`, ha già le autorizzazioni necessarie per modificare gruppi e utenti locali.
Se il membro aggiunto è un account locale, non è necessaria alcuna credenziale.
Se la risorsa `Group` aggiunge un account di dominio al gruppo locale, è necessaria una credenziale.

Le query anonime in Active Directory non sono consentite.
La proprietà `Credential` della risorsa `Group` corrisponde all'account di dominio usato per eseguire query in Active Directory.
Per quasi tutti gli scopi può trattarsi di un account utente generico, perché per impostazione predefinita gli utenti possono *leggere* la maggior parte degli oggetti in Active Directory.

## <a name="example-configuration"></a>Configurazione di esempio

Il codice di esempio seguente usa DSC per immettere un utente di dominio in un gruppo locale:

```powershell
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
ConvertTo-MOFInstance : System.InvalidOperationException error processing property 'Credential' OF
TYPE 'Group': Converting and storing encrypted passwords as plain text is not recommended.
For more information on securing credentials in MOF file, please refer to MSDN blog:
https://go.microsoft.com/fwlink/?LinkId=393729

At line:11 char:9
+   Group
At line:341 char:16
+     $aliasId = ConvertTo-MOFInstance $keywordName $canonicalizedValue
+                ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (:) [Write-Error], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessProperty,ConvertTo-MOFInstance
WARNING: It is not recommended to use domain credential for node 'localhost'. In order to suppress
the warning, you can add a property named 'PSDscAllowDomainUser' with a value of $true to your DSC
configuration data for node 'localhost'.

Compilation errors occurred while processing configuration
'DomainCredentialExample'. Please review the errors reported in error stream and modify your
configuration code appropriately.
At C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:3917 char:5
+     throw $ErrorRecord
+     ~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidOperation: (DomainCredentialExample:String) [], InvalidOperationException
    + FullyQualifiedErrorId : FailToProcessConfiguration
```

Questo esempio include due problemi:

1. Un errore indica che le password di testo semplice non sono consigliate
2. Un avviso sconsiglia l'uso di una credenziale di dominio

I flag **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** eliminano l'errore e l'avviso che informano l'utente dei rischi coinvolti.

## <a name="psdscallowplaintextpassword"></a>PSDSCAllowPlainTextPassword

Il primo messaggio di errore contiene un URL con la documentazione.
Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](./configData.md) e un certificato.
Per altre informazioni sui certificati e su DSC, [leggere questo post](https://aka.ms/certs4dsc).

Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
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

DomainCredentialExample -ConfigurationData $cd
```

### <a name="localhostmof"></a>localhost.mof

Il flag **PSDSCAllowPlainTextPassword** richiede che l'utente accetti il rischio correlato all'archiviazione delle password in testo normale in un file MOF. Nel file MOF generato, anche se è stato usato un oggetto **PSCredential** contenente una **SecureString**, le password vengono comunque visualizzate come testo normale. Questa è l'unica volta in cui vengono esposte le credenziali. Chiunque riesce ad accedere a questo file MOF ottiene l'accesso anche all'account amministratore.

```
/*
@TargetNode='localhost'
@GeneratedBy=Administrator
@GenerationDate=01/31/2019 06:43:13
@GenerationHost=Server01
*/

instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsAPlaintextPassword";
 UserName = "Administrator";

};

instance of MSFT_GroupResource as $MSFT_GroupResource1ref
{
ResourceID = "[Group]DomainUserToLocalGroup";
 MembersToInclude = {
    "contoso\\alice"
};
 Credential = $MSFT_Credential1ref;
 SourceInfo = "::11::9::Group";
 GroupName = "ApplicationAdmins";
 ModuleName = "PSDesiredStateConfiguration";

ModuleVersion = "1.0";

 ConfigurationName = "DomainCredentialExample";

};
```

### <a name="credentials-in-transit-and-at-rest"></a>Credenziali in transito e inattive

- Il flag **PSDscAllowPlainTextPassword** consente la compilazione di file MOF che contengono password come testo non crittografato.
  Adottare le necessarie precauzioni quando si archiviano file MOF che contengono password come testo non crittografato.
- Quando il file MOF viene recapitato a un nodo in modalità **push**, WinRM crittografa la comunicazione per proteggere la password come testo non crittografato, a meno che non si ignori l'impostazione predefinita con il parametro **AllowUnencrypted**.
  - La crittografia del file MOF con un certificato protegge il file MOF nello stato inattivo prima dell'applicazione a un nodo.
- Nella modalità **pull** è possibile configurare il server di pull Windows per usare HTTPS per crittografare il traffico tramite il protocollo specificato in Internet Information Server. Per altre informazioni, vedere gli articoli [Configurazione di un client di pull DSC](../pull-server/pullclient.md) e [Protezione del file MOF con certificati](../pull-server/secureMOF.md).
  - Nel servizio di [configurazione dello stato di Automazione di Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview), il traffico pull viene sempre crittografato.
- Nel nodo i file MOF vengono crittografati nello stato inattivo a partire da PowerShell 5.0.
  - In PowerShell 4.0 i file MOF non vengono decrittografati nello stato inattivo a meno che non vengano crittografati con un certificato quando ne viene eseguito il push o pull sul nodo.

**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**

## <a name="domain-credentials"></a>Credenziali di dominio

Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.
L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.

**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**

Se la proprietà `Username` della credenziale contiene un carattere '\\' o '\@', DSC la considera un account di dominio.
Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.
In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:

```powershell
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "contoso\Administrator"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

Configuration DomainCredentialExample
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration

    node localhost
    {
        Group DomainUserToLocalGroup
        {
            GroupName        = 'ApplicationAdmins'
            MembersToInclude = 'contoso\alice'
            Credential       = $credential
        }
    }
}

$cd = @{
    AllNodes = @(
        @{
            NodeName = 'localhost'
            PSDscAllowDomainUser = $true
            PSDscAllowPlainTextPassword = $true
        }
    )
}

DomainCredentialExample -ConfigurationData $cd
```

Lo script di configurazione genera ora il file MOF senza errori o avvisi.
