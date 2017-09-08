---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Visualizzazione della struttura degli oggetti Get Member
ms.assetid: a1819ed2-2ef3-453a-b2b0-f3589c550481
ms.openlocfilehash: 618f34bca7bfb76ce5d48ada642a687e279c8aad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
# <a name="viewing-object-structure-get-member"></a>Visualizzazione della struttura degli oggetti (Get-Member)
Poiché il ruolo degli oggetti è cruciale in Windows PowerShell, sono disponibili numerosi comandi nativi progettati per operare su tipi di oggetti arbitrari. Il più importante è il comando **Get-Member**.

La tecnica più semplice per analizzare gli oggetti restituiti da un comando consiste nell'inviare tramite pipe l'output del comando al cmdlet **Get-Member**. Il cmdlet **Get-Member** mostra il nome formale del tipo di oggetto e un elenco completo dei relativi membri. Il numero di elementi restituiti a volte può essere a volte enorme. Ad esempio, un oggetto Process può avere più di 100 membri.

Per visualizzare tutti i membri di un oggetto Process e impaginare l'output in modo che sia visibile per intero, digitare:

```
PS> Get-Process | Get-Member | Out-Host -Paging
```

L'output di questo comando avrà un aspetto simile al seguente:

```
TypeName: System.Diagnostics.Process

Name                           MemberType     Definition
----                           ----------     ----------
Handles                        AliasProperty  Handles = Handlecount
Name                           AliasProperty  Name = ProcessName
NPM                            AliasProperty  NPM = NonpagedSystemMemorySize
PM                             AliasProperty  PM = PagedMemorySize
VM                             AliasProperty  VM = VirtualMemorySize
WS                             AliasProperty  WS = WorkingSet
add_Disposed                   Method         System.Void add_Disposed(Event...
...
```

È possibile rendere più fruibile questo lungo elenco di informazioni filtrando gli elementi da visualizzare. Il comando **Get-Member** consente di elencare solo i membri che sono proprietà. Esistono diversi tipi di proprietà. Il cmdlet consente di visualizzare le proprietà di qualsiasi tipo impostando il parametro **Get-Member MemberType** sul valore **Properties**. L'elenco risultante è ancora molto lungo, ma un po' più gestibile:

```
PS> Get-Process | Get-Member -MemberType Properties

   TypeName: System.Diagnostics.Process

Name                       MemberType     Definition
----                       ----------     ----------
Handles                    AliasProperty  Handles = Handlecount
Name                       AliasProperty  Name = ProcessName
...
ExitCode                   Property       System.Int32 ExitCode {get;}
...
Handle                     Property       System.IntPtr Handle {get;}
...
CPU                        ScriptProperty System.Object CPU {get=$this.Total...
...
Path                       ScriptProperty System.Object Path {get=$this.Main...
...
```

> [!NOTE]
> I valori consentiti per MemberType sono AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet e All.

Per un processo esistono più di 60 proprietà. Il motivo per cui Windows PowerShell spesso visualizza solo un numero limitato di proprietà per qualsiasi oggetto noto, è che visualizzarle tutte significherebbe restituire una quantità di informazioni ingestibile.

> [!NOTE]
> Windows PowerShell determina come visualizzare un tipo di oggetto in base alle informazioni archiviate nei file XML con nomi che terminano con format.ps1xml. I dati di formattazione per gli oggetti Process, ovvero gli oggetti .NET System.Diagnostics, sono archiviati in DotNetTypes.format.ps1xml.

Se è necessario esaminare proprietà diverse da quelle visualizzate da Windows PowerShell per impostazione predefinita, occorre formattare i dati di output tramite i cmdlet Format.

