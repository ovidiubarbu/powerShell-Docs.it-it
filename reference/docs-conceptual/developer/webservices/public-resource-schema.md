---
title: Schema di risorse pubbliche | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366270"
---
# <a name="public-resource-schema"></a>Schema delle risorse pubbliche

Gestione OData USA MOF per definire le risorse e le relative proprietà. Le proprietà di un'entità OData di gestione corrispondono direttamente alle proprietà del tipo gestito restituito dal cmdlet sottostante.

## <a name="defining-a-resource"></a>Definizione di una risorsa

Ogni risorsa corrisponde a un oggetto restituito da un cmdlet di Windows PowerShell. Nel file MOF di risorse pubbliche si definisce una risorsa dichiarando una classe. La classe è costituita da proprietà che corrispondono alle proprietà dell'oggetto. Nell'esempio seguente, ad esempio, la classe [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) è rappresentata dal MOF seguente.

```csharp
class PswsTest_Process
{
    [Key] SInt32 Id;
    [Required] SInt32 BasePriority;
    [Required] SInt32 HandleCount;
    [Required] string MachineName;
    [Required] SInt32 MainWindowHandle;

    ...
};
```

Ogni nome di proprietà è preceduto da un tipo di dati. I tipi di dati di questo esempio corrispondono ai tipi di dati CLR primitivi di .NET Framework, ma le proprietà possono anche essere riferimenti ad altre risorse o tipi complessi, che vengono descritti in seguito.

Il qualificatore `Key` indica che una proprietà viene utilizzata per identificare in modo univoco un'istanza di risorsa. Una risorsa può avere più di una chiave.

Il qualificatore `Required` indica che la proprietà è obbligatoria. Se una proprietà è contrassegnata con il qualificatore `Key`, viene considerata obbligatoria e il qualificatore `Required` non è necessario.

### <a name="complex-data-types"></a>Tipi di dati complessi

Le proprietà delle entità possono avere tipi di dati complessi. I tipi di dati complessi sono tipi costituiti da altri tipi, simili a struct nel linguaggio di programmazione C. Un tipo complesso viene dichiarato nel file MOF come una classe con il qualificatore `ComplexType`, come nell'esempio seguente.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Per dichiarare una proprietà di entità come tipo complesso, dichiararla come tipo `string` con il qualificatore `EmbeddedInstance`, incluso il nome del tipo complesso. Nell'esempio seguente viene illustrata la dichiarazione di una proprietà del tipo `PswsTest_ProcessModule` dichiarata nell'esempio precedente.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associazione di entità

È possibile associare due entità usando i qualificatori Association e AssociationClass. Per ulteriori informazioni, vedere [associazione di entità OData di gestione](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipi derivati

È possibile derivare un tipo da un altro tipo. Il tipo derivato eredita tutte le proprietà del tipo da cui deriva, oltre alle proprietà derivate in modo esplicito. Nell'esempio seguente viene illustrata una dichiarazione di tipo e una dichiarazione di due tipi derivati da tale tipo.

```csharp
Class Product {

    [Key] String ProductName;

};

Class DairyProduct : Product {

    Uint16 PercentFat;
};
Class POPProduct : Product {

    Boolean IsCarbonated;
};
```