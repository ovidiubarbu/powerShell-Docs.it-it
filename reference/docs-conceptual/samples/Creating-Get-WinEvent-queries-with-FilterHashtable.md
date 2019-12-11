---
ms.date: 09/13/2019
title: Creazione di query Get-WinEvent con FilterHashtable
ms.openlocfilehash: 35d18dc894d90e698b38395b79ff4cf395515909
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444387"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="5ffe5-102">Creazione di query Get-WinEvent con FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="5ffe5-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="5ffe5-103">Per leggere il post del blog **Scripting Guy** originale del 3 giugno 2014, vedere [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Usare FilterHashTable per filtrare il registro eventi con PowerShell).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="5ffe5-104">Questo articolo è un estratto del post di blog originale e spiega come usare il parametro **FilterHashtable** del cmdlet `Get-WinEvent` per filtrare i registri eventi.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="5ffe5-105">Il cmdlet `Get-WinEvent` di PowerShell è un metodo efficace per filtrare i registri eventi e i log di diagnostica di Windows.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="5ffe5-106">Le prestazioni migliorano quando una query `Get-WinEvent` usa il parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="5ffe5-107">Quando si lavora con registri eventi di grandi dimensioni, non è efficace inviare gli oggetti nella pipeline a un comando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="5ffe5-108">Prima di PowerShell 6, il cmdlet `Get-EventLog` rappresentava un'altra opzione per ottenere i dati di log.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="5ffe5-109">Ad esempio, i comandi seguenti non sono efficienti per filtrare i log **Microsoft-Windows-Defrag**:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

```powershell
Get-EventLog -LogName Application | Where-Object Source -Match defrag

Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }
```

<span data-ttu-id="5ffe5-110">Il comando seguente usa una tabella hash che migliora le prestazioni:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="5ffe5-111">Post di blog sull'enumerazione</span><span class="sxs-lookup"><span data-stu-id="5ffe5-111">Blog posts about enumeration</span></span>

<span data-ttu-id="5ffe5-112">Questo articolo presenta informazioni su come usare i valori enumerati in una tabella hash.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="5ffe5-113">Per altre informazioni sull'enumerazione, leggere questi post del blog **Scripting Guy**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="5ffe5-114">Per creare una funzione che restituisce i valori enumerati, vedere [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumerazioni e valori).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="5ffe5-115">Per altre informazioni, vedere la [serie di post del blog Scripting Guy sull'enumerazione](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-key-value-pairs"></a><span data-ttu-id="5ffe5-116">Coppie chiave-valore della tabella hash</span><span class="sxs-lookup"><span data-stu-id="5ffe5-116">Hash table key-value pairs</span></span>

<span data-ttu-id="5ffe5-117">Per creare query efficienti, usare il cmdlet `Get-WinEvent` con il parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="5ffe5-118">**FilterHashtable** accetta una tabella hash come filtro per ottenere informazioni specifiche dai registri eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="5ffe5-119">Una tabella hash usa coppie **chiave-valore**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-119">A hash table uses **key-value** pairs.</span></span> <span data-ttu-id="5ffe5-120">Per altre informazioni sulle tabelle hash, vedere [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="5ffe5-121">Se le coppie **chiave-valore** sono sulla stessa riga, devono essere separate da un punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-121">If the **key-value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="5ffe5-122">Se ogni coppia **chiave-valore** è su una riga separata, il punto e virgola non è necessario.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-122">If each **key-value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="5ffe5-123">In questo articolo ad esempio le coppie **chiave-valore** sono posizionate su righe separate e non vengono usati punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-123">For example, this article places **key-value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="5ffe5-124">Questo esempio usa varie coppie **chiave-valore** del parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-124">This sample uses several of the **FilterHashtable** parameter's **key-value** pairs.</span></span> <span data-ttu-id="5ffe5-125">La query completa include **LogName**, **ProviderName**, **Keywords**, **ID** e **Level**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="5ffe5-126">Le coppie **chiave-valore** accettate sono riportate nella tabella seguente e sono incluse nella documentazione per il parametro [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-126">The accepted **key-value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="5ffe5-127">Nella tabella seguente vengono visualizzati i nomi delle chiavi, i tipi di dati e viene indicato se i caratteri jolly sono consentiti per un valore di dati.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

|    <span data-ttu-id="5ffe5-128">Nome chiave</span><span class="sxs-lookup"><span data-stu-id="5ffe5-128">Key name</span></span>    | <span data-ttu-id="5ffe5-129">Tipo di dati del valore</span><span class="sxs-lookup"><span data-stu-id="5ffe5-129">Value data type</span></span> | <span data-ttu-id="5ffe5-130">Caratteri jolly accettati?</span><span class="sxs-lookup"><span data-stu-id="5ffe5-130">Accepts wildcard characters?</span></span> |
| -------------- | --------------- | ---------------------------- |
| <span data-ttu-id="5ffe5-131">LogName</span><span class="sxs-lookup"><span data-stu-id="5ffe5-131">LogName</span></span>        | `<String[]>`    | <span data-ttu-id="5ffe5-132">Sì</span><span class="sxs-lookup"><span data-stu-id="5ffe5-132">Yes</span></span>                          |
| <span data-ttu-id="5ffe5-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="5ffe5-133">ProviderName</span></span>   | `<String[]>`    | <span data-ttu-id="5ffe5-134">Sì</span><span class="sxs-lookup"><span data-stu-id="5ffe5-134">Yes</span></span>                          |
| <span data-ttu-id="5ffe5-135">Path</span><span class="sxs-lookup"><span data-stu-id="5ffe5-135">Path</span></span>           | `<String[]>`    | <span data-ttu-id="5ffe5-136">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-136">No</span></span>                           |
| <span data-ttu-id="5ffe5-137">Parole chiave</span><span class="sxs-lookup"><span data-stu-id="5ffe5-137">Keywords</span></span>       | `<Long[]>`      | <span data-ttu-id="5ffe5-138">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-138">No</span></span>                           |
| <span data-ttu-id="5ffe5-139">ID</span><span class="sxs-lookup"><span data-stu-id="5ffe5-139">ID</span></span>             | `<Int32[]>`     | <span data-ttu-id="5ffe5-140">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-140">No</span></span>                           |
| <span data-ttu-id="5ffe5-141">Livello</span><span class="sxs-lookup"><span data-stu-id="5ffe5-141">Level</span></span>          | `<Int32[]>`     | <span data-ttu-id="5ffe5-142">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-142">No</span></span>                           |
| <span data-ttu-id="5ffe5-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="5ffe5-143">StartTime</span></span>      | `<DateTime>`    | <span data-ttu-id="5ffe5-144">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-144">No</span></span>                           |
| <span data-ttu-id="5ffe5-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="5ffe5-145">EndTime</span></span>        | `<DateTime>`    | <span data-ttu-id="5ffe5-146">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-146">No</span></span>                           |
| <span data-ttu-id="5ffe5-147">UserID</span><span class="sxs-lookup"><span data-stu-id="5ffe5-147">UserID</span></span>         | `<SID>`         | <span data-ttu-id="5ffe5-148">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-148">No</span></span>                           |
| <span data-ttu-id="5ffe5-149">Dati</span><span class="sxs-lookup"><span data-stu-id="5ffe5-149">Data</span></span>           | `<String[]>`    | <span data-ttu-id="5ffe5-150">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-150">No</span></span>                           |
| `<named-data>` | `<String[]>`    | <span data-ttu-id="5ffe5-151">No</span><span class="sxs-lookup"><span data-stu-id="5ffe5-151">No</span></span>                           |

<span data-ttu-id="5ffe5-152">La chiave `<named-data>` rappresenta un campo dati dell'evento denominato.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-152">The `<named-data>` key represents a named event data field.</span></span> <span data-ttu-id="5ffe5-153">Ad esempio, l'evento 1008 Perflib può contenere i dati dell'evento seguenti:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-153">For example, the Perflib event 1008 can contain the following event data:</span></span>

```xml
<EventData>
  <Data Name="Service">BITS</Data>
  <Data Name="Library">C:\Windows\System32\bitsperf.dll</Data>
  <Data Name="Win32Error">2</Data>
</EventData>
```

<span data-ttu-id="5ffe5-154">È possibile eseguire una query per questi eventi usando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-154">You can query for these events using the following command:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{LogName='Application'; 'Service'='Bits'}
```

> [!NOTE]
> <span data-ttu-id="5ffe5-155">In PowerShell 6 è stata aggiunta la possibilità di eseguire una query per `<named-data>`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-155">The ability to query for `<named-data>` was added in PowerShell 6.</span></span>

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="5ffe5-156">Creazione di una query con una tabella hash</span><span class="sxs-lookup"><span data-stu-id="5ffe5-156">Building a query with a hash table</span></span>

<span data-ttu-id="5ffe5-157">Per verificare i risultati e risolvere i problemi, è utile creare la tabella hash con una coppia **chiave-valore** alla volta.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-157">To verify results and troubleshoot problems, it helps to build the hash table one **key-value** pair at a time.</span></span> <span data-ttu-id="5ffe5-158">La query ottiene i dati dal log **Application**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-158">The query gets data from the **Application** log.</span></span> <span data-ttu-id="5ffe5-159">La tabella hash è equivalente a `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-159">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="5ffe5-160">Per iniziare, creare la query `Get-WinEvent`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-160">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="5ffe5-161">Usare la coppia **chiave-valore** del parametro **FilterHashtable** con la chiave **LogName** e il valore **Application**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-161">Use the **FilterHashtable** parameter's **key-value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="5ffe5-162">Continuare a comporre la tabella hash con la chiave **ProviderName**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-162">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="5ffe5-163">**ProviderName** è il nome visualizzato nel campo **Origine** nel **Visualizzatore eventi di Windows**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-163">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="5ffe5-164">Ad esempio, **.NET Runtime** nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-164">For example, **.NET Runtime** in the following screenshot:</span></span>

![Immagine delle origini di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="5ffe5-166">Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave \*\*ProviderName e il valore **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-166">Update the hash table and include the **key-value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="5ffe5-167">Se la query deve ottenere dati da registri eventi archiviati, usare la chiave **Path**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-167">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="5ffe5-168">Il valore **Path** specifica il percorso completo del file di log.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-168">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="5ffe5-169">Per altre informazioni, vedere il post del blog **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Usare PowerShell per analizzare i registri eventi salvati per individuare gli errori).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-169">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="5ffe5-170">Uso dei valori enumerati in una tabella hash</span><span class="sxs-lookup"><span data-stu-id="5ffe5-170">Using enumerated values in a hash table</span></span>

<span data-ttu-id="5ffe5-171">La chiave successiva nella tabella hash è **Keywords**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-171">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="5ffe5-172">Il tipo di dati **Keywords** è una matrice del tipo valore `[long]` che contiene un numero elevato.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-172">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="5ffe5-173">Usare il comando seguente per trovare il valore massimo di `[long]`:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-173">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="5ffe5-174">Per la chiave **Keywords** PowerShell usa un numero e non una stringa come **Security**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-174">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="5ffe5-175">**Visualizzatore eventi di Windows** visualizza i valori di **Keywords** come stringhe, ma sono valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-175">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="5ffe5-176">Nella tabella hash, se si usa la chiave **Keywords** con un valore stringa, viene visualizzato un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-176">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="5ffe5-177">Aprire il **Visualizzatore eventi di Windows** e dal riquadro **Azioni** fare clic su **Filtro registro corrente**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-177">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="5ffe5-178">Nel menu a discesa **Keywords** vengono visualizzate le parole chiave disponibili, come illustrato nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-178">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Immagine delle parole chiave di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="5ffe5-180">Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventKeywords`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-180">Use the following command to display the `StandardEventKeywords` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventKeywords] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventKeywords
Name             MemberType Definition
—-             ———- ———-
AuditFailure     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
AuditSuccess     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
CorrelationHint2 Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
EventLogClassic  Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
None             Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
ResponseTime     Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
Sqm              Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiContext       Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
WdiDiagnostic    Property   static System.Diagnostics.Eventing.Reader.StandardEventKey…
```

<span data-ttu-id="5ffe5-181">I valori enumerati sono documentati in **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-181">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="5ffe5-182">Per altre informazioni, vedere [Enumerazione StandardEventKeywords](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-182">For more information, see [StandardEventKeywords Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="5ffe5-183">I nomi e i valori enumerati per **Keywords** sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-183">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="5ffe5-184">Nome</span><span class="sxs-lookup"><span data-stu-id="5ffe5-184">Name</span></span>             |  <span data-ttu-id="5ffe5-185">Value</span><span class="sxs-lookup"><span data-stu-id="5ffe5-185">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="5ffe5-186">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="5ffe5-186">AuditFailure</span></span>     | <span data-ttu-id="5ffe5-187">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="5ffe5-187">4503599627370496</span></span>  |
| <span data-ttu-id="5ffe5-188">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="5ffe5-188">AuditSuccess</span></span>     | <span data-ttu-id="5ffe5-189">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="5ffe5-189">9007199254740992</span></span>  |
| <span data-ttu-id="5ffe5-190">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="5ffe5-190">CorrelationHint2</span></span> | <span data-ttu-id="5ffe5-191">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="5ffe5-191">18014398509481984</span></span> |
| <span data-ttu-id="5ffe5-192">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="5ffe5-192">EventLogClassic</span></span>  | <span data-ttu-id="5ffe5-193">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="5ffe5-193">36028797018963968</span></span> |
| <span data-ttu-id="5ffe5-194">Sqm</span><span class="sxs-lookup"><span data-stu-id="5ffe5-194">Sqm</span></span>              | <span data-ttu-id="5ffe5-195">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="5ffe5-195">2251799813685248</span></span>  |
| <span data-ttu-id="5ffe5-196">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="5ffe5-196">WdiDiagnostic</span></span>    | <span data-ttu-id="5ffe5-197">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="5ffe5-197">1125899906842624</span></span>  |
| <span data-ttu-id="5ffe5-198">WdiContext</span><span class="sxs-lookup"><span data-stu-id="5ffe5-198">WdiContext</span></span>       | <span data-ttu-id="5ffe5-199">562949953421312</span><span class="sxs-lookup"><span data-stu-id="5ffe5-199">562949953421312</span></span>   |
| <span data-ttu-id="5ffe5-200">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="5ffe5-200">ResponseTime</span></span>     | <span data-ttu-id="5ffe5-201">281474976710656</span><span class="sxs-lookup"><span data-stu-id="5ffe5-201">281474976710656</span></span>   |
| <span data-ttu-id="5ffe5-202">Nessuno</span><span class="sxs-lookup"><span data-stu-id="5ffe5-202">None</span></span>             | <span data-ttu-id="5ffe5-203">0</span><span class="sxs-lookup"><span data-stu-id="5ffe5-203">0</span></span>                 |

<span data-ttu-id="5ffe5-204">Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave **Keywords** e il valore di enumerazione **EventLogClassic** **36028797018963968**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-204">Update the hash table and include the **key-value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="5ffe5-205">Valore della proprietà statica Keywords (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-205">Keywords static property value (optional)</span></span>

<span data-ttu-id="5ffe5-206">La chiave **Keywords** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-206">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="5ffe5-207">Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_** .</span><span class="sxs-lookup"><span data-stu-id="5ffe5-207">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="5ffe5-208">Ad esempio, lo script seguente usa la proprietà **Value_** .</span><span class="sxs-lookup"><span data-stu-id="5ffe5-208">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="5ffe5-209">Filtro per ID evento</span><span class="sxs-lookup"><span data-stu-id="5ffe5-209">Filtering by Event Id</span></span>

<span data-ttu-id="5ffe5-210">Per ottenere dati più specifici, i risultati della query vengono filtrati in base all'**ID evento**. Per fare riferimento all'**ID evento** nella tabella hash si usano la chiave **ID** e un **ID evento** specifico come valore. Il **Visualizzatore eventi di Windows** visualizza l'**ID evento**. In questo esempio viene usato l'**ID evento 1023**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-210">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="5ffe5-211">Aggiornare la tabella hash e includere la coppia **chiave-valore** con la chiave **ID** e il valore **1023**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-211">Update the hash table and include the **key-value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="5ffe5-212">Filtro per livello</span><span class="sxs-lookup"><span data-stu-id="5ffe5-212">Filtering by Level</span></span>

<span data-ttu-id="5ffe5-213">Per affinare ulteriormente i risultati e includere solo gli eventi che sono errori, usare la chiave **Level**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-213">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="5ffe5-214">**Visualizzatore eventi di Windows** visualizza i valori di **Level** come valori stringa, ma sono valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-214">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="5ffe5-215">Nella tabella hash, se si usa la chiave **Level** con un valore stringa viene visualizzato un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-215">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="5ffe5-216">**Level** include valori come **Error**, **Warning** o **Informational**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-216">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="5ffe5-217">Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventLevel`.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-217">Use the following command to display the `StandardEventLevel` property names.</span></span>

```powershell
[System.Diagnostics.Eventing.Reader.StandardEventLevel] | Get-Member -Static -MemberType Property
```

```Output
   TypeName: System.Diagnostics.Eventing.Reader.StandardEventLevel

Name          MemberType Definition
----          ---------- ----------
Critical      Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Critical {get;}
Error         Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Error {get;}
Informational Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Informational {get;}
LogAlways     Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel LogAlways {get;}
Verbose       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Verbose {get;}
Warning       Property   static System.Diagnostics.Eventing.Reader.StandardEventLevel Warning {get;}
```

<span data-ttu-id="5ffe5-218">I valori enumerati sono documentati in **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-218">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="5ffe5-219">Per altre informazioni, vedere [Enumerazione StandardEventLevel](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="5ffe5-219">For more information, see [StandardEventLevel Enumeration](/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="5ffe5-220">I nomi e i valori enumerati per la chiave **Level** sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="5ffe5-220">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="5ffe5-221">Nome</span><span class="sxs-lookup"><span data-stu-id="5ffe5-221">Name</span></span>           | <span data-ttu-id="5ffe5-222">Value</span><span class="sxs-lookup"><span data-stu-id="5ffe5-222">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="5ffe5-223">Verbose</span><span class="sxs-lookup"><span data-stu-id="5ffe5-223">Verbose</span></span>        |   <span data-ttu-id="5ffe5-224">5</span><span class="sxs-lookup"><span data-stu-id="5ffe5-224">5</span></span>   |
| <span data-ttu-id="5ffe5-225">Informativo</span><span class="sxs-lookup"><span data-stu-id="5ffe5-225">Informational</span></span>  |   <span data-ttu-id="5ffe5-226">4</span><span class="sxs-lookup"><span data-stu-id="5ffe5-226">4</span></span>   |
| <span data-ttu-id="5ffe5-227">Avviso</span><span class="sxs-lookup"><span data-stu-id="5ffe5-227">Warning</span></span>        |   <span data-ttu-id="5ffe5-228">3</span><span class="sxs-lookup"><span data-stu-id="5ffe5-228">3</span></span>   |
| <span data-ttu-id="5ffe5-229">Errore di</span><span class="sxs-lookup"><span data-stu-id="5ffe5-229">Error</span></span>          |   <span data-ttu-id="5ffe5-230">2</span><span class="sxs-lookup"><span data-stu-id="5ffe5-230">2</span></span>   |
| <span data-ttu-id="5ffe5-231">Critico</span><span class="sxs-lookup"><span data-stu-id="5ffe5-231">Critical</span></span>       |   <span data-ttu-id="5ffe5-232">1</span><span class="sxs-lookup"><span data-stu-id="5ffe5-232">1</span></span>   |
| <span data-ttu-id="5ffe5-233">LogAlways</span><span class="sxs-lookup"><span data-stu-id="5ffe5-233">LogAlways</span></span>      |   <span data-ttu-id="5ffe5-234">0</span><span class="sxs-lookup"><span data-stu-id="5ffe5-234">0</span></span>   |

<span data-ttu-id="5ffe5-235">La tabella hash della query completata include la chiave **Level** e il valore **2**.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-235">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="5ffe5-236">Proprietà statica Level nell'enumerazione (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="5ffe5-236">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="5ffe5-237">La chiave **Level** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.</span><span class="sxs-lookup"><span data-stu-id="5ffe5-237">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="5ffe5-238">Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_** .</span><span class="sxs-lookup"><span data-stu-id="5ffe5-238">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="5ffe5-239">Ad esempio, lo script seguente usa la proprietà **Value_** .</span><span class="sxs-lookup"><span data-stu-id="5ffe5-239">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventLevel]::Informational
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=$C.Value__
}
```