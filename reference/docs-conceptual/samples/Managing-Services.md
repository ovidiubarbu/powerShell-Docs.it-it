---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione di servizi
ms.openlocfilehash: 7a238a3fea857c5dac1c12ca0d0371a49e6bf58c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870524"
---
# <a name="managing-services"></a><span data-ttu-id="d80c1-103">Gestione di servizi</span><span class="sxs-lookup"><span data-stu-id="d80c1-103">Managing Services</span></span>

<span data-ttu-id="d80c1-104">Sono disponibili otto cmdlet Service principali, progettati per una vasta gamma di attività dei servizi.</span><span class="sxs-lookup"><span data-stu-id="d80c1-104">There are eight core Service cmdlets, designed for a wide range of service tasks .</span></span> <span data-ttu-id="d80c1-105">Verranno esaminati solo l'elenco e la modifica dello stato di esecuzione dei servizi, ma è possibile ottenere un elenco di cmdlet Service usando `Get-Help \*-Service`, oltre a trovare informazioni sui diversi cmdlet Service con `Get-Help <Cmdlet-Name>`, ad esempio `Get-Help New-Service`.</span><span class="sxs-lookup"><span data-stu-id="d80c1-105">We will look only at listing and changing running state for services, but you can get a list of Service cmdlets by using `Get-Help \*-Service`, and you can find information about each Service cmdlet by using `Get-Help <Cmdlet-Name>`, such as `Get-Help New-Service`.</span></span>

## <a name="getting-services"></a><span data-ttu-id="d80c1-106">Ottenere servizi</span><span class="sxs-lookup"><span data-stu-id="d80c1-106">Getting Services</span></span>

<span data-ttu-id="d80c1-107">È possibile ottenere i servizi in un computer locale o remoto usando il cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="d80c1-107">You can get the services on a local or remote computer by using the `Get-Service` cmdlet.</span></span> <span data-ttu-id="d80c1-108">Come con `Get-Process`, l'uso del comando `Get-Service` senza parametri restituisce tutti i servizi.</span><span class="sxs-lookup"><span data-stu-id="d80c1-108">As with `Get-Process`, using the `Get-Service` command without parameters returns all services.</span></span> <span data-ttu-id="d80c1-109">È possibile filtrare per nome, usando anche un asterisco come carattere jolly:</span><span class="sxs-lookup"><span data-stu-id="d80c1-109">You can filter by name, even using an asterisk as a wildcard:</span></span>

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="d80c1-110">Poiché non è sempre ovvio quale sia il nome effettivo di un servizio, potrebbe essere necessario individuare i servizi in base al nome visualizzato.</span><span class="sxs-lookup"><span data-stu-id="d80c1-110">Because it is not always obvious what the real name for the service is, you may find you need to find services by display name.</span></span> <span data-ttu-id="d80c1-111">È possibile farlo usando il nome specifico, caratteri jolly o un elenco di nomi visualizzati:</span><span class="sxs-lookup"><span data-stu-id="d80c1-111">You can do this by specific name, using wildcards, or using a list of display names:</span></span>

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

<span data-ttu-id="d80c1-112">Il parametro ComputerName del cmdlet Get-Service può essere usato per ottenere servizi in computer remoti.</span><span class="sxs-lookup"><span data-stu-id="d80c1-112">You can use the ComputerName parameter of the Get-Service cmdlet to get the services on remote computers.</span></span> <span data-ttu-id="d80c1-113">Il parametro ComputerName accetta più valori e i caratteri jolly, pertanto è possibile recuperare i servizi di più computer con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="d80c1-113">The ComputerName parameter accepts multiple values and wildcard characters, so you can get the services on multiple computers with a single command.</span></span> <span data-ttu-id="d80c1-114">Il comando seguente ottiene ad esempio i servizi nel computer remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="d80c1-114">For example, the following command gets the services on the Server01 remote computer.</span></span>

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a><span data-ttu-id="d80c1-115">Ottenere i servizi richiesti e dipendenti</span><span class="sxs-lookup"><span data-stu-id="d80c1-115">Getting Required and Dependent Services</span></span>

<span data-ttu-id="d80c1-116">Il cmdlet Get-Service include due parametri molto utili per l'amministrazione dei servizi.</span><span class="sxs-lookup"><span data-stu-id="d80c1-116">The Get-Service cmdlet has two parameters that are very useful in service administration.</span></span> <span data-ttu-id="d80c1-117">Il parametro DependentServices ottiene i servizi che dipendono dal servizio.</span><span class="sxs-lookup"><span data-stu-id="d80c1-117">The DependentServices parameter gets services that depend on the service.</span></span> <span data-ttu-id="d80c1-118">Il parametro RequiredServices ottiene i servizi da cui dipende questo servizio.</span><span class="sxs-lookup"><span data-stu-id="d80c1-118">The RequiredServices parameter gets services upon which this service depends.</span></span>

<span data-ttu-id="d80c1-119">Questi parametri visualizzano solo i valori delle proprietà DependentServices e ServicesDependedOn (alias=RequiredServices) dell'oggetto System.ServiceProcess.ServiceController restituito da Get-Service, ma semplificano i comandi e rendono più semplice ottenere queste informazioni.</span><span class="sxs-lookup"><span data-stu-id="d80c1-119">These parameters just display the values of the DependentServices and ServicesDependedOn (alias=RequiredServices) properties of the System.ServiceProcess.ServiceController object that Get-Service returns, but they simplify commands and make getting this information much simpler.</span></span>

<span data-ttu-id="d80c1-120">Il comando seguente ottiene i servizi richiesti dal servizio LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="d80c1-120">The following command gets the services that the LanmanWorkstation service requires.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

<span data-ttu-id="d80c1-121">Il comando seguente ottiene i servizi che richiedono il servizio LanmanWorkstation.</span><span class="sxs-lookup"><span data-stu-id="d80c1-121">The following command gets the services that require the LanmanWorkstation service.</span></span>

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

<span data-ttu-id="d80c1-122">È anche possibile ottenere tutti i servizi che hanno dipendenze.</span><span class="sxs-lookup"><span data-stu-id="d80c1-122">You can even get all services that have dependencies.</span></span> <span data-ttu-id="d80c1-123">Il comando seguente ha proprio questo scopo e usa il cmdlet Format-Table per visualizzare le proprietà Status, Name, RequiredServices e DependentServices dei servizi nel computer.</span><span class="sxs-lookup"><span data-stu-id="d80c1-123">The following command does just that, and then it uses the Format-Table cmdlet to display the Status, Name, RequiredServices and DependentServices properties of the services on the computer.</span></span>

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a><span data-ttu-id="d80c1-124">Arresto, avvio, sospensione e riavvio di servizi</span><span class="sxs-lookup"><span data-stu-id="d80c1-124">Stopping, Starting, Suspending, and Restarting Services</span></span>

<span data-ttu-id="d80c1-125">I cmdlet Service hanno tutti lo stesso formato generale.</span><span class="sxs-lookup"><span data-stu-id="d80c1-125">The Service cmdlets all have the same general form.</span></span> <span data-ttu-id="d80c1-126">I servizi possono essere specificati in base al nome comune o al nome visualizzato e accettano elenchi e caratteri jolly come valori.</span><span class="sxs-lookup"><span data-stu-id="d80c1-126">Services can be specified by common name or display name, and take lists and wildcards as values.</span></span> <span data-ttu-id="d80c1-127">Per arrestare lo spooler di stampa, usare:</span><span class="sxs-lookup"><span data-stu-id="d80c1-127">To stop the print spooler, use:</span></span>

```powershell
Stop-Service -Name spooler
```

<span data-ttu-id="d80c1-128">Per avviare lo spooler di stampa dopo che è stato arrestato, usare:</span><span class="sxs-lookup"><span data-stu-id="d80c1-128">To start the print spooler after it is stopped, use:</span></span>

```powershell
Start-Service -Name spooler
```

<span data-ttu-id="d80c1-129">Per sospendere lo spooler di stampa, usare:</span><span class="sxs-lookup"><span data-stu-id="d80c1-129">To suspend the print spooler, use:</span></span>

```powershell
Suspend-Service -Name spooler
```

<span data-ttu-id="d80c1-130">Il cmdlet `Restart-Service` funziona esattamente come gli altri cmdlet Service, ma di seguito sono disponibili alcuni esempi più complessi.</span><span class="sxs-lookup"><span data-stu-id="d80c1-130">The `Restart-Service` cmdlet works in the same manner as the other Service cmdlets, but we will show some more complex examples for it.</span></span> <span data-ttu-id="d80c1-131">Il suo uso più semplice prevede che venga specificato il nome del servizio:</span><span class="sxs-lookup"><span data-stu-id="d80c1-131">In the simplest use, you specify the name of the service:</span></span>

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

<span data-ttu-id="d80c1-132">Si noterà che viene visualizzato un messaggio di avviso ripetuto sull'avvio dello spooler di stampa.</span><span class="sxs-lookup"><span data-stu-id="d80c1-132">You will notice that you get a repeated warning message about the Print Spooler starting up.</span></span> <span data-ttu-id="d80c1-133">Quando si esegue un'operazione di servizio che richiede un certo tempo, Windows PowerShell notificherà all'utente che sta ancora tentando di eseguire l'attività.</span><span class="sxs-lookup"><span data-stu-id="d80c1-133">When you perform a service operation that takes some time, Windows PowerShell will notify you that it is still attempting to perform the task.</span></span>

<span data-ttu-id="d80c1-134">Per riavviare più servizi, è possibile ottenere un elenco di servizi, filtrarli e quindi eseguire il riavvio:</span><span class="sxs-lookup"><span data-stu-id="d80c1-134">If you want to restart multiple services, you can get a list of services, filter them, and then perform the restart:</span></span>

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

<span data-ttu-id="d80c1-135">Questi cmdlet Service non hanno un parametro ComputerName, ma è possibile eseguirli in un computer remoto usando il cmdlet Invoke-Command.</span><span class="sxs-lookup"><span data-stu-id="d80c1-135">These Service cmdlets do not have a ComputerName parameter, but you can run them on a remote computer by using the Invoke-Command cmdlet.</span></span> <span data-ttu-id="d80c1-136">Il comando seguente riavvia ad esempio il servizio Spooler nel computer remoto Server01.</span><span class="sxs-lookup"><span data-stu-id="d80c1-136">For example, the following command restarts the Spooler service on the Server01 remote computer.</span></span>

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a><span data-ttu-id="d80c1-137">Impostazione delle proprietà dei servizi</span><span class="sxs-lookup"><span data-stu-id="d80c1-137">Setting Service Properties</span></span>

<span data-ttu-id="d80c1-138">Il cmdlet `Set-Service` consente di modificare le proprietà di un servizio in un computer locale o remoto.</span><span class="sxs-lookup"><span data-stu-id="d80c1-138">The `Set-Service` cmdlet changes the properties of a service on a local or remote computer.</span></span> <span data-ttu-id="d80c1-139">Poiché lo stato del servizio è una proprietà, è possibile usare questo cmdlet per avviare, arrestare e sospendere un servizio.</span><span class="sxs-lookup"><span data-stu-id="d80c1-139">Because the service status is a property, you can use this cmdlet to start, stop, and suspend a service.</span></span>
<span data-ttu-id="d80c1-140">Il cmdlet Set-Service ha anche un parametro StartupType che consente di modificare il tipo di avvio del servizio.</span><span class="sxs-lookup"><span data-stu-id="d80c1-140">The Set-Service cmdlet also has a StartupType parameter that lets you change the service startup type.</span></span>

<span data-ttu-id="d80c1-141">Per usare `Set-Service` in Windows Vista e versioni successive di Windows, aprire Windows PowerShell con l'opzione "Esegui come amministratore".</span><span class="sxs-lookup"><span data-stu-id="d80c1-141">To use `Set-Service` on Windows Vista and later versions of Windows, open Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="d80c1-142">Per altre informazioni, vedere [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span><span class="sxs-lookup"><span data-stu-id="d80c1-142">For more information, see [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)</span></span>

## <a name="see-also"></a><span data-ttu-id="d80c1-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="d80c1-143">See Also</span></span>

- [<span data-ttu-id="d80c1-144">Get-Service</span><span class="sxs-lookup"><span data-stu-id="d80c1-144">Get-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [<span data-ttu-id="d80c1-145">Set-Service</span><span class="sxs-lookup"><span data-stu-id="d80c1-145">Set-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [<span data-ttu-id="d80c1-146">Restart-Service</span><span class="sxs-lookup"><span data-stu-id="d80c1-146">Restart-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [<span data-ttu-id="d80c1-147">Suspend-Service</span><span class="sxs-lookup"><span data-stu-id="d80c1-147">Suspend-Service</span></span>](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
