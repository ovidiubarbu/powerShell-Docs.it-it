---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Opzioni delle credenziali nei dati di configurazione
ms.openlocfilehash: aac27f1ff4b4287b53745fa3b946fb3de84771c2
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870558"
---
# <a name="credentials-options-in-configuration-data"></a><span data-ttu-id="d0481-103">Opzioni delle credenziali nei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="d0481-103">Credentials Options in Configuration Data</span></span>

> <span data-ttu-id="d0481-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="d0481-104">Applies To: Windows PowerShell 5.0</span></span>

## <a name="plain-text-passwords-and-domain-users"></a><span data-ttu-id="d0481-105">Password di testo normale e utenti di dominio</span><span class="sxs-lookup"><span data-stu-id="d0481-105">Plain Text Passwords and Domain Users</span></span>

<span data-ttu-id="d0481-106">Le configurazioni DSC che contengono una credenziale senza crittografia generano un messaggio di errore relativo alle password di testo normale.</span><span class="sxs-lookup"><span data-stu-id="d0481-106">DSC configurations containing a credential without encryption will generate an error message about plain text passwords.</span></span> <span data-ttu-id="d0481-107">Inoltre, DSC genera un avviso quando si usano credenziali di dominio.</span><span class="sxs-lookup"><span data-stu-id="d0481-107">Also, DSC will generate a warning when using domain credentials.</span></span> <span data-ttu-id="d0481-108">Per eliminare questi messaggi di errore e di avviso, usare le parole chiave dei dati di configurazione DSC seguenti:</span><span class="sxs-lookup"><span data-stu-id="d0481-108">To suppress these error and warning messages use the DSC configuration data keywords:</span></span>

- <span data-ttu-id="d0481-109">**PsDscAllowPlainTextPassword**</span><span class="sxs-lookup"><span data-stu-id="d0481-109">**PsDscAllowPlainTextPassword**</span></span>
- <span data-ttu-id="d0481-110">**PsDscAllowDomainUser**</span><span class="sxs-lookup"><span data-stu-id="d0481-110">**PsDscAllowDomainUser**</span></span>

> [!NOTE]
> <span data-ttu-id="d0481-111">L'archiviazione o la trasmissione di password di testo normale non crittografata in genere non è protetta.</span><span class="sxs-lookup"><span data-stu-id="d0481-111">Storing/transmitting plaintext passwords unencrypted is generally not secure.</span></span> <span data-ttu-id="d0481-112">È consigliabile proteggere le credenziali tramite le tecniche illustrate più avanti in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="d0481-112">Securing credentials by using the techniques covered later in this topic is recommended.</span></span> <span data-ttu-id="d0481-113">Il servizio Automation DSC di Azure consente di gestire centralmente le credenziali da compilare nelle configurazioni e archiviare in modo sicuro.</span><span class="sxs-lookup"><span data-stu-id="d0481-113">The Azure Automation DSC service allows you to centrally manage credentials to be compiled in configurations and stored securely.</span></span> <span data-ttu-id="d0481-114">Per informazioni, vedere: [Compilazione di configurazioni DSC/Asset credenziali](/azure/automation/automation-dsc-compile#credential-assets)</span><span class="sxs-lookup"><span data-stu-id="d0481-114">For information, see: [Compiling DSC Configurations / Credential Assets](/azure/automation/automation-dsc-compile#credential-assets)</span></span>

## <a name="handling-credentials-in-dsc"></a><span data-ttu-id="d0481-115">Gestione delle credenziali in DSC</span><span class="sxs-lookup"><span data-stu-id="d0481-115">Handling Credentials in DSC</span></span>

<span data-ttu-id="d0481-116">Le risorse di configurazione DSC vengono eseguite come `Local System` per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="d0481-116">DSC configuration resources run as `Local System` by default.</span></span> <span data-ttu-id="d0481-117">Tuttavia, per alcune risorse è necessaria una credenziale, ad esempio quando la risorsa `Package` deve installare software nell'ambito di un account utente specifico.</span><span class="sxs-lookup"><span data-stu-id="d0481-117">However, some resources need a credential, for example when the `Package` resource needs to install software under a specific user account.</span></span>

<span data-ttu-id="d0481-118">Le risorse delle versioni precedenti usano un nome di proprietà `Credential` hardcoded per gestire questo caso.</span><span class="sxs-lookup"><span data-stu-id="d0481-118">Earlier resources used a hard-coded `Credential` property name to handle this.</span></span> <span data-ttu-id="d0481-119">In WMF 5.0 è stata aggiunta una proprietà `PsDscRunAsCredential` automatica per tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="d0481-119">WMF 5.0 added an automatic `PsDscRunAsCredential` property for all resources.</span></span> <span data-ttu-id="d0481-120">Per informazioni sull'uso di `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d0481-120">For information about using `PsDscRunAsCredential`, see [Running DSC with user credentials](runAsUser.md).</span></span> <span data-ttu-id="d0481-121">Le risorse più recenti e quelle personalizzate possono usare questa proprietà automatica invece di creare una proprietà personalizzata per le credenziali.</span><span class="sxs-lookup"><span data-stu-id="d0481-121">Newer resources and custom resources can use this automatic property instead of creating their own property for credentials.</span></span>

> [!NOTE]
> <span data-ttu-id="d0481-122">La progettazione di alcune risorse prevede l'uso di più credenziali per un motivo specifico e tali risorse hanno proprietà delle credenziali proprie.</span><span class="sxs-lookup"><span data-stu-id="d0481-122">The design of some resources are to use multiple credentials for a specific reason, and they will have their own credential properties.</span></span>

<span data-ttu-id="d0481-123">Per trovare le proprietà delle credenziali disponibili in una risorsa, usare `Get-DscResource -Name ResourceName -Syntax` o Intellisense in ISE (`CTRL+SPACE`).</span><span class="sxs-lookup"><span data-stu-id="d0481-123">To find the available credential properties on a resource use either `Get-DscResource -Name ResourceName -Syntax` or the Intellisense in the ISE (`CTRL+SPACE`).</span></span>

```powershell
Get-DscResource -Name Group -Syntax
```

```Output
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

<span data-ttu-id="d0481-124">Questo esempio usa una risorsa [Group](../resources/resources.md), inclusa nel modulo di risorse DSC `PSDesiredStateConfiguration` predefinito.</span><span class="sxs-lookup"><span data-stu-id="d0481-124">This example uses a [Group](../resources/resources.md) resource from the `PSDesiredStateConfiguration` built-in DSC resource module.</span></span> <span data-ttu-id="d0481-125">La risorsa può creare gruppi locali e aggiungere o rimuovere membri.</span><span class="sxs-lookup"><span data-stu-id="d0481-125">It can create local groups and add or remove members.</span></span> <span data-ttu-id="d0481-126">Accetta sia la proprietà `Credential` sia la proprietà `PsDscRunAsCredential` automatica.</span><span class="sxs-lookup"><span data-stu-id="d0481-126">It accepts both the `Credential` property and the automatic `PsDscRunAsCredential` property.</span></span> <span data-ttu-id="d0481-127">Tuttavia, la risorsa usa solo la proprietà `Credential`.</span><span class="sxs-lookup"><span data-stu-id="d0481-127">However, the resource only uses the `Credential` property.</span></span>

<span data-ttu-id="d0481-128">Per altre informazioni sulla proprietà `PsDscRunAsCredential`, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="d0481-128">For more information about the `PsDscRunAsCredential` property, see [Running DSC with user credentials](runAsUser.md).</span></span>

## <a name="example-the-group-resource-credential-property"></a><span data-ttu-id="d0481-129">Esempio: proprietà Credential della risorsa Group</span><span class="sxs-lookup"><span data-stu-id="d0481-129">Example: The Group resource Credential property</span></span>

<span data-ttu-id="d0481-130">Poiché DSC viene eseguito in `Local System`, ha già le autorizzazioni necessarie per modificare gruppi e utenti locali.</span><span class="sxs-lookup"><span data-stu-id="d0481-130">DSC runs under `Local System`, so it already has permissions to change local users and groups.</span></span> <span data-ttu-id="d0481-131">Se il membro aggiunto è un account locale, non è necessaria alcuna credenziale.</span><span class="sxs-lookup"><span data-stu-id="d0481-131">If the member added is a local account, then no credential is necessary.</span></span> <span data-ttu-id="d0481-132">Se la risorsa `Group` aggiunge un account di dominio al gruppo locale, è necessaria una credenziale.</span><span class="sxs-lookup"><span data-stu-id="d0481-132">If the `Group` resource adds a domain account to the local group, then a credential is necessary.</span></span>

<span data-ttu-id="d0481-133">Le query anonime in Active Directory non sono consentite.</span><span class="sxs-lookup"><span data-stu-id="d0481-133">Anonymous queries to Active Directory are not allowed.</span></span> <span data-ttu-id="d0481-134">La proprietà `Credential` della risorsa `Group` corrisponde all'account di dominio usato per eseguire query in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d0481-134">The `Credential` property of the `Group` resource is the domain account used to query Active Directory.</span></span> <span data-ttu-id="d0481-135">Per quasi tutti gli scopi può trattarsi di un account utente generico, perché per impostazione predefinita gli utenti possono *leggere* la maggior parte degli oggetti in Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d0481-135">For most purposes this could be a generic user account, because by default users can *read* most of the objects in Active Directory.</span></span>

## <a name="example-configuration"></a><span data-ttu-id="d0481-136">Configurazione di esempio</span><span class="sxs-lookup"><span data-stu-id="d0481-136">Example Configuration</span></span>

<span data-ttu-id="d0481-137">Il codice di esempio seguente usa DSC per immettere un utente di dominio in un gruppo locale:</span><span class="sxs-lookup"><span data-stu-id="d0481-137">The following example code uses DSC to populate a local group with a domain user:</span></span>

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

<span data-ttu-id="d0481-138">Questo codice genera un messaggio di errore e uno di avviso:</span><span class="sxs-lookup"><span data-stu-id="d0481-138">This code generates both an error and warning message:</span></span>

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

<span data-ttu-id="d0481-139">Questo esempio include due problemi:</span><span class="sxs-lookup"><span data-stu-id="d0481-139">This example has two issues:</span></span>

1. <span data-ttu-id="d0481-140">Un errore indica che le password di testo semplice non sono consigliate</span><span class="sxs-lookup"><span data-stu-id="d0481-140">An error explains that plain text passwords are not recommended</span></span>
2. <span data-ttu-id="d0481-141">Un avviso sconsiglia l'uso di una credenziale di dominio</span><span class="sxs-lookup"><span data-stu-id="d0481-141">A warning advises against using a domain credential</span></span>

<span data-ttu-id="d0481-142">I flag **PSDSCAllowPlainTextPassword** e **PSDSCAllowDomainUser** eliminano l'errore e l'avviso che informano l'utente dei rischi coinvolti.</span><span class="sxs-lookup"><span data-stu-id="d0481-142">The flags **PSDSCAllowPlainTextPassword** and **PSDSCAllowDomainUser** suppress the error and warning informing the user of the risk involved.</span></span>

## <a name="psdscallowplaintextpassword"></a><span data-ttu-id="d0481-143">PSDSCAllowPlainTextPassword</span><span class="sxs-lookup"><span data-stu-id="d0481-143">PSDSCAllowPlainTextPassword</span></span>

<span data-ttu-id="d0481-144">Il primo messaggio di errore contiene un URL con la documentazione.</span><span class="sxs-lookup"><span data-stu-id="d0481-144">The first error message has a URL with documentation.</span></span> <span data-ttu-id="d0481-145">Il collegamento descrive come crittografare le password usando una struttura [ConfigurationData](./configData.md) e un certificato.</span><span class="sxs-lookup"><span data-stu-id="d0481-145">This link explains how to encrypt passwords using a [ConfigurationData](./configData.md) structure and a certificate.</span></span> <span data-ttu-id="d0481-146">Per altre informazioni sui certificati e su DSC, [leggere questo post](https://aka.ms/certs4dsc).</span><span class="sxs-lookup"><span data-stu-id="d0481-146">For more information on certificates and DSC [read this post](https://aka.ms/certs4dsc).</span></span>

<span data-ttu-id="d0481-147">Per forzare una password di testo semplice, la risorsa richiede la presenza della parola chiave `PsDscAllowPlainTextPassword` nella sezione dei dati di configurazione, nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d0481-147">To force a plain text password, the resource requires the `PsDscAllowPlainTextPassword` keyword in the configuration data section as follows:</span></span>

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

### <a name="localhostmof"></a><span data-ttu-id="d0481-148">localhost.mof</span><span class="sxs-lookup"><span data-stu-id="d0481-148">localhost.mof</span></span>

<span data-ttu-id="d0481-149">Il flag **PSDSCAllowPlainTextPassword** richiede che l'utente accetti il rischio correlato all'archiviazione delle password in testo normale in un file MOF.</span><span class="sxs-lookup"><span data-stu-id="d0481-149">The **PSDSCAllowPlainTextPassword** flag requires that the user acknowledge the risk of storing plain text passwords in a MOF file.</span></span> <span data-ttu-id="d0481-150">Nel file MOF generato, anche se è stato usato un oggetto **PSCredential** contenente una **SecureString**, le password vengono comunque visualizzate come testo normale.</span><span class="sxs-lookup"><span data-stu-id="d0481-150">In the generated MOF file, even though a **PSCredential** object containing a **SecureString** was used, the passwords still appear as plain text.</span></span> <span data-ttu-id="d0481-151">Questa è l'unica volta in cui vengono esposte le credenziali.</span><span class="sxs-lookup"><span data-stu-id="d0481-151">This is the only time the credentials are exposed.</span></span> <span data-ttu-id="d0481-152">Chiunque riesce ad accedere a questo file MOF ottiene l'accesso anche all'account amministratore.</span><span class="sxs-lookup"><span data-stu-id="d0481-152">Gaining access to this MOF file gives anyone access to the Administrator account.</span></span>

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

### <a name="credentials-in-transit-and-at-rest"></a><span data-ttu-id="d0481-153">Credenziali in transito e inattive</span><span class="sxs-lookup"><span data-stu-id="d0481-153">Credentials in transit and at rest</span></span>

- <span data-ttu-id="d0481-154">Il flag **PSDscAllowPlainTextPassword** consente la compilazione di file MOF che contengono password come testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="d0481-154">The **PSDscAllowPlainTextPassword** flag allows the compilation of MOF files that contain passwords in clear text.</span></span> <span data-ttu-id="d0481-155">Adottare le necessarie precauzioni quando si archiviano file MOF che contengono password come testo non crittografato.</span><span class="sxs-lookup"><span data-stu-id="d0481-155">Take precautions when storing MOF files containing clear text passwords.</span></span>
- <span data-ttu-id="d0481-156">Quando il file MOF viene recapitato a un nodo in modalità **push**, WinRM crittografa la comunicazione per proteggere la password come testo non crittografato, a meno che non si ignori l'impostazione predefinita con il parametro **AllowUnencrypted**.</span><span class="sxs-lookup"><span data-stu-id="d0481-156">When the MOF file is delivered to a Node in **Push** mode, WinRM encrypts the communication to protect the clear text password unless you override the default with the **AllowUnencrypted** parameter.</span></span>
  - <span data-ttu-id="d0481-157">La crittografia del file MOF con un certificato protegge il file MOF nello stato inattivo prima dell'applicazione a un nodo.</span><span class="sxs-lookup"><span data-stu-id="d0481-157">Encrypting the MOF with a certificate protects the MOF file at rest before it has been applied to a node.</span></span>
- <span data-ttu-id="d0481-158">Nella modalità **pull** è possibile configurare il server di pull Windows per usare HTTPS per crittografare il traffico tramite il protocollo specificato in Internet Information Server.</span><span class="sxs-lookup"><span data-stu-id="d0481-158">In **Pull** mode, you can configure Windows pull server to use HTTPS to encrypt traffic using the protocol specified in Internet Information Server.</span></span> <span data-ttu-id="d0481-159">Per altre informazioni, vedere gli articoli [Configurazione di un client di pull DSC](../pull-server/pullclient.md) e [Protezione del file MOF con certificati](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="d0481-159">For more information, see the articles [Setting up a DSC pull client](../pull-server/pullclient.md) and [Securing MOF files with Certificates](../pull-server/secureMOF.md).</span></span>
  - <span data-ttu-id="d0481-160">Nel servizio di [configurazione dello stato di Automazione di Azure](/azure/automation/automation-dsc-overview), il traffico pull viene sempre crittografato.</span><span class="sxs-lookup"><span data-stu-id="d0481-160">In the [Azure Automation State Configuration](/azure/automation/automation-dsc-overview) service, Pull traffic is always encrypted.</span></span>
- <span data-ttu-id="d0481-161">Nel nodo i file MOF vengono crittografati nello stato inattivo a partire da PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="d0481-161">On the Node, MOF files are encrypted at rest Beginning in PowerShell 5.0.</span></span>
  - <span data-ttu-id="d0481-162">In PowerShell 4.0 i file MOF non vengono decrittografati nello stato inattivo a meno che non vengano crittografati con un certificato quando ne viene eseguito il push o pull sul nodo.</span><span class="sxs-lookup"><span data-stu-id="d0481-162">In PowerShell 4.0 MOF files are unencrypted at rest unless they are encrypted with a certificate when they pushed or pulled to the Node.</span></span>

<span data-ttu-id="d0481-163">**Microsoft consiglia di evitare password di testo semplice, che possono provocare rischi significativi per la sicurezza.**</span><span class="sxs-lookup"><span data-stu-id="d0481-163">**Microsoft advises to avoid plain text passwords due to the significant security risk.**</span></span>

## <a name="domain-credentials"></a><span data-ttu-id="d0481-164">Credenziali del dominio</span><span class="sxs-lookup"><span data-stu-id="d0481-164">Domain Credentials</span></span>

<span data-ttu-id="d0481-165">Una nuova esecuzione dello script di configurazione di esempio (con o senza crittografia) genera comunque l'avviso che sconsiglia l'uso di un account di dominio per una credenziale.</span><span class="sxs-lookup"><span data-stu-id="d0481-165">Running the example configuration script again (with or without encryption), still generates the warning that using a domain account for a credential is not recommended.</span></span> <span data-ttu-id="d0481-166">L'uso di un account locale elimina la potenziale esposizione delle credenziali di dominio, che potrebbero essere usate in altri server.</span><span class="sxs-lookup"><span data-stu-id="d0481-166">Using a local account eliminates potential exposure of domain credentials that could be used on other servers.</span></span>

<span data-ttu-id="d0481-167">**Quando si usano credenziali con risorse DSC, se possibile preferire un account locale a un account di dominio.**</span><span class="sxs-lookup"><span data-stu-id="d0481-167">**When using credentials with DSC resources, prefer a local account over a domain account when possible.**</span></span>

<span data-ttu-id="d0481-168">Se la proprietà `Username` della credenziale contiene un carattere '\\' o '\@', DSC la considera un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="d0481-168">If there is a '\\' or '\@' in the `Username` property of the credential, then DSC will treat it as a domain account.</span></span> <span data-ttu-id="d0481-169">Un'eccezione riguarda "localhost", "127.0.0.1" e "::1" nella parte del dominio del nome utente.</span><span class="sxs-lookup"><span data-stu-id="d0481-169">There is an exception for "localhost", "127.0.0.1", and "::1" in the domain portion of the user name.</span></span>

## <a name="psdscallowdomainuser"></a><span data-ttu-id="d0481-170">PSDscAllowDomainUser</span><span class="sxs-lookup"><span data-stu-id="d0481-170">PSDscAllowDomainUser</span></span>

<span data-ttu-id="d0481-171">Nell'esempio di risorsa `Group` DSC precedente per l'esecuzione di query su un dominio Active Directory *è necessario* un account di dominio.</span><span class="sxs-lookup"><span data-stu-id="d0481-171">In the DSC `Group` resource example above, querying an Active Directory domain *requires* a domain account.</span></span> <span data-ttu-id="d0481-172">In questo caso, aggiungere la proprietà `PSDscAllowDomainUser` al blocco `ConfigurationData` nel modo seguente:</span><span class="sxs-lookup"><span data-stu-id="d0481-172">In this case add the `PSDscAllowDomainUser` property to the `ConfigurationData` block as follows:</span></span>

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

<span data-ttu-id="d0481-173">Lo script di configurazione genera ora il file MOF senza errori o avvisi.</span><span class="sxs-lookup"><span data-stu-id="d0481-173">Now the configuration script will generate the MOF file with no errors or warnings.</span></span>
