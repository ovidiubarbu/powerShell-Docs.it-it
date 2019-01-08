---
ms.date: 10/30/2018
keywords: dsc,powershell,configurazione,installazione
title: Risoluzione dei problemi relativi a DSC
ms.openlocfilehash: e1f36bbc97569ac0d65f003ee08f52ec174a4520
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401704"
---
# <a name="troubleshooting-dsc"></a><span data-ttu-id="d8303-103">Risoluzione dei problemi relativi a DSC</span><span class="sxs-lookup"><span data-stu-id="d8303-103">Troubleshooting DSC</span></span>

<span data-ttu-id="d8303-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_</span><span class="sxs-lookup"><span data-stu-id="d8303-104">_Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0_</span></span>

<span data-ttu-id="d8303-105">Questo argomento illustra come risolvere eventuali problemi di DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-105">This topic describes ways to troubleshoot DSC when problems arise.</span></span>

## <a name="winrm-dependency"></a><span data-ttu-id="d8303-106">Dipendenza da WinRM</span><span class="sxs-lookup"><span data-stu-id="d8303-106">WinRM Dependency</span></span>

<span data-ttu-id="d8303-107">Desired State Configuration (DSC) in Windows PowerShell dipende da WinRM.</span><span class="sxs-lookup"><span data-stu-id="d8303-107">Windows PowerShell Desired State Configuration (DSC) depends on WinRM.</span></span> <span data-ttu-id="d8303-108">WinRM non è abilitato per impostazione predefinita in Windows Server 2008 R2 e Windows 7.</span><span class="sxs-lookup"><span data-stu-id="d8303-108">WinRM is not enabled by default on Windows Server 2008 R2 and Windows 7.</span></span> <span data-ttu-id="d8303-109">Per abilitare WinRM, eseguire `Set-WSManQuickConfig` in una sessione di Windows PowerShell con privilegi elevati.</span><span class="sxs-lookup"><span data-stu-id="d8303-109">Run `Set-WSManQuickConfig`, in a Windows PowerShell elevated session, to enable WinRM.</span></span>

## <a name="using-get-dscconfigurationstatus"></a><span data-ttu-id="d8303-110">Uso di Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="d8303-110">Using Get-DscConfigurationStatus</span></span>

<span data-ttu-id="d8303-111">Il cmdlet [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) ottiene informazioni di alto livello sullo stato di configurazione da un nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="d8303-111">The [Get-DscConfigurationStatus](/powershell/module/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet gets information about configuration status from a target node.</span></span> <span data-ttu-id="d8303-112">Viene restituito un oggetto completo che include informazioni dettagliate sull'esito positivo o negativo dell'esecuzione della configurazione.</span><span class="sxs-lookup"><span data-stu-id="d8303-112">A rich object is returned that includes high-level information about whether or not the configuration run was successful or not.</span></span> <span data-ttu-id="d8303-113">È possibile esaminare l'oggetto per scoprire i dettagli sull'esecuzione della configurazione, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="d8303-113">You can dig into the object to discover details about the configuration run such as:</span></span>

- <span data-ttu-id="d8303-114">Tutte le risorse con errori</span><span class="sxs-lookup"><span data-stu-id="d8303-114">All of the resources that failed</span></span>
- <span data-ttu-id="d8303-115">Qualsiasi risorsa che ha richiesto un riavvio</span><span class="sxs-lookup"><span data-stu-id="d8303-115">Any resource that requested a reboot</span></span>
- <span data-ttu-id="d8303-116">Impostazioni di metaconfigurazione al momento dell'esecuzione della configurazione</span><span class="sxs-lookup"><span data-stu-id="d8303-116">Meta-Configuration settings at time of configuration run</span></span>
- <span data-ttu-id="d8303-117">Altro.</span><span class="sxs-lookup"><span data-stu-id="d8303-117">Etc.</span></span>

<span data-ttu-id="d8303-118">Il set di parametri seguente restituisce informazioni sullo stato per l'ultima esecuzione della configurazione:</span><span class="sxs-lookup"><span data-stu-id="d8303-118">The following parameter set returns the status information for the last configuration run:</span></span>

```
Get-DscConfigurationStatus [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```
<span data-ttu-id="d8303-119">Il set di parametri seguente restituisce informazioni sullo stato per tutte le esecuzioni della configurazione precedenti:</span><span class="sxs-lookup"><span data-stu-id="d8303-119">The following parameter set returns the status information for all previous configuration runs:</span></span>

```
Get-DscConfigurationStatus -All
                           [-CimSession <CimSession[]>]
                           [-ThrottleLimit <int>]
                           [-AsJob]
                           [<CommonParameters>]
```

## <a name="example"></a><span data-ttu-id="d8303-120">Esempio</span><span class="sxs-lookup"><span data-stu-id="d8303-120">Example</span></span>

```powershell
PS C:\> $Status = Get-DscConfigurationStatus

PS C:\> $Status

Status         StartDate                Type            Mode    RebootRequested        NumberOfResources
------        ---------                ----            ----    ---------------        -----------------
Failure        11/24/2015  3:44:56     Consistency        Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName     :    MyService
DependsOn             :
ModuleName            :    PSDesiredStateConfiguration
ModuleVersion         :    1.1
PsDscRunAsCredential  :
ResourceID            :    [File]ServiceDll
SourceInfo            :    c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds     :    0.19
Error                 :    SourcePath must be accessible for current configuration. The related file/directory is:
                           \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState            :
InDesiredState        :    False
InitialState          :
InstanceName          :    ServiceDll
RebootRequested       :    False
ReosurceName          :    File
StartDate             :    11/24/2015  3:44:56
PSComputerName        :
```

## <a name="my-script-wont-run-using-dsc-logs-to-diagnose-script-errors"></a><span data-ttu-id="d8303-121">Non viene eseguito lo script: Uso di DSC Registra per diagnosticare gli errori di script</span><span class="sxs-lookup"><span data-stu-id="d8303-121">My script won't run: Using DSC logs to diagnose script errors</span></span>

<span data-ttu-id="d8303-122">Come tutti i software Windows, DSC registra errori ed eventi in [registri](/windows/desktop/EventLog/about-event-logging) che possono essere visualizzati dal [Visualizzatore eventi](https://support.microsoft.com/hub/4338813/windows-help).</span><span class="sxs-lookup"><span data-stu-id="d8303-122">Like all Windows software, DSC records errors and events in [logs](/windows/desktop/EventLog/about-event-logging) that can be viewed from the [Event Viewer](https://support.microsoft.com/hub/4338813/windows-help).</span></span>
<span data-ttu-id="d8303-123">Esaminando questi registri è possibile comprendere perché un'operazione specifica non è riuscita e come evitare l'errore in futuro.</span><span class="sxs-lookup"><span data-stu-id="d8303-123">Examining these logs can help you understand why a particular operation failed, and how to prevent failure in the future.</span></span> <span data-ttu-id="d8303-124">La scrittura di script di configurazione può essere complessa, quindi per rendere più semplice il rilevamento degli errori durante la scrittura è possibile usare la risorsa Log DSC per tenere traccia dello stato della configurazione nel registro eventi DSC Analytic.</span><span class="sxs-lookup"><span data-stu-id="d8303-124">Writing configuration scripts can be tricky, so to make tracking errors easier as you author, use the DSC Log resource to track the progress of your configuration in the DSC Analytic event log.</span></span>

## <a name="where-are-dsc-event-logs"></a><span data-ttu-id="d8303-125">Dove sono i registri eventi DSC?</span><span class="sxs-lookup"><span data-stu-id="d8303-125">Where are DSC event logs?</span></span>

<span data-ttu-id="d8303-126">Nel Visualizzatore eventi, gli eventi DSC sono: **Le applicazioni e servizi di log/Microsoft/Windows/Desired State Configuration**</span><span class="sxs-lookup"><span data-stu-id="d8303-126">In Event Viewer, DSC events are in: **Applications and Services Logs/Microsoft/Windows/Desired State Configuration**</span></span>

<span data-ttu-id="d8303-127">Per visualizzare i registri eventi è anche possibile eseguire il cmdlet di PowerShell corrispondente, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent):</span><span class="sxs-lookup"><span data-stu-id="d8303-127">The corresponding PowerShell cmdlet, [Get-WinEvent](/powershell/module/Microsoft.PowerShell.Diagnostics/Get-WinEvent), can also be run to view the event logs:</span></span>

```
PS C:\> Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
11/17/2014 10:27:23 PM        4102 Information      Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
```

<span data-ttu-id="d8303-128">Come illustrato in precedenza, il nome del log principale di DSC è **Microsoft->Windows->DSC** (gli altri nomi di log in Windows non sono riportati per brevità).</span><span class="sxs-lookup"><span data-stu-id="d8303-128">As shown above, DSC's primary log name is **Microsoft->Windows->DSC** (other log names under Windows are not shown here for brevity).</span></span> <span data-ttu-id="d8303-129">Il nome principale viene aggiunto al nome del canale per creare il nome completo del registro.</span><span class="sxs-lookup"><span data-stu-id="d8303-129">The primary name is appended to the channel name to create the complete log name.</span></span> <span data-ttu-id="d8303-130">Il motore DSC scrive principalmente in tre tipi di log: [I log di Debug, operativo e analitico](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="d8303-130">The DSC engine writes mainly into three types of logs: [Operational, Analytic, and Debug logs](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc722404(v=ws.11)).</span></span> <span data-ttu-id="d8303-131">Poiché i registri di debug e analitico sono disattivati per impostazione predefinita, è necessario abilitarli nel Visualizzatore eventi.</span><span class="sxs-lookup"><span data-stu-id="d8303-131">Since the analytic and debug logs are turned off by default, you should enable them in Event Viewer.</span></span> <span data-ttu-id="d8303-132">A tale scopo, aprire il Visualizzatore eventi digitando Show-EventLog in Windows PowerShell oppure fare clic sul pulsante **Start**, scegliere **Pannello di controllo**, fare clic su **Strumenti di amministrazione** e quindi su **Visualizzatore eventi**.</span><span class="sxs-lookup"><span data-stu-id="d8303-132">To do this, open Event Viewer by typing Show-EventLog in Windows PowerShell; or, click the **Start** button, click **Control Panel**, click **Administrative Tools**, and then click **Event Viewer**.</span></span>
<span data-ttu-id="d8303-133">Scegliere **Visualizza registri analitici e di debug** dal menu **Visualizza** del Visualizzatore eventi.</span><span class="sxs-lookup"><span data-stu-id="d8303-133">On the **View** menu in Event viewer, click **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="d8303-134">Il nome del registro per il canale analitico è **Microsoft-Windows-Dsc/Analytic** e per il canale di debug è **Microsoft-Windows-Dsc/Debug**.</span><span class="sxs-lookup"><span data-stu-id="d8303-134">The log name for the analytic channel is **Microsoft-Windows-Dsc/Analytic**, and the debug channel is **Microsoft-Windows-Dsc/Debug**.</span></span> <span data-ttu-id="d8303-135">È anche possibile usare l'utilità [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) per abilitare i registri, come illustrato nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="d8303-135">You could also use the [wevtutil](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/cc732848(v=ws.11)) utility to enable the logs, as shown in the following example.</span></span>

```powershell
wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
```

## <a name="what-do-dsc-logs-contain"></a><span data-ttu-id="d8303-136">Cosa contengono i registri DSC?</span><span class="sxs-lookup"><span data-stu-id="d8303-136">What do DSC logs contain?</span></span>

<span data-ttu-id="d8303-137">I registri DSC sono suddivisi in tre canali in base all'importanza del messaggio.</span><span class="sxs-lookup"><span data-stu-id="d8303-137">DSC logs are split over the three log channels based on the importance of the message.</span></span> <span data-ttu-id="d8303-138">Il registro operativo in DSC contiene tutti i messaggi di errore e può essere usato per identificare un problema.</span><span class="sxs-lookup"><span data-stu-id="d8303-138">The operational log in DSC contains all error messages, and can be used to identify a problem.</span></span> <span data-ttu-id="d8303-139">Il registro analitico include un volume maggiore di eventi e consente di identificare la posizione in cui si sono verificati gli errori.</span><span class="sxs-lookup"><span data-stu-id="d8303-139">The analytic log has a higher volume of events, and can identify where error(s) occurred.</span></span> <span data-ttu-id="d8303-140">Questo canale contiene anche i messaggi dettagliati, se disponibili.</span><span class="sxs-lookup"><span data-stu-id="d8303-140">This channel also contains verbose messages (if any).</span></span> <span data-ttu-id="d8303-141">Il registro di debug contiene registri che aiutano a capire come si sono verificati gli errori.</span><span class="sxs-lookup"><span data-stu-id="d8303-141">The debug log contains logs that can help you understand how the errors occurred.</span></span> <span data-ttu-id="d8303-142">I messaggi di evento DSC sono strutturati in modo che ogni messaggio inizi con un ID processo che rappresenta in modo univoco un'operazione DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-142">DSC event messages are structured such that every event message begins with a job ID that uniquely represents a DSC operation.</span></span> <span data-ttu-id="d8303-143">Nell'esempio seguente si tenta di ottenere il messaggio dal primo evento registrato nel registro operativo DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-143">The example below attempts to obtain the message from the first event logged into the operational DSC log.</span></span>

```powershell
PS C:\> $AllDscOpEvents = Get-WinEvent -LogName "Microsoft-Windows-Dsc/Operational"
PS C:\> $FirstOperationalEvent = $AllDscOpEvents[0]
PS C:\> $FirstOperationalEvent.Message
Job {02C38626-D95A-47F1-9DA2-C1D44A7128E7} :
Consistency engine was run successfully.
```

<span data-ttu-id="d8303-144">Gli eventi DSC vengono registrati in una struttura specifica che consente all'utente di aggregare gli eventi relativi a un processo DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-144">DSC events are logged in a particular structure that enables the user to aggregate events from one DSC job.</span></span> <span data-ttu-id="d8303-145">La struttura è la seguente:</span><span class="sxs-lookup"><span data-stu-id="d8303-145">The structure is as follows:</span></span>

```
Job ID : <Guid>
<Event Message>
```

## <a name="gathering-events-from-a-single-dsc-operation"></a><span data-ttu-id="d8303-146">Raccolta di eventi da una singola operazione DSC</span><span class="sxs-lookup"><span data-stu-id="d8303-146">Gathering events from a single DSC operation</span></span>

<span data-ttu-id="d8303-147">I registri eventi DSC contengono eventi generati da diverse operazioni DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-147">DSC event logs contain events generated by various DSC operations.</span></span> <span data-ttu-id="d8303-148">In genere, tuttavia, all'utente interessano i dettagli solo di un'operazione specifica.</span><span class="sxs-lookup"><span data-stu-id="d8303-148">However, you'll usually be concerned with the detail about just one particular operation.</span></span> <span data-ttu-id="d8303-149">Tutti i registri DSC possono essere raggruppati in base alla proprietà ID processo, che è univoca per ogni operazione DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-149">All DSC logs can be grouped by the job ID property that is unique for every DSC operation.</span></span> <span data-ttu-id="d8303-150">L'ID processo viene visualizzato come primo valore della proprietà in tutti gli eventi DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-150">The job ID is displayed as the first property value in all DSC events.</span></span> <span data-ttu-id="d8303-151">I passaggi seguenti illustrano come riunire tutti gli eventi in una struttura di matrice raggruppata.</span><span class="sxs-lookup"><span data-stu-id="d8303-151">The following steps explain how to accumulate all events in a grouped array structure.</span></span>

```powershell
<##########################################################################
 Step 1 : Enable analytic and debug DSC channels (Operational channel is enabled by default)
###########################################################################>

wevtutil.exe set-log "Microsoft-Windows-Dsc/Analytic" /q:true /e:true
wevtutil.exe set-log "Microsoft-Windows-Dsc/Debug" /q:True /e:true

<##########################################################################
 Step 2 : Perform the required DSC operation (Below is an example, you could run any DSC operation instead)
###########################################################################>

Get-DscLocalConfigurationManager

<##########################################################################
Step 3 : Collect all DSC Logs, from the Analytic, Debug and Operational channels
###########################################################################>

$DscEvents=[System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Operational") `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Analytic" -Oldest) `
         + [System.Array](Get-WinEvent "Microsoft-Windows-Dsc/Debug" -Oldest)


<##########################################################################
 Step 4 : Group all logs based on the job ID
###########################################################################>
$SeparateDscOperations = $DscEvents | Group {$_.Properties[0].value}
```

<span data-ttu-id="d8303-152">In questo caso la variabile `$SeparateDscOperations` contiene i registri raggruppati in base a ID processo.</span><span class="sxs-lookup"><span data-stu-id="d8303-152">Here, the variable `$SeparateDscOperations` contains logs grouped by the job IDs.</span></span> <span data-ttu-id="d8303-153">Ogni elemento della matrice di questa variabile rappresenta un gruppo di eventi registrati da un'operazione DSC diversa e consente l'accesso ad altre informazioni sui registri.</span><span class="sxs-lookup"><span data-stu-id="d8303-153">Each array element of this variable represents a group of events logged by a different DSC operation, allowing access to more information about the logs.</span></span>

```
PS C:\> $SeparateDscOperations

Count Name                      Group
----- ----                      -----
   48 {1A776B6A-5BAC-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
   40 {E557E999-5BA8-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....

PS C:\> $SeparateDscOperations[0].Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 3:47:29 PM          4115 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4198 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4114 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4102 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4098 Warning          Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4176 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
12/2/2013 3:47:29 PM          4182 Information      Job {1A776B6A-5BAC-11E3-BF41-00155D553612} : ...
```

<span data-ttu-id="d8303-154">È possibile estrarre i dati nella variabile `$SeparateDscOperations` usando [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span><span class="sxs-lookup"><span data-stu-id="d8303-154">You can extract the data in the variable `$SeparateDscOperations` using [Where-Object](/powershell/module/microsoft.powershell.core/where-object).</span></span> <span data-ttu-id="d8303-155">Di seguito sono illustrati cinque scenari in cui è possibile estrarre i dati per la risoluzione dei problemi relativi a DSC:</span><span class="sxs-lookup"><span data-stu-id="d8303-155">Following are five scenarios in which you might want to extract data for troubleshooting DSC:</span></span>

### <a name="1-operations-failures"></a><span data-ttu-id="d8303-156">1: Errori relativi alle operazioni</span><span class="sxs-lookup"><span data-stu-id="d8303-156">1: Operations failures</span></span>

<span data-ttu-id="d8303-157">Tutti gli eventi hanno [livelli di gravità](/windows/desktop/WES/defining-severity-levels).</span><span class="sxs-lookup"><span data-stu-id="d8303-157">All events have [severity levels](/windows/desktop/WES/defining-severity-levels).</span></span> <span data-ttu-id="d8303-158">Queste informazioni possono essere usate per identificare gli eventi di errore:</span><span class="sxs-lookup"><span data-stu-id="d8303-158">This information can be used to identify the error events:</span></span>

```
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.LevelDisplayName -contains "Error"}

Count Name                      Group
----- ----                      -----
   38 {5BCA8BE7-5BB6-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord, System.Diagnostics....
```

### <a name="2-details-of-operations-run-in-the-last-half-hour"></a><span data-ttu-id="d8303-159">2: Dettagli delle operazioni eseguite nell'ultima mezz'ora</span><span class="sxs-lookup"><span data-stu-id="d8303-159">2: Details of operations run in the last half hour</span></span>

<span data-ttu-id="d8303-160">`TimeCreated`, una proprietà di ogni evento di Windows, indica l'ora di creazione dell'evento.</span><span class="sxs-lookup"><span data-stu-id="d8303-160">`TimeCreated`, a property of every Windows event, states the time the event was created.</span></span> <span data-ttu-id="d8303-161">Il confronto tra questa proprietà e un oggetto di data/ora specifico consente di filtrare tutti gli eventi:</span><span class="sxs-lookup"><span data-stu-id="d8303-161">Comparing this property with a particular date/time object can be used to filter all events:</span></span>

```powershell
PS C:\> $DateLatest = (Get-Date).AddMinutes(-30)
PS C:\> $SeparateDscOperations | Where-Object {$_.Group.TimeCreated -gt $DateLatest}

Count Name                      Group
----- ----                      -----
    1 {6CEC5B09-5BB0-11E3-BF... {System.Diagnostics.Eventing.Reader.EventLogRecord}
```

### <a name="3-messages-from-the-latest-operation"></a><span data-ttu-id="d8303-162">3: Messaggi dell'operazione più recente</span><span class="sxs-lookup"><span data-stu-id="d8303-162">3: Messages from the latest operation</span></span>

<span data-ttu-id="d8303-163">L'operazione più recente viene archiviata nel primo indice del gruppo di matrici `$SeparateDscOperations`.</span><span class="sxs-lookup"><span data-stu-id="d8303-163">The latest operation is stored in the first index of the array group `$SeparateDscOperations`.</span></span>
<span data-ttu-id="d8303-164">Eseguendo una query relativa ai messaggi del gruppo con indice 0, vengono restituiti tutti i messaggi per l'operazione più recente:</span><span class="sxs-lookup"><span data-stu-id="d8303-164">Querying the group's messages for index 0 returns all messages for the latest operation:</span></span>

```powershell
PS C:\> $SeparateDscOperations[0].Group.Message
Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
Running consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Configuration is sent from computer NULL by user sid S-1-5-18.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Starting consistency engine.
Job {1A776B6A-5BAC-11E3-BF41-00155D553612} :
Displaying messages from built-in DSC resources:
 WMI channel 1
 ResourceID:
 Message : [INCH-VM]:                            [] Consistency check completed.
```

### <a name="4-error-messages-logged-for-recent-failed-operations"></a><span data-ttu-id="d8303-165">4: Messaggi di errore registrati per operazioni recenti non riuscite</span><span class="sxs-lookup"><span data-stu-id="d8303-165">4: Error messages logged for recent failed operations</span></span>

<span data-ttu-id="d8303-166">`$SeparateDscOperations[0].Group` contiene un set di eventi per l'operazione più recente.</span><span class="sxs-lookup"><span data-stu-id="d8303-166">`$SeparateDscOperations[0].Group` contains a set of events for the latest operation.</span></span> <span data-ttu-id="d8303-167">Eseguire il cmdlet `Where-Object` per filtrare gli eventi in base al nome visualizzato del livello.</span><span class="sxs-lookup"><span data-stu-id="d8303-167">Run the `Where-Object` cmdlet to filter the events based on their level display name.</span></span> <span data-ttu-id="d8303-168">I risultati vengono archiviati nella variabile `$myFailedEvent`, che può essere analizzata più in dettaglio per ottenere il messaggio di evento:</span><span class="sxs-lookup"><span data-stu-id="d8303-168">Results are stored in the `$myFailedEvent` variable, which can be further dissected to get the event message:</span></span>

```powershell
PS C:\> $myFailedEvent = ($SeparateDscOperations[0].Group | Where-Object {$_.LevelDisplayName -eq "Error"})

PS C:\> $myFailedEvent.Message

Job {5BCA8BE7-5BB6-11E3-BF41-00155D553612} :
DSC Engine Error :
 Error Message Current configuration does not exist. Execute Start-DscConfiguration command with -Path pa
rameter to specify a configuration file and create a current configuration first.
Error Code : 1
```

### <a name="5-all-events-generated-for-a-particular-job-id"></a><span data-ttu-id="d8303-169">5: Tutti gli eventi generati per un ID processo specifico.</span><span class="sxs-lookup"><span data-stu-id="d8303-169">5: All events generated for a particular job ID.</span></span>

<span data-ttu-id="d8303-170">`$SeparateDscOperations` è una matrice di gruppi, ognuno dei quali ha un nome che rappresenta l'ID processo univoco.</span><span class="sxs-lookup"><span data-stu-id="d8303-170">`$SeparateDscOperations` is an array of groups, each of which has the name as the unique job ID.</span></span> <span data-ttu-id="d8303-171">Eseguendo il cmdlet `Where-Object`, è possibile estrarre i gruppi di eventi con un ID processo specifico:</span><span class="sxs-lookup"><span data-stu-id="d8303-171">By running the `Where-Object` cmdlet, you can extract those groups of events that have a particular job ID:</span></span>

```powershell
PS C:\> ($SeparateDscOperations | Where-Object {$_.Name -eq $jobX} ).Group

   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
12/2/2013 4:33:24 PM          4102 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4168 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4146 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
12/2/2013 4:33:24 PM          4120 Information      Job {847A5619-5BB2-11E3-BF41-00155D553612} : ...
```

## <a name="using-xdscdiagnostics-to-analyze-dsc-logs"></a><span data-ttu-id="d8303-172">Uso di xDscDiagnostics per analizzare i registri DSC</span><span class="sxs-lookup"><span data-stu-id="d8303-172">Using xDscDiagnostics to analyze DSC logs</span></span>

<span data-ttu-id="d8303-173">**xDscDiagnostics** è un modulo di PowerShell costituito da alcune funzioni che consentono di analizzare gli errori di DSC nel computer in uso.</span><span class="sxs-lookup"><span data-stu-id="d8303-173">**xDscDiagnostics** is a PowerShell module that consists of several functions that can help analyze DSC failures on your machine.</span></span> <span data-ttu-id="d8303-174">Queste funzioni possono aiutare a identificare tutti gli eventi locali delle operazioni DSC passate oppure gli eventi DSC in computer remoti (con credenziali valide).</span><span class="sxs-lookup"><span data-stu-id="d8303-174">These functions can help you identify all local events from past DSC operations, or DSC events on remote computers (with valid credentials).</span></span> <span data-ttu-id="d8303-175">Il termine operazione DSC in questo ambito viene usato per definire una singola esecuzione di DSC univoca, dall'inizio alla fine.</span><span class="sxs-lookup"><span data-stu-id="d8303-175">Here, the term DSC operation is used to define a single unique DSC execution from its start to its end.</span></span> <span data-ttu-id="d8303-176">Ad esempio, `Test-DscConfiguration` sarebbe un'operazione DSC distinta.</span><span class="sxs-lookup"><span data-stu-id="d8303-176">For example, `Test-DscConfiguration` would be a separate DSC operation.</span></span> <span data-ttu-id="d8303-177">Allo stesso modo, ogni altro cmdlet in DSC (ad esempio `Get-DscConfiguration`, `Start-DscConfiguration` e così via) può essere identificato come operazione DSC distinta.</span><span class="sxs-lookup"><span data-stu-id="d8303-177">Similarly, every other cmdlet in DSC (such as `Get-DscConfiguration`, `Start-DscConfiguration`, etc.) could each be identified as separate DSC operations.</span></span> <span data-ttu-id="d8303-178">Le funzioni vengono spiegate in [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span><span class="sxs-lookup"><span data-stu-id="d8303-178">The functions are explained at [xDscDiagnostics](https://github.com/PowerShell/xDscDiagnostics).</span></span> <span data-ttu-id="d8303-179">La Guida è disponibile eseguendo `Get-Help <cmdlet name>`.</span><span class="sxs-lookup"><span data-stu-id="d8303-179">Help is available by running `Get-Help <cmdlet name>`.</span></span>

### <a name="getting-details-of-dsc-operations"></a><span data-ttu-id="d8303-180">Acquisizione dei dettagli delle operazioni DSC</span><span class="sxs-lookup"><span data-stu-id="d8303-180">Getting details of DSC operations</span></span>

<span data-ttu-id="d8303-181">La funzione `Get-xDscOperation` consente di trovare i risultati delle operazioni DSC eseguite in uno o più computer e restituisce un oggetto che contiene la raccolta di eventi generati da ogni operazione DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-181">The `Get-xDscOperation` function lets you find the results of the DSC operations that run on one or multiple computers, and returns an object that contains the collection of events produced by each DSC operation.</span></span> <span data-ttu-id="d8303-182">Nell'output seguente, ad esempio, sono stati eseguiti tre comandi.</span><span class="sxs-lookup"><span data-stu-id="d8303-182">For example, in the following output, three commands were run.</span></span> <span data-ttu-id="d8303-183">Il primo ha avuto esito positivo e gli altri due esito negativo.</span><span class="sxs-lookup"><span data-stu-id="d8303-183">The first one passed, and the other two failed.</span></span> <span data-ttu-id="d8303-184">Questi risultati sono riepilogati nell'output di `Get-xDscOperation`.</span><span class="sxs-lookup"><span data-stu-id="d8303-184">These results are summarized in the output of `Get-xDscOperation`.</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation

ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 9:37:52 AM  Failure  9701aadf-395e-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   2          6/23/2016 9:36:54 AM  Failure  7e8e2d6e-395c-11e6-9165-00155d390509  {@{Message=; TimeC...
SRV1   3          6/23/2016 9:36:54 AM  Success  af72c6aa-3960-11e6-9165-00155d390509  {@{Message=Operati...
```

<span data-ttu-id="d8303-185">È anche possibile specificare che vengano restituiti solo i risultati relativi alle operazioni più recenti usando il parametro `Newest`:</span><span class="sxs-lookup"><span data-stu-id="d8303-185">You can also specify that you want only results for the most recent operations by using the `Newest` parameter:</span></span>

```powershell
PS C:\DiagnosticsTest> Get-xDscOperation -Newest 5
ComputerName   SequenceId TimeCreated           Result   JobID                                 AllEvents
------------   ---------- -----------           ------   -----                                 ---------
SRV1   1          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   2          6/23/2016 4:36:54 PM  Success  5c06402b-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   3          6/23/2016 4:36:54 PM  Success                                        {@{Message=; TimeC...
SRV1   4          6/23/2016 4:36:54 PM  Success  5c06402a-399b-11e6-9165-00155d390509  {@{Message=Operati...
SRV1   5          6/23/2016 4:36:51 PM  Success                                        {@{Message=; TimeC...
```

### <a name="getting-details-of-dsc-events"></a><span data-ttu-id="d8303-186">Acquisizione dei dettagli degli eventi DSC</span><span class="sxs-lookup"><span data-stu-id="d8303-186">Getting details of DSC events</span></span>

<span data-ttu-id="d8303-187">Il cmdlet `Trace-xDscOperation` restituisce un oggetto contenente una raccolta di eventi, i relativi tipi e l'output del messaggio generato da un'operazione DSC specifica.</span><span class="sxs-lookup"><span data-stu-id="d8303-187">The `Trace-xDscOperation` cmdlet returns an object containing a collection of events, their event types, and the message output generated from a particular DSC operation.</span></span> <span data-ttu-id="d8303-188">In genere, quando viene individuato un errore in un'operazione tramite `Get-xDscOperation`, è necessario tracciare tale operazione per determinare gli eventi che hanno causato l'errore.</span><span class="sxs-lookup"><span data-stu-id="d8303-188">Typically, when you find a failure in any of the operations using `Get-xDscOperation`, you would trace that operation to find out which of the events caused a failure.</span></span>

<span data-ttu-id="d8303-189">Usare il parametro `SequenceID` per ottenere gli eventi per un'operazione specifica in un computer specifico.</span><span class="sxs-lookup"><span data-stu-id="d8303-189">Use the `SequenceID` parameter to get the events for a specific operation for a specific computer.</span></span>
<span data-ttu-id="d8303-190">Ad esempio, se si specifica 9 come `SequenceID`, `Trace-xDscOperaion` ottiene la traccia per l'operazione DSC al nono posto dopo l'ultima operazione:</span><span class="sxs-lookup"><span data-stu-id="d8303-190">For example, if you specify a `SequenceID` of 9, `Trace-xDscOperaion` get the trace for the DSC operation that was 9th from the last operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -SequenceID 9

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM Running consistency engine.
SRV1   OPERATIONAL  6/24/2016 10:51:52 AM The local configuration manager is updating the PSModulePath to WindowsPowerShell\Modules;C:\Prog...
SRV1   OPERATIONAL  6/24/2016 10:51:53 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 10:51:54 AM Operation Consistency Check or Pull completed successfully.
```

<span data-ttu-id="d8303-191">Passare il **GUID** assegnato a un'operazione DSC specifica (come restituito dal `Get-xDscOperation` cmdlet) per ottenere i dettagli dell'evento per l'operazione DSC:</span><span class="sxs-lookup"><span data-stu-id="d8303-191">Pass the **GUID** assigned to a specific DSC operation (as returned by the `Get-xDscOperation` cmdlet) to get the event details for that DSC operation:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -JobID 9e0bfb6b-3a3a-11e6-9165-00155d390509

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 from computer NULL.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Starting consistency engine.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Current.mof.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature, [xDSCWebService]PSDSCPullServer.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with resource name [WindowsFeature]DSC...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[WindowsFeature]DSCServiceFeature] The operation 'Get...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCServiceFeature] True in 0.3130 sec...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCServiceFeature]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with resource name [xDSCWebService]P...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Ensure
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Port
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check Physical Path ...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Check State
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [[xDSCWebService]PSDSCPullServer] Get Full Path for We...
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCPullServer] True in 0.0160 seconds.
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCPullServer]
SRV1   VERBOSE      6/24/2016 11:36:56 AM [SRV1]:                            [] Consistency check completed.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV1   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV1   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCache.mof
```

<span data-ttu-id="d8303-192">Si noti che, poiché `Trace-xDscOperation` aggrega gli eventi dei registri di debug, operativo e analitico, verrà chiesto di abilitare questi registri, come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="d8303-192">Note that, since `Trace-xDscOperation` aggregates events from the Analytic, Debug, and Operational logs, it will prompt you to enable these logs as described above.</span></span>

<span data-ttu-id="d8303-193">In alternativa, è possibile raccogliere informazioni sugli eventi salvando l'output di `Trace-xDscOperation` in una variabile.</span><span class="sxs-lookup"><span data-stu-id="d8303-193">Alternately, you can gather information on the events by saving the output of `Trace-xDscOperation` into a variable.</span></span> <span data-ttu-id="d8303-194">È possibile usare i comandi seguenti per visualizzare tutti gli eventi per un'operazione DSC specifica.</span><span class="sxs-lookup"><span data-stu-id="d8303-194">You can use the following commands to display all the events for a particular DSC operation.</span></span>

```powershell
PS C:\DiagnosticsTest> $Trace = Trace-xDscOperation -SequenceID 4

PS C:\DiagnosticsTest> $Trace.Event
```

<span data-ttu-id="d8303-195">In questo modo, verranno visualizzati gli stessi risultati del cmdlet `Get-WinEvent`, come nell'output seguente:</span><span class="sxs-lookup"><span data-stu-id="d8303-195">This will display the same results as the `Get-WinEvent` cmdlet, such as in the output below:</span></span>

```output
   ProviderName: Microsoft-Windows-DSC

TimeCreated                     Id LevelDisplayName Message
-----------                     -- ---------------- -------
6/23/2016 1:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 1:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:07:00 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:07:01 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 2:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 2:36:56 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:06:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:06:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 3:36:55 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 3:36:55 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:06:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 4:36:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 4:36:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 5:36:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 5:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 6:36:56 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 6:36:57 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:06:52 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:06:53 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 7:36:53 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
6/23/2016 7:36:54 AM          4343 Information      The DscTimer has successfully run LCM method PerformRequiredConfigurationChecks with flag 5.
6/23/2016 8:06:54 AM          4312 Information      The DscTimer is running LCM method PerformRequiredConfigurationChecks with the flag set to 5.
```

<span data-ttu-id="d8303-196">Idealmente, è consigliabile usare prima di tutto `Get-xDscOperation` per elencare le ultime esecuzioni della configurazione DSC nei computer.</span><span class="sxs-lookup"><span data-stu-id="d8303-196">Ideally, you would first use `Get-xDscOperation` to list out the last few DSC configuration runs on your machines.</span></span> <span data-ttu-id="d8303-197">In seguito, è possibile esaminare qualsiasi singola operazione (usando il campo SequenceID o JobID) con `Trace-xDscOperation` per determinare le azioni eseguite in background.</span><span class="sxs-lookup"><span data-stu-id="d8303-197">Following this, you can examine any single operation (using its SequenceID or JobID) with `Trace-xDscOperation` to discover what it did behind the scenes.</span></span>

### <a name="getting-events-for-a-remote-computer"></a><span data-ttu-id="d8303-198">Acquisizione degli eventi per un computer remoto</span><span class="sxs-lookup"><span data-stu-id="d8303-198">Getting events for a remote computer</span></span>

<span data-ttu-id="d8303-199">Utilizzare il parametro `ComputerName` del cmdlet `Trace-xDscOperation` per acquisire i dettagli dell'evento in un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="d8303-199">Use the `ComputerName` parameter of the `Trace-xDscOperation` cmdlet to get the event details on a remote computer.</span></span> <span data-ttu-id="d8303-200">Prima di procedere, è necessario creare una regola firewall per consentire l'amministrazione remota nel computer remoto:</span><span class="sxs-lookup"><span data-stu-id="d8303-200">Before you can do this, you have to create a firewall rule to allow remote administration on the remote computer:</span></span>

```powershell
New-NetFirewallRule -Name "Service RemoteAdmin" -DisplayName "Remote" -Action Allow
```

<span data-ttu-id="d8303-201">Ora è possibile specificare il computer nella chiamata a `Trace-xDscOperation`:</span><span class="sxs-lookup"><span data-stu-id="d8303-201">Now you can specify that computer in your call to `Trace-xDscOperation`:</span></span>

```powershell
PS C:\DiagnosticsTest> Trace-xDscOperation -ComputerName SRV2 -Credential Get-Credential -SequenceID 5

ComputerName   EventType    TimeCreated           Message
------------   ---------    -----------           -------
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull started by user sid S-1-5-20 f...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Running consistency engine.
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Starting consistency...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Applying configuration from C:\Windows\System32\Configuration\Curr...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Parsing the configuration to apply.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM  Resource execution sequence :: [WindowsFeature]DSCServiceFeature,...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[WindowsFeature]DSCSer...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_RoleResource with re...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[WindowsFeature]DSCSer...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Resource ]  [[xDSCWebService]PSDSCP...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Executing operations for PS DSC resource MSFT_xDSCWebService with ...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ Start  Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Test     ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]: LCM:  [ End    Resource ]  [[xDSCWebService]PSDSCP...
SRV2   VERBOSE      6/24/2016 11:36:56 AM [SRV2]:                            [] Consistency check co...
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Consistency engine was run successfully.
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Job runs under the following LCM setting. ...
SRV2   OPERATIONAL  6/24/2016 11:36:56 AM Operation Consistency Check or Pull completed successfully.
SRV2   ANALYTIC     6/24/2016 11:36:56 AM Deleting file from C:\Windows\System32\Configuration\DSCEngineCach...
```

## <a name="my-resources-wont-update-how-to-reset-the-cache"></a><span data-ttu-id="d8303-202">Risorse personali non vengono aggiornate: Come reimpostare la cache</span><span class="sxs-lookup"><span data-stu-id="d8303-202">My resources won't update: How to reset the cache</span></span>

<span data-ttu-id="d8303-203">Il motore DSC memorizza nella cache le risorse implementate come modulo di PowerShell, per garantire maggiore efficienza.</span><span class="sxs-lookup"><span data-stu-id="d8303-203">The DSC engine caches resources implemented as a PowerShell module for efficiency purposes.</span></span>
<span data-ttu-id="d8303-204">Tuttavia, ciò può provocare problemi quando si crea una risorsa e contemporaneamente la si testa, perché DSC carica la versione memorizzata nella cache fino a quando non viene riavviato il processo.</span><span class="sxs-lookup"><span data-stu-id="d8303-204">However, this can cause problems when you are authoring a resource and testing it simultaneously because DSC will load the cached version until the process is restarted.</span></span> <span data-ttu-id="d8303-205">Per fare in modo che DSC carichi la versione più recente, è necessario terminare in modo esplicito il processo che ospita il motore DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-205">The only way to make DSC load the newer version is to explicitly kill the process hosting the DSC engine.</span></span>

<span data-ttu-id="d8303-206">Analogamente, quando si esegue `Start-DscConfiguration`, dopo l'aggiunta e la modifica di una risorsa personalizzata, la modifica potrebbe non venire applicata fino a quando il computer non viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="d8303-206">Similarly, when you run `Start-DscConfiguration`, after adding and modifying a custom resource, the modification may not execute unless, or until, the computer is rebooted.</span></span> <span data-ttu-id="d8303-207">Ciò avviene perché DSC viene eseguito nel processo host del provider WMI (WmiPrvSE) e in genere ci sono molte istanze di WmiPrvSE in esecuzione contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d8303-207">This is because DSC runs in the WMI Provider Host Process (WmiPrvSE), and usually, there are many instances of WmiPrvSE running at once.</span></span> <span data-ttu-id="d8303-208">Quando si riavvia, il processo host viene riavviato e la cache viene cancellata.</span><span class="sxs-lookup"><span data-stu-id="d8303-208">When you reboot, the host process is restarted and the cache is cleared.</span></span>

<span data-ttu-id="d8303-209">Per riciclare la configurazione e cancellare la cache senza riavviare il computer, è necessario arrestare e quindi riavviare il processo host.</span><span class="sxs-lookup"><span data-stu-id="d8303-209">To successfully recycle the configuration and clear the cache without rebooting, you must stop and then restart the host process.</span></span> <span data-ttu-id="d8303-210">Questa operazione può essere eseguita per ogni istanza, identificando il processo, arrestandolo e riavviandolo.</span><span class="sxs-lookup"><span data-stu-id="d8303-210">This can be done on a per instance basis, whereby you identify the process, stop it, and restart it.</span></span> <span data-ttu-id="d8303-211">In alternativa, è possibile usare `DebugMode`, come illustrato di seguito, per ricaricare la risorsa PowerShell DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-211">Or, you can use `DebugMode`, as demonstrated below, to reload the PowerShell DSC resource.</span></span>

<span data-ttu-id="d8303-212">Per identificare il processo che ospita il motore DSC e arrestarlo per ogni istanza, è possibile elencare l'ID processo di WmiPrvSE che ospita il motore DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-212">To identify which process is hosting the DSC engine and stop it on a per instance basis, you can list the process ID of the WmiPrvSE which is hosting the DSC engine.</span></span> <span data-ttu-id="d8303-213">Quindi, per aggiornare il provider, arrestare il processo WmiPrvSE usando i comandi seguenti ed eseguire **Start-DscConfiguration** di nuovo.</span><span class="sxs-lookup"><span data-stu-id="d8303-213">Then, to update the provider, stop the WmiPrvSE process using the commands below, and then run **Start-DscConfiguration** again.</span></span>

```powershell
###
### find the process that is hosting the DSC engine
###
$dscProcessID = Get-WmiObject msft_providers |
Where-Object {$_.provider -like 'dsccore'} |
Select-Object -ExpandProperty HostProcessIdentifier

###
### Stop the process
###
Get-Process -Id $dscProcessID | Stop-Process
```

## <a name="using-debugmode"></a><span data-ttu-id="d8303-214">Uso di DebugMode</span><span class="sxs-lookup"><span data-stu-id="d8303-214">Using DebugMode</span></span>

<span data-ttu-id="d8303-215">È possibile configurare Gestione configurazione locale per DSC in modo da usare `DebugMode` per cancellare sempre la cache quando il processo host viene riavviato.</span><span class="sxs-lookup"><span data-stu-id="d8303-215">You can configure the DSC Local Configuration Manager (LCM) to use `DebugMode` to always clear the cache when the host process is restarted.</span></span> <span data-ttu-id="d8303-216">Se l'impostazione è **TRUE**, il motore ricarica sempre la risorsa PowerShell DSC.</span><span class="sxs-lookup"><span data-stu-id="d8303-216">When set to **TRUE**, it causes the engine to always reload the PowerShell DSC resource.</span></span> <span data-ttu-id="d8303-217">Dopo aver terminato di scrivere la risorsa, è possibile impostare di nuovo il valore su **FALSE** per ripristinare il comportamento del motore in base a cui i moduli vengono memorizzati nella cache.</span><span class="sxs-lookup"><span data-stu-id="d8303-217">Once you are done writing your resource, you can set it back to **FALSE** and the engine will revert to its behavior of caching the modules.</span></span>

<span data-ttu-id="d8303-218">Di seguito è illustrato in che modo `DebugMode` può aggiornare automaticamente la cache.</span><span class="sxs-lookup"><span data-stu-id="d8303-218">Following is a demonstration to show how `DebugMode` can automatically refresh the cache.</span></span> <span data-ttu-id="d8303-219">Si analizzi prima di tutto la configurazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="d8303-219">First, let's look at the default configuration:</span></span>

```powershell
PS C:\> Get-DscLocalConfigurationManager
```

```output
AllowModuleOverwrite           : False
CertificateID                  :
ConfigurationID                :
ConfigurationMode              : ApplyAndMonitor
ConfigurationModeFrequencyMins : 30
Credential                     :
DebugMode                      : {None}
DownloadManagerCustomData      :
DownloadManagerName            :
LocalConfigurationManagerState : Ready
RebootNodeIfNeeded             : False
RefreshFrequencyMins           : 15
RefreshMode                    : PUSH
PSComputerName                 :
```

<span data-ttu-id="d8303-220">È possibile vedere che `DebugMode` è impostato su **"None"**.</span><span class="sxs-lookup"><span data-stu-id="d8303-220">You can see that `DebugMode` is set to **"None"**.</span></span>

<span data-ttu-id="d8303-221">Per la dimostrazione di `DebugMode`, usare la risorsa di PowerShell seguente:</span><span class="sxs-lookup"><span data-stu-id="d8303-221">To set up the `DebugMode` demonstration, use the following PowerShell resource:</span></span>

```powershell
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    "1" | Out-File -PSPath "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        $onlyProperty
    )
    return $false
}
```

<span data-ttu-id="d8303-222">Creare quindi una configurazione usando la risorsa precedente denominata `TestProviderDebugMode`:</span><span class="sxs-lookup"><span data-stu-id="d8303-222">Now, author a configuration using the above resource called `TestProviderDebugMode`:</span></span>

```powershell
Configuration ConfigTestDebugMode
{
    Import-DscResource -Name TestProviderDebugMode
    Node localhost
    {
        TestProviderDebugMode test
        {
            onlyProperty = "blah"
        }
    }
}
ConfigTestDebugMode
```

<span data-ttu-id="d8303-223">Si noterà che il contenuto del file `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` è **1**.</span><span class="sxs-lookup"><span data-stu-id="d8303-223">You will see that the contents of file: `$env:SystemDrive\OutputFromTestProviderDebugMode.txt` is **1**.</span></span>

<span data-ttu-id="d8303-224">Aggiornare quindi il codice del provider usando lo script seguente:</span><span class="sxs-lookup"><span data-stu-id="d8303-224">Now, update the provider code using the following script:</span></span>

```powershell
$newResourceOutput = Get-Random -Minimum 5 -Maximum 30
$content = @"
function Get-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return @{onlyProperty = Get-Content -Path "$env:SystemDrive\OutputFromTestProviderDebugMode.txt"}
}
function Set-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    "$newResourceOutput" | Out-File -PSPath C:\OutputFromTestProviderDebugMode.txt
}
function Test-TargetResource
{
    param
    (
        [Parameter(Mandatory)]
        `$onlyProperty
    )
    return `$false
}
"@ | Out-File -FilePath "C:\Program Files\WindowsPowerShell\Modules\MyPowerShellModules\DSCResources\TestProviderDebugMode\TestProviderDebugMode.psm1
```

<span data-ttu-id="d8303-225">Questo script genera un numero casuale e aggiorna di conseguenza il codice del provider.</span><span class="sxs-lookup"><span data-stu-id="d8303-225">This script generates a random number and updates the provider code accordingly.</span></span> <span data-ttu-id="d8303-226">Con `DebugMode` impostato su false, i contenuti del file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" non vengono mai modificati.</span><span class="sxs-lookup"><span data-stu-id="d8303-226">With `DebugMode` set to false, the contents of the file "**$env:SystemDrive\OutputFromTestProviderDebugMode.txt**" are never changed.</span></span>

<span data-ttu-id="d8303-227">A questo punto, impostare `DebugMode` su **"ForceModuleImport"** nello script di configurazione:</span><span class="sxs-lookup"><span data-stu-id="d8303-227">Now, set `DebugMode` to **"ForceModuleImport"** in your configuration script:</span></span>

```powershell
LocalConfigurationManager
{
    DebugMode = "ForceModuleImport"
}
```

<span data-ttu-id="d8303-228">Quando si esegue di nuovo lo script precedente, si noterà che il contenuto del file è diverso ogni volta.</span><span class="sxs-lookup"><span data-stu-id="d8303-228">When you run the above script again, you will see that the content of the file is different every time.</span></span> <span data-ttu-id="d8303-229">È possibile eseguire `Get-DscConfiguration` per verificare.</span><span class="sxs-lookup"><span data-stu-id="d8303-229">(You can run `Get-DscConfiguration` to check it).</span></span> <span data-ttu-id="d8303-230">Di seguito è riportato il risultato di due esecuzioni aggiuntive (quando si esegue lo script, i risultati potrebbero essere diversi):</span><span class="sxs-lookup"><span data-stu-id="d8303-230">Below is the result of two additional runs (your results may be different when you run the script):</span></span>

```powershell
PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
20                                      localhost

PS C:\> Get-DscConfiguration -CimSession (New-CimSession localhost)

onlyProperty                            PSComputerName
------------                            --------------
14                                      localhost
```

## <a name="see-also"></a><span data-ttu-id="d8303-231">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d8303-231">See Also</span></span>

### <a name="concepts"></a><span data-ttu-id="d8303-232">Concetti</span><span class="sxs-lookup"><span data-stu-id="d8303-232">Concepts</span></span>

- [<span data-ttu-id="d8303-233">Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate</span><span class="sxs-lookup"><span data-stu-id="d8303-233">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](../resources/authoringResource.md)

### <a name="other-resources"></a><span data-ttu-id="d8303-234">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d8303-234">Other Resources</span></span>

- [<span data-ttu-id="d8303-235">Cmdlet di Windows PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="d8303-235">Windows PowerShell Desired State Configuration Cmdlets</span></span>](/powershell/module/psdesiredstateconfiguration/)
