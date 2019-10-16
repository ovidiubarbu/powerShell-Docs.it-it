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
# <a name="public-resource-schema"></a><span data-ttu-id="e4dce-102">Schema delle risorse pubbliche</span><span class="sxs-lookup"><span data-stu-id="e4dce-102">Public Resource Schema</span></span>

<span data-ttu-id="e4dce-103">Gestione OData USA MOF per definire le risorse e le relative proprietà.</span><span class="sxs-lookup"><span data-stu-id="e4dce-103">Management OData uses MOF to define resources and their properties.</span></span> <span data-ttu-id="e4dce-104">Le proprietà di un'entità OData di gestione corrispondono direttamente alle proprietà del tipo gestito restituito dal cmdlet sottostante.</span><span class="sxs-lookup"><span data-stu-id="e4dce-104">The properties of a Management OData entity correspond directly to the properties of the managed type returned by the underlying cmdlet.</span></span>

## <a name="defining-a-resource"></a><span data-ttu-id="e4dce-105">Definizione di una risorsa</span><span class="sxs-lookup"><span data-stu-id="e4dce-105">Defining a resource</span></span>

<span data-ttu-id="e4dce-106">Ogni risorsa corrisponde a un oggetto restituito da un cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e4dce-106">Each resource corresponds to an object returned by a Windows PowerShell cmdlet.</span></span> <span data-ttu-id="e4dce-107">Nel file MOF di risorse pubbliche si definisce una risorsa dichiarando una classe.</span><span class="sxs-lookup"><span data-stu-id="e4dce-107">In the public resource MOF file, you define a resource by declaring a class.</span></span> <span data-ttu-id="e4dce-108">La classe è costituita da proprietà che corrispondono alle proprietà dell'oggetto.</span><span class="sxs-lookup"><span data-stu-id="e4dce-108">The class consists of properties that correspond to the properties of the object.</span></span> <span data-ttu-id="e4dce-109">Nell'esempio seguente, ad esempio, la classe [System. Diagnostics. Process](/dotnet/api/System.Diagnostics.Process) è rappresentata dal MOF seguente.</span><span class="sxs-lookup"><span data-stu-id="e4dce-109">For example, in the following example, the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) class is represented by the following MOF.</span></span>

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

<span data-ttu-id="e4dce-110">Ogni nome di proprietà è preceduto da un tipo di dati.</span><span class="sxs-lookup"><span data-stu-id="e4dce-110">Each property name is preceded by a data type.</span></span> <span data-ttu-id="e4dce-111">I tipi di dati di questo esempio corrispondono ai tipi di dati CLR primitivi di .NET Framework, ma le proprietà possono anche essere riferimenti ad altre risorse o tipi complessi, che vengono descritti in seguito.</span><span class="sxs-lookup"><span data-stu-id="e4dce-111">The data types in this example correspond to primitive CLR data types in the .NET Frameworks, but properties can also be references to other resources or complex types, which are both described later.</span></span>

<span data-ttu-id="e4dce-112">Il qualificatore `Key` indica che una proprietà viene utilizzata per identificare in modo univoco un'istanza di risorsa.</span><span class="sxs-lookup"><span data-stu-id="e4dce-112">The `Key` qualifier indicates that a property is used to uniquely identify a resource instance.</span></span> <span data-ttu-id="e4dce-113">Una risorsa può avere più di una chiave.</span><span class="sxs-lookup"><span data-stu-id="e4dce-113">A resource can have more than one key.</span></span>

<span data-ttu-id="e4dce-114">Il qualificatore `Required` indica che la proprietà è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="e4dce-114">The `Required` qualifier indicates that the property is required.</span></span> <span data-ttu-id="e4dce-115">Se una proprietà è contrassegnata con il qualificatore `Key`, viene considerata obbligatoria e il qualificatore `Required` non è necessario.</span><span class="sxs-lookup"><span data-stu-id="e4dce-115">If a property is labeled with the `Key` qualifier, it is considered to be required, and the `Required` qualifier is not necessary.</span></span>

### <a name="complex-data-types"></a><span data-ttu-id="e4dce-116">Tipi di dati complessi</span><span class="sxs-lookup"><span data-stu-id="e4dce-116">Complex data types</span></span>

<span data-ttu-id="e4dce-117">Le proprietà delle entità possono avere tipi di dati complessi.</span><span class="sxs-lookup"><span data-stu-id="e4dce-117">Properties of entities can have complex data types.</span></span> <span data-ttu-id="e4dce-118">I tipi di dati complessi sono tipi costituiti da altri tipi, simili a struct nel linguaggio di programmazione C.</span><span class="sxs-lookup"><span data-stu-id="e4dce-118">Complex data types are types that are made up of other types, similar to structs in the C programming language.</span></span> <span data-ttu-id="e4dce-119">Un tipo complesso viene dichiarato nel file MOF come una classe con il qualificatore `ComplexType`, come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="e4dce-119">A complex type is declared in the MOF file as a class with the `ComplexType` qualifier, as in the following example.</span></span>

```csharp
[ComplexType]
class PswsTest_ProcessModule
{
    String ModuleName;
    String FileName;
};
```

<span data-ttu-id="e4dce-120">Per dichiarare una proprietà di entità come tipo complesso, dichiararla come tipo `string` con il qualificatore `EmbeddedInstance`, incluso il nome del tipo complesso.</span><span class="sxs-lookup"><span data-stu-id="e4dce-120">To declare an entity property as a complex type, you declare it as a `string` type with the `EmbeddedInstance` qualifier, including the name of the complex type.</span></span> <span data-ttu-id="e4dce-121">Nell'esempio seguente viene illustrata la dichiarazione di una proprietà del tipo `PswsTest_ProcessModule` dichiarata nell'esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="e4dce-121">The following example shows the declaration of a property of the `PswsTest_ProcessModule` type declared in the previous example.</span></span>

```csharp
[Required, EmbeddedInstance("PswsTest_ProcessModule")] String Modules[];
```

### <a name="associating-entities"></a><span data-ttu-id="e4dce-122">Associazione di entità</span><span class="sxs-lookup"><span data-stu-id="e4dce-122">Associating entities</span></span>

<span data-ttu-id="e4dce-123">È possibile associare due entità usando i qualificatori Association e AssociationClass.</span><span class="sxs-lookup"><span data-stu-id="e4dce-123">You can associate two entities by using the Association and AssociationClass qualifiers.</span></span> <span data-ttu-id="e4dce-124">Per ulteriori informazioni, vedere [associazione di entità OData di gestione](./associating-management-odata-entities.md).</span><span class="sxs-lookup"><span data-stu-id="e4dce-124">For more information, see [Associating Management OData Entities](./associating-management-odata-entities.md).</span></span>

### <a name="derived-types"></a><span data-ttu-id="e4dce-125">Tipi derivati</span><span class="sxs-lookup"><span data-stu-id="e4dce-125">Derived types</span></span>

<span data-ttu-id="e4dce-126">È possibile derivare un tipo da un altro tipo.</span><span class="sxs-lookup"><span data-stu-id="e4dce-126">You can derive a type from another type.</span></span> <span data-ttu-id="e4dce-127">Il tipo derivato eredita tutte le proprietà del tipo da cui deriva, oltre alle proprietà derivate in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="e4dce-127">The derived type inherits all of the properties of the type from which it derives in addition to any properties explicitly derived.</span></span> <span data-ttu-id="e4dce-128">Nell'esempio seguente viene illustrata una dichiarazione di tipo e una dichiarazione di due tipi derivati da tale tipo.</span><span class="sxs-lookup"><span data-stu-id="e4dce-128">The following example shows a type declaration and then a declaration of two types derived from that type.</span></span>

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