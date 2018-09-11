---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339872"
---
# <a name="unified-and-consistent-state-and-status-representation"></a><span data-ttu-id="b29dc-102">Rappresentazione degli stati unificata e coerente</span><span class="sxs-lookup"><span data-stu-id="b29dc-102">Unified and Consistent State and Status Representation</span></span>

<span data-ttu-id="b29dc-103">In questa versione è stata introdotta una serie di miglioramenti per lo stato di Gestione configurazione locale e lo stato di DSC generati dall'automazione.</span><span class="sxs-lookup"><span data-stu-id="b29dc-103">A series of enhancements have been made in this release for automations built LCM state and DSC status.</span></span> <span data-ttu-id="b29dc-104">I miglioramenti includono rappresentazioni dello stato unificate e coerenti, una proprietà datetime gestibile per gli oggetti di stato restituiti dal cmdlet `Get-DscConfigurationStatus` e una proprietà con dettagli avanzati sullo stato di Gestione configurazione locale restituita dal cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="b29dc-104">These include unified and consistent state and status representations, manageable datetime property of status objects returned by `Get-DscConfigurationStatus` cmdlet and enhanced LCM state details property returned by `Get-DscLocalConfigurationManager` cmdlet.</span></span>

<span data-ttu-id="b29dc-105">La rappresentazione dello stato di Gestione configurazione locale e delle operazioni DSC è stata rivista e unificata in base alle regole seguenti:</span><span class="sxs-lookup"><span data-stu-id="b29dc-105">The representation of LCM state and DSC operation status are revisited and unified according to following rules:</span></span>

1. <span data-ttu-id="b29dc-106">La risorsa non elaborata non influisce sullo stato di Gestione configurazione locale e DSC.</span><span class="sxs-lookup"><span data-stu-id="b29dc-106">Notprocessed resource does not impact LCM state and DSC status.</span></span>
2. <span data-ttu-id="b29dc-107">Gestione configurazione locale interrompe l'elaborazione di ulteriori risorse quando rileva una risorsa che richiede il riavvio.</span><span class="sxs-lookup"><span data-stu-id="b29dc-107">LCM stop processing further resources once it encounters a resource that requests reboot.</span></span>
3. <span data-ttu-id="b29dc-108">Una risorsa che richiede il riavvio non è nello stato desiderato fino all'effettiva esecuzione del riavvio.</span><span class="sxs-lookup"><span data-stu-id="b29dc-108">A resource that requests reboot is not in desired state until reboot actually happens.</span></span>
4. <span data-ttu-id="b29dc-109">In presenza di una risorsa in errore, Gestione configurazione locale continua con l'elaborazione di altre risorse, a condizione che non siano dipendenti da quelle in errore.</span><span class="sxs-lookup"><span data-stu-id="b29dc-109">After encountering a resource that fails, LCM keeps processing further resources as long as they are not dependent on the failure one.</span></span>
5. <span data-ttu-id="b29dc-110">Lo stato complessivo restituito dal cmdlet `Get-DscConfigurationStatus` è il soprainsieme dello stato di tutte le risorse.</span><span class="sxs-lookup"><span data-stu-id="b29dc-110">The overall status returned by `Get-DscConfigurationStatus` cmdlet is the super set of all resources' status.</span></span>
6. <span data-ttu-id="b29dc-111">Lo stato PendingReboot è un soprainsieme dello stato PendingConfiguration.</span><span class="sxs-lookup"><span data-stu-id="b29dc-111">The PendingReboot state is a superset of PendingConfiguration state.</span></span>

<span data-ttu-id="b29dc-112">Nella tabella seguente sono illustrate le proprietà correlate allo stato risultanti in alcuni scenari tipici.</span><span class="sxs-lookup"><span data-stu-id="b29dc-112">The table below illustrates the resultant state and status related properties under a few typical scenarios.</span></span>

| <span data-ttu-id="b29dc-113">Scenario</span><span class="sxs-lookup"><span data-stu-id="b29dc-113">Scenario</span></span>                        | <span data-ttu-id="b29dc-114">LCMState</span><span class="sxs-lookup"><span data-stu-id="b29dc-114">LCMState</span></span>             | <span data-ttu-id="b29dc-115">Stato</span><span class="sxs-lookup"><span data-stu-id="b29dc-115">Status</span></span>     | <span data-ttu-id="b29dc-116">RebootRequested</span><span class="sxs-lookup"><span data-stu-id="b29dc-116">Reboot Requested</span></span> | <span data-ttu-id="b29dc-117">ResourcesInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b29dc-117">ResourcesInDesiredState</span></span>   | <span data-ttu-id="b29dc-118">ResourcesNotInDesiredState</span><span class="sxs-lookup"><span data-stu-id="b29dc-118">ResourcesNotInDesiredState</span></span> |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| <span data-ttu-id="b29dc-119">S<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-119">S<sub>i</sub></span></span>                   | <span data-ttu-id="b29dc-120">Idle</span><span class="sxs-lookup"><span data-stu-id="b29dc-120">Idle</span></span>                 | <span data-ttu-id="b29dc-121">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="b29dc-121">Success</span></span>    | <span data-ttu-id="b29dc-122">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-122">$false</span></span>        | <span data-ttu-id="b29dc-123">S</span><span class="sxs-lookup"><span data-stu-id="b29dc-123">S</span></span>                            | <span data-ttu-id="b29dc-124">$null</span><span class="sxs-lookup"><span data-stu-id="b29dc-124">$null</span></span>                          |
| <span data-ttu-id="b29dc-125">F<sub>i</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-125">F<sub>i</sub></span></span>                   | <span data-ttu-id="b29dc-126">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29dc-126">PendingConfiguration</span></span> | <span data-ttu-id="b29dc-127">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-127">Failure</span></span>    | <span data-ttu-id="b29dc-128">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-128">$false</span></span>        | <span data-ttu-id="b29dc-129">$null</span><span class="sxs-lookup"><span data-stu-id="b29dc-129">$null</span></span>                        | <span data-ttu-id="b29dc-130">F</span><span class="sxs-lookup"><span data-stu-id="b29dc-130">F</span></span>                              |
| <span data-ttu-id="b29dc-131">S,F</span><span class="sxs-lookup"><span data-stu-id="b29dc-131">S,F</span></span>                             | <span data-ttu-id="b29dc-132">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29dc-132">PendingConfiguration</span></span> | <span data-ttu-id="b29dc-133">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-133">Failure</span></span>    | <span data-ttu-id="b29dc-134">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-134">$false</span></span>        | <span data-ttu-id="b29dc-135">S</span><span class="sxs-lookup"><span data-stu-id="b29dc-135">S</span></span>                            | <span data-ttu-id="b29dc-136">F</span><span class="sxs-lookup"><span data-stu-id="b29dc-136">F</span></span>                              |
| <span data-ttu-id="b29dc-137">F,S</span><span class="sxs-lookup"><span data-stu-id="b29dc-137">F,S</span></span>                             | <span data-ttu-id="b29dc-138">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29dc-138">PendingConfiguration</span></span> | <span data-ttu-id="b29dc-139">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-139">Failure</span></span>    | <span data-ttu-id="b29dc-140">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-140">$false</span></span>        | <span data-ttu-id="b29dc-141">S</span><span class="sxs-lookup"><span data-stu-id="b29dc-141">S</span></span>                            | <span data-ttu-id="b29dc-142">F</span><span class="sxs-lookup"><span data-stu-id="b29dc-142">F</span></span>                              |
| <span data-ttu-id="b29dc-143">S<sub>1</sub>, F, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-143">S<sub>1</sub>, F, S<sub>2</sub></span></span> | <span data-ttu-id="b29dc-144">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29dc-144">PendingConfiguration</span></span> | <span data-ttu-id="b29dc-145">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-145">Failure</span></span>    | <span data-ttu-id="b29dc-146">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-146">$false</span></span>        | <span data-ttu-id="b29dc-147">S<sub>1</sub>, S<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-147">S<sub>1</sub>, S<sub>2</sub></span></span> | <span data-ttu-id="b29dc-148">F</span><span class="sxs-lookup"><span data-stu-id="b29dc-148">F</span></span>                              |
| <span data-ttu-id="b29dc-149">F<sub>1</sub>, S, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-149">F<sub>1</sub>, S, F<sub>2</sub></span></span> | <span data-ttu-id="b29dc-150">PendingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b29dc-150">PendingConfiguration</span></span> | <span data-ttu-id="b29dc-151">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-151">Failure</span></span>    | <span data-ttu-id="b29dc-152">$false</span><span class="sxs-lookup"><span data-stu-id="b29dc-152">$false</span></span>        | <span data-ttu-id="b29dc-153">S</span><span class="sxs-lookup"><span data-stu-id="b29dc-153">S</span></span>                            | <span data-ttu-id="b29dc-154">F<sub>1</sub>, F<sub>2</sub></span><span class="sxs-lookup"><span data-stu-id="b29dc-154">F<sub>1</sub>, F<sub>2</sub></span></span>   |
| <span data-ttu-id="b29dc-155">S, r</span><span class="sxs-lookup"><span data-stu-id="b29dc-155">S, r</span></span>                            | <span data-ttu-id="b29dc-156">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b29dc-156">PendingReboot</span></span>        | <span data-ttu-id="b29dc-157">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="b29dc-157">Success</span></span>    | <span data-ttu-id="b29dc-158">$true</span><span class="sxs-lookup"><span data-stu-id="b29dc-158">$true</span></span>         | <span data-ttu-id="b29dc-159">S</span><span class="sxs-lookup"><span data-stu-id="b29dc-159">S</span></span>                            | <span data-ttu-id="b29dc-160">r</span><span class="sxs-lookup"><span data-stu-id="b29dc-160">r</span></span>                              |
| <span data-ttu-id="b29dc-161">F, r</span><span class="sxs-lookup"><span data-stu-id="b29dc-161">F, r</span></span>                            | <span data-ttu-id="b29dc-162">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b29dc-162">PendingReboot</span></span>        | <span data-ttu-id="b29dc-163">Operazioni non riuscite</span><span class="sxs-lookup"><span data-stu-id="b29dc-163">Failure</span></span>    | <span data-ttu-id="b29dc-164">$true</span><span class="sxs-lookup"><span data-stu-id="b29dc-164">$true</span></span>         | <span data-ttu-id="b29dc-165">$null</span><span class="sxs-lookup"><span data-stu-id="b29dc-165">$null</span></span>                        | <span data-ttu-id="b29dc-166">F, r</span><span class="sxs-lookup"><span data-stu-id="b29dc-166">F, r</span></span>                           |
| <span data-ttu-id="b29dc-167">r, S</span><span class="sxs-lookup"><span data-stu-id="b29dc-167">r, S</span></span>                            | <span data-ttu-id="b29dc-168">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b29dc-168">PendingReboot</span></span>        | <span data-ttu-id="b29dc-169">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="b29dc-169">Success</span></span>    | <span data-ttu-id="b29dc-170">$true</span><span class="sxs-lookup"><span data-stu-id="b29dc-170">$true</span></span>         | <span data-ttu-id="b29dc-171">$null</span><span class="sxs-lookup"><span data-stu-id="b29dc-171">$null</span></span>                        | <span data-ttu-id="b29dc-172">r</span><span class="sxs-lookup"><span data-stu-id="b29dc-172">r</span></span>                              |
| <span data-ttu-id="b29dc-173">r, F</span><span class="sxs-lookup"><span data-stu-id="b29dc-173">r, F</span></span>                            | <span data-ttu-id="b29dc-174">PendingReboot</span><span class="sxs-lookup"><span data-stu-id="b29dc-174">PendingReboot</span></span>        | <span data-ttu-id="b29dc-175">Operazione completata</span><span class="sxs-lookup"><span data-stu-id="b29dc-175">Success</span></span>    | <span data-ttu-id="b29dc-176">$true</span><span class="sxs-lookup"><span data-stu-id="b29dc-176">$true</span></span>         | <span data-ttu-id="b29dc-177">$null</span><span class="sxs-lookup"><span data-stu-id="b29dc-177">$null</span></span>                        | <span data-ttu-id="b29dc-178">r</span><span class="sxs-lookup"><span data-stu-id="b29dc-178">r</span></span>                              |

- <span data-ttu-id="b29dc-179">S<sub>i</sub>: una serie di risorse applicata correttamente</span><span class="sxs-lookup"><span data-stu-id="b29dc-179">S<sub>i</sub>: A series of resources that applied successfully</span></span>
- <span data-ttu-id="b29dc-180">F<sub>i</sub>: una serie di risorse con applicazione non riuscita</span><span class="sxs-lookup"><span data-stu-id="b29dc-180">F<sub>i</sub>: A series of resources that applied unsuccessfully</span></span>
- <span data-ttu-id="b29dc-181">r: una risorsa che richiede il riavvio</span><span class="sxs-lookup"><span data-stu-id="b29dc-181">r: A resource that requires reboot</span></span>

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a><span data-ttu-id="b29dc-182">Miglioramenti per il cmdlet Get-DscConfigurationStatus</span><span class="sxs-lookup"><span data-stu-id="b29dc-182">Enhancement in Get-DscConfigurationStatus cmdlet</span></span>

<span data-ttu-id="b29dc-183">Sono stati apportati alcuni miglioramenti al cmdlet `Get-DscConfigurationStatus` in questa versione.</span><span class="sxs-lookup"><span data-stu-id="b29dc-183">A few enhancements have been made to `Get-DscConfigurationStatus` cmdlet in this release.</span></span> <span data-ttu-id="b29dc-184">In precedenza, la proprietà StartDate degli oggetti restituiti dal cmdlet è di tipo String.</span><span class="sxs-lookup"><span data-stu-id="b29dc-184">Previously, the StartDate property of objects returned by the cmdlet is of String type.</span></span> <span data-ttu-id="b29dc-185">Ora è di tipo Datetime e questo facilita operazioni complesse di selezione e filtro basate sulle proprietà intrinseche di un oggetto Datetime.</span><span class="sxs-lookup"><span data-stu-id="b29dc-185">Now, it is of Datetime type, which enables complex selecting and filtering easier based on the intrinsic properties of a Datetime object.</span></span>

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

<span data-ttu-id="b29dc-186">L'esempio seguente restituisce tutti i record di operazioni DSC eseguite nello stesso giorno della settimana del giorno corrente.</span><span class="sxs-lookup"><span data-stu-id="b29dc-186">The following example returns all DSC operation records that happened on the same day of week as the current day.</span></span>

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

<span data-ttu-id="b29dc-187">Vengono eliminati i record delle operazioni che non apportano modifiche alla configurazione del nodo, ad esempio le operazioni di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="b29dc-187">Records of operations that do not make changes to node’s configuration (i.e. read only operations) are eliminated.</span></span> <span data-ttu-id="b29dc-188">Pertanto `Test-DscConfiguration`, le operazioni `Get-DscConfiguration` non vengono più modificate negli oggetti restituiti dal cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="b29dc-188">Therefore, `Test-DscConfiguration`, `Get-DscConfiguration` operations are no longer adulterated in returned objects from `Get-DscConfigurationStatus` cmdlet.</span></span> <span data-ttu-id="b29dc-189">I record dell'operazione di impostazione della metaconfigurazione vengono aggiunti all'oggetto restituito dal cmdlet `Get-DscConfigurationStatus`.</span><span class="sxs-lookup"><span data-stu-id="b29dc-189">Records of meta configuration setting operation is added to the return of `Get-DscConfigurationStatus` cmdlet.</span></span>

<span data-ttu-id="b29dc-190">Di seguito è riportato un esempio di risultato restituito dal cmdlet `Get-DscConfigurationStatus –All`.</span><span class="sxs-lookup"><span data-stu-id="b29dc-190">Following is an example of result returned from `Get-DscConfigurationStatus –All` cmdlet.</span></span>

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

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a><span data-ttu-id="b29dc-191">Miglioramenti per il cmdlet Get-DscLocalConfigurationManager</span><span class="sxs-lookup"><span data-stu-id="b29dc-191">Enhancement in Get-DscLocalConfigurationManager cmdlet</span></span>

<span data-ttu-id="b29dc-192">Viene aggiunto un nuovo campo di LCMStateDetail all'oggetto restituito dal cmdlet `Get-DscLocalConfigurationManager`.</span><span class="sxs-lookup"><span data-stu-id="b29dc-192">A new field of LCMStateDetail is added to the object returned from `Get-DscLocalConfigurationManager` cmdlet.</span></span> <span data-ttu-id="b29dc-193">Questo campo viene popolato quando LCMState è "Busy".</span><span class="sxs-lookup"><span data-stu-id="b29dc-193">This field is populated when LCMState is "Busy".</span></span> <span data-ttu-id="b29dc-194">Può essere recuperato dal cmdlet seguente:</span><span class="sxs-lookup"><span data-stu-id="b29dc-194">It can be retrieved by following cmdlet:</span></span>

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

<span data-ttu-id="b29dc-195">Quello che segue è un esempio dell'output di un'operazione di monitoraggio continuo per una configurazione che richiede due riavvii in un nodo remoto.</span><span class="sxs-lookup"><span data-stu-id="b29dc-195">Following is an example output of a continuous monitoring on a configuration that requires two reboots on a remote node.</span></span>

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
