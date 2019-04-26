---
title: Estensione di oggetti di Output | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a252e0ec-d456-42d7-bd49-d6b8bc57f388
caps.latest.revision: 11
ms.openlocfilehash: 9c9d50c880f843e21621e5735c800e3afb48b2ad
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068165"
---
# <a name="extending-output-objects"></a><span data-ttu-id="77a98-102">Estensione degli oggetti di output</span><span class="sxs-lookup"><span data-stu-id="77a98-102">Extending Output Objects</span></span>

<span data-ttu-id="77a98-103">È possibile estendere gli oggetti di .NET Framework che vengono restituiti dal cmdlet, funzioni e gli script utilizzando il file di tipi (con estensione PS1XML).</span><span class="sxs-lookup"><span data-stu-id="77a98-103">You can extend the .NET Framework objects that are returned by cmdlets, functions, and scripts by using types files (.ps1xml).</span></span> <span data-ttu-id="77a98-104">Tipi file sono file basati su XML che consentono di aggiungere proprietà e metodi agli oggetti esistenti.</span><span class="sxs-lookup"><span data-stu-id="77a98-104">Types files are XML-based files that let you add properties and methods to existing objects.</span></span> <span data-ttu-id="77a98-105">Ad esempio, Windows PowerShell fornisce il file Types.ps1xml, che aggiunge elementi a più oggetti di .NET Framework esistenti.</span><span class="sxs-lookup"><span data-stu-id="77a98-105">For example, Windows PowerShell provides the Types.ps1xml file, which adds elements to several existing .NET Framework objects.</span></span> <span data-ttu-id="77a98-106">Il file Types.ps1xml si trova nella directory di installazione di Windows PowerShell (`$pshome`).</span><span class="sxs-lookup"><span data-stu-id="77a98-106">The Types.ps1xml file is located in the Windows PowerShell installation directory (`$pshome`).</span></span> <span data-ttu-id="77a98-107">È possibile creare il proprio file di tipi per estendere ulteriormente gli oggetti o per estendere altri oggetti.</span><span class="sxs-lookup"><span data-stu-id="77a98-107">You can create your own types file to further extend those objects or to extend other objects.</span></span> <span data-ttu-id="77a98-108">Quando si estende un oggetto usando un file di tipi, qualsiasi istanza dell'oggetto viene estesa con i nuovi elementi.</span><span class="sxs-lookup"><span data-stu-id="77a98-108">When you extend an object by using a types file, any instance of the object is extended with the new elements.</span></span>

## <a name="extending-the-systemarray-object"></a><span data-ttu-id="77a98-109">Estendendo l'oggetto System. Array</span><span class="sxs-lookup"><span data-stu-id="77a98-109">Extending the System.Array Object</span></span>

<span data-ttu-id="77a98-110">L'esempio seguente mostra in che modo Windows PowerShell estende la [System. Array](/dotnet/api/System.Array) oggetto nel file Types.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="77a98-110">The following example shows how Windows PowerShell extends the [System.Array](/dotnet/api/System.Array) object in the Types.ps1xml file.</span></span> <span data-ttu-id="77a98-111">Per impostazione predefinita [System. Array](/dotnet/api/System.Array) gli oggetti hanno una `Length` proprietà elenca il numero di oggetti nella matrice.</span><span class="sxs-lookup"><span data-stu-id="77a98-111">By default, [System.Array](/dotnet/api/System.Array) objects have a `Length` property that lists the number of objects in the array.</span></span> <span data-ttu-id="77a98-112">Tuttavia, poiché la lunghezza"nome" non descrive chiaramente la proprietà, Windows PowerShell aggiunge il `Count` proprietà alias, che consente di visualizzare lo stesso valore di `Length` proprietà.</span><span class="sxs-lookup"><span data-stu-id="77a98-112">However, because the name "length" does not clearly describe the property, Windows PowerShell adds the `Count` alias property, which displays the same value as the `Length` property.</span></span> <span data-ttu-id="77a98-113">Il codice XML seguente aggiunge il `Count` proprietà per il [System. Array](/dotnet/api/System.Array) tipo.</span><span class="sxs-lookup"><span data-stu-id="77a98-113">The following XML adds the `Count` property to the [System.Array](/dotnet/api/System.Array) type.</span></span>

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

<span data-ttu-id="77a98-114">Per visualizzare questa nuova proprietà alias, usare una [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando su qualsiasi matrice, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="77a98-114">To see this new alias property, use a [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) command on any array, as shown in the following example.</span></span>

```powershell
Get-Member -InputObject (1,2,3,4)
```

<span data-ttu-id="77a98-115">Il comando restituisce i risultati seguenti.</span><span class="sxs-lookup"><span data-stu-id="77a98-115">The command returns the following results.</span></span>
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
<span data-ttu-id="77a98-116">È possibile usare la `Count` proprietà o il `Length` proprietà per determinare il numero di oggetti presenti in una matrice.</span><span class="sxs-lookup"><span data-stu-id="77a98-116">You can use either the `Count` property or the `Length` property to determine how many objects are in an array.</span></span> <span data-ttu-id="77a98-117">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="77a98-117">For example:</span></span>

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

## <a name="custom-types-files"></a><span data-ttu-id="77a98-118">File di tipi personalizzati</span><span class="sxs-lookup"><span data-stu-id="77a98-118">Custom Types Files</span></span>

<span data-ttu-id="77a98-119">Per creare un file di tipi personalizzati, avviare copiando un file esistente di tipi.</span><span class="sxs-lookup"><span data-stu-id="77a98-119">To create a custom types file, start by copying an existing types file.</span></span> <span data-ttu-id="77a98-120">Il nuovo file può avere qualsiasi nome, ma deve avere un'estensione di file con estensione ps1xml.</span><span class="sxs-lookup"><span data-stu-id="77a98-120">The new file can have any name, but it must have a .ps1xml file name extension.</span></span> <span data-ttu-id="77a98-121">Quando si copia il file, è possibile inserire il nuovo file in qualsiasi directory accessibile a Windows PowerShell, ma è utile inserire i file nella directory di installazione di Windows PowerShell (`$pshome`) o in una sottodirectory della directory di installazione.</span><span class="sxs-lookup"><span data-stu-id="77a98-121">When you copy the file, you can place the new file in any directory that is accessible to Windows PowerShell, but it is useful to place the files in the Windows PowerShell installation directory (`$pshome`) or in a subdirectory of the installation directory.</span></span>

<span data-ttu-id="77a98-122">Per aggiungere i tipi estesi per il file, aggiungere un elemento di tipi per ogni oggetto che si vuole estendere.</span><span class="sxs-lookup"><span data-stu-id="77a98-122">To add your own extended types to the file, add a types element for each object that you want to extend.</span></span> <span data-ttu-id="77a98-123">Gli argomenti seguenti forniscono esempi.</span><span class="sxs-lookup"><span data-stu-id="77a98-123">The following topics provide examples.</span></span>

- <span data-ttu-id="77a98-124">Per altre informazioni sull'aggiunta di proprietà e set di proprietà, vedere [proprietà estese](./extending-properties-for-objects.md)</span><span class="sxs-lookup"><span data-stu-id="77a98-124">For more information about adding properties and property sets, see [Extended Properties](./extending-properties-for-objects.md)</span></span>

- <span data-ttu-id="77a98-125">Per altre informazioni sull'aggiunta di metodi, vedere [metodi estesi](./defining-default-methods-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="77a98-125">For more information about adding methods, see [Extended Methods](./defining-default-methods-for-objects.md).</span></span>

- <span data-ttu-id="77a98-126">Per altre informazioni sull'aggiunta di set di membri, vedere [esteso set di membri](./defining-default-member-sets-for-objects.md).</span><span class="sxs-lookup"><span data-stu-id="77a98-126">For more information about adding member sets, see [Extended Member Sets](./defining-default-member-sets-for-objects.md).</span></span>

<span data-ttu-id="77a98-127">Dopo aver definito i tipi estesi, è possibile usare uno dei metodi seguenti per rendere disponibili gli oggetti estesi:</span><span class="sxs-lookup"><span data-stu-id="77a98-127">After you define your own extended types, use one of the following methods to make your extended objects available:</span></span>

- <span data-ttu-id="77a98-128">Per rendere il file di tipi estesi disponibili per la sessione corrente, usare il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet per aggiungere il nuovo file.</span><span class="sxs-lookup"><span data-stu-id="77a98-128">To make your extended types file available to the current session, use the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet to add the new file.</span></span> <span data-ttu-id="77a98-129">Se si desidera che i tipi hanno la precedenza sui tipi definiti in altri tipi di file (inclusi i file Types.ps1xml), usare il `PrependData` parametro il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="77a98-129">If you want your types to take precedence over the types that are defined in other types files (including the Types.ps1xml file), use the `PrependData` parameter of the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.</span></span>
- <span data-ttu-id="77a98-130">Per rendere il file di tipi estesi disponibili per tutte le sessioni future, aggiungere il file dei tipi a un modulo, esportare la sessione corrente o aggiungere il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando al profilo di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="77a98-130">To make your extended types file available to all future sessions, add the types file to a module, export the current session, or add the [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) command to your Windows PowerShell profile.</span></span>

## <a name="signing-types-files"></a><span data-ttu-id="77a98-131">La firma dei file di tipi</span><span class="sxs-lookup"><span data-stu-id="77a98-131">Signing Types Files</span></span>

<span data-ttu-id="77a98-132">Tipi file devono essere firmati digitalmente da eventuali manomissioni perché il codice XML può includere i blocchi di script.</span><span class="sxs-lookup"><span data-stu-id="77a98-132">Types files should be digitally signed to prevent tampering because the XML can include script blocks.</span></span> <span data-ttu-id="77a98-133">Per altre informazioni sull'aggiunta di firme digitali, vedere [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="77a98-133">For more information about adding digital signatures, see [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)</span></span>

## <a name="see-also"></a><span data-ttu-id="77a98-134">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="77a98-134">See Also</span></span>

[<span data-ttu-id="77a98-135">Definizione di proprietà predefinite per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="77a98-135">Defining Default Properties for Objects</span></span>](./extending-properties-for-objects.md)

[<span data-ttu-id="77a98-136">Definizione di metodi predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="77a98-136">Defining Default Methods for Objects</span></span>](./defining-default-methods-for-objects.md)

[<span data-ttu-id="77a98-137">Definizione di set di membri predefiniti per gli oggetti</span><span class="sxs-lookup"><span data-stu-id="77a98-137">Defining Default Member Sets for Objects</span></span>](./defining-default-member-sets-for-objects.md)

[<span data-ttu-id="77a98-138">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="77a98-138">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
