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
ms.openlocfilehash: c7e20ff0f36e8cab2d414ff2e5924b3359ad9c60
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057247"
---
# <a name="public-resource-schema"></a><span data-ttu-id="43479-102">Schema delle risorse pubbliche</span><span class="sxs-lookup"><span data-stu-id="43479-102">Public Resource Schema</span></span>

<span data-ttu-id="43479-103">OData di gestione Usa MOF per definire le risorse e le relative proprietà.</span><span class="sxs-lookup"><span data-stu-id="43479-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="43479-104">Le proprietà di un'entità OData di gestione corrispondono direttamente alle proprietà del tipo gestito restituito dal cmdlet sottostante.</span><span class="sxs-lookup"><span data-stu-id="43479-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="43479-105">La definizione di una risorsa</span><span class="sxs-lookup"><span data-stu-id="43479-105">Defining a resource</span></span>

<span data-ttu-id="43479-106">Ogni risorsa corrisponde a un oggetto restituito da un cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43479-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="43479-107">Nella risorsa pubblica file MOF, si definisce una risorsa con la dichiarazione di una classe.</span><span class="sxs-lookup"><span data-stu-id="43479-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="43479-108">La classe è costituita da proprietà che corrispondono alle proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="43479-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="43479-109">Ad esempio, nell'esempio seguente, il [Diagnostics](/dotnet/api/System.Diagnostics.Process) classe è rappresentata da MOF seguenti.</span><span class="sxs-lookup"><span data-stu-id="43479-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="43479-110">Ogni nome di proprietà è preceduto da un tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="43479-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="43479-111">I tipi di dati in questo esempio corrispondono ai tipi di dati primitivi CLR in .NET Framework, ma le proprietà possono anche essere riferimenti ad altre risorse o tipi complessi, entrambi descritti in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="43479-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="43479-112">Il `Key` qualificatore indica che una proprietà viene utilizzata per identificare in modo univoco un'istanza di risorsa.</span><span class="sxs-lookup"><span data-stu-id="43479-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="43479-113">Una risorsa può avere più di una chiave.</span><span class="sxs-lookup"><span data-stu-id="43479-113">A resource can have more than one key.</span></span>

<span data-ttu-id="43479-114">Il `Required` qualificatore indica che la proprietà è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="43479-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="43479-115">Se una proprietà è contrassegnata con il `Key` qualificatore, viene considerato come obbligatoria e `Required` qualificatore non è necessario.</span><span class="sxs-lookup"><span data-stu-id="43479-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="43479-116">Tipi di dati complessi</span><span class="sxs-lookup"><span data-stu-id="43479-116">Complex data types</span></span>

<span data-ttu-id="43479-117">Le proprietà di entità possono avere tipi di dati complessi.</span><span class="sxs-lookup"><span data-stu-id="43479-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="43479-118">Tipi di dati complessi sono tipi che sono costituiti da altri tipi, simile a struct nel linguaggio di programmazione C.</span><span class="sxs-lookup"><span data-stu-id="43479-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="43479-119">Un tipo complesso è dichiarato nel file MOF come una classe con il `ComplexType` qualificatore, come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="43479-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="43479-120">Per dichiarare una proprietà di entità come un tipo complesso, si dichiara la classe come un `string` tipo con il `EmbeddedInstance` qualificatore, incluso il nome del tipo complesso.</span><span class="sxs-lookup"><span data-stu-id="43479-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="43479-121">Nell'esempio seguente illustra la dichiarazione di una proprietà del `PswsTest_ProcessModule` tipo dichiarato nell'esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="43479-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="43479-122">Associazione entità</span><span class="sxs-lookup"><span data-stu-id="43479-122">Associating entities</span></span>

<span data-ttu-id="43479-123">È possibile associare due entità con i qualificatori di associazione e AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="43479-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="43479-124">Per altre informazioni, vedere [associazione di entità OData di gestione](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="43479-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="43479-125">Tipi derivati</span><span class="sxs-lookup"><span data-stu-id="43479-125">Derived types</span></span>

<span data-ttu-id="43479-126">È possibile derivare un tipo da un altro tipo.</span><span class="sxs-lookup"><span data-stu-id="43479-126">You can derive a type from another type.</span></span> <span data-ttu-id="43479-127">Il tipo derivato eredita tutte le proprietà del tipo da cui deriva oltre a qualsiasi proprietà derivata in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="43479-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="43479-128">Nell'esempio seguente mostra una dichiarazione del tipo e quindi una dichiarazione di due tipi derivati da questo tipo.</span><span class="sxs-lookup"><span data-stu-id="43479-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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