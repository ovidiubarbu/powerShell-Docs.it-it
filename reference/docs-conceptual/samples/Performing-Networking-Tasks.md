---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Esecuzione di attività di rete
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 250ae6e5f6431ce659b3600188d7e30e501c3247
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058285"
---
# <a name="performing-networking-tasks"></a><span data-ttu-id="53b66-103">Esecuzione di attività di rete</span><span class="sxs-lookup"><span data-stu-id="53b66-103">Performing Networking Tasks</span></span>

<span data-ttu-id="53b66-104">Poiché TCP/IP è il protocollo di rete usato più di frequente, è coinvolto nella maggior parte delle attività di basso livello per l'amministrazione dei protocolli di rete.</span><span class="sxs-lookup"><span data-stu-id="53b66-104">Because TCP/IP is the most commonly used network protocol, most low-level network protocol administration tasks involve TCP/IP.</span></span> <span data-ttu-id="53b66-105">In questa sezione si useranno Windows PowerShell e WMI per eseguire queste attività.</span><span class="sxs-lookup"><span data-stu-id="53b66-105">In this section, we use Windows PowerShell and WMI to do these tasks.</span></span>

## <a name="listing-ip-addresses-for-a-computer"></a><span data-ttu-id="53b66-106">Visualizzazione di un elenco di indirizzi IP per un computer</span><span class="sxs-lookup"><span data-stu-id="53b66-106">Listing IP Addresses for a Computer</span></span>

<span data-ttu-id="53b66-107">Per ottenere tutti gli indirizzi IP in uso nel computer locale, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="53b66-107">To get all IP addresses in use on the local computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Format-Table -Property IPAddress
```

<span data-ttu-id="53b66-108">L'output di questo comando è diverso rispetto alla maggior parte degli elenchi di proprietà, perché i valori sono racchiusi tra parentesi graffe:</span><span class="sxs-lookup"><span data-stu-id="53b66-108">The output of this command differs from most property lists, because values are enclosed in braces:</span></span>

```output
IPAddress
---------
{192.168.1.80}
{192.168.148.1}
{192.168.171.1}
{0.0.0.0}
```

<span data-ttu-id="53b66-109">Per capire il motivo della presenza delle parentesi graffe, usare il cmdlet Get-Member per esaminare la proprietà **IPAddress**:</span><span class="sxs-lookup"><span data-stu-id="53b66-109">To understand why the braces appear, use the Get-Member cmdlet to examine the **IPAddress** property:</span></span>

```
PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Get-Member -Name IPAddress


TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapterConfiguration

Name      MemberType Definition
----      ---------- ----------
IPAddress Property   System.String[] IPAddress {get;}
```

<span data-ttu-id="53b66-110">La proprietà IPAddress per ogni scheda di rete è in effetti una matrice.</span><span class="sxs-lookup"><span data-stu-id="53b66-110">The IPAddress property for each network adapter is actually an array.</span></span> <span data-ttu-id="53b66-111">Le parentesi graffe nella definizione indicano che **IPAddress** non è un valore **System.String**, bensì una matrice di valori **System.String**.</span><span class="sxs-lookup"><span data-stu-id="53b66-111">The braces in the definition indicate that **IPAddress** is not a **System.String** value, but an array of **System.String** values.</span></span>

## <a name="listing-ip-configuration-data"></a><span data-ttu-id="53b66-112">Visualizzazione di un elenco di dati di configurazione IP</span><span class="sxs-lookup"><span data-stu-id="53b66-112">Listing IP Configuration Data</span></span>

<span data-ttu-id="53b66-113">Per visualizzare dati di configurazione IP dettagliati per ogni scheda di rete, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="53b66-113">To display detailed IP configuration data for each network adapter, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName .
```

<span data-ttu-id="53b66-114">La visualizzazione predefinita per l'oggetto configurazione della scheda di rete è un set molto ridotto delle informazioni disponibili.</span><span class="sxs-lookup"><span data-stu-id="53b66-114">The default display for the network adapter configuration object is a very reduced set of the available information.</span></span> <span data-ttu-id="53b66-115">Per controlli più approfonditi e per la risoluzione dei problemi, usare Select-Object o un cmdlet di formattazione, ad esempio Format-List, per specificare le proprietà da visualizzare.</span><span class="sxs-lookup"><span data-stu-id="53b66-115">For in-depth inspection and troubleshooting, use Select-Object or a formatting cmdlet, such as Format-List, to specify the properties to be displayed.</span></span>

<span data-ttu-id="53b66-116">Se non si è interessati alle proprietà IPX o WINS, come è probabile nel caso di una rete TCP/IP moderna, si può usare il parametro ExcludeProperty di Select-Object per nascondere le proprietà con nomi che iniziano con "WINS" o "IPX":</span><span class="sxs-lookup"><span data-stu-id="53b66-116">If you are not interested in IPX or WINS properties—probably the case in a modern TCP/IP network—you can use the ExcludeProperty parameter of Select-Object to hide properties with names that begin with "WINS" or "IPX:"</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

<span data-ttu-id="53b66-117">Questo comando restituisce informazioni dettagliate sulle proprietà DHCP, DNS, di routing e su altre proprietà di configurazione IP secondarie.</span><span class="sxs-lookup"><span data-stu-id="53b66-117">This command returns detailed information about DHCP, DNS, routing, and other minor IP configuration properties.</span></span>

## <a name="pinging-computers"></a><span data-ttu-id="53b66-118">Ping di computer</span><span class="sxs-lookup"><span data-stu-id="53b66-118">Pinging Computers</span></span>

<span data-ttu-id="53b66-119">È possibile eseguire un semplice ping su un computer usando **Win32_PingStatus**.</span><span class="sxs-lookup"><span data-stu-id="53b66-119">You can perform a simple ping against a computer using by **Win32_PingStatus**.</span></span> <span data-ttu-id="53b66-120">Il comando seguente esegue il ping, ma restituisce un output lungo:</span><span class="sxs-lookup"><span data-stu-id="53b66-120">The following command performs the ping, but returns lengthy output:</span></span>

```powershell
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

<span data-ttu-id="53b66-121">Un formato più utile per le informazioni di riepilogo è una visualizzazione delle proprietà Address, ResponseTime e StatusCode, come quella generata dal comando seguente.</span><span class="sxs-lookup"><span data-stu-id="53b66-121">A more useful form for summary information a display of the Address, ResponseTime, and StatusCode properties, as generated by the following command.</span></span> <span data-ttu-id="53b66-122">Il parametro Autosize di Format-Table ridimensiona le colonne della tabella in modo che vengano visualizzate correttamente in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53b66-122">The Autosize parameter of Format-Table resizes the table columns so that they display properly in Windows PowerShell.</span></span>

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
```

<span data-ttu-id="53b66-123">Il valore 0 per StatusCode indica un ping con esito positivo.</span><span class="sxs-lookup"><span data-stu-id="53b66-123">A StatusCode of 0 indicates a successful ping.</span></span>

<span data-ttu-id="53b66-124">Si può usare una matrice per eseguire il ping di più computer con un unico comando.</span><span class="sxs-lookup"><span data-stu-id="53b66-124">You can use an array to ping multiple computers with a single command.</span></span> <span data-ttu-id="53b66-125">Poiché sono presenti più indirizzi, usare **ForEach-Object** per eseguire separatamente il ping di ogni indirizzo:</span><span class="sxs-lookup"><span data-stu-id="53b66-125">Because there is more than one address, use the **ForEach-Object** to ping each address separately:</span></span>

```powershell
'127.0.0.1','localhost','research.microsoft.com' | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="53b66-126">Si può usare lo stesso formato del comando per eseguire il ping di tutti i computer di una subnet, ad esempio una rete privata che usa il numero di rete 192.168.1.0 e una subnet mask classe C standard (255.255.255.0). Solo gli indirizzi compresi nell'intervallo da 192.168.1.1 a 192.168.1.254 sono indirizzi locali legittimi (0 è sempre riservato per il numero di rete e 255 è un indirizzo di broadcast subnet).</span><span class="sxs-lookup"><span data-stu-id="53b66-126">You can use the same command format to ping all of the computers on a subnet, such as a private network that uses network number 192.168.1.0 and a standard Class C subnet mask (255.255.255.0)., Only addresses in the range of 192.168.1.1 through 192.168.1.254 are legitimate local addresses (0 is always reserved for the network number and 255 is a subnet broadcast address).</span></span>

<span data-ttu-id="53b66-127">Per rappresentare una matrice di numeri da 1 a 254 in Windows PowerShell, usare l'istruzione **1..254.**</span><span class="sxs-lookup"><span data-stu-id="53b66-127">To represent an array of the numbers from 1 through 254 in Windows PowerShell, use the statement **1..254.**</span></span> <span data-ttu-id="53b66-128">Per eseguire un ping dell'intera subnet si può generare la matrice e quindi aggiungere i valori a un indirizzo parziale nell'istruzione di ping:</span><span class="sxs-lookup"><span data-stu-id="53b66-128">A complete subnet ping can be performed by generating the array and then adding the values onto a partial address in the ping statement:</span></span>

```powershell
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

<span data-ttu-id="53b66-129">Si noti che questa tecnica per la generazione di un intervallo di indirizzi può essere usata anche altrove.</span><span class="sxs-lookup"><span data-stu-id="53b66-129">Note that this technique for generating a range of addresses can be used elsewhere as well.</span></span> <span data-ttu-id="53b66-130">In questo modo si può generare un set completo di indirizzi:</span><span class="sxs-lookup"><span data-stu-id="53b66-130">You can generate a complete set of addresses in this way:</span></span>

```powershell
$ips = 1..254 | ForEach-Object -Process {'192.168.1.' + $_}
```

## <a name="retrieving-network-adapter-properties"></a><span data-ttu-id="53b66-131">Recupero delle proprietà delle schede di rete</span><span class="sxs-lookup"><span data-stu-id="53b66-131">Retrieving Network Adapter Properties</span></span>

<span data-ttu-id="53b66-132">Come accennato in precedenza in questo manuale dell'utente, è possibile recuperare le proprietà di configurazione generali usando **Win32_NetworkAdapterConfiguration**.</span><span class="sxs-lookup"><span data-stu-id="53b66-132">Earlier in this user's guide, we mentioned that you could retrieve general configuration properties by using **Win32_NetworkAdapterConfiguration**.</span></span> <span data-ttu-id="53b66-133">Anche se non si tratta di informazioni TCP/IP in senso stretto, le informazioni sulle schede di rete, come indirizzi MAC e dati sul tipo di scheda, possono essere utili per capire cosa accade in un computer.</span><span class="sxs-lookup"><span data-stu-id="53b66-133">Although not strictly TCP/IP information, network adapter information such as MAC addresses and adapter types can be useful for understanding what is going on with a computer.</span></span> <span data-ttu-id="53b66-134">Per ottenere un riepilogo di queste informazioni, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="53b66-134">To get a summary of this information, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

## <a name="assigning-the-dns-domain-for-a-network-adapter"></a><span data-ttu-id="53b66-135">Assegnazione del dominio DNS per una scheda di rete</span><span class="sxs-lookup"><span data-stu-id="53b66-135">Assigning the DNS Domain for a Network Adapter</span></span>

<span data-ttu-id="53b66-136">Per assegnare il dominio DNS per la risoluzione automatica dei nomi, usare il metodo **Win32_NetworkAdapterConfiguration SetDNSDomain**.</span><span class="sxs-lookup"><span data-stu-id="53b66-136">To assign the DNS domain for automatic name resolution, use the **Win32_NetworkAdapterConfiguration SetDNSDomain** method.</span></span> <span data-ttu-id="53b66-137">Poiché il dominio DNS viene assegnato in modo indipendente per la configurazione di ogni scheda di rete, è necessario usare un'istruzione **ForEach-Object** per assegnare il dominio a ogni scheda:</span><span class="sxs-lookup"><span data-stu-id="53b66-137">Because you assign the DNS domain for each network adapter configuration independently, you need to use a **ForEach-Object** statement to assign the domain to each adapter:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain('fabrikam.com') }
```

<span data-ttu-id="53b66-138">L'istruzione di filtro "IPEnabled=$true" è necessaria, perché anche in una rete che usa solo TCP/IP, numerose configurazioni delle schede di rete presenti in un computer non rappresentano realmente schede TCP/IP, bensì elementi software generici che supportano RAS, PPTP, QoS e altri servizi per tutte le schede, di conseguenza non hanno un indirizzo proprio.</span><span class="sxs-lookup"><span data-stu-id="53b66-138">The filtering statement "IPEnabled=$true" is necessary, because even on a network that uses only TCP/IP, several of the network adapter configurations on a computer are not true TCP/IP adapters; they are general software elements supporting RAS, PPTP, QoS, and other services for all adapters and thus do not have an address of their own.</span></span>

<span data-ttu-id="53b66-139">Si può filtrare il comando usando il cmdlet **Where-Object** anziché il filtro **Get-WmiObject**.</span><span class="sxs-lookup"><span data-stu-id="53b66-139">You can filter the command by using the **Where-Object** cmdlet, instead of using the **Get-WmiObject** filter.</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain('fabrikam.com')}
```

## <a name="performing-dhcp-configuration-tasks"></a><span data-ttu-id="53b66-140">Esecuzione di attività di configurazione DHCP</span><span class="sxs-lookup"><span data-stu-id="53b66-140">Performing DHCP Configuration Tasks</span></span>

<span data-ttu-id="53b66-141">Per la modifica dei dettagli relativi a DHCP occorre lavorare su un set di schede di rete, esattamente come per la configurazione DNS.</span><span class="sxs-lookup"><span data-stu-id="53b66-141">Modifying DHCP details involves working with a set of network adapters, just as the DNS configuration does.</span></span> <span data-ttu-id="53b66-142">Svariate azioni possono essere eseguite tramite WMI e in questa sezione sono descritte alcune delle più comuni.</span><span class="sxs-lookup"><span data-stu-id="53b66-142">There are several distinct actions you can perform by using WMI, and we will step through a few of the common ones.</span></span>

### <a name="determining-dhcp-enabled-adapters"></a><span data-ttu-id="53b66-143">Determinazione delle schede abilitate per DHCP</span><span class="sxs-lookup"><span data-stu-id="53b66-143">Determining DHCP-Enabled Adapters</span></span>

<span data-ttu-id="53b66-144">Per trovare le schede abilitate per DHCP in un computer, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="53b66-144">To find the DHCP-enabled adapters on a computer, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName .
```

<span data-ttu-id="53b66-145">Per escludere le schede con problemi di configurazione IP, è possibile recuperare solo le schede abilitate per IP:</span><span class="sxs-lookup"><span data-stu-id="53b66-145">To exclude adapters with IP configuration problems, you can retrieve only IP-enabled adapters:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName .
```

### <a name="retrieving-dhcp-properties"></a><span data-ttu-id="53b66-146">Recupero delle proprietà DHCP</span><span class="sxs-lookup"><span data-stu-id="53b66-146">Retrieving DHCP Properties</span></span>

<span data-ttu-id="53b66-147">Poiché le proprietà correlate a DHCP di una scheda di rete in genere iniziano con "DHCP", si può usare il parametro Property di Format-Table per visualizzare solo le proprietà di questo tipo:</span><span class="sxs-lookup"><span data-stu-id="53b66-147">Because DHCP-related properties for an adapter generally begin with "DHCP," you can use the Property parameter of Format-Table to display only those properties:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=$true" -ComputerName . | Format-Table -Property DHCP*
```

### <a name="enabling-dhcp-on-each-adapter"></a><span data-ttu-id="53b66-148">Abilitazione di DHCP in ogni scheda</span><span class="sxs-lookup"><span data-stu-id="53b66-148">Enabling DHCP on Each Adapter</span></span>

<span data-ttu-id="53b66-149">Per abilitare il protocollo DHCP in tutte le schede, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="53b66-149">To enable DHCP on all adapters, use the following command:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=$true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

<span data-ttu-id="53b66-150">Si può usare l'istruzione **Filter** "IPEnabled=$true and DHCPEnabled=$false" per evitare l'abilitazione di DHCP nelle schede in cui è già abilitato, ma l'omissione di questo passaggio non genera errori.</span><span class="sxs-lookup"><span data-stu-id="53b66-150">You can use the **Filter** statement "IPEnabled=$true and DHCPEnabled=$false" to avoid enabling DHCP where it is already enabled, but omitting this step will not cause errors.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a><span data-ttu-id="53b66-151">Rilascio e rinnovo di lease DHCP in schede specifiche</span><span class="sxs-lookup"><span data-stu-id="53b66-151">Releasing and Renewing DHCP Leases on Specific Adapters</span></span>

<span data-ttu-id="53b66-152">La classe **Win32_NetworkAdapterConfiguration** usa i metodi **ReleaseDHCPLease** e **RenewDHCPLease**.</span><span class="sxs-lookup"><span data-stu-id="53b66-152">The **Win32_NetworkAdapterConfiguration** class has **ReleaseDHCPLease** and **RenewDHCPLease** methods.</span></span> <span data-ttu-id="53b66-153">Entrambi si usano nello stesso modo.</span><span class="sxs-lookup"><span data-stu-id="53b66-153">Both are used in the same way.</span></span> <span data-ttu-id="53b66-154">In generale, usare questi metodi se è necessario rilasciare o rinnovare gli indirizzi per una sola scheda in una subnet specifica.</span><span class="sxs-lookup"><span data-stu-id="53b66-154">In general, use these methods if you only need to release or renew addresses for an adapter on a specific subnet.</span></span> <span data-ttu-id="53b66-155">Il modo più semplice per filtrare le schede in una subnet è scegliere solo le configurazioni delle schede che usano il gateway della subnet in questione.</span><span class="sxs-lookup"><span data-stu-id="53b66-155">The easiest way to filter adapters on a subnet is to choose only the adapter configurations that use the gateway for that subnet.</span></span> <span data-ttu-id="53b66-156">Ad esempio, il comando seguente rilascia tutti i lease DHCP nelle schede del computer locale che ottengono lease DHCP da 192.168.1.254:</span><span class="sxs-lookup"><span data-stu-id="53b66-156">For example, the following command releases all DHCP leases on adapters on the local computer that are obtaining DHCP leases from 192.168.1.254:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

<span data-ttu-id="53b66-157">L'unica modifica necessaria per rinnovare un lease DHCP consiste nell'usare il metodo **RenewDHCPLease** anziché il metodo **ReleaseDHCPLease**:</span><span class="sxs-lookup"><span data-stu-id="53b66-157">The only change for renewing a DHCP lease is to use the **RenewDHCPLease** method instead of the **ReleaseDHCPLease** method:</span></span>

```powershell
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=$true and DHCPEnabled=$true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains '192.168.1.254'} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> <span data-ttu-id="53b66-158">Quando si usano questi metodi in un computer remoto, tenere presente che, se si è connessi al sistema remoto tramite la scheda con il lease rilasciato o rinnovato, si può perdere l'accesso al sistema.</span><span class="sxs-lookup"><span data-stu-id="53b66-158">When using these methods on a remote computer, be aware that you can lose access to the remote system if you are connected to it through the adapter with the released or renewed lease.</span></span>

### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a><span data-ttu-id="53b66-159">Rilascio e rinnovo di lease DHCP in tutte le schede</span><span class="sxs-lookup"><span data-stu-id="53b66-159">Releasing and Renewing DHCP Leases on All Adapters</span></span>

<span data-ttu-id="53b66-160">Per eseguire il rilascio o il rinnovo globale degli indirizzi DHCP in tutte le schede, si possono usare i metodi di **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll**.</span><span class="sxs-lookup"><span data-stu-id="53b66-160">You can perform global DHCP address releases or renewals on all adapters by using the **Win32_NetworkAdapterConfiguration** methods, **ReleaseDHCPLeaseAll** and **RenewDHCPLeaseAll**.</span></span> <span data-ttu-id="53b66-161">Tuttavia, il comando va applicato alla classe WMI e non a una particolare scheda, perché il rilascio o rinnovo globale dei lease viene eseguito sulla classe, non su una specifica scheda.</span><span class="sxs-lookup"><span data-stu-id="53b66-161">However, the command must apply to the WMI class, rather than a particular adapter, because releasing and renewing leases globally is performed on the class, not on a specific adapter.</span></span>

<span data-ttu-id="53b66-162">Per ottenere un riferimento a una classe WMI, anziché le istanze della classe, è possibile elencare tutte le classi WMI e quindi selezionare solo la classe desiderata in base al nome.</span><span class="sxs-lookup"><span data-stu-id="53b66-162">You can get a reference to a WMI class, instead of class instances, by listing all WMI classes and then selecting only the desired class by name.</span></span> <span data-ttu-id="53b66-163">Ad esempio, il comando seguente restituisce la classe Win32_NetworkAdapterConfiguration:</span><span class="sxs-lookup"><span data-stu-id="53b66-163">For example, the following command returns the Win32_NetworkAdapterConfiguration class:</span></span>

```powershell
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'}
```

<span data-ttu-id="53b66-164">Si può trattare l'intero comando allo stesso modo della classe e quindi richiamare su di esso il metodo **ReleaseDHCPAdapterLease**.</span><span class="sxs-lookup"><span data-stu-id="53b66-164">You can treat the entire command as the class and then invoke the **ReleaseDHCPAdapterLease** method on it.</span></span> <span data-ttu-id="53b66-165">Nel comando seguente, le parentesi che racchiudono gli elementi della pipeline **Get-WmiObject** e **Where-Object** indicano a Windows PowerShell di valutarli per primi:</span><span class="sxs-lookup"><span data-stu-id="53b66-165">In the following command, the parentheses surrounding the **Get-WmiObject** and **Where-Object** pipeline elements direct Windows PowerShell to evaluate them first:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).ReleaseDHCPLeaseAll()
```

<span data-ttu-id="53b66-166">Si può usare lo stesso formato del comando per richiamare il metodo **RenewDHCPLeaseAll**:</span><span class="sxs-lookup"><span data-stu-id="53b66-166">You can use the same command format to invoke the **RenewDHCPLeaseAll** method:</span></span>

```powershell
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq 'Win32_NetworkAdapterConfiguration'} ).RenewDHCPLeaseAll()
```

## <a name="creating-a-network-share"></a><span data-ttu-id="53b66-167">Creazione di una condivisione di rete</span><span class="sxs-lookup"><span data-stu-id="53b66-167">Creating a Network Share</span></span>

<span data-ttu-id="53b66-168">Per creare una condivisione di rete, usare il metodo **Win32_Share Create**:</span><span class="sxs-lookup"><span data-stu-id="53b66-168">To create a network share, use the **Win32_Share Create** method:</span></span>

```powershell
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq 'Win32_Share'}).Create('C:\temp','TempShare',0,25,'test share of the temp folder')
```

<span data-ttu-id="53b66-169">Si può creare la condivisione di rete anche usando **net share** in Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="53b66-169">You can also create the share by using **net share** in Windows PowerShell:</span></span>

```powershell
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

## <a name="removing-a-network-share"></a><span data-ttu-id="53b66-170">Rimozione di una condivisione di rete</span><span class="sxs-lookup"><span data-stu-id="53b66-170">Removing a Network Share</span></span>

<span data-ttu-id="53b66-171">Si può rimuovere una condivisione di rete con **Win32_Share**, ma la procedura è leggermente diversa rispetto alla creazione di una condivisione, perché è necessario recuperare la specifica condivisione da rimuovere anziché la classe **Win32_Share**.</span><span class="sxs-lookup"><span data-stu-id="53b66-171">You can remove a network share with **Win32_Share**, but the process is slightly different from creating a share, because you need to retrieve the specific share to be removed, rather than the **Win32_Share** class.</span></span> <span data-ttu-id="53b66-172">L'istruzione seguente elimina la condivisione "TempShare":</span><span class="sxs-lookup"><span data-stu-id="53b66-172">The following statement deletes the share "TempShare":</span></span>

```powershell
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

<span data-ttu-id="53b66-173">Si può anche usare **net share**:</span><span class="sxs-lookup"><span data-stu-id="53b66-173">**Net share** works as well:</span></span>

```
PS> net share tempshare /delete

tempshare was deleted successfully.
```

## <a name="connecting-a-windows-accessible-network-drive"></a><span data-ttu-id="53b66-174">Connessione di un'unità di rete accessibile a Windows</span><span class="sxs-lookup"><span data-stu-id="53b66-174">Connecting a Windows Accessible Network Drive</span></span>

<span data-ttu-id="53b66-175">I cmdlet **New-PSDrive** creano un'unità Windows PowerShell, ma le unità create in questo modo sono disponibili solo per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53b66-175">The **New-PSDrive** cmdlets creates a Windows PowerShell drive, but drives created this way are available only to Windows PowerShell.</span></span> <span data-ttu-id="53b66-176">Per creare una nuova unità di rete, è possibile usare l'oggetto COM **WScript.Network**.</span><span class="sxs-lookup"><span data-stu-id="53b66-176">To create a new networked drive, you can use the **WScript.Network** COM object.</span></span> <span data-ttu-id="53b66-177">Il comando seguente esegue il mapping della condivisione \\\\FPS01\\users all'unità locale B:</span><span class="sxs-lookup"><span data-stu-id="53b66-177">The following command maps the share \\\\FPS01\\users to local drive B:</span></span>

```powershell
(New-Object -ComObject WScript.Network).MapNetworkDrive('B:', '\\FPS01\users')
```

<span data-ttu-id="53b66-178">Si può anche usare il comando **net use**:</span><span class="sxs-lookup"><span data-stu-id="53b66-178">The **net use** command works as well:</span></span>

```powershell
net use B: \\FPS01\users
```

<span data-ttu-id="53b66-179">Le unità di cui viene eseguito il mapping con **WScript.Network** o net use sono immediatamente disponibili per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="53b66-179">Drives mapped with either **WScript.Network** or net use are immediately available to Windows PowerShell.</span></span>