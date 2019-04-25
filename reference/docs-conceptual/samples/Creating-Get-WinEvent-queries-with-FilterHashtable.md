---
ms.date: 3/18/2019
title: Creazione di query Get-WinEvent con FilterHashtable
ms.openlocfilehash: 28ba3c99a297944003a28eaba7de34b77d9df536
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058814"
---
# <a name="creating-get-winevent-queries-with-filterhashtable"></a><span data-ttu-id="ebdca-102">Creazione di query Get-WinEvent con FilterHashtable</span><span class="sxs-lookup"><span data-stu-id="ebdca-102">Creating Get-WinEvent queries with FilterHashtable</span></span>

<span data-ttu-id="ebdca-103">Per leggere il post del blog **Scripting Guy** originale del 3 giugno 2014, vedere [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/) (Usare FilterHashTable per filtrare il registro eventi con PowerShell).</span><span class="sxs-lookup"><span data-stu-id="ebdca-103">To read the original June 3, 2014 **Scripting Guy** blog post, see [Use FilterHashTable to Filter Event Log with PowerShell](https://devblogs.microsoft.com/scripting/use-filterhashtable-to-filter-event-log-with-powershell/).</span></span>

<span data-ttu-id="ebdca-104">Questo articolo è un estratto del post di blog originale e spiega come usare il parametro **FilterHashtable** del cmdlet `Get-WinEvent` per filtrare i registri eventi.</span><span class="sxs-lookup"><span data-stu-id="ebdca-104">This article is an excerpt of the original blog post and explains how to use the `Get-WinEvent` cmdlet's **FilterHashtable** parameter to filter event logs.</span></span> <span data-ttu-id="ebdca-105">Il cmdlet `Get-WinEvent` di PowerShell è un metodo efficace per filtrare i registri eventi e i log di diagnostica di Windows.</span><span class="sxs-lookup"><span data-stu-id="ebdca-105">PowerShell's `Get-WinEvent` cmdlet is a powerful method to filter Windows event and diagnostic logs.</span></span> <span data-ttu-id="ebdca-106">Le prestazioni migliorano quando una query `Get-WinEvent` usa il parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-106">Performance improves when a `Get-WinEvent` query uses the **FilterHashtable** parameter.</span></span>

<span data-ttu-id="ebdca-107">Quando si lavora con registri eventi di grandi dimensioni, non è efficace inviare gli oggetti nella pipeline a un comando `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="ebdca-107">When you work with large event logs, it's not efficient to send objects down the pipeline to a `Where-Object` command.</span></span> <span data-ttu-id="ebdca-108">Prima di PowerShell 6, il cmdlet `Get-EventLog` rappresentava un'altra opzione per ottenere i dati di log.</span><span class="sxs-lookup"><span data-stu-id="ebdca-108">Prior to PowerShell 6, the `Get-EventLog` cmdlet was another option to get log data.</span></span> <span data-ttu-id="ebdca-109">Ad esempio, i comandi seguenti non sono efficienti per filtrare i log **Microsoft-Windows-Defrag**:</span><span class="sxs-lookup"><span data-stu-id="ebdca-109">For example, the following commands are inefficient to filter the **Microsoft-Windows-Defrag** logs:</span></span>

`Get-EventLog -LogName Application | Where-Object Source -Match defrag`

`Get-WinEvent -LogName Application | Where-Object { $_.ProviderName -Match 'defrag' }`

<span data-ttu-id="ebdca-110">Il comando seguente usa una tabella hash che migliora le prestazioni:</span><span class="sxs-lookup"><span data-stu-id="ebdca-110">The following command uses a hash table that improves the performance:</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='*defrag'
}
```

## <a name="blog-posts-about-enumeration"></a><span data-ttu-id="ebdca-111">Post di blog sull'enumerazione</span><span class="sxs-lookup"><span data-stu-id="ebdca-111">Blog posts about enumeration</span></span>

<span data-ttu-id="ebdca-112">Questo articolo presenta informazioni su come usare i valori enumerati in una tabella hash.</span><span class="sxs-lookup"><span data-stu-id="ebdca-112">This article presents information about how to use enumerated values in a hash table.</span></span> <span data-ttu-id="ebdca-113">Per altre informazioni sull'enumerazione, leggere questi post del blog **Scripting Guy**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-113">For more information about enumeration, read these **Scripting Guy** blog posts.</span></span> <span data-ttu-id="ebdca-114">Per creare una funzione che restituisce i valori enumerati, vedere [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values) (Enumerazioni e valori).</span><span class="sxs-lookup"><span data-stu-id="ebdca-114">To create a function that returns the enumerated values, see [Enumerations and Values](https://devblogs.microsoft.com/scripting/hey-scripting-guy-weekend-scripter-enumerations-and-values).</span></span>
<span data-ttu-id="ebdca-115">Per altre informazioni, vedere la [serie di post del blog Scripting Guy sull'enumerazione](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span><span class="sxs-lookup"><span data-stu-id="ebdca-115">For more information, see the [Scripting Guy series of blog posts about enumeration](https://devblogs.microsoft.com/scripting/?s=about+enumeration).</span></span>

## <a name="hash-table-keyvalue-pairs"></a><span data-ttu-id="ebdca-116">Coppie chiave/valore della tabella di hash</span><span class="sxs-lookup"><span data-stu-id="ebdca-116">Hash table key/value pairs</span></span>

<span data-ttu-id="ebdca-117">Per creare query efficienti, usare il cmdlet `Get-WinEvent` con il parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-117">To build efficient queries, use the `Get-WinEvent` cmdlet with the **FilterHashtable** parameter.</span></span>
<span data-ttu-id="ebdca-118">**FilterHashtable** accetta una tabella hash come filtro per ottenere informazioni specifiche dai registri eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="ebdca-118">**FilterHashtable** accepts a hash table as a filter to get specific information from Windows event logs.</span></span> <span data-ttu-id="ebdca-119">Una tabella hash usa coppie **chiave/valore**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-119">A hash table uses **key/value** pairs.</span></span> <span data-ttu-id="ebdca-120">Per altre informazioni sulle tabelle hash, vedere [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span><span class="sxs-lookup"><span data-stu-id="ebdca-120">For more information about hash tables, see [about_Hash_Tables](/powershell/module/microsoft.powershell.core/about/about_hash_tables).</span></span>

<span data-ttu-id="ebdca-121">Se le coppie **chiave/valore** sono sulla stessa riga, devono essere separate da un punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="ebdca-121">If the **key/value** pairs are on the same line, they must be separated by a semicolon.</span></span> <span data-ttu-id="ebdca-122">Se ogni coppia **chiave/valore** è su una riga separata, non è necessario il punto e virgola.</span><span class="sxs-lookup"><span data-stu-id="ebdca-122">If each **key/value** pair is on a separate line, the semicolon isn't needed.</span></span> <span data-ttu-id="ebdca-123">Ad esempio, in questo articolo le coppie **chiave/valore** sono posizionate su righe separate e non vengono usati punti e virgola.</span><span class="sxs-lookup"><span data-stu-id="ebdca-123">For example, this article places **key/value** pairs on separate lines and doesn't use semicolons.</span></span>

<span data-ttu-id="ebdca-124">Questo esempio usa varie coppie **chiave/valore** del parametro **FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-124">This sample uses several of the **FilterHashtable** parameter's **key/value** pairs.</span></span> <span data-ttu-id="ebdca-125">La query completa include **LogName**, **ProviderName**, **Keywords**, **ID** e **Level**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-125">The completed query includes **LogName**, **ProviderName**, **Keywords**, **ID**, and **Level**.</span></span>

<span data-ttu-id="ebdca-126">Le coppie **chiave/valore** accettate sono riportate nella tabella seguente e sono incluse nella documentazione per il parametro [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-126">The accepted **key/value** pairs are shown in the following table and are included in the documentation for the [Get-WinEvent](/powershell/module/microsoft.powershell.diagnostics/Get-WinEvent)
**FilterHashtable** parameter.</span></span>

<span data-ttu-id="ebdca-127">Nella tabella seguente vengono visualizzati i nomi delle chiavi, i tipi di dati e viene indicato se i caratteri jolly sono consentiti per un valore di dati.</span><span class="sxs-lookup"><span data-stu-id="ebdca-127">The following table displays the key names, data types, and whether wildcard characters are accepted for a data value.</span></span>

| <span data-ttu-id="ebdca-128">Nome chiave</span><span class="sxs-lookup"><span data-stu-id="ebdca-128">Key name</span></span>     | <span data-ttu-id="ebdca-129">Tipo di dati del valore</span><span class="sxs-lookup"><span data-stu-id="ebdca-129">Value data type</span></span>    | <span data-ttu-id="ebdca-130">Caratteri jolly accettati?</span><span class="sxs-lookup"><span data-stu-id="ebdca-130">Accepts wildcard characters?</span></span> |
|------------- | ------------------ | ---------------------------- |
| <span data-ttu-id="ebdca-131">LogName</span><span class="sxs-lookup"><span data-stu-id="ebdca-131">LogName</span></span>      | `<String[]>`       | <span data-ttu-id="ebdca-132">Sì</span><span class="sxs-lookup"><span data-stu-id="ebdca-132">Yes</span></span> |
| <span data-ttu-id="ebdca-133">ProviderName</span><span class="sxs-lookup"><span data-stu-id="ebdca-133">ProviderName</span></span> | `<String[]>`       | <span data-ttu-id="ebdca-134">Sì</span><span class="sxs-lookup"><span data-stu-id="ebdca-134">Yes</span></span> |
| <span data-ttu-id="ebdca-135">Path</span><span class="sxs-lookup"><span data-stu-id="ebdca-135">Path</span></span>         | `<String[]>`       | <span data-ttu-id="ebdca-136">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-136">No</span></span>  |
| <span data-ttu-id="ebdca-137">Parole chiave</span><span class="sxs-lookup"><span data-stu-id="ebdca-137">Keywords</span></span>     | `<Long[]>`         | <span data-ttu-id="ebdca-138">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-138">No</span></span>  |
| <span data-ttu-id="ebdca-139">ID</span><span class="sxs-lookup"><span data-stu-id="ebdca-139">ID</span></span>           | `<Int32[]>`        | <span data-ttu-id="ebdca-140">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-140">No</span></span>  |
| <span data-ttu-id="ebdca-141">Livello</span><span class="sxs-lookup"><span data-stu-id="ebdca-141">Level</span></span>        | `<Int32[]>`        | <span data-ttu-id="ebdca-142">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-142">No</span></span>  |
| <span data-ttu-id="ebdca-143">StartTime</span><span class="sxs-lookup"><span data-stu-id="ebdca-143">StartTime</span></span>    | `<DateTime>`       | <span data-ttu-id="ebdca-144">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-144">No</span></span>  |
| <span data-ttu-id="ebdca-145">EndTime</span><span class="sxs-lookup"><span data-stu-id="ebdca-145">EndTime</span></span>      | `<DateTime>`       | <span data-ttu-id="ebdca-146">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-146">No</span></span>  |
| <span data-ttu-id="ebdca-147">UserID</span><span class="sxs-lookup"><span data-stu-id="ebdca-147">UserID</span></span>       | `<SID>`            | <span data-ttu-id="ebdca-148">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-148">No</span></span>  |
| <span data-ttu-id="ebdca-149">Dati</span><span class="sxs-lookup"><span data-stu-id="ebdca-149">Data</span></span>         | `<String[]>`       | <span data-ttu-id="ebdca-150">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-150">No</span></span>  |
| *            | `<String[]>`       | <span data-ttu-id="ebdca-151">No</span><span class="sxs-lookup"><span data-stu-id="ebdca-151">No</span></span>  |

## <a name="building-a-query-with-a-hash-table"></a><span data-ttu-id="ebdca-152">Creazione di una query con una tabella hash</span><span class="sxs-lookup"><span data-stu-id="ebdca-152">Building a query with a hash table</span></span>

<span data-ttu-id="ebdca-153">Per verificare i risultati e risolvere i problemi, è utile comporre la tabella hash con una coppia **chiave/valore** alla volta.</span><span class="sxs-lookup"><span data-stu-id="ebdca-153">To verify results and troubleshoot problems, it helps to build the hash table one **key/value** pair at a time.</span></span> <span data-ttu-id="ebdca-154">La query ottiene i dati dal log **Application**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-154">The query gets data from the **Application** log.</span></span> <span data-ttu-id="ebdca-155">La tabella hash è equivalente a `Get-WinEvent –LogName Application`.</span><span class="sxs-lookup"><span data-stu-id="ebdca-155">The hash table is equivalent to `Get-WinEvent –LogName Application`.</span></span>

<span data-ttu-id="ebdca-156">Per iniziare, creare la query `Get-WinEvent`.</span><span class="sxs-lookup"><span data-stu-id="ebdca-156">To begin, create the `Get-WinEvent` query.</span></span> <span data-ttu-id="ebdca-157">Usare la coppia **chiave/valore** del parametro **FilterHashtable** con la chiave **LogName** e il valore **Application**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-157">Use the **FilterHashtable** parameter's **key/value** pair with the key, **LogName**, and the value, **Application**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
}
```

<span data-ttu-id="ebdca-158">Continuare a comporre la tabella hash con la chiave **ProviderName**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-158">Continue to build the hash table with the **ProviderName** key.</span></span> <span data-ttu-id="ebdca-159">**ProviderName** è il nome visualizzato nel campo **Origine** nel **Visualizzatore eventi di Windows**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-159">The **ProviderName** is the name that appears in the **Source** field in the **Windows Event Viewer**.</span></span> <span data-ttu-id="ebdca-160">Ad esempio, **.NET Runtime** nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="ebdca-160">For example, **.NET Runtime** in the following screenshot:</span></span>

![Immagine delle origini di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/providername.png)

<span data-ttu-id="ebdca-162">Aggiornare la tabella hash e includere la coppia **chiave/valore** con la chiave \*\*ProviderName e il valore **.NET Runtime**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-162">Update the hash table and include the **key/value** pair with the key, \*\*ProviderName, and the value, **.NET Runtime**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
}
```

<span data-ttu-id="ebdca-163">Se la query deve ottenere dati da registri eventi archiviati, usare la chiave **Path**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-163">If your query needs to get data from archived event logs, use the **Path** key.</span></span> <span data-ttu-id="ebdca-164">Il valore **Path** specifica il percorso completo del file di log.</span><span class="sxs-lookup"><span data-stu-id="ebdca-164">The **Path** value specifies the full path to the log file.</span></span> <span data-ttu-id="ebdca-165">Per altre informazioni, vedere il post del blog **Scripting Guy** [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors) (Usare PowerShell per analizzare i registri eventi salvati per individuare gli errori).</span><span class="sxs-lookup"><span data-stu-id="ebdca-165">For more information, see the **Scripting Guy** blog post, [Use PowerShell to Parse Saved Event Logs for Errors](https://devblogs.microsoft.com/scripting/use-powershell-to-parse-saved-event-logs-for-errors).</span></span>

## <a name="using-enumerated-values-in-a-hash-table"></a><span data-ttu-id="ebdca-166">Uso dei valori enumerati in una tabella hash</span><span class="sxs-lookup"><span data-stu-id="ebdca-166">Using enumerated values in a hash table</span></span>

<span data-ttu-id="ebdca-167">La chiave successiva nella tabella hash è **Keywords**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-167">**Keywords** is the next key in the hash table.</span></span> <span data-ttu-id="ebdca-168">Il tipo di dati **Keywords** è una matrice del tipo valore `[long]` che contiene un numero elevato.</span><span class="sxs-lookup"><span data-stu-id="ebdca-168">The **Keywords** data type is an array of the `[long]` value type that holds a large number.</span></span> <span data-ttu-id="ebdca-169">Usare il comando seguente per trovare il valore massimo di `[long]`:</span><span class="sxs-lookup"><span data-stu-id="ebdca-169">Use the following command to find the maximum value of `[long]`:</span></span>

```powershell
[long]::MaxValue
```

```Output
9223372036854775807
```

<span data-ttu-id="ebdca-170">Per la chiave **Keywords** PowerShell usa un numero e non una stringa come **Security**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-170">For the **Keywords** key, PowerShell uses a number, not a string such as **Security**.</span></span> <span data-ttu-id="ebdca-171">**Visualizzatore eventi di Windows** visualizza i valori di **Keywords** come stringhe, ma sono valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="ebdca-171">**Windows Event Viewer** displays the **Keywords** as strings, but they are enumerated values.</span></span> <span data-ttu-id="ebdca-172">Nella tabella hash, se si usa la chiave **Keywords** con un valore stringa, viene visualizzato un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="ebdca-172">In the hash table, if you use the **Keywords** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="ebdca-173">Aprire il **Visualizzatore eventi di Windows** e dal riquadro **Azioni** fare clic su **Filtro registro corrente**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-173">Open the **Windows Event Viewer** and from the **Actions** pane, click on **Filter current log**.</span></span>
<span data-ttu-id="ebdca-174">Nel menu a discesa **Keywords** vengono visualizzate le parole chiave disponibili, come illustrato nello screenshot seguente:</span><span class="sxs-lookup"><span data-stu-id="ebdca-174">The **Keywords** drop-down menu displays the available keywords, as shown in the following screenshot:</span></span>

![Immagine delle parole chiave di Visualizzatore eventi di Windows.](./media/creating-get-winEvent-queries-with-filterhashtable/keywords.png)

<span data-ttu-id="ebdca-176">Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventKeywords`.</span><span class="sxs-lookup"><span data-stu-id="ebdca-176">Use the following command to display the `StandardEventKeywords` property names.</span></span>

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

<span data-ttu-id="ebdca-177">I valori enumerati sono documentati in **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-177">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="ebdca-178">Per altre informazioni, vedere [Enumerazione StandardEventKeywords](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="ebdca-178">For more information, see [StandardEventKeywords Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventkeywords?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="ebdca-179">I nomi e i valori enumerati per **Keywords** sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="ebdca-179">The **Keywords** names and enumerated values are as follows:</span></span>

| <span data-ttu-id="ebdca-180">Nome</span><span class="sxs-lookup"><span data-stu-id="ebdca-180">Name</span></span>             |  <span data-ttu-id="ebdca-181">Value</span><span class="sxs-lookup"><span data-stu-id="ebdca-181">Value</span></span>            |
| ---------------- | ------------------|
| <span data-ttu-id="ebdca-182">AuditFailure</span><span class="sxs-lookup"><span data-stu-id="ebdca-182">AuditFailure</span></span>     | <span data-ttu-id="ebdca-183">4503599627370496</span><span class="sxs-lookup"><span data-stu-id="ebdca-183">4503599627370496</span></span>  |
| <span data-ttu-id="ebdca-184">AuditSuccess</span><span class="sxs-lookup"><span data-stu-id="ebdca-184">AuditSuccess</span></span>     | <span data-ttu-id="ebdca-185">9007199254740992</span><span class="sxs-lookup"><span data-stu-id="ebdca-185">9007199254740992</span></span>  |
| <span data-ttu-id="ebdca-186">CorrelationHint2</span><span class="sxs-lookup"><span data-stu-id="ebdca-186">CorrelationHint2</span></span> | <span data-ttu-id="ebdca-187">18014398509481984</span><span class="sxs-lookup"><span data-stu-id="ebdca-187">18014398509481984</span></span> |
| <span data-ttu-id="ebdca-188">EventLogClassic</span><span class="sxs-lookup"><span data-stu-id="ebdca-188">EventLogClassic</span></span>  | <span data-ttu-id="ebdca-189">36028797018963968</span><span class="sxs-lookup"><span data-stu-id="ebdca-189">36028797018963968</span></span> |
| <span data-ttu-id="ebdca-190">Sqm</span><span class="sxs-lookup"><span data-stu-id="ebdca-190">Sqm</span></span>              | <span data-ttu-id="ebdca-191">2251799813685248</span><span class="sxs-lookup"><span data-stu-id="ebdca-191">2251799813685248</span></span>  |
| <span data-ttu-id="ebdca-192">WdiDiagnostic</span><span class="sxs-lookup"><span data-stu-id="ebdca-192">WdiDiagnostic</span></span>    | <span data-ttu-id="ebdca-193">1125899906842624</span><span class="sxs-lookup"><span data-stu-id="ebdca-193">1125899906842624</span></span>  |
| <span data-ttu-id="ebdca-194">WdiContext</span><span class="sxs-lookup"><span data-stu-id="ebdca-194">WdiContext</span></span>       | <span data-ttu-id="ebdca-195">562949953421312</span><span class="sxs-lookup"><span data-stu-id="ebdca-195">562949953421312</span></span>   |
| <span data-ttu-id="ebdca-196">ResponseTime</span><span class="sxs-lookup"><span data-stu-id="ebdca-196">ResponseTime</span></span>     | <span data-ttu-id="ebdca-197">281474976710656</span><span class="sxs-lookup"><span data-stu-id="ebdca-197">281474976710656</span></span>   |
| <span data-ttu-id="ebdca-198">Nessuno</span><span class="sxs-lookup"><span data-stu-id="ebdca-198">None</span></span>             | <span data-ttu-id="ebdca-199">0</span><span class="sxs-lookup"><span data-stu-id="ebdca-199">0</span></span>                 |

<span data-ttu-id="ebdca-200">Aggiornare la tabella hash e includere la coppia **chiave/valore** con la chiave **Keywords** e il valore di enumerazione **EventLogClassic** **36028797018963968** .</span><span class="sxs-lookup"><span data-stu-id="ebdca-200">Update the hash table and include the **key/value** pair with the key, **Keywords**, and the **EventLogClassic** enumeration value, **36028797018963968**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
}
```

### <a name="keywords-static-property-value-optional"></a><span data-ttu-id="ebdca-201">Valore della proprietà statica Keywords (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="ebdca-201">Keywords static property value (optional)</span></span>

<span data-ttu-id="ebdca-202">La chiave **Keywords** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.</span><span class="sxs-lookup"><span data-stu-id="ebdca-202">The **Keywords** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="ebdca-203">Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-203">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="ebdca-204">Ad esempio, lo script seguente usa la proprietà **Value_**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-204">For example, the following script uses the **Value__** property.</span></span>

```powershell
$C = [System.Diagnostics.Eventing.Reader.StandardEventKeywords]::EventLogClassic
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=$C.Value__
}
```

## <a name="filtering-by-event-id"></a><span data-ttu-id="ebdca-205">Filtro per ID evento</span><span class="sxs-lookup"><span data-stu-id="ebdca-205">Filtering by Event Id</span></span>

<span data-ttu-id="ebdca-206">Per ottenere dati più specifici, i risultati della query vengono filtrati in base all'**ID evento**. Per fare riferimento all'**ID evento** nella tabella hash si usano la chiave **ID** e un **ID evento** specifico come valore. Il **Visualizzatore eventi di Windows** visualizza l'**ID evento**. In questo esempio viene usato l'**ID evento 1023**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-206">To get more specific data, the query's results are filtered by **Event Id**. The **Event Id** is referenced in the hash table as the key **ID** and the value is a specific **Event Id**. The **Windows Event Viewer** displays the **Event Id**. This example uses **Event Id 1023**.</span></span>

<span data-ttu-id="ebdca-207">Aggiornare la tabella hash e includere la coppia **chiave/valore** con la chiave **ID** e il valore **1023**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-207">Update the hash table and include the **key/value** pair with the key, **ID** and the value, **1023**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
}
```

## <a name="filtering-by-level"></a><span data-ttu-id="ebdca-208">Filtro per livello</span><span class="sxs-lookup"><span data-stu-id="ebdca-208">Filtering by Level</span></span>

<span data-ttu-id="ebdca-209">Per affinare ulteriormente i risultati e includere solo gli eventi che sono errori, usare la chiave **Level**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-209">To further refine the results and include only events that are errors, use the **Level** key.</span></span>
<span data-ttu-id="ebdca-210">**Visualizzatore eventi di Windows** visualizza i valori di **Level** come valori stringa, ma sono valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="ebdca-210">**Windows Event Viewer** displays the **Level** as string values, but they are enumerated values.</span></span> <span data-ttu-id="ebdca-211">Nella tabella hash, se si usa la chiave **Level** con un valore stringa viene visualizzato un messaggio di errore.</span><span class="sxs-lookup"><span data-stu-id="ebdca-211">In the hash table, if you use the **Level** key with a string value, an error message is displayed.</span></span>

<span data-ttu-id="ebdca-212">**Level** include valori come **Error**, **Warning** o **Informational**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-212">**Level** has values such as **Error**, **Warning**, or **Informational**.</span></span> <span data-ttu-id="ebdca-213">Usare il comando seguente per visualizzare i nomi delle proprietà `StandardEventLevel`.</span><span class="sxs-lookup"><span data-stu-id="ebdca-213">Use the following command to display the `StandardEventLevel` property names.</span></span>

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

<span data-ttu-id="ebdca-214">I valori enumerati sono documentati in **.NET Framework**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-214">The enumerated values are documented in the **.NET Framework**.</span></span> <span data-ttu-id="ebdca-215">Per altre informazioni, vedere [Enumerazione StandardEventLevel](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span><span class="sxs-lookup"><span data-stu-id="ebdca-215">For more information, see [StandardEventLevel Enumeration](https://docs.microsoft.com/en-us/dotnet/api/system.diagnostics.eventing.reader.standardeventlevel?redirectedfrom=MSDN&view=netframework-4.7.2).</span></span>

<span data-ttu-id="ebdca-216">I nomi e i valori enumerati per la chiave **Level** sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="ebdca-216">The **Level** key's names and enumerated values are as follows:</span></span>

| <span data-ttu-id="ebdca-217">Nome</span><span class="sxs-lookup"><span data-stu-id="ebdca-217">Name</span></span>           | <span data-ttu-id="ebdca-218">Value</span><span class="sxs-lookup"><span data-stu-id="ebdca-218">Value</span></span> |
| -------------- | ----- |
| <span data-ttu-id="ebdca-219">Verbose</span><span class="sxs-lookup"><span data-stu-id="ebdca-219">Verbose</span></span>        |   <span data-ttu-id="ebdca-220">5</span><span class="sxs-lookup"><span data-stu-id="ebdca-220">5</span></span>   |
| <span data-ttu-id="ebdca-221">Informativo</span><span class="sxs-lookup"><span data-stu-id="ebdca-221">Informational</span></span>  |   <span data-ttu-id="ebdca-222">4</span><span class="sxs-lookup"><span data-stu-id="ebdca-222">4</span></span>   |
| <span data-ttu-id="ebdca-223">Avviso</span><span class="sxs-lookup"><span data-stu-id="ebdca-223">Warning</span></span>        |   <span data-ttu-id="ebdca-224">3</span><span class="sxs-lookup"><span data-stu-id="ebdca-224">3</span></span>   |
| <span data-ttu-id="ebdca-225">Errore di</span><span class="sxs-lookup"><span data-stu-id="ebdca-225">Error</span></span>          |   <span data-ttu-id="ebdca-226">2</span><span class="sxs-lookup"><span data-stu-id="ebdca-226">2</span></span>   |
| <span data-ttu-id="ebdca-227">Critico</span><span class="sxs-lookup"><span data-stu-id="ebdca-227">Critical</span></span>       |   <span data-ttu-id="ebdca-228">1</span><span class="sxs-lookup"><span data-stu-id="ebdca-228">1</span></span>   |
| <span data-ttu-id="ebdca-229">LogAlways</span><span class="sxs-lookup"><span data-stu-id="ebdca-229">LogAlways</span></span>      |   <span data-ttu-id="ebdca-230">0</span><span class="sxs-lookup"><span data-stu-id="ebdca-230">0</span></span>   |

<span data-ttu-id="ebdca-231">La tabella hash della query completata include la chiave **Level** e il valore **2**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-231">The hash table for the completed query includes the key, **Level**, and the value, **2**.</span></span>

```powershell
Get-WinEvent -FilterHashtable @{
   LogName='Application'
   ProviderName='.NET Runtime'
   Keywords=36028797018963968
   ID=1023
   Level=2
}
```

### <a name="level-static-property-in-enumeration-optional"></a><span data-ttu-id="ebdca-232">Proprietà statica Level nell'enumerazione (facoltativo)</span><span class="sxs-lookup"><span data-stu-id="ebdca-232">Level static property in enumeration (optional)</span></span>

<span data-ttu-id="ebdca-233">La chiave **Level** viene enumerata, ma è possibile usare un nome di proprietà statica nella query per la tabella hash.</span><span class="sxs-lookup"><span data-stu-id="ebdca-233">The **Level** key is enumerated, but you can use a static property name in the hash table query.</span></span>
<span data-ttu-id="ebdca-234">Invece di usare la stringa restituita, il nome della proprietà deve essere convertito in un valore con la proprietà **Value_**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-234">Rather than using the returned string, the property name must be converted to a value with the **Value__** property.</span></span>

<span data-ttu-id="ebdca-235">Ad esempio, lo script seguente usa la proprietà **Value_**.</span><span class="sxs-lookup"><span data-stu-id="ebdca-235">For example, the following script uses the **Value__** property.</span></span>

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