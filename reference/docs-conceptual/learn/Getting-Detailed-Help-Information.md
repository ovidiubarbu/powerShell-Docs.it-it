---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Ottenere informazioni dettagliate della Guida
ms.openlocfilehash: 3f52de8c9963618c154b119d5f4859a92d61fbda
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030394"
---
# <a name="getting-detailed-help-information"></a><span data-ttu-id="ad314-103">Ottenere informazioni dettagliate della Guida</span><span class="sxs-lookup"><span data-stu-id="ad314-103">Getting detailed help information</span></span>

<span data-ttu-id="ad314-104">PowerShell include articoli della Guida dettagliati che descrivono concetti correlati a PowerShell e il linguaggio PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad314-104">PowerShell includes detailed Help articles that explain PowerShell concepts and the PowerShell language.</span></span> <span data-ttu-id="ad314-105">Sono disponibili anche articoli della Guida per ogni cmdlet e provider e per molti script e funzioni.</span><span class="sxs-lookup"><span data-stu-id="ad314-105">There are also Help articles for each cmdlet and provider and for many functions and scripts.</span></span>

<span data-ttu-id="ad314-106">È possibile visualizzare questi articoli nel prompt dei comandi o esaminare la versione più recente di questi articoli online nella documentazione di [PowerShell](/powershell/scripting/overview).</span><span class="sxs-lookup"><span data-stu-id="ad314-106">You can display these Help articles at the command prompt or view the most recently updated versions of these articles in the [PowerShell](/powershell/scripting/overview) documentation online.</span></span>

## <a name="getting-help-for-cmdlets"></a><span data-ttu-id="ad314-107">Ottenere informazioni della Guida per i cmdlet</span><span class="sxs-lookup"><span data-stu-id="ad314-107">Getting help for cmdlets</span></span>

<span data-ttu-id="ad314-108">Per ottenere informazioni della Guida sui cmdlet di PowerShell, usare il cmdlet [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="ad314-108">To get Help about PowerShell cmdlets, use the [Get-Help](/powershell/module/microsoft.powershell.core/Get-Help) cmdlet.</span></span> <span data-ttu-id="ad314-109">Ad esempio, per ottenere informazioni della Guida sul cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-109">For example, to get Help for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem
```

<span data-ttu-id="ad314-110">o</span><span class="sxs-lookup"><span data-stu-id="ad314-110">or</span></span>

```powershell
Get-ChildItem -?
```

<span data-ttu-id="ad314-111">È anche possibile ottenere informazioni della Guida sul cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="ad314-111">You can even get Help about the Get-Help cmdlet.</span></span> <span data-ttu-id="ad314-112">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ad314-112">For example:</span></span>

```powershell
Get-Help Get-Help
```

<span data-ttu-id="ad314-113">Per ottenere un elenco di tutti gli articoli della Guida sui cmdlet nella sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-113">To get a list of all the cmdlet Help articles in your session, type:</span></span>

```powershell
Get-Help -Category Cmdlet
```

<span data-ttu-id="ad314-114">Per visualizzare una pagina di ogni articolo per volta, usare la funzione `help` o l'alias associato `man`.</span><span class="sxs-lookup"><span data-stu-id="ad314-114">To display one page of each Help article at a time, use the `help` function or its alias `man`.</span></span>
<span data-ttu-id="ad314-115">Ad esempio, per visualizzare la Guida per il cmdlet `Get-ChildItem`, digitare</span><span class="sxs-lookup"><span data-stu-id="ad314-115">For example, to display Help for the `Get-ChildItem` cmdlet, type</span></span>

```powershell
man Get-ChildItem
```

<span data-ttu-id="ad314-116">o</span><span class="sxs-lookup"><span data-stu-id="ad314-116">or</span></span>

```powershell
help Get-ChildItem
```

<span data-ttu-id="ad314-117">Per visualizzare informazioni dettagliate, usare il parametro **Detailed** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ad314-117">To display detailed information, use the **Detailed** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ad314-118">Ad esempio, per ottenere informazioni dettagliate sul cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-118">For example, to get detailed information about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Detailed
```

<span data-ttu-id="ad314-119">Per visualizzare tutto il contenuto dell'articolo della Guida, usare il parametro **Full** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ad314-119">To display all content in the Help article, use the **Full** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ad314-120">Ad esempio, per visualizzare tutto il contenuto dell'articolo della Guida per il cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-120">For example, to display all content in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Full
```

<span data-ttu-id="ad314-121">Per ottenere informazioni della Guida dettagliate sui parametri di un cmdlet, usare il parametro **Parameter** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ad314-121">To get detailed Help about the parameters of a cmdlet, use the **Parameter** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ad314-122">Ad esempio, per ottenere informazioni della Guida dettagliate per tutti i parametri del cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-122">For example, to get detailed Help for all of the parameters of the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Parameter *
```

<span data-ttu-id="ad314-123">Per visualizzare solo gli esempi in un articolo della Guida, usare il parametro **Examples** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ad314-123">To display only the examples in a Help article, use the **Examples** parameter of the `Get-Help`.</span></span>
<span data-ttu-id="ad314-124">Ad esempio, per visualizzare solo gli esempi dell'articolo della Guida per il cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-124">For example, to display only the examples in the Help article for the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Examples
```

<span data-ttu-id="ad314-125">Per informazioni su come scrivere articoli della Guida per i cmdlet personalizzati, vedere [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets) (Come scrivere articoli della Guida sui cmdlet).</span><span class="sxs-lookup"><span data-stu-id="ad314-125">For information about how to write Help articles for the cmdlets that you write, see [How to Write Cmdlet Help](/powershell/developer/help/writing-help-for-windows-powershell-cmdlets).</span></span>

## <a name="getting-conceptual-help"></a><span data-ttu-id="ad314-126">Ottenere informazioni della Guida di carattere concettuale</span><span class="sxs-lookup"><span data-stu-id="ad314-126">Getting conceptual help</span></span>

<span data-ttu-id="ad314-127">Il cmdlet `Get-Help` visualizza anche informazioni sugli articoli di carattere concettuale in PowerShell, tra cui gli articoli sul linguaggio PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad314-127">The `Get-Help` cmdlet also displays information about conceptual articles in PowerShell, including articles about the PowerShell language.</span></span> <span data-ttu-id="ad314-128">Gli articoli della Guida di carattere concettuale iniziano con il prefisso "about_", ad esempio about_line_editing.</span><span class="sxs-lookup"><span data-stu-id="ad314-128">Conceptual Help articles begin with the "about_" prefix, such as about_line_editing.</span></span> <span data-ttu-id="ad314-129">Il nome dell'articolo di carattere concettuale deve essere immesso in inglese anche nelle versioni di Windows PowerShell in altre lingue.</span><span class="sxs-lookup"><span data-stu-id="ad314-129">(The name of the conceptual article must be entered in English even on non-English versions of PowerShell.)</span></span>

<span data-ttu-id="ad314-130">Per visualizzare un elenco di articoli di carattere concettuale, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-130">To display a list of conceptual articles, type:</span></span>

```powershell
Get-Help about_*
```

<span data-ttu-id="ad314-131">Per visualizzare un articolo specifico della Guida, digitarne il nome, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ad314-131">To display a particular Help article, type the article name, for example:</span></span>

```powershell
Get-Help about_command_syntax
```

<span data-ttu-id="ad314-132">I parametri di `Get-Help`, come **Detailed**, **Parameter** ed **Examples**, non hanno effetto sulla visualizzazione di articoli della Guida di carattere concettuale.</span><span class="sxs-lookup"><span data-stu-id="ad314-132">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of conceptual Help articles.</span></span>

## <a name="getting-help-about-providers"></a><span data-ttu-id="ad314-133">Ottenere informazioni della Guida sui provider</span><span class="sxs-lookup"><span data-stu-id="ad314-133">Getting help about providers</span></span>

<span data-ttu-id="ad314-134">Il cmdlet `Get-Help` visualizza informazioni sui provider di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ad314-134">The `Get-Help` cmdlet displays information about PowerShell providers.</span></span> <span data-ttu-id="ad314-135">Per ottenere informazioni della Guida su un provider, digitare `Get-Help` seguito dal nome del provider.</span><span class="sxs-lookup"><span data-stu-id="ad314-135">To get Help for a provider, type `Get-Help` followed by the provider name.</span></span> <span data-ttu-id="ad314-136">Per visualizzare ad esempio la Guida per il provider del Registro di sistema, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-136">For example, to get Help for the Registry provider, type:</span></span>

```powershell
Get-Help registry
```

<span data-ttu-id="ad314-137">Per ottenere un elenco di tutti gli argomenti della Guida sui provider nella sessione, digitare</span><span class="sxs-lookup"><span data-stu-id="ad314-137">To get a list of all the provider Help articles in your session, type</span></span>

```powershell
Get-Help -Category provider
```

<span data-ttu-id="ad314-138">I parametri di `Get-Help`, come **Detailed**, **Parameter** ed **Examples**, non hanno effetto sulla visualizzazione di articoli della Guida sui provider.</span><span class="sxs-lookup"><span data-stu-id="ad314-138">The parameters of `Get-Help`, such as **Detailed**, **Parameter**, and **Examples**, have no effect on the display of provider Help articles.</span></span>

## <a name="getting-help-about-scripts-and-functions"></a><span data-ttu-id="ad314-139">Ottenere informazioni della Guida su script e funzioni</span><span class="sxs-lookup"><span data-stu-id="ad314-139">Getting help about scripts and functions</span></span>

<span data-ttu-id="ad314-140">In PowerShell sono disponibili argomenti della Guida per molti script e funzioni.</span><span class="sxs-lookup"><span data-stu-id="ad314-140">Many scripts and functions in PowerShell have Help articles.</span></span> <span data-ttu-id="ad314-141">Usare il cmdlet `Get-Help` per visualizzare gli argomenti della Guida per script e funzioni.</span><span class="sxs-lookup"><span data-stu-id="ad314-141">Use the `Get-Help` cmdlet to display the Help articles for scripts and functions.</span></span>

<span data-ttu-id="ad314-142">Per visualizzare la Guida per una funzione, digitare `Get-Help` seguito dal nome della funzione.</span><span class="sxs-lookup"><span data-stu-id="ad314-142">To display the Help for a function, type `Get-Help` followed by the function name.</span></span> <span data-ttu-id="ad314-143">Ad esempio, per ottenere informazioni della Guida per la funzione `Disable-PSRemoting`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-143">For example, to get Help for the `Disable-PSRemoting` function, type:</span></span>

```powershell
Get-Help Disable-PSRemoting
```

<span data-ttu-id="ad314-144">Per visualizzare la Guida per uno script, digitare il percorso del file script.</span><span class="sxs-lookup"><span data-stu-id="ad314-144">To display the Help for a script, type the path to the script file.</span></span> <span data-ttu-id="ad314-145">Se lo script non si trova in un percorso elencato nella variabile di ambiente Path, è necessario usare il percorso completo.</span><span class="sxs-lookup"><span data-stu-id="ad314-145">If the script is not in a path listed in the Path environment variable, you must use the fully qualified path.</span></span>

<span data-ttu-id="ad314-146">Ad esempio, per visualizzare l'articolo della Guida per uno script denominato "TestScript.ps1" nella directory C:\\PS-Test, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-146">For example, if you have a script called "TestScript.ps1" in your C:\\PS-Test directory, to display the Help article for the script, type:</span></span>

```powershell
Get-Help c:\ps-test\TestScript.ps1
```

<span data-ttu-id="ad314-147">I parametri progettati per la visualizzazione della Guida dei cmdlet, funzionano anche per gli script e le funzioni.</span><span class="sxs-lookup"><span data-stu-id="ad314-147">The parameters that are designed for displaying cmdlet Help work for script and function Help, too.</span></span> <span data-ttu-id="ad314-148">Tuttavia, la Guida per le funzioni e gli script non viene visualizzata quando si esegue `Get-Help *`.</span><span class="sxs-lookup"><span data-stu-id="ad314-148">However, help for functions and scripts is not shown when you run `Get-Help *`.</span></span>

<span data-ttu-id="ad314-149">Per informazioni sulla redazione di articoli della Guida per le funzioni e gli script, vedere gli articoli seguenti:</span><span class="sxs-lookup"><span data-stu-id="ad314-149">For information about writing Help articles for your functions and scripts, see the following articles:</span></span>

- [<span data-ttu-id="ad314-150">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ad314-150">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ad314-151">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ad314-151">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ad314-152">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ad314-152">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)

## <a name="getting-help-online"></a><span data-ttu-id="ad314-153">Ottenere informazioni della Guida online</span><span class="sxs-lookup"><span data-stu-id="ad314-153">Getting help online</span></span>

<span data-ttu-id="ad314-154">La visualizzazione online degli articoli della Guida è uno dei metodi migliori per ottenere informazioni utili.</span><span class="sxs-lookup"><span data-stu-id="ad314-154">Viewing the Help articles online is one of the best ways to get help.</span></span> <span data-ttu-id="ad314-155">Gli articoli online sono più semplici da aggiornare e offrono i contenuti più recenti.</span><span class="sxs-lookup"><span data-stu-id="ad314-155">Online articles are easier to update and provide the most current content.</span></span>

<span data-ttu-id="ad314-156">Per ottenere informazioni della Guida online, usare il parametro **Online** del cmdlet `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="ad314-156">To get Help online, use the **Online** parameter of the `Get-Help` cmdlet.</span></span> <span data-ttu-id="ad314-157">Tutti gli articoli della Guida per PowerShell, inclusi gli articoli della Guida di carattere concettuale (About) e sui provider, sono disponibili online nella documentazione di [PowerShell](/powershell/scripting/powershell-scripting).</span><span class="sxs-lookup"><span data-stu-id="ad314-157">All the Help articles that come with PowerShell, including provider Help and conceptual (About) Help articles, are available online in the [PowerShell](/powershell/scripting/powershell-scripting) documentation.</span></span>

> [!NOTE]
> <span data-ttu-id="ad314-158">Non è possibile usare il parametro **Online** con gli articoli della Guida di natura concettuale (about_\*) o sui provider.</span><span class="sxs-lookup"><span data-stu-id="ad314-158">You can't use the **Online** parameter with conceptual (about_\*) or provider Help articles.</span></span>
> <span data-ttu-id="ad314-159">Poiché la Guida online è facoltativa, non funziona per ogni cmdlet, funzione o script.</span><span class="sxs-lookup"><span data-stu-id="ad314-159">Online help is optional, so it does not work for every cmdlet, function, or script.</span></span>

<span data-ttu-id="ad314-160">Ad esempio, per ottenere la versione online dell'articolo della Guida sul cmdlet `Get-ChildItem`, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-160">For example, to get the online version of the Help article about the `Get-ChildItem` cmdlet, type:</span></span>

```powershell
Get-Help Get-ChildItem -Online
```

<span data-ttu-id="ad314-161">PowerShell visualizza l'articolo nel browser predefinito.</span><span class="sxs-lookup"><span data-stu-id="ad314-161">PowerShell opens the article in your default browser.</span></span> <span data-ttu-id="ad314-162">Se la Guida online è supportata per un articolo della Guida, è anche possibile visualizzare l'URL dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="ad314-162">If online Help is supported for a Help article, you can also view the URL of the Help article.</span></span> <span data-ttu-id="ad314-163">L'URL appare nella sezione Collegamenti correlati di un articolo della Guida.</span><span class="sxs-lookup"><span data-stu-id="ad314-163">The URL appears in the Related Links section of a Help article.</span></span>

<span data-ttu-id="ad314-164">Per visualizzare ad esempio l'URL per la versione online del cmdlet Add-Computer, digitare:</span><span class="sxs-lookup"><span data-stu-id="ad314-164">For example, to see the URL for the online version of the Add-Computer cmdlet, type:</span></span>

```powershell
Get-Help Add-Computer
```

<span data-ttu-id="ad314-165">Di seguito viene mostrata la prima riga della sezione Collegamenti correlati dell'articolo.</span><span class="sxs-lookup"><span data-stu-id="ad314-165">The first line in the Related Links section of the article is shown below.</span></span>

```Output
Online version: http://go.microsoft.com/fwlink/?LinkId=821564
```

<span data-ttu-id="ad314-166">Per informazioni su come offrire supporto online per gli articoli della Guida personalizzati, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="ad314-166">For information about how to provide online support for your Help articles, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

## <a name="see-also"></a><span data-ttu-id="ad314-167">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ad314-167">See also</span></span>

- [<span data-ttu-id="ad314-168">about_Functions</span><span class="sxs-lookup"><span data-stu-id="ad314-168">about_Functions</span></span>](/powershell/module/microsoft.powershell.core/about/about_functions)
- [<span data-ttu-id="ad314-169">about_Scripts</span><span class="sxs-lookup"><span data-stu-id="ad314-169">about_Scripts</span></span>](/powershell/module/microsoft.powershell.core/about/about_scripts)
- [<span data-ttu-id="ad314-170">about_Comment_Based_Help</span><span class="sxs-lookup"><span data-stu-id="ad314-170">about_Comment_Based_Help</span></span>](/powershell/module/microsoft.powershell.core/about/about_comment_based_help)
- [<span data-ttu-id="ad314-171">Get-Help</span><span class="sxs-lookup"><span data-stu-id="ad314-171">Get-Help</span></span>](/powershell/module/microsoft.powershell.core/get-help)
