---
title: Come creare un file di formattazione (format. ps1xml) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: eb568878-f63e-4561-98e2-16ee2ac7559d
caps.latest.revision: 8
ms.openlocfilehash: e97e9ddb1bf81ba66e5f3cedddd22e3a861ce228
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72363620"
---
# <a name="how-to-create-a-formatting-file-formatps1xml"></a><span data-ttu-id="b09bf-102">Come creare un file di formattazione (con estensione format.ps1xml)</span><span class="sxs-lookup"><span data-stu-id="b09bf-102">How to Create a Formatting File (.format.ps1xml)</span></span>

<span data-ttu-id="b09bf-103">In questo argomento viene descritto come creare un file di formattazione (format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="b09bf-103">This topic describes how to create a formatting file (.format.ps1xml).</span></span>

> [!NOTE]
> <span data-ttu-id="b09bf-104">È anche possibile creare un file di formattazione eseguendo una copia di uno dei file forniti da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b09bf-104">You can also create a formatting file by making a copy of one of the files provided by Windows PowerShell.</span></span> <span data-ttu-id="b09bf-105">Se si crea una copia di un file esistente, eliminare la firma digitale esistente e aggiungere la propria firma al nuovo file.</span><span class="sxs-lookup"><span data-stu-id="b09bf-105">If you make a copy of an existing file, delete the existing digital signature, and add your own signature to the new file.</span></span>

### <a name="to-create-a-formatps1xml-file"></a><span data-ttu-id="b09bf-106">Per creare un file con estensione format. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="b09bf-106">To create a .format.ps1xml file.</span></span>

1. <span data-ttu-id="b09bf-107">Creare un file di testo (con estensione txt) utilizzando un editor di testo, ad esempio Blocco note.</span><span class="sxs-lookup"><span data-stu-id="b09bf-107">Create a text file (.txt) using a text editor such as Notepad.</span></span>

2. <span data-ttu-id="b09bf-108">Copiare le righe seguenti nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b09bf-108">Copy the following lines into the formatting file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8" ?>
   <Configuration>
   <ViewDefinitions>
   </ViewDefinitions>
   </Configuration>
   ```

   - <span data-ttu-id="b09bf-109">I tag \<Configuration > \</> di configurazione definiscono il nodo `Configuration` radice.</span><span class="sxs-lookup"><span data-stu-id="b09bf-109">The \<Configuration>\</Configuration> tags define the root `Configuration` node.</span></span> <span data-ttu-id="b09bf-110">Tutti i tag XML aggiuntivi verranno racchiusi in questo nodo.</span><span class="sxs-lookup"><span data-stu-id="b09bf-110">All additional XML tags will be enclosed within this node.</span></span>

   - <span data-ttu-id="b09bf-111">I <ViewDefinitions></ViewDefinitions> Tag definiscono il nodo `ViewDefinitions`.</span><span class="sxs-lookup"><span data-stu-id="b09bf-111">The <ViewDefinitions></ViewDefinitions> tags define the `ViewDefinitions` node.</span></span> <span data-ttu-id="b09bf-112">Tutte le visualizzazioni vengono definite all'interno di questo nodo.</span><span class="sxs-lookup"><span data-stu-id="b09bf-112">All views are defined within this node.</span></span>

3. <span data-ttu-id="b09bf-113">Salvare il file nella cartella di installazione di Windows PowerShell, nella cartella del modulo o in una sottocartella della cartella del modulo.</span><span class="sxs-lookup"><span data-stu-id="b09bf-113">Save the file to the Windows PowerShell installation folder, to your module folder, or to a subfolder of the module folder.</span></span> <span data-ttu-id="b09bf-114">Quando si salva il file, utilizzare il formato del nome seguente: `MyFile.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="b09bf-114">Use the following name format when you save the file:  `MyFile.format.ps1xml`.</span></span> <span data-ttu-id="b09bf-115">I file di formattazione devono usare l'estensione `.format.ps1xml`.</span><span class="sxs-lookup"><span data-stu-id="b09bf-115">Formatting files must use the `.format.ps1xml` extension.</span></span>

   <span data-ttu-id="b09bf-116">A questo punto è possibile aggiungere visualizzazioni al file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b09bf-116">You are now ready to add views to the formatting file.</span></span> <span data-ttu-id="b09bf-117">Non esiste alcun limite al numero di visualizzazioni che è possibile definire in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="b09bf-117">There is no limit to the number of views that can be defined in a formatting file.</span></span> <span data-ttu-id="b09bf-118">È possibile aggiungere una singola visualizzazione per ogni oggetto, più visualizzazioni per lo stesso oggetto o una singola visualizzazione utilizzata da più oggetti.</span><span class="sxs-lookup"><span data-stu-id="b09bf-118">You can add a single view for each object, multiple views for the same object, or a single view that is used by multiple objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="b09bf-119">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b09bf-119">See Also</span></span>

[<span data-ttu-id="b09bf-120">Scrittura di un file di formattazione e di tipi di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b09bf-120">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
