---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Informazioni sulle pipeline di PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 3ee03f001668fb24ff9be1ea6ecb3817e319d0ee
ms.sourcegitcommit: 59727f71dc204785a1bcdedc02716d8340a77aeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/28/2018
ms.locfileid: "43134129"
---
# <a name="understanding-pipelines"></a><span data-ttu-id="c6af5-103">Informazioni sulle pipeline</span><span class="sxs-lookup"><span data-stu-id="c6af5-103">Understanding pipelines</span></span>

<span data-ttu-id="c6af5-104">Le pipeline si comportano come una serie di segmenti di pipe connessi.</span><span class="sxs-lookup"><span data-stu-id="c6af5-104">Pipelines act like a series of connected segments of pipe.</span></span> <span data-ttu-id="c6af5-105">Gli elementi che si muovono nella pipeline passano tramite ogni segmento.</span><span class="sxs-lookup"><span data-stu-id="c6af5-105">Items moving along the pipeline pass through each segment.</span></span> <span data-ttu-id="c6af5-106">Per creare una pipeline in PowerShell, è necessario collegare tra loro i comandi con l'operatore di pipe "|".</span><span class="sxs-lookup"><span data-stu-id="c6af5-106">To create a pipeline in PowerShell, you connect commands together with the pipe operator "|".</span></span> <span data-ttu-id="c6af5-107">L'output di ogni comando viene usato come input per il comando successivo.</span><span class="sxs-lookup"><span data-stu-id="c6af5-107">The output of each command is used as input to the next command.</span></span>

<span data-ttu-id="c6af5-108">La notazione usata per le pipeline è simile a quella usata in altre shell.</span><span class="sxs-lookup"><span data-stu-id="c6af5-108">The notation used for pipelines is similar to the notation used in other shells.</span></span> <span data-ttu-id="c6af5-109">A prima vista, può non essere evidente come si differenziano le pipeline in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6af5-109">At first glance, it may not be apparent how pipelines are different in PowerShell.</span></span> <span data-ttu-id="c6af5-110">Anche se sullo schermo viene visualizzato testo, PowerShell invia tramite pipe oggetti, e non testo, tra i comandi.</span><span class="sxs-lookup"><span data-stu-id="c6af5-110">Although you see text on the screen, PowerShell pipes objects, not text, between commands.</span></span>

## <a name="the-powershell-pipeline"></a><span data-ttu-id="c6af5-111">Pipeline di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6af5-111">The PowerShell pipeline</span></span>

<span data-ttu-id="c6af5-112">Le pipeline sono senza dubbio il concetto più importante usato nelle interfacce della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="c6af5-112">Pipelines are arguably the most valuable concept used in command-line interfaces.</span></span> <span data-ttu-id="c6af5-113">Se usate correttamente, le pipeline riducono la necessità di usare comandi complessi e semplificano la visualizzazione del flusso di lavoro per i comandi.</span><span class="sxs-lookup"><span data-stu-id="c6af5-113">When used properly, pipelines reduce the effort of using complex commands and make it easier to see the flow of work for the commands.</span></span> <span data-ttu-id="c6af5-114">Ogni comando in una pipeline (denominato elemento della pipeline) passa il proprio output al comando successivo nella pipeline, elemento per elemento.</span><span class="sxs-lookup"><span data-stu-id="c6af5-114">Each command in a pipeline (called a pipeline element) passes its output to the next command in the pipeline, item-by-item.</span></span> <span data-ttu-id="c6af5-115">I comandi non devono gestire più di un elemento per volta.</span><span class="sxs-lookup"><span data-stu-id="c6af5-115">Commands don't have to handle more than one item at a time.</span></span> <span data-ttu-id="c6af5-116">Ne risultano un utilizzo inferiore delle risorse e la possibilità di iniziare a ottenere l'output immediatamente.</span><span class="sxs-lookup"><span data-stu-id="c6af5-116">The result is reduced resource consumption and the ability to begin getting the output immediately.</span></span>

<span data-ttu-id="c6af5-117">Ad esempio, se si usa il cmdlet `Out-Host` per forzare una visualizzazione pagina per pagina dell'output di un altro comando, l'output avrà lo stesso aspetto del normale testo visualizzato sullo schermo, suddiviso in pagine:</span><span class="sxs-lookup"><span data-stu-id="c6af5-117">For example, if you use the `Out-Host` cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```powershell
Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging
```

```Output
    Directory: C:\WINDOWS\system32

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
d-----        4/12/2018   2:15 AM                0409
d-----        5/13/2018  11:31 PM                1033
d-----        4/11/2018   4:38 PM                AdvancedInstallers
d-----        5/13/2018  11:13 PM                af-ZA
d-----        5/13/2018  11:13 PM                am-et
d-----        4/11/2018   4:38 PM                AppLocker
d-----        5/13/2018  11:31 PM                appmgmt
d-----        7/11/2018   2:05 AM                appraiser
d---s-        4/12/2018   2:20 AM                AppV
d-----        5/13/2018  11:10 PM                ar-SA
d-----        5/13/2018  11:13 PM                as-IN
d-----        8/14/2018   9:03 PM                az-Latn-AZ
d-----        5/13/2018  11:13 PM                be-BY
d-----        5/13/2018  11:10 PM                BestPractices
d-----        5/13/2018  11:10 PM                bg-BG
d-----        5/13/2018  11:13 PM                bn-BD
d-----        5/13/2018  11:13 PM                bn-IN
d-----        8/14/2018   9:03 PM                Boot
d-----        8/14/2018   9:03 PM                bs-Latn-BA
d-----        4/11/2018   4:38 PM                Bthprops
d-----        4/12/2018   2:19 AM                ca-ES
d-----        8/14/2018   9:03 PM                ca-ES-valencia
d-----        5/13/2018  10:46 PM                CatRoot
d-----        8/23/2018   5:07 PM                catroot2
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="c6af5-118">La divisione in pagine riduce anche l'utilizzo della CPU perché i trasferimenti vengono elaborati nel cmdlet `Out-Host` quando è pronta per la visualizzazione una pagina completa.</span><span class="sxs-lookup"><span data-stu-id="c6af5-118">Paging also reduces CPU utilization because processing transfers to the `Out-Host` cmdlet when it has a complete page ready to display.</span></span> <span data-ttu-id="c6af5-119">I cmdlet precedenti nella pipeline sospendono l'esecuzione finché non è disponibile la pagina di output successiva.</span><span class="sxs-lookup"><span data-stu-id="c6af5-119">The cmdlets that precede it in the pipeline pause execution until the next page of output is available.</span></span>

<span data-ttu-id="c6af5-120">È possibile notare la differenza con Gestione attività Windows per monitorare l'uso della CPU e della memoria da parte di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6af5-120">You can see the difference Windows Task Manager to monitor CPU and memory used by PowerShell.</span></span> <span data-ttu-id="c6af5-121">Eseguire questo comando: `Get-ChildItem C:\\Windows -Recurse`.</span><span class="sxs-lookup"><span data-stu-id="c6af5-121">Run the following command: `Get-ChildItem C:\\Windows -Recurse`.</span></span> <span data-ttu-id="c6af5-122">Confrontare l'utilizzo della CPU e della memoria con questo comando: `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span><span class="sxs-lookup"><span data-stu-id="c6af5-122">Compare the CPU and memory usage to this command: `Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging`.</span></span>

## <a name="objects-in-the-pipeline"></a><span data-ttu-id="c6af5-123">Oggetti nella pipeline</span><span class="sxs-lookup"><span data-stu-id="c6af5-123">Objects in the pipeline</span></span>

<span data-ttu-id="c6af5-124">Quando si esegue un cmdlet in PowerShell, viene visualizzato output di testo perché è necessario rappresentare gli oggetti come testo in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="c6af5-124">When you run a cmdlet in PowerShell, you see text output because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="c6af5-125">L'output di testo può non visualizzare tutte le proprietà dell'oggetto restituito.</span><span class="sxs-lookup"><span data-stu-id="c6af5-125">The text output may not display all of the properties of the object being output.</span></span>

<span data-ttu-id="c6af5-126">Ad esempio, si consideri il cmdlet `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="c6af5-126">For example, consider the `Get-Location` cmdlet.</span></span> <span data-ttu-id="c6af5-127">Se si esegue `Get-Location` mentre il percorso corrente è la radice dell'unità C, verrà visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="c6af5-127">If you run `Get-Location` while your current location is the root of the C drive, you see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="c6af5-128">L'output di testo è un riepilogo delle informazioni e non una rappresentazione completa dell'oggetto restituito da `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="c6af5-128">The text output is a summary of information, not a complete representation of the object returned by `Get-Location`.</span></span> <span data-ttu-id="c6af5-129">L'intestazione nell'output viene aggiunta dal processo che formatta i dati per la visualizzazione sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="c6af5-129">The heading in the output is added by the process that formats the data for onscreen display.</span></span>

<span data-ttu-id="c6af5-130">Quando l'output viene inviato tramite pipe al cmdlet `Get-Member`, si ottengono informazioni sull'oggetto restituito da `Get-Location`.</span><span class="sxs-lookup"><span data-stu-id="c6af5-130">When you pipe the output to the `Get-Member` cmdlet you get information about the object returned by `Get-Location`.</span></span>

```powershell
PS> Get-Location | Get-Member
```

```Output
   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Equals       Method     bool Equals(System.Object obj)
GetHashCode  Method     int GetHashCode()
GetType      Method     type GetType()
ToString     Method     string ToString()
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   string Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {get;}
ProviderPath Property   string ProviderPath {get;}
```

<span data-ttu-id="c6af5-131">`Get-Location` restituisce un oggetto **PathInfo** che contiene il percorso corrente e altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="c6af5-131">`Get-Location` returns a **PathInfo** object that contains the current path and other information.</span></span>