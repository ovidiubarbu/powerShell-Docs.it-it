---
title: Estensione di oggetti di output | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369720"
---
# <a name="extending-output-objects"></a><span data-ttu-id="87a8b-102">Estensione degli oggetti di output</span><span class="sxs-lookup"><span data-stu-id="87a8b-102">Extending Output Objects</span></span>

<span data-ttu-id="87a8b-103">È possibile estendere gli oggetti .NET Framework restituiti da cmdlet, funzioni e script tramite i file di tipi (con estensione ps1xml).</span><span class="sxs-lookup"><span data-stu-id="87a8b-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="87a8b-104">I file di tipi sono file basati su XML che consentono di aggiungere proprietà e metodi agli oggetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="87a8b-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="87a8b-105">Ad esempio, Windows PowerShell fornisce il file types. ps1xml, che aggiunge elementi a diversi oggetti di .NET Framework esistenti.</span><span class="sxs-lookup"><span data-stu-id="87a8b-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="87a8b-106">Il file types. ps1xml si trova nella directory di installazione di Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="87a8b-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="87a8b-107">È possibile creare un file di tipi personalizzato per estendere ulteriormente tali oggetti o per estendere altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="87a8b-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="87a8b-108">Quando si estende un oggetto utilizzando un file di tipi, qualsiasi istanza dell'oggetto viene estesa con i nuovi elementi.</span><span class="sxs-lookup"><span data-stu-id="87a8b-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="87a8b-109">Estensione dell'oggetto System. Array</span><span class="sxs-lookup"><span data-stu-id="87a8b-109">Extending the System.Array Object</span></span>

<span data-ttu-id="87a8b-110">Nell'esempio seguente viene illustrato come Windows PowerShell estende l'oggetto [System. Array](/dotnet/api/System.Array) nel file types. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="87a8b-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="87a8b-111">Per impostazione predefinita, gli oggetti [System. Array](/dotnet/api/System.Array) hanno una proprietà `Length` che elenca il numero di oggetti nella matrice.</span><span class="sxs-lookup"><span data-stu-id="87a8b-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="87a8b-112">Tuttavia, poiché il nome "length" non descrive chiaramente la proprietà, Windows PowerShell aggiunge la proprietà alias `Count`, che visualizza lo stesso valore della proprietà `Length`.</span><span class="sxs-lookup"><span data-stu-id="87a8b-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="87a8b-113">Nel codice XML seguente viene aggiunta la proprietà `Count` al tipo [System. Array](/dotnet/api/System.Array) .</span><span class="sxs-lookup"><span data-stu-id="87a8b-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

```xml
<Type>
  <Name>System.Array</Name>
  <Members>
    <AliasProperty>
      <Name>Count</Name>
      <ReferencedMemberName>Length</ReferencedMemberName>
    </AliasProperty>
  </Members>
</Type>

```

<span data-ttu-id="87a8b-114">Per visualizzare la nuova proprietà alias, usare un comando [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) in qualsiasi matrice, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="87a8b-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="87a8b-115">Il comando restituisce i risultati seguenti.</span><span class="sxs-lookup"><span data-stu-id="87a8b-115">The command returns the following results.</span></span>
```output
Name           MemberType    Definition
----           ----------    ----------
Count          AliasProperty Count = Length
Address        Method        System.Object& Address(Int32 )
Clone          Method        System.Object Clone()
CopyTo         Method        System.Void CopyTo(Array array, Int32 index):
Equals         Method        System.Boolean Equals(Object obj)
Get            Method        System.Object Get(Int32 )
...
Length         Property      System.Int32 Length {get;}
```
<span data-ttu-id="87a8b-116">Per determinare il numero di oggetti in una matrice, è possibile usare la proprietà `Count` o la proprietà `Length`.</span><span class="sxs-lookup"><span data-stu-id="87a8b-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="87a8b-117">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="87a8b-117">For example:</span></span>

```powershell
PS> (1, 2, 3, 4).Count
```

```output
4
```

```powershell
PS> (1, 2, 3, 4).Length
```

```output
4
```

## <a name="custom-types-files"></a><span data-ttu-id="87a8b-118">File di tipi personalizzati</span><span class="sxs-lookup"><span data-stu-id="87a8b-118">Custom Types Files</span></span>

<span data-ttu-id="87a8b-119">Per creare un file di tipi personalizzati, iniziare copiando un file di tipi esistente.</span><span class="sxs-lookup"><span data-stu-id="87a8b-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="87a8b-120">Il nuovo file può avere un nome qualsiasi, ma deve avere un'estensione del nome file. ps1xml.</span><span class="sxs-lookup"><span data-stu-id="87a8b-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="87a8b-121">Quando si copia il file, è possibile inserire il nuovo file in qualsiasi directory accessibile a Windows PowerShell, ma è utile inserire i file nella directory di installazione di Windows PowerShell (`$pshome`) o in una sottodirectory della directory di installazione.</span><span class="sxs-lookup"><span data-stu-id="87a8b-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="87a8b-122">Per aggiungere tipi estesi personalizzati al file, aggiungere un elemento types per ogni oggetto che si desidera estendere.</span><span class="sxs-lookup"><span data-stu-id="87a8b-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="87a8b-123">Negli argomenti seguenti vengono forniti esempi.</span><span class="sxs-lookup"><span data-stu-id="87a8b-123">The following topics provide examples.</span></span>

- <span data-ttu-id="87a8b-124">Per ulteriori informazioni sull'aggiunta di proprietà e set di proprietà, vedere [proprietà estese](./extending-properties-for-objects.md) .</span><span class="sxs-lookup"><span data-stu-id="87a8b-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="87a8b-125">Per ulteriori informazioni sull'aggiunta di metodi, vedere [metodi estesi](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="87a8b-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="87a8b-126">Per ulteriori informazioni sull'aggiunta di set di membri, vedere [set di membri estesi](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="87a8b-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="87a8b-127">Dopo aver definito i tipi estesi personalizzati, usare uno dei metodi seguenti per rendere disponibili gli oggetti estesi:</span><span class="sxs-lookup"><span data-stu-id="87a8b-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="87a8b-128">Per rendere disponibile il file dei tipi estesi per la sessione corrente, usare il cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) per aggiungere il nuovo file.</span><span class="sxs-lookup"><span data-stu-id="87a8b-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="87a8b-129">Se si vuole che i tipi abbiano la precedenza sui tipi definiti in altri file di tipi (incluso il file types. ps1xml), usare il parametro `PrependData` del cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .</span><span class="sxs-lookup"><span data-stu-id="87a8b-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="87a8b-130">Per rendere il file di tipi estesi disponibile per tutte le sessioni future, aggiungere il file di tipi a un modulo, esportare la sessione corrente o aggiungere il comando [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) al profilo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="87a8b-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="87a8b-131">Tipi di firma file</span><span class="sxs-lookup"><span data-stu-id="87a8b-131">Signing Types Files</span></span>

<span data-ttu-id="87a8b-132">I tipi di file devono essere firmati digitalmente per evitare manomissioni perché il codice XML può includere blocchi di script.</span><span class="sxs-lookup"><span data-stu-id="87a8b-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="87a8b-133">Per ulteriori informazioni sull'aggiunta di firme digitali, vedere [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="87a8b-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="87a8b-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="87a8b-134">See Also</span></span>

[<span data-ttu-id="87a8b-135">Definizione delle proprietà predefinite per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="87a8b-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="87a8b-136">Definizione dei metodi predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="87a8b-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="87a8b-137">Definizione dei set di membri predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="87a8b-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="87a8b-138">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="87a8b-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
