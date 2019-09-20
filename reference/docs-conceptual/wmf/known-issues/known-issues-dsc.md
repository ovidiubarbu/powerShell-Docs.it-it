---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Problemi noti e limitazioni di Desired State Configuration (DSC)
ms.openlocfilehash: 6faf24795d14a93f265943029d9f6f1388f32263
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147721"
---
# <a name="desired-state-configuration-dsc-known-issues-and-limitations"></a><span data-ttu-id="a5bed-103">Problemi noti e limitazioni di Desired State Configuration (DSC)</span><span class="sxs-lookup"><span data-stu-id="a5bed-103">Desired State Configuration (DSC) Known Issues and Limitations</span></span>

## <a name="breaking-change-certificates-used-to-encryptdecrypt-passwords-in-dsc-configurations-may-not-work-after-installing-wmf-50-rtm"></a><span data-ttu-id="a5bed-104">Modifica che causa un'interruzione: è possibile che i certificati usati per crittografare/decrittografare le password nelle configurazioni DSC non funzionino dopo l'installazione di WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="a5bed-104">Breaking Change: Certificates used to encrypt/decrypt passwords in DSC configurations may not work after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="a5bed-105">Nelle versioni WMF 4.0 e WMF 5.0 Preview, DSC non consente lunghezze maggiori di 121 caratteri per le password nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-105">In WMF 4.0 and WMF 5.0 Preview releases, DSC would not allow passwords in the configuration to be of length more than 121 characters.</span></span> <span data-ttu-id="a5bed-106">DSC imponeva l'uso di password brevi anche se erano preferibili password lunghe e complesse.</span><span class="sxs-lookup"><span data-stu-id="a5bed-106">DSC was forcing to use short passwords even if lengthy and strong password was desired.</span></span> <span data-ttu-id="a5bed-107">Questa modifica consente una lunghezza arbitraria per le password nella configurazione DSC.</span><span class="sxs-lookup"><span data-stu-id="a5bed-107">This breaking change allows passwords to be of arbitrary length in the DSC configuration.</span></span>

<span data-ttu-id="a5bed-108">**Soluzione:** creare nuovamente il certificato con utilizzo di chiavi Crittografia dati o Crittografia chiave e utilizzo chiavi avanzato Crittografia documento (1.3.6.1.4.1.311.80.1).</span><span class="sxs-lookup"><span data-stu-id="a5bed-108">**Resolution:** Re-create the certificate with Data Encipherment or Key Encipherment Key usage, and Document Encryption Enhanced Key usage (1.3.6.1.4.1.311.80.1).</span></span> <span data-ttu-id="a5bed-109">Per altre informazioni, vedere [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span><span class="sxs-lookup"><span data-stu-id="a5bed-109">For more information, see [Protect-CmsMessage](/powershell/module/Microsoft.PowerShell.Security/Protect-CmsMessage).</span></span>

## <a name="dsc-cmdlets-may-fail-after-installing-wmf-50-rtm"></a><span data-ttu-id="a5bed-110">Potrebbero verificarsi problemi con i cmdlet DSC dopo l'installazione di WMF 5.0 RTM</span><span class="sxs-lookup"><span data-stu-id="a5bed-110">DSC cmdlets may fail after installing WMF 5.0 RTM</span></span>

<span data-ttu-id="a5bed-111">`Start-DscConfiguration` e altri cmdlet DSC potrebbero non funzionare dopo l'installazione di WMF 5.0 RTM con l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="a5bed-111">`Start-DscConfiguration` and other DSC cmdlets may fail after installing WMF 5.0 RTM with the following error:</span></span>

```Output
LCM failed to retrieve the property PendingJobStep from the object of class dscInternalCache .
+ CategoryInfo : ObjectNotFound: (root/Microsoft/...gurationManager:String) [], CimException
+ FullyQualifiedErrorId : MI RESULT 6
+ PSComputerName : localhost
```

<span data-ttu-id="a5bed-112">**Soluzione:** eliminare DSCEngineCache.mof eseguendo il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="a5bed-112">**Resolution:** Delete DSCEngineCache.mof by running the following command in an elevated PowerShell session (Run as Administrator):</span></span>

```powershell
Remove-Item -Path $env:SystemRoot\system32\Configuration\DSCEngineCache.mof
```

## <a name="dsc-cmdlets-may-not-work-if-wmf-50-rtm-is-installed-on-top-of-wmf-50-production-preview"></a><span data-ttu-id="a5bed-113">I cmdlet DSC potrebbero non funzionare se si installa WMF 5.0 RTM su WMF 5.0 Production Preview</span><span class="sxs-lookup"><span data-stu-id="a5bed-113">DSC cmdlets may not work if WMF 5.0 RTM is installed on top of WMF 5.0 Production Preview</span></span>

<span data-ttu-id="a5bed-114">**Soluzione:** eseguire il comando seguente in una sessione di PowerShell con privilegi elevati (Esegui come amministratore):</span><span class="sxs-lookup"><span data-stu-id="a5bed-114">**Resolution:** Run the following command in an elevated PowerShell session (run as administrator):</span></span>

```powershell
mofcomp $env:windir\system32\wbem\DscCoreConfProv.mof
```

## <a name="lcm-can-go-into-an-unstable-state-while-using-get-dscconfiguration-in-debugmode"></a><span data-ttu-id="a5bed-115">Lo stato di Gestione configurazione locale può diventare instabile durante l'uso di Get-DscConfiguration in DebugMode</span><span class="sxs-lookup"><span data-stu-id="a5bed-115">LCM can go into an unstable state while using Get-DscConfiguration in DebugMode</span></span>

<span data-ttu-id="a5bed-116">Se Gestione configurazione locale è in DebugMode, la pressione di CTRL+C per arrestare l'elaborazione di `Get-DscConfiguration` può causare il passaggio a uno stato instabile per Gestione configurazione locale, nel quale non funzionerà la maggior parte dei cmdlet DSC.</span><span class="sxs-lookup"><span data-stu-id="a5bed-116">If LCM is in DebugMode, pressing CTRL+C to stop the processing of `Get-DscConfiguration` can cause LCM to go into an unstable state such that majority of DSC cmdlets won’t work.</span></span>

<span data-ttu-id="a5bed-117">**Soluzione:** non premere CTRL+C durante il debug del cmdlet `Get-DscConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="a5bed-117">**Resolution:** Don’t press CTRL+C while debugging `Get-DscConfiguration` cmdlet.</span></span>

## <a name="stop-dscconfiguration-may-not-respond-in-debugmode"></a><span data-ttu-id="a5bed-118">Stop-DscConfiguration potrebbe non rispondere in DebugMode</span><span class="sxs-lookup"><span data-stu-id="a5bed-118">Stop-DscConfiguration may not respond in DebugMode</span></span>

<span data-ttu-id="a5bed-119">Se Gestione configurazione locale è in DebugMode, `Stop-DscConfiguration` potrebbe non rispondere durante il tentativo di arrestare un'operazione avviata da `Get-DscConfiguration`</span><span class="sxs-lookup"><span data-stu-id="a5bed-119">If LCM is in DebugMode, `Stop-DscConfiguration` may not respond while trying to stop an operation started by `Get-DscConfiguration`</span></span>

<span data-ttu-id="a5bed-120">**Soluzione:** terminare il debug dell'operazione avviata da `Get-DscConfiguration`, come illustrato in [Debug di risorse DSC](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="a5bed-120">**Resolution:** Finish the debugging of the operation started by `Get-DscConfiguration` as outlined in [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

## <a name="no-verbose-error-messages-are-shown-in-debugmode"></a><span data-ttu-id="a5bed-121">In DebugMode non vengono visualizzati messaggi di errore dettagliati</span><span class="sxs-lookup"><span data-stu-id="a5bed-121">No Verbose Error Messages are shown in DebugMode</span></span>

<span data-ttu-id="a5bed-122">Se Gestione configurazione locale è in **DebugMode**, non viene visualizzato alcun messaggio di errore dettagliato da risorse DSC.</span><span class="sxs-lookup"><span data-stu-id="a5bed-122">If LCM is in **DebugMode**, no verbose error messages are displayed from DSC Resources.</span></span>

<span data-ttu-id="a5bed-123">**Soluzione:** disabilitare **DebugMode** per visualizzare messaggi dettagliati dalla risorsa</span><span class="sxs-lookup"><span data-stu-id="a5bed-123">**Resolution:** Disable **DebugMode** to see verbose messages from the resource</span></span>

## <a name="invoke-dscresource-operations-cannot-be-retrieved-by-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="a5bed-124">Le operazioni Invoke-DscResource non possono essere recuperate dal cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="a5bed-124">Invoke-DscResource operations cannot be retrieved by Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="a5bed-125">Dopo aver usato il cmdlet `Invoke-DscResource` per richiamare direttamente i metodi di qualsiasi risorsa, i record di tale operazione non possono essere recuperati tramite `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="a5bed-125">After using `Invoke-DscResource` cmdlet to directly invoke any resource’s methods, the records of such operation cannot be retrieved through `Get-DscConfigurationStatus`.</span></span>

<span data-ttu-id="a5bed-126">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-126">**Resolution:** None.</span></span>

## <a name="get-dscconfigurationstatus-returns-pull-cycle-operations-as-type-consistency"></a><span data-ttu-id="a5bed-127">Get-DscConfigurationStatus restituisce le operazioni del ciclo di pull come operazioni di tipo **Consistency**</span><span class="sxs-lookup"><span data-stu-id="a5bed-127">Get-DscConfigurationStatus returns pull cycle operations as type **Consistency**</span></span>

<span data-ttu-id="a5bed-128">Quando un nodo viene impostato sulla modalità di aggiornamento PULL, per ogni operazione pull eseguita il cmdlet `Get-DscConfigurationStatus` restituisce **Consistency** invece di *Initial* come tipo di operazione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-128">When a node is set to PULL refresh mode, for each pull operation performed, `Get-DscConfigurationStatus` cmdlet reports the operation type as **Consistency** instead of *Initial*</span></span>

<span data-ttu-id="a5bed-129">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-129">**Resolution:** None.</span></span>

## <a name="invoke-dscresource-cmdlet-does-not-return-message-in-the-order-they-were-produced"></a><span data-ttu-id="a5bed-130">Il cmdlet Invoke-DscResource non restituisce i messaggi nell'ordine di generazione</span><span class="sxs-lookup"><span data-stu-id="a5bed-130">Invoke-DscResource cmdlet does not return message in the order they were produced</span></span>

<span data-ttu-id="a5bed-131">Il cmdlet `Invoke-DscResource` non restituisce i messaggi dettagliati, di avviso e di errore nell'ordine con cui vengono generati da Gestione configurazione locale o dalla risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="a5bed-131">The `Invoke-DscResource` cmdlet does not return verbose, warning, and error messages in the order they were produced by LCM or the DSC resource.</span></span>

<span data-ttu-id="a5bed-132">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-132">**Resolution:** None.</span></span>

## <a name="dsc-resources-cannot-be-debugged-easily-when-used-with-invoke-dscresource"></a><span data-ttu-id="a5bed-133">Non è possibile eseguire facilmente il debug di risorse DSC usate con Invoke-DscResource</span><span class="sxs-lookup"><span data-stu-id="a5bed-133">DSC Resources cannot be debugged easily when used with Invoke-DscResource</span></span>

<span data-ttu-id="a5bed-134">Quando Gestione configurazione locale è in esecuzione in modalità di debug, il cmdlet `Invoke-DscResource` non fornisce informazioni sullo spazio di esecuzione a cui connettersi per il debug.</span><span class="sxs-lookup"><span data-stu-id="a5bed-134">When LCM is running in debug mode, `Invoke-DscResource` cmdlet does not give information about runspace to connect to for debugging.</span></span> <span data-ttu-id="a5bed-135">Per altre informazioni, vedere [Debug di risorse DSC](/powershell/dsc/troubleshooting/debugResource).</span><span class="sxs-lookup"><span data-stu-id="a5bed-135">For more information, see [Debugging DSC resources](/powershell/dsc/troubleshooting/debugResource).</span></span>

<span data-ttu-id="a5bed-136">**Soluzione:** Individuare e associare lo spazio di esecuzione usando i cmdlet `Get-PSHostProcessInfo`, `Enter-PSHostProcess`, `Get-Runspace` e `Debug-Runspace` per eseguire il debug della risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="a5bed-136">**Resolution:** Discover and attach to the runspace using cmdlets `Get-PSHostProcessInfo`, `Enter-PSHostProcess` , `Get-Runspace` and `Debug-Runspace` to debug the DSC resource.</span></span>

```powershell
# Find all the processes hosting PowerShell
Get-PSHostProcessInfo

ProcessName    ProcessId AppDomainName
-----------    --------- -------------
powershell          3932 DefaultAppDomain
powershell_ise      2304 DefaultAppDomain
WmiPrvSE            3396 DscPsPluginWkr_AppDomain

# Enter the process that is hosting DSC engine (WMI process with DscPsPluginWkr_Appdomain)
Enter-PSHostProcess -Id 3396 -AppDomainName DscPsPluginWkr_AppDomain

# Find all the available rusnspaces in that process
Get-Runspace

Id Name       ComputerName Type  State  Availability
-- ----       ------------ ----  -----  ------------
 2 Runspace2  localhost    Local Opened InBreakpoint
 5 RemoteHost localhost    Local Opened Busy

# Debug the runspace that is in **InBreakpoint** availability state
Debug-Runspace -Id 2
```

## <a name="various-partial-configuration-documents-for-same-node-cannot-have-identical-resource-names"></a><span data-ttu-id="a5bed-137">Documenti di configurazioni parziali diversi per lo stesso nodo non possono avere nomi di risorse identici</span><span class="sxs-lookup"><span data-stu-id="a5bed-137">Various Partial Configuration documents for same node cannot have identical resource names</span></span>

<span data-ttu-id="a5bed-138">Nel caso di più configurazioni parziali distribuite in un singolo nodo, la presenza di nomi identici per le risorse può causare un errore di runtime.</span><span class="sxs-lookup"><span data-stu-id="a5bed-138">For several partial configurations that are deployed onto a single node, identical names of resources cause run time error.</span></span>

<span data-ttu-id="a5bed-139">**Soluzione:** usare nomi diversi anche per le stesse risorse in configurazioni parziali diverse.</span><span class="sxs-lookup"><span data-stu-id="a5bed-139">**Resolution:** Use different names for even same resources in different partial configurations.</span></span>

## <a name="start-dscconfiguration-useexisting-does-not-work-with--credential"></a><span data-ttu-id="a5bed-140">Start-DscConfiguration -UseExisting non funziona con -Credential</span><span class="sxs-lookup"><span data-stu-id="a5bed-140">Start-DscConfiguration –UseExisting does not work with -Credential</span></span>

<span data-ttu-id="a5bed-141">Quando si usa `Start-DscConfiguration` con il parametro **UseExisting**, il parametro **Credential** viene ignorato.</span><span class="sxs-lookup"><span data-stu-id="a5bed-141">When using `Start-DscConfiguration` with **UseExisting** parameter, the **Credential** parameter is ignored.</span></span> <span data-ttu-id="a5bed-142">DSC usa l'identità del processo predefinita per continuare l'operazione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-142">DSC uses default process identity to proceed the operation.</span></span> <span data-ttu-id="a5bed-143">Ciò causa un errore quando sono necessarie credenziali diverse per procedere nel nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="a5bed-143">This causes error when a different credential is needed to proceed on remote node.</span></span>

<span data-ttu-id="a5bed-144">**Soluzione:** usare una sessione CIM per operazioni DSC remote:</span><span class="sxs-lookup"><span data-stu-id="a5bed-144">**Resolution:** Use CIM session for remote DSC operations:</span></span>

```powershell
$session = New-CimSession -ComputerName $node -Credential $credential
Start-DscConfiguration -UseExisting -CimSession $session
```

## <a name="ipv6-addresses-as-node-names-in-dsc-configurations"></a><span data-ttu-id="a5bed-145">Indirizzi IPv6 come nomi di nodo in configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="a5bed-145">IPv6 Addresses as Node Names in DSC configurations</span></span>

<span data-ttu-id="a5bed-146">Gli indirizzi IPv6 come nomi dei nodi negli script di configurazione DSC non sono supportati in questa versione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-146">IPv6 addresses as node names in DSC configuration scripts are not supported in this release.</span></span>

<span data-ttu-id="a5bed-147">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-147">**Resolution:** None.</span></span>

## <a name="debugging-of-class-based-dsc-resources"></a><span data-ttu-id="a5bed-148">Debug di risorse DSC `Class-Based`</span><span class="sxs-lookup"><span data-stu-id="a5bed-148">Debugging of `Class-Based` DSC Resources</span></span>

<span data-ttu-id="a5bed-149">Il debug di risorse DSC basate su classi non è supportato in questa versione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-149">Debugging of class-based DSC Resources is not supported in this release.</span></span>

<span data-ttu-id="a5bed-150">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-150">**Resolution:** None.</span></span>

## <a name="variables-and-functions-defined-in-script-scope-in-dsc-class-based-resource-are-not-preserved-across-multiple-calls-to-a-dsc-resource"></a><span data-ttu-id="a5bed-151">Le variabili e le funzioni definite nell'ambito $script per le risorse DSC basate su classi non vengono mantenute per più chiamate a una risorsa DSC</span><span class="sxs-lookup"><span data-stu-id="a5bed-151">Variables and functions defined in $script scope in DSC Class-Based Resource are not preserved across multiple calls to a DSC Resource</span></span>

<span data-ttu-id="a5bed-152">Più chiamate consecutive di `Start-DSCConfiguration` avranno esito negativo se la configurazione usa qualsiasi risorsa basata su classi con variabili o funzioni definite nell'ambito `$script`.</span><span class="sxs-lookup"><span data-stu-id="a5bed-152">Multiple consecutive calls to `Start-DSCConfiguration` fails if the configuration is using any class-based resource which has variables or functions defined in `$script` scope.</span></span>

<span data-ttu-id="a5bed-153">**Soluzione:** definire tutte le variabili e tutte le funzioni nella classe della risorsa DSC stessa.</span><span class="sxs-lookup"><span data-stu-id="a5bed-153">**Resolution:** Define all variables and functions in DSC Resource class itself.</span></span> <span data-ttu-id="a5bed-154">Nessuna variabile/funzione con ambito `$script`.</span><span class="sxs-lookup"><span data-stu-id="a5bed-154">No `$script` scope variables/functions.</span></span>

## <a name="dsc-resource-debugging-when-a-resource-is-using-psdscrunascredential"></a><span data-ttu-id="a5bed-155">Debug delle risorse DSC quando una risorsa usa PSDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a5bed-155">DSC Resource Debugging when a resource is using PSDscRunAsCredential</span></span>

<span data-ttu-id="a5bed-156">Il debug delle risorse DSC quando una risorsa usa la proprietà **PSDscRunAsCredential** nella configurazione non è supportato in questa versione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-156">DSC Resource debugging when a resource is using the **PSDscRunAsCredential** property in the configuration is not supported in this release.</span></span>

<span data-ttu-id="a5bed-157">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-157">**Resolution:** None.</span></span>

## <a name="psdscrunascredential-is-not-supported-for-dsc-composite-resources"></a><span data-ttu-id="a5bed-158">La proprietà PsDscRunAsCredential non è supportata per le risorse DSC composite</span><span class="sxs-lookup"><span data-stu-id="a5bed-158">PsDscRunAsCredential is not supported for DSC Composite Resources</span></span>

<span data-ttu-id="a5bed-159">**Soluzione:** usare la proprietà Credential, se disponibile.</span><span class="sxs-lookup"><span data-stu-id="a5bed-159">**Resolution:** Use Credential property if available.</span></span> <span data-ttu-id="a5bed-160">WindowsFeatureSet e ServiceSet di esempio</span><span class="sxs-lookup"><span data-stu-id="a5bed-160">Example ServiceSet and WindowsFeatureSet</span></span>

## <a name="get-dscresource--syntax-does-not-reflect-psdscrunascredential-correctly"></a><span data-ttu-id="a5bed-161">Get-DscResource -Syntax non rappresenta correttamente PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="a5bed-161">Get-DscResource -Syntax does not reflect PsDscRunAsCredential correctly</span></span>

<span data-ttu-id="a5bed-162">il parametro **Syntax** non rappresenta correttamente **PsDscRunAsCredential** quando la risorsa contrassegna la proprietà come obbligatoria o non la supporta.</span><span class="sxs-lookup"><span data-stu-id="a5bed-162">The **Syntax** parameter does not reflect **PsDscRunAsCredential** correctly when resource marks it as mandatory or does not support it.</span></span>

<span data-ttu-id="a5bed-163">**Soluzione:** Nessuna.</span><span class="sxs-lookup"><span data-stu-id="a5bed-163">**Resolution:** None.</span></span> <span data-ttu-id="a5bed-164">Tuttavia, con la creazione della configurazione in ISE vengono usati i metadati corretti della proprietà **PsDscRunAsCredential** quando si usa IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="a5bed-164">However, authoring configuration in ISE reflects correct metadata about **PsDscRunAsCredential** property when using IntelliSense.</span></span>

## <a name="windowsoptionalfeature-is-not-available-in-windows-7"></a><span data-ttu-id="a5bed-165">WindowsOptionalFeature non è disponibile in Windows 7</span><span class="sxs-lookup"><span data-stu-id="a5bed-165">WindowsOptionalFeature is not available in Windows 7</span></span>

<span data-ttu-id="a5bed-166">La risorsa DSC **WindowsOptionalFeature** non è disponibile in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a5bed-166">The **WindowsOptionalFeature** DSC resource is not available in Windows 7.</span></span> <span data-ttu-id="a5bed-167">La risorsa richiede il modulo Gestione e manutenzione immagini distribuzione e i cmdlet di Gestione e manutenzione immagini distribuzione disponibili a partire da Windows 8 e nelle versioni più recenti del sistema operativo Windows.</span><span class="sxs-lookup"><span data-stu-id="a5bed-167">This resource requires the DISM module, and DISM cmdlets that are available starting in Windows 8 and newer releases of the Windows operating system.</span></span>

## <a name="for-class-based-dsc-resources-import-dscresource--moduleversion-may-not-work-as-expected"></a><span data-ttu-id="a5bed-168">Per le risorse DSC basate su classi, Import-DscResource -ModuleVersion potrebbe non funzionare come previsto</span><span class="sxs-lookup"><span data-stu-id="a5bed-168">For Class-based DSC resources, Import-DscResource -ModuleVersion may not work as expected</span></span>

<span data-ttu-id="a5bed-169">Se il nodo di compilazione include più versioni di un modulo di risorse DSC basato su classi, `Import-DscResource -ModuleVersion` non recupera la versione specificata e genera l'errore di compilazione seguente.</span><span class="sxs-lookup"><span data-stu-id="a5bed-169">If the compilation node has multiple versions of a class-based DSC resource module, `Import-DscResource -ModuleVersion` does not pick the specified version and results in following compilation error.</span></span>

```Output
ImportClassResourcesFromModule : Exception calling "ImportClassResourcesFromModule" with "3" argument(s):
 "Keyword 'MyTestResource' already defined in the configuration."
At C:\Windows\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\PSDesiredStateConfiguration.psm1:2035 char:35
+ ... rcesFound = ImportClassResourcesFromModule -Module $mod -Resources $r ...
+                 ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (:) [ImportClassResourcesFromModule], MethodInvocationException
    + FullyQualifiedErrorId : PSInvalidOperationException,ImportClassResourcesFromModule
```

<span data-ttu-id="a5bed-170">**Soluzione:** importare la versione richiesta definendo l'oggetto **ModuleSpecification** per il parametro **ModuleName** con la chiave **RequiredVersion** specificata come segue:</span><span class="sxs-lookup"><span data-stu-id="a5bed-170">**Resolution:** Import the required version by defining the **ModuleSpecification** object to the **ModuleName** parameter with **RequiredVersion** key specified as follows:</span></span>

```powershell
Import-DscResource -ModuleName @{ModuleName='MyModuleName';RequiredVersion='1.2'}
```

## <a name="some-dsc-resources-like-registry-resource-may-start-to-take-a-long-time-to-process-the-request"></a><span data-ttu-id="a5bed-171">Alcune risorse DSC, come la risorsa Registry, potrebbero iniziare a richiedere molto tempo per elaborare la richiesta.</span><span class="sxs-lookup"><span data-stu-id="a5bed-171">Some DSC resources like registry resource may start to take a long time to process the request.</span></span>

<span data-ttu-id="a5bed-172">**Risoluzione 1:** creare un'attività di pianificazione che pulisce periodicamente la cartella seguente.</span><span class="sxs-lookup"><span data-stu-id="a5bed-172">**Resolution 1:** Create a schedule task that cleans up the following folder periodically.</span></span>

```powershell
$env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis
```

<span data-ttu-id="a5bed-173">**Risoluzione 2:** modificare la configurazione DSC in modo da pulire la cartella *CommandAnalysis* al termine della configurazione.</span><span class="sxs-lookup"><span data-stu-id="a5bed-173">**Resolution 2:** Change the DSC configuration to clean up the *CommandAnalysis* folder at the end of the configuration.</span></span>

```powershell
Configuration $configName
{

   # User Data
    Registry SetRegisteredOwner
    {
        Ensure = 'Present'
        Force = $True
        Key = $Node.RegisteredKey
        ValueName = $Node.RegisteredOwnerValue
        ValueType = 'String'
        ValueData = $Node.RegisteredOwnerData
    }
    #
    # Script to delete the config
    #
    script DeleteCommandAnalysisCache
    {
        DependsOn = "[Registry]SetRegisteredOwner"
        getscript = "@{}"
        testscript = 'Remove-Item -Path $env:windir\system32\config\systemprofile\AppData\Local\Microsoft\Windows\PowerShell\CommandAnalysis -Force -Recurse -ErrorAction SilentlyContinue -ErrorVariable ev | out-null;$true'
        setscript = '$true'
    }
}
```
