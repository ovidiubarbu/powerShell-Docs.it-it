---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Opzioni delle credenziali nei dati di configurazione
ms.openlocfilehash: 2c6685f3b6992537d1652f172cf926b85dd634c6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="credentials-options-in-configuration-data"></a>Opzioni delle credenziali nei dati di configurazione
>Si applica a: Windows PowerShell 5.0

## <a name="plain-text-passwords-and-domain-users"></a>Password di testo normale e utenti di dominio

Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.
Inoltre, DSC genera un avviso quando si usano credenziali di dominio.
Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:
* **PsDscAllowPlainTextPassword**
* **PsDscAllowDomainUser**

> [!NOTE]
> L'archiviazione o la trasmissione di password di testo normale non crittografata in genere non è protetta. È consigliabile proteggere le credenziali tramite le tecniche illustrate più avanti in questo argomento.
> Il servizio Automation DSC di Azure consente di gestire centralmente le credenziali da compilare nelle configurazioni e archiviare in modo sicuro.
> Per informazioni, vedere [Compilazione di configurazioni in Azure Automation DSC/Asset credenziali](/azure/automation/automation-dsc-compile#credential-assets)

Di seguito è riportato un esempio del passaggio di credenziali non crittografate:

```powershell
#Prompt user for their credentials
#credentials will be unencrypted in the MOF
$promptedCreds = get-credential -Message "Please enter your credentials to generate a DSC MOF:"

# Store passwords in plaintext, in the document itself
# will also be stored in plaintext in the mof
$password = "ThisIsAPlaintextPassword" | ConvertTo-SecureString -asPlainText -Force
$username = "User1"
[PSCredential] $credential = New-Object System.Management.Automation.PSCredential($username,$password)

# DSC requires explicit confirmation before storing passwords insecurely
$ConfigurationData = @{
    AllNodes = @(
        @{
            # The "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="*"
            PSDscAllowPlainTextPassword = $true
        },
        #however, each node still needs to be explicitly defined for "*" to have meaning
        @{
            NodeName = "TestMachine1"
        },
        #we can also use a property to define node-specific passwords, although this is no more secure
        @{
            NodeName = "TestMachine2";
            UserName = "User2"
            LocalPassword = "ThisIsYetAnotherPlaintextPassword"
        }
        )
}
configuration unencryptedPasswordDemo
{
    Node "TestMachine1"
    {
        # We use the plaintext password to generate a new account
        User User1
        {
            UserName = $username
            Password = $credential
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }
        # We use the prompted password to add this account to the local admins group
        Group addToAdmin
        {
            # Ensure the user exists before we add the user to a group
            DependsOn = "[User]User1"
            Credential = $promptedCreds
            GroupName = "Administrators"
            Ensure = "Present"
            MembersToInclude = "User1"
        }
    }

    Node "TestMachine2"
    {
        # Now we'll use a node-specific password to this machine
        $password = $Node.LocalPass | ConvertTo-SecureString -asPlainText -Force
        $username = $node.UserName
        [PSCredential] $nodeCred = New-Object System.Management.Automation.PSCredential($username,$password)

        User User2
        {
            UserName = $username
            Password = $nodeCred
            Description = "local account"
            Ensure = "Present"
            Disabled = $false
            PasswordNeverExpires = $true
            PasswordChangeRequired = $false
        }

        Group addToAdmin
        {
            Credential = $domain
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }

}
# We declared the ConfigurationData in a local variable, but we need to pass it in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData
# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

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

Questo esempio usa una risorsa [Group](https://msdn.microsoft.com/powershell/dsc/groupresource), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.
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
1. Un errore indica che le password di testo semplice non sono consigliate
2. Un avviso sconsiglia l'uso di una credenziale di dominio

## <a name="psdscallowplaintextpassword"></a>PsDscAllowPlainTextPassword

Il primo messaggio di errore contiene un URL con la documentazione.
Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](https://msdn.microsoft.com/powershell/dsc/configdata) e un certificato.
Per altre informazioni sui certificati e su DSC, [leggere questo post](http://aka.ms/certs4dsc).

Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:

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

> [!NOTE]
> `NodeName` non può essere un asterisco, ma è obbligatorio un nome di nodo specifico.

**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**

Un'eccezione potrebbe essere quando si usa il servizio Automation DSC di Azure poiché i dati vengono sempre archiviati crittografati, che siano in transito, inattivi nel servizio o inattivi nel nodo.

## <a name="domain-credentials"></a>Credenziali di dominio

Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.
L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.

**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**

Se la proprietà `Username` della credenziale contiene un carattere "\'" o "@", DSC la considera un account di dominio.
Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.

## <a name="psdscallowdomainuser"></a>PSDscAllowDomainUser

Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.
In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:

```powershell
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