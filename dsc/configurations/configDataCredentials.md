---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Opzioni delle credenziali nei dati di configurazione
ms.openlocfilehash: 10cf3456fcc7104b7dd779db30aebace54ba087a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54046642"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="cc5cc-103">Opzioni delle credenziali nei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="cc5cc-103">Credentials Options in Configuration Data</span></span>
><span data-ttu-id="cc5cc-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cc5cc-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="cc5cc-105">Password di testo normale e utenti di dominio</span><span class="sxs-lookup"><span data-stu-id="cc5cc-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="cc5cc-106">Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span>
<span data-ttu-id="cc5cc-107">Inoltre, DSC genera un avviso quando si usano credenziali di dominio.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-107">Also, DSC will generate a warning when using domain credentials.</span></span>
<span data-ttu-id="cc5cc-108">Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>
* <span data-ttu-id="cc5cc-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="cc5cc-109">**PsDscAllowPlainTextPassword**</span></span>
* <span data-ttu-id="cc5cc-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="cc5cc-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="cc5cc-111">L'archiviazione o la trasmissione di password di testo normale non crittografata in genere non è protetta.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="cc5cc-112">È consigliabile proteggere le credenziali tramite le tecniche illustrate più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span>
> <span data-ttu-id="cc5cc-113">Il servizio Automation DSC di Azure consente di gestire centralmente le credenziali da compilare nelle configurazioni e archiviare in modo sicuro.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span>
> <span data-ttu-id="cc5cc-114">Per informazioni, vedere: [Compilazione di configurazioni DSC / asset credenziali](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="cc5cc-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

<span data-ttu-id="cc5cc-115">Di seguito è riportato un esempio del passaggio di credenziali non crittografate:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-115">The following is an example of passing plain text credentials:</span></span>

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
        $password = $Node.LocalPassword | ConvertTo-SecureString -asPlainText -Force
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
            Credential = $promptedCreds
            GroupName = "Administrators"
            DependsOn = "[User]User2"
            Ensure = "Present"
            MembersToInclude = "User2"
        }
    }
}

# We declared the ConfigurationData in a local variable, but we need to pass it
# in to our configuration function
# We need to invoke the configuration function we created to generate a MOF
unencryptedPasswordDemo -ConfigurationData $ConfigurationData

# We need to pass the MOF to the machines we named.
#-wait: doesn't use jobs so we get blocked at the prompt until the configuration is done
#-verbose: so we can see what's going on and catch any errors
#-force: for testing purposes, I run start-dscconfiguration frequently + want to make sure i'm
#        not blocked by previous configurations that are still running
Start-DscConfiguration ./unencryptedPasswordDemo -verbose -wait -force
```

<span data-ttu-id="cc5cc-116">Questo è un estratto dal file "MOF" generato dalla configurazione per "TestMachine1".</span><span class="sxs-lookup"><span data-stu-id="cc5cc-116">This is an excerpt from the ".mof" file generated by the configuration for "TestMachine1".</span></span> <span data-ttu-id="cc5cc-117">Il `System.Security.SecureString` usato nella configurazione è stata convertita in testo normale e archiviata nel file "MOF" come un `MSF_Credential`.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-117">The `System.Security.SecureString` used in the configuration was converted to plain text and stored in the ".mof" file as a `MSF_Credential`.</span></span> <span data-ttu-id="cc5cc-118">Oggetto `SecureString` viene crittografata con il profilo utente corrente.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-118">A `SecureString` is encrypted with the current users profile.</span></span> <span data-ttu-id="cc5cc-119">Questo funziona bene con tutte le forme di gestione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-119">This works well with all forms of PowerShell remote management.</span></span> <span data-ttu-id="cc5cc-120">Un file "con estensione MOF" è progettato per essere un meccanismo di configurazione indipendente di standby.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-120">A ".mof" file is designed to be a stand alone configuration mechanism.</span></span> <span data-ttu-id="cc5cc-121">A partire da PowerShell 5.0, i file "MOF" in un nodo vengono crittografati quando sono inattivi, ma non in transito per il nodo.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-121">Beginning in PowerShell 5.0, ".mof" files on a Node are encrypted at rest, but not in transit to the Node.</span></span> <span data-ttu-id="cc5cc-122">Ciò significa che le password in un file "con estensione MOF" sono esposti come testo non crittografato quando li si applica a un nodo.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-122">This means that passwords in a ".mof" file are exposed as clear text when you apply them to a Node.</span></span> <span data-ttu-id="cc5cc-123">Per crittografare le credenziali, è necessario usare una **Server di Pull**.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-123">To encrypt credentials, you need to use a **Pull Server**.</span></span> <span data-ttu-id="cc5cc-124">Per altre informazioni, vedere [i file MOF di sicurezza con certificati](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="cc5cc-124">For more information, see [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>

```syntax
instance of MSFT_Credential as $MSFT_Credential1ref
{
Password = "ThisIsYetAnotherPlaintextPassword";
 UserName = "User2";

};

instance of MSFT_UserResource as $MSFT_UserResource1ref
{
ResourceID = "[User]User2";
 Description = "local account";
 UserName = "User2";
 Ensure = "Present";
 Password = $MSFT_Credential1ref;
 Disabled = False;
 SourceInfo = "::66::9::User";
 PasswordNeverExpires = True;
 ModuleName = "PsDesiredStateConfiguration";
 PasswordChangeRequired = False;

ModuleVersion = "1.0";

 ConfigurationName = "unencryptedPasswordDemo";

};
```

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="cc5cc-125">Gestione delle credenziali in DSC</span><span class="sxs-lookup"><span data-stu-id="cc5cc-125">Handling Credentials in DSC</span></span>

<span data-ttu-id="cc5cc-126">Le risorse di configurazione DSC vengono eseguite come `Local System` per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-126">DSC configuration resources run as `Local System` by default.</span></span>
<span data-ttu-id="cc5cc-127">Tuttavia, per alcune risorse è necessaria una credenziale, ad esempio quando la risorsa `Package` deve installare software nell'ambito di un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-127">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="cc5cc-128">Le risorse delle versioni precedenti usano un nome di proprietà `Credential` hardcoded per gestire questo caso.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-128">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span>
<span data-ttu-id="cc5cc-129">In WMF 5.0 è stata aggiunta una proprietà `PsDscRunAsCredential` automatica per tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-129">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span>
<span data-ttu-id="cc5cc-130">Per informazioni sull'uso di `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="cc5cc-130">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span>
<span data-ttu-id="cc5cc-131">Le risorse più recenti e quelle personalizzate possono usare questa proprietà automatica invece di creare una proprietà personalizzata per le credenziali.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-131">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="cc5cc-132">La progettazione di alcune risorse prevede l'uso di più credenziali per un motivo specifico e tali risorse hanno proprietà delle credenziali proprie.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-132">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="cc5cc-133">Per trovare le proprietà delle credenziali disponibili in una risorsa, usare `Get-DscResource -Name ResourceName -Syntax` o Intellisense in ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="cc5cc-133">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

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

<span data-ttu-id="cc5cc-134">Questo esempio usa una risorsa [Group](../resources/resources.md), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-134">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span>
<span data-ttu-id="cc5cc-135">La risorsa può creare gruppi locali e aggiungere o rimuovere membri.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-135">It can create local groups and add or remove members.</span></span>
<span data-ttu-id="cc5cc-136">Accetta sia la proprietà `Credential` sia la proprietà `PsDscRunAsCredential` automatica.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-136">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span>
<span data-ttu-id="cc5cc-137">Tuttavia, la risorsa usa solo la proprietà `Credential`.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-137">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="cc5cc-138">Per altre informazioni sulla proprietà `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="cc5cc-138">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="cc5cc-139">Esempio: La risorsa del gruppo di proprietà Credential</span><span class="sxs-lookup"><span data-stu-id="cc5cc-139">Example: The Group resource Credential property</span></span>

<span data-ttu-id="cc5cc-140">Poiché DSC viene eseguito in `Local System`, ha già le autorizzazioni necessarie per modificare gruppi e utenti locali.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-140">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span>
<span data-ttu-id="cc5cc-141">Se il membro aggiunto è un account locale, non è necessaria alcuna credenziale.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-141">If the member added is a local account, then no credential is necessary.</span></span>
<span data-ttu-id="cc5cc-142">Se la risorsa `Group` aggiunge un account di dominio al gruppo locale, è necessaria una credenziale.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-142">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="cc5cc-143">Le query anonime in Active Directory non sono consentite.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-143">Anonymous queries to Active Directory are not allowed.</span></span>
<span data-ttu-id="cc5cc-144">La proprietà `Credential` della risorsa `Group` corrisponde all'account di dominio usato per eseguire query in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-144">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span>
<span data-ttu-id="cc5cc-145">Per quasi tutti gli scopi può trattarsi di un account utente generico, perché per impostazione predefinita gli utenti possono *leggere* la maggior parte degli oggetti in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-145">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="cc5cc-146">Configurazione di esempio</span><span class="sxs-lookup"><span data-stu-id="cc5cc-146">Example Configuration</span></span>

<span data-ttu-id="cc5cc-147">Il codice di esempio seguente usa DSC per immettere un utente di dominio in un gruppo locale:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-147">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="cc5cc-148">Questo codice genera un messaggio di errore e uno di avviso:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-148">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="cc5cc-149">Questo esempio include due problemi:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-149">This example has two issues:</span></span>
1. <span data-ttu-id="cc5cc-150">Un errore indica che le password di testo semplice non sono consigliate</span><span class="sxs-lookup"><span data-stu-id="cc5cc-150">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="cc5cc-151">Un avviso sconsiglia l'uso di una credenziale di dominio</span><span class="sxs-lookup"><span data-stu-id="cc5cc-151">A warning advises against using a domain credential</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="cc5cc-152">PsDscAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="cc5cc-152">PsDscAllowPlainTextPassword</span></span>

<span data-ttu-id="cc5cc-153">Il primo messaggio di errore contiene un URL con la documentazione.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-153">The first error message has a URL with documentation.</span></span>
<span data-ttu-id="cc5cc-154">Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](./configData.md) e un certificato.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-154">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span>
<span data-ttu-id="cc5cc-155">Per altre informazioni sui certificati e su DSC, [leggere questo post](http://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="cc5cc-155">For more information on certificates and DSC [read this post](http://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="cc5cc-156">Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-156">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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
> <span data-ttu-id="cc5cc-157">`NodeName` non può essere un asterisco, ma è obbligatorio un nome di nodo specifico.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-157">`NodeName` cannot equal asterisk, a specific node name is mandatory.</span></span>

<span data-ttu-id="cc5cc-158">**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="cc5cc-158">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="cc5cc-159">Credenziali di dominio</span><span class="sxs-lookup"><span data-stu-id="cc5cc-159">Domain Credentials</span></span>

<span data-ttu-id="cc5cc-160">Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-160">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span>
<span data-ttu-id="cc5cc-161">L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-161">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="cc5cc-162">**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**</span><span class="sxs-lookup"><span data-stu-id="cc5cc-162">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="cc5cc-163">Se la proprietà `Username` della credenziale contiene un carattere "\'" o "@", DSC la considera un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-163">If there is a '\' or '@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span>
<span data-ttu-id="cc5cc-164">Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-164">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="cc5cc-165">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="cc5cc-165">PSDscAllowDomainUser</span></span>

<span data-ttu-id="cc5cc-166">Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-166">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span>
<span data-ttu-id="cc5cc-167">In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="cc5cc-167">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="cc5cc-168">Lo script di configurazione genera ora il file MOF senza errori o avvisi.</span><span class="sxs-lookup"><span data-stu-id="cc5cc-168">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
