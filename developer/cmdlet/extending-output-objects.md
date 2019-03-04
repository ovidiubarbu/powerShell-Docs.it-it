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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861927"
---
# <a name="extending-output-objects"></a>Estensione degli oggetti di output

È possibile estendere gli oggetti di .NET Framework che vengono restituiti dal cmdlet, funzioni e gli script utilizzando il file di tipi (con estensione PS1XML). Tipi file sono file basati su XML che consentono di aggiungere proprietà e metodi agli oggetti esistenti. Ad esempio, Windows PowerShell fornisce il file Types.ps1xml, che aggiunge elementi a più oggetti di .NET Framework esistenti. Il file Types.ps1xml si trova nella directory di installazione di Windows PowerShell (`$pshome`). È possibile creare il proprio file di tipi per estendere ulteriormente gli oggetti o per estendere altri oggetti. Quando si estende un oggetto usando un file di tipi, qualsiasi istanza dell'oggetto viene estesa con i nuovi elementi.

## <a name="extending-the-systemarray-object"></a>Estendendo l'oggetto System. Array

L'esempio seguente mostra in che modo Windows PowerShell estende la [System. Array](/dotnet/api/System.Array) oggetto nel file Types.ps1xml. Per impostazione predefinita [System. Array](/dotnet/api/System.Array) gli oggetti hanno una `Length` proprietà elenca il numero di oggetti nella matrice. Tuttavia, poiché la lunghezza"nome" non descrive chiaramente la proprietà, Windows PowerShell aggiunge il `Count` proprietà alias, che consente di visualizzare lo stesso valore di `Length` proprietà. Il codice XML seguente aggiunge il `Count` proprietà per il [System. Array](/dotnet/api/System.Array) tipo.

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

Per visualizzare questa nuova proprietà alias, usare una [Get-Member](/powershell/module/Microsoft.PowerShell.Utility/Get-Member) comando su qualsiasi matrice, come illustrato nell'esempio seguente.

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
È possibile usare la `Count` proprietà o il `Length` proprietà per determinare il numero di oggetti presenti in una matrice. Ad esempio:

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

Per creare un file di tipi personalizzati, avviare copiando un file esistente di tipi. Il nuovo file può avere qualsiasi nome, ma deve avere un'estensione di file con estensione ps1xml. Quando si copia il file, è possibile inserire il nuovo file in qualsiasi directory accessibile a Windows PowerShell, ma è utile inserire i file nella directory di installazione di Windows PowerShell (`$pshome`) o in una sottodirectory della directory di installazione.

Per aggiungere i tipi estesi per il file, aggiungere un elemento di tipi per ogni oggetto che si vuole estendere. Gli argomenti seguenti forniscono esempi.

- Per altre informazioni sull'aggiunta di proprietà e set di proprietà, vedere [proprietà estese](./extending-properties-for-objects.md)

- Per altre informazioni sull'aggiunta di metodi, vedere [metodi estesi](./defining-default-methods-for-objects.md).

- Per altre informazioni sull'aggiunta di set di membri, vedere [esteso set di membri](./defining-default-member-sets-for-objects.md).

Dopo aver definito i tipi estesi, è possibile usare uno dei metodi seguenti per rendere disponibili gli oggetti estesi:

- Per rendere il file di tipi estesi disponibili per la sessione corrente, usare il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet per aggiungere il nuovo file. Se si desidera che i tipi hanno la precedenza sui tipi definiti in altri tipi di file (inclusi i file Types.ps1xml), usare il `PrependData` parametro il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) cmdlet.
- Per rendere il file di tipi estesi disponibili per tutte le sessioni future, aggiungere il file dei tipi a un modulo, esportare la sessione corrente o aggiungere il [Update-TypeData](/powershell/module/Microsoft.PowerShell.Utility/Update-TypeData) comando al profilo di Windows PowerShell.

## <a name="signing-types-files"></a>La firma dei file di tipi

Tipi file devono essere firmati digitalmente da eventuali manomissioni perché il codice XML può includere i blocchi di script. Per altre informazioni sull'aggiunta di firme digitali, vedere [about_Signing](/powershell/module/microsoft.powershell.core/about/about_signing)

## <a name="see-also"></a>Vedere anche

[Definizione di proprietà predefinite per gli oggetti](./extending-properties-for-objects.md)

[Definizione di metodi predefiniti per gli oggetti](./defining-default-methods-for-objects.md)

[Definizione di set di membri predefiniti per gli oggetti](./defining-default-member-sets-for-objects.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
