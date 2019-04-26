---
title: Associare le entità OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 947a3add-3593-400d-8144-8b44c8adbe5e
caps.latest.revision: 5
ms.openlocfilehash: 44b718e024eb98ac562edb50076287a31f5edc6b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080748"
---
# <a name="associating-management-odata-entities"></a>Associazione delle entità OData di gestione

Spesso è utile creare un'associazione tra due entità OData di gestione diversi. Ad esempio, un servizio OData di gestione è stato possibile disporre di entità che gestiscono un catalogo dei prodotti organizzate in categorie e definire le entità `Product` e `Category`. Associando queste due entità, un client può ottenere informazioni su tutti i prodotti in una categoria con una singola richiesta al servizio web.

Un esempio che illustra come creare associazioni tra entità può essere scaricato dalla [esempio di associazione](https://code.msdn.microsoft.com:443/windowsdesktop/Association-sample-0f0fa87e).

## <a name="creating-the-association-in-the-resource-schema-file"></a>Crea l'associazione nel file di schema di risorse

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

Il `Category` classe definisce una proprietà che è una matrice dei nomi dei prodotti che appartengono alla categoria.

Per associare due entità, è necessario definire una classe con il `Association` attributo nel file MOF dello schema di risorse per il servizio. La classe deve definire le due entità per essere associato, chiamato `ends` dell'associazione. Nell'esempio seguente viene illustrata una definizione di una classe che definisce un'associazione tra le entità di categoria e i prodotti.

```csharp
[Association]
class ProductCategory {
Category ref theCategory;
Product ref theProducts;
}
```

È anche necessario modificare la dichiarazione della proprietà Products della classe della categoria. Si utilizza il `AssociationClass` parola chiave per specificare che la proprietà è un'estremità dell'associazione. La proprietà deve essere definita anche come riferimento a un'entità distinta, anziché una matrice di stringhe. Eseguire questa operazione usando il `ref` (parola chiave). Nell'esempio seguente illustra la definizione di proprietà per l'associazione.

```csharp
class Sample_Category {

[key] string CategoryName;

[AssociationClass("Sample_ProductCategory"),ToEnd("theProducts")]
Sample_Product ref AssociatedProducts[];
};
```

Infine, è necessario dichiarare l'altra estremità dell'associazione tramite l'aggiunta di una definizione di proprietà per il `Product` classe. Si tratta di un riferimento a una matrice o a una singola entità. Supponendo che ogni prodotto appartiene a una sola categoria, la definizione sarà come indicato di seguito.

```csharp
class Sample_Product {

[key] string ProductName;
[AssociationClass("Sample_ProductCategory"),ToEnd("theCategory")]
Sample_Category ref AssociatedCategory;
};
```

Le proprietà che rappresentano le due estremità dell'associazione sono definite proprietà di navigazione.

#### <a name="steps-for-associating-entities-in-the-resource-schema-file"></a>Passaggi per l'associazione di entità nel file di schema di risorse

- Definire l'associazione come una classe usando la `Association` (parola chiave).

- Definire le entità finali dell'associazione utilizzando la parola chiave AssociationClass per qualificare le proprietà delle entità associate.

## <a name="creating-the-association-in-the-resource-mapping-xml-file"></a>Crea l'associazione nel file XML di mapping di risorse

Esistono tre casi diversi da prendere in considerazione durante il mapping di un'associazione nel file XML di mapping di risorse.

#### <a name="determining-how-to-associate-entities-in-the-resource-mapping-file"></a>Determinare come associare le entità nel file di mapping di risorse

- Se la proprietà di navigazione è presente nell'oggetto sottostante. Tipo .NET framework e tale proprietà contiene le chiavi esterne, è necessario alcun mapping esplicito.

- Se la proprietà di navigazione non esiste nel tipo sottostante di .NET Framework, è necessario specificare un cmdlet che recupera l'elenco di chiavi delle istanze associate. Eseguire questa operazione aggiungendo un `Association` elemento annidato sotto la `CmdletImplementation` elemento, che segue gli elementi che definiscono il `cmdlets` per altri comandi CRUD.

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

- Se la proprietà di navigazione esiste nel tipo sottostante di .NET Framework, ma contiene istanze degli oggetti invece di chiavi esterne, quindi è necessario creare un cmdlet (scrivendo una funzione di Windows PowerShell o script) per recuperare le chiavi esterne. È quindi possibile specificare tale cmdlet nel file di mapping di risorse. Lo script per recuperare le chiavi, ad esempio, avrebbe un aspetto simile al seguente.

  ```
  Param(
      [string] $Key
      )

  (get-category $key).AssociatedProducts

  ```

  E il codice XML nel file di mapping di risorse potrebbe essere simile al seguente.

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

- Oltre a specificare un cmdlet per recuperare le entità associate, è possibile specificare anche i cmdlet per aggiungere e rimuovere i riferimenti dalla raccolta. L'esempio seguente presuppone che il cmdlet Add-ProductToCategory e Remove-ProductFromCategory esista (possono anche essere definiti in uno script o una funzione dell'esempio precedente).

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

## <a name="querying-associated-entities"></a>Esecuzione di query su entità associate

Il client può recuperare un elenco delle istanze di cui è associata a un'entità mediante la creazione di query specifiche.

#### <a name="constructing-queries-for-associated-entities"></a>Costruzione delle query per le entità associate

- Un client può richiedere i dettagli di una categoria senza recuperare i prodotti associati. Ad esempio, la richiesta seguente ottiene i dettagli del `food` categoria.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')
  ```

  Per ottenere i prodotti della categoria associati (ma non i dettagli della categoria, il client specifica la proprietà di navigazione nella richiesta.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/AssociatedProducts
  ```

- Per recuperare solo gli URL dei prodotti, utilizzare il `$links` qualificatore nella richiesta.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')/$links/AssociatedProducts
  ```

- Il client può ottenere i dettagli di categoria sia i prodotti associati usando il `$expand` qualificatore.

  ```
  http://localhost:7000/MODataSvc/sample.svc/Category('food')?$expand=AssociatedProducts
  ```

## <a name="see-also"></a>Vedere anche

[Creazione di un servizio Web di estensione IIS OData gestione](./creating-a-management-odata-web-service.md)