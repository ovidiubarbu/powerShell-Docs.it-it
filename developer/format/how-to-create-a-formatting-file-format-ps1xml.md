---
title: Come creare un File di formattazione (. format.ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862967"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="a1f85-102">Come creare un file di formattazione (con estensione format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="a1f85-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="a1f85-103">In questo argomento viene descritto come creare un file di formattazione (. format.ps1xml).</span><span class="sxs-lookup"><span data-stu-id="a1f85-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="a1f85-104">È anche possibile creare un file di formattazione eseguendo una copia di uno dei file di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a1f85-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="a1f85-105">Se si esegue una copia di un file esistente, eliminare la firma digitale esistente e aggiungere la propria firma per il nuovo file.</span><span class="sxs-lookup"><span data-stu-id="a1f85-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="a1f85-106">Per creare un. file format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="a1f85-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="a1f85-107">Creare un file di testo (txt) usando un testo dell'editor, ad esempio Blocco note.</span><span class="sxs-lookup"><span data-stu-id="a1f85-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="a1f85-108">Copiare le righe seguenti nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a1f85-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="a1f85-109">Il \<Configuration >\</Configuration > tag definiscono radice `Configuration` nodo.</span><span class="sxs-lookup"><span data-stu-id="a1f85-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="a1f85-110">Tutti i tag XML aggiuntivi verranno racchiusi all'interno di questo nodo.</span><span class="sxs-lookup"><span data-stu-id="a1f85-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="a1f85-111">Il <ViewDefinitions> </ViewDefinitions> tag definiscono il `ViewDefinitions` nodo.</span><span class="sxs-lookup"><span data-stu-id="a1f85-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="a1f85-112">Tutte le visualizzazioni vengono definite all'interno di questo nodo.</span><span class="sxs-lookup"><span data-stu-id="a1f85-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="a1f85-113">Salvare il file nella cartella di installazione di Windows PowerShell, alla cartella del modulo o in una sottocartella della cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="a1f85-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="a1f85-114">Usare il formato nome seguente quando si salva il file: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="a1f85-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="a1f85-115">File di formattazione devono usare il `.format.ps1xml` estensione.</span><span class="sxs-lookup"><span data-stu-id="a1f85-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="a1f85-116">A questo punto si è pronti aggiungere le visualizzazioni per il file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a1f85-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="a1f85-117">Non sono previsti limiti al numero di visualizzazioni che possono essere definite in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="a1f85-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="a1f85-118">È possibile aggiungere una visualizzazione singola per ogni oggetto, più visualizzazioni per lo stesso oggetto o una singola visualizzazione che viene usata da più oggetti.</span><span class="sxs-lookup"><span data-stu-id="a1f85-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1f85-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a1f85-119">See Also</span></span>

[<span data-ttu-id="a1f85-120">La scrittura di un metodo di formattazione di Windows PowerShell e i tipi di File</span><span class="sxs-lookup"><span data-stu-id="a1f85-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
