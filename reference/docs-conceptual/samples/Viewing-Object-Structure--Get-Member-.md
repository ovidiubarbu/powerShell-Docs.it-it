---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Visualizzazione della struttura degli oggetti Get Member
ms.openlocfilehash: 80b36abd303a708195f12d96511e616178d11b5a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030712"
---
# <a name="viewing-object-structure-get-member"></a><span data-ttu-id="e20bb-103">Visualizzazione della struttura degli oggetti (Get-Member)</span><span class="sxs-lookup"><span data-stu-id="e20bb-103">Viewing Object Structure (Get-Member)</span></span>

<span data-ttu-id="e20bb-104">Poiché il ruolo degli oggetti è cruciale in Windows PowerShell, sono disponibili numerosi comandi nativi progettati per operare su tipi di oggetti arbitrari.</span><span class="sxs-lookup"><span data-stu-id="e20bb-104">Because objects play such a central role in Windows PowerShell, there are several native commands designed to work with arbitrary object types.</span></span> <span data-ttu-id="e20bb-105">Il più importante è il comando **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="e20bb-105">The most important one is the **Get-Member** command.</span></span>

<span data-ttu-id="e20bb-106">La tecnica più semplice per analizzare gli oggetti restituiti da un comando consiste nell'inviare tramite pipe l'output del comando al cmdlet **Get-Member**.</span><span class="sxs-lookup"><span data-stu-id="e20bb-106">The simplest technique for analyzing the objects that a command returns is to pipe the output of that command to the **Get-Member** cmdlet.</span></span> <span data-ttu-id="e20bb-107">Il cmdlet **Get-Member** mostra il nome formale del tipo di oggetto e un elenco completo dei relativi membri.</span><span class="sxs-lookup"><span data-stu-id="e20bb-107">The **Get-Member** cmdlet shows you the formal name of the object type and a complete listing of its members.</span></span> <span data-ttu-id="e20bb-108">Il numero di elementi restituiti a volte può essere a volte enorme.</span><span class="sxs-lookup"><span data-stu-id="e20bb-108">The number of elements that are returned can sometimes be overwhelming.</span></span> <span data-ttu-id="e20bb-109">Ad esempio, un oggetto Process può avere più di 100 membri.</span><span class="sxs-lookup"><span data-stu-id="e20bb-109">For example, a process object can have over 100 members.</span></span>

<span data-ttu-id="e20bb-110">Per visualizzare tutti i membri di un oggetto Process e impaginare l'output in modo che sia visibile per intero, digitare:</span><span class="sxs-lookup"><span data-stu-id="e20bb-110">To see all the members of a Process object and page the output so you can view all of it, type:</span></span>

```powershell
Get-Process | Get-Member | Out-Host -Paging
```

<span data-ttu-id="e20bb-111">L'output di questo comando avrà un aspetto simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="e20bb-111">The output from this command will look something like this:</span></span>

```output
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

<span data-ttu-id="e20bb-112">È possibile rendere più fruibile questo lungo elenco di informazioni filtrando gli elementi da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="e20bb-112">We can make this long list of information more usable by filtering for elements we want to see.</span></span> <span data-ttu-id="e20bb-113">Il comando **Get-Member** consente di elencare solo i membri che sono proprietà.</span><span class="sxs-lookup"><span data-stu-id="e20bb-113">The **Get-Member** command lets you list only members that are properties.</span></span> <span data-ttu-id="e20bb-114">Esistono diversi tipi di proprietà.</span><span class="sxs-lookup"><span data-stu-id="e20bb-114">There are several forms of properties.</span></span> <span data-ttu-id="e20bb-115">Il cmdlet consente di visualizzare le proprietà di qualsiasi tipo impostando il parametro **Get-Member MemberType** sul valore **Properties**.</span><span class="sxs-lookup"><span data-stu-id="e20bb-115">The cmdlet displays properties of any type if we set the **Get-Member MemberType** parameter to the value **Properties**.</span></span> <span data-ttu-id="e20bb-116">L'elenco risultante è ancora molto lungo, ma un po' più gestibile:</span><span class="sxs-lookup"><span data-stu-id="e20bb-116">The resulting list is still very long, but a bit more manageable:</span></span>

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
> <span data-ttu-id="e20bb-117">I valori consentiti per MemberType sono AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet e All.</span><span class="sxs-lookup"><span data-stu-id="e20bb-117">The allowed values of MemberType are AliasProperty, CodeProperty, Property, NoteProperty, ScriptProperty, Properties, PropertySet, Method, CodeMethod, ScriptMethod, Methods, ParameterizedProperty, MemberSet, and All.</span></span>

<span data-ttu-id="e20bb-118">Per un processo esistono più di 60 proprietà.</span><span class="sxs-lookup"><span data-stu-id="e20bb-118">There are over 60 properties for a process.</span></span> <span data-ttu-id="e20bb-119">Il motivo per cui Windows PowerShell spesso visualizza solo un numero limitato di proprietà per qualsiasi oggetto noto, è che visualizzarle tutte significherebbe restituire una quantità di informazioni ingestibile.</span><span class="sxs-lookup"><span data-stu-id="e20bb-119">The reason Windows PowerShell often shows only a handful of properties for any well-known object is that showing all of them would produce an unmanageable amount of information.</span></span>

> [!NOTE]
> <span data-ttu-id="e20bb-120">Windows PowerShell determina come visualizzare un tipo di oggetto in base alle informazioni archiviate nei file XML con nomi che terminano con format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e20bb-120">Windows PowerShell determines how to display an object type by using information stored in XML files that have names ending in .format.ps1xml.</span></span> <span data-ttu-id="e20bb-121">I dati di formattazione per gli oggetti Process, ovvero gli oggetti .NET System.Diagnostics, sono archiviati in DotNetTypes.format.ps1xml.</span><span class="sxs-lookup"><span data-stu-id="e20bb-121">The formatting data for process objects, which are .NET System.Diagnostics.Process objects, is stored in DotNetTypes.format.ps1xml.</span></span>

<span data-ttu-id="e20bb-122">Se è necessario esaminare proprietà diverse da quelle visualizzate da Windows PowerShell per impostazione predefinita, occorre formattare i dati di output</span><span class="sxs-lookup"><span data-stu-id="e20bb-122">If you need to look at properties other than those that Windows PowerShell displays by default, you will need to format the output data yourself.</span></span> <span data-ttu-id="e20bb-123">tramite i cmdlet Format.</span><span class="sxs-lookup"><span data-stu-id="e20bb-123">This can be done by using the format cmdlets.</span></span>
