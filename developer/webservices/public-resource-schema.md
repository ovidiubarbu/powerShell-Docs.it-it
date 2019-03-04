---
title: Schema della risorsa pubblica | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e67298ee-a773-4402-8afb-d97ad0e030e5
caps.latest.revision: 4
ms.openlocfilehash: a9204ca7b28fc5792ef9bd18f6b0b24964de7386
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859547"
---
# <a name="public-resource-schema"></a>Schema delle risorse pubbliche

OData di gestione Usa MOF per definire le risorse e le relative proprietà. Le proprietà di un'entità OData di gestione corrispondono direttamente alle proprietà del tipo gestito restituito dal cmdlet sottostante.

## <a name="defining-a-resource"></a>La definizione di una risorsa

Ogni risorsa corrisponde a un oggetto restituito da un cmdlet di Windows PowerShell. Nel file MOF risorse publc, si definisce una risorsa con la dichiarazione di una classe. La classe è costituita da proprietà che corrispondono alle proprietà dell'oggetto. Ad esempio, nell'esempio seguente, il [Diagnostics](/dotnet/api/System.Diagnostics.Process) classe è rappresentata da MOF seguenti.

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

Ogni nome di proprietà è preceduto da un tipo di dati. I tipi di dati in questo esempio corrispondono ai tipi di dati primitivi CLR in .NET Framework, ma le proprietà possono anche essere riferimenti ad altre risorse o tipi complessi, entrambi descritti in un secondo momento.

Il `Key` qualificatore indica che una proprietà viene utilizzata per identificare in modo univoco un'istanza di risorsa. Una risorsa può avere più di una chiave.

Il `Required` qualificatore indica che la proprietà è obbligatoria. Se una proprietà è contrassegnata con il `Key` qualificatore, viene considerato come obbligatoria e `Required` qualificatore non è necessario.

### <a name="complex-data-types"></a>Tipi di dati complessi

Le proprietà di entità possono avere tipi di dati complessi. Tipi di dati complessi sono tipi che sono costituiti da altri tipi, simile a struct nel linguaggio di programmazione C. Un tipo complesso è dichiarato nel file MOF come una classe con il `ComplexType` qualificatore, come nell'esempio seguente.

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

Per dichiarare una proprietà di entità come un tipo complesso, si dichiara la classe come un `string` tipo con il `EmbeddedInstance` qualificatore, incluso il nome del tipo complesso. Il seguente esempio hshows la dichiarazione di una proprietà del `PswsTest_ProcessModule` tipo dichiarato nell'esempio precedente.

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a>Associazione entità

È possibile associare due entità con i qualificatori di associazione e AssocationClass. Per altre informazioni, vedere [associazione di entità OData di gestione](./associating-management-odata-entities.md).

### <a name="derived-types"></a>Tipi derivati

È possibile derivare un tipo da un altro tipo. Il tipo derivato eredita tutte le proprietà del tipo da cui deriva oltre a qualsiasi proprietà derivata in modo esplicito. Nell'esempio seguente mostra una dichiarazione del tipo e quindi una dichiarazione di due tipi derivati da questo tipo.

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