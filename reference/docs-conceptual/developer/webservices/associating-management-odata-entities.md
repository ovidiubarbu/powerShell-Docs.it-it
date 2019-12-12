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
# <a name="associating-management-odata-entities"></a>Associazione delle entità OData di gestione

Spesso è utile creare un'associazione tra due entità OData di gestione diverse. Un servizio OData di gestione, ad esempio, può avere entità che gestiscono un catalogo di prodotti organizzati in categorie e definiscono le entità `Product` e `Category`. Associando queste due entità, un client può ottenere informazioni su tutti i prodotti in una categoria con una singola richiesta al servizio Web.

Un esempio che illustra come creare associazioni tra le entità può essere scaricato nell' [esempio di associazione](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Creazione dell'associazione nel file di schema della risorsa

Il file MOF seguente definisce due entità. Si creerà un'associazione tra di essi.

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

La classe `Category` definisce una proprietà che è una matrice dei nomi dei prodotti che appartengono a tale categoria.

Per associare due entità, è necessario definire una classe con l'attributo `Association` nel file MOF dello schema della risorsa per il servizio. La classe deve definire le due entità da associare, denominate `ends` dell'associazione. Nell'esempio seguente viene illustrata una definizione di una classe che definisce un'associazione tra le entità Category e Products.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

È inoltre necessario modificare la dichiarazione della proprietà Products nella classe Category. Usare la parola chiave `AssociationClass` per specificare che la proprietà è un'entità finale dell'associazione. La proprietà deve essere definita anche come riferimento a un'entità separata, anziché a una matrice di stringhe. A tale scopo, usare la parola chiave `ref`. Nell'esempio seguente viene illustrata la definizione di proprietà per l'associazione.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Infine, è necessario dichiarare l'altra entità finale dell'associazione aggiungendo una definizione di proprietà alla classe `Product`. Si tratta di un riferimento a una matrice o a una singola entità. Supponendo che ogni prodotto appartenga a una sola categoria, la definizione è la seguente.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Le proprietà che rappresentano le due entità finali dell'associazione sono denominate proprietà di navigazione.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Passaggi per l'associazione di entità nel file di schema della risorsa

- Definire l'associazione come classe usando la parola chiave `Association`.

- Definire le entità finali dell'associazione usando la parola chiave AssociationClass per qualificare le proprietà delle entità associate.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Creazione dell'associazione nel file XML di mapping delle risorse

Esistono tre casi diversi da considerare quando si esegue il mapping di un'associazione nel file XML di mapping delle risorse.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinazione della modalità di associazione delle entità nel file di mapping delle risorse

- Se la proprietà di navigazione è presente nell'oggetto sottostante. .NET Framework tipo e tale proprietà contiene chiavi esterne, non è necessario alcun mapping esplicito.

- Se la proprietà di navigazione non esiste nel tipo di .NET Framework sottostante, è necessario specificare un cmdlet che recuperi l'elenco di chiavi delle istanze associate. A tale scopo, aggiungere un elemento `Association` annidato sotto l'elemento `CmdletImplementation`, seguendo gli elementi che definiscono la `cmdlets` per gli altri comandi CRUD.

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

- Se la proprietà di navigazione esiste nel tipo di .NET Framework sottostante, ma contiene istanze di oggetti anziché chiavi esterne, è necessario creare un cmdlet (scrivendo una funzione o uno script di Windows PowerShell) per recuperare le chiavi esterne. Il cmdlet viene quindi specificato nel file di mapping delle risorse. Ad esempio, lo script per recuperare le chiavi avrà un aspetto simile al seguente.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  Il codice XML nel file di mapping delle risorse sarà simile al seguente.

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

- Oltre a specificare un cmdlet per il recupero delle entità associate, è inoltre possibile specificare i cmdlet per aggiungere e rimuovere i riferimenti dalla raccolta. Nell'esempio seguente si presuppone che siano presenti i cmdlet Add-ProductToCategory e Remove-ProductFromCategory (possono anche essere definiti in uno script o in una funzione come nell'esempio precedente).

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

## <a name="querying-associated-entities"></a>Esecuzione di query sulle entità associate

Il client può recuperare un elenco delle istanze associate a un'entità creando query specifiche.

#### <a name="constructing-queries-for-associated-entities"></a>Creazione di query per le entità associate

- Un client può richiedere i dettagli di una categoria senza recuperare i prodotti associati. La richiesta seguente, ad esempio, ottiene i dettagli della categoria `food`.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Per ottenere i prodotti associati della categoria (ma non i dettagli della categoria stessa, il client specifica la proprietà di navigazione nella richiesta.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Per recuperare solo gli URL dei prodotti, utilizzare il qualificatore `$links` nella richiesta.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Il client può ottenere sia i dettagli della categoria che i prodotti associati utilizzando il qualificatore `$expand`.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Vedere anche

[Creazione di un servizio Web di estensione IIS OData di gestione](./creating-a-management-odata-web-service.md)