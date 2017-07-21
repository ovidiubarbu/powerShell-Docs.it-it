---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Opzioni delle credenziali nei dati di configurazione
ms.openlocfilehash: 7fadce447c418b229a534e92d12bc2131365a37a
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="fa0e5-103">Opzioni delle credenziali nei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="fa0e5-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="fa0e5-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="fa0e5-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="fa0e5-105">Password di testo normale e utenti di dominio</span><span class="sxs-lookup"><span data-stu-id="fa0e5-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="fa0e5-106">Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-106">DSC configurations containing a credential without encryption will generate an error messages about plain text passwords.</span></span>
<span data-ttu-id="fa0e5-107">Inoltre, DSC genera un avviso quando si usano credenziali di dominio.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="fa0e5-108">Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="fa0e5-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="fa0e5-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="fa0e5-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="fa0e5-110">**PsDscAllowDomainUser**</span></span>

><span data-ttu-id="fa0e5-111">**Nota:** l'uso di password non crittografate non è un metodo sicuro.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-111">**Note:** Using plaintext passwords is not secure.</span></span> <span data-ttu-id="fa0e5-112">È consigliabile proteggere le credenziali tramite le tecniche illustrate più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>

<span data-ttu-id="fa0e5-113">Di seguito è riportato un esempio del passaggio di credenziali non crittografate:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-113">The following is an example of passing plain text credentials:</span></span>

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

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="fa0e5-114">Gestione delle credenziali in DSC</span><span class="sxs-lookup"><span data-stu-id="fa0e5-114">Handling Credentials in DSC</span></span>

<span data-ttu-id="fa0e5-115">Le risorse di configurazione DSC vengono eseguite come `Local System` per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-115">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="fa0e5-116">Tuttavia, per alcune risorse è necessaria una credenziale, ad esempio quando la risorsa `Package` deve installare software nell'ambito di un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-116">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="fa0e5-117">Le risorse delle versioni precedenti usano un nome di proprietà `Credential` hardcoded per gestire questo caso.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-117">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="fa0e5-118">In WMF 5.0 è stata aggiunta una proprietà `PsDscRunAsCredential` automatica per tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-118">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="fa0e5-119">Per informazioni sull'uso di `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="fa0e5-119">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="fa0e5-120">Le risorse più recenti e quelle personalizzate possono usare questa proprietà automatica invece di creare una proprietà personalizzata per le credenziali.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-120">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

<span data-ttu-id="fa0e5-121">*Si noti che la progettazione di alcune risorse prevede l'uso di più credenziali per un motivo specifico e tali risorse hanno proprietà delle credenziali proprie.*</span><span class="sxs-lookup"><span data-stu-id="fa0e5-121">*Note that the design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.*</span></span>

<span data-ttu-id="fa0e5-122">Per trovare le proprietà delle credenziali disponibili in una risorsa, usare `Get-DscResource -Name ResourceName -Syntax` o Intellisense in ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="fa0e5-122">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="fa0e5-123">Questo esempio usa una risorsa [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-123">This example uses a [Group](https://msdn.microsoft.com/en-us/powershell/dsc/groupresource) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="fa0e5-124">La risorsa può creare gruppi locali e aggiungere o rimuovere membri.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-124">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="fa0e5-125">Accetta sia la proprietà `Credential` sia la proprietà `PsDscRunAsCredential` automatica.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-125">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="fa0e5-126">Tuttavia, la risorsa usa solo la proprietà `Credential`.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-126">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="fa0e5-127">Per altre informazioni sulla proprietà `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="fa0e5-127">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="fa0e5-128">Esempio: proprietà Credential della risorsa Group</span><span class="sxs-lookup"><span data-stu-id="fa0e5-128">Example: The Group resource Credential property</span></span>

<span data-ttu-id="fa0e5-129">Poiché DSC viene eseguito in `Local System`, ha già le autorizzazioni necessarie per modificare gruppi e utenti locali.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-129">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="fa0e5-130">Se il membro aggiunto è un account locale, non è necessaria alcuna credenziale.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-130">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="fa0e5-131">Se la risorsa `Group` aggiunge un account di dominio al gruppo locale, è necessaria una credenziale.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-131">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="fa0e5-132">Le query anonime in Active Directory non sono consentite.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-132">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="fa0e5-133">La proprietà `Credential` della risorsa `Group` corrisponde all'account di dominio usato per eseguire query in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-133">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="fa0e5-134">Per quasi tutti gli scopi può trattarsi di un account utente generico, perché per impostazione predefinita gli utenti possono *leggere* la maggior parte degli oggetti in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-134">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="fa0e5-135">Configurazione di esempio</span><span class="sxs-lookup"><span data-stu-id="fa0e5-135">Example Configuration</span></span>

<span data-ttu-id="fa0e5-136">Il codice di esempio seguente usa DSC per immettere un utente di dominio in un gruppo locale:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-136">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="fa0e5-137">Questo codice genera un messaggio di errore e uno di avviso:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-137">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="fa0e5-138">Questo esempio include due problemi:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-138">This example has two issues:</span></span>
1.  <span data-ttu-id="fa0e5-139">Un errore indica che le password di testo semplice non sono consigliate</span><span class="sxs-lookup"><span data-stu-id="fa0e5-139">An error explains that plain text passwords are not recommended</span></span>
2.  <span data-ttu-id="fa0e5-140">Un avviso sconsiglia l'uso di una credenziale di dominio</span><span class="sxs-lookup"><span data-stu-id="fa0e5-140">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="fa0e5-141">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="fa0e5-141">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="fa0e5-142">Il primo messaggio di errore contiene un URL con la documentazione.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-142">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="fa0e5-143">Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e un certificato.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-143">This link explains how to encrypt passwords using a [ConfigurationData](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) structure and a certificate.</span></span>
<span data-ttu-id="fa0e5-144">Per altre informazioni sui certificati e su DSC, [leggere questo post](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="fa0e5-144">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="fa0e5-145">Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-145">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

<span data-ttu-id="fa0e5-146">*Si noti che `NodeName` non può essere un asterisco, ma è obbligatorio un nome di nodo specifico.*</span><span class="sxs-lookup"><span data-stu-id="fa0e5-146">*Note that `NodeName` cannot equal asterisk, a specific node name is mandatory.*</span></span>

<span data-ttu-id="fa0e5-147">**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="fa0e5-147">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="fa0e5-148">Credenziali di dominio</span><span class="sxs-lookup"><span data-stu-id="fa0e5-148">Domain Credentials</span></span>

<span data-ttu-id="fa0e5-149">Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-149">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="fa0e5-150">L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-150">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="fa0e5-151">**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**</span><span class="sxs-lookup"><span data-stu-id="fa0e5-151">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="fa0e5-152">Se la proprietà `Username` della credenziale contiene un carattere "\'" o "@", DSC la considera un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-152">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="fa0e5-153">Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-153">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="fa0e5-154">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="fa0e5-154">PSDscAllowDomainUser</span></span>

<span data-ttu-id="fa0e5-155">Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-155">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="fa0e5-156">In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="fa0e5-156">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="fa0e5-157">Lo script di configurazione genera ora il file MOF senza errori o avvisi.</span><span class="sxs-lookup"><span data-stu-id="fa0e5-157">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>

