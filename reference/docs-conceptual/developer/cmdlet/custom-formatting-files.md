---
title: File di formattazione personalizzati | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369830"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="57124-102">File di formattazione personalizzati</span><span class="sxs-lookup"><span data-stu-id="57124-102">Custom Formatting Files</span></span>

<span data-ttu-id="57124-103">Il formato di visualizzazione per gli oggetti restituiti da cmdlet, funzioni e script viene definito utilizzando i file di formattazione (file format. ps1xml).</span><span class="sxs-lookup"><span data-stu-id="57124-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="57124-104">Molti di questi file sono forniti da Windows PowerShell per definire il formato di visualizzazione predefinito per gli oggetti restituiti dai cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57124-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="57124-105">Tuttavia, è anche possibile creare file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefiniti o per definire la visualizzazione degli oggetti restituiti dai propri comandi.</span><span class="sxs-lookup"><span data-stu-id="57124-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="57124-106">Windows PowerShell usa i dati nei file di formattazione per determinare gli elementi visualizzati e il modo in cui vengono formattati i dati.</span><span class="sxs-lookup"><span data-stu-id="57124-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="57124-107">I dati visualizzati possono includere le proprietà di un oggetto o il valore di un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="57124-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="57124-108">I blocchi di script vengono utilizzati se si desidera visualizzare un valore non disponibile direttamente dalle proprietà di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="57124-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="57124-109">Ad esempio, è possibile aggiungere il valore di due proprietà di un oggetto e visualizzare la somma come una porzione di dati separata.</span><span class="sxs-lookup"><span data-stu-id="57124-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="57124-110">Quando si scrive un file di formattazione personalizzato, sarà necessario definire le *visualizzazioni* per gli oggetti che si desidera visualizzare.</span><span class="sxs-lookup"><span data-stu-id="57124-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="57124-111">È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti oppure è possibile definire più visualizzazioni per lo stesso oggetto.</span><span class="sxs-lookup"><span data-stu-id="57124-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="57124-112">Non esiste alcun limite al numero di visualizzazioni che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="57124-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="57124-113">I file di formattazione non determinano gli elementi di un oggetto restituiti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="57124-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="57124-114">Quando un oggetto viene restituito alla pipeline, sono disponibili tutti i membri di tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="57124-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="57124-115">Formatta visualizzazioni</span><span class="sxs-lookup"><span data-stu-id="57124-115">Format Views</span></span>

<span data-ttu-id="57124-116">Le visualizzazioni di formattazione possono visualizzare oggetti in formato tabella, formato elenco, formato esteso e formato personalizzato.</span><span class="sxs-lookup"><span data-stu-id="57124-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="57124-117">Nella maggior parte dei casi, ogni definizione di formattazione è descritta da un set di tag XML che descrivono una visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="57124-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="57124-118">Ogni vista contiene il nome della vista, gli oggetti che utilizzano la vista e gli elementi della vista, ad esempio le informazioni su colonna e riga per una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="57124-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="57124-119">Sono disponibili le viste seguenti.</span><span class="sxs-lookup"><span data-stu-id="57124-119">The following views are available.</span></span>

<span data-ttu-id="57124-120">Visualizzazione tabella sono elencate le proprietà di un oggetto o di un valore del blocco di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="57124-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="57124-121">Ogni colonna rappresenta una proprietà dell'oggetto o un valore del blocco di script.</span><span class="sxs-lookup"><span data-stu-id="57124-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="57124-122">È possibile definire una vista tabella che Visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e valori di blocchi di script.</span><span class="sxs-lookup"><span data-stu-id="57124-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="57124-123">Ogni riga della tabella rappresenta un oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="57124-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="57124-124">Per ulteriori informazioni su questa vista, vedere [visualizzazione tabella](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="57124-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="57124-125">Visualizzazione elenco elenca le proprietà di un oggetto o di un valore del blocco di script in un'unica colonna.</span><span class="sxs-lookup"><span data-stu-id="57124-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="57124-126">Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore della proprietà o del blocco di script.</span><span class="sxs-lookup"><span data-stu-id="57124-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="57124-127">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione elenco](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="57124-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="57124-128">Visualizzazione estesa elenca una singola proprietà di un oggetto o un valore del blocco di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="57124-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="57124-129">Nessuna etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="57124-129">There is no label or header for this view.</span></span> <span data-ttu-id="57124-130">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione estesa](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="57124-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="57124-131">Visualizzazione personalizzata consente di visualizzare una visualizzazione personalizzabile delle proprietà degli oggetti o dei valori del blocco di script che non rispettano la struttura rigida delle visualizzazioni di tabella, delle visualizzazioni elenco o delle visualizzazioni estese.</span><span class="sxs-lookup"><span data-stu-id="57124-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="57124-132">È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata utilizzata da un'altra visualizzazione, ad esempio una visualizzazione tabella o una visualizzazione elenco.</span><span class="sxs-lookup"><span data-stu-id="57124-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="57124-133">Per ulteriori informazioni su questa visualizzazione, vedere [visualizzazione personalizzata](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="57124-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="57124-134">Visualizzazione di elementi XML</span><span class="sxs-lookup"><span data-stu-id="57124-134">View XML Elements</span></span>

<span data-ttu-id="57124-135">Nell'esempio seguente vengono illustrati i tag XML utilizzati per definire una vista tabella contenente due colonne.</span><span class="sxs-lookup"><span data-stu-id="57124-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="57124-136">L'elemento [ViewDefinitions](../format/viewdefinitions-element-format.md) è l'elemento contenitore per tutte le visualizzazioni definite nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="57124-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="57124-137">L'elemento [View](../format/view-element-format.md) definisce la tabella, l'elenco, la larghezza o la visualizzazione personalizzata specifica.</span><span class="sxs-lookup"><span data-stu-id="57124-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="57124-138">All'interno di ogni visualizzazione, l'elemento [Name](../format/name-element-for-view-format.md) specifica il nome della vista, l'elemento [ViewSelectedBy](../format/viewselectedby-element-format.md) definisce gli oggetti che utilizzano la visualizzazione e i diversi elementi del controllo, ad esempio l'elemento `TableControl`, definiscono il formato della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="57124-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

```xml
ViewDefinitions
  <View>
    <Name>Name of View</Name>
    <ViewSelectedBy>
      <TypeName>Object to display using this view</TypeName>
      <TypeName>Object to display using this view</TypeName>
    </ViewSelectedBy>
    <TableControl>
      <TableHeaders>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
        <TableColumnHeader>
          <Width></Width>
        </TableColumnHeader>
      </TableHeaders>
      <TableRowEntries>
        <TableRowEntry>
          <TableColumnItems>
            <TableColumnItem>
              <PropertyName>Header for column 1</PropertyName>
            </TableColumnItem>
            <TableColumnItem>
              <PropertyName>Header for column 2</PropertyName>
            </TableColumnItem>
          </TableColumnItems>
        </TableRowEntry>
      </TableRowEntries>
    </TableControl)
  </View>
</ViewDefinitions>

```

## <a name="see-also"></a><span data-ttu-id="57124-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57124-139">See Also</span></span>

[<span data-ttu-id="57124-140">Visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="57124-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="57124-141">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="57124-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="57124-142">Visualizzazione estesa</span><span class="sxs-lookup"><span data-stu-id="57124-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="57124-143">Visualizzazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="57124-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="57124-144">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="57124-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
