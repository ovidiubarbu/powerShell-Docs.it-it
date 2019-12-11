---
ms.date: 07/09/2019
keywords: dsc,gpo,powershell,configurazione
title: Avvio rapido - Convertire i criteri di gruppo in DSC
ms.openlocfilehash: 8c89dbbce5b2b146194b799d7e36ecce3105bfeb
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953468"
---
> <span data-ttu-id="659f9-103">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="659f9-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart-convert-group-policy-into-dsc"></a><span data-ttu-id="659f9-104">Avvio rapido: Convertire i criteri di gruppo in DSC</span><span class="sxs-lookup"><span data-stu-id="659f9-104">Quickstart: Convert Group Policy into DSC</span></span>

<span data-ttu-id="659f9-105">È possibile generare una configurazione DSC da una baseline dei criteri di gruppo o del Centro sicurezza di Azure.</span><span class="sxs-lookup"><span data-stu-id="659f9-105">You can generate a DSC configuration from a Group Policy or Azure Security Center baseline.</span></span> <span data-ttu-id="659f9-106">Il modulo [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) include i comandi seguenti per l'esecuzione di questa attività.</span><span class="sxs-lookup"><span data-stu-id="659f9-106">The [BaselineManagement](https://www.powershellgallery.com/packages/BaselineManagement) module includes the following commands for accomplishing this task.</span></span>

- <span data-ttu-id="659f9-107">`ConvertFrom-GPO` - Converte i criteri di gruppo archiviati come file.</span><span class="sxs-lookup"><span data-stu-id="659f9-107">`ConvertFrom-GPO` - Converts Group Policies, stored as files.</span></span> <span data-ttu-id="659f9-108">È anche possibile specificare una directory che contiene più i criteri che verranno combinati in un'unica configurazione.</span><span class="sxs-lookup"><span data-stu-id="659f9-108">You can also specify a directory containing multiple policies that will be combined into one Configuration.</span></span>
  - <span data-ttu-id="659f9-109">Per esportare i criteri di gruppo nell'ambiente in uso, usare il cmdlet [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) o seguire le istruzioni in [Esportare un oggetto Criteri di gruppo in un file](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span><span class="sxs-lookup"><span data-stu-id="659f9-109">To export Group Policies in your environment, use the [Backup-GPO](/powershell/module/grouppolicy/backup-gpo?view=win10-ps) cmdlet, or follow the instructions in [Export a GPO to a File](/microsoft-desktop-optimization-pack/agpm/export-a-gpo-to-a-file).</span></span>
- <span data-ttu-id="659f9-110">`ConvertFrom-SCM` - Converte le baseline di Security Compliance Manager archiviate come file `.xml`.</span><span class="sxs-lookup"><span data-stu-id="659f9-110">`ConvertFrom-SCM` - Converts Security Compliance Manager baselines, stored as `.xml` files.</span></span>
- <span data-ttu-id="659f9-111">`ConvertFrom-ASC` - Converte le baseline del Centro sicurezza di Azure archiviate come file `.json`.</span><span class="sxs-lookup"><span data-stu-id="659f9-111">`ConvertFrom-ASC` - Converts Azure Security Center baselines, stored as `.json` files.</span></span>
- <span data-ttu-id="659f9-112">`Merge-GPOs` - Converte i criteri di gruppo applicati a un computer di destinazione.</span><span class="sxs-lookup"><span data-stu-id="659f9-112">`Merge-GPOs` - Converts Group Policies applied to a target computer.</span></span>

<span data-ttu-id="659f9-113">I cmdlet elencati sopra convertono una baseline in un file `.mof` DSC.</span><span class="sxs-lookup"><span data-stu-id="659f9-113">The cmdlets listed above convert a baseline into a DSC `.mof` file.</span></span> <span data-ttu-id="659f9-114">È anche possibile scegliere di creare uno script di configurazione (`.ps1`) che è possibile modificare e ricompilare.</span><span class="sxs-lookup"><span data-stu-id="659f9-114">You can also choose to output a Configuration script (`.ps1`), that you can edit and recompile.</span></span> <span data-ttu-id="659f9-115">I cmdlet rilevano gli errori di compilazione per le risorse mancanti o i blocchi di risorse duplicati.</span><span class="sxs-lookup"><span data-stu-id="659f9-115">The cmdlets detect compilation errors for missing resources, or duplicate resource blocks.</span></span> <span data-ttu-id="659f9-116">I blocchi di risorse che causano errori di compilazione vengono impostati come commenti.</span><span class="sxs-lookup"><span data-stu-id="659f9-116">Resource blocks that would cause compilation errors are commented out.</span></span>

<span data-ttu-id="659f9-117">L'esempio seguente converte una [baseline di Microsoft Security](https://www.microsoft.com/en-us/download/details.aspx?id=55319) in uno script di configurazione DSC (`.ps1`) e in un file `.mof`.</span><span class="sxs-lookup"><span data-stu-id="659f9-117">The following example converts a [Microsoft Security Baseline](https://www.microsoft.com/en-us/download/details.aspx?id=55319) into a DSC configuration script (`.ps1`) and `.mof` file.</span></span>

```powershell
Install-Module BaselineManagement
Import-Module BaselineManagement
ConvertFrom-GPO -Path '.\Windows 10 Version 1903 and Windows Server Version 1903 Security Baseline\GPOs\' -OutputConfigurationScript
```

<span data-ttu-id="659f9-118">Dopo aver eseguito i comandi, vengono visualizzati due file nella directory predefinita "Output" creata nel percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="659f9-118">After running the commands, you see two files in the default "Output" directory created under your current path.</span></span>

```powershell
Get-ChildItem -Path .\Output
```

```Output
    Directory:  C:\Temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----         7/9/2019   9:35 AM   227.37KB DSCFromGPO.ps1
-a----         7/9/2019   9:35 AM   410.03KB localhost.mof
```

<span data-ttu-id="659f9-119">Ogni nodo gestito richiede anche i due moduli seguenti:</span><span class="sxs-lookup"><span data-stu-id="659f9-119">Each managed node will also need the following two modules:</span></span>

- [<span data-ttu-id="659f9-120">SecurityPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="659f9-120">SecurityPolicyDSC</span></span>](https://www.powershellgallery.com/packages/SecurityPolicyDsc)
- [<span data-ttu-id="659f9-121">AuditPolicyDSC</span><span class="sxs-lookup"><span data-stu-id="659f9-121">AuditPolicyDSC</span></span>](https://www.powershellgallery.com/packages/AuditPolicyDsc)

> [!NOTE]
> <span data-ttu-id="659f9-122">**BaselineManagement** è una soluzione sviluppata dalla community per rendere più facilmente individuabile DSC per il supporto delle soluzioni della community che provengono dai gestori di progetti e non da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="659f9-122">**BaselineManagement** is a solution developed by the community to make DSC more discoverable for Support for community solutions come from the project maintainers and not from Microsoft.</span></span> <span data-ttu-id="659f9-123">È possibile aprire un nuovo argomento per **BaselineManagement** in [GitHub](https://github.com/microsoft/BaselineManagement).</span><span class="sxs-lookup"><span data-stu-id="659f9-123">You can open a new issue for **BaselineManagement** on [GitHub](https://github.com/microsoft/BaselineManagement).</span></span>

## <a name="next-steps"></a><span data-ttu-id="659f9-124">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="659f9-124">Next steps</span></span>

- <span data-ttu-id="659f9-125">Per caricare lo script di configurazione nel servizio State Configuration di Automazione di Azure, vedere [Introduzione](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span><span class="sxs-lookup"><span data-stu-id="659f9-125">To upload your configuration script into Azure Automation State Configuration, see [Getting Started](/automation/automation-dsc-getting-started#importing-a-configuration-into-azure-automation).</span></span>
- <span data-ttu-id="659f9-126">Aggiungere i moduli **SecurityPolicyDSC** e **AuditPolicyDSC** all'[Account di Automazione](/azure/automation/shared-resources/modules).</span><span class="sxs-lookup"><span data-stu-id="659f9-126">Add the **SecurityPolicyDSC** and **AuditPolicyDSC** modules to your [Automation Account](/azure/automation/shared-resources/modules).</span></span>
- <span data-ttu-id="659f9-127">Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="659f9-127">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
