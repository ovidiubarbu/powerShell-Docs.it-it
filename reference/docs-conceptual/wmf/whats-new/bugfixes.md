---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Correzioni di bug in WMF 5.1
ms.openlocfilehash: 8edf295eb6304dc04de2fa5d3792b1c2fc4b01f3
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147851"
---
# <a name="bug-fixes-in-wmf-51"></a><span data-ttu-id="0ad21-103">Correzioni di bug in WMF 5.1</span><span class="sxs-lookup"><span data-stu-id="0ad21-103">Bug Fixes in WMF 5.1</span></span>

## <a name="bug-fixes"></a><span data-ttu-id="0ad21-104">Correzioni di bug</span><span class="sxs-lookup"><span data-stu-id="0ad21-104">Bug fixes</span></span>

<span data-ttu-id="0ad21-105">In WMF 5.1 sono stati corretti i bug importanti seguenti:</span><span class="sxs-lookup"><span data-stu-id="0ad21-105">The following notable bugs are fixed in WMF 5.1:</span></span>

### <a name="module-auto-discovery-fully-honors-psmodulepath"></a><span data-ttu-id="0ad21-106">Rispetto completo del modulo auto-discovery PSModulePath</span><span class="sxs-lookup"><span data-stu-id="0ad21-106">Module auto-discovery fully honors PSModulePath</span></span>

<span data-ttu-id="0ad21-107">In WMF 3 è stato introdotto il modulo auto-discovery (caricamento automatico di moduli senza un'istanza esplicita di Import-Module quando si chiama un comando).</span><span class="sxs-lookup"><span data-stu-id="0ad21-107">Module auto-discovery (loading modules automatically without an explicit Import-Module when calling a command) was introduced in WMF 3.</span></span> <span data-ttu-id="0ad21-108">Quando è stata introdotta tale versione, PowerShell cercava i comandi in `$PSHome\Modules` prima di usare `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="0ad21-108">When introduced, PowerShell checked for commands in `$PSHome\Modules` before using `$env:PSModulePath`.</span></span>

<span data-ttu-id="0ad21-109">WMF 5.1 modifica questo comportamento per rispettare `$env:PSModulePath` completamente.</span><span class="sxs-lookup"><span data-stu-id="0ad21-109">WMF 5.1 changes this behavior to honor `$env:PSModulePath` completely.</span></span> <span data-ttu-id="0ad21-110">In questo modo, un modulo creato dall'utente che definisce i comandi di PowerShell (ad esempio `Get-ChildItem`) può essere caricato automaticamente e può sostituire correttamente il comando integrato.</span><span class="sxs-lookup"><span data-stu-id="0ad21-110">This allows for a user-authored module that defines commands provided by PowerShell (e.g. `Get-ChildItem`) to be auto-loaded and correctly overriding the built-in command.</span></span>

### <a name="file-redirection-no-longer-hard-codes--encoding-unicode"></a><span data-ttu-id="0ad21-111">Il reindirizzamento di file non usa più -Encoding Unicode hardcoded</span><span class="sxs-lookup"><span data-stu-id="0ad21-111">File redirection no longer hard-codes -Encoding Unicode</span></span>

<span data-ttu-id="0ad21-112">In tutte le versioni precedenti di PowerShell, non era possibile controllare la codifica del file usato dall'operatore di reindirizzamento di file.</span><span class="sxs-lookup"><span data-stu-id="0ad21-112">In all previous versions of PowerShell, it was impossible to control the file encoding used by the file redirection operator.</span></span>

<span data-ttu-id="0ad21-113">A partire da WMF 5.1, è ora possibile modificare la codifica del file di reindirizzamento impostando `$PSDefaultParameterValues`:</span><span class="sxs-lookup"><span data-stu-id="0ad21-113">Starting with WMF 5.1, you can now change the file encoding of redirection by setting `$PSDefaultParameterValues`:</span></span>

```powershell
$PSDefaultParameterValues["Out-File:Encoding"] = "Ascii"
```

### <a name="fixed-a-regression-in-accessing-members-of-systemreflectiontypeinfo"></a><span data-ttu-id="0ad21-114">Correzione di una regressione nell'accesso dei membri di System.Reflection.TypeInfo</span><span class="sxs-lookup"><span data-stu-id="0ad21-114">Fixed a regression in accessing members of System.Reflection.TypeInfo</span></span>

<span data-ttu-id="0ad21-115">Una regressione introdotta in WMF 5.0 interrompeva l'accesso ai membri di `System.Reflection.RuntimeType`, ad esempio `[int].ImplementedInterfaces`.</span><span class="sxs-lookup"><span data-stu-id="0ad21-115">A regression introduced in WMF 5.0 broke accessing members of `System.Reflection.RuntimeType`, for example, `[int].ImplementedInterfaces`.</span></span> <span data-ttu-id="0ad21-116">Questo bug è stato corretto in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="0ad21-116">This bug has been fixed in WMF 5.1.</span></span>

### <a name="fixed-some-issues-with-com-objects"></a><span data-ttu-id="0ad21-117">Risolti alcuni problemi con gli oggetti COM</span><span class="sxs-lookup"><span data-stu-id="0ad21-117">Fixed some issues with COM objects</span></span>

<span data-ttu-id="0ad21-118">In WMF 5.0 è stato introdotto un nuovo strumento di associazione COM per richiamare metodi su oggetti COM e accedere alle proprietà degli oggetti COM.</span><span class="sxs-lookup"><span data-stu-id="0ad21-118">WMF 5.0 introduced a new COM binder for invoking methods on COM objects and accessing properties of COM objects.</span></span> <span data-ttu-id="0ad21-119">Questo nuovo strumento di associazione ha migliorato in modo significativo le prestazioni e ha inoltre introdotto alcuni bug che sono stati corretti in WMF 5.1.</span><span class="sxs-lookup"><span data-stu-id="0ad21-119">This new binder improved performance significantly but also introduced some bugs which have been fixed in WMF 5.1.</span></span>

#### <a name="argument-conversions-were-not-always-performed-correctly"></a><span data-ttu-id="0ad21-120">Le conversioni di argomenti non venivano sempre eseguite correttamente</span><span class="sxs-lookup"><span data-stu-id="0ad21-120">Argument conversions were not always performed correctly</span></span>

<span data-ttu-id="0ad21-121">Nell'esempio seguente:</span><span class="sxs-lookup"><span data-stu-id="0ad21-121">In the following example:</span></span>

```powershell
$obj = New-Object -ComObject WScript.Shell
$obj.SendKeys([char]173)
```

<span data-ttu-id="0ad21-122">Il metodo **SendKeys** prevede una stringa, ma PowerShell non converte il carattere in una stringa, rinviando la conversione a **IDispatch::Invoke** che usa **VariantChangeType** per eseguire la conversione.</span><span class="sxs-lookup"><span data-stu-id="0ad21-122">The **SendKeys** method expects a string, but PowerShell did not convert the char to a string, deferring the conversion to **IDispatch::Invoke**, which uses **VariantChangeType** to do the conversion.</span></span> <span data-ttu-id="0ad21-123">In questo esempio, il risultato è l'invio delle chiavi '1', '7' e '3' invece della chiave **Volume.Mute** prevista.</span><span class="sxs-lookup"><span data-stu-id="0ad21-123">In this example, this resulted in sending the keys '1', '7', and '3' instead of the expected **Volume.Mute** key.</span></span>

#### <a name="enumerable-com-objects-not-always-handled-correctly"></a><span data-ttu-id="0ad21-124">Gli oggetti COM enumerabili non venivano sempre gestiti correttamente</span><span class="sxs-lookup"><span data-stu-id="0ad21-124">Enumerable COM objects not always handled correctly</span></span>

<span data-ttu-id="0ad21-125">PowerShell in genere enumera la maggior parte degli oggetti enumerabili, ma una regressione introdotta in WMF 5.0 impediva l'enumerazione di oggetti COM che implementano IEnumerable.</span><span class="sxs-lookup"><span data-stu-id="0ad21-125">PowerShell normally enumerates most enumerable objects, but a regression introduced in WMF 5.0 prevented the enumeration of COM objects that implement IEnumerable.</span></span> <span data-ttu-id="0ad21-126">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="0ad21-126">For example:</span></span>

```powershell
function Get-COMDictionary
{
    $d = New-Object -ComObject Scripting.Dictionary
    $d.Add('a', 2)
    $d.Add('b', 2)
    return $d
}

$x = Get-COMDictionary
```

<span data-ttu-id="0ad21-127">Nell'esempio precedente, WMF 5.0 ha scritto in modo errato **Scripting.Dictionary** nella pipeline anziché enumerare le coppie chiave-valore.</span><span class="sxs-lookup"><span data-stu-id="0ad21-127">In the above example, WMF 5.0 incorrectly wrote the **Scripting.Dictionary** to the pipeline instead of enumerating the key/value pairs.</span></span>

### <a name="ordered-was-not-allowed-inside-classes"></a><span data-ttu-id="0ad21-128">[ordered] non è consentito all'interno delle classi</span><span class="sxs-lookup"><span data-stu-id="0ad21-128">[ordered] was not allowed inside classes</span></span>

<span data-ttu-id="0ad21-129">In WMF 5.0 sono state introdotte classi con la convalida dei valori letterali di tipo per le classi.</span><span class="sxs-lookup"><span data-stu-id="0ad21-129">WMF 5.0 introduced classes with validation of type literals used in classes.</span></span> <span data-ttu-id="0ad21-130">`[ordered]` è simile a un valore letterale di tipo, ma non è un tipo .NET.</span><span class="sxs-lookup"><span data-stu-id="0ad21-130">`[ordered]` looks like a type literal but is not a true .NET type.</span></span> <span data-ttu-id="0ad21-131">WMF 5.0 restituiva erroneamente un errore relativo a `[ordered]` in una classe:</span><span class="sxs-lookup"><span data-stu-id="0ad21-131">WMF 5.0 incorrectly reported an error on `[ordered]` inside a class:</span></span>

```powershell
class CThing
{
    [object] foo($i)
    {
        [ordered]@{ Thing = $i }
    }
}
```

### <a name="help-on-about-topics-with-multiple-versions-does-not-work"></a><span data-ttu-id="0ad21-132">Supporto non funzionante sugli argomenti della Guida con più versioni</span><span class="sxs-lookup"><span data-stu-id="0ad21-132">Help on About topics with multiple versions does not work</span></span>

<span data-ttu-id="0ad21-133">Prima di WMF 5.1, se erano installate più versioni di un modulo e tutte condividevano un argomento della Guida, ad esempio about_PSReadline, `help about_PSReadline` restituiva più argomenti e non era possibile visualizzare la Guida vera e propria.</span><span class="sxs-lookup"><span data-stu-id="0ad21-133">Before WMF 5.1, if you had multiple versions of a module installed and they all shared a help topic, for example, about_PSReadline, `help about_PSReadline` would return multiple topics with no obvious way to view the real help.</span></span>

<span data-ttu-id="0ad21-134">In WMF 5.1 il problema è stato risolto restituendo la Guida per la versione più recente dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="0ad21-134">WMF 5.1 fixes this by returning the help for the latest version of the topic.</span></span>

<span data-ttu-id="0ad21-135">`Get-Help` non fornisce un modo per specificare la versione per la quale si vuole visualizzare la Guida.</span><span class="sxs-lookup"><span data-stu-id="0ad21-135">`Get-Help` does not provide a way to specify which version you want help for.</span></span> <span data-ttu-id="0ad21-136">Per risolvere il problema, passare alla directory dei moduli e visualizzare la Guida direttamente con uno strumento come il proprio editor preferito.</span><span class="sxs-lookup"><span data-stu-id="0ad21-136">To work around this, navigate to the modules directory and view the help directly with a tool like your favorite editor.</span></span>

### <a name="powershellexe-reading-from-stdin-stopped-working"></a><span data-ttu-id="0ad21-137">La lettura di PowerShell.exe da STDIN non funziona più</span><span class="sxs-lookup"><span data-stu-id="0ad21-137">powershell.exe reading from STDIN stopped working</span></span>

<span data-ttu-id="0ad21-138">I clienti usano `powershell -command -` da app native per eseguire PowerShell passandolo nello script tramite STDIN. Purtroppo questa funzionalità non è più disponibile a causa di altri modifiche nell'host della console.</span><span class="sxs-lookup"><span data-stu-id="0ad21-138">Customers use `powershell -command -` from native apps to execute PowerShell passing in the script via STDIN unfortunately this was broken by other changes in the console host.</span></span>

<span data-ttu-id="0ad21-139">Questo problema è stato risolto per la versione 5.1 in Windows 10 Anniversary Update.</span><span class="sxs-lookup"><span data-stu-id="0ad21-139">This is fixed for version 5.1 in the Windows 10 Anniversary Update.</span></span>

### <a name="powershellexe-creates-spike-in-cpu-usage-on-startup"></a><span data-ttu-id="0ad21-140">PowerShell.exe crea picchi di utilizzo della CPU all'avvio</span><span class="sxs-lookup"><span data-stu-id="0ad21-140">powershell.exe creates spike in CPU usage on startup</span></span>

<span data-ttu-id="0ad21-141">PowerShell usa una query WMI per controllare se è stato avviato tramite Criteri di gruppo per evitare di causare ritardi nella fase di accesso.</span><span class="sxs-lookup"><span data-stu-id="0ad21-141">PowerShell uses a WMI query to check if it was started via Group Policy to avoid causing delay in login.</span></span> <span data-ttu-id="0ad21-142">Ne risulta che la query WMI inserisce tzres.mui.dll in ogni processo nel sistema, perché la classe WMI **Win32_Process** tenta di recuperare informazioni sul fuso orario locale.</span><span class="sxs-lookup"><span data-stu-id="0ad21-142">The WMI query ends up injecting tzres.mui.dll into every process on the system since the WMI **Win32_Process** class attempts to retrieve local timezone information.</span></span> <span data-ttu-id="0ad21-143">Ciò comporta un notevole picco di utilizzo della CPU in **wmiprvse** (host del provider WMI).</span><span class="sxs-lookup"><span data-stu-id="0ad21-143">This results in a large CPU spike in **wmiprvse** (the WMI provider host).</span></span> <span data-ttu-id="0ad21-144">La soluzione consiste nell'usare chiamate all'API Win32 per ottenere le stesse informazioni invece di usare WMI.</span><span class="sxs-lookup"><span data-stu-id="0ad21-144">Fix is to use Win32 API calls to get the same information instead of using WMI.</span></span>
