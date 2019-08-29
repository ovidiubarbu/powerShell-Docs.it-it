---
ms.date: 08/15/2019
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration) per Windows
ms.openlocfilehash: a4f9db481afda65fc4ac5e553230dbba3037ac9a
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988871"
---
# <a name="get-started-with-desired-state-configuration-dsc-for-windows"></a><span data-ttu-id="77201-103">Introduzione a DSC (Desired State Configuration) per Windows</span><span class="sxs-lookup"><span data-stu-id="77201-103">Get started with Desired State Configuration (DSC) for Windows</span></span>

<span data-ttu-id="77201-104">Questo argomento illustra come iniziare a usare PowerShell DSC (Desired State Configuration) per Windows.</span><span class="sxs-lookup"><span data-stu-id="77201-104">This topic explains how to get started using PowerShell Desired State Configuration (DSC) for Windows.</span></span>
<span data-ttu-id="77201-105">Per informazioni generali su DSC, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="77201-105">For general information about DSC, see [Get Started with Windows PowerShell Desired State Configuration](../overview/overview.md).</span></span>

## <a name="supported-windows-operation-system-versions"></a><span data-ttu-id="77201-106">Versioni del sistema operativo Windows supportate</span><span class="sxs-lookup"><span data-stu-id="77201-106">Supported Windows operation system versions</span></span>

<span data-ttu-id="77201-107">Sono supportate le versioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="77201-107">The following versions are supported:</span></span>

- <span data-ttu-id="77201-108">Windows Server 2019</span><span class="sxs-lookup"><span data-stu-id="77201-108">Windows Server 2019</span></span>
- <span data-ttu-id="77201-109">Windows Server 2016</span><span class="sxs-lookup"><span data-stu-id="77201-109">Windows Server 2016</span></span>
- <span data-ttu-id="77201-110">Windows Server 2012 R2</span><span class="sxs-lookup"><span data-stu-id="77201-110">Windows Server 2012R2</span></span>
- <span data-ttu-id="77201-111">Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="77201-111">Windows Server 2012</span></span>
- <span data-ttu-id="77201-112">Windows Server 2008 R2 SP1</span><span class="sxs-lookup"><span data-stu-id="77201-112">Windows Server 2008 R2 SP1</span></span>
- <span data-ttu-id="77201-113">Windows 10</span><span class="sxs-lookup"><span data-stu-id="77201-113">Windows 10</span></span>
- <span data-ttu-id="77201-114">Windows 8.1</span><span class="sxs-lookup"><span data-stu-id="77201-114">Windows 8.1</span></span>
- <span data-ttu-id="77201-115">Windows 7</span><span class="sxs-lookup"><span data-stu-id="77201-115">Windows 7</span></span>

<span data-ttu-id="77201-116">Lo SKU del prodotto autonomo [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) non contiene un'implementazione di DSC, di conseguenza non può essere gestito da PowerShell DSC o da Configurazione stato di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="77201-116">The [Microsoft Hyper-V Server](/windows-server/virtualization/hyper-v/hyper-v-server-2016) standalone product sku does not contain an implementation of Desired State Configuraion so it cannot be managed by PowerShell DSC or Azure Automation State Configuration.</span></span>

## <a name="installing-dsc"></a><span data-ttu-id="77201-117">Installazione di DSC</span><span class="sxs-lookup"><span data-stu-id="77201-117">Installing DSC</span></span>

<span data-ttu-id="77201-118">PowerShell DSC è incluso in Windows e viene aggiornato tramite Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="77201-118">PowerShell Desired State Configuration is included in Windows and updated through Windows Management Framework.</span></span>
<span data-ttu-id="77201-119">La versione più recente è [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span><span class="sxs-lookup"><span data-stu-id="77201-119">The latest version is [Windows Management Framework 5.1](https://www.microsoft.com/en-us/download/details.aspx?id=54616).</span></span>

> [!NOTE]
> <span data-ttu-id="77201-120">Non è necessario abilitare la funzionalità "DSC-Service" di Windows Server per gestire un computer con DSC.</span><span class="sxs-lookup"><span data-stu-id="77201-120">You do not need to enable the Windows Server feature 'DSC-Service' to manage a machine using DSC.</span></span>
> <span data-ttu-id="77201-121">Questa funzionalità è necessaria solo quando si crea un'istanza del server di pull Windows.</span><span class="sxs-lookup"><span data-stu-id="77201-121">That feature is only needed when building a Windows Pull Server instance.</span></span>

## <a name="using-dsc-for-windows"></a><span data-ttu-id="77201-122">Uso di DSC per Windows</span><span class="sxs-lookup"><span data-stu-id="77201-122">Using DSC for Windows</span></span>

<span data-ttu-id="77201-123">Le sezioni seguenti illustrano come creare ed eseguire configurazioni DSC nei computer Windows.</span><span class="sxs-lookup"><span data-stu-id="77201-123">The following sections explain how to create and run DSC configurations on Windows computers.</span></span>

### <a name="creating-a-configuration-mof-document"></a><span data-ttu-id="77201-124">Creazione di un documento MOF di configurazione</span><span class="sxs-lookup"><span data-stu-id="77201-124">Creating a configuration MOF document</span></span>

<span data-ttu-id="77201-125">Per creare una configurazione, si usa la parola chiave Configuration di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77201-125">The Windows PowerShell Configuration keyword is used to create a configuration.</span></span>
<span data-ttu-id="77201-126">I passaggi seguenti descrivono la creazione di un documento di configurazione con Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77201-126">The following steps describe the creation of a configuration document using Windows PowerShell.</span></span>

#### <a name="define-a-configuration-and-generate-the-configuration-document"></a><span data-ttu-id="77201-127">Definire una configurazione e generare il documento di configurazione:</span><span class="sxs-lookup"><span data-stu-id="77201-127">Define a configuration and generate the configuration document:</span></span>

```powershell
Configuration EnvironmentVariable_Path
{
    param ()

    Import-DscResource -ModuleName 'PSDscResources'

    Node localhost
    {
        Environment CreatePathEnvironmentVariable
        {
            Name = 'TestPathEnvironmentVariable'
            Value = 'TestValue'
            Ensure = 'Present'
            Path = $true
            Target = @('Process', 'Machine')
        }
    }
}

EnvironmentVariable_Path -OutputPath:"C:\EnvironmentVariable_Path"
```
#### <a name="install-a-module-containing-dsc-resources"></a><span data-ttu-id="77201-128">Installare un modulo contenente risorse DSC</span><span class="sxs-lookup"><span data-stu-id="77201-128">Install a module containing DSC resources</span></span>

<span data-ttu-id="77201-129">Windows PowerShell DSC (Desired State Configuration) include moduli predefiniti contenenti le risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="77201-129">Windows PowerShell Desired State Configuration includes built-in modules containing DSC resources.</span></span>
<span data-ttu-id="77201-130">È anche possibile caricare moduli da origini esterne, ad esempio PowerShell Gallery, usando i cmdlet di PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="77201-130">You can also load modules from external sources such as the PowerShell Gallery, using the PowerShellGet cmdlets.</span></span>

`Install-Module 'PSDscResources' -Verbose`

#### <a name="apply-the-configuration-to-the-machine"></a><span data-ttu-id="77201-131">Applicare la configurazione al computer</span><span class="sxs-lookup"><span data-stu-id="77201-131">Apply the configuration to the machine</span></span>

<span data-ttu-id="77201-132">È possibile applicare i documenti di configurazione (file MOF) al computer usando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="77201-132">Configuration documents (MOF files) can be applied to the machine using the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

`Start-DscConfiguration -Path 'C:\EnvironmentVariable_Path' -Wait -Verbose`

#### <a name="get-the-current-state-of-the-configuration"></a><span data-ttu-id="77201-133">Ottenere lo stato corrente della configurazione</span><span class="sxs-lookup"><span data-stu-id="77201-133">Get the current state of the configuration</span></span>

<span data-ttu-id="77201-134">Il cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) esegue una query per ottenere lo stato corrente del computer e restituisce i valori correnti per la configurazione.</span><span class="sxs-lookup"><span data-stu-id="77201-134">The [Get-DscConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet queries the current status of the machine and returns the current values for the configuration.</span></span>

`Get-DscConfiguration`

<span data-ttu-id="77201-135">Il cmdlet [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) restituisce la metaconfigurazione corrente applicata al computer.</span><span class="sxs-lookup"><span data-stu-id="77201-135">The [Get-DscLocalConfigurationManager](/powershell/module/psdesiredstateconfiguration/get-dscLocalConfigurationManager) cmdlet returns the current meta-configuration applied to the machine.</span></span>

`Get-DscLocalConfigurationManager`

#### <a name="remove-the-current-configuration-from-a-machine"></a><span data-ttu-id="77201-136">Rimuovere la configurazione corrente da un computer</span><span class="sxs-lookup"><span data-stu-id="77201-136">Remove the current configuration from a machine</span></span>

<span data-ttu-id="77201-137">[Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span><span class="sxs-lookup"><span data-stu-id="77201-137">The [Remove-DscConfigurationDocument](/powershell/module/psdesiredstateconfiguration/remove-dscconfigurationdocument)</span></span>

`Remove-DscConfigurationDocument -Stage Current -Verbose`

#### <a name="configure-settings-in-local-configuration-manager"></a><span data-ttu-id="77201-138">Configurare le impostazioni in Gestione configurazione locale</span><span class="sxs-lookup"><span data-stu-id="77201-138">Configure settings in Local Configuration Manager</span></span>

<span data-ttu-id="77201-139">Applicare un file MOF di metaconfigurazione al computer usando il cmdlet [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="77201-139">Apply a Meta Configuration MOF file to the machine using the [Set-DSCLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Set-DscLocalConfigurationManager) cmdlet.</span></span>
<span data-ttu-id="77201-140">Richiede il percorso del file MOF di metaconfigurazione.</span><span class="sxs-lookup"><span data-stu-id="77201-140">Requires the path to the Meta Configuration MOF.</span></span>

`Set-DSCLocalConfigurationManager -Path 'c:\metaconfig\localhost.meta.mof' -Verbose`

## <a name="windows-powershell-desired-state-configuration-log-files"></a><span data-ttu-id="77201-141">File di log di Windows PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="77201-141">Windows PowerShell Desired State Configuration log files</span></span>

<span data-ttu-id="77201-142">I log per DSC vengono scritti nel percorso `Microsoft-Windows-Dsc/Operational` di Registro eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="77201-142">Logs for DSC are written to Windows Event Log in the path `Microsoft-Windows-Dsc/Operational`.</span></span>
<span data-ttu-id="77201-143">È possibile abilitare altri log a scopo di debug attenendosi alla procedura descritta in [Dove sono i registri eventi DSC?](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span><span class="sxs-lookup"><span data-stu-id="77201-143">Additional logs for debugging purposes can be enabled following the steps in [Where Are DSC Event Logs](/powershell/dsc/troubleshooting/troubleshooting#where-are-dsc-event-logs).</span></span>
