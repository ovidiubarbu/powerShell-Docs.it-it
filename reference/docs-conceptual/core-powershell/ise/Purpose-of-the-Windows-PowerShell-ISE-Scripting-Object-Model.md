---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Scopo del modello a oggetti di scripting di Windows PowerShell ISE
ms.assetid: d176a131-ab0c-43ee-80c1-f824ab8e4a05
ms.openlocfilehash: 65535948d681ec63c6cc36583c6d145cfa19b937
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="purpose-of-the-windows-powershell-ise-scripting-object-model"></a><span data-ttu-id="a4897-103">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-103">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>
  <span data-ttu-id="a4897-104">Gli oggetti sono associati al formato e alla funzione di Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="a4897-104">Objects are associated with the form and function of Windows PowerShell Integrated Scripting Environment (ISE).</span></span> <span data-ttu-id="a4897-105">Il riferimento del modello a oggetti fornisce dettagli sulle proprietà dei membri e sui metodi esposti da tali oggetti.</span><span class="sxs-lookup"><span data-stu-id="a4897-105">The object model reference provides details about the member properties and methods that these objects expose.</span></span> <span data-ttu-id="a4897-106">Vengono forniti esempi per mostrare come usare gli script per accedere direttamente a tali metodi e proprietà.</span><span class="sxs-lookup"><span data-stu-id="a4897-106">Examples are provided to show how you can use scripts to directly access these methods and properties.</span></span> <span data-ttu-id="a4897-107">Il modello a oggetti di scripting semplifica la gamma di attività seguenti.</span><span class="sxs-lookup"><span data-stu-id="a4897-107">The scripting object model makes the following range of tasks easier.</span></span>

## <a name="customizing-the-appearance-of-windows-powershell-ise"></a><span data-ttu-id="a4897-108">Personalizzazione dell'aspetto di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-108">Customizing the appearance of Windows PowerShell ISE</span></span>
 <span data-ttu-id="a4897-109">È possibile usare il modello a oggetti per modificare le impostazioni e le opzioni dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="a4897-109">You can use the object model to modify the application settings and options.</span></span> <span data-ttu-id="a4897-110">Ad esempio, è possibile modificarle come segue:</span><span class="sxs-lookup"><span data-stu-id="a4897-110">For example, you can modify them as follows:</span></span>

-   <span data-ttu-id="a4897-111">È possibile modificare il colore di errori, avvisi, output dettagliati e output di debug.</span><span class="sxs-lookup"><span data-stu-id="a4897-111">You can change the color of errors, warnings, verbose outputs, and debug outputs.</span></span>

-   <span data-ttu-id="a4897-112">È possibile ottenere o impostare i colori di sfondo per il riquadro dei comandi, il riquadro di output e il riquadro di script.</span><span class="sxs-lookup"><span data-stu-id="a4897-112">You can get or set the background colors for the Command pane, the Output pane, and the Script pane.</span></span>

-   <span data-ttu-id="a4897-113">È possibile impostare il colore di primo piano per il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="a4897-113">You can set the foreground color for the Output pane.</span></span>

-   <span data-ttu-id="a4897-114">È possibile impostare il nome del tipo di carattere e la dimensione del carattere per Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4897-114">You can set the font name and font size for Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="a4897-115">È possibile configurare gli avvisi.</span><span class="sxs-lookup"><span data-stu-id="a4897-115">You can configure warnings.</span></span> <span data-ttu-id="a4897-116">Questa impostazione include gli avvisi che vengono generati quando viene aperto un file in più schede di PowerShell o quando uno script nel file viene eseguito prima del salvataggio del file.</span><span class="sxs-lookup"><span data-stu-id="a4897-116">This setting includes warnings that are issued when a file is opened in multiple PowerShell tabs or when a script in the file is run before the file has been saved.</span></span>

-   <span data-ttu-id="a4897-117">È possibile passare da una vista in cui il riquadro di script e il riquadro di output sono affiancati a una vista in cui il riquadro di script si trova sopra il riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="a4897-117">You can switch between a view where the Script pane and the Output pane are side-by-side and a view where the Script pane is on top of the Output pane.</span></span> <span data-ttu-id="a4897-118">È possibile ancorare il riquadro dei comandi nella parte inferiore o superiore del riquadro di output.</span><span class="sxs-lookup"><span data-stu-id="a4897-118">You can dock the Command pane to the bottom or the top of the Output pane.</span></span>

## <a name="enhancing-the-functionality-of-windows-powershell-ise"></a><span data-ttu-id="a4897-119">Miglioramento della funzionalità di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-119">Enhancing the functionality of Windows PowerShell ISE</span></span>
 <span data-ttu-id="a4897-120">È possibile usare il modello a oggetti per migliorare le funzionalità di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4897-120">You can use the object model to enhance the functionality of Windows PowerShell ISE.</span></span> <span data-ttu-id="a4897-121">Ad esempio, è possibile:</span><span class="sxs-lookup"><span data-stu-id="a4897-121">For example, you can:</span></span>

-   <span data-ttu-id="a4897-122">Aggiungere e modificare l'istanza di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="a4897-122">Add and modify the instance of Windows PowerShell ISE itself.</span></span> <span data-ttu-id="a4897-123">Ad esempio, per modificare i menu è possibile aggiungere nuove voci di menu e associare nuove voci di menu agli script.</span><span class="sxs-lookup"><span data-stu-id="a4897-123">For example, to change the menus, you can add new menu items and map the new menu items to scripts.</span></span>

-   <span data-ttu-id="a4897-124">Creare script che eseguono alcune operazioni che si possono eseguire con i comandi di menu e i pulsanti in Windows PowerShell ISE,</span><span class="sxs-lookup"><span data-stu-id="a4897-124">Create scripts that perform some of the tasks that you can perform by using the menu commands and buttons in Windows PowerShell ISE.</span></span> <span data-ttu-id="a4897-125">ad esempio aggiungere, rimuovere o selezionare una scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4897-125">For example, you can add, remove, or select a PowerShell tab.</span></span>

-   <span data-ttu-id="a4897-126">Attività di complemento che possono essere eseguite con i comandi di menu e i pulsanti,</span><span class="sxs-lookup"><span data-stu-id="a4897-126">Complement tasks that can be performed by using menu commands and buttons.</span></span> <span data-ttu-id="a4897-127">ad esempio rinominare una scheda di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4897-127">For example, you can rename a PowerShell tab.</span></span>

-   <span data-ttu-id="a4897-128">Modificare i buffer di testo per il riquadro dei comandi, il riquadro di output e il riquadro di script associati a un file.</span><span class="sxs-lookup"><span data-stu-id="a4897-128">Manipulate text buffers for the Command pane, the Output pane, and the Script pane that are associated with a file.</span></span> <span data-ttu-id="a4897-129">Ad esempio, è possibile:</span><span class="sxs-lookup"><span data-stu-id="a4897-129">For example, you can:</span></span>

    -   <span data-ttu-id="a4897-130">Ottenere o impostare tutto il testo.</span><span class="sxs-lookup"><span data-stu-id="a4897-130">Get or set all text.</span></span>

    -   <span data-ttu-id="a4897-131">Ottenere o impostare una selezione di testo.</span><span class="sxs-lookup"><span data-stu-id="a4897-131">Get or set a text selection.</span></span>

    -   <span data-ttu-id="a4897-132">Eseguire uno script o una parte specifica di uno script.</span><span class="sxs-lookup"><span data-stu-id="a4897-132">Run a script or run a selected portion of a script.</span></span>

    -   <span data-ttu-id="a4897-133">Scorrere di una riga nella visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="a4897-133">Scroll a line into view.</span></span>

    -   <span data-ttu-id="a4897-134">Inserire il testo in una posizione di inserimento.</span><span class="sxs-lookup"><span data-stu-id="a4897-134">Insert text at a caret position.</span></span>

    -   <span data-ttu-id="a4897-135">Selezionare un blocco di testo.</span><span class="sxs-lookup"><span data-stu-id="a4897-135">Select a block of text.</span></span>

    -   <span data-ttu-id="a4897-136">Ottenere l'ultimo numero di riga.</span><span class="sxs-lookup"><span data-stu-id="a4897-136">Get the last line number.</span></span>

-   <span data-ttu-id="a4897-137">Eseguire operazioni sui file.</span><span class="sxs-lookup"><span data-stu-id="a4897-137">Perform file operations.</span></span> <span data-ttu-id="a4897-138">Ad esempio, è possibile:</span><span class="sxs-lookup"><span data-stu-id="a4897-138">For example, you can:</span></span>

    -   <span data-ttu-id="a4897-139">Aprire un file, salvarlo o salvarlo con un altro nome.</span><span class="sxs-lookup"><span data-stu-id="a4897-139">Open a file, save a file, or save a file by using a different name.</span></span>

    -   <span data-ttu-id="a4897-140">Determinare se un file è stato modificato dopo l'ultimo salvataggio.</span><span class="sxs-lookup"><span data-stu-id="a4897-140">Determine whether a file has been changed after it was last saved.</span></span>

    -   <span data-ttu-id="a4897-141">Ottenere il nome del file.</span><span class="sxs-lookup"><span data-stu-id="a4897-141">Get the file name.</span></span>

    -   <span data-ttu-id="a4897-142">Selezionare un file.</span><span class="sxs-lookup"><span data-stu-id="a4897-142">Select a file.</span></span>

## <a name="automating-tasks"></a><span data-ttu-id="a4897-143">Automazione di attività</span><span class="sxs-lookup"><span data-stu-id="a4897-143">Automating tasks</span></span>
 <span data-ttu-id="a4897-144">È possibile usare il modello a oggetti di scripting per creare scelte rapide da tastiera per le operazioni frequenti.</span><span class="sxs-lookup"><span data-stu-id="a4897-144">You can use the scripting object model to create keyboard shortcuts for frequent operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="a4897-145">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a4897-145">See Also</span></span>
- [<span data-ttu-id="a4897-146">Gerarchia del modello a oggetti ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-146">The ISE Object Model Hierarchy</span></span>](The-ISE-Object-Model-Hierarchy.md) 
- [<span data-ttu-id="a4897-147">Riferimenti al modello a oggetti di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-147">Windows PowerShell ISE Object Model Reference</span></span>](Windows-PowerShell-ISE-Object-Model-Reference.md) 
- [<span data-ttu-id="a4897-148">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="a4897-148">The Windows PowerShell ISE Scripting Object Model</span></span>](The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  