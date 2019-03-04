---
title: I file di formattazione personalizzata | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 85d27545-8097-4010-9947-6d8b3ce2eac0
caps.latest.revision: 15
ms.openlocfilehash: 71c1c181058c5646c817b90d9832976a78c6c7de
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860607"
---
# <a name="custom-formatting-files"></a><span data-ttu-id="d058a-102">File di formattazione personalizzati</span><span class="sxs-lookup"><span data-stu-id="d058a-102">Custom Formatting Files</span></span>

<span data-ttu-id="d058a-103">Il formato di visualizzazione per gli oggetti restituiti dal cmdlet, funzioni e gli script vengono definiti utilizzando il file di formattazione (format.ps1xml file).</span><span class="sxs-lookup"><span data-stu-id="d058a-103">The display format for the objects returned by cmdlets, functions, and scripts are defined using formatting files (format.ps1xml files).</span></span> <span data-ttu-id="d058a-104">Molti di questi file vengono forniti tramite Windows PowerShell per definire il formato di visualizzazione predefinito per gli oggetti restituiti dai cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d058a-104">Several of these files are provided by Windows PowerShell to define the default display format for those objects returned by Windows PowerShell cmdlets.</span></span> <span data-ttu-id="d058a-105">Tuttavia, è anche possibile creare i proprio file di formattazione personalizzati per sovrascrivere i formati di visualizzazione predefinito o per definire la visualizzazione degli oggetti restituiti da comandi personalizzati.</span><span class="sxs-lookup"><span data-stu-id="d058a-105">However, you can also create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

<span data-ttu-id="d058a-106">Windows PowerShell Usa i dati in questi file di formattazione per determinare ciò che viene visualizzato e il modo in cui sono formattati i dati.</span><span class="sxs-lookup"><span data-stu-id="d058a-106">Windows PowerShell uses the data in these formatting files to determine what is displayed and how the data is formatted.</span></span> <span data-ttu-id="d058a-107">I dati visualizzati possono includere le proprietà di un oggetto o il valore di un blocco di script.</span><span class="sxs-lookup"><span data-stu-id="d058a-107">The displayed data can include the properties of an object or the value of a script block.</span></span>  <span data-ttu-id="d058a-108">Se si desidera visualizzare un valore che non è disponibile direttamente dalle proprietà di un oggetto, vengono utilizzati i blocchi di script.</span><span class="sxs-lookup"><span data-stu-id="d058a-108">Script blocks are used if you want to display some value that is not available directly from the properties of an object.</span></span> <span data-ttu-id="d058a-109">Ad esempio, è possibile aggiungere il valore di due proprietà di un oggetto e visualizzare la somma come una parte separata dei dati.</span><span class="sxs-lookup"><span data-stu-id="d058a-109">For example, you may want to add the value of two properties of an object and display the sum as a separate piece of data.</span></span> <span data-ttu-id="d058a-110">Quando si scrive un file di formattazione personalizzato, è necessario definire *viste* per gli oggetti che si desidera visualizzare.</span><span class="sxs-lookup"><span data-stu-id="d058a-110">When you write your own formatting file, you will need to define *views* for the objects that you want to display.</span></span> <span data-ttu-id="d058a-111">È possibile definire una singola visualizzazione per ogni oggetto, è possibile definire una singola visualizzazione per più oggetti o è possibile definire più visualizzazioni per lo stesso oggetto.</span><span class="sxs-lookup"><span data-stu-id="d058a-111">You can define a single view for each object, you can define a single view for multiple objects, or you can define multiple views for the same object.</span></span> <span data-ttu-id="d058a-112">Non sono previsti limiti al numero di visualizzazioni che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="d058a-112">There is no limit to the number of views that you can define.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d058a-113">File di formattazione non determinano gli elementi di un oggetto che vengono restituiti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="d058a-113">Formatting files do not determine the elements of an object that are returned to the pipeline.</span></span> <span data-ttu-id="d058a-114">Quando un oggetto viene restituito alla pipeline, sono disponibili tutti i membri di tale oggetto.</span><span class="sxs-lookup"><span data-stu-id="d058a-114">When an object is returned to the pipeline, all members of that object are available.</span></span>

## <a name="format-views"></a><span data-ttu-id="d058a-115">Viste di formato</span><span class="sxs-lookup"><span data-stu-id="d058a-115">Format Views</span></span>

<span data-ttu-id="d058a-116">Formattazione viste è possono visualizzare gli oggetti in un formato di tabella, un formato di elenco, un formato esteso e un formato personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d058a-116">Formatting views can display objects in a table format, a list format, a wide format, and a custom format.</span></span> <span data-ttu-id="d058a-117">Nella maggior parte, ogni definizione di formattazione è descritta da un set di tag XML che descrivono una vista.</span><span class="sxs-lookup"><span data-stu-id="d058a-117">For the most part, each formatting definition is described by a set of XML tags that describe a view.</span></span> <span data-ttu-id="d058a-118">Ogni visualizzazione contiene il nome della visualizzazione, gli oggetti che utilizzano la vista e gli elementi della visualizzazione, ad esempio le informazioni di colonna e riga per una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="d058a-118">Each view contains the name of the view, the objects that use the view, and the elements of the view, such as the column and row information for a table view.</span></span>

<span data-ttu-id="d058a-119">Le viste seguenti sono disponibili.</span><span class="sxs-lookup"><span data-stu-id="d058a-119">The following views are available.</span></span>

<span data-ttu-id="d058a-120">Visualizzazione tabella sono elencate le proprietà di un oggetto o un valore di blocco di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="d058a-120">Table view Lists the properties of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d058a-121">Ogni colonna rappresenta una proprietà dell'oggetto o un valore di blocco di script.</span><span class="sxs-lookup"><span data-stu-id="d058a-121">Each column represents a property of the object or a script block value.</span></span> <span data-ttu-id="d058a-122">È possibile definire una visualizzazione tabella che visualizza tutte le proprietà di un oggetto, un subset delle proprietà di un oggetto o una combinazione di proprietà e i valori di blocco di script.</span><span class="sxs-lookup"><span data-stu-id="d058a-122">You can define a table view that displays all the properties of an object, a subset of the properties of an object, or a combination of properties and script block values.</span></span> <span data-ttu-id="d058a-123">Ogni riga della tabella rappresenta un oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="d058a-123">Each row of the table represents a returned object.</span></span> <span data-ttu-id="d058a-124">Per altre informazioni su questa vista, vedere [vista tabella](../format/creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d058a-124">For more information about this view, see [Table View](../format/creating-a-table-view.md).</span></span>

<span data-ttu-id="d058a-125">Visualizzazione elenco sono elencate le proprietà di un oggetto o un valore di blocco di script in una singola colonna.</span><span class="sxs-lookup"><span data-stu-id="d058a-125">List view Lists the properties of an object or a script block value in a single column.</span></span> <span data-ttu-id="d058a-126">Ogni riga dell'elenco Visualizza un'etichetta facoltativa o il nome della proprietà seguito dal valore del blocco di proprietà o dello script.</span><span class="sxs-lookup"><span data-stu-id="d058a-126">Each row of the list displays an optional label or the property name followed by the value of the property or script block.</span></span> <span data-ttu-id="d058a-127">Per altre informazioni su questa vista, vedere [visualizzazione elenco](../format/creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d058a-127">For more information about this view, see [List View](../format/creating-a-list-view.md).</span></span>

<span data-ttu-id="d058a-128">Visualizzazione più ampia elenca una singola proprietà di un oggetto o un valore di blocco di script in una o più colonne.</span><span class="sxs-lookup"><span data-stu-id="d058a-128">Wide view Lists a single property of an object or a script block value in one or more columns.</span></span> <span data-ttu-id="d058a-129">Non sono etichetta o intestazione per questa visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d058a-129">There is no label or header for this view.</span></span> <span data-ttu-id="d058a-130">Per altre informazioni su questa vista, vedere [visualizzazione estesa](../format/creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d058a-130">For more information about this view, see [Wide View](../format/creating-a-wide-view.md).</span></span>

<span data-ttu-id="d058a-131">Visualizzazione personalizzata consente di visualizzare una visualizzazione di proprietà degli oggetti o valori di blocco di script personalizzabile che non rispettano la struttura rigida di viste delle tabelle, visualizzazioni elenco o visualizzazioni ampie.</span><span class="sxs-lookup"><span data-stu-id="d058a-131">Custom view Displays a customizable view of object properties or script block values that does not adhere to the rigid structure of table views, list views, or wide views.</span></span> <span data-ttu-id="d058a-132">È possibile definire una visualizzazione personalizzata autonoma oppure è possibile definire una visualizzazione personalizzata che viene usata da un'altra visualizzazione, ad esempio una tabella o una vista elenco.</span><span class="sxs-lookup"><span data-stu-id="d058a-132">You can define a standalone custom view, or you can define a custom view that is used by another view, such as a table view or list view.</span></span> <span data-ttu-id="d058a-133">Per altre informazioni su questa vista, vedere [vista personalizzata](../format/creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="d058a-133">For more information about this view, see [Custom View](../format/creating-custom-controls.md).</span></span>

## <a name="view-xml-elements"></a><span data-ttu-id="d058a-134">Visualizzare gli elementi XML</span><span class="sxs-lookup"><span data-stu-id="d058a-134">View XML Elements</span></span>

<span data-ttu-id="d058a-135">Nell'esempio seguente mostra i tag XML utilizzati per definire una visualizzazione tabella che contiene due colonne.</span><span class="sxs-lookup"><span data-stu-id="d058a-135">The following example shows the XML tags used to define a table view that contains two columns.</span></span> <span data-ttu-id="d058a-136">Il [ViewDefinitions](../format/viewdefinitions-element-format.md) elemento corrisponde all'elemento contenitore per tutte le viste definite nel file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="d058a-136">The [ViewDefinitions](../format/viewdefinitions-element-format.md) element is the container element for all the views defined in the formatting file.</span></span> <span data-ttu-id="d058a-137">Il [vista](../format/view-element-format.md) elemento definisce la tabella specifica, elenco, visualizzazione wide o personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d058a-137">The [View](../format/view-element-format.md) element defines the specific table, list, wide, or custom view.</span></span> <span data-ttu-id="d058a-138">All'interno di ogni visualizzazione, il [nome](../format/name-element-for-view-format.md) elemento specifica il nome della visualizzazione, il [ViewSelectedBy](../format/viewselectedby-element-format.md) elemento definisce gli oggetti che utilizzano la vista e gli elementi di controllo diverso (come il `TableControl` elemento) definisce il formato di visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="d058a-138">Within each view, the [Name](../format/name-element-for-view-format.md) element specifies the name of the view, the [ViewSelectedBy](../format/viewselectedby-element-format.md) element defines the objects that use the view, and the different control elements (such as the `TableControl` element) define the format of the view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d058a-139">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d058a-139">See Also</span></span>

[<span data-ttu-id="d058a-140">Visualizzazione tabella</span><span class="sxs-lookup"><span data-stu-id="d058a-140">Table View</span></span>](../format/creating-a-table-view.md)

[<span data-ttu-id="d058a-141">Visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="d058a-141">List View</span></span>](../format/creating-a-list-view.md)

[<span data-ttu-id="d058a-142">Visualizzazione più ampia</span><span class="sxs-lookup"><span data-stu-id="d058a-142">Wide View</span></span>](../format/creating-a-wide-view.md)

[<span data-ttu-id="d058a-143">Visualizzazione personalizzata</span><span class="sxs-lookup"><span data-stu-id="d058a-143">Custom View</span></span>](../format/creating-custom-controls.md)

[<span data-ttu-id="d058a-144">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d058a-144">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
