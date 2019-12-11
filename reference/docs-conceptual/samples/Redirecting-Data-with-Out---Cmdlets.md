---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Reindirizzamento dei dati con i cmdlet Out
ms.openlocfilehash: d4cc14e26bdef0f973f948177d0c1e68929605fa
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030071"
---
# <a name="redirecting-data-with-out--cmdlets"></a><span data-ttu-id="41173-103">Reindirizzamento dei dati con i cmdlet Out-\*</span><span class="sxs-lookup"><span data-stu-id="41173-103">Redirecting Data with Out-\* Cmdlets</span></span>

<span data-ttu-id="41173-104">In Windows PowerShell sono disponibili diversi cmdlet che consentono di controllare direttamente l'output dei dati.</span><span class="sxs-lookup"><span data-stu-id="41173-104">Windows PowerShell provides several cmdlets that let you control data output directly.</span></span> <span data-ttu-id="41173-105">Questi cmdlet hanno in comune due importanti caratteristiche.</span><span class="sxs-lookup"><span data-stu-id="41173-105">These cmdlets share two important characteristics.</span></span>

<span data-ttu-id="41173-106">Per prima cosa, in genere trasformano i dati in una forma di testo,</span><span class="sxs-lookup"><span data-stu-id="41173-106">First, they generally transform data to some form of text.</span></span> <span data-ttu-id="41173-107">dal momento che convertono i dati in output per i componenti di sistema che richiedono input di testo.</span><span class="sxs-lookup"><span data-stu-id="41173-107">They do this because they output the data to system components that require text input.</span></span> <span data-ttu-id="41173-108">Ciò significa che devono rappresentare gli oggetti come testo.</span><span class="sxs-lookup"><span data-stu-id="41173-108">This means they need to represent the objects as text.</span></span> <span data-ttu-id="41173-109">Il testo viene pertanto formattato così com'è visualizzato nella finestra della console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41173-109">Therefore, the text is formatted as you see it in the Windows PowerShell console window.</span></span>

<span data-ttu-id="41173-110">In secondo luogo, questi cmdlet usano il verbo **Out** di Windows PowerShell poiché inviano informazioni altrove all'esterno di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41173-110">Second, these cmdlets use the Windows PowerShell verb **Out** because they send information out from Windows PowerShell to somewhere else.</span></span> <span data-ttu-id="41173-111">Il cmdlet **Out-Host** non costituisce un'eccezione: la visualizzazione della finestra host è all'esterno di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="41173-111">The **Out-Host** cmdlet is no exception: the host window display is outside of Windows PowerShell.</span></span> <span data-ttu-id="41173-112">Questo aspetto è importante perché quando i dati vengono inviati all'esterno di Windows PowerShell, vengono effettivamente rimossi.</span><span class="sxs-lookup"><span data-stu-id="41173-112">This is important because when data is sent out of Windows PowerShell, it is actually removed.</span></span> <span data-ttu-id="41173-113">È possibile verificare quanto affermato se si prova a creare una pipeline per il paging dei dati alla finestra host e si tenta di formattarla come elenco, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="41173-113">You can see this if you try to create a pipeline that pages data to the host window, and then attempt to format it as a list, as shown here:</span></span>

```powershell
Get-Process | Out-Host -Paging | Format-List
```

<span data-ttu-id="41173-114">Si potrebbe pensare che il comando visualizzerà pagine di informazioni sui processi in formato elenco.</span><span class="sxs-lookup"><span data-stu-id="41173-114">You might expect the command to display pages of process information in list format.</span></span> <span data-ttu-id="41173-115">Al contrario, viene visualizzato l'elenco tabulare predefinito:</span><span class="sxs-lookup"><span data-stu-id="41173-115">Instead, it displays the default tabular list:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    101       5     1076       3316    32     0.05   2888 alg
...
    618      18    39348      51108   143   211.20    740 explorer
    257       8     9752      16828    79     3.02   2560 explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="41173-116">Il cmdlet **Out-Host** invia i dati direttamente alla console, pertanto il comando **Format-List** non riceve mai niente da formattare.</span><span class="sxs-lookup"><span data-stu-id="41173-116">The **Out-Host** cmdlet sends the data directly to the console, so the **Format-List** command never receives anything to format.</span></span>

<span data-ttu-id="41173-117">Il modo corretto per definire la struttura di questo comando consiste nell'inserire il cmdlet **Out-Host** alla fine della pipeline come mostrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="41173-117">The correct way to structure this command is to put the **Out-Host** cmdlet at the end of the pipeline as shown below.</span></span> <span data-ttu-id="41173-118">In questo modo, i dati dei processi vengono formattati in un elenco prima dell'esecuzione del paging e della visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="41173-118">This causes the process data to be formatted in a list before being paged and displayed.</span></span>

```
PS> Get-Process | Format-List | Out-Host -Paging

Id      : 2888
Handles : 101
CPU     : 0.046875
Name    : alg
...

Id      : 740
Handles : 612
CPU     : 211.703125
Name    : explorer

Id      : 2560
Handles : 257
CPU     : 3.015625
Name    : explorer
...
<SPACE> next page; <CR> next line; Q quit
...
```

<span data-ttu-id="41173-119">Ciò si applica a tutti i cmdlet **Out**.</span><span class="sxs-lookup"><span data-stu-id="41173-119">This applies to all of the **Out** cmdlets.</span></span> <span data-ttu-id="41173-120">Un cmdlet **Out** deve essere sempre visualizzato alla fine della pipeline.</span><span class="sxs-lookup"><span data-stu-id="41173-120">An **Out** cmdlet should always appear at the end of the pipeline.</span></span>

> [!NOTE]
> <span data-ttu-id="41173-121">Tutti i cmdlet **Out** eseguono il rendering dell'output come testo, usando la formattazione esistente per la finestra della console, inclusi i limiti di lunghezza delle righe.</span><span class="sxs-lookup"><span data-stu-id="41173-121">All the **Out** cmdlets render output as text, using the formatting in effect for the console window, including line length limits.</span></span>

## <a name="paging-console-output-out-host"></a><span data-ttu-id="41173-122">Paging dell'output della console (Out-Host)</span><span class="sxs-lookup"><span data-stu-id="41173-122">Paging Console Output (Out-Host)</span></span>

<span data-ttu-id="41173-123">Per impostazione predefinita, Windows PowerShell invia dati alla finestra host, che è esattamente quello che fa il cmdlet Out-Host.</span><span class="sxs-lookup"><span data-stu-id="41173-123">By default, Windows PowerShell sends data to the host window, which is exactly what the Out-Host cmdlet does.</span></span> <span data-ttu-id="41173-124">L'uso principale del cmdlet Out-Host è il paging dei dati come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="41173-124">The primary use for the Out-Host cmdlet is paging data as we discussed earlier.</span></span> <span data-ttu-id="41173-125">Il comando seguente usa ad esempio Out-Host per il paging dell'output del cmdlet Get-Command:</span><span class="sxs-lookup"><span data-stu-id="41173-125">For example, the following command uses Out-Host to page the output of the Get-Command cmdlet:</span></span>

```powershell
Get-Command | Out-Host -Paging
```

<span data-ttu-id="41173-126">È anche possibile usare la funzione **more** per il paging dei dati.</span><span class="sxs-lookup"><span data-stu-id="41173-126">You can also use the **more** function to page data.</span></span> <span data-ttu-id="41173-127">In Windows PowerShell **more** è una funzione che chiama **Out-Host -Paging**.</span><span class="sxs-lookup"><span data-stu-id="41173-127">In Windows PowerShell, **more** is a function that calls **Out-Host -Paging**.</span></span> <span data-ttu-id="41173-128">Il comando seguente dimostra l'uso della funzione **more** per il paging dell'output di Get-Command:</span><span class="sxs-lookup"><span data-stu-id="41173-128">The following command demonstrates using the **more** function to page the output of Get-Command:</span></span>

```powershell
Get-Command | more
```

<span data-ttu-id="41173-129">Se si include uno o più nomi di file come argomenti della funzione more, la funzione leggerà i file specificati ed eseguirà il paging del contenuto all'host:</span><span class="sxs-lookup"><span data-stu-id="41173-129">If you include one or more filenames as arguments to the more function, the function will read the specified files and page their contents to the host:</span></span>

```
PS> more c:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
...
```

## <a name="discarding-output-out-null"></a><span data-ttu-id="41173-130">Eliminazione dell'output (Out-Null)</span><span class="sxs-lookup"><span data-stu-id="41173-130">Discarding Output (Out-Null)</span></span>

<span data-ttu-id="41173-131">Il cmdlet **Out-Null** è progettato per eliminare immediatamente qualsiasi input ricevuto.</span><span class="sxs-lookup"><span data-stu-id="41173-131">The **Out-Null** cmdlet is designed to immediately discard any input it receives.</span></span> <span data-ttu-id="41173-132">Questa funzionalità è utile per l'eliminazione dei dati non necessari ottenuti come effetto collaterale dell'esecuzione di un comando.</span><span class="sxs-lookup"><span data-stu-id="41173-132">This is useful for discarding unnecessary data that you get as a side-effect of running a command.</span></span> <span data-ttu-id="41173-133">Quando si digita il comando seguente, non verrà restituito niente dal comando:</span><span class="sxs-lookup"><span data-stu-id="41173-133">When type the following command, you do not get anything back from the command:</span></span>

```powershell
Get-Command | Out-Null
```

<span data-ttu-id="41173-134">Il cmdlet **Out-Null** non elimina l'output di errore.</span><span class="sxs-lookup"><span data-stu-id="41173-134">The **Out-Null** cmdlet does not discard error output.</span></span> <span data-ttu-id="41173-135">Se ad esempio si immette il comando seguente, viene visualizzato un messaggio che informa che Windows PowerShell non riconosce "Is-NotACommand":</span><span class="sxs-lookup"><span data-stu-id="41173-135">For example, if you enter the following command, a message is displayed informing you that Windows PowerShell does not recognize 'Is-NotACommand':</span></span>

```
PS> Get-Command Is-NotACommand | Out-Null
Get-Command : 'Is-NotACommand' is not recognized as a cmdlet, function, operabl
e program, or script file.
At line:1 char:12
+ Get-Command  <<<< Is-NotACommand | Out-Null
```

## <a name="printing-data-out-printer"></a><span data-ttu-id="41173-136">Stampa dei dati (Out-Printer)</span><span class="sxs-lookup"><span data-stu-id="41173-136">Printing Data (Out-Printer)</span></span>

<span data-ttu-id="41173-137">È possibile stampare dati usando il cmdlet **Out-Printer**.</span><span class="sxs-lookup"><span data-stu-id="41173-137">You can print data by using the **Out-Printer** cmdlet.</span></span> <span data-ttu-id="41173-138">Il cmdlet **Out-Printer** userà la stampante predefinita se non si specifica il nome della stampante.</span><span class="sxs-lookup"><span data-stu-id="41173-138">The **Out-Printer** cmdlet will use your default printer if you do not provide a printer name.</span></span> <span data-ttu-id="41173-139">È possibile usare qualsiasi stampante basata su Windows specificandone il nome visualizzato.</span><span class="sxs-lookup"><span data-stu-id="41173-139">You can use any Windows-based printer by specifying its display name.</span></span> <span data-ttu-id="41173-140">Non è necessario alcun tipo di mapping delle porte della stampante, né una stampante fisica reale.</span><span class="sxs-lookup"><span data-stu-id="41173-140">There is no need for any kind of printer port mapping or even a real physical printer.</span></span> <span data-ttu-id="41173-141">Se ad esempio sono installati gli strumenti di acquisizione immagini per i documenti di Microsoft Office, è possibile inviare i dati in un file di immagine digitando:</span><span class="sxs-lookup"><span data-stu-id="41173-141">For example, if you have the Microsoft Office document imaging tools installed, you can send the data to an image file by typing:</span></span>

```powershell
Get-Command Get-Command | Out-Printer -Name 'Microsoft Office Document Image Writer'
```

## <a name="saving-data-out-file"></a><span data-ttu-id="41173-142">Salvataggio dei dati (Out-File)</span><span class="sxs-lookup"><span data-stu-id="41173-142">Saving Data (Out-File)</span></span>

<span data-ttu-id="41173-143">È possibile inviare l'output in un file anziché nella finestra della console usando il cmdlet **Out-File**.</span><span class="sxs-lookup"><span data-stu-id="41173-143">You can send output to a file instead of the console window by using the **Out-File** cmdlet.</span></span> <span data-ttu-id="41173-144">La seguente riga di comando invia un elenco di processi al file **C:\\temp\\processlist.txt**:</span><span class="sxs-lookup"><span data-stu-id="41173-144">The following command line sends a list of processes to the file **C:\\temp\\processlist.txt**:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt
```

<span data-ttu-id="41173-145">I risultati dell'uso del cmdlet **Out-File** potrebbero non essere quelli previsti se si è abituati al reindirizzamento dell'output tradizionale.</span><span class="sxs-lookup"><span data-stu-id="41173-145">The results of using the **Out-File** cmdlet may not be what you expect if you are used to traditional output redirection.</span></span> <span data-ttu-id="41173-146">Per comprendere questo comportamento, è necessario considerare il contesto in cui viene eseguito il cmdlet **Out-File**.</span><span class="sxs-lookup"><span data-stu-id="41173-146">To understand its behavior, you must be aware of the context in which the **Out-File** cmdlet operates.</span></span>

<span data-ttu-id="41173-147">Per impostazione predefinita, il cmdlet **Out-File** crea un file Unicode.</span><span class="sxs-lookup"><span data-stu-id="41173-147">By default, the **Out-File** cmdlet creates a Unicode file.</span></span> <span data-ttu-id="41173-148">Questo è il valore predefinito migliore a lungo termine, ma significa che gli strumenti che prevedono file ASCII non funzioneranno correttamente con il formato di output predefinito.</span><span class="sxs-lookup"><span data-stu-id="41173-148">This is the best default in the long run, but it means that tools that expect ASCII files will not work correctly with the default output format.</span></span> <span data-ttu-id="41173-149">È possibile cambiare il formato di output predefinito in ASCII usando il parametro **Encoding**:</span><span class="sxs-lookup"><span data-stu-id="41173-149">You can change the default output format to ASCII by using the **Encoding** parameter:</span></span>

```powershell
Get-Process | Out-File -FilePath C:\temp\processlist.txt -Encoding ASCII
```

<span data-ttu-id="41173-150">**Out-file** formatta il contenuto del file come output della console.</span><span class="sxs-lookup"><span data-stu-id="41173-150">**Out-file** formats file contents to look like console output.</span></span> <span data-ttu-id="41173-151">In questo modo l'output risulta troncato proprio come accade nella maggior parte dei casi in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="41173-151">This causes the output to be truncated just as it is in a console window in most circumstances.</span></span> <span data-ttu-id="41173-152">Se ad esempio si esegue il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="41173-152">For example, if you run the following command:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt
```

<span data-ttu-id="41173-153">L'output sarà il seguente:</span><span class="sxs-lookup"><span data-stu-id="41173-153">The output will look like this:</span></span>

```output
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
...
```

<span data-ttu-id="41173-154">Per ottenere un output che non forzi il ritorno a capo automatico in base alla larghezza dello schermo, è possibile usare il parametro **Width** per specificare la lunghezza delle righe.</span><span class="sxs-lookup"><span data-stu-id="41173-154">To get output that does not force line wraps to match the screen width, you can use the **Width** parameter to specify line width.</span></span> <span data-ttu-id="41173-155">Dal momento che **Width** è un parametro intero a 32 bit, il valore massimo che può avere è 2147483647.</span><span class="sxs-lookup"><span data-stu-id="41173-155">Because **Width** is a 32-bit integer parameter, the maximum value it can have is 2147483647.</span></span> <span data-ttu-id="41173-156">Digitare quanto segue per impostare la lunghezza delle righe su questo valore massimo:</span><span class="sxs-lookup"><span data-stu-id="41173-156">Type the following to set the line width to this maximum value:</span></span>

```powershell
Get-Command | Out-File -FilePath c:\temp\output.txt -Width 2147483647
```

<span data-ttu-id="41173-157">Il cmdlet **Out-File** è particolarmente utile quando si vuole salvare l'output come sarebbe stato visualizzato nella console.</span><span class="sxs-lookup"><span data-stu-id="41173-157">The **Out-File** cmdlet is most useful when you want to save output as it would have displayed on the console.</span></span> <span data-ttu-id="41173-158">Per un controllo più preciso del formato dell'output, sono necessari strumenti più avanzati,</span><span class="sxs-lookup"><span data-stu-id="41173-158">For finer control over output format, you need more advanced tools.</span></span> <span data-ttu-id="41173-159">che saranno presi in esame nel capitolo successivo, insieme ad alcuni dettagli sulla manipolazione degli oggetti.</span><span class="sxs-lookup"><span data-stu-id="41173-159">We will look at those in the next chapter, along with some details about object manipulation.</span></span>
