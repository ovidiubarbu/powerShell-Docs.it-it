---
ms.date: 04/11/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazione di un server di pull SMB DSC
ms.openlocfilehash: 722120369df9ff383a02c69111e0bacf2e2e76a5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678051"
---
# <a name="setting-up-a-dsc-smb-pull-server"></a><span data-ttu-id="63aed-103">Configurazione di un server di pull SMB DSC</span><span class="sxs-lookup"><span data-stu-id="63aed-103">Setting up a DSC SMB pull server</span></span>

<span data-ttu-id="63aed-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="63aed-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

> [!IMPORTANT]
> <span data-ttu-id="63aed-105">Il server di pull (funzionalità di Windows *servizio DSC*) è un componente supportato di Windows Server, tuttavia non si prevede di offrire nuove caratteristiche o funzionalità.</span><span class="sxs-lookup"><span data-stu-id="63aed-105">The Pull Server (Windows Feature *DSC-Service*) is a supported component of Windows Server however there are no plans to offer new features or capabilities.</span></span> <span data-ttu-id="63aed-106">È consigliabile avviare la transizione dei client gestiti ad [Automation DSC per Azure](/azure/automation/automation-dsc-getting-started) (include funzionalità superiori al server di pull in Windows Server) o a una delle soluzioni della community riportate [qui](pullserver.md#community-solutions-for-pull-service).</span><span class="sxs-lookup"><span data-stu-id="63aed-106">It is recommended to begin transitioning managed clients to [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (includes features beyond Pull Server on Windows Server) or one of the community solutions listed [here](pullserver.md#community-solutions-for-pull-service).</span></span>

<span data-ttu-id="63aed-107">Un server di pull [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) DSC è un computer che ospita condivisioni file SMB che rendono disponibili i file di configurazione DSC e le risorse DSC ai nodi di destinazione quando tali nodi li richiedono.</span><span class="sxs-lookup"><span data-stu-id="63aed-107">A DSC [SMB](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831795(v=ws.11)) pull server is a computer hosting SMB file shares that make DSC configuration files and DSC resources available to target nodes when those nodes ask for them.</span></span>

<span data-ttu-id="63aed-108">Per usare un server di pull SMB per DSC, è necessario:</span><span class="sxs-lookup"><span data-stu-id="63aed-108">To use an SMB pull server for DSC, you have to:</span></span>

- <span data-ttu-id="63aed-109">Configurare una condivisione file SMB in un server che esegue PowerShell 4.0 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="63aed-109">Set up an SMB file share on a server running PowerShell 4.0 or higher</span></span>
- <span data-ttu-id="63aed-110">Configurare un client che esegue PowerShell 4.0 o versione successiva per effettuare il pull da tale condivisione SMB</span><span class="sxs-lookup"><span data-stu-id="63aed-110">Configure a client running PowerShell 4.0 or higher to pull from that SMB share</span></span>

## <a name="using-the-xsmbshare-resource-to-create-an-smb-file-share"></a><span data-ttu-id="63aed-111">Uso della la risorsa xSmbShare per creare una condivisione file SMB</span><span class="sxs-lookup"><span data-stu-id="63aed-111">Using the xSmbShare resource to create an SMB file share</span></span>

<span data-ttu-id="63aed-112">Esistono diversi modi per configurare una condivisione file SMB, ma ecco come è possibile farlo tramite DSC.</span><span class="sxs-lookup"><span data-stu-id="63aed-112">There are a number of ways to set up an SMB file share, but let's look at how you can do this by using DSC.</span></span>

### <a name="install-the-xsmbshare-resource"></a><span data-ttu-id="63aed-113">Installare la risorsa xSmbShare</span><span class="sxs-lookup"><span data-stu-id="63aed-113">Install the xSmbShare resource</span></span>

<span data-ttu-id="63aed-114">Chiamare il cmdlet [Install-Module](/powershell/module/PowershellGet/Install-Module) per installare il modulo **xSmbShare**.</span><span class="sxs-lookup"><span data-stu-id="63aed-114">Call the [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet to install the **xSmbShare** module.</span></span>

> [!NOTE]
> <span data-ttu-id="63aed-115">Il cmdlet `Install-Module` è incluso nel modulo **PowerShellGet**, disponibile in PowerShell 5.0.</span><span class="sxs-lookup"><span data-stu-id="63aed-115">`Install-Module` is included in the **PowerShellGet** module, which is included in PowerShell 5.0.</span></span> <span data-ttu-id="63aed-116">È possibile scaricare il modulo **PowerShellGet** per PowerShell 3.0 e 4.0 dalla pagina dell'[anteprima dei moduli PackageManagement di PowerShell](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span><span class="sxs-lookup"><span data-stu-id="63aed-116">You can download the **PowerShellGet** module for PowerShell 3.0 and 4.0 at [PackageManagement PowerShell Modules Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).</span></span>
> <span data-ttu-id="63aed-117">**xSmbShare** contiene la risorsa DSC **xSmbShare**, che può essere usata per creare una condivisione file SMB.</span><span class="sxs-lookup"><span data-stu-id="63aed-117">The **xSmbShare** contains the DSC resource **xSmbShare**, which can be used to create an SMB file share.</span></span>

### <a name="create-the-directory-and-file-share"></a><span data-ttu-id="63aed-118">Creare la directory e la condivisione file</span><span class="sxs-lookup"><span data-stu-id="63aed-118">Create the directory and file share</span></span>

<span data-ttu-id="63aed-119">La configurazione seguente usa la risorsa **File** per creare la directory per la condivisione e la risorsa **xSmbShare** per configurare la condivisione SMB:</span><span class="sxs-lookup"><span data-stu-id="63aed-119">The following configuration uses the **File** resource to create the directory for the share and the **xSmbShare** resource to set up the SMB share:</span></span>

```powershell
Configuration SmbShare
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'admininstrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

<span data-ttu-id="63aed-120">La configurazione crea la directory `C:\DscSmbShare`se non esiste già e quindi usa tale directory come una condivisione file SMB.</span><span class="sxs-lookup"><span data-stu-id="63aed-120">The configuration creates the directory `C:\DscSmbShare`, if it doesn't already exist, and then uses that directory as an SMB file share.</span></span> <span data-ttu-id="63aed-121">**FullAccess** dovrebbe essere concessa a qualsiasi account che è necessario scrivere o eliminare dalla condivisione file.</span><span class="sxs-lookup"><span data-stu-id="63aed-121">**FullAccess** should be given to any account that needs to write to or delete from the file share.</span></span> <span data-ttu-id="63aed-122">**ReadAccess** deve essere concessa a qualsiasi nodo client che ottengono le configurazioni e/o le risorse DSC dalla condivisione.</span><span class="sxs-lookup"><span data-stu-id="63aed-122">**ReadAccess** must be given to any client nodes that get configurations and/or DSC resources from the share.</span></span>

> [!NOTE]
> <span data-ttu-id="63aed-123">DSC viene eseguito come account di sistema per impostazione predefinita, in modo che il computer stesso deve avere accesso alla condivisione.</span><span class="sxs-lookup"><span data-stu-id="63aed-123">DSC runs as the system account by default, so the computer itself must have access to the share.</span></span>

### <a name="give-file-system-access-to-the-pull-client"></a><span data-ttu-id="63aed-124">Consentire l'accesso al file system al client di pull</span><span class="sxs-lookup"><span data-stu-id="63aed-124">Give file system access to the pull client</span></span>

<span data-ttu-id="63aed-125">L'assegnazione di **ReadAccess** a un nodo client consente a tale nodo di accedere alla condivisione SMB, ma non a file o cartelle al suo interno.</span><span class="sxs-lookup"><span data-stu-id="63aed-125">Giving **ReadAccess** to a client node allows that node to access the SMB share, but not to files or folders within that share.</span></span> <span data-ttu-id="63aed-126">È necessario concedere esplicitamente l'accesso di nodi per la cartella di condivisione SMB e le sottocartelle.</span><span class="sxs-lookup"><span data-stu-id="63aed-126">You have to explicitly grant client nodes access to the SMB share folder and subfolders.</span></span> <span data-ttu-id="63aed-127">DSC consente tale operazione usando la risorsa **cNtfsPermissionEntry**, contenuta nel modulo [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0).</span><span class="sxs-lookup"><span data-stu-id="63aed-127">We can do this with DSC by adding using the **cNtfsPermissionEntry** resource, which is contained in the [CNtfsAccessControl](https://www.powershellgallery.com/packages/cNtfsAccessControl/1.2.0) module.</span></span> <span data-ttu-id="63aed-128">La configurazione seguente aggiunge un blocco **cNtfsPermissionEntry** che concede l'accesso ReadAndExecute al client di pull:</span><span class="sxs-lookup"><span data-stu-id="63aed-128">The following configuration adds a **cNtfsPermissionEntry** block that grants ReadAndExecute access to the pull client:</span></span>

```powershell
Configuration DSCSMB
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Import-DscResource -ModuleName xSmbShare
    Import-DscResource -ModuleName cNtfsAccessControl

    Node localhost
    {

        File CreateFolder
        {
            DestinationPath = 'C:\DscSmbShare'
            Type = 'Directory'
            Ensure = 'Present'
        }

        xSMBShare CreateShare
        {
            Name = 'DscSmbShare'
            Path = 'C:\DscSmbShare'
            FullAccess = 'administrator'
            ReadAccess = 'myDomain\Contoso-Server$'
            FolderEnumerationMode = 'AccessBased'
            Ensure = 'Present'
            DependsOn = '[File]CreateFolder'
        }

        cNtfsPermissionEntry PermissionSet1
        {
            Ensure = 'Present'
            Path = 'C:\DscSmbShare'
            Principal = 'myDomain\Contoso-Server$'
            AccessControlInformation = @(
                cNtfsAccessControlInformation
                {
                    AccessControlType = 'Allow'
                    FileSystemRights = 'ReadAndExecute'
                    Inheritance = 'ThisFolderSubfoldersAndFiles'
                    NoPropagateInherit = $false
                }
            )
            DependsOn = '[File]CreateFolder'
        }
    }
}
```

## <a name="placing-configurations-and-resources"></a><span data-ttu-id="63aed-129">Inserimento di configurazioni e risorse</span><span class="sxs-lookup"><span data-stu-id="63aed-129">Placing configurations and resources</span></span>

<span data-ttu-id="63aed-130">Salvare nella condivisione SMB tutti i file MOF di configurazione e/o le risorse DSC che si vuole siano disponibili per il pull dai nodi client.</span><span class="sxs-lookup"><span data-stu-id="63aed-130">Save any configuration MOF files and/or DSC resources that you want client nodes to pull in the SMB share folder.</span></span>

<span data-ttu-id="63aed-131">Qualsiasi file MOF di configurazione deve essere denominato *ConfigurationID.mof*, dove *ConfigurationID* è il valore della proprietà **ConfigurationID** di Gestione configurazione locale del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="63aed-131">Any configuration MOF file must be named *ConfigurationID*.mof, where *ConfigurationID* is the value of the **ConfigurationID** property of the target node's LCM.</span></span> <span data-ttu-id="63aed-132">Per altre informazioni sulla configurazione di client di pull, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-132">For more information about setting up pull clients, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="63aed-133">Se si usa un server di pull SMB, è necessario usare gli ID di configurazione.</span><span class="sxs-lookup"><span data-stu-id="63aed-133">You must use configuration IDs if you are using an SMB pull server.</span></span> <span data-ttu-id="63aed-134">I nomi di configurazione non sono supportati per SMB.</span><span class="sxs-lookup"><span data-stu-id="63aed-134">Configuration names are not supported for SMB.</span></span>

<span data-ttu-id="63aed-135">Ogni modulo di risorse deve essere compresso e denominato in base alla convenzione seguente `{Module Name}_{Module Version}.zip`.</span><span class="sxs-lookup"><span data-stu-id="63aed-135">Each resource module needs to be zipped and named according to the following pattern `{Module Name}_{Module Version}.zip`.</span></span> <span data-ttu-id="63aed-136">Ad esempio, un modulo denominato xWebAdminstration con versione 3.1.2.0 verrebbe denominato 'xWebAdministration_3.2.1.0.zip'.</span><span class="sxs-lookup"><span data-stu-id="63aed-136">For example, a module named xWebAdminstration with a module version of 3.1.2.0 would be named 'xWebAdministration_3.2.1.0.zip'.</span></span> <span data-ttu-id="63aed-137">Ogni versione di un modulo deve essere contenuta in un unico file ZIP.</span><span class="sxs-lookup"><span data-stu-id="63aed-137">Each version of a module must be contained in a single zip file.</span></span> <span data-ttu-id="63aed-138">Versioni distinte di un modulo in un file zip non sono supportate.</span><span class="sxs-lookup"><span data-stu-id="63aed-138">Separate versions of a module in a zip file are not supported.</span></span> <span data-ttu-id="63aed-139">Prima di creare un pacchetto i moduli delle risorse DSC per l'uso con server di pull, è necessario apportare una piccola modifica alla struttura di directory.</span><span class="sxs-lookup"><span data-stu-id="63aed-139">Before packaging up DSC resource modules for use with pull server, you need to make a small change to the directory structure.</span></span>

<span data-ttu-id="63aed-140">Il formato predefinito dei moduli contenenti risorse DSC in WMF 5.0 è `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="63aed-140">The default format of modules containing DSC resource in WMF 5.0 is `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.</span></span>

<span data-ttu-id="63aed-141">Prima creare il pacchetto per il server di pull, rimuovere semplicemente la cartella `{Module version}` in modo il percorso diventi `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span><span class="sxs-lookup"><span data-stu-id="63aed-141">Before packaging up for the pull server simply remove the `{Module version}` folder so the path becomes `{Module Folder}\DscResources\{DSC Resource Folder}\`.</span></span> <span data-ttu-id="63aed-142">Con questa modifica, comprimere la cartella come descritto in precedenza e collocare i file ZIP nella cartella di condivisione SMB.</span><span class="sxs-lookup"><span data-stu-id="63aed-142">With this change, zip the folder as described above and place these zip files in the SMB share folder.</span></span>

## <a name="creating-the-mof-checksum"></a><span data-ttu-id="63aed-143">Creazione del checksum per il file MOF</span><span class="sxs-lookup"><span data-stu-id="63aed-143">Creating the MOF checksum</span></span>

<span data-ttu-id="63aed-144">Un file MOF di configurazione deve essere associato a un file di checksum in modo che Gestione configurazione locale in un nodo di destinazione possa convalidare la configurazione.</span><span class="sxs-lookup"><span data-stu-id="63aed-144">A configuration MOF file needs to be paired with a checksum file so that an LCM on a target node can validate the configuration.</span></span>
<span data-ttu-id="63aed-145">Per creare un checksum, chiamare il cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum).</span><span class="sxs-lookup"><span data-stu-id="63aed-145">To create a checksum, call the [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet.</span></span> <span data-ttu-id="63aed-146">Il cmdlet accetta un parametro `Path` che specifica la cartella in cui si trova il file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="63aed-146">The cmdlet takes a `Path` parameter that specifies the folder where the configuration MOF is located.</span></span> <span data-ttu-id="63aed-147">Il cmdlet crea un file di checksum denominato `ConfigurationMOFName.mof.checksum`, in cui `ConfigurationMOFName` è il nome del file MOF di configurazione.</span><span class="sxs-lookup"><span data-stu-id="63aed-147">The cmdlet creates a checksum file named `ConfigurationMOFName.mof.checksum`, where `ConfigurationMOFName` is the name of the configuration mof file.</span></span>
<span data-ttu-id="63aed-148">Se nella cartella specificata sono presenti più file MOF di configurazione, viene creato un checksum per ogni configurazione nella cartella.</span><span class="sxs-lookup"><span data-stu-id="63aed-148">If there are more than one configuration MOF files in the specified folder, a checksum is created for each configuration in the folder.</span></span>

<span data-ttu-id="63aed-149">Il file di checksum deve essere presente nella stessa directory del file MOF di configurazione (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` per impostazione predefinita) e avere lo stesso nome, con estensione `.checksum`.</span><span class="sxs-lookup"><span data-stu-id="63aed-149">The checksum file must be present in the same directory as the configuration MOF file (`$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration` by default), and have the same name with the `.checksum` extension appended.</span></span>

> [!NOTE]
> <span data-ttu-id="63aed-150">Se si modifica il file MOF di configurazione in qualsiasi modo, è anche necessario ricreare il file di checksum.</span><span class="sxs-lookup"><span data-stu-id="63aed-150">If you change the configuration MOF file in any way, you must also recreate the checksum file.</span></span>

## <a name="setting-up-a-pull-client-for-smb"></a><span data-ttu-id="63aed-151">Impostazione di un client di pull per SMB</span><span class="sxs-lookup"><span data-stu-id="63aed-151">Setting up a pull client for SMB</span></span>

<span data-ttu-id="63aed-152">Per impostare un client che esegue il pull di configurazioni e/o di risorse da una condivisione SMB, configurare Gestione configurazione locale con i blocchi **ConfigurationRepositoryShare** e **ResourceRepositoryShare** che specificano la condivisione da cui eseguire il pull di configurazioni e risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="63aed-152">To set up a client that pulls configurations and/or resources from an SMB share, you configure the client's Local Configuration Manager (LCM) with **ConfigurationRepositoryShare** and **ResourceRepositoryShare** blocks that specify the share from which to pull configurations and DSC resources.</span></span>

<span data-ttu-id="63aed-153">Per altre informazioni sulla configurazione di Gestione configurazione locale, vedere [Configurazione di un client di pull usando un ID configurazione](pullClientConfigID.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-153">For more information about configuring the LCM, see [Setting up a pull client using configuration ID](pullClientConfigID.md).</span></span>

> [!NOTE]
> <span data-ttu-id="63aed-154">Per semplicità, questo esempio usa **PSDscAllowPlainTextPassword** per consentire il passaggio di una password non crittografata al parametro **Credential**.</span><span class="sxs-lookup"><span data-stu-id="63aed-154">For simplicity, this example uses the **PSDscAllowPlainTextPassword** to allow passing a plaintext password to the **Credential** parameter.</span></span> <span data-ttu-id="63aed-155">Per informazioni sul passaggio di credenziali in modo più sicuro, vedere [Opzioni delle credenziali nei dati di configurazione](../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-155">For information about passing credentials more securely, see [Credentials Options in Configuration Data](../configurations/configDataCredentials.md).</span></span>
>
> <span data-ttu-id="63aed-156">È **necessario** specificare **ConfigurationID** nel blocco **Impostazioni** di una metaconfigurazione per un server di pull SMB, anche se si esegue solo il pull di risorse.</span><span class="sxs-lookup"><span data-stu-id="63aed-156">You **MUST** specify a **ConfigurationID** in the **Settings** block of a metaconfiguration for an SMB pull server, even if you are only pulling resources.</span></span>

```powershell
$secpasswd = ConvertTo-SecureString “Pass1Word” -AsPlainText -Force
$mycreds = New-Object System.Management.Automation.PSCredential (“TestUser”, $secpasswd)

[DSCLocalConfigurationManager()]
configuration SmbCredTest
{
    Node $AllNodes.NodeName
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
            ConfigurationID    = '16db7357-9083-4806-a80c-ebbaf4acd6c1'
        }

         ConfigurationRepositoryShare SmbConfigShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds
        }

        ResourceRepositoryShare SmbResourceShare
        {
            SourcePath = '\\WIN-E0TRU6U11B1\DscSmbShare'
            Credential = $mycreds

        }
    }
}

$ConfigurationData = @{
    AllNodes = @(
        @{
            #the "*" means "all nodes named in ConfigData" so we don't have to repeat ourselves
            NodeName="localhost"
            PSDscAllowPlainTextPassword = $true
        })
}
```

## <a name="acknowledgements"></a><span data-ttu-id="63aed-157">Riconoscimenti</span><span class="sxs-lookup"><span data-stu-id="63aed-157">Acknowledgements</span></span>

<span data-ttu-id="63aed-158">Ringraziamento particolare a persone indicate di seguito:</span><span class="sxs-lookup"><span data-stu-id="63aed-158">Special thanks to the following individuals:</span></span>

- <span data-ttu-id="63aed-159">Mike F. Robbins, i cui post sull'uso di SMB per DSC hanno aiutato a comporre il contenuto in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="63aed-159">Mike F. Robbins, whose posts on using SMB for DSC helped inform the content in this topic.</span></span> <span data-ttu-id="63aed-160">Il suo blog è [Mike F Robbins](http://mikefrobbins.com/).</span><span class="sxs-lookup"><span data-stu-id="63aed-160">His blog is at [Mike F Robbins](http://mikefrobbins.com/).</span></span>
- <span data-ttu-id="63aed-161">Serge Nikalaichyk, che ha creato il modulo **cNtfsAccessControl**.</span><span class="sxs-lookup"><span data-stu-id="63aed-161">Serge Nikalaichyk, who authored the **cNtfsAccessControl** module.</span></span> <span data-ttu-id="63aed-162">L'origine per questo modulo è in [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span><span class="sxs-lookup"><span data-stu-id="63aed-162">The source for this module is at [cNtfsAccessControl](https://github.com/SNikalaichyk/cNtfsAccessControl).</span></span>

## <a name="see-also"></a><span data-ttu-id="63aed-163">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="63aed-163">See also</span></span>

<span data-ttu-id="63aed-164">[Panoramica di Windows PowerShell DSC (Desired State Configuration)](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="63aed-164">[Windows PowerShell Desired State Configuration Overview](../overview/overview.md)</span></span>

[<span data-ttu-id="63aed-165">Applicazione delle configurazioni</span><span class="sxs-lookup"><span data-stu-id="63aed-165">Enacting configurations</span></span>](enactingConfigurations.md)

[<span data-ttu-id="63aed-166">Configurazione di un client di pull usando un ID configurazione</span><span class="sxs-lookup"><span data-stu-id="63aed-166">Setting up a pull client using configuration ID</span></span>](pullClientConfigID.md)
