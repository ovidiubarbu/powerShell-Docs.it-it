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
# <a name="extending-output-objects"></a>Estensione degli oggetti di output

È possibile estendere gli oggetti .NET Framework restituiti da cmdlet, funzioni e script tramite i file di tipi (con estensione ps1xml). I file di tipi sono file basati su XML che consentono di aggiungere proprietà e metodi agli oggetti esistenti. Ad esempio, Windows PowerShell fornisce il file types. ps1xml, che aggiunge elementi a diversi oggetti di .NET Framework esistenti. Il file types. ps1xml si trova nella directory di installazione di Windows PowerShell (`$pshome`). È possibile creare un file di tipi personalizzato per estendere ulteriormente tali oggetti o per estendere altri oggetti. Quando si estende un oggetto utilizzando un file di tipi, qualsiasi istanza dell'oggetto viene estesa con i nuovi elementi.

## <a name="extending-the-systemarray-object"></a>Estensione dell'oggetto System. Array

Nell'esempio seguente viene illustrato come Windows PowerShell estende l'oggetto [System. Array](/dotnet/api/System.Array) nel file types. ps1xml. Per impostazione predefinita, gli oggetti [System. Array](/dotnet/api/System.Array) hanno una proprietà `Length` che elenca il numero di oggetti nella matrice. Tuttavia, poiché il nome "length" non descrive chiaramente la proprietà, Windows PowerShell aggiunge la proprietà alias `Count`, che visualizza lo stesso valore della proprietà `Length`. Nel codice XML seguente viene aggiunta la proprietà `Count` al tipo [System. Array](/dotnet/api/System.Array) .

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

Per visualizzare la nuova proprietà alias, usare un comando [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) in qualsiasi matrice, come illustrato nell'esempio seguente.

```powershell
Get-Member -InputObject (1,2,3,4)
```

Il comando restituisce i risultati seguenti.
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
Per determinare il numero di oggetti in una matrice, è possibile usare la proprietà `Count` o la proprietà `Length`. Ad esempio:

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

## <a name="custom-types-files"></a>File di tipi personalizzati

Per creare un file di tipi personalizzati, iniziare copiando un file di tipi esistente. Il nuovo file può avere un nome qualsiasi, ma deve avere un'estensione del nome file. ps1xml. Quando si copia il file, è possibile inserire il nuovo file in qualsiasi directory accessibile a Windows PowerShell, ma è utile inserire i file nella directory di installazione di Windows PowerShell (`$pshome`) o in una sottodirectory della directory di installazione.

Per aggiungere tipi estesi personalizzati al file, aggiungere un elemento types per ogni oggetto che si desidera estendere. Negli argomenti seguenti vengono forniti esempi.

- Per ulteriori informazioni sull'aggiunta di proprietà e set di proprietà, vedere [proprietà estese](./extending-properties-for-objects.md) .

- Per ulteriori informazioni sull'aggiunta di metodi, vedere [metodi estesi](./defining-default-methods-for-objects.md).

- Per ulteriori informazioni sull'aggiunta di set di membri, vedere [set di membri estesi](./defining-default-member-sets-for-objects.md).

Dopo aver definito i tipi estesi personalizzati, usare uno dei metodi seguenti per rendere disponibili gli oggetti estesi:

- Per rendere disponibile il file dei tipi estesi per la sessione corrente, usare il cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) per aggiungere il nuovo file. Se si vuole che i tipi abbiano la precedenza sui tipi definiti in altri file di tipi (incluso il file types. ps1xml), usare il parametro `PrependData` del cmdlet [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) .
- Per rendere il file di tipi estesi disponibile per tutte le sessioni future, aggiungere il file di tipi a un modulo, esportare la sessione corrente o aggiungere il comando [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) al profilo di Windows PowerShell.

## <a name="signing-types-files"></a>Tipi di firma file

I tipi di file devono essere firmati digitalmente per evitare manomissioni perché il codice XML può includere blocchi di script. Per ulteriori informazioni sull'aggiunta di firme digitali, vedere [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Vedere anche

[Definizione delle proprietà predefinite per gli oggetti](./extending-properties-for-objects.md)

[Definizione dei metodi predefiniti per gli oggetti](./defining-default-methods-for-objects.md)

[Definizione dei set di membri predefiniti per gli oggetti](./defining-default-member-sets-for-objects.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
