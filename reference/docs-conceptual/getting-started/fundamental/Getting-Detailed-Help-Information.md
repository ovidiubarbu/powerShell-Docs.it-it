---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Ottenere informazioni dettagliate della Guida
ms.assetid: 6fb4daf7-8607-4a3e-b692-f77631adc1b9
ms.openlocfilehash: 67e02b503acf4d683c5a190d6642dea384bbfad2
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="e79f4-103">Ottenere informazioni dettagliate della Guida</span><span class="sxs-lookup"><span data-stu-id="e79f4-103">Getting Detailed Help Information</span></span>
<span data-ttu-id="e79f4-104">Windows PowerShell include argomenti dettagliati della Guida che illustrano i concetti e il linguaggio di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e79f4-104">Windows PowerShell includes detailed Help topics that explain Windows PowerShell concepts and the Windows PowerShell language.</span></span> <span data-ttu-id="e79f4-105">Sono inoltre disponibili argomenti della Guida per tutti i cmdlet e i provider, nonché per molti script e funzioni.</span><span class="sxs-lookup"><span data-stu-id="e79f4-105">There are also Help topics for each cmdlet and provider and Help topics for many functions and scripts.</span></span>

<span data-ttu-id="e79f4-106">È possibile visualizzare gli argomenti della Guida al prompt dei comandi oppure visualizzarne le versioni più aggiornate nella Libreria Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="e79f4-106">You can display these Help topics at the command prompt or view the most recently updated versions of these topics in the Microsoft TechNet Library.</span></span> <span data-ttu-id="e79f4-107">Molti programmi che ospitano Windows PowerShell, come Windows PowerShell Integrated Scripting Environment, offrono funzionalità aggiuntive della Guida, come la Guida sensibile al contesto e il file della Guida compilato (con estensione chm).</span><span class="sxs-lookup"><span data-stu-id="e79f4-107">Many programs that host Windows PowerShell, such as Windows PowerShell Integrated Scripting Environment, provide additional Help features, such as context-sensitive Help and compiled Help file (.chm).</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="e79f4-108">Ottenere informazioni della Guida per i cmdlet</span><span class="sxs-lookup"><span data-stu-id="e79f4-108">Getting Help for Cmdlets</span></span>
<span data-ttu-id="e79f4-109">Per ottenere informazioni della Guida sui cmdlet di Windows PowerShell, usare il cmdlet [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2).</span><span class="sxs-lookup"><span data-stu-id="e79f4-109">To get Help about Windows PowerShell cmdlets, use the [Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2) cmdlet.</span></span> <span data-ttu-id="e79f4-110">Per visualizzare ad esempio la Guida per il cmdlet [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc), digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-110">For example, to get Help for the [Get-ChildItem [m2]](https://technet.microsoft.com/library/4b270d63-c995-45b8-b5b4-3f8887efbfcc) cmdlet, type:</span></span>

```
get-help get-childitem
```

<span data-ttu-id="e79f4-111">o</span><span class="sxs-lookup"><span data-stu-id="e79f4-111">or</span></span>

```
get-childitem -?
```

<span data-ttu-id="e79f4-112">È anche possibile ottenere informazioni della Guida sul cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-112">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="e79f4-113">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="e79f4-113">For example:</span></span>

```
get-help get-help
```

<span data-ttu-id="e79f4-114">Per ottenere un elenco di tutti gli argomenti della Guida sui cmdlet nella sessione corrente, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-114">To get a list of all the cmdlet Help topics in your session, type:</span></span>

```
get-help -category cmdlet
```

<span data-ttu-id="e79f4-115">Per visualizzare una pagina alla volta di ogni argomento della Guida, usare la funzione **help** o il relativo alias **man**.</span><span class="sxs-lookup"><span data-stu-id="e79f4-115">To display one page of each Help topic at a time, use the **help** function or its alias **man**.</span></span> <span data-ttu-id="e79f4-116">Per visualizzare ad esempio la Guida per il cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-116">For example, to display Help for the Get-ChildItem cmdlet, type</span></span>

```
man get-childitem
```

<span data-ttu-id="e79f4-117">o</span><span class="sxs-lookup"><span data-stu-id="e79f4-117">or</span></span>

```
help get-childitem
```

<span data-ttu-id="e79f4-118">Per visualizzare informazioni dettagliate su un cmdlet, una funzione o uno script, incluse le descrizioni dei relativi parametri ed esempi della sua applicazione, usare il parametro *Detailed* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-118">To display detailed information about a cmdlet, function, or script, including descriptions of its parameters and examples of its use, use the *Detailed* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e79f4-119">Per ottenere ad esempio informazioni dettagliate sul cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-119">For example, to get detailed information about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -detailed
```

<span data-ttu-id="e79f4-120">Per visualizzare l'intero contenuto dell'argomento della Guida, usare il parametro *Full* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-120">To display all content in the Help topic, use the *Full* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e79f4-121">Per visualizzare ad esempio l'intero contenuto dell'argomento della Guida per il cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-121">For example, to display all content in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -full
```

<span data-ttu-id="e79f4-122">Per ottenere informazioni dettagliate della Guida sui parametri di un cmdlet, usare il parametro *Parameter* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-122">To get detailed Help about the parameters of a cmdlet, use the *Parameter* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e79f4-123">Per ottenere ad esempio informazioni dettagliate della Guida per tutti i parametri del cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-123">For example, to get detailed Help for all of the parameters of the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -parameter *
```

<span data-ttu-id="e79f4-124">Per visualizzare solo gli esempi di un argomento della Guida, usare il parametro *Example* di Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-124">To display only the examples in a Help topic, use the *Example* parameter of the Get-Help.</span></span> <span data-ttu-id="e79f4-125">Per visualizzare ad esempio solo gli esempi dell'argomento della Guida per il cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-125">For example, to display only the examples in the Help topic for the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -examples
```

<span data-ttu-id="e79f4-126">Per informazioni su come scrivere argomenti della Guida per cmdlet personalizzati, vedere [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere la Guida dei cmdlet) in MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="e79f4-126">For information about how to write Help topics for the cmdlets that you write, see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="e79f4-127">Ottenere informazioni della Guida concettuale</span><span class="sxs-lookup"><span data-stu-id="e79f4-127">Getting Conceptual Help</span></span>
<span data-ttu-id="e79f4-128">Il cmdlet Get-Help visualizza anche informazioni sugli argomenti concettuali in Windows PowerShell, inclusi gli argomenti sul linguaggio di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e79f4-128">The Get-Help cmdlet also displays information about conceptual topics in Windows PowerShell, including topics about the Windows PowerShell language.</span></span> <span data-ttu-id="e79f4-129">Gli argomenti della Guida concettuale iniziano con il prefisso "about_", ad esempio about_line_editing</span><span class="sxs-lookup"><span data-stu-id="e79f4-129">Conceptual Help topics begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="e79f4-130">(il nome dell'argomento concettuale deve essere immesso in inglese anche nelle versioni di Windows PowerShell in altre lingue).</span><span class="sxs-lookup"><span data-stu-id="e79f4-130">(The name of the conceptual topic must be entered in English even on non-English versions of Windows PowerShell.)</span></span>

<span data-ttu-id="e79f4-131">Per visualizzare un elenco di argomenti concettuali, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-131">To display a list of conceptual topics, type:</span></span>

```
get-help about_*
```

<span data-ttu-id="e79f4-132">Per visualizzare uno specifico argomento della Guida, digitare il nome dell'argomento, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="e79f4-132">To display a particular Help topic, type the topic name, for example:</span></span>

```
get-help about_command_syntax
```

<span data-ttu-id="e79f4-133">I parametri di Get-Help, come *Detailed*, *Parameter* e *Examples*, non hanno alcun effetto sulla visualizzazione degli argomenti della Guida concettuale.</span><span class="sxs-lookup"><span data-stu-id="e79f4-133">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of conceptual Help topics.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="e79f4-134">Ottenere informazioni della Guida sui provider</span><span class="sxs-lookup"><span data-stu-id="e79f4-134">Getting Help About Providers</span></span>
<span data-ttu-id="e79f4-135">Il cmdlet Get-Help visualizza informazioni sui provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e79f4-135">The Get-Help cmdlet displays information about Windows PowerShell providers.</span></span> <span data-ttu-id="e79f4-136">Per visualizzare le informazioni della Guida per un provider, digitare "Get-Help" seguito dal nome del provider.</span><span class="sxs-lookup"><span data-stu-id="e79f4-136">To get Help for a provider, type "Get-Help" followed by the provider name.</span></span> <span data-ttu-id="e79f4-137">Per visualizzare ad esempio la Guida per il provider del Registro di sistema, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-137">For example, to get Help for the Registry provider, type:</span></span>

```
get-help registry
```

<span data-ttu-id="e79f4-138">Per ottenere un elenco di tutti gli argomenti della Guida sui provider nella sessione corrente, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-138">To get a list of all the provider Help topics in your session, type</span></span>

```
get-help -category provider
```

<span data-ttu-id="e79f4-139">I parametri di Get-Help, come *Detailed*, *Parameter* e *Examples*, non hanno alcun effetto sulla visualizzazione degli argomenti della Guida sui provider.</span><span class="sxs-lookup"><span data-stu-id="e79f4-139">The parameters of Get-Help, such as *Detailed*, *Parameter*, and *Examples*, have no effect on the display of provider Help topics.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="e79f4-140">Ottenere informazioni della Guida sugli script e sulle funzioni</span><span class="sxs-lookup"><span data-stu-id="e79f4-140">Getting Help About Scripts and Functions</span></span>
<span data-ttu-id="e79f4-141">A molti script e funzioni di Windows PowerShell sono associati argomenti della Guida.</span><span class="sxs-lookup"><span data-stu-id="e79f4-141">Many scripts and functions in Windows PowerShell have Help topics.</span></span> <span data-ttu-id="e79f4-142">Usare il cmdlet Get-Help per visualizzare gli argomenti della Guida per gli script e le funzioni.</span><span class="sxs-lookup"><span data-stu-id="e79f4-142">Use the Get-Help cmdlet to display the Help topics for scripts and functions.</span></span>

<span data-ttu-id="e79f4-143">Per visualizzare la Guida per una funzione, digitare "get-help" seguito dal nome della funzione.</span><span class="sxs-lookup"><span data-stu-id="e79f4-143">To display the Help for a function, type "get-help" followed by the function name.</span></span> <span data-ttu-id="e79f4-144">Per ottenere ad esempio informazioni della Guida per la funzione Disable-PSRemoting, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-144">For example, to get Help for the Disable-PSRemoting function, type:</span></span>

```
get-help disable-psremoting
```

<span data-ttu-id="e79f4-145">Per visualizzare la Guida per uno script, digitare il percorso completo del file di script.</span><span class="sxs-lookup"><span data-stu-id="e79f4-145">To display the Help for a script, type the fully qualified path to the script file.</span></span> <span data-ttu-id="e79f4-146">Se lo script è in un percorso elencato nella variabile di ambiente Path, è possibile omettere il percorso dal comando.</span><span class="sxs-lookup"><span data-stu-id="e79f4-146">If the script is in a path that is listed in the Path environment variable, you can omit the path from the command.</span></span>

<span data-ttu-id="e79f4-147">Se ad esempio si dispone di uno script denominato "TestScript.ps1" nella directory C:\\PS-Test, per visualizzare l'argomento della Guida per lo script digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-147">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help topic for the script, type:</span></span>

```
get-help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="e79f4-148">I parametri progettati per la visualizzazione della Guida dei cmdlet, come *Detailed*, *Full*, *Examples* e *Parameter*, possono essere usati anche per la Guida relativa agli script e alle funzioni.</span><span class="sxs-lookup"><span data-stu-id="e79f4-148">The parameters that were designed for displaying cmdlet Help, such as *Detailed*, *Full*, *Examples*, and *Parameter*, work for script Help and function Help, too.</span></span> <span data-ttu-id="e79f4-149">Quando tuttavia si visualizza l'intera Guida, digitando "get-help \*", la Guida per le funzioni e gli script non viene visualizzata.</span><span class="sxs-lookup"><span data-stu-id="e79f4-149">However, when you display all Help, by typing "get-help \*", Help for functions and scripts does not appear.</span></span>

<span data-ttu-id="e79f4-150">Per informazioni su come scrivere argomenti della Guida per funzioni e script personalizzati, vedere [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af) e [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span><span class="sxs-lookup"><span data-stu-id="e79f4-150">For information about writing Help topics for your functions and scripts, see [about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105), [about_Scripts](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af), and [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf).</span></span>

## <a name="getting-help-online"></a><span data-ttu-id="e79f4-151">Ottenere informazioni della Guida online</span><span class="sxs-lookup"><span data-stu-id="e79f4-151">Getting Help Online</span></span>
<span data-ttu-id="e79f4-152">Se si è connessi a Internet, uno dei modi migliori per ottenere assistenza è visualizzare gli argomenti della Guida online.</span><span class="sxs-lookup"><span data-stu-id="e79f4-152">If you are connected to the Internet, one of the best ways to get Help is to view the Help topics online.</span></span> <span data-ttu-id="e79f4-153">Essendo più semplici da aggiornare, gli argomenti della Guida online sono quelli con i contenuti più attuali.</span><span class="sxs-lookup"><span data-stu-id="e79f4-153">Because online topics are easy to update, they are likely to provide the most current content.</span></span>

<span data-ttu-id="e79f4-154">Per ottenere informazioni della Guida online, usare il parametro *Online* del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-154">To get Help online, try the *Online* parameter of the Get-Help cmdlet.</span></span> <span data-ttu-id="e79f4-155">Il parametro *Online* del cmdlet Get-Help può essere usato solo per il cmdlet Help, la funzione Help e lo script Help.</span><span class="sxs-lookup"><span data-stu-id="e79f4-155">The *Online* parameter of the Get-Help cmdlet works only for cmdlet Help, function Help, and script Help.</span></span> <span data-ttu-id="e79f4-156">Non è possibile usare il parametro *Online* con gli argomenti concettuali (about_) o con quelli della Guida per i provider.</span><span class="sxs-lookup"><span data-stu-id="e79f4-156">You cannot use the *Online* parameter with conceptual (About) topics or provider Help topics.</span></span> <span data-ttu-id="e79f4-157">Poiché questa funzionalità è opzionale, non funziona inoltre per gli argomenti della Guida di tutti i cmdlet, le funzioni o gli script.</span><span class="sxs-lookup"><span data-stu-id="e79f4-157">Also, because this feature is optional, it does not work for every cmdlet, function, or script Help topic.</span></span>

<span data-ttu-id="e79f4-158">Tutti gli argomenti della Guida disponibili per Windows PowerShell, inclusi gli argomenti della Guida concettuale (about_) e per i provider, sono tuttavia accessibili online nella sezione [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) della Libreria Microsoft TechNet.</span><span class="sxs-lookup"><span data-stu-id="e79f4-158">However, all the Help topics that come with Windows PowerShell, including provider Help and conceptual (About) Help topics, are available online in the [Windows PowerShell](http://go.microsoft.com/fwlink/?LinkID=107116) section of the Microsoft TechNet Library.</span></span>

<span data-ttu-id="e79f4-159">Per usare il parametro *Online* del cmdlet Get-Help, usare il comando nel formato seguente.</span><span class="sxs-lookup"><span data-stu-id="e79f4-159">To use the *Online* parameter of the Get-Help cmdlet, use the following command format.</span></span>

```
get-help <command-name> -online
```

<span data-ttu-id="e79f4-160">Per ottenere ad esempio la versione online dell'argomento della Guida sul cmdlet Get-ChildItem, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-160">For example, to get the online version of the Help topic about the Get-ChildItem cmdlet, type:</span></span>

```
get-help get-childitem -online
```

<span data-ttu-id="e79f4-161">Se è disponibile una versione online dell'argomento della Guida, si aprirà nel browser predefinito.</span><span class="sxs-lookup"><span data-stu-id="e79f4-161">If an online version of the Help topic is available, it will open in your default browser.</span></span>

<span data-ttu-id="e79f4-162">Se la Guida online è supportata per un argomento della Guida, è inoltre possibile visualizzare l'indirizzo Internet (URL) dell'argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="e79f4-162">If online Help is supported for a Help topic, you can also view the Internet address (URL) of the Help topic.</span></span> <span data-ttu-id="e79f4-163">L'indirizzo Internet compare nella sezione Collegamenti correlati di un argomento della Guida.</span><span class="sxs-lookup"><span data-stu-id="e79f4-163">The Internet address appears in the Related Links section of a Help topic.</span></span>

<span data-ttu-id="e79f4-164">Per visualizzare ad esempio l'URL per la versione online del cmdlet Add-Computer, digitare:</span><span class="sxs-lookup"><span data-stu-id="e79f4-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```
get-help add-computer
```

<span data-ttu-id="e79f4-165">Di seguito è riportata la prima riga nella sezione Collegamenti correlati dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="e79f4-165">The first line in the Related Links section of the topic is shown below.</span></span>

```
Online version: http://go.microsoft.com/fwlink/?LinkID=135194
```

<span data-ttu-id="e79f4-166">Per informazioni su come offrire supporto online per argomenti della Guida personalizzati, vedere [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf) e [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) (Come scrivere la Guida dei cmdlet) in MSDN Library.</span><span class="sxs-lookup"><span data-stu-id="e79f4-166">For information about how to provide online support for your Help topics, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf), and see [How to Write Cmdlet Help](https://go.microsoft.com/fwlink/?LinkID=123415) in the MSDN library.</span></span>

## <a name="see-also"></a><span data-ttu-id="e79f4-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e79f4-167">See Also</span></span>
- <span data-ttu-id="e79f4-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span><span class="sxs-lookup"><span data-stu-id="e79f4-168">[about_Functions [m2]](https://technet.microsoft.com/en-us/library/61d40692-5300-4de9-a9b5-bae31815e105)</span></span>
- [<span data-ttu-id="e79f4-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="e79f4-169">about_Scripts</span></span>](https://technet.microsoft.com/en-us/library/7dc08334-dcfe-450b-b949-0554855623af)
- [<span data-ttu-id="e79f4-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="e79f4-170">about_Comment_Based_Help</span></span>](https://technet.microsoft.com/en-us/library/99a81ccc-21a0-49ec-a1b3-9efe2b4c0bbf)
- <span data-ttu-id="e79f4-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span><span class="sxs-lookup"><span data-stu-id="e79f4-171">[Get-Help [m2]](https://technet.microsoft.com/library/2d7fe1b4-0025-4580-a911-d81922dd6cd2)</span></span>

