---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso dei comandi Format per modificare la visualizzazione dell'output
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 35ccd2525d40ffd5e3f25a1abfa38904a109bde5
ms.sourcegitcommit: 396509cd0d415acc306b68758b6f833406e26bf5
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2019
ms.locfileid: "58320422"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="43f57-103">Uso dei comandi Format per modificare la visualizzazione dell'output</span><span class="sxs-lookup"><span data-stu-id="43f57-103">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="43f57-104">Windows PowerShell include un set di cmdlet che consentono di controllare le proprietà visualizzate per oggetti specifici.</span><span class="sxs-lookup"><span data-stu-id="43f57-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="43f57-105">I nomi di tutti i cmdlet iniziano con il verbo **Format**.</span><span class="sxs-lookup"><span data-stu-id="43f57-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="43f57-106">Consentono di selezionare una o più proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="43f57-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="43f57-107">I cmdlet **Format** sono **Format-Wide**, **Format-List**, **Format-Table** e **Format-Custom**.</span><span class="sxs-lookup"><span data-stu-id="43f57-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="43f57-108">Questo Manuale dell'utente illustra solo i cmdlet **Format-Wide**, **Format-List** e **Format-Table**.</span><span class="sxs-lookup"><span data-stu-id="43f57-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="43f57-109">Ogni cmdlet Format ha proprietà predefinite che verranno usate se non si specificano proprietà specifiche da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="43f57-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="43f57-110">Tutti i cmdlet usano inoltre lo stesso nome di parametro, **Property**, per specificare le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="43f57-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="43f57-111">Dal momento che **Format-Wide** indica solo una singola proprietà, il relativo parametro **Property** accetta solo un valore, ma i parametri della proprietà di **Format-List** e **Format-Table** accetteranno un elenco di nomi di proprietà.</span><span class="sxs-lookup"><span data-stu-id="43f57-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="43f57-112">Se si usa il comando **Get-Process -Name powershell** con due istanze di Windows PowerShell in esecuzione, si otterrà un output simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="43f57-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```output
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="43f57-113">Nel resto di questa sezione verrà illustrato come usare i cmdlet **Format** per modificare il modo in cui viene visualizzato l'output di questo comando.</span><span class="sxs-lookup"><span data-stu-id="43f57-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="43f57-114">Uso di Format-Wide per output a elemento singolo</span><span class="sxs-lookup"><span data-stu-id="43f57-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="43f57-115">Per impostazione predefinita, il cmdlet **Format-Wide** visualizza solo la proprietà predefinita di un oggetto.</span><span class="sxs-lookup"><span data-stu-id="43f57-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="43f57-116">Le informazioni associate a ogni oggetto sono visualizzate in una singola colonna:</span><span class="sxs-lookup"><span data-stu-id="43f57-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="43f57-117">È inoltre possibile specificare una proprietà non predefinita:</span><span class="sxs-lookup"><span data-stu-id="43f57-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="43f57-118">Controllo della visualizzazione di Format-Wide con il parametro Column</span><span class="sxs-lookup"><span data-stu-id="43f57-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="43f57-119">Con il cmdlet `Format-Wide` è possibile visualizzare unicamente una sola proprietà alla volta.</span><span class="sxs-lookup"><span data-stu-id="43f57-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span>
<span data-ttu-id="43f57-120">Questa funzionalità risulta utile per la visualizzazione di elenchi semplici che mostrano un solo elemento per riga.</span><span class="sxs-lookup"><span data-stu-id="43f57-120">This makes it useful for displaying simple lists that show only one element per line.</span></span>
<span data-ttu-id="43f57-121">Per ottenere un elenco semplice, impostare il valore del parametro **Column** su 1 digitando:</span><span class="sxs-lookup"><span data-stu-id="43f57-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 1
```

```output
Custom
Hex
List
Table
Wide
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="43f57-122">Uso di Format-List per una visualizzazione elenco</span><span class="sxs-lookup"><span data-stu-id="43f57-122">Using Format-List for a List View</span></span>

<span data-ttu-id="43f57-123">Il cmdlet **Format-List** visualizza un oggetto sotto forma di elenco, con ogni proprietà denominata e visualizzata in una riga distinta:</span><span class="sxs-lookup"><span data-stu-id="43f57-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="43f57-124">È possibile specificare il numero di proprietà che si vuole:</span><span class="sxs-lookup"><span data-stu-id="43f57-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="43f57-125">Ottenere informazioni dettagliate usando Format-List con i caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="43f57-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="43f57-126">Il cmdlet **Format-List** consente di usare un carattere jolly come valore del relativo parametro **Property**.</span><span class="sxs-lookup"><span data-stu-id="43f57-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="43f57-127">In questo modo si possono visualizzare informazioni dettagliate.</span><span class="sxs-lookup"><span data-stu-id="43f57-127">This lets you display detailed information.</span></span> <span data-ttu-id="43f57-128">Gli oggetti includono spesso più informazioni di quelle richieste, motivo per cui per impostazione predefinita Windows PowerShell non mostra tutti i valori della proprietà.</span><span class="sxs-lookup"><span data-stu-id="43f57-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="43f57-129">Per visualizzare tutte le proprietà di un oggetto, usare il comando **Format-List -Property \&#42;**.</span><span class="sxs-lookup"><span data-stu-id="43f57-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="43f57-130">Il comando seguente genera oltre 60 righe di output per un unico processo:</span><span class="sxs-lookup"><span data-stu-id="43f57-130">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="43f57-131">Anche se il comando **Format-List** è utile per la visualizzazione dei dettagli, se si vuole una panoramica dell'output che includa molti elementi, spesso una visualizzazione semplificata in formato tabulare è più utile.</span><span class="sxs-lookup"><span data-stu-id="43f57-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="43f57-132">Uso di Format-Table per output in formato tabulare</span><span class="sxs-lookup"><span data-stu-id="43f57-132">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="43f57-133">Se si usa il cmdlet **Format-Table** senza nomi di proprietà specificati per formattare l'output del comando **Get-Process**, si ottiene esattamente lo stesso output di quando non si esegue alcuna formattazione.</span><span class="sxs-lookup"><span data-stu-id="43f57-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="43f57-134">Il motivo è che i processi sono in genere visualizzati in formato tabulare, come quasi tutti gli oggetti di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="43f57-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="43f57-135">Ottimizzazione dell'output di Format-Table (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="43f57-135">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="43f57-136">Anche se una visualizzazione tabulare è utile per mostrare molte informazioni da mettere a confronto, potrebbe essere difficile interpretarle se lo schermo è troppo ridotto rispetto ai dati.</span><span class="sxs-lookup"><span data-stu-id="43f57-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="43f57-137">Se ad esempio si prova a visualizzare il percorso, l'ID, il nome e la società di un processo, si otterrà un output troncato per la colonna della società e del percorso del processo:</span><span class="sxs-lookup"><span data-stu-id="43f57-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="43f57-138">Se si specifica il parametro **AutoSize** quando si esegue il comando **Format-Table**, Windows PowerShell calcolerà la larghezza delle colonne in base ai dati effettivi da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="43f57-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="43f57-139">In questo modo la colonna **Path** risulta leggibile, ma la colonna della società rimane troncata:</span><span class="sxs-lookup"><span data-stu-id="43f57-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="43f57-140">Il cmdlet **Format-Table** potrebbe comunque troncare i dati, ma solo alla fine della schermata.</span><span class="sxs-lookup"><span data-stu-id="43f57-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="43f57-141">Per tutte le proprietà, fatta eccezione per l'ultima visualizzata, viene assegnato tutto lo spazio richiesto per la corretta visualizzazione degli elementi di dati più lunghi.</span><span class="sxs-lookup"><span data-stu-id="43f57-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="43f57-142">Si può notare che il nome della società è visibile ma il percorso risulta troncato se si invertono le posizioni di **Path** e **Company** nell'elenco dei valori di **Property**:</span><span class="sxs-lookup"><span data-stu-id="43f57-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="43f57-143">Il comando **Format-Table** presuppone che quanto più una proprietà sia vicina all'inizio dell'elenco dei valori, tanto più sia importante.</span><span class="sxs-lookup"><span data-stu-id="43f57-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="43f57-144">Per questo motivo, tenta di visualizzare interamente le proprietà più vicino all'inizio dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="43f57-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="43f57-145">Se il comando **Format-Table** non è in grado di visualizzare tutte le proprietà, alcune colonne saranno rimosse dalla visualizzazione e apparirà un avviso.</span><span class="sxs-lookup"><span data-stu-id="43f57-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="43f57-146">È possibile osservare questo comportamento specificando **Name** come ultima proprietà dell'elenco:</span><span class="sxs-lookup"><span data-stu-id="43f57-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="43f57-147">Nell'output precedente la colonna ID viene troncata per essere adattata alle dimensioni dell'elenco e le intestazioni di colonna sono impilate.</span><span class="sxs-lookup"><span data-stu-id="43f57-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="43f57-148">Il ridimensionamento automatico delle colonne non comporta sempre i risultati sperati.</span><span class="sxs-lookup"><span data-stu-id="43f57-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="43f57-149">Ritorno a capo automatico dell'output di Format-Table nelle colonne (Wrap)</span><span class="sxs-lookup"><span data-stu-id="43f57-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="43f57-150">È possibile forzare il ritorno a capo automatico dei dati più lunghi di **Format-Table** nella relative colonne visualizzate usando il parametro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="43f57-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="43f57-151">Con il solo parametro **Wrap**, tuttavia, l'operazione non produrrà necessariamente i risultati previsti, dal momento che verranno usate le impostazioni predefinite se non si specifica anche **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="43f57-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="43f57-152">Un vantaggio dell'uso del solo parametro **Wrap** è che non rallenta molto l'elaborazione.</span><span class="sxs-lookup"><span data-stu-id="43f57-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="43f57-153">Se si esegue un elenco di file ricorsivo di un sistema di directory di grandi dimensioni, potrebbe richiedere molto tempo e usare una grande quantità di memoria prima di visualizzare i primi elementi dell'output se si usa **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="43f57-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="43f57-154">Se si non teme il carico del sistema, **AutoSize** produce buoni risultati con il parametro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="43f57-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="43f57-155">Alle colonne iniziali è sempre assegnato lo spazio necessario per visualizzare gli elementi su una riga, proprio come quando si specifica **AutoSize** senza il parametro **Wrap**.</span><span class="sxs-lookup"><span data-stu-id="43f57-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="43f57-156">L'unica differenza è che la colonna finale verrà mandata a capo se necessario:</span><span class="sxs-lookup"><span data-stu-id="43f57-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="43f57-157">Alcune colonne potrebbero non essere visualizzate se si specificano per prime le colonne più larghe, pertanto è consigliabile specificare per primi gli elementi di dati più piccoli.</span><span class="sxs-lookup"><span data-stu-id="43f57-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="43f57-158">Nell'esempio seguente viene specificato per primo l'elemento del percorso estremamente lungo, ma anche con il ritorno a capo automatico la colonna finale **Name** viene persa:</span><span class="sxs-lookup"><span data-stu-id="43f57-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="43f57-159">Organizzazione dell'output di tabella (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="43f57-159">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="43f57-160">Un altro parametro utile per il controllo dell'output in formato tabulare è **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="43f57-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="43f57-161">Specialmente gli elenchi in formato tabulare più lunghi possono essere difficili da confrontare.</span><span class="sxs-lookup"><span data-stu-id="43f57-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="43f57-162">Il parametro **GroupBy** raggruppa l'output in base al valore di una proprietà.</span><span class="sxs-lookup"><span data-stu-id="43f57-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="43f57-163">È ad esempio possibile raggruppare i processi per società per un controllo più semplice, omettendo il valore della società nell'elenco delle proprietà:</span><span class="sxs-lookup"><span data-stu-id="43f57-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```