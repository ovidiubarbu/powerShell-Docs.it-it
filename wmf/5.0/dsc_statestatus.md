---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 0e8d0cb1e4afa7bc791d45bfb0b981654cb09ed5
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892570"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="980bf-102">Rappresentazione degli stati unificata e coerente</span><span class="sxs-lookup"><span data-stu-id="980bf-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="980bf-103">In questa versione è stata introdotta una serie di miglioramenti per lo stato di Gestione configurazione locale e lo stato di DSC generati dall'automazione.</span><span class="sxs-lookup"><span data-stu-id="980bf-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="980bf-104">I miglioramenti includono rappresentazioni dello stato unificate e coerenti, una proprietà datetime gestibile per gli oggetti di stato restituiti dal cmdlet `Get-DscConfigurationStatus` e una proprietà con dettagli avanzati sullo stato di Gestione configurazione locale restituita dal cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="980bf-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="980bf-105">La rappresentazione dello stato di Gestione configurazione locale e delle operazioni DSC è stata rivista e unificata in base alle regole seguenti:</span><span class="sxs-lookup"><span data-stu-id="980bf-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="980bf-106">La risorsa non elaborata non influisce sullo stato di Gestione configurazione locale e DSC.</span><span class="sxs-lookup"><span data-stu-id="980bf-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="980bf-107">Gestione configurazione locale interrompe l'elaborazione di ulteriori risorse quando rileva una risorsa che richiede il riavvio.</span><span class="sxs-lookup"><span data-stu-id="980bf-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="980bf-108">Una risorsa che richiede il riavvio non è nello stato desiderato fino all'effettiva esecuzione del riavvio.</span><span class="sxs-lookup"><span data-stu-id="980bf-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="980bf-109">In presenza di una risorsa in errore, Gestione configurazione locale continua con l'elaborazione di altre risorse, a condizione che non siano dipendenti da quelle in errore.</span><span class="sxs-lookup"><span data-stu-id="980bf-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="980bf-110">Lo stato complessivo restituito dal cmdlet `Get-DscConfigurationStatus` è il soprainsieme dello stato di tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="980bf-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="980bf-111">Lo stato PendingReboot è un soprainsieme dello stato PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="980bf-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

   <span data-ttu-id="980bf-112">Nella tabella seguente sono illustrate le proprietà correlate allo stato risultanti in alcuni scenari tipici.</span><span class="sxs-lookup"><span data-stu-id="980bf-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

   | <span data-ttu-id="980bf-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="980bf-113">Scenario</span></span>                    | <span data-ttu-id="980bf-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="980bf-114">LCMState</span></span>       | <span data-ttu-id="980bf-115">Stato</span><span class="sxs-lookup"><span data-stu-id="980bf-115">Status</span></span> | <span data-ttu-id="980bf-116">RebootRequested</span><span class="sxs-lookup"><span data-stu-id="980bf-116">Reboot Requested</span></span>  | <span data-ttu-id="980bf-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="980bf-117">ResourcesInDesiredState</span></span>  | <span data-ttu-id="980bf-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="980bf-118">ResourcesNotInDesiredState</span></span> |
   |---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
   | <span data-ttu-id="980bf-119">S**^**</span><span class="sxs-lookup"><span data-stu-id="980bf-119">S**^**</span></span>                          | <span data-ttu-id="980bf-120">Idle</span><span class="sxs-lookup"><span data-stu-id="980bf-120">Idle</span></span>                 | <span data-ttu-id="980bf-121">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="980bf-121">Success</span></span>    | <span data-ttu-id="980bf-122">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-122">$false</span></span>        | <span data-ttu-id="980bf-123">S</span><span class="sxs-lookup"><span data-stu-id="980bf-123">S</span></span>                            | <span data-ttu-id="980bf-124">$null</span><span class="sxs-lookup"><span data-stu-id="980bf-124">$null</span></span>                          |
   | <span data-ttu-id="980bf-125">F**^**</span><span class="sxs-lookup"><span data-stu-id="980bf-125">F**^**</span></span>                          | <span data-ttu-id="980bf-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="980bf-126">PendingConfiguration</span></span> | <span data-ttu-id="980bf-127">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-127">Failure</span></span>    | <span data-ttu-id="980bf-128">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-128">$false</span></span>        | <span data-ttu-id="980bf-129">$null</span><span class="sxs-lookup"><span data-stu-id="980bf-129">$null</span></span>                        | <span data-ttu-id="980bf-130">F</span><span class="sxs-lookup"><span data-stu-id="980bf-130">F</span></span>                              |
   | <span data-ttu-id="980bf-131">S,F</span><span class="sxs-lookup"><span data-stu-id="980bf-131">S,F</span></span>                             | <span data-ttu-id="980bf-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="980bf-132">PendingConfiguration</span></span> | <span data-ttu-id="980bf-133">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-133">Failure</span></span>    | <span data-ttu-id="980bf-134">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-134">$false</span></span>        | <span data-ttu-id="980bf-135">S</span><span class="sxs-lookup"><span data-stu-id="980bf-135">S</span></span>                            | <span data-ttu-id="980bf-136">F</span><span class="sxs-lookup"><span data-stu-id="980bf-136">F</span></span>                              |
   | <span data-ttu-id="980bf-137">F,S</span><span class="sxs-lookup"><span data-stu-id="980bf-137">F,S</span></span>                             | <span data-ttu-id="980bf-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="980bf-138">PendingConfiguration</span></span> | <span data-ttu-id="980bf-139">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-139">Failure</span></span>    | <span data-ttu-id="980bf-140">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-140">$false</span></span>        | <span data-ttu-id="980bf-141">S</span><span class="sxs-lookup"><span data-stu-id="980bf-141">S</span></span>                            | <span data-ttu-id="980bf-142">F</span><span class="sxs-lookup"><span data-stu-id="980bf-142">F</span></span>                              |
   | <span data-ttu-id="980bf-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="980bf-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="980bf-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="980bf-144">PendingConfiguration</span></span> | <span data-ttu-id="980bf-145">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-145">Failure</span></span>    | <span data-ttu-id="980bf-146">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-146">$false</span></span>        | <span data-ttu-id="980bf-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="980bf-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="980bf-148">F</span><span class="sxs-lookup"><span data-stu-id="980bf-148">F</span></span>                              |
   | <span data-ttu-id="980bf-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="980bf-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="980bf-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="980bf-150">PendingConfiguration</span></span> | <span data-ttu-id="980bf-151">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-151">Failure</span></span>    | <span data-ttu-id="980bf-152">$false</span><span class="sxs-lookup"><span data-stu-id="980bf-152">$false</span></span>        | <span data-ttu-id="980bf-153">S</span><span class="sxs-lookup"><span data-stu-id="980bf-153">S</span></span>                            | <span data-ttu-id="980bf-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="980bf-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
   | <span data-ttu-id="980bf-155">S, r</span><span class="sxs-lookup"><span data-stu-id="980bf-155">S, r</span></span>                            | <span data-ttu-id="980bf-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="980bf-156">PendingReboot</span></span>        | <span data-ttu-id="980bf-157">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="980bf-157">Success</span></span>    | <span data-ttu-id="980bf-158">$true</span><span class="sxs-lookup"><span data-stu-id="980bf-158">$true</span></span>         | <span data-ttu-id="980bf-159">S</span><span class="sxs-lookup"><span data-stu-id="980bf-159">S</span></span>                            | <span data-ttu-id="980bf-160">r</span><span class="sxs-lookup"><span data-stu-id="980bf-160">r</span></span>                              |
   | <span data-ttu-id="980bf-161">F, r</span><span class="sxs-lookup"><span data-stu-id="980bf-161">F, r</span></span>                            | <span data-ttu-id="980bf-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="980bf-162">PendingReboot</span></span>        | <span data-ttu-id="980bf-163">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="980bf-163">Failure</span></span>    | <span data-ttu-id="980bf-164">$true</span><span class="sxs-lookup"><span data-stu-id="980bf-164">$true</span></span>         | <span data-ttu-id="980bf-165">$null</span><span class="sxs-lookup"><span data-stu-id="980bf-165">$null</span></span>                        | <span data-ttu-id="980bf-166">F, r</span><span class="sxs-lookup"><span data-stu-id="980bf-166">F, r</span></span>                           |
   | <span data-ttu-id="980bf-167">r, S</span><span class="sxs-lookup"><span data-stu-id="980bf-167">r, S</span></span>                            | <span data-ttu-id="980bf-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="980bf-168">PendingReboot</span></span>        | <span data-ttu-id="980bf-169">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="980bf-169">Success</span></span>    | <span data-ttu-id="980bf-170">$true</span><span class="sxs-lookup"><span data-stu-id="980bf-170">$true</span></span>         | <span data-ttu-id="980bf-171">$null</span><span class="sxs-lookup"><span data-stu-id="980bf-171">$null</span></span>                        | <span data-ttu-id="980bf-172">r</span><span class="sxs-lookup"><span data-stu-id="980bf-172">r</span></span>                              |
   | <span data-ttu-id="980bf-173">r, F</span><span class="sxs-lookup"><span data-stu-id="980bf-173">r, F</span></span>                            | <span data-ttu-id="980bf-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="980bf-174">PendingReboot</span></span>        | <span data-ttu-id="980bf-175">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="980bf-175">Success</span></span>    | <span data-ttu-id="980bf-176">$true</span><span class="sxs-lookup"><span data-stu-id="980bf-176">$true</span></span>         | <span data-ttu-id="980bf-177">$null</span><span class="sxs-lookup"><span data-stu-id="980bf-177">$null</span></span>                        | <span data-ttu-id="980bf-178">r</span><span class="sxs-lookup"><span data-stu-id="980bf-178">r</span></span>                              |

   <span data-ttu-id="980bf-179">^
   S<sub>i</sub>: una serie di risorse applicata correttamente F<sub>i</sub>: una serie di risorse applicata non correttamente r: una risorsa che richiede il riavvio\*</span><span class="sxs-lookup"><span data-stu-id="980bf-179">^
   S<sub>i</sub>: A series of resources that applied successfully F<sub>i</sub>: A series of resources that applied unsuccessfully r: A resource that requires reboot \*</span></span>

   ```powershell
   $LCMState = (Get-DscLocalConfigurationManager).LCMState
   $Status = (Get-DscConfigurationStatus).Status

   $RebootRequested = (Get-DscConfigurationStatus).RebootRequested

   $ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

   $ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
   ```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="980bf-180">Miglioramenti per il cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="980bf-180">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="980bf-181">Sono stati apportati alcuni miglioramenti al cmdlet `Get-DscConfigurationStatus` in questa versione.</span><span class="sxs-lookup"><span data-stu-id="980bf-181">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="980bf-182">In precedenza, la proprietà StartDate degli oggetti restituiti dal cmdlet è di tipo String.</span><span class="sxs-lookup"><span data-stu-id="980bf-182">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="980bf-183">Ora è di tipo Datetime e questo facilita operazioni complesse di selezione e filtro basate sulle proprietà intrinseche di un oggetto Datetime.</span><span class="sxs-lookup"><span data-stu-id="980bf-183">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *
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

<span data-ttu-id="980bf-184">Ecco un esempio che restituisce tutti i record di operazioni DSC eseguite nello stesso giorno della settimana di oggi.</span><span class="sxs-lookup"><span data-stu-id="980bf-184">Following is an example that returns all DSC operation records happened on the same day of week as today.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="980bf-185">Vengono eliminati i record delle operazioni che non apportano modifiche alla configurazione del nodo, ad esempio le operazioni di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="980bf-185">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="980bf-186">Pertanto `Test-DscConfiguration`, le operazioni `Get-DscConfiguration` non vengono più modificate negli oggetti restituiti dal cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="980bf-186">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span>
<span data-ttu-id="980bf-187">I record dell'operazione di impostazione della metaconfigurazione vengono aggiunti all'oggetto restituito dal cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="980bf-187">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="980bf-188">Di seguito è riportato un esempio di risultato restituito dal cmdlet `Get-DscConfigurationStatus` -All.</span><span class="sxs-lookup"><span data-stu-id="980bf-188">Following is an example of result returned from `Get-DscConfigurationStatus` –All cmdlet.</span></span>

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="980bf-189">Miglioramenti per il cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="980bf-189">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="980bf-190">Viene aggiunto un nuovo campo di LCMStateDetail all'oggetto restituito dal cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="980bf-190">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="980bf-191">Questo campo viene popolato quando LCMState è "Busy".</span><span class="sxs-lookup"><span data-stu-id="980bf-191">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="980bf-192">Può essere recuperato dal cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="980bf-192">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="980bf-193">Quello che segue è un esempio dell'output di un'operazione di monitoraggio continuo per una configurazione che richiede due riavvii in un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="980bf-193">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

```output
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