---
title: Associazione di entità OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359810"
---
# <a name="associating-management-odata-entities"></a><span data-ttu-id="ddee1-102">Associazione delle entità OData di gestione</span><span class="sxs-lookup"><span data-stu-id="ddee1-102">Associating Management OData Entities</span></span>

<span data-ttu-id="ddee1-103">Spesso è utile creare un'associazione tra due entità OData di gestione diverse.</span><span class="sxs-lookup"><span data-stu-id="ddee1-103">It is often useful to create an association between two different Management OData entities.</span></span> <span data-ttu-id="ddee1-104">Un servizio OData di gestione, ad esempio, può avere entità che gestiscono un catalogo di prodotti organizzati in categorie e definiscono le entità `Product` e `Category`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-104">For example, a Management OData service could have entities that manage a catalogue of products that are organized in categories, and define the entities `Product` and `Category`.</span></span> <span data-ttu-id="ddee1-105">Associando queste due entità, un client può ottenere informazioni su tutti i prodotti in una categoria con una singola richiesta al servizio Web.</span><span class="sxs-lookup"><span data-stu-id="ddee1-105">By associating these two entities, a client can get information about all of the products in a category with a single request to the web service.</span></span>

<span data-ttu-id="ddee1-106">Un esempio che illustra come creare associazioni tra le entità può essere scaricato nell' [esempio di associazione](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span><span class="sxs-lookup"><span data-stu-id="ddee1-106">A sample that shows how to create associations between entities can be downloaded at [Association sample](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).</span></span>

## <a name="creating-the-association-in-the-resource-schema-file"></a><span data-ttu-id="ddee1-107">Creazione dell'associazione nel file di schema della risorsa</span><span class="sxs-lookup"><span data-stu-id="ddee1-107">Creating the Association in the resource schema file</span></span>

<span data-ttu-id="ddee1-108">Il file MOF seguente definisce due entità.</span><span class="sxs-lookup"><span data-stu-id="ddee1-108">The following MOF defines two entities.</span></span> <span data-ttu-id="ddee1-109">Si creerà un'associazione tra di essi.</span><span class="sxs-lookup"><span data-stu-id="ddee1-109">We will create an association between them.</span></span>

```csharp
class Product {

[key] string ProductName;

// other fields ...
};

class Category {

[key] string CategoryName;

string Products[];

// other fields
}
```

<span data-ttu-id="ddee1-110">La classe `Category` definisce una proprietà che è una matrice dei nomi dei prodotti che appartengono a tale categoria.</span><span class="sxs-lookup"><span data-stu-id="ddee1-110">The `Category` class defines a property that is an array of the names of the products that belong to that category.</span></span>

<span data-ttu-id="ddee1-111">Per associare due entità, è necessario definire una classe con l'attributo `Association` nel file MOF dello schema della risorsa per il servizio.</span><span class="sxs-lookup"><span data-stu-id="ddee1-111">To associate two entities, you must define a class with the `Association` attribute in the resource schema MOF file for the service.</span></span> <span data-ttu-id="ddee1-112">La classe deve definire le due entità da associare, denominate `ends` dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="ddee1-112">The class must define the two entities to be associated, called `ends` of the association.</span></span> <span data-ttu-id="ddee1-113">Nell'esempio seguente viene illustrata una definizione di una classe che definisce un'associazione tra le entità Category e Products.</span><span class="sxs-lookup"><span data-stu-id="ddee1-113">The following example shows a definition of a class that defines an association between the Category and Products entities.</span></span>

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

<span data-ttu-id="ddee1-114">È inoltre necessario modificare la dichiarazione della proprietà Products nella classe Category.</span><span class="sxs-lookup"><span data-stu-id="ddee1-114">You must also change the declaration of the Products property in the Category class.</span></span> <span data-ttu-id="ddee1-115">Usare la parola chiave `AssociationClass` per specificare che la proprietà è un'entità finale dell'associazione.</span><span class="sxs-lookup"><span data-stu-id="ddee1-115">You use the `AssociationClass` keyword to specify that the property is one end of the association.</span></span> <span data-ttu-id="ddee1-116">La proprietà deve essere definita anche come riferimento a un'entità separata, anziché a una matrice di stringhe.</span><span class="sxs-lookup"><span data-stu-id="ddee1-116">The property must also be defined as a reference to a separate entity, rather than an array of strings.</span></span> <span data-ttu-id="ddee1-117">A tale scopo, usare la parola chiave `ref`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-117">You do this by using the `ref` keyword.</span></span> <span data-ttu-id="ddee1-118">Nell'esempio seguente viene illustrata la definizione di proprietà per l'associazione.</span><span class="sxs-lookup"><span data-stu-id="ddee1-118">The following example shows the property definition for the association.</span></span>

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

<span data-ttu-id="ddee1-119">Infine, è necessario dichiarare l'altra entità finale dell'associazione aggiungendo una definizione di proprietà alla classe `Product`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-119">Finally, you must declare the other end of the association by adding a property definition to the `Product` class.</span></span> <span data-ttu-id="ddee1-120">Si tratta di un riferimento a una matrice o a una singola entità.</span><span class="sxs-lookup"><span data-stu-id="ddee1-120">This is a reference to either an array or to a single entity.</span></span> <span data-ttu-id="ddee1-121">Supponendo che ogni prodotto appartenga a una sola categoria, la definizione è la seguente.</span><span class="sxs-lookup"><span data-stu-id="ddee1-121">Assuming that each product belongs to only one category, the definition would be as follows.</span></span>

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

<span data-ttu-id="ddee1-122">Le proprietà che rappresentano le due entità finali dell'associazione sono denominate proprietà di navigazione.</span><span class="sxs-lookup"><span data-stu-id="ddee1-122">The properties that represent the two ends of the association are called navigation properties.</span></span>

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a><span data-ttu-id="ddee1-123">Passaggi per l'associazione di entità nel file di schema della risorsa</span><span class="sxs-lookup"><span data-stu-id="ddee1-123">Steps for associating entities in the resource schema file</span></span>

- <span data-ttu-id="ddee1-124">Definire l'associazione come classe usando la parola chiave `Association`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-124">Define the association as a class by using the `Association` keyword.</span></span>

- <span data-ttu-id="ddee1-125">Definire le entità finali dell'associazione usando la parola chiave AssociationClass per qualificare le proprietà delle entità associate.</span><span class="sxs-lookup"><span data-stu-id="ddee1-125">Define the ends of the association by using the AssociationClass keyword to qualify properties of the associated entities.</span></span>

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a><span data-ttu-id="ddee1-126">Creazione dell'associazione nel file XML di mapping delle risorse</span><span class="sxs-lookup"><span data-stu-id="ddee1-126">Creating the association in the resource mapping XML file</span></span>

<span data-ttu-id="ddee1-127">Esistono tre casi diversi da considerare quando si esegue il mapping di un'associazione nel file XML di mapping delle risorse.</span><span class="sxs-lookup"><span data-stu-id="ddee1-127">There are three different cases to consider when mapping an association in the resource mapping XML file.</span></span>

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a><span data-ttu-id="ddee1-128">Determinazione della modalità di associazione delle entità nel file di mapping delle risorse</span><span class="sxs-lookup"><span data-stu-id="ddee1-128">Determining how to associate entities in the resource mapping file</span></span>

- <span data-ttu-id="ddee1-129">Se la proprietà di navigazione è presente nell'oggetto sottostante.</span><span class="sxs-lookup"><span data-stu-id="ddee1-129">If the navigation property is present in the underlying.</span></span> <span data-ttu-id="ddee1-130">.NET Framework tipo e tale proprietà contiene chiavi esterne, non è necessario alcun mapping esplicito.</span><span class="sxs-lookup"><span data-stu-id="ddee1-130">.NET Framework type, and that property contains foreign keys, no explicit mapping is necessary.</span></span>

- <span data-ttu-id="ddee1-131">Se la proprietà di navigazione non esiste nel tipo di .NET Framework sottostante, è necessario specificare un cmdlet che recuperi l'elenco di chiavi delle istanze associate.</span><span class="sxs-lookup"><span data-stu-id="ddee1-131">If the navigation property does not exist in the underlying .NET Framework type, you must specify a cmdlet that retrieves the list of keys of the associated instances.</span></span> <span data-ttu-id="ddee1-132">A tale scopo, aggiungere un elemento `Association` annidato sotto l'elemento `CmdletImplementation`, seguendo gli elementi che definiscono la `cmdlets` per gli altri comandi CRUD.</span><span class="sxs-lookup"><span data-stu-id="ddee1-132">You do this by adding an `Association` element nested under the `CmdletImplementation` element, following the elements that define the `cmdlets` for the other CRUD commands.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="ddee1-133">Se la proprietà di navigazione esiste nel tipo di .NET Framework sottostante, ma contiene istanze di oggetti anziché chiavi esterne, è necessario creare un cmdlet (scrivendo una funzione o uno script di Windows PowerShell) per recuperare le chiavi esterne.</span><span class="sxs-lookup"><span data-stu-id="ddee1-133">If the navigation property does exist in the underlying .NET Framework type, but it contains object instances instead of foreign keys, then you must create a cmdlet (by writing a Windows PowerShell function or script) to retrieve the foreign keys.</span></span> <span data-ttu-id="ddee1-134">Il cmdlet viene quindi specificato nel file di mapping delle risorse.</span><span class="sxs-lookup"><span data-stu-id="ddee1-134">You then specify that cmdlet in the resource mapping file.</span></span> <span data-ttu-id="ddee1-135">Ad esempio, lo script per recuperare le chiavi avrà un aspetto simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="ddee1-135">For example, the script to retrieve the keys would look like the following.</span></span>

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  <span data-ttu-id="ddee1-136">Il codice XML nel file di mapping delle risorse sarà simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="ddee1-136">And the XML in the resource mapping file would look like the following.</span></span>

  ```xml
  Class Name=" Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
                 <Cmdlet>Get-ProductsInCategory.ps1</Cmdlet>
                 <ParameterForThisObject>Category</ParameterForThisObject>
              </GetReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

- <span data-ttu-id="ddee1-137">Oltre a specificare un cmdlet per il recupero delle entità associate, è inoltre possibile specificare i cmdlet per aggiungere e rimuovere i riferimenti dalla raccolta.</span><span class="sxs-lookup"><span data-stu-id="ddee1-137">In addition to specifying a cmdlet to retrieve the associated entities, you can also specify cmdlets to add and remove references from the collection.</span></span> <span data-ttu-id="ddee1-138">Nell'esempio seguente si presuppone che siano presenti i cmdlet Add-ProductToCategory e Remove-ProductFromCategory (possono anche essere definiti in uno script o in una funzione come nell'esempio precedente).</span><span class="sxs-lookup"><span data-stu-id="ddee1-138">The following example assumes that the Add-ProductToCategory and Remove-ProductFromCategory cmdlets exist (they can also be defined in a script or function as in the previous example).</span></span>

  ```xml
  Class Name="Sample.Category">
     <CmdletImplementation>
        <Query> ... </Query>
        <Associations>
           <Field>
              <Name>AssociatedProducts</Name>
              <GetReference>
  ...
              </GetReference>
        <AddReference>
     <CmdletName>"Add-ProductToCategory"</>
     <ParameterForThisObject>"Product"</>
     <ParameterForReferredObject>"Category"</>
        </AddReference>
        <RemoveReference>
     <CmdletName="Remove-ProductFromCategory"/>
     <ParameterForThisObject >"Product"</>
     <ParameterForReferredObject >"Category"</>
        </RemoveReference>
           </Field>
        </Associations>
     </CmdletImplementation>
  </Class>
  ```

## <a name="querying-associated-entities"></a><span data-ttu-id="ddee1-139">Esecuzione di query sulle entità associate</span><span class="sxs-lookup"><span data-stu-id="ddee1-139">Querying associated entities</span></span>

<span data-ttu-id="ddee1-140">Il client può recuperare un elenco delle istanze associate a un'entità creando query specifiche.</span><span class="sxs-lookup"><span data-stu-id="ddee1-140">The client can retrieve a list of the instances associated with an entity by creating specific queries.</span></span>

#### <a name="constructing-queries-for-associated-entities"></a><span data-ttu-id="ddee1-141">Creazione di query per le entità associate</span><span class="sxs-lookup"><span data-stu-id="ddee1-141">Constructing queries for associated entities</span></span>

- <span data-ttu-id="ddee1-142">Un client può richiedere i dettagli di una categoria senza recuperare i prodotti associati.</span><span class="sxs-lookup"><span data-stu-id="ddee1-142">A client can request the details of a category without retrieving its associated products.</span></span> <span data-ttu-id="ddee1-143">La richiesta seguente, ad esempio, ottiene i dettagli della categoria `food`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-143">For example, the following request gets details of the `food` category.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  <span data-ttu-id="ddee1-144">Per ottenere i prodotti associati della categoria (ma non i dettagli della categoria stessa, il client specifica la proprietà di navigazione nella richiesta.</span><span class="sxs-lookup"><span data-stu-id="ddee1-144">To get the associated products of the category (but not details of the category itself, the client specifies the navigation property in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- <span data-ttu-id="ddee1-145">Per recuperare solo gli URL dei prodotti, utilizzare il qualificatore `$links` nella richiesta.</span><span class="sxs-lookup"><span data-stu-id="ddee1-145">To retrieve only URLs of the products, use the `$links` qualifier in the request.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- <span data-ttu-id="ddee1-146">Il client può ottenere sia i dettagli della categoria che i prodotti associati utilizzando il qualificatore `$expand`.</span><span class="sxs-lookup"><span data-stu-id="ddee1-146">The client can get both the category details and its associated products by using the `$expand` qualifier.</span></span>

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a><span data-ttu-id="ddee1-147">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ddee1-147">See Also</span></span>

[<span data-ttu-id="ddee1-148">Creazione di un servizio Web di estensione IIS OData di gestione</span><span class="sxs-lookup"><span data-stu-id="ddee1-148">Creating a Management OData IIS Extension Web Service</span></span>](./creating-a-management-odata-web-service.md)