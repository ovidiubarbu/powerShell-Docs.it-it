---
title: Come importare i cmdlet di uso di moduli | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a41d9e5f-de6f-47b7-9601-c108609320d0
caps.latest.revision: 8
ms.openlocfilehash: c007bb11324e10ffd100797dccd9e6ab0d09a73e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067978"
---
# <a name="how-to-import-cmdlets-using-modules"></a><span data-ttu-id="6e3f8-102">Come importare i cmdlet usando i moduli</span><span class="sxs-lookup"><span data-stu-id="6e3f8-102">How to Import Cmdlets Using Modules</span></span>

<span data-ttu-id="6e3f8-103">In questo argomento viene descritto come importare i cmdlet di una sessione di Windows PowerShell usando un modulo binario.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-103">This topic describes how to import cmdlets to a Windows PowerShell session by using a binary module.</span></span>

> [!NOTE]
> <span data-ttu-id="6e3f8-104">I membri dei moduli possono includere i cmdlet, provider, funzioni, variabili, alias e molto altro ancora.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-104">The members of modules can include cmdlets, providers, functions, variables, aliases, and much more.</span></span> <span data-ttu-id="6e3f8-105">Gli snap-in può contenere solo i cmdlet e provider.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-105">Snap-ins can contain only cmdlets and providers.</span></span>

## <a name="how-to-load-cmdlets-using-a-module"></a><span data-ttu-id="6e3f8-106">Come caricare i cmdlet di uso di un modulo</span><span class="sxs-lookup"><span data-stu-id="6e3f8-106">How to load cmdlets using a module</span></span>

1. <span data-ttu-id="6e3f8-107">Creare una cartella del modulo che ha lo stesso nome del file di assembly in cui vengono implementati i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-107">Create a module folder that has the same name as the assembly file in which the cmdlets are implemented.</span></span> <span data-ttu-id="6e3f8-108">In questa procedura, si crea la cartella del modulo nel `system32` cartella.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-108">In this procedure, the module folder is created in the `system32` folder.</span></span>

   `%SystemRoot%\system32\WindowsPowerShell\v1.0\Modules\mymodule`

2. <span data-ttu-id="6e3f8-109">Assicurarsi che il `PSModulePath` variabile di ambiente include il percorso della cartella del nuovo modulo.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-109">Make sure that the `PSModulePath` environment variable includes the path to your new module folder.</span></span> <span data-ttu-id="6e3f8-110">Per impostazione predefinita, la cartella di sistema è già stato aggiunto per il `PSModulePath` variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-110">By default, the system folder is already added to the `PSModulePath` environment variable.</span></span>

3. <span data-ttu-id="6e3f8-111">Copiare l'assembly di cmdlet nella cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-111">Copy the cmdlet assembly into the module folder.</span></span>

4. <span data-ttu-id="6e3f8-112">Eseguire il comando seguente per aggiungere i cmdlet nella sessione:</span><span class="sxs-lookup"><span data-stu-id="6e3f8-112">Run the following command to add the cmdlets to the session:</span></span>

   `import-module [Module_Name]`

   <span data-ttu-id="6e3f8-113">Questa procedura è utilizzabile per testare i cmdlet.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-113">This procedure can be used to test your cmdlets.</span></span> <span data-ttu-id="6e3f8-114">Aggiunge tutti i cmdlet dell'assembly alla sessione.</span><span class="sxs-lookup"><span data-stu-id="6e3f8-114">It adds all the cmdlets in the assembly to the session.</span></span> <span data-ttu-id="6e3f8-115">Per altre informazioni sui moduli, vedere i diversi tipi di moduli, i diversi modi per caricare i moduli e come limitare gli elementi di un modulo che vengono esportati [scrittura di un modulo di Windows PowerShell](../module/writing-a-windows-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="6e3f8-115">For more information about modules, the different types of modules, the different ways to load modules, and how to restrict the elements of a module that are exported, see [Writing a Windows PowerShell Module](../module/writing-a-windows-powershell-module.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6e3f8-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="6e3f8-116">See Also</span></span>

[<span data-ttu-id="6e3f8-117">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="6e3f8-117">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="6e3f8-118">Installazione dei moduli</span><span class="sxs-lookup"><span data-stu-id="6e3f8-118">Installing Modules</span></span>](../module/installing-a-powershell-module.md)