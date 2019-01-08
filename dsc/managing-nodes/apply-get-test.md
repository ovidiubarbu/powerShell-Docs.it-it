---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Applicare, ottenere e testare le configurazioni in un nodo
ms.openlocfilehash: 41f8d2d75d3dd9621de615e7999c2690cb8ce44a
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401723"
---
# <a name="apply-get-and-test-configurations-on-a-node"></a>Applicare, ottenere e testare le configurazioni in un nodo

Questa Guida illustrerà come lavorare con le configurazioni in una nodo di destinazione. Questa guida è suddiviso in questa procedura:

## <a name="apply-a-configuration"></a>Applicare una configurazione

Per applicare e gestire una configurazione, è necessario generare un file "con estensione MOF". Il codice seguente rappresenta una semplice configurazione che verrà usata in questa Guida.

```powershell
Configuration Sample
{
    # This will generate two .mof files, a localhost.mof, and a server02.mof
    Node localhost, server02
    {
        File SampleFile
        {
            DestinationPath = 'C:\Temp\temp.txt'
            Contents = 'This is a simple resource to show Configuration functionality on a Node.'
        }
    }
}

# The -OutputPath parameter is built into every Configuration automatically.
# The value of -OutputPath determines where the .mof file should be stored, once compiled.
Sample -OutputPath "C:\Temp\"
```

La compilazione di questa configurazione restituirà due file "con estensione MOF".

```output
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a----       11/27/2018   7:29 AM     2.13KB localhost.mof
-a----       11/27/2018   7:29 AM     2.13KB server02.mof
```

Per applicare una configurazione, usare il [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet. Il `-Path` parametro specifica una directory in cui si trovano i file "MOF". Se nessun `-Computername` viene specificato `Start-DSCConfiguration` tenterà di applicare ogni configurazione per il nome del computer specificato dal nome del file 'file MOF' (\<nomecomputer\>MOF). Specificare `-Verbose` a `Start-DSCConfiguration` per visualizzare un output più dettagliato.

```powershell
Start-DSCConfiguration -Path C:\Temp\ -Verbose
```

Se `-Wait` non viene specificato, viene visualizzato un processo creato. Il processo creato disporrà di uno **ChildJob** per ogni file "MOF" elaborate dal `Start-DSCConfiguration`.

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
45     Job45           Configuratio... Running       True            localhost,server02   Start-DSCConfiguration...
```

Se una configurazione sta richiedendo molto tempo e si vuole arrestarla, è possibile usare [Stop-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Stop-DscConfiguration) per arrestare l'applicazione nel nodo locale.

```powershell
Stop-DSCConfiguration -Force
```

Al termine dell'operazione, è possibile visualizzare lo stato dei processi tramite l'oggetto processo restituito da [Get-Job](/powershell/module/microsoft.powershell.core/get-job).

```powershell
$job = Get-Job
$job.ChildJobs
```

```output
Id     Name            PSJobTypeName   State         HasMoreData     Location             Command
--     ----            -------------   -----         -----------     --------             -------
49     Job49           Configuratio... Completed     True            localhost            Start-DSCConfiguration...
50     Job50           Configuratio... Completed     True            server02             Start-DSCConfiguration...
```

Per visualizzare il **Verbose** di output, usare i comandi seguenti per visualizzare i **Verbose** stream per ogni **ChildJob**. Per altre informazioni sui processi di PowerShell, vedere [about_Jobs](/powershell/module/microsoft.powershell.core/about/about_jobs).

```powershell
# View the verbose output of the localhost job using array indexing.
$job.ChildJobs[0].Verbose
```

```output
Perform operation 'Invoke CimMethod' with following parameters, ''methodName' = SendConfigurationApply,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' = root/Microsoft/Windows/DesiredStateConfiguration'.
An LCM method call arrived from computer SERVER01 with user sid S-1-5-21-124525095-708259637-1543119021-1282804.
[SERVER01]: LCM:  [ Start  Set      ]
[SERVER01]: LCM:  [ Start  Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ Start  Test     ]  [[File]SampleFile]
[SERVER01]:                            [[File]SampleFile] The destination object was found and no action is required.
[SERVER01]: LCM:  [ End    Test     ]  [[File]SampleFile]  in 0.0370 seconds.
[SERVER01]: LCM:  [ Skip   Set      ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Resource ]  [[File]SampleFile]
[SERVER01]: LCM:  [ End    Set      ]
[SERVER01]: LCM:  [ End    Set      ]    in  0.2400 seconds.
Operation 'Invoke CimMethod' complete.
```

A partire da PowerShell 5.0, il `-UseExisting` parametro è stato aggiunto al `Start-DSCConfiguration`. Specificando `-UseExisting`, è indicare al cmdlet per usare la configurazione applicata esistente invece di quella specificata per il `-Path` parametro.

```powershell
Start-DSCConfiguration -UseExisting -Verbose -Wait
```

## <a name="test-a-configuration"></a>Testare una configurazione

È possibile testare una configurazione attualmente applicata mediante [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration). `Test-DSCConfiguration` restituirà `True` se il nodo è conforme, e `False` in caso contrario.

```powershell
Test-DSCConfiguration
```

A partire da PowerShell 5.0, il `-Detailed` parametro è stato aggiunto che restituisce un oggetto con le raccolte per **ResourcesInDesiredState** e **ResourcesNotInDesiredState**

```powershell
Test-DSCConfiguration -Detailed
```

A partire da PowerShell 5.0 è possibile testare una configurazione senza applicarlo. Il `-ReferenceConfiguration` parametro accetta il percorso di un file "MOF" per eseguire il test di nodo rispetto. No **impostare** azioni vengono eseguite nel nodo. In PowerShell 4.0, sono disponibili soluzioni alternative per testare una configurazione senza applicarlo, ma non vengano descritti di seguito.

## <a name="get-configuration-values"></a>Ottenere i valori di configurazione

Il [Get-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) cmdlet restituisce i valori correnti per qualsiasi risorsa configurata nella configurazione attualmente applicata.

```powershell
Get-DSCConfiguration
```

Output di esempio configurazione avrebbe un aspetto simile al seguente se è stata applicata.

```output
ConfigurationName    : Sample
DependsOn            :
ModuleName           : PSDesiredStateConfiguration
ModuleVersion        :
PsDscRunAsCredential :
ResourceId           : [File]SampleFile
SourceInfo           :
Attributes           : {archive}
Checksum             :
Contents             :
CreatedDate          : 11/27/2018 7:16:06 AM
Credential           :
DestinationPath      : C:\Temp\temp.txt
Ensure               : present
Force                :
MatchSource          :
ModifiedDate         : 11/27/2018 7:16:06 AM
Recurse              :
Size                 : 75
SourcePath           :
SubItems             :
Type                 : file
PSComputerName       :
CimClassName         : MSFT_FileDirectoryConfiguration
```

## <a name="get-configuration-status"></a>Ottenere lo stato di configurazione

A partire da PowerShell 5.0 il [Get-DSCConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet consente di visualizzare la cronologia delle configurazioni applicate al nodo. PowerShell DSC tiene traccia delle ultime configurazioni di {{N}} applicate in **Push** oppure **Pull** modalità. Ciò include eventuali *coerenza* controlli eseguiti da Gestione configurazione locale. Per impostazione predefinita, `Get-DSCConfigurationStatus` Mostra solo l'ultima voce di cronologia.

```powershell
Get-DSCConfigurationStatus
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
```

Usare il `-All` parametro per visualizzare tutta la cronologia dello stato di configurazione.

> [!NOTE]
> Output viene troncato per brevità.

```powershell
Get-DSCConfigurationStatus -All
```

```output
Status     StartDate                 Type            Mode  RebootRequested      NumberOfResources
------     ---------                 ----            ----  ---------------      -----------------
Success    11/27/2018 7:18:40 AM     Consistency     PUSH  False                1
Success    11/27/2018 7:16:06 AM     Initial         PUSH  False                1
Success    11/27/2018 7:04:53 AM     Initial         PUSH  False                1
Success    11/27/2018 7:03:45 AM     Consistency     PUSH  False                2
Success    11/27/2018 7:03:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:48:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:44 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:33:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:18:40 AM     Consistency     PUSH  False                2
Success    11/27/2018 6:03:44 AM     Consistency     PUSH  False                2
```

## <a name="manage-configuration-documents"></a>Gestire i documenti di configurazione

Gestione configurazione locale gestisce la configurazione del nodo consultando **documenti di configurazione**. Questi file "MOF" si trovano nella directory "C:\Windows\System32\Configuration".

A partire da PowerShell 5.0 il [Remove-DSCConfigurationDocument](/powershell/module/PSDesiredStateConfiguration/Remove-DscConfigurationDocument) consente di rimuovere i file "MOF" per interrompere verifiche di coerenza futura o rimuovere una configurazione con errori quando vengono applicate. Il `-Stage` parametro consente di specificare quali file "MOF" che si desidera rimuovere.

```powershell
Remove-DSCConfigurationDocument -Stage Current
```

> [!NOTE]
> In PowerShell 4.0, è comunque possibile rimuovere questi file "MOF" direttamente usando [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item).

## <a name="publish-configurations"></a>Pubblicare le configurazioni

A partire da PowerShell 5.0, il [Publish-DSCConfiguration](/powershell/module/PSDesiredStateConfiguration/Publish-DscConfiguration) è stato aggiunto il cmdlet. Questo cmdlet consente di pubblicare un file "con estensione MOF" a computer remoti, senza applicarlo.

```powershell
Publish-DscConfiguration -Path '$home\WebServer' -ComputerName "ContosoWebServer" -Credential (get-credential Contoso\webadministrator)
```

## <a name="see-also"></a>Vedere anche

- [Ottenere, testare e impostare](../resources/get-test-set.md)
