---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Rimozione di oggetti dalla pipeline Where Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: 4140c4c3ebb26223d03ca139992fedf6e184a38b
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="removing-objects-from-the-pipeline-where-object"></a><span data-ttu-id="b7f35-103">Rimozione di oggetti dalla pipeline (Where-Object)</span><span class="sxs-lookup"><span data-stu-id="b7f35-103">Removing Objects from the Pipeline (Where-Object)</span></span>
<span data-ttu-id="b7f35-104">In Windows PowerShell spesso si generano e si passano più oggetti a una pipeline di quelli desiderati.</span><span class="sxs-lookup"><span data-stu-id="b7f35-104">In Windows PowerShell, you often generate and pass along more objects to a pipeline than you want.</span></span> <span data-ttu-id="b7f35-105">È possibile specificare le proprietà di oggetti specifici da visualizzare usando i cmdlet **Format**, ma questo non consente di risolvere il problema della rimozione di interi oggetti dalla visualizzazione.</span><span class="sxs-lookup"><span data-stu-id="b7f35-105">You can specify the properties of particular objects to display by using the **Format** cmdlets, but this does not help with the problem of removing entire objects from the display.</span></span> <span data-ttu-id="b7f35-106">Si consiglia di filtrare gli oggetti prima della fine di una pipeline, in modo da eseguire operazioni solo su un sottoinsieme degli oggetti generati inizialmente.</span><span class="sxs-lookup"><span data-stu-id="b7f35-106">You may want to filter objects before the end of a pipeline, so you can perform actions on only a subset of the initially-generated objects.</span></span>

<span data-ttu-id="b7f35-107">Windows PowerShell include un cmdlet **Where-Object** che consente di testare ogni oggetto nella pipeline e passarlo lungo la pipeline solo se soddisfa una specifica condizione di test.</span><span class="sxs-lookup"><span data-stu-id="b7f35-107">Windows PowerShell includes a **Where-Object** cmdlet that allows you to test each object in the pipeline and only pass it along the pipeline if it meets a particular test condition.</span></span> <span data-ttu-id="b7f35-108">Gli oggetti che non superano il test vengono rimossi dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="b7f35-108">Objects that do not pass the test are removed from the pipeline.</span></span> <span data-ttu-id="b7f35-109">La condizione di test viene specificata sotto forma di valore del parametro **Where-ObjectFilterScript**.</span><span class="sxs-lookup"><span data-stu-id="b7f35-109">You supply the test condition as the value of the **Where-ObjectFilterScript** parameter.</span></span>

### <a name="performing-simple-tests-with-where-object"></a><span data-ttu-id="b7f35-110">Esecuzione di test semplici con Where-Object</span><span class="sxs-lookup"><span data-stu-id="b7f35-110">Performing Simple Tests with Where-Object</span></span>
<span data-ttu-id="b7f35-111">Il valore di **FilterScript** è un *blocco di script*, uno o più comandi di Windows PowerShell racchiusi tra parentesi graffe ({}), che restituisce true o false.</span><span class="sxs-lookup"><span data-stu-id="b7f35-111">The value of **FilterScript** is a *script block* -  one or more Windows PowerShell commands surrounded by braces {} - that evaluates to true or false.</span></span> <span data-ttu-id="b7f35-112">Questi blocchi di script possono essere molto semplici, ma per la loro creazione è richiesta familiarità con un altro concetto di Windows PowerShell, gli operatori di confronto.</span><span class="sxs-lookup"><span data-stu-id="b7f35-112">These script blocks can be very simple, but creating them requires knowing about another Windows PowerShell concept, comparison operators.</span></span> <span data-ttu-id="b7f35-113">Un operatore di confronto mette a confronto gli elementi visualizzati alle sue due estremità.</span><span class="sxs-lookup"><span data-stu-id="b7f35-113">A comparison operator compares the items that appear on each side of it.</span></span> <span data-ttu-id="b7f35-114">Gli operatori di confronto iniziano con un carattere "-" e sono seguiti da un nome.</span><span class="sxs-lookup"><span data-stu-id="b7f35-114">Comparison operators begin with a '-' character and are followed by a name.</span></span> <span data-ttu-id="b7f35-115">Gli operatori di confronto di base possono essere usati con qualsiasi tipo di oggetto.</span><span class="sxs-lookup"><span data-stu-id="b7f35-115">Basic comparison operators work on almost any kind of object.</span></span> <span data-ttu-id="b7f35-116">Quelli più avanzati potrebbero funzionare solo su testo o array.</span><span class="sxs-lookup"><span data-stu-id="b7f35-116">The more advanced comparison operators might only work on text or arrays.</span></span>

> [!NOTE]
> <span data-ttu-id="b7f35-117">Per impostazione predefinita, quando si lavora sul testo, gli operatori di confronto di Windows PowerShell non fanno distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="b7f35-117">By default, when working with text, Windows PowerShell comparison operators are case-insensitive.</span></span>

<span data-ttu-id="b7f35-118">In base a considerazioni a livello di analisi, i simboli come <, > e = non sono usati come operatori di confronto.</span><span class="sxs-lookup"><span data-stu-id="b7f35-118">Due to parsing considerations, symbols such as <,>, and = are not used as comparison operators.</span></span> <span data-ttu-id="b7f35-119">Al contrario, gli operatori di confronto possono essere costituiti da lettere.</span><span class="sxs-lookup"><span data-stu-id="b7f35-119">Instead, comparison operators are comprised of letters.</span></span> <span data-ttu-id="b7f35-120">Nella tabella seguente sono elencati gli operatori di confronto di base.</span><span class="sxs-lookup"><span data-stu-id="b7f35-120">The basic comparison operators are listed in the following table.</span></span>

|<span data-ttu-id="b7f35-121">Operatore di confronto</span><span class="sxs-lookup"><span data-stu-id="b7f35-121">Comparison Operator</span></span>|<span data-ttu-id="b7f35-122">Significato</span><span class="sxs-lookup"><span data-stu-id="b7f35-122">Meaning</span></span>|<span data-ttu-id="b7f35-123">Esempio (restituisce true)</span><span class="sxs-lookup"><span data-stu-id="b7f35-123">Example (returns true)</span></span>|
|-----------------------|-----------|--------------------------|
|<span data-ttu-id="b7f35-124">-eq</span><span class="sxs-lookup"><span data-stu-id="b7f35-124">-eq</span></span>|<span data-ttu-id="b7f35-125">È uguale a</span><span class="sxs-lookup"><span data-stu-id="b7f35-125">is equal to</span></span>|<span data-ttu-id="b7f35-126">1 -eq 1</span><span class="sxs-lookup"><span data-stu-id="b7f35-126">1 -eq 1</span></span>|
|<span data-ttu-id="b7f35-127">-ne</span><span class="sxs-lookup"><span data-stu-id="b7f35-127">-ne</span></span>|<span data-ttu-id="b7f35-128">Non è uguale a</span><span class="sxs-lookup"><span data-stu-id="b7f35-128">Is not equal to</span></span>|<span data-ttu-id="b7f35-129">1 -ne 2</span><span class="sxs-lookup"><span data-stu-id="b7f35-129">1 -ne 2</span></span>|
|<span data-ttu-id="b7f35-130">-lt</span><span class="sxs-lookup"><span data-stu-id="b7f35-130">-lt</span></span>|<span data-ttu-id="b7f35-131">È minore di</span><span class="sxs-lookup"><span data-stu-id="b7f35-131">Is less than</span></span>|<span data-ttu-id="b7f35-132">1 -lt 2</span><span class="sxs-lookup"><span data-stu-id="b7f35-132">1 -lt 2</span></span>|
|<span data-ttu-id="b7f35-133">-le</span><span class="sxs-lookup"><span data-stu-id="b7f35-133">-le</span></span>|<span data-ttu-id="b7f35-134">È minore o uguale a</span><span class="sxs-lookup"><span data-stu-id="b7f35-134">Is less than or equal to</span></span>|<span data-ttu-id="b7f35-135">1 -le 2</span><span class="sxs-lookup"><span data-stu-id="b7f35-135">1 -le 2</span></span>|
|<span data-ttu-id="b7f35-136">-gt</span><span class="sxs-lookup"><span data-stu-id="b7f35-136">-gt</span></span>|<span data-ttu-id="b7f35-137">È maggiore di</span><span class="sxs-lookup"><span data-stu-id="b7f35-137">Is greater than</span></span>|<span data-ttu-id="b7f35-138">2 -gt 1</span><span class="sxs-lookup"><span data-stu-id="b7f35-138">2 -gt 1</span></span>|
|<span data-ttu-id="b7f35-139">-ge</span><span class="sxs-lookup"><span data-stu-id="b7f35-139">-ge</span></span>|<span data-ttu-id="b7f35-140">È maggiore o uguale a</span><span class="sxs-lookup"><span data-stu-id="b7f35-140">Is greater than or equal to</span></span>|<span data-ttu-id="b7f35-141">2 -ge 1</span><span class="sxs-lookup"><span data-stu-id="b7f35-141">2 -ge 1</span></span>|
|<span data-ttu-id="b7f35-142">-like</span><span class="sxs-lookup"><span data-stu-id="b7f35-142">-like</span></span>|<span data-ttu-id="b7f35-143">Corrisponde (confronto con caratteri jolly per il testo)</span><span class="sxs-lookup"><span data-stu-id="b7f35-143">Is like (wildcard comparison for text)</span></span>|<span data-ttu-id="b7f35-144">"file.doc" -like "f\*.do?"</span><span class="sxs-lookup"><span data-stu-id="b7f35-144">"file.doc" -like "f\*.do?"</span></span>|
|<span data-ttu-id="b7f35-145">-notlike</span><span class="sxs-lookup"><span data-stu-id="b7f35-145">-notlike</span></span>|<span data-ttu-id="b7f35-146">Non corrisponde (confronto con caratteri jolly per il testo)</span><span class="sxs-lookup"><span data-stu-id="b7f35-146">Is not like (wildcard comparison for text)</span></span>|<span data-ttu-id="b7f35-147">"file.doc" -notlike "p\*.doc"</span><span class="sxs-lookup"><span data-stu-id="b7f35-147">"file.doc" -notlike "p\*.doc"</span></span>|
|<span data-ttu-id="b7f35-148">-contains</span><span class="sxs-lookup"><span data-stu-id="b7f35-148">-contains</span></span>|<span data-ttu-id="b7f35-149">Contiene</span><span class="sxs-lookup"><span data-stu-id="b7f35-149">Contains</span></span>|<span data-ttu-id="b7f35-150">1,2,3 -contains 1</span><span class="sxs-lookup"><span data-stu-id="b7f35-150">1,2,3 -contains 1</span></span>|
|<span data-ttu-id="b7f35-151">-notcontains</span><span class="sxs-lookup"><span data-stu-id="b7f35-151">-notcontains</span></span>|<span data-ttu-id="b7f35-152">Non contiene</span><span class="sxs-lookup"><span data-stu-id="b7f35-152">Does not contain</span></span>|<span data-ttu-id="b7f35-153">1,2,3 -notcontains 4</span><span class="sxs-lookup"><span data-stu-id="b7f35-153">1,2,3 -notcontains 4</span></span>|

<span data-ttu-id="b7f35-154">I blocchi di script di Where-Object usano la variabile speciale "$_" per fare riferimento all'oggetto corrente nella pipeline.</span><span class="sxs-lookup"><span data-stu-id="b7f35-154">Where-Object script blocks use the special variable '$_' to refer to the current object in the pipeline.</span></span> <span data-ttu-id="b7f35-155">Di seguito è riportato un esempio del funzionamento.</span><span class="sxs-lookup"><span data-stu-id="b7f35-155">Here is an example of how it works.</span></span> <span data-ttu-id="b7f35-156">Se si ha un elenco di numeri e si vogliono restituire solo quelli minori di 3, è possibile usare Where-Object per filtrare i numeri digitando:</span><span class="sxs-lookup"><span data-stu-id="b7f35-156">If you have a list of numbers, and only want to return the ones that are less than 3, you can use Where-Object to filter the numbers by typing:</span></span>

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a><span data-ttu-id="b7f35-157">Filtro in base alle proprietà dell'oggetto</span><span class="sxs-lookup"><span data-stu-id="b7f35-157">Filtering Based on Object Properties</span></span>
<span data-ttu-id="b7f35-158">Dal momento che $_ fa riferimento all'oggetto della pipeline corrente, è possibile accedere alle relative proprietà per i test.</span><span class="sxs-lookup"><span data-stu-id="b7f35-158">Since $_ refers to the current pipeline object, we can access its properties for our tests.</span></span>

<span data-ttu-id="b7f35-159">È ad esempio possibile esaminare la classe Win32_SystemDriver in Strumentazione gestione Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="b7f35-159">As an example, we can look at the Win32_SystemDriver class in WMI.</span></span> <span data-ttu-id="b7f35-160">Potrebbero esserci centinaia di driver di sistema in un determinato sistema, ma solo uno specifico set di driver di sistema potrebbe essere interessante, ad esempio quello dei driver attualmente in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b7f35-160">There might be hundreds of system drivers on a particular system, but you might only be interested in a particular set of the system drivers, such as those which are currently running.</span></span> <span data-ttu-id="b7f35-161">Se si usa Get-Member per visualizzare i membri di Win32_SystemDriver (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**), si noterà che la proprietà pertinente è State e che ha il valore "Running" quando il driver è in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b7f35-161">If you use Get-Member to view Win32_SystemDriver members (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**) you will see that the relevant property is State, and that it has a value of "Running" when the driver is running.</span></span> <span data-ttu-id="b7f35-162">È possibile filtrare i driver di sistema selezionando solo quelli in esecuzione digitando:</span><span class="sxs-lookup"><span data-stu-id="b7f35-162">You can filter the system drivers, selecting only the running ones by typing:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"}
```

<span data-ttu-id="b7f35-163">Questa operazione genera comunque un lungo elenco.</span><span class="sxs-lookup"><span data-stu-id="b7f35-163">This still produces a long list.</span></span> <span data-ttu-id="b7f35-164">Si consiglia di applicare un filtro per selezionare solo i driver impostati per l'avvio automatico testando anche il valore StartMode:</span><span class="sxs-lookup"><span data-stu-id="b7f35-164">You may want to filter to only select the drivers set to start automatically by testing the StartMode value as well:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

<span data-ttu-id="b7f35-165">Questa operazione produce numerose informazioni che non sono più necessarie poiché è noto che i driver sono in esecuzione.</span><span class="sxs-lookup"><span data-stu-id="b7f35-165">This gives us a lot of information we no longer need because we know that the drivers are running.</span></span> <span data-ttu-id="b7f35-166">In effetti, le uniche informazioni che a questo punto risultano probabilmente necessarie sono il nome e il nome visualizzato.</span><span class="sxs-lookup"><span data-stu-id="b7f35-166">In fact, the only information we probably need at this point are the name and the display name.</span></span> <span data-ttu-id="b7f35-167">Il comando seguente include solo queste due proprietà, generando un output molto più semplice:</span><span class="sxs-lookup"><span data-stu-id="b7f35-167">The following command includes only those two properties, resulting in much simpler output:</span></span>

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

<span data-ttu-id="b7f35-168">Sono presenti due elementi Where-Object nel comando precedente, ma possono essere espressi con un unico elemento Where-Object usando l'operatore logico -and, come nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="b7f35-168">There are two Where-Object elements in the above command, but they can be expressed in a single Where-Object element by using the -and logical operator, like this:</span></span>

```
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq "Running") -and ($_.StartMode -eq "Manual") } | Format-Table -Property Name,DisplayName
```

<span data-ttu-id="b7f35-169">Nella tabella seguente sono elencati gli operatori logici standard.</span><span class="sxs-lookup"><span data-stu-id="b7f35-169">The standard logical operators are listed in the following table.</span></span>

|<span data-ttu-id="b7f35-170">Operatore logico</span><span class="sxs-lookup"><span data-stu-id="b7f35-170">Logical Operator</span></span>|<span data-ttu-id="b7f35-171">Significato</span><span class="sxs-lookup"><span data-stu-id="b7f35-171">Meaning</span></span>|<span data-ttu-id="b7f35-172">Esempio (restituisce true)</span><span class="sxs-lookup"><span data-stu-id="b7f35-172">Example (returns true)</span></span>|
|--------------------|-----------|--------------------------|
|<span data-ttu-id="b7f35-173">-and</span><span class="sxs-lookup"><span data-stu-id="b7f35-173">-and</span></span>|<span data-ttu-id="b7f35-174">AND logico; true se i valori a entrambe le estremità sono true</span><span class="sxs-lookup"><span data-stu-id="b7f35-174">Logical and; true if both sides are true</span></span>|<span data-ttu-id="b7f35-175">(1 -eq 1) -and (2 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="b7f35-175">(1 -eq 1) -and (2 -eq 2)</span></span>|
|<span data-ttu-id="b7f35-176">-or</span><span class="sxs-lookup"><span data-stu-id="b7f35-176">-or</span></span>|<span data-ttu-id="b7f35-177">OR logico; true se i valori a entrambe le estremità sono true</span><span class="sxs-lookup"><span data-stu-id="b7f35-177">Logical or; true if either side is true</span></span>|<span data-ttu-id="b7f35-178">(1 -eq 1) -or (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="b7f35-178">(1 -eq 1) -or (1 -eq 2)</span></span>|
|<span data-ttu-id="b7f35-179">-not</span><span class="sxs-lookup"><span data-stu-id="b7f35-179">-not</span></span>|<span data-ttu-id="b7f35-180">NOT logico; inverte true e false</span><span class="sxs-lookup"><span data-stu-id="b7f35-180">Logical not; reverses true and false</span></span>|<span data-ttu-id="b7f35-181">-not (1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="b7f35-181">-not (1 -eq 2)</span></span>|
|\!|<span data-ttu-id="b7f35-182">NOT logico; inverte true e false</span><span class="sxs-lookup"><span data-stu-id="b7f35-182">Logical not; reverses true and false</span></span>|<span data-ttu-id="b7f35-183">\!(1 -eq 2)</span><span class="sxs-lookup"><span data-stu-id="b7f35-183">\!(1 -eq 2)</span></span>|
