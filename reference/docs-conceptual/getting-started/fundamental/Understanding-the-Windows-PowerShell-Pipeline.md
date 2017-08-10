---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Informazioni sulla pipeline di Windows PowerShell
ms.assetid: 6be50926-7943-4ef7-9499-4490d72a63fb
ms.openlocfilehash: 6d152e52d2fcfb9dd592eb9ac40500615f2186cb
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="understanding-the-windows-powershell-pipeline"></a><span data-ttu-id="12ca0-103">Informazioni sulla pipeline di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="12ca0-103">Understanding the Windows PowerShell Pipeline</span></span>
<span data-ttu-id="12ca0-104">Il piping è usato praticamente ovunque in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ca0-104">Piping works virtually everywhere in Windows PowerShell.</span></span> <span data-ttu-id="12ca0-105">Anche se sullo schermo viene visualizzato del testo, Windows PowerShell non invia tramite pipe testo tra i comandi,</span><span class="sxs-lookup"><span data-stu-id="12ca0-105">Although you see text on the screen, Windows PowerShell does not pipe text between commands.</span></span> <span data-ttu-id="12ca0-106">bensì oggetti.</span><span class="sxs-lookup"><span data-stu-id="12ca0-106">Instead, it pipes objects.</span></span>

<span data-ttu-id="12ca0-107">La notazione usata per le pipeline è simile a quella usata in altre shell, pertanto, a prima vista, potrebbe non essere evidente che Windows PowerShell stia introducendo qualcosa di nuovo.</span><span class="sxs-lookup"><span data-stu-id="12ca0-107">The notation used for pipelines is similar to that used in other shells, so at first glance, it may not be apparent that Windows PowerShell introduces something new.</span></span> <span data-ttu-id="12ca0-108">Se ad esempio si usa il cmdlet **Out-Host** per forzare una visualizzazione pagina per pagina dell'output di un altro comando, l'output avrà lo stesso aspetto del normale testo visualizzato sullo schermo, suddiviso in pagine:</span><span class="sxs-lookup"><span data-stu-id="12ca0-108">For example, if you use the **Out-Host** cmdlet to force a page-by-page display of output from another command, the output looks just like the normal text displayed on the screen, broken up into pages:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32 | Out-Host -Paging

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\system32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2005-10-22  11:04 PM        315 $winnt$.inf
-a---        2004-08-04   8:00 AM      68608 access.cpl
-a---        2004-08-04   8:00 AM      64512 acctres.dll
-a---        2004-08-04   8:00 AM     183808 accwiz.exe
-a---        2004-08-04   8:00 AM      61952 acelpdec.ax
-a---        2004-08-04   8:00 AM     129536 acledit.dll
-a---        2004-08-04   8:00 AM     114688 aclui.dll
-a---        2004-08-04   8:00 AM     194048 activeds.dll
-a---        2004-08-04   8:00 AM     111104 activeds.tlb
-a---        2004-08-04   8:00 AM       4096 actmovie.exe
-a---        2004-08-04   8:00 AM     101888 actxprxy.dll
-a---        2003-02-21   6:50 PM     143150 admgmt.msc
-a---        2006-01-25   3:35 PM      53760 admparse.dll
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="12ca0-109">Il comando Out-Host -Paging è un elemento della pipeline utile in caso di output lungo da visualizzare lentamente.</span><span class="sxs-lookup"><span data-stu-id="12ca0-109">The Out-Host -Paging command is a useful pipeline element whenever you have lengthy output that you would like to display slowly.</span></span> <span data-ttu-id="12ca0-110">La sua utilità si rivela in particolare se l'operazione richiede un uso elevato della CPU.</span><span class="sxs-lookup"><span data-stu-id="12ca0-110">It is especially useful if the operation is very CPU-intensive.</span></span> <span data-ttu-id="12ca0-111">Dal momento che l'elaborazione viene trasferita al cmdlet Out-Host quando dispone di una pagina completa pronta per la visualizzazione, i cmdlet che lo precedono nella pipeline interrompono l'operazione finché non è disponibile la pagina successiva di output.</span><span class="sxs-lookup"><span data-stu-id="12ca0-111">Because processing is transferred to the Out-Host cmdlet when it has a complete page ready to display, cmdlets that precede it in the pipeline halt operation until the next page of output is available.</span></span> <span data-ttu-id="12ca0-112">È possibile vedere questo comportamento se si usa Gestione attività Windows per monitorare l'uso della CPU e della memoria da parte di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ca0-112">You can see this if you use the Windows Task Manager to monitor CPU and memory use by Windows PowerShell.</span></span>

<span data-ttu-id="12ca0-113">Eseguire il comando seguente: **Get-ChildItem C:\\Windows -Recurse**.</span><span class="sxs-lookup"><span data-stu-id="12ca0-113">Run the following command: **Get-ChildItem C:\\Windows -Recurse**.</span></span> <span data-ttu-id="12ca0-114">Confrontare l'uso della CPU e della memoria con questo comando: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="12ca0-114">Compare the CPU and memory usage to this command: **Get-ChildItem C:\\Windows -Recurse | Out-Host -Paging**.</span></span> <span data-ttu-id="12ca0-115">Quello che si vede sullo schermo è testo, poiché è necessario rappresentare gli oggetti come testo in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="12ca0-115">What you see on the screen is text, but that is because it is necessary to represent objects as text in a console window.</span></span> <span data-ttu-id="12ca0-116">Questa è solo una rappresentazione di quello che accade veramente in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="12ca0-116">This is just a representation of what is really going on inside Windows PowerShell.</span></span> <span data-ttu-id="12ca0-117">Si consideri ad esempio il cmdlet Get-Location.</span><span class="sxs-lookup"><span data-stu-id="12ca0-117">For example, consider the Get-Location cmdlet.</span></span> <span data-ttu-id="12ca0-118">Se si digita **Get-Location** mentre il percorso corrente è la radice dell'unità C, verrà visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="12ca0-118">If you type **Get-Location** while your current location is the root of the C drive, you would see the following output:</span></span>

```
PS> Get-Location

Path
----
C:\
```

<span data-ttu-id="12ca0-119">Se Windows PowerShell ha inviato il testo attraverso una pipe, emettendo un comando come **Get-Location | Out-Host**, passerà da **Get-Location** a **Out-Host** un set di caratteri nell'ordine in cui sono visualizzati sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="12ca0-119">If Windows PowerShell pipelined text, issuing a command such as **Get-Location | Out-Host**, would pass from **Get-Location** to **Out-Host** a set of characters in the order they are displayed onscreen.</span></span> <span data-ttu-id="12ca0-120">In altre parole, se le informazioni dell'intestazione venissero ignorate, **Out-Host** riceverebbe per prima cosa il carattere "**C"**, quindi il carattere "**:"** e infine il carattere "**\\"**.</span><span class="sxs-lookup"><span data-stu-id="12ca0-120">In other words, if you were to ignore the heading information, **Out-Host** would first receive the character '**C'**, then the character '**:'**, then the character '**\\'**.</span></span> <span data-ttu-id="12ca0-121">Il cmdlet **Out-Host** non è in grado di determinare quale significato associare all'output di caratteri del cmdlet **Get-Location**.</span><span class="sxs-lookup"><span data-stu-id="12ca0-121">The **Out-Host** cmdlet could not determine what meaning to associate with the characters output by the **Get-Location** cmdlet.</span></span>

<span data-ttu-id="12ca0-122">Invece di usare del testo per consentire ai comandi in una pipeline di comunicare, Windows PowerShell usa oggetti.</span><span class="sxs-lookup"><span data-stu-id="12ca0-122">Instead of using text to let commands in a pipeline communicate, Windows PowerShell uses objects.</span></span> <span data-ttu-id="12ca0-123">Dal punto di vista di un utente, gli oggetti impacchettano le informazioni correlate in un modulo che rende più semplice manipolare le informazioni come unità ed estrarre gli specifici elementi richiesti.</span><span class="sxs-lookup"><span data-stu-id="12ca0-123">From the standpoint of a user, objects package related information into a form that makes it easier to manipulate the information as a unit, and extract specific items that you need.</span></span>

<span data-ttu-id="12ca0-124">Il comando **Get-Location** non restituisce testo contenente il percorso corrente,</span><span class="sxs-lookup"><span data-stu-id="12ca0-124">The **Get-Location** command does not return text that contains the current path.</span></span> <span data-ttu-id="12ca0-125">ma un pacchetto di informazioni denominato oggetto **PathInfo** che contiene il percorso corrente insieme ad altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="12ca0-125">It returns a package of information called a **PathInfo** object that contains the current path along with some other information.</span></span> <span data-ttu-id="12ca0-126">Il cmdlet **Out-Host** invia quindi questo oggetto **PathInfo** sullo schermo e Windows PowerShell decide quali informazioni visualizzare e come visualizzarle in base alle proprie regole di formattazione.</span><span class="sxs-lookup"><span data-stu-id="12ca0-126">The **Out-Host** cmdlet then sends this **PathInfo** object to the screen, and Windows PowerShell decides what information to display and how to display it based on its formatting rules.</span></span>

<span data-ttu-id="12ca0-127">In realtà, l'output delle informazioni dell'intestazione del cmdlet **Get-Location** viene aggiunto solo alla fine del processo, durante la formattazione dei dati per la visualizzazione sullo schermo.</span><span class="sxs-lookup"><span data-stu-id="12ca0-127">In fact, the heading information output by the **Get-Location** cmdlet is added only at the end of the process, as part of the process of formatting the data for onscreen display.</span></span> <span data-ttu-id="12ca0-128">Ciò che compare sullo schermo è un riepilogo delle informazioni e non una rappresentazione completa dell'oggetto di output.</span><span class="sxs-lookup"><span data-stu-id="12ca0-128">What you see onscreen is a summary of information, and not a complete representation of the output object.</span></span>

<span data-ttu-id="12ca0-129">Dato che possono esistere più output di informazioni da un comando di Windows PowerShell rispetto a quelli visualizzati nella finestra della console, in che modo è possibile recuperare gli elementi non visibili?</span><span class="sxs-lookup"><span data-stu-id="12ca0-129">Given that there may be more information output from a Windows PowerShell command than what we see displayed in the console window, how can you retrieve the non-visible elements?</span></span> <span data-ttu-id="12ca0-130">Come si visualizzano i dati aggiuntivi?</span><span class="sxs-lookup"><span data-stu-id="12ca0-130">How do you view the extra data?</span></span> <span data-ttu-id="12ca0-131">E cosa accade se si vogliono visualizzare i dati in un formato diverso da quello che Windows PowerShell usa normalmente?</span><span class="sxs-lookup"><span data-stu-id="12ca0-131">And what if you want to view the data in a format different than the one Windows PowerShell normally uses?</span></span>

<span data-ttu-id="12ca0-132">Nel resto di questa sezione viene spiegato come individuare la struttura di oggetti specifici di Windows PowerShell, selezionando elementi specifici e formattandoli per una visualizzazione più semplice, e come inviare queste informazioni a percorsi di output alternativi, ad esempio file e stampanti.</span><span class="sxs-lookup"><span data-stu-id="12ca0-132">The rest of this chapter discusses how you can discover the structure of specific Windows PowerShell objects, selecting specific items and formatting them for easier display, and how to send this information to alternative output locations such as files and printers.</span></span>
