---
ms.date: 06/12/2017
keywords: jea,powershell,sicurezza
title: Funzionalità del ruolo JEA
ms.openlocfilehash: 528b41c0e2ffdcfed3251fb0f714c649e7290761
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229543"
---
# <a name="jea-role-capabilities"></a><span data-ttu-id="cc450-103">Funzionalità del ruolo JEA</span><span class="sxs-lookup"><span data-stu-id="cc450-103">JEA Role Capabilities</span></span>

> <span data-ttu-id="cc450-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="cc450-104">Applies to: Windows PowerShell 5.0</span></span>

<span data-ttu-id="cc450-105">Quando si crea un endpoint JEA, è necessario definire una o più "funzioni del ruolo" che descrivono *cosa* può eseguire un utente in una sessione JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-105">When creating a JEA endpoint, you will need to define one or more "role capabilities" which describe *what* someone can do in a JEA session.</span></span>
<span data-ttu-id="cc450-106">Una funzionalità del ruolo è un file di dati di PowerShell con l'estensione psrc che elenca tutti i cmdlet, le funzioni, i provider e i programmi esterni che devono essere resi disponibili per connettere gli utenti.</span><span class="sxs-lookup"><span data-stu-id="cc450-106">A role capability is a PowerShell data file with the .psrc extension that lists all the cmdlets, functions, providers, and external programs that should be made available to connecting users.</span></span>

<span data-ttu-id="cc450-107">Questo argomento illustra come creare un file delle funzionalità del ruolo di PowerShell per gli utenti JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-107">This topic describes how to create a PowerShell role capability file for your JEA users.</span></span>

## <a name="determine-which-commands-to-allow"></a><span data-ttu-id="cc450-108">Determinare i comandi da consentire</span><span class="sxs-lookup"><span data-stu-id="cc450-108">Determine which commands to allow</span></span>

<span data-ttu-id="cc450-109">Il primo passaggio durante la creazione di un file delle funzionalità del ruolo è considerare gli elementi a cui gli utenti assegnati al ruolo devono accedere.</span><span class="sxs-lookup"><span data-stu-id="cc450-109">The first step when creating a role capability file is to consider what the users who are assigned the role will need access to.</span></span>
<span data-ttu-id="cc450-110">Questo processo di raccolta dei requisiti potrebbe impiegare del tempo, ma è un processo molto importante.</span><span class="sxs-lookup"><span data-stu-id="cc450-110">This requirements gathering process can take a while, but it is a very important process.</span></span>
<span data-ttu-id="cc450-111">L'accesso a un numero limitato di cmdlet e funzioni potrebbe impedire agli utenti di svolgere il loro lavoro in maniera completa.</span><span class="sxs-lookup"><span data-stu-id="cc450-111">Giving users access to too few cmdlets and functions can prevent them from getting their job done.</span></span>
<span data-ttu-id="cc450-112">L'accesso a un numero eccessivo di cmdlet e funzioni che non rientrano nei privilegi amministrativi impliciti degli utenti potrebbe creare problemi di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="cc450-112">Allowing access to too many cmdlets and functions can lead to users doing more than you intended with their implicit admin privileges, weakening your security stance.</span></span>

<span data-ttu-id="cc450-113">L'esecuzione di questo processo dipende dagli obiettivi della società. I suggerimenti seguenti tuttavia possono aiutare a capire se si è nella direzione giusta.</span><span class="sxs-lookup"><span data-stu-id="cc450-113">How you go about this process will depend on your organization and goals, however the following tips can help ensure you're on the right path.</span></span>

1. <span data-ttu-id="cc450-114">**Identificare** i comandi usati dagli utenti necessari per eseguire il loro lavoro.</span><span class="sxs-lookup"><span data-stu-id="cc450-114">**Identify** the commands users are using to get their jobs done.</span></span> <span data-ttu-id="cc450-115">Questa operazione potrebbe comportare il controllo delle azioni del personale IT, degli script di automazione o l'analisi dei log o delle trascrizioni delle sessioni di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc450-115">This may involve surveying IT staff, checking automation scripts, or analyzing PowerShell session transcripts or logs.</span></span>
2. <span data-ttu-id="cc450-116">**Aggiornare** l'uso degli strumenti della riga di comando per renderli equivalenti, se possibile, a quelli di PowerShell, per un miglior controllo e una migliore esperienza di personalizzazione di JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-116">**Update** use of command line tools to PowerShell equivalents, where possible, for the best auditing and JEA customization experience.</span></span> <span data-ttu-id="cc450-117">I programmi esterni non possono essere vincolati in modo granulare come le funzioni e i cmdlet nativi di PowerShell in JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-117">External programs cannot be constrained as granularly as native PowerShell cmdlets and functions in JEA.</span></span>
3. <span data-ttu-id="cc450-118">**Limitare** l'ambito dei cmdlet, se necessario, per consentire solo parametri o valori di parametri specifici.</span><span class="sxs-lookup"><span data-stu-id="cc450-118">**Restrict** the scope of the cmdlets if necessary to only allow specific parameters or parameter values.</span></span> <span data-ttu-id="cc450-119">Ciò è particolarmente importante nel caso in cui gli utenti debbano gestire solo parte di un sistema.</span><span class="sxs-lookup"><span data-stu-id="cc450-119">This is particularly important if users should only be able to manage part of a system.</span></span>
4. <span data-ttu-id="cc450-120">**Creare** funzioni personalizzate per sostituire i comandi complessi o difficili da vincolare in JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-120">**Create** custom functions to replace complex commands or commands which are difficult to constrain in JEA.</span></span> <span data-ttu-id="cc450-121">Una funzione semplice che esegue il wrapping di un comando complesso o applica una logica di convalida aggiuntiva può offrire un controllo maggiore agli amministratori e agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="cc450-121">A simple function that wraps a complex command or applies additional validation logic can offer additional control for admins and end-user simplicity.</span></span>
5. <span data-ttu-id="cc450-122">**Testare** l'elenco relativo all'ambito di comandi consentiti per utenti e/o servizi di automazione e apportare le modifiche necessarie.</span><span class="sxs-lookup"><span data-stu-id="cc450-122">**Test** the scoped list of allowable commands with your users and/or automation services and adjust as necessary.</span></span>

<span data-ttu-id="cc450-123">È importante ricordare che i comandi in una sessione JEA sono spesso eseguiti con privilegi amministrativi o comunque elevati.</span><span class="sxs-lookup"><span data-stu-id="cc450-123">It is important to remember that commands in a JEA session are often run with admin (or otherwise elevated) privileges.</span></span>
<span data-ttu-id="cc450-124">Un'attenta selezione dei comandi disponibili è importante per garantire che l'endpoint JEA non consenta all'utente che si connette di elevare le proprie autorizzazioni.</span><span class="sxs-lookup"><span data-stu-id="cc450-124">Careful selection of available commands is important to ensure the JEA endpoint does not allow the connecting user to elevate their permissions.</span></span>
<span data-ttu-id="cc450-125">Di seguito sono riportati alcuni esempi di comandi che possono essere usati maliziosamente in uno stato non vincolato.</span><span class="sxs-lookup"><span data-stu-id="cc450-125">Below are some examples of commands that can be used maliciously if allowed in an unconstrained state.</span></span>
<span data-ttu-id="cc450-126">Si noti che questo non è un elenco completo e deve essere usato solo come punto di partenza per l'analisi.</span><span class="sxs-lookup"><span data-stu-id="cc450-126">Note that this is not an exhaustive list and should only be used as a cautionary starting point.</span></span>

### <a name="examples-of-potentially-dangerous-commands"></a><span data-ttu-id="cc450-127">Esempi di comandi potenzialmente pericolosi</span><span class="sxs-lookup"><span data-stu-id="cc450-127">Examples of potentially dangerous commands</span></span>

<span data-ttu-id="cc450-128">Rischio</span><span class="sxs-lookup"><span data-stu-id="cc450-128">Risk</span></span> | <span data-ttu-id="cc450-129">Esempio</span><span class="sxs-lookup"><span data-stu-id="cc450-129">Example</span></span> | <span data-ttu-id="cc450-130">Comandi correlati</span><span class="sxs-lookup"><span data-stu-id="cc450-130">Related commands</span></span>
-----|---------|-----------------
<span data-ttu-id="cc450-131">Concessione dei privilegi di amministratore all'utente che si connette per ignorare JEA</span><span class="sxs-lookup"><span data-stu-id="cc450-131">Granting the connecting user admin privileges to bypass JEA</span></span> | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | <span data-ttu-id="cc450-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span><span class="sxs-lookup"><span data-stu-id="cc450-132">`Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`</span></span>
<span data-ttu-id="cc450-133">Esecuzione di codice arbitrario, ad esempio malware, attacchi o script personalizzati per ignorare le protezioni</span><span class="sxs-lookup"><span data-stu-id="cc450-133">Running arbitrary code, such as malware, exploits, or custom scripts to bypass protections</span></span> | `Start-Process -FilePath '\\san\share\malware.exe'` | <span data-ttu-id="cc450-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span><span class="sxs-lookup"><span data-stu-id="cc450-134">`Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`</span></span>

## <a name="create-a-role-capability-file"></a><span data-ttu-id="cc450-135">Creare un file delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="cc450-135">Create a role capability file</span></span>

<span data-ttu-id="cc450-136">È possibile creare un nuovo file delle funzionalità del ruolo di PowerShell con il cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).</span><span class="sxs-lookup"><span data-stu-id="cc450-136">You can create a new PowerShell role capability file with the [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile) cmdlet.</span></span>

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

<span data-ttu-id="cc450-137">Il file delle funzionalità del ruolo creato può essere aperto in un editor di testo e modificato per consentire i comandi appropriati per il ruolo.</span><span class="sxs-lookup"><span data-stu-id="cc450-137">The resulting role capability file can be opened in a text editor and modified to allow the desired commands for the role.</span></span>
<span data-ttu-id="cc450-138">La documentazione della Guida di PowerShell contiene molti esempi su come configurare il file.</span><span class="sxs-lookup"><span data-stu-id="cc450-138">The PowerShell help documentation contains several examples of how you can configure the file.</span></span>

### <a name="allowing-powershell-cmdlets-and-functions"></a><span data-ttu-id="cc450-139">Consentire l'uso di funzioni e i cmdlet di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc450-139">Allowing PowerShell cmdlets and functions</span></span>

<span data-ttu-id="cc450-140">Per autorizzare gli utenti a eseguire i cmdlet o le funzioni di PowerShell, aggiungere il nome del cmdlet o della funzione nei campi VisibleCmdlets o VisibleFunctions.</span><span class="sxs-lookup"><span data-stu-id="cc450-140">To authorize users to run PowerShell cmdlets or functions, add the cmdlet or function name to the VisibleCmdlets or VisibleFunctions fields.</span></span>
<span data-ttu-id="cc450-141">Nel caso in cui non si è certi se un comando è una funzione o un cmdlet, è possibile eseguire `Get-Command <name>` e verificare la proprietà "CommandType" nell'output.</span><span class="sxs-lookup"><span data-stu-id="cc450-141">If you aren't sure whether a command is a cmdlet or function, you can run `Get-Command <name>` and check the "CommandType" property in the output.</span></span>

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

<span data-ttu-id="cc450-142">In alcuni casi l'ambito di una funzione o di cmdlet specifico è troppo esteso per le esigenze degli utenti.</span><span class="sxs-lookup"><span data-stu-id="cc450-142">Sometimes the scope of a specific cmdlet or function is too broad for your users' needs.</span></span>
<span data-ttu-id="cc450-143">Un amministratore DNS, ad esempio, deve probabilmente solo accedere per riavviare il servizio DNS.</span><span class="sxs-lookup"><span data-stu-id="cc450-143">A DNS admin, for example, probably only needs access to restart the DNS service.</span></span>
<span data-ttu-id="cc450-144">In un ambiente multi-tenant dove i tenant hanno accesso agli strumenti di gestione self-service, questi dovrebbero essere limitati alla gestione con le proprie risorse.</span><span class="sxs-lookup"><span data-stu-id="cc450-144">In a multi-tenant environment where tenants are granted access to self-service management tools, tenants should be limited to managing with their own resources.</span></span>
<span data-ttu-id="cc450-145">In questi casi, è possibile limitare i parametri offerti dal cmdlet o dalla funzione.</span><span class="sxs-lookup"><span data-stu-id="cc450-145">For these cases, you can restrict which parameters are exposed from the cmdlet or function.</span></span>

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

<span data-ttu-id="cc450-146">Negli scenari più avanzati, è necessario anche limitare i valori che un utente può specificare per tali parametri.</span><span class="sxs-lookup"><span data-stu-id="cc450-146">In more advanced scenarios, you may also need to restrict which values someone can supply to these parameters.</span></span>
<span data-ttu-id="cc450-147">Le funzionalità del ruolo consentono di definire un set di valori consentiti o un modello di espressione regolare che viene valutato per determinare se è consentito un input specifico.</span><span class="sxs-lookup"><span data-stu-id="cc450-147">Role capabilities let you define a set of allowed values or a regular expression pattern that is evaluated to determine if a given input is allowed.</span></span>

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> <span data-ttu-id="cc450-148">I [parametri comuni di PowerShell](https://technet.microsoft.com/library/hh847884.aspx) sono sempre consentiti, anche se si limita la disponibilità dei parametri.</span><span class="sxs-lookup"><span data-stu-id="cc450-148">The [common PowerShell parameters](https://technet.microsoft.com/library/hh847884.aspx) are always allowed, even if you restrict the available parameters.</span></span>
> <span data-ttu-id="cc450-149">È consigliabile non elencarli in maniera esplicita nel campo Parameters.</span><span class="sxs-lookup"><span data-stu-id="cc450-149">You should not explicitly list them in the Parameters field.</span></span>

<span data-ttu-id="cc450-150">La tabella seguente illustra le varie modalità per personalizzare una funzione o un cmdlet visibile.</span><span class="sxs-lookup"><span data-stu-id="cc450-150">The table below describes the various ways you can customize a visible cmdlet or function.</span></span>
<span data-ttu-id="cc450-151">È possibile combinare le varie modalità descritte di seguito nel campo VisibleCmdlets.</span><span class="sxs-lookup"><span data-stu-id="cc450-151">You can mix and match any of the below in the VisibleCmdlets field.</span></span>

<span data-ttu-id="cc450-152">Esempio</span><span class="sxs-lookup"><span data-stu-id="cc450-152">Example</span></span>                                                                                      | <span data-ttu-id="cc450-153">Caso d'uso</span><span class="sxs-lookup"><span data-stu-id="cc450-153">Use case</span></span>
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
<span data-ttu-id="cc450-154">`'My-Func'` o `@{ Name = 'My-Func' }`</span><span class="sxs-lookup"><span data-stu-id="cc450-154">`'My-Func'` or `@{ Name = 'My-Func' }`</span></span>                                                       | <span data-ttu-id="cc450-155">Consente all'utente di eseguire `My-Func` senza limitazioni sui parametri.</span><span class="sxs-lookup"><span data-stu-id="cc450-155">Allows the user to run `My-Func` without any restrictions on the parameters.</span></span>
`'MyModule\My-Func'`                                                                         | <span data-ttu-id="cc450-156">Consente all'utente di eseguire `My-Func` dal modulo `MyModule` senza limitazioni sui parametri.</span><span class="sxs-lookup"><span data-stu-id="cc450-156">Allows the user to run `My-Func` from the module `MyModule` without any restrictions on the parameters.</span></span>
`'My-*'`                                                                                     | <span data-ttu-id="cc450-157">Consente all'utente di eseguire qualsiasi cmdlet o funzione con il verbo `My`.</span><span class="sxs-lookup"><span data-stu-id="cc450-157">Allows the user to run any cmdlet or function with the verb `My`.</span></span>
`'*-Func'`                                                                                   | <span data-ttu-id="cc450-158">Consente all'utente di eseguire qualsiasi cmdlet o funzione con il sostantivo `Func`.</span><span class="sxs-lookup"><span data-stu-id="cc450-158">Allows the user to run any cmdlet or function with the noun `Func`.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | <span data-ttu-id="cc450-159">Consente all'utente di eseguire `My-Func` con il parametro `Param1` e/o `Param2`.</span><span class="sxs-lookup"><span data-stu-id="cc450-159">Allows the user to run `My-Func` with the `Param1` and/or `Param2` parameters.</span></span> <span data-ttu-id="cc450-160">È possibile specificare qualsiasi valore per i parametri.</span><span class="sxs-lookup"><span data-stu-id="cc450-160">Any value can be supplied to the parameters.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | <span data-ttu-id="cc450-161">Consente all'utente di eseguire `My-Func` con il parametro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="cc450-161">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="cc450-162">Solo "Value1" e "Value2" possono essere specificati per il parametro.</span><span class="sxs-lookup"><span data-stu-id="cc450-162">Only "Value1" and "Value2" can be supplied to the parameter.</span></span>
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | <span data-ttu-id="cc450-163">Consente all'utente di eseguire `My-Func` con il parametro `Param1`.</span><span class="sxs-lookup"><span data-stu-id="cc450-163">Allows the user to run `My-Func` with the `Param1` parameter.</span></span> <span data-ttu-id="cc450-164">Per il parametro può essere specificato qualsiasi valore che inizia con "contoso".</span><span class="sxs-lookup"><span data-stu-id="cc450-164">Any value starting with "contoso" can be supplied to the parameter.</span></span>

> [!WARNING]
> <span data-ttu-id="cc450-165">In base alle procedure consigliate sulla sicurezza, è consigliabile non usare caratteri jolly nella definizione di cmdlet o funzioni visibili.</span><span class="sxs-lookup"><span data-stu-id="cc450-165">For best security practices, it is not recommended to use wildcards when defining visible cmdlets or functions.</span></span>
> <span data-ttu-id="cc450-166">In alternativa, è necessario elencare in modo esplicito ogni comando attendibile per assicurarsi che nessun altro comando che condivide lo stesso schema di denominazione venga involontariamente autorizzato.</span><span class="sxs-lookup"><span data-stu-id="cc450-166">Instead, you should explicitly list each trusted command to ensure no other commands that share the same naming scheme are unintentionally authorized.</span></span>

<span data-ttu-id="cc450-167">Non è possibile applicare un ValidatePattern e ValidateSet allo stesso cmdlet o funzione.</span><span class="sxs-lookup"><span data-stu-id="cc450-167">You cannot apply both a ValidatePattern and ValidateSet to the same cmdlet or function.</span></span>

<span data-ttu-id="cc450-168">In caso contrario, il ValidatePattern sostituirà il ValidateSet.</span><span class="sxs-lookup"><span data-stu-id="cc450-168">If you do, the ValidatePattern will override the ValidateSet.</span></span>

<span data-ttu-id="cc450-169">Per altre informazioni su ValidatePattern, vedere [questo post *Hey, Scripting Guy!*](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e il contenuto dei riferimenti [Espressioni regolari di PowerShell](https://technet.microsoft.com/library/hh847880.aspx).</span><span class="sxs-lookup"><span data-stu-id="cc450-169">For more information about ValidatePattern, check out [this *Hey, Scripting Guy!* post](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) and the [PowerShell Regular Expressions](https://technet.microsoft.com/library/hh847880.aspx) reference content.</span></span>

### <a name="allowing-external-commands-and-powershell-scripts"></a><span data-ttu-id="cc450-170">Consentire l'uso di comandi esterni e degli script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc450-170">Allowing external commands and PowerShell scripts</span></span>

<span data-ttu-id="cc450-171">Per consentire agli utenti di usare file eseguibili e script di PowerShell (ps1) in una sessione JEA, è necessario aggiungere il percorso completo per ogni programma nel campo VisibleExternalCommands.</span><span class="sxs-lookup"><span data-stu-id="cc450-171">To allow users to run executables and PowerShell scripts (.ps1) in a JEA session, you have to add the full path to each program in the VisibleExternalCommands field.</span></span>

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

<span data-ttu-id="cc450-172">È consigliabile, se possibile, usare i cmdlet e le funzioni equivalenti di PowerShell di tutti i file eseguibili esterni autorizzati dal momento che si ha il controllo sui parametri consentiti con le funzioni e i cmdlet di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc450-172">It is advised, where possible, to use PowerShell cmdlet/function equivalents of any external executables you authorize since you have control over which parameters are allowed with PowerShell cmdlets/functions.</span></span>

<span data-ttu-id="cc450-173">Molti file eseguibili consentono di leggere lo stato attuale e quindi modificarlo specificando parametri diversi.</span><span class="sxs-lookup"><span data-stu-id="cc450-173">Many executables allow you to both read the current state and then change it just by providing different parameters.</span></span>

<span data-ttu-id="cc450-174">Si consideri ad esempio il ruolo di amministratore di un file server che vuole controllare quali condivisioni di rete sono ospitate dal computer locale.</span><span class="sxs-lookup"><span data-stu-id="cc450-174">For example, consider the role of a file server admin who wants to check which network shares are hosted by the local machine.</span></span>
<span data-ttu-id="cc450-175">Un modo per eseguire questa operazione è usare `net share`.</span><span class="sxs-lookup"><span data-stu-id="cc450-175">One way to check is to use `net share`.</span></span>
<span data-ttu-id="cc450-176">Consentire tuttavia l'uso di net.exe è molto pericoloso perché l'amministratore potrebbe facilmente usare il comando per ottenere privilegi di amministratore con `net group Administrators unprivilegedjeauser /add`.</span><span class="sxs-lookup"><span data-stu-id="cc450-176">However, allowing net.exe is very dangerous because the admin could just as easily use the command to gain admin privileges with `net group Administrators unprivilegedjeauser /add`.</span></span>
<span data-ttu-id="cc450-177">Un approccio migliore consiste nell'usare [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) che consente di ottenere lo stesso risultato, ma ha un ambito più ristretto.</span><span class="sxs-lookup"><span data-stu-id="cc450-177">A better approach is to allow [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) which achieves the same result but has a much more limited scope.</span></span>

<span data-ttu-id="cc450-178">Quando si rendono disponibili comandi esterni per gli utenti di una sessione JEA, specificare sempre il percorso completo del file eseguibile per assicurarsi che non venga eseguito un programma denominato in modo analogo (e potenzialmente pericoloso) che si trova in un'altra posizione nel sistema.</span><span class="sxs-lookup"><span data-stu-id="cc450-178">When making external commands available to users in a JEA session, always specify the complete path to the executable to ensure a similarly named (and potentially malicious) program placed elsewhere on the system does not get executed instead.</span></span>

### <a name="allowing-access-to-powershell-providers"></a><span data-ttu-id="cc450-179">Consentire accesso ai provider di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cc450-179">Allowing access to PowerShell providers</span></span>

<span data-ttu-id="cc450-180">Per impostazione predefinita, non sono disponibili provider di PowerShell nelle sessioni JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-180">By default, no PowerShell providers are available in JEA sessions.</span></span>

<span data-ttu-id="cc450-181">In questo modo si riduce il rischio di accesso a informazioni sensibili e alle impostazioni di configurazione da parte dell'utente che si connette.</span><span class="sxs-lookup"><span data-stu-id="cc450-181">This is primarily to reduce the risk of sensitive information and configuration settings being disclosed to the connecting user.</span></span>

<span data-ttu-id="cc450-182">Se necessario, è possibile consentire l'accesso ai provider di PowerShell usando il comando `VisibleProviders`.</span><span class="sxs-lookup"><span data-stu-id="cc450-182">When necessary, you can allow access to the PowerShell providers using the `VisibleProviders` command.</span></span>
<span data-ttu-id="cc450-183">Per un elenco completo dei provider, eseguire `Get-PSProvider`.</span><span class="sxs-lookup"><span data-stu-id="cc450-183">For a full list of providers, run `Get-PSProvider`.</span></span>

```powershell
VisibleProviders = 'Registry'
```

<span data-ttu-id="cc450-184">Per eseguire semplici operazioni che richiedono l'accesso al file system, al Registro di sistema, all'archivio dei certificati o ad altri provider sensibili, è anche possibile scrivere una funzione personalizzata che interagisca con il provider per conto dell'utente.</span><span class="sxs-lookup"><span data-stu-id="cc450-184">For simple tasks that require access to the file system, registry, certificate store, or other sensitive providers, you can also consider writing a custom function that works with the provider on the user's behalf.</span></span>
<span data-ttu-id="cc450-185">Le funzioni, i cmdlet e i programmi esterni disponibili in una sessione JEA non sono soggetti agli stessi vincoli di JEA e possono accedere a qualsiasi provider per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="cc450-185">Functions, cmdlets, and external programs that are available in a JEA session are not subject to the same constraints as JEA -- they can access any provider by default.</span></span>
<span data-ttu-id="cc450-186">Si consideri anche l'uso dell'[unità utente](session-configurations.md#user-drive) quando è necessario copiare file da o in un endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-186">Also consider using the [user drive](session-configurations.md#user-drive) when copying files to/from a JEA endpoint is required.</span></span>

### <a name="creating-custom-functions"></a><span data-ttu-id="cc450-187">Creazione di funzioni personalizzate</span><span class="sxs-lookup"><span data-stu-id="cc450-187">Creating custom functions</span></span>

<span data-ttu-id="cc450-188">È possibile creare funzioni personalizzate in un file delle funzionalità del ruolo per semplificare attività complesse per gli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="cc450-188">You can author custom functions in a role capability file to simplify complex tasks for your end users.</span></span>
<span data-ttu-id="cc450-189">Le funzioni personalizzate sono utili anche quando è necessaria una logica di convalida avanzata per i valori dei parametri dei cmdlet.</span><span class="sxs-lookup"><span data-stu-id="cc450-189">Custom functions are also useful when you require advanced validation logic for cmdlet parameter values.</span></span>
<span data-ttu-id="cc450-190">È possibile scrivere funzioni semplici nel campo **FunctionDefinitions**:</span><span class="sxs-lookup"><span data-stu-id="cc450-190">You can write simple functions in the **FunctionDefinitions** field:</span></span>

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> <span data-ttu-id="cc450-191">Non dimenticare di aggiungere il nome delle funzioni personalizzate per il campo **VisibleFunctions** in modo che possano essere eseguite dagli utenti JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-191">Don't forget to add the name of your custom functions to the **VisibleFunctions** field so they can be run by the JEA users.</span></span>

<span data-ttu-id="cc450-192">Il corpo (blocco di script) di funzioni personalizzate viene eseguito nella modalità linguaggio predefinita per il sistema e non è soggetto ai vincoli di linguaggio di JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-192">The body (script block) of custom functions runs in the default language mode for the system and is not subject to JEA's language constraints.</span></span>
<span data-ttu-id="cc450-193">Ciò significa che le funzioni possono accedere al file system e al Registro di sistema ed eseguire comandi che non sono stati resi visibili nel file delle funzionalità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="cc450-193">This means that functions can access the file system and registry, and run commands that were not made visible in the role capability file.</span></span>
<span data-ttu-id="cc450-194">Evitare l'esecuzione di codice arbitrario quando si usano parametri ed evitare il piping dell'input dell'utente direttamente nei cmdlet, ad esempio `Invoke-Expression`.</span><span class="sxs-lookup"><span data-stu-id="cc450-194">Take care to avoid allowing arbitrary code to be run when using parameters and avoid piping user input directly into cmdlets like `Invoke-Expression`.</span></span>

<span data-ttu-id="cc450-195">Nell'esempio precedente, si noterà che è stato usato il nome del modulo qualificato completo (FQMN) `Microsoft.PowerShell.Utility\Select-Object`al posto della sintassi abbreviata`Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="cc450-195">In the above example, you will notice that the fully qualified module name (FQMN) `Microsoft.PowerShell.Utility\Select-Object` was used instead of the shorthand `Select-Object`.</span></span>
<span data-ttu-id="cc450-196">Le funzioni definite nei file delle funzionalità del ruolo sono comunque soggette all'ambito delle sessioni JEA, che include le funzioni proxy che JEA crea per vincolare i comandi esistenti.</span><span class="sxs-lookup"><span data-stu-id="cc450-196">Functions defined in role capability files are still subject to the scope of JEA sessions, which includes the proxy functions JEA creates to constrain existing commands.</span></span>

<span data-ttu-id="cc450-197">Select-Object è un'impostazione predefinita, un cmdlet vincolato in tutte le sessioni JEA che non consente di selezionare le proprietà arbitrarie in oggetti.</span><span class="sxs-lookup"><span data-stu-id="cc450-197">Select-Object is a default, constrained cmdlet in all JEA sessions that doesn't allow you to select arbitrary properties on objects.</span></span>
<span data-ttu-id="cc450-198">Per usare Select-Object non vincolato in funzioni, è necessario richiedere in modo esplicito l'implementazione completa, specificando il nome FQMN.</span><span class="sxs-lookup"><span data-stu-id="cc450-198">To use the unconstrained Select-Object in functions, you must explicitly request the full implementation by specifying the FQMN.</span></span>
<span data-ttu-id="cc450-199">Tutti i cmdlet vincolati in una sessione JEA hanno lo stesso comportamento se chiamati da una funzione, in linea con la [precedenza dei comandi](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc450-199">Any constrained cmdlet in a JEA session will exhibit the same behavior when invoked from a function, in line with PowerShell's [command precedence](https://msdn.microsoft.com/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence).</span></span>

<span data-ttu-id="cc450-200">Se si creano molte funzioni personalizzate, potrebbe risultare più facile inserirle in un [modulo di script di PowerShell](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="cc450-200">If you are writing a lot of custom functions, it may be easier to put them in a [PowerShell Script Module](https://msdn.microsoft.com/library/dd878340(v=vs.85).aspx).</span></span>
<span data-ttu-id="cc450-201">È possibile quindi rendere tali funzioni visibili nella sessione JEA tramite il campo VisibleFunctions, così come si farebbe con i moduli incorporati e di terze parti.</span><span class="sxs-lookup"><span data-stu-id="cc450-201">You can then make those functions visible in the JEA session using the VisibleFunctions field like you would with built-in and third party modules.</span></span>

<span data-ttu-id="cc450-202">Per il corretto funzionamento del completamento alla pressione del tasto TAB nelle sessioni JEA, è necessario includere la funzione predefinita `tabexpansion2` nell'elenco **VisibleFunctions**.</span><span class="sxs-lookup"><span data-stu-id="cc450-202">For tab completion to work properly in JEA sessions you must include the built-in function `tabexpansion2` in the **VisibleFunctions** list.</span></span>

## <a name="place-role-capabilities-in-a-module"></a><span data-ttu-id="cc450-203">Inserire le funzionalità del ruolo in un modulo</span><span class="sxs-lookup"><span data-stu-id="cc450-203">Place role capabilities in a module</span></span>

<span data-ttu-id="cc450-204">Per fare in modo che PowerShell trovi il file delle funzionalità del ruolo, è necessario inserire il file in una cartella "RoleCapabilities" in un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc450-204">In order for PowerShell to find a role capability file, it must be stored in a "RoleCapabilities" folder in a PowerShell module.</span></span>
<span data-ttu-id="cc450-205">Il modulo può essere archiviato in qualsiasi cartella inclusa nella variabile di ambiente `$env:PSModulePath`, tuttavia non deve essere collocato in System32 (riservato per i moduli predefiniti) o in una cartella in cui gli utenti non attendibili che si connettono possano modificare i file.</span><span class="sxs-lookup"><span data-stu-id="cc450-205">The module can be stored in any folder included in the `$env:PSModulePath` environment variable, however you should not place it in System32 (reserved for built-in modules) or a folder where the untrusted, connecting users could modify the files.</span></span>
<span data-ttu-id="cc450-206">Di seguito è riportato un esempio di creazione di un modulo di script di PowerShell di base denominato *ContosoJEA* nel percorso "Programmi".</span><span class="sxs-lookup"><span data-stu-id="cc450-206">Below is an example of creating a basic PowerShell script module called *ContosoJEA* in the "Program Files" path.</span></span>

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

<span data-ttu-id="cc450-207">Per altre informazioni sui moduli di PowerShell, sui manifesti dei moduli e sulla variabile di ambiente PSModulePath, vedere [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) (Informazioni sui moduli di PowerShell).</span><span class="sxs-lookup"><span data-stu-id="cc450-207">See [Understanding a PowerShell Module](https://msdn.microsoft.com/library/dd878324.aspx) for more information about PowerShell modules, module manifests, and the PSModulePath environment variable.</span></span>

## <a name="updating-role-capabilities"></a><span data-ttu-id="cc450-208">Aggiornamento delle funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="cc450-208">Updating role capabilities</span></span>

<span data-ttu-id="cc450-209">È possibile aggiornare un file delle funzionalità del ruolo in qualsiasi momento semplicemente salvando le modifiche.</span><span class="sxs-lookup"><span data-stu-id="cc450-209">You can update a role capability file at any time by simply saving changes to the role capability file.</span></span>
<span data-ttu-id="cc450-210">Ogni nuova sessione JEA avviata dopo l'aggiornamento delle funzionalità del ruolo includerà le funzionalità modificate.</span><span class="sxs-lookup"><span data-stu-id="cc450-210">Any new JEA sessions started after the role capability has been updated will reflect the revised capabilities.</span></span>

<span data-ttu-id="cc450-211">Per questo motivo il controllo dell'accesso alla cartella delle funzionalità del ruolo è molto importante.</span><span class="sxs-lookup"><span data-stu-id="cc450-211">This is why controlling access to the role capabilities folder is so important.</span></span>
<span data-ttu-id="cc450-212">Solo gli amministratori estremamente attendibili dovrebbero aver accesso per modificare i file delle funzionalità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="cc450-212">Only highly trusted administrators should be able to change role capability files.</span></span>
<span data-ttu-id="cc450-213">Se un utente non attendibile può modificare i file delle funzionalità del ruolo, sarà in grado di ottenere accesso ai cmdlet che consentono di elevare i privilegi.</span><span class="sxs-lookup"><span data-stu-id="cc450-213">If an untrusted user can change role capability files, they can easily give themselves access to cmdlets which allow them to elevate their privileges.</span></span>

<span data-ttu-id="cc450-214">Gli amministratori che vogliono bloccare l'accesso alle funzionalità del ruolo devono assicurarsi che il sistema locale abbia accesso di lettura ai file delle funzionalità del ruolo e ai moduli inclusi.</span><span class="sxs-lookup"><span data-stu-id="cc450-214">For administrators looking to lock down access to the role capabilities, ensure Local System has read access to the role capability files and containing modules.</span></span>

## <a name="how-role-capabilities-are-merged"></a><span data-ttu-id="cc450-215">Come vengono uniti le funzionalità del ruolo</span><span class="sxs-lookup"><span data-stu-id="cc450-215">How role capabilities are merged</span></span>

<span data-ttu-id="cc450-216">È possibile concedere agli utenti accesso a più funzionalità del ruolo quando accedono a una sessione JEA a seconda dei mapping del ruolo nel [file di configurazione sessione](session-configurations.md).</span><span class="sxs-lookup"><span data-stu-id="cc450-216">Users can be granted access to multiple role capabilities when they enter a JEA session depending on the role mappings in the [session configuration file](session-configurations.md).</span></span>
<span data-ttu-id="cc450-217">In questo caso, JEA prova ad assegnare all'utente il set di comandi *più permissivo* consentito da uno dei ruoli.</span><span class="sxs-lookup"><span data-stu-id="cc450-217">When this happens, JEA tries to give the user the *most permissive* set of commands allowed by any of the roles.</span></span>

<span data-ttu-id="cc450-218">**VisibleCmdlets e VisibleFunctions**</span><span class="sxs-lookup"><span data-stu-id="cc450-218">**VisibleCmdlets and VisibleFunctions**</span></span>

<span data-ttu-id="cc450-219">La logica di unione più complessa influisce su cmdlet e funzioni, che possono avere i parametri e i valori di parametro limitati in JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-219">The most complex merge logic affects cmdlets and functions, which can have their parameters and parameter values limited in JEA.</span></span>

<span data-ttu-id="cc450-220">Di seguito vengono definite le regole:</span><span class="sxs-lookup"><span data-stu-id="cc450-220">The rules are as follows:</span></span>

1. <span data-ttu-id="cc450-221">Se un cmdlet viene reso visibile solo in un ruolo, sarà visibile all'utente con i vincoli del parametro applicabile.</span><span class="sxs-lookup"><span data-stu-id="cc450-221">If a cmdlet is only made visible in one role, it will be visible to the user with any applicable parameter constraints.</span></span>
2. <span data-ttu-id="cc450-222">Se un cmdlet viene reso visibile in più di un ruolo e ogni ruolo ha gli stessi vincoli sul cmdlet, il cmdlet sarà visibile all'utente con tali vincoli.</span><span class="sxs-lookup"><span data-stu-id="cc450-222">If a cmdlet is made visible in more than one role, and each role has the same constraints on the cmdlet, the cmdlet will be visible to the user with those constraints.</span></span>
3. <span data-ttu-id="cc450-223">Se un cmdlet viene reso visibile in più di un ruolo e ogni ruolo consente un set diverso di parametri, il cmdlet e tutti i parametri definiti in ogni ruolo saranno visibili all'utente.</span><span class="sxs-lookup"><span data-stu-id="cc450-223">If a cmdlet is made visible in more than one role, and each role allows a different set of parameters, the cmdlet and all of the parameters defined across every role will be visible to the user.</span></span> <span data-ttu-id="cc450-224">Se un ruolo non ha vincoli sui parametri, tutti i parametri saranno consentiti.</span><span class="sxs-lookup"><span data-stu-id="cc450-224">If one role doesn't have constraints on the parameters, all parameters will be allowed.</span></span>
4. <span data-ttu-id="cc450-225">Se un ruolo definisce un set di convalida o un modello di convalida per un parametro di cmdlet e l'altro ruolo consente il parametro, ma non vincola i valori del parametro, il set di convalida o il modello verrà ignorato.</span><span class="sxs-lookup"><span data-stu-id="cc450-225">If one role defines a validate set or validate pattern for a cmdlet parameter, and the other role allows the parameter but does not constrain the parameter values, the validate set or pattern will be ignored.</span></span>
5. <span data-ttu-id="cc450-226">Se viene definito un set di convalida per lo stesso parametro del cmdlet in più di un ruolo, saranno consentiti tutti i valori da tutti i set di convalida.</span><span class="sxs-lookup"><span data-stu-id="cc450-226">If a validate set is defined for the same cmdlet parameter in more than one role, all values from all validate sets will be allowed.</span></span>
6. <span data-ttu-id="cc450-227">Se viene definito un modello di convalida per lo stesso parametro del cmdlet in più di un ruolo, saranno consentiti tutti i valori che corrispondono ai modelli.</span><span class="sxs-lookup"><span data-stu-id="cc450-227">If a validate pattern is defined for the same cmdlet parameter in more than one role, any values that match any of the patterns will be allowed.</span></span>
7. <span data-ttu-id="cc450-228">Se viene definito un set di convalida in uno o più ruoli e un modello di convalida è definito in un altro ruolo per lo stesso parametro del cmdlet, il set di convalida viene ignorato e si applica la regola (6) ai modelli di convalida rimanenti.</span><span class="sxs-lookup"><span data-stu-id="cc450-228">If a validate set is defined in one or more roles, and a validate pattern is defined in another role for the same cmdlet parameter, the validate set is ignored and rule (6) applies to the remaining validate patterns.</span></span>

<span data-ttu-id="cc450-229">Di seguito è riportato un esempio di come i ruoli vengono uniti in base a queste regole:</span><span class="sxs-lookup"><span data-stu-id="cc450-229">Below is an example of how roles are merged according to these rules:</span></span>

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permissions for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored because of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```

<span data-ttu-id="cc450-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span><span class="sxs-lookup"><span data-stu-id="cc450-230">**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**</span></span>

<span data-ttu-id="cc450-231">Tutti gli altri campi nel file delle funzionalità del ruolo vengono aggiunti a un set cumulativo di comandi esterni consentiti, alias, provider e script di avvio.</span><span class="sxs-lookup"><span data-stu-id="cc450-231">All other fields in the role capability file are simply added to a cumulative set of allowable external commands, aliases, providers, and startup scripts.</span></span>
<span data-ttu-id="cc450-232">Qualsiasi comando, alias, provider o script disponibile in una funzionalità del ruolo sarà disponibile per l'utente JEA.</span><span class="sxs-lookup"><span data-stu-id="cc450-232">Any command, alias, provider, or script available in one role capability will be available to the JEA user.</span></span>

<span data-ttu-id="cc450-233">Accertarsi che il set combinato di provider da una sola funzionalità del ruoli e i cmdlet/funzioni/comandi da un'altra funzionalità non consentano agli utenti che si connettono di accedere non intenzionalmente alle risorse di sistema.</span><span class="sxs-lookup"><span data-stu-id="cc450-233">Be careful to ensure that the combined set of providers from one role capability and cmdlets/functions/commands from another do not allow connecting users unintentional access to system resources.</span></span>
<span data-ttu-id="cc450-234">Ad esempio, se un ruolo consente l'uso del cmdlet `Remove-Item` e un altro il provider `FileSystem`, c'è il rischio che un utente JEA possa eliminare file arbitrari nel computer.</span><span class="sxs-lookup"><span data-stu-id="cc450-234">For example, if one role allows the `Remove-Item` cmdlet and another allows the `FileSystem` provider, you are at risk of a JEA user deleting arbitrary files on your computer.</span></span>
<span data-ttu-id="cc450-235">Altre informazioni sull'identificazione delle autorizzazioni effettive degli utenti sono disponibili nell'[argomento Controllo di JEA](audit-and-report.md).</span><span class="sxs-lookup"><span data-stu-id="cc450-235">Additional information about identifying users' effective permissions can be found in the [auditing JEA topic](audit-and-report.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="cc450-236">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="cc450-236">Next steps</span></span>

- [<span data-ttu-id="cc450-237">Creare un file di configurazione sessione</span><span class="sxs-lookup"><span data-stu-id="cc450-237">Create a session configuration file</span></span>](session-configurations.md)
