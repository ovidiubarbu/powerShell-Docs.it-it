---
ms.date: 01/17/2019
keywords: dsc,powershell,configurazione,installazione
title: Riavviare un nodo
ms.openlocfilehash: 22c63fab9b6646f522f8531b46a43a94ff883552
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954028"
---
# <a name="reboot-a-node"></a><span data-ttu-id="c7d00-103">Riavviare un nodo</span><span class="sxs-lookup"><span data-stu-id="c7d00-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="c7d00-104">Questo argomento descrive come riavviare un nodo.</span><span class="sxs-lookup"><span data-stu-id="c7d00-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="c7d00-105">Per eseguire correttamente il riavvio è necessario configurare correttamente le impostazioni di Gestione configurazione locale **ActionAfterReboot** e **RebootNodeIfNeeded**.</span><span class="sxs-lookup"><span data-stu-id="c7d00-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="c7d00-106">Per informazioni sulle impostazioni di Gestione configurazione locale, vedere [Configurare Gestione configurazione locale](../managing-nodes/metaConfig.md) o [Configurare Gestione configurazione locale (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="c7d00-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="c7d00-107">I nodi possono essere riavviati all'interno di una risorsa tramite il flag `$global:DSCMachineStatus`.</span><span class="sxs-lookup"><span data-stu-id="c7d00-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="c7d00-108">L'impostazione del flag su `1` nella funzione `Set-TargetResource` forza la Gestione configurazione locale a riavviare direttamente il nodo dopo il metodo **Set** della risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="c7d00-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="c7d00-109">Con questo flag, la risorsa **PendingReboot** nel modulo di risorse DSC [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) rileva se un riavvio è in sospeso all'esterno di DSC.</span><span class="sxs-lookup"><span data-stu-id="c7d00-109">Using this flag, the **PendingReboot** resource in the [ComputerManagementDsc](https://github.com/PowerShell/ComputerManagementDsc) DSC Resource module detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="c7d00-110">Le [configurazioni](configurations.md) possono eseguire i passaggi che richiedono il riavvio del nodo,</span><span class="sxs-lookup"><span data-stu-id="c7d00-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="c7d00-111">tra cui:</span><span class="sxs-lookup"><span data-stu-id="c7d00-111">This could include things such as:</span></span>

- <span data-ttu-id="c7d00-112">Aggiornamenti di Windows</span><span class="sxs-lookup"><span data-stu-id="c7d00-112">Windows updates</span></span>
- <span data-ttu-id="c7d00-113">Installazione di software</span><span class="sxs-lookup"><span data-stu-id="c7d00-113">Software install</span></span>
- <span data-ttu-id="c7d00-114">Ridenominazione dei file</span><span class="sxs-lookup"><span data-stu-id="c7d00-114">File renames</span></span>
- <span data-ttu-id="c7d00-115">Ridenominazione del computer</span><span class="sxs-lookup"><span data-stu-id="c7d00-115">Computer rename</span></span>

<span data-ttu-id="c7d00-116">La risorsa **PendingReboot** esegue un controllo in percorsi specifici del computer per determinare se è presente un riavvio in sospeso.</span><span class="sxs-lookup"><span data-stu-id="c7d00-116">The **PendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="c7d00-117">Se il nodo richiede un riavvio all'esterno di DSC, la risorsa **PendingReboot** imposta il flag `$global:DSCMachineStatus` su `1` forzando un riavvio e risolvendo la condizione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="c7d00-117">If the Node requires a reboot outside of DSC, the **PendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="c7d00-118">Tutte le risorse DSC possono indicare a Gestione configurazione locale di riavviare il nodo impostando questo flag nella funzione `Set-TargetResource`.</span><span class="sxs-lookup"><span data-stu-id="c7d00-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="c7d00-119">Per altre informazioni, vedere [Scrittura di una risorsa DSC personalizzata con MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c7d00-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="c7d00-120">Sintassi</span><span class="sxs-lookup"><span data-stu-id="c7d00-120">Syntax</span></span>

```
PendingReboot [String] #ResourceName
{
    Name = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [SkipCcmClientSDK = [bool]]
    [SkipComponentBasedServicing = [bool]]
    [SkipPendingComputerRename = [bool]]
    [SkipPendingFileRename = [bool]]
    [SkipWindowsUpdate = [bool]]
}
```

## <a name="properties"></a><span data-ttu-id="c7d00-121">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c7d00-121">Properties</span></span>

| <span data-ttu-id="c7d00-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="c7d00-122">Property</span></span> | <span data-ttu-id="c7d00-123">Descrizione</span><span class="sxs-lookup"><span data-stu-id="c7d00-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="c7d00-124">Nome</span><span class="sxs-lookup"><span data-stu-id="c7d00-124">Name</span></span>| <span data-ttu-id="c7d00-125">Parametro obbligatorio che deve essere univoco per ogni istanza della risorsa all'interno di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="c7d00-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="c7d00-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="c7d00-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="c7d00-127">Ignorare i riavvii attivati dal modulo di manutenzione pacchetti basato su componenti.</span><span class="sxs-lookup"><span data-stu-id="c7d00-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="c7d00-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="c7d00-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="c7d00-129">Ignorare i riavvii attivati da Windows Update.</span><span class="sxs-lookup"><span data-stu-id="c7d00-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="c7d00-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="c7d00-130">SkipPendingFileRename</span></span> | <span data-ttu-id="c7d00-131">Ignorare i riavvii di ridenominazione file in sospeso.</span><span class="sxs-lookup"><span data-stu-id="c7d00-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="c7d00-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="c7d00-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="c7d00-133">Ignorare i riavvii attivati dal client di ConfigMgr.</span><span class="sxs-lookup"><span data-stu-id="c7d00-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="c7d00-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="c7d00-134">SkipComputerRename</span></span> | <span data-ttu-id="c7d00-135">Ignorare i riavvii attivati dalla ridenominazione del computer.</span><span class="sxs-lookup"><span data-stu-id="c7d00-135">Skip reboots triggered by Computer renames.</span></span> |
| <span data-ttu-id="c7d00-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="c7d00-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="c7d00-137">Supportata v5.</span><span class="sxs-lookup"><span data-stu-id="c7d00-137">Supported in v5.</span></span> <span data-ttu-id="c7d00-138">Esegue la risorsa con l'utente specificato.</span><span class="sxs-lookup"><span data-stu-id="c7d00-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="c7d00-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="c7d00-139">DependsOn</span></span> | <span data-ttu-id="c7d00-140">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="c7d00-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="c7d00-141">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="c7d00-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="c7d00-142">Per altre informazioni, vedere [Uso di DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="c7d00-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="c7d00-143">Esempio</span><span class="sxs-lookup"><span data-stu-id="c7d00-143">Example</span></span>

<span data-ttu-id="c7d00-144">L'esempio seguente installa Microsoft Exchange usando la risorsa [xExchange](https://github.com/PowerShell/xExchange).</span><span class="sxs-lookup"><span data-stu-id="c7d00-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="c7d00-145">Durante l'installazione, la risorsa **PendingReboot** viene usata per riavviare il nodo.</span><span class="sxs-lookup"><span data-stu-id="c7d00-145">Throughout the install, the **PendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="c7d00-146">Questo esempio richiede le credenziali di un account che disponga dei diritti per aggiungere un server di Exchange alla foresta.</span><span class="sxs-lookup"><span data-stu-id="c7d00-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="c7d00-147">Per altre informazioni sull'uso delle credenziali in DSC, vedere [Gestione delle credenziali in DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="c7d00-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

```powershell
$ConfigurationData = @{
    AllNodes = @(
        @{
            NodeName                    = '*'
            PSDSCAllowPlainTextPassword = $true
        },
        @{
            NodeName = 'DSCPULL-1'
        }
    )
}

Configuration Example
{
    param
    (
        [Parameter(Mandatory = $true)]
        [System.Management.Automation.PSCredential]
        $ExchangeAdminCredential
    )

    Import-DscResource -Module xExchange
    Import-DscResource -Module ComputerManagementDsc

    Node $AllNodes.NodeName
    {
        # Copy the Exchange setup files locally
        File ExchangeBinaries
        {
            Ensure          = 'Present'
            Type            = 'Directory'
            Recurse         = $true
            SourcePath      = '\\rras-1\Binaries\E15CU6'
            DestinationPath = 'C:\Binaries\E15CU6'
        }

        # Check if a reboot is needed before installing Exchange
        PendingReboot BeforeExchangeInstall
        {
            Name       = 'BeforeExchangeInstall'
            DependsOn  = '[File]ExchangeBinaries'
        }

        # Do the Exchange install
        xExchInstall InstallExchange
        {
            Path       = 'C:\Binaries\E15CU6\Setup.exe'
            Arguments  = '/mode:Install /role:Mailbox /Iacceptexchangeserverlicenseterms'
            Credential = $ExchangeAdminCredential
            DependsOn  = '[PendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        PendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="c7d00-148">Questo esempio presuppone che Gestione configurazione locale sia configurata per consentire i riavvii e continuare la configurazione dopo il riavvio.</span><span class="sxs-lookup"><span data-stu-id="c7d00-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="c7d00-149">Download</span><span class="sxs-lookup"><span data-stu-id="c7d00-149">Where to Download</span></span>

<span data-ttu-id="c7d00-150">È possibile scaricare le risorse usate in questo argomento nei percorsi seguenti o usando PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c7d00-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="c7d00-151">ComputerManagementDsc</span><span class="sxs-lookup"><span data-stu-id="c7d00-151">ComputerManagementDsc</span></span>](https://github.com/PowerShell/ComputerManagementDsc)
- [<span data-ttu-id="c7d00-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="c7d00-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
