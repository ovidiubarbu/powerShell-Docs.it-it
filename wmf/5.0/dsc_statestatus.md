---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7b4e4dbeaf9c3c48e7b2dfc74435dfa2cd9c7ea7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/25/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="da5f5-102">Rappresentazione degli stati unificata e coerente</span><span class="sxs-lookup"><span data-stu-id="da5f5-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="da5f5-103">In questa versione è stata introdotta una serie di miglioramenti per lo stato di Gestione configurazione locale e lo stato di DSC generati dall'automazione.</span><span class="sxs-lookup"><span data-stu-id="da5f5-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="da5f5-104">I miglioramenti includono rappresentazioni dello stato unificate e coerenti, una proprietà datetime gestibile per gli oggetti di stato restituiti dal cmdlet Get-DscConfigurationStatus e una proprietà con dettagli avanzati sullo stato di Gestione configurazione locale restituita dal cmdlet Get-DscLocalConfigurationManager.</span><span class="sxs-lookup"><span data-stu-id="da5f5-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by Get-DscConfigurationStatus cmdlet and enhanced LCM state details property returned by Get-DscLocalConfigurationManager cmdlet.</span></span>

<span data-ttu-id="da5f5-105">La rappresentazione dello stato di Gestione configurazione locale e delle operazioni DSC è stata rivista e unificata in base alle regole seguenti:</span><span class="sxs-lookup"><span data-stu-id="da5f5-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>
1.  <span data-ttu-id="da5f5-106">La risorsa non elaborata non influisce sullo stato di Gestione configurazione locale e DSC.</span><span class="sxs-lookup"><span data-stu-id="da5f5-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2.  <span data-ttu-id="da5f5-107">Gestione configurazione locale interrompe l'elaborazione di ulteriori risorse quando rileva una risorsa che richiede il riavvio.</span><span class="sxs-lookup"><span data-stu-id="da5f5-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3.  <span data-ttu-id="da5f5-108">Una risorsa che richiede il riavvio non è nello stato desiderato fino all'effettiva esecuzione del riavvio.</span><span class="sxs-lookup"><span data-stu-id="da5f5-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4.  <span data-ttu-id="da5f5-109">In presenza di una risorsa in errore, Gestione configurazione locale continua con l'elaborazione di altre risorse, a condizione che non siano dipendenti da quelle in errore.</span><span class="sxs-lookup"><span data-stu-id="da5f5-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5.  <span data-ttu-id="da5f5-110">Lo stato complessivo restituito dal cmdlet Get-DscConfigurationStatus è il soprainsieme dello stato di tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="da5f5-110">The overall status returned by Get-DscConfigurationStatus cmdlet is the super set of all resources' status.</span></span>
6.  <span data-ttu-id="da5f5-111">Lo stato PendingReboot è un soprainsieme dello stato PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="da5f5-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="da5f5-112">Nella tabella seguente sono illustrate le proprietà correlate allo stato risultanti in alcuni scenari tipici.</span><span class="sxs-lookup"><span data-stu-id="da5f5-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="da5f5-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="da5f5-113">Scenario</span></span>                    | <span data-ttu-id="da5f5-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="da5f5-114">LCMState</span></span>       | <span data-ttu-id="da5f5-115">Stato</span><span class="sxs-lookup"><span data-stu-id="da5f5-115">Status</span></span> | <span data-ttu-id="da5f5-116">RebootRequested</span><span class="sxs-lookup"><span data-stu-id="da5f5-116">Reboot Requested</span></span>  | <span data-ttu-id="da5f5-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="da5f5-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="da5f5-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="da5f5-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="da5f5-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="da5f5-119">S**^**</span></span>                          | <span data-ttu-id="da5f5-120">Idle</span><span class="sxs-lookup"><span data-stu-id="da5f5-120">Idle</span></span>                 | <span data-ttu-id="da5f5-121">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="da5f5-121">Success</span></span>    | <span data-ttu-id="da5f5-122">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-122">$false</span></span>        | <span data-ttu-id="da5f5-123">S</span><span class="sxs-lookup"><span data-stu-id="da5f5-123">S</span></span>                            | <span data-ttu-id="da5f5-124">$null</span><span class="sxs-lookup"><span data-stu-id="da5f5-124">$null</span></span>                          |
| <span data-ttu-id="da5f5-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="da5f5-125">F**^**</span></span>                          | <span data-ttu-id="da5f5-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="da5f5-126">PendingConfiguration</span></span> | <span data-ttu-id="da5f5-127">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-127">Failure</span></span>    | <span data-ttu-id="da5f5-128">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-128">$false</span></span>        | <span data-ttu-id="da5f5-129">$null</span><span class="sxs-lookup"><span data-stu-id="da5f5-129">$null</span></span>                        | <span data-ttu-id="da5f5-130">F</span><span class="sxs-lookup"><span data-stu-id="da5f5-130">F</span></span>                              |
| <span data-ttu-id="da5f5-131">S,F</span><span class="sxs-lookup"><span data-stu-id="da5f5-131">S,F</span></span>                             | <span data-ttu-id="da5f5-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="da5f5-132">PendingConfiguration</span></span> | <span data-ttu-id="da5f5-133">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-133">Failure</span></span>    | <span data-ttu-id="da5f5-134">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-134">$false</span></span>        | <span data-ttu-id="da5f5-135">S</span><span class="sxs-lookup"><span data-stu-id="da5f5-135">S</span></span>                            | <span data-ttu-id="da5f5-136">F</span><span class="sxs-lookup"><span data-stu-id="da5f5-136">F</span></span>                              |
| <span data-ttu-id="da5f5-137">F,S</span><span class="sxs-lookup"><span data-stu-id="da5f5-137">F,S</span></span>                             | <span data-ttu-id="da5f5-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="da5f5-138">PendingConfiguration</span></span> | <span data-ttu-id="da5f5-139">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-139">Failure</span></span>    | <span data-ttu-id="da5f5-140">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-140">$false</span></span>        | <span data-ttu-id="da5f5-141">S</span><span class="sxs-lookup"><span data-stu-id="da5f5-141">S</span></span>                            | <span data-ttu-id="da5f5-142">F</span><span class="sxs-lookup"><span data-stu-id="da5f5-142">F</span></span>                              |
| <span data-ttu-id="da5f5-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="da5f5-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="da5f5-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="da5f5-144">PendingConfiguration</span></span> | <span data-ttu-id="da5f5-145">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-145">Failure</span></span>    | <span data-ttu-id="da5f5-146">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-146">$false</span></span>        | <span data-ttu-id="da5f5-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="da5f5-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="da5f5-148">F</span><span class="sxs-lookup"><span data-stu-id="da5f5-148">F</span></span>                              |
| <span data-ttu-id="da5f5-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="da5f5-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="da5f5-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="da5f5-150">PendingConfiguration</span></span> | <span data-ttu-id="da5f5-151">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-151">Failure</span></span>    | <span data-ttu-id="da5f5-152">$false</span><span class="sxs-lookup"><span data-stu-id="da5f5-152">$false</span></span>        | <span data-ttu-id="da5f5-153">S</span><span class="sxs-lookup"><span data-stu-id="da5f5-153">S</span></span>                            | <span data-ttu-id="da5f5-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="da5f5-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="da5f5-155">S, r</span><span class="sxs-lookup"><span data-stu-id="da5f5-155">S, r</span></span>                            | <span data-ttu-id="da5f5-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="da5f5-156">PendingReboot</span></span>        | <span data-ttu-id="da5f5-157">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="da5f5-157">Success</span></span>    | <span data-ttu-id="da5f5-158">$true</span><span class="sxs-lookup"><span data-stu-id="da5f5-158">$true</span></span>         | <span data-ttu-id="da5f5-159">S</span><span class="sxs-lookup"><span data-stu-id="da5f5-159">S</span></span>                            | <span data-ttu-id="da5f5-160">r</span><span class="sxs-lookup"><span data-stu-id="da5f5-160">r</span></span>                              |
| <span data-ttu-id="da5f5-161">F, r</span><span class="sxs-lookup"><span data-stu-id="da5f5-161">F, r</span></span>                            | <span data-ttu-id="da5f5-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="da5f5-162">PendingReboot</span></span>        | <span data-ttu-id="da5f5-163">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="da5f5-163">Failure</span></span>    | <span data-ttu-id="da5f5-164">$true</span><span class="sxs-lookup"><span data-stu-id="da5f5-164">$true</span></span>         | <span data-ttu-id="da5f5-165">$null</span><span class="sxs-lookup"><span data-stu-id="da5f5-165">$null</span></span>                        | <span data-ttu-id="da5f5-166">F, r</span><span class="sxs-lookup"><span data-stu-id="da5f5-166">F, r</span></span>                           |
| <span data-ttu-id="da5f5-167">r, S</span><span class="sxs-lookup"><span data-stu-id="da5f5-167">r, S</span></span>                            | <span data-ttu-id="da5f5-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="da5f5-168">PendingReboot</span></span>        | <span data-ttu-id="da5f5-169">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="da5f5-169">Success</span></span>    | <span data-ttu-id="da5f5-170">$true</span><span class="sxs-lookup"><span data-stu-id="da5f5-170">$true</span></span>         | <span data-ttu-id="da5f5-171">$null</span><span class="sxs-lookup"><span data-stu-id="da5f5-171">$null</span></span>                        | <span data-ttu-id="da5f5-172">r</span><span class="sxs-lookup"><span data-stu-id="da5f5-172">r</span></span>                              |
| <span data-ttu-id="da5f5-173">r, F</span><span class="sxs-lookup"><span data-stu-id="da5f5-173">r, F</span></span>                            | <span data-ttu-id="da5f5-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="da5f5-174">PendingReboot</span></span>        | <span data-ttu-id="da5f5-175">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="da5f5-175">Success</span></span>    | <span data-ttu-id="da5f5-176">$true</span><span class="sxs-lookup"><span data-stu-id="da5f5-176">$true</span></span>         | <span data-ttu-id="da5f5-177">$null</span><span class="sxs-lookup"><span data-stu-id="da5f5-177">$null</span></span>                        | <span data-ttu-id="da5f5-178">r</span><span class="sxs-lookup"><span data-stu-id="da5f5-178">r</span></span>                              |

<span data-ttu-id="da5f5-179">^ S<sub>i</sub>: una serie di risorse applicata correttamente F<sub>i</sub>: una serie di risorse applicata non correttamente r: una risorsa che richiede il riavvio\*</span><span class="sxs-lookup"><span data-stu-id="da5f5-179">^ S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="da5f5-180">Miglioramenti per il cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="da5f5-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="da5f5-181">In questa versione sono stati introdotti alcuni miglioramenti per il cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="da5f5-181">A few enhancements have been made to Get-DscConfigurationStatus cmdlet in this release.</span></span> <span data-ttu-id="da5f5-182">In precedenza, la proprietà StartDate degli oggetti restituiti dal cmdlet è di tipo String.</span><span class="sxs-lookup"><span data-stu-id="da5f5-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="da5f5-183">Ora è di tipo Datetime e questo facilita operazioni complesse di selezione e filtro basate sulle proprietà intrinseche di un oggetto Datetime.</span><span class="sxs-lookup"><span data-stu-id="da5f5-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | fl *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

<span data-ttu-id="da5f5-184">Ecco un esempio che restituisce tutti i record di operazioni DSC eseguite nello stesso giorno della settimana di oggi.</span><span class="sxs-lookup"><span data-stu-id="da5f5-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | where { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="da5f5-185">Vengono eliminati i record delle operazioni che non apportano modifiche alla configurazione del nodo, ad esempio le operazioni di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="da5f5-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="da5f5-186">Pertanto, le operazioni Test-DscConfiguration e Get-DscConfiguration non vengono più modificate negli oggetti restituiti dal cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="da5f5-186">Therefore, Test-DscConfiguration, Get-DscConfiguration operations are no longer adulterated in returned objects from Get-DscConfigurationStatus cmdlet.</span></span>
<span data-ttu-id="da5f5-187">I record dell'operazione di impostazione della metaconfigurazione viene aggiunto all'oggetto restituito dal cmdlet Get-DscConfigurationStatus.</span><span class="sxs-lookup"><span data-stu-id="da5f5-187">Records of meta configuration setting operation is added to the return of Get-DscConfigurationStatus cmdlet.</span></span>

<span data-ttu-id="da5f5-188">Di seguito è riportato un esempio di risultato restituito dal cmdlet Get-DscConfigurationStatus -All.</span><span class="sxs-lookup"><span data-stu-id="da5f5-188">Following is an example of result returned from Get-DscConfigurationStatus –All cmdlet.</span></span>

```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="da5f5-189">Miglioramenti per il cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="da5f5-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="da5f5-190">È stato aggiunto un nuovo campo LCMStateDetail all'oggetto restituito dal cmdlet Get-DscLocalConfigurationManager.</span><span class="sxs-lookup"><span data-stu-id="da5f5-190">A new field of LCMStateDetail is added to the object returned from Get-DscLocalConfigurationManager cmdlet.</span></span> <span data-ttu-id="da5f5-191">Questo campo viene popolato quando LCMState è "Busy".</span><span class="sxs-lookup"><span data-stu-id="da5f5-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="da5f5-192">Può essere recuperato dal cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="da5f5-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="da5f5-193">Quello che segue è un esempio dell'output di un'operazione di monitoraggio continuo per una configurazione che richiede due riavvii in un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="da5f5-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
