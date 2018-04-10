---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Debug di risorse DSC
ms.openlocfilehash: 6a1f4b04a11185c2cfe9be26324bd66ed13ca7dd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="debugging-dsc-resources"></a>Debug di risorse DSC

> Si applica a: Windows PowerShell 5.0

In PowerShell 5.0 è stata introdotta una nuova funzionalità in DSC (Desired State Configuration) che permette di eseguire il debug di una risorsa DSC durante l'applicazione di una configurazione.

## <a name="enabling-dsc-debugging"></a>Abilitazione del debug di DSC
Prima di poter eseguire il debug di una risorsa, è necessario abilitare il debug chiamando il cmdlet [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx).
Questo cmdlet accetta il parametro obbligatorio **BreakAll**.

È possibile verificare che il debug sia stato abilitato osservando il risultato di una chiamata a [Get-DscLocalConfigurationManager](https://technet.microsoft.com/library/dn407378.aspx).

L'output di PowerShell seguente mostra il risultato dell'abilitazione del debug:


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


## <a name="starting-a-configuration-with-debug-enabled"></a>Avvio di una configurazione con il debug abilitato
Per eseguire il debug di una risorsa DSC, è necessario avviare una configurazione che chiami la risorsa.
In questo esempio una semplice configurazione chiama la risorsa [WindowsFeature](windowsfeatureResource.md) per verificare che la funzionalità "WindowsPowerShellWebAccess" sia installata:

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
Dopo aver compilato la configurazione, avviarla chiamando [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx).
La configurazione verrà arrestata quando Gestione configurazione locale effettua una chiamata alla prima risorsa nella configurazione.
Se si usano i parametri `-Verbose` e `-Wait`, l'output visualizza le righe che devono essere immesse per avviare il debug.

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
A questo punto, Gestione configurazione locale ha chiamato la risorsa e ha raggiunto il primo punto di interruzione.
Le ultime tre righe dell'output mostrano come collegarsi al processo e avviare il debug dello script della risorsa.

## <a name="debugging-the-resource-script"></a>Debug dello script della risorsa

Avviare una nuova istanza di PowerShell ISE.
Nel riquadro della console immettere le ultime tre righe di output dall'output di `Start-DscConfiguration` come comandi, sostituendo `<credentials>` con credenziali utente valide.
Dovrebbe essere visualizzato un messaggio simile a:

```powershell
[TEST-SRV]: [DBG]: [Process:9000]: [RemoteHost]: PS C:\DebugTest>>
```

Lo script della risorsa verrà aperto nel riquadro di script e il debugger viene interrotto alla prima riga della funzione **Test-TargetResource** (metodo **Test()** di una risorsa basata su classi).
A questo punto è possibile usare i comandi di debug in ISE per eseguire lo script della risorsa un'istruzione alla volta, esaminare i valori delle variabili, visualizzare lo stack di chiamate e così via.
Per informazioni sul debug in PowerShell ISE, vedere [How to Debug Scripts in Windows PowerShell ISE](https://technet.microsoft.com/en-us/library/dd819480.aspx) (Come eseguire il debug degli script in Windows PowerShell ISE).
Tenere presente che ogni riga nello script della risorsa (o classe) è impostata come punto di interruzione.

## <a name="disabling-dsc-debugging"></a>Disabilitare il debug di DSC

Dopo la chiamata di [Enable-DscDebug](https://technet.microsoft.com/library/mt517870.aspx), tutte le chiamate a [Start-DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) comporteranno l'interruzione della configurazione nel debugger. Per consentire la normale esecuzione delle configurazioni, è necessario disabilitare il debug chiamando il cmdlet [Disable-DscDebug](https://technet.microsoft.com/en-us/library/mt517872.aspx).

>**Nota:** il riavvio non modifica lo stato di debug della Gestione configurazione locale. Se il debug è abilitato, quando si avvia una configurazione questa verrà interrotta nel debugger dopo il riavvio.


## <a name="see-also"></a>Vedere anche
- [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md)
- [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)