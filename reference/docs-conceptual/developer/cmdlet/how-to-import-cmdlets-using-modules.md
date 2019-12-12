---
title: Come importare i cmdlet mediante i moduli | Microsoft Docs
ms.custom: ''
ms.date: 08/28/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: 2f145795a57c988da0cb4ed294142aa141c53cae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364460"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="2baa7-102">Come importare i cmdlet usando i moduli</span><span class="sxs-lookup"><span data-stu-id="2baa7-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="2baa7-103">Questo articolo descrive come importare i cmdlet in una sessione di PowerShell usando un modulo binario.</span><span class="sxs-lookup"><span data-stu-id="2baa7-103">This article describes how to import cmdlets to a PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="2baa7-104">I membri dei moduli possono includere cmdlet, provider, funzioni, variabili, alias e molto altro ancora.</span><span class="sxs-lookup"><span data-stu-id="2baa7-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="2baa7-105">Gli snap-in possono contenere solo cmdlet e provider.</span><span class="sxs-lookup"><span data-stu-id="2baa7-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="2baa7-106">Come caricare i cmdlet usando un modulo</span><span class="sxs-lookup"><span data-stu-id="2baa7-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="2baa7-107">Creare una cartella del modulo con lo stesso nome del file di assembly in cui sono implementati i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2baa7-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="2baa7-108">In questa procedura viene creata la cartella del modulo nella cartella Windows `system32`.</span><span class="sxs-lookup"><span data-stu-id="2baa7-108">In this procedure, the module folder is created in the Windows `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

1. <span data-ttu-id="2baa7-109">Verificare che la variabile di ambiente `PSModulePath` includa il percorso della nuova cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="2baa7-110">Per impostazione predefinita, la cartella di sistema è già stata aggiunta alla variabile di ambiente `PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="2baa7-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span> <span data-ttu-id="2baa7-111">Per visualizzare il `PSModulePath`, digitare: `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="2baa7-111">To view the `PSModulePath`, type: `$env:PSModulePath`.</span></span>

1. <span data-ttu-id="2baa7-112">Copiare l'assembly del cmdlet nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-112">Copy the cmdlet assembly into the module folder.</span></span>

1. <span data-ttu-id="2baa7-113">Aggiungere un file manifesto del modulo (`.psd1`) nella cartella radice del modulo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-113">Add a module manifest file (`.psd1`) in the module's root folder.</span></span> <span data-ttu-id="2baa7-114">PowerShell usa il manifesto del modulo per importare il modulo.</span><span class="sxs-lookup"><span data-stu-id="2baa7-114">PowerShell uses the module manifest to import your module.</span></span> <span data-ttu-id="2baa7-115">Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](../module/how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="2baa7-115">For more information, see [How to Write a PowerShell Module Manifest](../module/how-to-write-a-powershell-module-manifest.md).</span></span>

1. <span data-ttu-id="2baa7-116">Eseguire il comando seguente per aggiungere i cmdlet alla sessione:</span><span class="sxs-lookup"><span data-stu-id="2baa7-116">Run the following command to add the cmdlets to the session:</span></span>

   `Import-Module [Module_Name]`

   <span data-ttu-id="2baa7-117">Questa procedura può essere utilizzata per testare i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2baa7-117">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="2baa7-118">Aggiunge tutti i cmdlet nell'assembly alla sessione.</span><span class="sxs-lookup"><span data-stu-id="2baa7-118">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="2baa7-119">Per ulteriori informazioni sui moduli, vedere [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="2baa7-119">For more information about modules, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2baa7-120">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2baa7-120">See also</span></span>

[<span data-ttu-id="2baa7-121">Come scrivere un manifesto del modulo PowerShell</span><span class="sxs-lookup"><span data-stu-id="2baa7-121">How to Write a PowerShell Module Manifest</span></span>](../module/how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="2baa7-122">Importazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="2baa7-122">Importing a PowerShell Module</span></span>](../module/importing-a-powershell-module.md)

[<span data-ttu-id="2baa7-123">Import-Module</span><span class="sxs-lookup"><span data-stu-id="2baa7-123">Import-Module</span></span>](/powershell/module/Microsoft.PowerShell.Core/Import-Module)

[<span data-ttu-id="2baa7-124">Installazione di moduli</span><span class="sxs-lookup"><span data-stu-id="2baa7-124">Installing Modules</span></span>](../module/installing-a-powershell-module.md)

[<span data-ttu-id="2baa7-125">Modifica del percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="2baa7-125">Modifying the PSModulePath Installation Path</span></span>](../module/modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="2baa7-126">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2baa7-126">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
