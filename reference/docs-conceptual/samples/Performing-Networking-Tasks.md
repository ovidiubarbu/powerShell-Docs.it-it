---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Esecuzione di attività di rete
ms.openlocfilehash: e0aa3b8ef3d911ab0fe851f6621d70e1265c5bd4
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737203"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="218cc-103">Esecuzione di attività di rete</span><span class="sxs-lookup"><span data-stu-id="218cc-103">Performing Networking Tasks</span></span>

<span data-ttu-id="218cc-104">Poiché TCP/IP è il protocollo di rete usato più di frequente, è coinvolto nella maggior parte delle attività di basso livello per l'amministrazione dei protocolli di rete.</span><span class="sxs-lookup"><span data-stu-id="218cc-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="218cc-105">In questa sezione si useranno PowerShell e WMI per eseguire queste attività.</span><span class="sxs-lookup"><span data-stu-id="218cc-105">In this section, we use PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="218cc-106">Visualizzazione di un elenco di indirizzi IP per un computer</span><span class="sxs-lookup"><span data-stu-id="218cc-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="218cc-107">Per ottenere tutti gli indirizzi IP in uso nel computer locale, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="218cc-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExpandProperty IPAddress
```

<span data-ttu-id="218cc-108">L'output di questo comando è diverso rispetto alla maggior parte degli elenchi di proprietà, perché i valori sono racchiusi tra parentesi graffe:</span><span class="sxs-lookup"><span data-stu-id="218cc-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```Output
10.0.0.1
fe80::60ea:29a7:a233:7cb7
2601:600:a27f:a470:f532:6451:5630:ec8b
2601:600:a27f:a470:e167:477d:6c5c:342d
2601:600:a27f:a470:b021:7f0d:eab9:6299
2601:600:a27f:a470:a40e:ebce:1a8c:a2f3
2601:600:a27f:a470:613c:12a2:e0e0:bd89
2601:600:a27f:a470:444f:17ec:b463:7edd
2601:600:a27f:a470:10fd:7063:28e9:c9f3
2601:600:a27f:a470:60ea:29a7:a233:7cb7
2601:600:a27f:a470::2ec1
```

<span data-ttu-id="218cc-109">Per capire il motivo della presenza delle parentesi graffe, usare il cmdlet `Get-Member` per esaminare la proprietà **IPAddress**:</span><span class="sxs-lookup"><span data-stu-id="218cc-109">To understand why the braces appear, use the `Get-Member` cmdlet to examine the **IPAddress** property:</span></span>

```powershell
 Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Get-Member -Name IPAddress
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_NetworkAdapterConfiguration
Name      MemberType Definition
----      ---------- ----------
IPAddress Property   string[] IPAddress {get;}
```

<span data-ttu-id="218cc-110">La proprietà IPAddress per ogni scheda di rete è in effetti una matrice.</span><span class="sxs-lookup"><span data-stu-id="218cc-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="218cc-111">Le parentesi graffe nella definizione indicano che **IPAddress** non è un valore **System.String**, bensì una matrice di valori **System.String**.</span><span class="sxs-lookup"><span data-stu-id="218cc-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="218cc-112">Visualizzazione di un elenco di dati di configurazione IP</span><span class="sxs-lookup"><span data-stu-id="218cc-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="218cc-113">Per visualizzare dati di configurazione IP dettagliati per ogni scheda di rete, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="218cc-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true
```

<span data-ttu-id="218cc-114">La visualizzazione predefinita per l'oggetto configurazione della scheda di rete è un set molto ridotto delle informazioni disponibili.</span><span class="sxs-lookup"><span data-stu-id="218cc-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="218cc-115">Per controlli più approfonditi e la risoluzione dei problemi, usare `Select-Object` o un cmdlet di formattazione, ad esempio `Format-List`, per specificare le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="218cc-115">For in-depth inspection and troubleshooting, use `Select-Object` or a formatting cmdlet, such as `Format-List`, to specify the properties to be displayed.</span></span>

<span data-ttu-id="218cc-116">Nelle reti TCP/IP moderne non si sarà probabilmente interessati alle proprietà IPX o WINS.</span><span class="sxs-lookup"><span data-stu-id="218cc-116">In modern TCP/IP networks you are probably not interested in IPX or WINS properties.</span></span> <span data-ttu-id="218cc-117">È possibile usare il parametro **ExcludeProperty** di `Select-Object` per nascondere le proprietà con nomi che iniziano con "WINS" o "IPX".</span><span class="sxs-lookup"><span data-stu-id="218cc-117">You can use the **ExcludeProperty** parameter of `Select-Object` to hide properties with names that begin with "WINS" or "IPX".</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  Select-Object -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="218cc-118">Questo comando restituisce informazioni dettagliate sulle proprietà DHCP, DNS, di routing e su altre proprietà di configurazione IP secondarie.</span><span class="sxs-lookup"><span data-stu-id="218cc-118">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="218cc-119">Ping di computer</span><span class="sxs-lookup"><span data-stu-id="218cc-119">Pinging Computers</span></span>

<span data-ttu-id="218cc-120">È possibile eseguire un semplice ping su un computer usando **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="218cc-120">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="218cc-121">Il comando seguente esegue il ping, ma restituisce un output lungo:</span><span class="sxs-lookup"><span data-stu-id="218cc-121">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'"
```

<span data-ttu-id="218cc-122">Un formato più utile per le informazioni di riepilogo è una visualizzazione delle proprietà Address, ResponseTime e StatusCode, come quella generata dal comando seguente.</span><span class="sxs-lookup"><span data-stu-id="218cc-122">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="218cc-123">Il parametro **Autosize** di `Format-Table` ridimensiona le colonne della tabella in modo da visualizzarle correttamente in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218cc-123">The **Autosize** parameter of `Format-Table` resizes the table columns so that they display properly in PowerShell.</span></span>

```powershell
Get-CimInstance -Class Win32_PingStatus -Filter "Address='127.0.0.1'" |
  Format-Table -Property Address,ResponseTime,StatusCode -Autosize
```

```Output
Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="218cc-124">Il valore 0 per StatusCode indica un ping con esito positivo.</span><span class="sxs-lookup"><span data-stu-id="218cc-124">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="218cc-125">Si può usare una matrice per eseguire il ping di più computer con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="218cc-125">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="218cc-126">Poiché sono presenti più indirizzi, usare `ForEach-Object` per effettuare il ping di ogni indirizzo separatamente:</span><span class="sxs-lookup"><span data-stu-id="218cc-126">Because there is more than one address, use the `ForEach-Object` to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' |
  ForEach-Object -Process {
    Get-CimInstance -Class Win32_PingStatus -Filter ("Address='$_'") |
      Select-Object -Property Address,ResponseTime,StatusCode
  }
```

<span data-ttu-id="218cc-127">Si può usare lo stesso formato del comando per eseguire il ping di tutti i computer di una subnet, ad esempio una rete privata che usa il numero di rete 192.168.1.0 e una subnet mask classe C standard (255.255.255.0). Solo gli indirizzi compresi nell'intervallo da 192.168.1.1 a 192.168.1.254 sono indirizzi locali legittimi (0 è sempre riservato per il numero di rete e 255 è un indirizzo di broadcast subnet).</span><span class="sxs-lookup"><span data-stu-id="218cc-127">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="218cc-128">Per rappresentare una matrice di numeri da 1 a 254 in PowerShell, usare l'istruzione **1..254.**</span><span class="sxs-lookup"><span data-stu-id="218cc-128">To represent an array of the numbers from 1 through 254 in PowerShell, use the statement **1..254.**</span></span>
<span data-ttu-id="218cc-129">Per eseguire un ping dell'intera subnet si può generare la matrice e quindi aggiungere i valori a un indirizzo parziale nell'istruzione di ping:</span><span class="sxs-lookup"><span data-stu-id="218cc-129">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {
  Get-CimInstance -Class Win32_PingStatus -Filter ("Address='192.168.1.$_ '") } |
    Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="218cc-130">Si noti che questa tecnica per la generazione di un intervallo di indirizzi può essere usata anche altrove.</span><span class="sxs-lookup"><span data-stu-id="218cc-130">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="218cc-131">In questo modo si può generare un set completo di indirizzi:</span><span class="sxs-lookup"><span data-stu-id="218cc-131">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="218cc-132">Recupero delle proprietà delle schede di rete</span><span class="sxs-lookup"><span data-stu-id="218cc-132">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="218cc-133">Come accennato in precedenza, è possibile recuperare le proprietà di configurazione generali usando la classe **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="218cc-133">Earlier, we mentioned that you could retrieve general configuration properties using the **Win32_NetworkAdapterConfiguration** class.</span></span> <span data-ttu-id="218cc-134">Anche se non si tratta di informazioni TCP/IP in senso stretto, le informazioni sulle schede di rete, come indirizzi MAC e dati sul tipo di scheda, possono essere utili per capire cosa accade in un computer.</span><span class="sxs-lookup"><span data-stu-id="218cc-134">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="218cc-135">Per ottenere un riepilogo di queste informazioni, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="218cc-135">To get a summary of this information, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="218cc-136">Assegnazione del dominio DNS per una scheda di rete</span><span class="sxs-lookup"><span data-stu-id="218cc-136">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="218cc-137">Per assegnare il dominio DNS per la risoluzione automatica dei nomi, usare il metodo **SetDNSDomain** della classe **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="218cc-137">To assign the DNS domain for automatic name resolution, use the **SetDNSDomain** method of the **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="218cc-138">Poiché il dominio DNS viene assegnato in modo indipendente per la configurazione di ogni scheda di rete, è necessario usare un'istruzione `ForEach-Object` per assegnare il dominio a ogni scheda:</span><span class="sxs-lookup"><span data-stu-id="218cc-138">Because you assign the DNS domain for each network adapter configuration independently, you need to use a `ForEach-Object` statement to assign the domain to each adapter:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process { $_.SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="218cc-139">L'istruzione di filtro `IPEnabled=$true` è necessaria perché anche in una rete che usa solo TCP/IP molte delle configurazioni di scheda di rete presenti in un computer non rappresentano realmente schede TCP/IP, bensì elementi software generici che supportano RAS, PPTP, QoS e altri servizi per tutte le schede e di conseguenza non hanno un indirizzo proprio.</span><span class="sxs-lookup"><span data-stu-id="218cc-139">The filtering statement `IPEnabled=$true` is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="218cc-140">È possibile filtrare il comando usando il cmdlet `Where-Object` anziché il filtro `Get-CimInstance`.</span><span class="sxs-lookup"><span data-stu-id="218cc-140">You can filter the command by using the `Where-Object` cmdlet, instead of using the `Get-CimInstance` filter.</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration |
  Where-Object {$_.IPEnabled} |
    ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="218cc-141">Esecuzione di attività di configurazione DHCP</span><span class="sxs-lookup"><span data-stu-id="218cc-141">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="218cc-142">Per la modifica dei dettagli relativi a DHCP occorre lavorare su un set di schede di rete, esattamente come per la configurazione DNS.</span><span class="sxs-lookup"><span data-stu-id="218cc-142">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="218cc-143">Svariate azioni possono essere eseguite tramite WMI e in questa sezione sono descritte alcune delle più comuni.</span><span class="sxs-lookup"><span data-stu-id="218cc-143">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="218cc-144">Determinazione delle schede abilitate per DHCP</span><span class="sxs-lookup"><span data-stu-id="218cc-144">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="218cc-145">Per trovare le schede abilitate per DHCP in un computer, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="218cc-145">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true"
```

<span data-ttu-id="218cc-146">Per escludere le schede con problemi di configurazione IP, è possibile recuperare solo le schede abilitate per IP:</span><span class="sxs-lookup"><span data-stu-id="218cc-146">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true"
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="218cc-147">Recupero delle proprietà DHCP</span><span class="sxs-lookup"><span data-stu-id="218cc-147">Retrieving DHCP Properties</span></span>

<span data-ttu-id="218cc-148">Poiché le proprietà correlate a DHCP di una scheda di rete in genere iniziano con `DHCP`, è possibile usare il parametro Property di `Format-Table` per visualizzare solo le proprietà di questo tipo:</span><span class="sxs-lookup"><span data-stu-id="218cc-148">Because DHCP-related properties for an adapter generally begin with `DHCP`, you can use the Property parameter of `Format-Table` to display only those properties:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" |
  Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="218cc-149">Abilitazione di DHCP in ogni scheda</span><span class="sxs-lookup"><span data-stu-id="218cc-149">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="218cc-150">Per abilitare il protocollo DHCP in tutte le schede, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="218cc-150">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true |
  ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="218cc-151">È possibile usare l'istruzione **Filter** `IPEnabled=$true and DHCPEnabled=$false` per evitare l'abilitazione del protocollo DHCP nelle schede in cui è già abilitato. L'omissione di questo passaggio, tuttavia, non genera errori.</span><span class="sxs-lookup"><span data-stu-id="218cc-151">You can use the **Filter** statement `IPEnabled=$true and DHCPEnabled=$false` to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="218cc-152">Rilascio e rinnovo di lease DHCP in schede specifiche</span><span class="sxs-lookup"><span data-stu-id="218cc-152">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="218cc-153">La classe **Win32_NetworkAdapterConfiguration** usa i metodi **ReleaseDHCPLease** e **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="218cc-153">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="218cc-154">Entrambi si usano nello stesso modo.</span><span class="sxs-lookup"><span data-stu-id="218cc-154">Both are used in the same way.</span></span> <span data-ttu-id="218cc-155">In generale, usare questi metodi se è necessario rilasciare o rinnovare gli indirizzi per una sola scheda in una subnet specifica.</span><span class="sxs-lookup"><span data-stu-id="218cc-155">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="218cc-156">Il modo più semplice per filtrare le schede in una subnet è scegliere solo le configurazioni delle schede che usano il gateway della subnet in questione.</span><span class="sxs-lookup"><span data-stu-id="218cc-156">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="218cc-157">Ad esempio, il comando seguente rilascia tutti i lease DHCP nelle schede del computer locale che ottengono lease DHCP da 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="218cc-157">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="218cc-158">L'unica modifica necessaria per rinnovare un lease DHCP consiste nell'usare il metodo **RenewDHCPLease** anziché il metodo **ReleaseDHCPLease**:</span><span class="sxs-lookup"><span data-stu-id="218cc-158">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-CimInstance -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" |
  Where-Object {$_.DHCPServer -contains '192.168.1.254'} |
    ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="218cc-159">Quando si usano questi metodi in un computer remoto, tenere presente che, se si è connessi al sistema remoto tramite la scheda con il lease rilasciato o rinnovato, si può perdere l'accesso al sistema.</span><span class="sxs-lookup"><span data-stu-id="218cc-159">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="218cc-160">Rilascio e rinnovo di lease DHCP in tutte le schede</span><span class="sxs-lookup"><span data-stu-id="218cc-160">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="218cc-161">Per eseguire il rilascio o il rinnovo globale degli indirizzi DHCP in tutte le schede, si possono usare i metodi di **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="218cc-161">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span>
<span data-ttu-id="218cc-162">Tuttavia, il comando va applicato alla classe WMI e non a una particolare scheda, perché il rilascio o rinnovo globale dei lease viene eseguito sulla classe, non su una specifica scheda.</span><span class="sxs-lookup"><span data-stu-id="218cc-162">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="218cc-163">Per ottenere un riferimento a una classe WMI, anziché le istanze della classe, è possibile elencare tutte le classi WMI e quindi selezionare solo la classe desiderata in base al nome.</span><span class="sxs-lookup"><span data-stu-id="218cc-163">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="218cc-164">Ad esempio, il comando seguente restituisce la classe **Win32_NetworkAdapterConfiguration**:</span><span class="sxs-lookup"><span data-stu-id="218cc-164">For example, the following command returns the **Win32_NetworkAdapterConfiguration** class:</span></span>

```powershell
Get-CimInstance -List | Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="218cc-165">Si può trattare l'intero comando allo stesso modo della classe e quindi richiamare su di esso il metodo **ReleaseDHCPAdapterLease**.</span><span class="sxs-lookup"><span data-stu-id="218cc-165">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="218cc-166">Nel comando seguente le parentesi che racchiudono gli elementi della pipeline `Get-CimInstance` e `Where-Object` indicano a PowerShell di valutarli per primi:</span><span class="sxs-lookup"><span data-stu-id="218cc-166">In the following command, the parentheses surrounding the `Get-CimInstance` and `Where-Object` pipeline elements direct PowerShell to evaluate them first:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="218cc-167">Si può usare lo stesso formato del comando per richiamare il metodo **RenewDHCPLeaseAll**:</span><span class="sxs-lookup"><span data-stu-id="218cc-167">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="218cc-168">Creazione di una condivisione di rete</span><span class="sxs-lookup"><span data-stu-id="218cc-168">Creating a Network Share</span></span>

<span data-ttu-id="218cc-169">Per creare una condivisione di rete usare il metodo **Create** di **Win32_Share**:</span><span class="sxs-lookup"><span data-stu-id="218cc-169">To create a network share, use the **Create** method of **Win32_Share**:</span></span>

```powershell
(Get-CimInstance -List |
  Where-Object {$_.Name -eq 'Win32_Share'}).Create(
    'C:\temp','TempShare',0,25,'test share of the temp folder'
  )
```

<span data-ttu-id="218cc-170">È anche possibile creare la condivisione usando `net share` in PowerShell in Windows:</span><span class="sxs-lookup"><span data-stu-id="218cc-170">You can also create the share by using `net share` in PowerShell on Windows:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="218cc-171">Rimozione di una condivisione di rete</span><span class="sxs-lookup"><span data-stu-id="218cc-171">Removing a Network Share</span></span>

<span data-ttu-id="218cc-172">Si può rimuovere una condivisione di rete con **Win32_Share**, ma la procedura è leggermente diversa rispetto alla creazione di una condivisione, perché è necessario recuperare la specifica condivisione da rimuovere anziché la classe **Win32_Share**.</span><span class="sxs-lookup"><span data-stu-id="218cc-172">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="218cc-173">L'istruzione seguente elimina la condivisione **TempShare**:</span><span class="sxs-lookup"><span data-stu-id="218cc-173">The following statement deletes the share **TempShare**:</span></span>

```powershell
(Get-CimInstance -Class Win32_Share -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="218cc-174">In Windows è anche possibile usare `net share`:</span><span class="sxs-lookup"><span data-stu-id="218cc-174">In Windows, `net share` works as well:</span></span>

```powershell
net share tempshare /delete
```

```Output
tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="218cc-175">Connessione di un'unità di rete accessibile a Windows</span><span class="sxs-lookup"><span data-stu-id="218cc-175">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="218cc-176">Il cmdlet `New-PSDrive` crea un'unità PowerShell, ma le unità create in questo modo sono disponibili solo per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218cc-176">The `New-PSDrive` cmdlets creates a PowerShell drive, but drives created this way are available only to PowerShell.</span></span> <span data-ttu-id="218cc-177">Per creare una nuova unità di rete, è possibile usare l'oggetto COM **WScript.Network**.</span><span class="sxs-lookup"><span data-stu-id="218cc-177">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="218cc-178">Il comando seguente esegue il mapping della condivisione `\\FPS01\users` all'unità locale `B:`.</span><span class="sxs-lookup"><span data-stu-id="218cc-178">The following command maps the share `\\FPS01\users` to local drive `B:`,</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="218cc-179">In Windows è anche possibile usare il comando `net use`:</span><span class="sxs-lookup"><span data-stu-id="218cc-179">On Windows, the `net use` command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="218cc-180">Le unità di cui viene eseguito il mapping con **WScript.Network** o `net use` sono immediatamente disponibili per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="218cc-180">Drives mapped with either **WScript.Network** or `net use` are immediately available to PowerShell.</span></span>
