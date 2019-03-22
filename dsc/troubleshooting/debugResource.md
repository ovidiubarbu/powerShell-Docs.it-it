---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Debug di risorse DSC
ms.openlocfilehash: c088e13a25ba31ceebaf52b2d24b5d32b96ae2fc
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/18/2019
ms.locfileid: "58055581"
---
# <a name="debugging-dsc-resources"></a><span data-ttu-id="02052-103">Debug di risorse DSC</span><span class="sxs-lookup"><span data-stu-id="02052-103">Debugging DSC resources</span></span>

> <span data-ttu-id="02052-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="02052-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="02052-105">In PowerShell 5.0 è stata introdotta una nuova funzionalità in DSC (Desired State Configuration) che consente di eseguire il debug di una risorsa DSC durante l'applicazione di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="02052-105">In PowerShell 5.0, a new feature was introduced in Desired State Configuration (DSC) that allows you to debug a DSC resource as a configuration is being applied.</span></span>

## <a name="enabling-dsc-debugging"></a><span data-ttu-id="02052-106">Abilitazione del debug di DSC</span><span class="sxs-lookup"><span data-stu-id="02052-106">Enabling DSC debugging</span></span>
<span data-ttu-id="02052-107">Prima di poter eseguire il debug di una risorsa, è necessario abilitare il debug chiamando il cmdlet [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug).</span><span class="sxs-lookup"><span data-stu-id="02052-107">Before you can debug a resource, you have to enable debugging by calling the [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug) cmdlet.</span></span>
<span data-ttu-id="02052-108">Questo cmdlet accetta il parametro obbligatorio **BreakAll**.</span><span class="sxs-lookup"><span data-stu-id="02052-108">This cmdlet takes a mandatory parameter, **BreakAll**.</span></span>

<span data-ttu-id="02052-109">È possibile verificare che il debug sia stato abilitato osservando il risultato di una chiamata a [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span><span class="sxs-lookup"><span data-stu-id="02052-109">You can verify that debugging has been enabled by looking at the result of a call to [Get-DscLocalConfigurationManager](/powershell/module/PSDesiredStateConfiguration/Get-DscLocalConfigurationManager).</span></span>

<span data-ttu-id="02052-110">L'output di PowerShell seguente mostra il risultato dell'abilitazione del debug:</span><span class="sxs-lookup"><span data-stu-id="02052-110">The following PowerShell output shows the result of enabling debugging:</span></span>


```powershell
PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
NONE

PS C:\DebugTest> Enable-DscDebug -BreakAll

PS C:\DebugTest> $LCM = Get-DscLocalConfigurationManager

PS C:\DebugTest> $LCM.DebugMode
ForceModuleImport
ResourceScriptBreakAll

PS C:\DebugTest>
```


## <a name="starting-a-configuration-with-debug-enabled"></a><span data-ttu-id="02052-111">Avvio di una configurazione con il debug abilitato</span><span class="sxs-lookup"><span data-stu-id="02052-111">Starting a configuration with debug enabled</span></span>
<span data-ttu-id="02052-112">Per eseguire il debug di una risorsa DSC, è necessario avviare una configurazione che chiami la risorsa.</span><span class="sxs-lookup"><span data-stu-id="02052-112">To debug a DSC resource, you start a configuration that calls that resource.</span></span>
<span data-ttu-id="02052-113">In questo esempio una semplice configurazione chiama la risorsa **WindowsFeature** per verificare che la funzionalità "WindowsPowerShellWebAccess" sia installata:</span><span class="sxs-lookup"><span data-stu-id="02052-113">For this example, we'll look at a simple configuration that calls the **WindowsFeature** resource to ensure that the "WindowsPowerShellWebAccess" feature is installed:</span></span>

```powershell
Configuration PSWebAccess
    {
    Import-DscResource -ModuleName 'PsDesiredStateConfiguration'
    Node localhost
        {
        WindowsFeature PSWA
            {
            Name = 'WindowsPowerShellWebAccess'
            Ensure = 'Present'
            }
        }
    }
PSWebAccess
```
<span data-ttu-id="02052-114">Dopo aver compilato la configurazione, avviarla chiamando [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span><span class="sxs-lookup"><span data-stu-id="02052-114">After compiling the configuration, start it by calling [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).</span></span>
<span data-ttu-id="02052-115">La configurazione verrà arrestata quando Gestione configurazione locale effettua una chiamata alla prima risorsa nella configurazione.</span><span class="sxs-lookup"><span data-stu-id="02052-115">The configuration will stop when the Local Configuration Manager (LCM) calls into the first resource in the configuration.</span></span>
<span data-ttu-id="02052-116">Se si usano i parametri `-Verbose` e `-Wait`, l'output visualizza le righe che devono essere immesse per avviare il debug.</span><span class="sxs-lookup"><span data-stu-id="02052-116">If you use the `-Verbose` and `-Wait` parameters, the output displays the lines you need to enter to start debugging.</span></span>

```powershell
Start-DscConfiguration .\PSWebAccess -Wait -Verbose
VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfiguration
Manager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: An LCM method call arrived from computer TEST-SRV with user sid S-1-5-21-2127521184-1604012920-1887927527-108583.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Set      ]
WARNING: [TEST-SRV]:                            [DSCEngine] Warning LCM is in Debug 'ResourceScriptBreakAll' mode.  Resource script processing will
be stopped to wait for PowerShell script debugger to attach.
VERBOSE: [TEST-SRV]:                            [DSCEngine] Importing the module C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateCo
nfiguration\DscResources\MSFT_RoleResource\MSFT_RoleResource.psm1 in force mode.
VERBOSE: [TEST-SRV]: LCM:  [ Start  Resource ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]: LCM:  [ Start  Test     ]  [[WindowsFeature]PSWA]
VERBOSE: [TEST-SRV]:                            [[WindowsFeature]PSWA] Importing the module MSFT_RoleResource in force mode.
WARNING: [TEST-SRV]:                            [[WindowsFeature]PSWA] Resource is waiting for PowerShell script debugger to attach.
Use the following commands to begin debugging this resource script:
Enter-PSSession -ComputerName TEST-SRV -Credential <credentials>
Enter-PSHostProcess -Id 9000 -AppDomainName DscPsPluginWkr_AppDomain
Debug-Runspace -Id 9
```
<span data-ttu-id="02052-117">A questo punto, Gestione configurazione locale ha chiamato la risorsa e ha raggiunto il primo punto di interruzione.</span><span class="sxs-lookup"><span data-stu-id="02052-117">At this point, the LCM has called the resource, and come to the first break point.</span></span>
<span data-ttu-id="02052-118">Le ultime tre righe dell'output mostrano come collegarsi al processo e avviare il debug dello script della risorsa.</span><span class="sxs-lookup"><span data-stu-id="02052-118">The last three lines in the output show you how to attach to the process and start debugging the resource script.</span></span>

## <a name="debugging-the-resource-script"></a><span data-ttu-id="02052-119">Debug dello script della risorsa</span><span class="sxs-lookup"><span data-stu-id="02052-119">Debugging the resource script</span></span>

<span data-ttu-id="02052-120">Avviare una nuova istanza di PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="02052-120">Start a new instance of the PowerShell ISE.</span></span>
<span data-ttu-id="02052-121">Nel riquadro della console immettere le ultime tre righe di output dall'output di `Start-DscConfiguration` come comandi, sostituendo `<credentials>` con credenziali utente valide.</span><span class="sxs-lookup"><span data-stu-id="02052-121">In the console pane, enter the last three lines of output from the `Start-DscConfiguration` output as commands, replacing `<credentials>` with valid user credentials.</span></span>
<span data-ttu-id="02052-122">Dovrebbe essere visualizzato un messaggio simile a:</span><span class="sxs-lookup"><span data-stu-id="02052-122">You should now see a prompt that looks similar to:</span></span>

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

<span data-ttu-id="02052-123">Lo script della risorsa verrà aperto nel riquadro di script e il debugger viene interrotto alla prima riga della funzione **Test-TargetResource** (metodo **Test()** di una risorsa basata su classi).</span><span class="sxs-lookup"><span data-stu-id="02052-123">The resource script will open in the script pane, and the debugger is stopped at the first line of the **Test-TargetResource** function (the **Test()** method of a class-based resource).</span></span>
<span data-ttu-id="02052-124">A questo punto è possibile usare i comandi di debug in ISE per eseguire lo script della risorsa un'istruzione alla volta, esaminare i valori delle variabili, visualizzare lo stack di chiamate e così via.</span><span class="sxs-lookup"><span data-stu-id="02052-124">Now you can use the debug commands in the ISE to step through the resource script, look at variable values, view the call stack, and so on.</span></span> <span data-ttu-id="02052-125">Tenere presente che ogni riga nello script della risorsa (o classe) è impostata come punto di interruzione.</span><span class="sxs-lookup"><span data-stu-id="02052-125">Remember that every line in the resource script (or class) is set as a break point.</span></span>

## <a name="disabling-dsc-debugging"></a><span data-ttu-id="02052-126">Disabilitare il debug di DSC</span><span class="sxs-lookup"><span data-stu-id="02052-126">Disabling DSC debugging</span></span>

<span data-ttu-id="02052-127">Dopo la chiamata di [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), tutte le chiamate a [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) comporteranno l'interruzione della configurazione nel debugger.</span><span class="sxs-lookup"><span data-stu-id="02052-127">After calling [Enable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Enable-DscDebug), all calls to [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) will result in the configuration breaking into the debugger.</span></span> <span data-ttu-id="02052-128">Per consentire la normale esecuzione delle configurazioni, è necessario disabilitare il debug chiamando il cmdlet [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug).</span><span class="sxs-lookup"><span data-stu-id="02052-128">To allow configurations to run normally, you must disable debugging by calling the [Disable-DscDebug](/powershell/module/PSDesiredStateConfiguration/Disable-DscDebug) cmdlet.</span></span>

><span data-ttu-id="02052-129">**Nota:** il riavvio non modifica lo stato di debug della Gestione configurazione locale.</span><span class="sxs-lookup"><span data-stu-id="02052-129">**Note:** Rebooting does not change the debug state of the LCM.</span></span> <span data-ttu-id="02052-130">Se il debug è abilitato, quando si avvia una configurazione questa verrà interrotta nel debugger dopo il riavvio.</span><span class="sxs-lookup"><span data-stu-id="02052-130">If debugging is enabled, starting a configuration will still break into the debugger after a reboot.</span></span>

## <a name="see-also"></a><span data-ttu-id="02052-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="02052-131">See Also</span></span>

- [<span data-ttu-id="02052-132">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="02052-132">Writing a custom DSC resource with MOF</span></span>](../resources/authoringResourceMOF.md)
- [<span data-ttu-id="02052-133">Scrittura di una risorsa DSC personalizzata con classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="02052-133">Writing a custom DSC resource with PowerShell classes</span></span>](../resources/authoringResourceClass.md)
