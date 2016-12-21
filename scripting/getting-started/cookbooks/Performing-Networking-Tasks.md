---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: "Esecuzione di attività di rete"
ms.technology: powershell
ms.assetid: a43cc55f-70c1-45c8-9467-eaad0d57e3b5
ms.openlocfilehash: 1c938500da191c2791b3178971cdcea28f57aacd
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="performing-networking-tasks"></a>Esecuzione di attività di rete
Poiché TCP/IP è il protocollo di rete usato più di frequente, è coinvolto nella maggior parte delle attività di basso livello per l'amministrazione dei protocolli di rete. In questa sezione si useranno Windows PowerShell e WMI per eseguire queste attività.

### <a name="listing-ip-addresses-for-a-computer"></a>Visualizzazione di un elenco di indirizzi IP per un computer
Per ottenere tutti gli indirizzi IP in uso nel computer locale, usare il comando seguente:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Format-Table -Property IPAddress
```

L'output di questo comando è diverso rispetto alla maggior parte degli elenchi di proprietà, perché i valori sono racchiusi tra parentesi graffe:

<a name="preipaddress"></a><pre>IPAddress
---------
{192.168.1.80} {192.168.148.1} {192.168.171.1} {0.0.0.0}</pre>

Per capire il motivo della presenza delle parentesi graffe, usare il cmdlet Get-Member per esaminare la proprietà **IPAddress**:

<pre>PS> Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName. | Get-Member -Name IPAddress TypeName: System.Management.ManagementObject#root\cimv2\Win32_NetworkAdapter Configuration Name      MemberType Definition ----      ---------- ---------- IPAddress Property   System.String[] IPAddress {get;}</pre>

La proprietà IPAddress per ogni scheda di rete è in effetti una matrice. Le parentesi graffe nella definizione indicano che **IPAddress** non è un valore **System.String**, bensì una matrice di valori **System.String**.

### <a name="listing-ip-configuration-data"></a>Visualizzazione di un elenco di dati di configurazione IP
Per visualizzare dati di configurazione IP dettagliati per ogni scheda di rete, usare il comando seguente:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName .
```

La visualizzazione predefinita per l'oggetto configurazione della scheda di rete è un set molto ridotto delle informazioni disponibili. Per controlli più approfonditi e per la risoluzione dei problemi, usare Select-Object o un cmdlet di formattazione, ad esempio Format-List, per specificare le proprietà da visualizzare.

Se non si è interessati alle proprietà IPX o WINS, come è probabile nel caso di una rete TCP/IP moderna, si può usare il parametro ExcludeProperty di Select-Object per nascondere le proprietà con nomi che iniziano con "WINS" o "IPX":

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=TRUE -ComputerName . | Select-Object -Property [a-z]* -ExcludeProperty IPX*,WINS*
```

Questo comando restituisce informazioni dettagliate sulle proprietà DHCP, DNS, di routing e su altre proprietà di configurazione IP secondarie.

### <a name="pinging-computers"></a>Ping di computer
È possibile eseguire un semplice ping su un computer usando **Win32_PingStatus**. Il comando seguente esegue il ping, ma restituisce un output lungo:

```
Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName .
```

Un formato più utile per le informazioni di riepilogo è una visualizzazione delle proprietà Address, ResponseTime e StatusCode, come quella generata dal comando seguente. Il parametro Autosize di Format-Table ridimensiona le colonne della tabella in modo che vengano visualizzate correttamente in Windows PowerShell.

```
PS> Get-WmiObject -Class Win32_PingStatus -Filter "Address='127.0.0.1'" -ComputerName . | Format-Table -Property Address,ResponseTime,StatusCode -Autosize

Address   ResponseTime StatusCode
-------   ------------ ----------
127.0.0.1            0          0
A status code of 0 indicates a successful ping.
```

Si può usare una matrice per eseguire il ping di più computer con un unico comando. Poiché sono presenti più indirizzi, usare **ForEach-Object** per eseguire separatamente il ping di ogni indirizzo:

```
"127.0.0.1","localhost","research.microsoft.com" | ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='" + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Si può usare lo stesso formato del comando per eseguire il ping di tutti i computer di una subnet, ad esempio una rete privata che usa il numero di rete 192.168.1.0 e una subnet mask classe C standard (255.255.255.0). Solo gli indirizzi compresi nell'intervallo da 192.168.1.1 a 192.168.1.254 sono indirizzi locali legittimi (0 è sempre riservato per il numero di rete e 255 è un indirizzo di broadcast subnet).

Per rappresentare una matrice di numeri da 1 a 254 in Windows PowerShell, usare l'istruzione **1..254.** Per eseguire un ping dell'intera subnet si può generare la matrice e quindi aggiungere i valori a un indirizzo parziale nell'istruzione di ping:

```
1..254| ForEach-Object -Process {Get-WmiObject -Class Win32_PingStatus -Filter ("Address='192.168.1." + $_ + "'") -ComputerName .} | Select-Object -Property Address,ResponseTime,StatusCode
```

Si noti che questa tecnica per la generazione di un intervallo di indirizzi può essere usata anche altrove. In questo modo si può generare un set completo di indirizzi:

`$ips = 1..254 | ForEach-Object -Process {"192.168.1." + $_}`

### <a name="retrieving-network-adapter-properties"></a>Recupero delle proprietà delle schede di rete
Come accennato in precedenza in questo manuale dell'utente, è possibile recuperare le proprietà di configurazione generali usando **Win32_NetworkAdapterConfiguration**. Anche se non si tratta di informazioni TCP/IP in senso stretto, le informazioni sulle schede di rete, come indirizzi MAC e dati sul tipo di scheda, possono essere utili per capire cosa accade in un computer. Per ottenere un riepilogo di queste informazioni, usare il comando seguente:

```
Get-WmiObject -Class Win32_NetworkAdapter -ComputerName .
```

### <a name="assigning-the-dns-domain-for-a-network-adapter"></a>Assegnazione del dominio DNS per una scheda di rete
Per assegnare il dominio DNS per la risoluzione automatica dei nomi, usare il metodo **Win32_NetworkAdapterConfiguration SetDNSDomain**. Poiché il dominio DNS viene assegnato in modo indipendente per la configurazione di ogni scheda di rete, è necessario usare un'istruzione **ForEach-Object** per assegnare il dominio a ogni scheda:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process { $_. SetDNSDomain("fabrikam.com") }
```

L'istruzione di filtro "IPEnabled=true" è necessaria, perché anche in una rete che usa solo TCP/IP, numerose configurazioni delle schede di rete presenti in un computer non rappresentano realmente schede TCP/IP, bensì elementi software generici che supportano RAS, PPTP, QoS e altri servizi per tutte le schede, di conseguenza non hanno un indirizzo proprio.

Si può filtrare il comando usando il cmdlet **Where-Object** anziché il filtro **Get-WmiObject**.

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -ComputerName . | Where-Object -FilterScript {$_.IPEnabled} | ForEach-Object -Process {$_.SetDNSDomain("fabrikam.com")}
```

### <a name="performing-dhcp-configuration-tasks"></a>Esecuzione di attività di configurazione DHCP
Per la modifica dei dettagli relativi a DHCP occorre lavorare su un set di schede di rete, esattamente come per la configurazione DNS. Svariate azioni possono essere eseguite tramite WMI e in questa sezione sono descritte alcune delle più comuni.

#### <a name="determining-dhcp-enabled-adapters"></a>Determinazione delle schede abilitate per DHCP
Per trovare le schede abilitate per DHCP in un computer, usare il comando seguente:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName .
```

Per escludere le schede con problemi di configurazione IP, è possibile recuperare solo le schede abilitate per IP:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName .
```

#### <a name="retrieving-dhcp-properties"></a>Recupero delle proprietà DHCP
Poiché le proprietà correlate a DHCP di una scheda di rete in genere iniziano con "DHCP", si può usare il parametro Property di Format-Table per visualizzare solo le proprietà di questo tipo:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "DHCPEnabled=true" -ComputerName . | Format-Table -Property DHCP*
```

#### <a name="enabling-dhcp-on-each-adapter"></a>Abilitazione di DHCP in ogni scheda
Per abilitare il protocollo DHCP in tutte le schede, usare il comando seguente:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter IPEnabled=true -ComputerName . | ForEach-Object -Process {$_.EnableDHCP()}
```

Si può usare l'istruzione **Filter** "IPEnabled=true and DHCPEnabled=false" per evitare l'abilitazione di DHCP nelle schede in cui è già abilitato, ma l'omissione di questo passaggio non genera errori.

#### <a name="releasing-and-renewing-dhcp-leases-on-specific-adapters"></a>Rilascio e rinnovo di lease DHCP in schede specifiche
La classe **Win32_NetworkAdapterConfiguration** usa i metodi **ReleaseDHCPLease** e **RenewDHCPLease**. Entrambi si usano nello stesso modo. In generale, usare questi metodi se è necessario rilasciare o rinnovare gli indirizzi per una sola scheda in una subnet specifica. Il modo più semplice per filtrare le schede in una subnet è scegliere solo le configurazioni delle schede che usano il gateway della subnet in questione. Ad esempio, il comando seguente rilascia tutti i lease DHCP nelle schede del computer locale che ottengono lease DHCP da 192.168.1.254:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

L'unica modifica necessaria per rinnovare un lease DHCP consiste nell'usare il metodo **RenewDHCPLease** anziché il metodo **ReleaseDHCPLease**:

```
Get-WmiObject -Class Win32_NetworkAdapterConfiguration -Filter "IPEnabled=true and DHCPEnabled=true" -ComputerName . | Where-Object -FilterScript {$_.DHCPServer -contains "192.168.1.254"} | ForEach-Object -Process {$_.ReleaseDHCPLease()}
```

> [!NOTE]
> Quando si usano questi metodi in un computer remoto, tenere presente che, se si è connessi al sistema remoto tramite la scheda con il lease rilasciato o rinnovato, si può perdere l'accesso al sistema.

#### <a name="releasing-and-renewing-dhcp-leases-on-all-adapters"></a>Rilascio e rinnovo di lease DHCP in tutte le schede
Per eseguire il rilascio o il rinnovo globale degli indirizzi DHCP in tutte le schede, si possono usare i metodi di **Win32_NetworkAdapterConfiguration**, **ReleaseDHCPLeaseAll** e **RenewDHCPLeaseAll**. Tuttavia, il comando va applicato alla classe WMI e non a una particolare scheda, perché il rilascio o rinnovo globale dei lease viene eseguito sulla classe, non su una specifica scheda.

Per ottenere un riferimento a una classe WMI, anziché le istanze della classe, è possibile elencare tutte le classi WMI e quindi selezionare solo la classe desiderata in base al nome. Ad esempio, il comando seguente restituisce la classe Win32_NetworkAdapterConfiguration:

```
Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"}
```

Si può trattare l'intero comando allo stesso modo della classe e quindi richiamare su di esso il metodo **ReleaseDHCPAdapterLease**. Nel comando seguente, le parentesi che racchiudono gli elementi della pipeline **Get-WmiObject** e **Where-Object** indicano a Windows PowerShell di valutarli per primi:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).ReleaseDHCPLeaseAll()
```

Si può usare lo stesso formato del comando per richiamare il metodo **RenewDHCPLeaseAll**:

```
( Get-WmiObject -List | Where-Object -FilterScript {$_.Name -eq "Win32_NetworkAdapterConfiguration"} ).RenewDHCPLeaseAll()
```

### <a name="creating-a-network-share"></a>Creazione di una condivisione di rete
Per creare una condivisione di rete, usare il metodo **Win32_Share Create**:

```
(Get-WmiObject -List -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Win32_Share"}).Create("C:\temp","TempShare",0,25,"test share of the temp folder")
```

Si può creare la condivisione di rete anche usando **net share** in Windows PowerShell:

```
net share tempshare=c:\temp /users:25 /remark:"test share of the temp folder"
```

### <a name="removing-a-network-share"></a>Rimozione di una condivisione di rete
Si può rimuovere una condivisione di rete con **Win32_Share**, ma la procedura è leggermente diversa rispetto alla creazione di una condivisione, perché è necessario recuperare la specifica condivisione da rimuovere anziché la classe **Win32_Share**. L'istruzione seguente elimina la condivisione "TempShare":

```
(Get-WmiObject -Class Win32_Share -ComputerName . -Filter "Name='TempShare'").Delete()
```

Si può anche usare **net share**:

```
PS> net share tempshare /delete
tempshare was deleted successfully.
```

### <a name="connecting-a-windows-accessible-network-drive"></a>Connessione di un'unità di rete accessibile a Windows
I cmdlet **New-PSDrive** creano un'unità Windows PowerShell, ma le unità create in questo modo sono disponibili solo per Windows PowerShell. Per creare una nuova unità di rete, è possibile usare l'oggetto COM **WScript.Network**. Il comando seguente esegue il mapping della condivisione \\\\FPS01\\users all'unità locale B:

```
(New-Object -ComObject WScript.Network).MapNetworkDrive("B:", "\\FPS01\users")
```

Si può anche usare il comando **net use**:

```
net use B: \\FPS01\users
```

Le unità di cui viene eseguito il mapping con **WScript.Network** o net use sono immediatamente disponibili per Windows PowerShell.

