---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: Uso dei comandi Format per modificare la visualizzazione dell'output
ms.openlocfilehash: f270d5ec5efe5caf506d6a8a45285990996f6ae6
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "74417600"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="af81b-103">Uso dei comandi Format per modificare la visualizzazione dell'output</span><span class="sxs-lookup"><span data-stu-id="af81b-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="af81b-104">PowerShell include un set di cmdlet che consentono di controllare la visualizzazione delle proprietà per oggetti specifici.</span><span class="sxs-lookup"><span data-stu-id="af81b-104">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="af81b-105">I nomi di tutti i cmdlet iniziano con il verbo `Format`.</span><span class="sxs-lookup"><span data-stu-id="af81b-105">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="af81b-106">Consentono di selezionare le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="af81b-106">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="af81b-107">Questo articolo descrive i cmdlet `Format-Wide`, `Format-List` e `Format-Table`.</span><span class="sxs-lookup"><span data-stu-id="af81b-107">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="af81b-108">Tutti i tipi di oggetto in PowerShell includono proprietà predefinite che vengono usate quando non sono specificate le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="af81b-108">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="af81b-109">Tutti i cmdlet usano anche lo stesso parametro **Property** per specificare le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="af81b-109">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="af81b-110">Poiché `Format-Wide` visualizza solo una singola proprietà, il relativo parametro **Property** accetta un solo valore, ma i parametri della proprietà di `Format-List` e `Format-Table` accettano un elenco di nomi di proprietà.</span><span class="sxs-lookup"><span data-stu-id="af81b-110">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="af81b-111">In questo esempio l'output predefinito del cmdlet `Get-Process` indica che sono in esecuzione due istanze di Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="af81b-111">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="af81b-112">Il formato predefinito per gli oggetti **Process** visualizza le proprietà indicate di seguito:</span><span class="sxs-lookup"><span data-stu-id="af81b-112">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="af81b-113">Uso di Format-Wide per output a elemento singolo</span><span class="sxs-lookup"><span data-stu-id="af81b-113">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="af81b-114">Per impostazione predefinita, il cmdlet `Format-Wide` visualizza solo la proprietà predefinita di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="af81b-114">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="af81b-115">Le informazioni associate a ogni oggetto sono visualizzate in una singola colonna:</span><span class="sxs-lookup"><span data-stu-id="af81b-115">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="af81b-116">È inoltre possibile specificare una proprietà non predefinita:</span><span class="sxs-lookup"><span data-stu-id="af81b-116">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="af81b-117">Controllo della visualizzazione di Format-Wide con il parametro Column</span><span class="sxs-lookup"><span data-stu-id="af81b-117">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="af81b-118">Con il cmdlet `Format-Wide` è possibile visualizzare unicamente una sola proprietà alla volta.</span><span class="sxs-lookup"><span data-stu-id="af81b-118">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="af81b-119">È utile per la visualizzazione di elenchi di grandi dimensioni in più colonne.</span><span class="sxs-lookup"><span data-stu-id="af81b-119">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="af81b-120">Uso di Format-List per una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="af81b-120">Using Format-List for a List View</span></span>

<span data-ttu-id="af81b-121">Il cmdlet `Format-List` visualizza un oggetto sotto forma di elenco. Ogni proprietà ha un'etichetta ed è visualizzata in una riga distinta:</span><span class="sxs-lookup"><span data-stu-id="af81b-121">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="af81b-122">È possibile specificare il numero di proprietà che si vuole:</span><span class="sxs-lookup"><span data-stu-id="af81b-122">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="af81b-123">Ottenere informazioni dettagliate usando Format-List con i caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="af81b-123">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="af81b-124">Il cmdlet `Format-List` consente di usare un carattere jolly come valore del rispettivo parametro **Property**.</span><span class="sxs-lookup"><span data-stu-id="af81b-124">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="af81b-125">In questo modo si possono visualizzare informazioni dettagliate.</span><span class="sxs-lookup"><span data-stu-id="af81b-125">This lets you display detailed information.</span></span> <span data-ttu-id="af81b-126">Gli oggetti includono spesso più informazioni di quelle necessarie, motivo per cui per impostazione predefinita PowerShell non visualizza tutti i valori della proprietà.</span><span class="sxs-lookup"><span data-stu-id="af81b-126">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="af81b-127">Per visualizzare tutte le proprietà di un oggetto, usare il comando `Format-List -Property *`.</span><span class="sxs-lookup"><span data-stu-id="af81b-127">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="af81b-128">Il comando seguente genera oltre 60 righe di output per un unico processo:</span><span class="sxs-lookup"><span data-stu-id="af81b-128">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="af81b-129">Anche se il comando `Format-List` è utile per la visualizzazione dei dettagli, se si vuole una panoramica dell'output che includa molti elementi, è spesso più utile una visualizzazione semplificata in formato tabulare.</span><span class="sxs-lookup"><span data-stu-id="af81b-129">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="af81b-130">Uso di Format-Table per output in formato tabulare</span><span class="sxs-lookup"><span data-stu-id="af81b-130">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="af81b-131">Se si usa il cmdlet `Format-Table` senza nomi di proprietà specificati per formattare l'output del comando `Get-Process`, si ottiene esattamente lo stesso output di quando non si usa un cmdlet `Format`.</span><span class="sxs-lookup"><span data-stu-id="af81b-131">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="af81b-132">Per impostazione predefinita, PowerShell visualizza gli oggetti **Process** in un formato tabulare.</span><span class="sxs-lookup"><span data-stu-id="af81b-132">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="af81b-133">Ottimizzazione dell'output di Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="af81b-133">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="af81b-134">Una visualizzazione tabulare è utile per visualizzare molte informazioni, ma potrebbe essere di difficile interpretazione se la schermata è troppo ristretta per contenere i dati.</span><span class="sxs-lookup"><span data-stu-id="af81b-134">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="af81b-135">Nell'esempio precedente l'output è troncato.</span><span class="sxs-lookup"><span data-stu-id="af81b-135">In the previous example, the output is truncated.</span></span> <span data-ttu-id="af81b-136">Se si specifica il parametro **AutoSize** quando si esegue il comando `Format-Table`, PowerShell calcola la larghezza delle colonne in base ai dati effettivi da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="af81b-136">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="af81b-137">In questo modo le colonne risultano leggibili.</span><span class="sxs-lookup"><span data-stu-id="af81b-137">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="af81b-138">Il cmdlet `Format-Table` potrebbe comunque troncare i dati, ma solo alla fine della schermata.</span><span class="sxs-lookup"><span data-stu-id="af81b-138">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="af81b-139">Per tutte le proprietà, fatta eccezione per l'ultima visualizzata, viene assegnato tutto lo spazio richiesto per la corretta visualizzazione degli elementi di dati più lunghi.</span><span class="sxs-lookup"><span data-stu-id="af81b-139">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="af81b-140">Il comando `Format-Table` presuppone che le proprietà siano elencate in ordine di importanza.</span><span class="sxs-lookup"><span data-stu-id="af81b-140">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="af81b-141">Per questo motivo, tenta di visualizzare interamente le proprietà in prossimità dell'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="af81b-141">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="af81b-142">Se il comando `Format-Table` non visualizza tutte le proprietà, rimuove alcune colonne dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="af81b-142">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="af81b-143">Questo comportamento è illustrato nell'esempio precedente della proprietà **DependentServices**.</span><span class="sxs-lookup"><span data-stu-id="af81b-143">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="af81b-144">Ritorno a capo automatico dell'output di Format-Table nelle colonne (Wrap)</span><span class="sxs-lookup"><span data-stu-id="af81b-144">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="af81b-145">È possibile forzare il ritorno a capo automatico dei dati più lunghi di `Format-Table` nella rispettiva colonna visualizzata usando il parametro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="af81b-145">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="af81b-146">È possibile che con il parametro**Wrap** non si ottengano i risultati previsti, dal momento che il parametro usa le impostazioni predefinite se non è specificato anche **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="af81b-146">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="af81b-147">L'uso del solo parametro **Wrap** non rallenta molto l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="af81b-147">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="af81b-148">L'uso di **AutoSize** per formattare un elenco di file ricorsivi di una struttura di directory di grandi dimensioni potrebbe tuttavia richiedere molto tempo e usare una grande quantità di memoria prima di visualizzare i primi elementi dell'output.</span><span class="sxs-lookup"><span data-stu-id="af81b-148">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="af81b-149">Se non si teme il carico del sistema, **AutoSize** produce buoni risultati con il parametro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="af81b-149">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="af81b-150">Le colonne iniziali usano la larghezza necessaria per visualizzare gli elementi in una sola riga, ma se è necessario viene applicato il ritorno a capo automatico nell'ultima colonna.</span><span class="sxs-lookup"><span data-stu-id="af81b-150">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="af81b-151">Alcune colonne potrebbero non essere visualizzate quando si specificano per prime le colonne più larghe.</span><span class="sxs-lookup"><span data-stu-id="af81b-151">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="af81b-152">Per ottenere risultati ottimali, specificare prima gli elementi di dati più piccoli.</span><span class="sxs-lookup"><span data-stu-id="af81b-152">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="af81b-153">Nell'esempio seguente vengono specificate prima le proprietà più larghe.</span><span class="sxs-lookup"><span data-stu-id="af81b-153">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="af81b-154">Nonostante il ritorno a capo automatico, l'ultima colonna **Id** viene omessa:</span><span class="sxs-lookup"><span data-stu-id="af81b-154">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="af81b-155">Organizzazione dell'output di tabella (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="af81b-155">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="af81b-156">Un altro parametro utile per il controllo dell'output in formato tabulare è **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="af81b-156">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="af81b-157">Specialmente gli elenchi in formato tabulare più lunghi possono essere difficili da confrontare.</span><span class="sxs-lookup"><span data-stu-id="af81b-157">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="af81b-158">Il parametro **GroupBy** raggruppa l'output in base al valore di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="af81b-158">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="af81b-159">È ad esempio possibile raggruppare i servizi per **StartType** per un'analisi più semplice, omettendo il valore **StartType** nell'elenco delle proprietà:</span><span class="sxs-lookup"><span data-stu-id="af81b-159">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
