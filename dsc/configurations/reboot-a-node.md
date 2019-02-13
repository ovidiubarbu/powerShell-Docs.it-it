---
ms.date: 1/17/2019
keywords: dsc,powershell,configurazione,installazione
title: Riavviare un nodo
ms.openlocfilehash: 33ecd98aa62c3dc94a8ff2213fd3e68bf0c05cb7
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680742"
---
# <a name="reboot-a-node"></a><span data-ttu-id="5aeba-103">Riavviare un nodo</span><span class="sxs-lookup"><span data-stu-id="5aeba-103">Reboot a Node</span></span>

> [!NOTE]
> <span data-ttu-id="5aeba-104">In questo argomento descrive come riavviare un nodo.</span><span class="sxs-lookup"><span data-stu-id="5aeba-104">This topic talks about how to reboot a Node.</span></span> <span data-ttu-id="5aeba-105">Affinché il riavvio venga portato a termine il **ActionAfterReboot** e **RebootNodeIfNeeded** è necessario configurare correttamente le impostazioni di Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="5aeba-105">In order for the reboot to be successful the **ActionAfterReboot** and **RebootNodeIfNeeded** LCM settings need to be configured properly.</span></span>
> <span data-ttu-id="5aeba-106">Per altre informazioni sulle impostazioni di Gestione configurazione locale, vedere [configurare Gestione configurazione locale](../managing-nodes/metaConfig.md), o [configurare Gestione configurazione locale (v4)](../managing-nodes/metaConfig4.md).</span><span class="sxs-lookup"><span data-stu-id="5aeba-106">To read about Local Configuration Manager settings, see [Configure the Local Configuration Manager](../managing-nodes/metaConfig.md), or [Configure the Local Configuration Manager (v4)](../managing-nodes/metaConfig4.md).</span></span>

<span data-ttu-id="5aeba-107">I nodi possono essere riavviati all'interno di una risorsa, tramite il `$global:DSCMachineStatus` flag.</span><span class="sxs-lookup"><span data-stu-id="5aeba-107">Nodes can be rebooted from within a resource, by using the `$global:DSCMachineStatus` flag.</span></span> <span data-ttu-id="5aeba-108">Impostando questo flag su `1` nella `Set-TargetResource` forza la funzione LCM riavviare il nodo direttamente dopo il **impostare** metodo della risorsa corrente.</span><span class="sxs-lookup"><span data-stu-id="5aeba-108">Setting this flag to `1` in the `Set-TargetResource` function forces the LCM to reboot the Node directly after the **Set** method of the current resource.</span></span> <span data-ttu-id="5aeba-109">Usare questo flag, il **xPendingReboot** risorse rileva se è in sospeso un riavvio all'esterno di DSC.</span><span class="sxs-lookup"><span data-stu-id="5aeba-109">Using this flag, the **xPendingReboot** resource detects if a reboot is pending outside of DSC.</span></span>

<span data-ttu-id="5aeba-110">I [configurazioni](configurations.md) può eseguire i passaggi che richiedono il nodo da riavviare.</span><span class="sxs-lookup"><span data-stu-id="5aeba-110">Your [configurations](configurations.md) may perform steps that require the Node to reboot.</span></span> <span data-ttu-id="5aeba-111">Potrebbe trattarsi di operazioni, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="5aeba-111">This could include things such as:</span></span>

- <span data-ttu-id="5aeba-112">Windows: aggiornamenti</span><span class="sxs-lookup"><span data-stu-id="5aeba-112">Windows updates</span></span>
- <span data-ttu-id="5aeba-113">Installazione del software</span><span class="sxs-lookup"><span data-stu-id="5aeba-113">Software install</span></span>
- <span data-ttu-id="5aeba-114">Rinomina file</span><span class="sxs-lookup"><span data-stu-id="5aeba-114">File renames</span></span>
- <span data-ttu-id="5aeba-115">Ridenominazione del computer</span><span class="sxs-lookup"><span data-stu-id="5aeba-115">Computer rename</span></span>

<span data-ttu-id="5aeba-116">Il **xPendingReboot** risorsa controlli dei computer specifici per determinare se un riavvio in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5aeba-116">The **xPendingReboot** resource checks specific computer locations to determine if a reboot is pending.</span></span> <span data-ttu-id="5aeba-117">Se il nodo richiede un riavvio all'esterno di DSC, il **xPendingReboot** set di risorse di `$global:DSCMachineStatus` flag `1` forzare un riavvio e risolvendo la condizione in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5aeba-117">If the Node requires a reboot outside of DSC, the **xPendingReboot** resource sets the `$global:DSCMachineStatus` flag to `1` forcing a reboot and resolving the pending condition.</span></span>

> [!NOTE]
> <span data-ttu-id="5aeba-118">Qualsiasi risorsa DSC può indicare a Gestione configurazione locale per riavviare il nodo impostando questo flag `Set-TargetResource` (funzione).</span><span class="sxs-lookup"><span data-stu-id="5aeba-118">Any DSC resource can instruct the LCM to reboot the node by setting this flag in the `Set-TargetResource` function.</span></span> <span data-ttu-id="5aeba-119">Per altre informazioni, vedere [scrittura di una risorsa DSC personalizzata con MOF](../resources/authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="5aeba-119">For more information, see [Writing a custom DSC resource with MOF](../resources/authoringResourceMOF.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="5aeba-120">Sintassi</span><span class="sxs-lookup"><span data-stu-id="5aeba-120">Syntax</span></span>

```
xPendingReboot [String] #ResourceName
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

## <a name="properties"></a><span data-ttu-id="5aeba-121">Proprietà</span><span class="sxs-lookup"><span data-stu-id="5aeba-121">Properties</span></span>

| <span data-ttu-id="5aeba-122">Proprietà</span><span class="sxs-lookup"><span data-stu-id="5aeba-122">Property</span></span> | <span data-ttu-id="5aeba-123">Description</span><span class="sxs-lookup"><span data-stu-id="5aeba-123">Description</span></span> |
| --- | --- |
| <span data-ttu-id="5aeba-124">Nome</span><span class="sxs-lookup"><span data-stu-id="5aeba-124">Name</span></span>| <span data-ttu-id="5aeba-125">Parametro obbligatorio che deve essere univoco per ogni istanza della risorsa all'interno di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="5aeba-125">Required parameter that must be unique per instance of the resource within a configuration.</span></span>|
| <span data-ttu-id="5aeba-126">SkipComponentBasedServicing</span><span class="sxs-lookup"><span data-stu-id="5aeba-126">SkipComponentBasedServicing</span></span> | <span data-ttu-id="5aeba-127">Riavvii Skip attivati dal componente di manutenzione pacchetti basato su componenti.</span><span class="sxs-lookup"><span data-stu-id="5aeba-127">Skip reboots triggered by the Component-Based Servicing component.</span></span> |
| <span data-ttu-id="5aeba-128">SkipWindowsUpdate</span><span class="sxs-lookup"><span data-stu-id="5aeba-128">SkipWindowsUpdate</span></span> | <span data-ttu-id="5aeba-129">Riavvii Skip attivati da Windows Update.</span><span class="sxs-lookup"><span data-stu-id="5aeba-129">Skip reboots triggered by Windows Update.</span></span>|
| <span data-ttu-id="5aeba-130">SkipPendingFileRename</span><span class="sxs-lookup"><span data-stu-id="5aeba-130">SkipPendingFileRename</span></span> | <span data-ttu-id="5aeba-131">Ignorare i riavvii di ridenominazione di file in sospeso.</span><span class="sxs-lookup"><span data-stu-id="5aeba-131">Skip pending file rename reboots.</span></span> |
| <span data-ttu-id="5aeba-132">SkipCcmClientSDK</span><span class="sxs-lookup"><span data-stu-id="5aeba-132">SkipCcmClientSDK</span></span> | <span data-ttu-id="5aeba-133">Riavvii Skip attivati dal client di Configuration Manager.</span><span class="sxs-lookup"><span data-stu-id="5aeba-133">Skip reboots triggered by the ConfigMgr client.</span></span> |
| <span data-ttu-id="5aeba-134">SkipComputerRename</span><span class="sxs-lookup"><span data-stu-id="5aeba-134">SkipComputerRename</span></span> | <span data-ttu-id="5aeba-135">Skip riavvia precedentemente per le operazioni di ridenominazione di Computer.</span><span class="sxs-lookup"><span data-stu-id="5aeba-135">Skip reboots triggerd by Computer renames.</span></span> |
| <span data-ttu-id="5aeba-136">PSDSCRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="5aeba-136">PSDSCRunAsCredential</span></span> | <span data-ttu-id="5aeba-137">Supportato in v5.</span><span class="sxs-lookup"><span data-stu-id="5aeba-137">Supported in v5.</span></span> <span data-ttu-id="5aeba-138">Viene eseguita la risorsa con l'utente specificato.</span><span class="sxs-lookup"><span data-stu-id="5aeba-138">Executes the resource as the specified user.</span></span> |
| <span data-ttu-id="5aeba-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="5aeba-139">DependsOn</span></span> | <span data-ttu-id="5aeba-140">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="5aeba-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="5aeba-141">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="5aeba-141">For example, if the ID of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> <span data-ttu-id="5aeba-142">Per altre informazioni, vedere [usando DependsOn](resource-depends-on.md)</span><span class="sxs-lookup"><span data-stu-id="5aeba-142">For more information, see [Using DependsOn](resource-depends-on.md)</span></span>|

## <a name="example"></a><span data-ttu-id="5aeba-143">Esempio</span><span class="sxs-lookup"><span data-stu-id="5aeba-143">Example</span></span>

<span data-ttu-id="5aeba-144">L'esempio seguente installa Microsoft Exchange tramite i [xExchange](https://github.com/PowerShell/xExchange) risorsa.</span><span class="sxs-lookup"><span data-stu-id="5aeba-144">The following example installs Microsoft Exchange using the [xExchange](https://github.com/PowerShell/xExchange) resource.</span></span>
<span data-ttu-id="5aeba-145">Durante l'installazione, il **xPendingReboot** risorsa viene usata per riavviare il nodo.</span><span class="sxs-lookup"><span data-stu-id="5aeba-145">Throughout the install, the **xPendingReboot** resource is used to reboot the Node.</span></span>

> [!NOTE]
> <span data-ttu-id="5aeba-146">Questo esempio richiede le credenziali di un account che disponga dei diritti per aggiungere un server di Exchange della foresta.</span><span class="sxs-lookup"><span data-stu-id="5aeba-146">This example requires the credential of an account that has rights to add an Exchange server to the forest.</span></span> <span data-ttu-id="5aeba-147">Per altre informazioni sull'uso delle credenziali in DSC, vedere [gestione delle credenziali in DSC](../configurations/configDataCredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5aeba-147">For more information on using credentials in DSC, see [Handling Credentials in DSC](../configurations/configDataCredentials.md)</span></span>

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
    Import-DscResource -Module xPendingReboot

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
        xPendingReboot BeforeExchangeInstall
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
            DependsOn  = '[xPendingReboot]BeforeExchangeInstall'
        }

        # See if a reboot is required after installing Exchange
        xPendingReboot AfterExchangeInstall
        {
            Name      = 'AfterExchangeInstall'
            DependsOn = '[xExchInstall]InstallExchange'
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="5aeba-148">Questo esempio si presuppone di aver configurato la gestione configurazione locale per consentire i riavvii e continuare la configurazione dopo il riavvio.</span><span class="sxs-lookup"><span data-stu-id="5aeba-148">This example assumes that you have configured your Local Configuration Manager to allow reboots and continue the configuration after a reboot.</span></span>

## <a name="where-to-download"></a><span data-ttu-id="5aeba-149">Come scaricare</span><span class="sxs-lookup"><span data-stu-id="5aeba-149">Where to Download</span></span>

<span data-ttu-id="5aeba-150">È possibile scaricare le risorse usate in questo argomento nei percorsi seguenti o usando PowerShell gallery.</span><span class="sxs-lookup"><span data-stu-id="5aeba-150">You can download the resources used in this topic at the following locations, or by using the PowerShell gallery.</span></span>

- [<span data-ttu-id="5aeba-151">xPendingReboot</span><span class="sxs-lookup"><span data-stu-id="5aeba-151">xPendingReboot</span></span>](https://github.com/PowerShell/xPendingReboot)
- [<span data-ttu-id="5aeba-152">xExchange</span><span class="sxs-lookup"><span data-stu-id="5aeba-152">xExchange</span></span>](https://github.com/PowerShell/xExchange)
