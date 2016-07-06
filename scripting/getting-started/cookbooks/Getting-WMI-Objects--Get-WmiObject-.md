---
title: Recupero di oggetti WMI (Get-WmiObject)
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: 2e6f58860c7aebcf60d8df562f009fce0db3c955

---

# Recupero di oggetti WMI (Get-WmiObject)

## Recupero di oggetti WMI (Get\-WmiObject)
Strumentazione gestione Windows (WMI) è una tecnologia fondamentale per l'amministrazione del sistema Windows poiché espone un'ampia gamma di informazioni in modo uniforme. Considerando le potenzialità d'uso di WMI, il cmdlet di Windows PowerShell per l'accesso agli oggetti WMI, **Get\-WmiObject**, è uno dei più utili per eseguire il lavoro effettivo. Verrà illustrato come usare Get\-WmiObject per accedere agli oggetti WMI e quindi in che modo usare tali oggetti per eseguire operazioni specifiche.

### Elenco delle classi WMI
Il primo problema che la maggior parte degli utenti di WMI si trova ad affrontare è scoprire che cosa si può fare con WMI. Le classi WMI descrivono le risorse che possono essere gestite. Sono disponibili centinaia di classi WMI, alcune delle quali contengono decine di proprietà.

**Get\-WmiObject** affronta questo problema rendendo individuabile WMI. È possibile ottenere un elenco delle classi WMI disponibili nel computer locale digitando:

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

È possibile recuperare le stesse informazioni da un computer remoto usando il parametro ComputerName, specificando un nome di computer o un indirizzo IP:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

L'elenco delle classi restituito dai computer remoti può variare in base allo specifico sistema operativo in esecuzione nel computer e alle particolari estensioni di WMI aggiunte dalle applicazioni installate.

> [!NOTE]
> Quando si usa Get\-WmiObject per connettersi a un computer remoto, all'interno di questo deve essere in esecuzione WMI e, in base alla configurazione predefinita, l'account in uso deve appartenere al gruppo Administrators locale nel computer remoto stesso. Non è necessario che nel sistema remoto sia installato Windows PowerShell. In questo modo è possibile amministrare i sistemi operativi che non eseguono Windows PowerShell, ma che dispongono di WMI.

È anche possibile includere ComputerName quando ci si connette al sistema locale. Come nome computer è possibile usare il nome del computer locale, il relativo indirizzo IP (o l'indirizzo di loopback 127.0.0.1) o il punto ("."), secondo il formato WMI. Se si esegue Windows PowerShell in un computer denominato Admin01 con indirizzo IP 192.168.1.90, i comandi seguenti restituiranno tutti l'elenco delle classi WMI per tale computer:

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Per impostazione predefinita, Get\-WmiObject usa lo spazio dei nomi root\/cimv2. Se si vuole specificare un altro spazio dei nomi WMI, usare il parametro **Namespace** e specificare il percorso dello spazio dei nomi corrispondente:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### Visualizzazione dei dettagli della classe WMI
Se si conosce già il nome di una classe WMI, è possibile usarlo per ottenere immediatamente informazioni. Ad, esempio, una delle classi WMI comunemente usate per il recupero di informazioni su un computer è **Win32\_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Anche se vengono mostrati tutti i parametri, il comando può essere espresso in modo più conciso. Il parametro **ComputerName** non è necessario quando ci si connette al sistema locale. Viene mostrato solo per dimostrare il caso più generale e ricordare l'esistenza del parametro. Il valore predefinito di **Namespace** è root\/cimv2, che può essere omesso anch'esso. La maggior parte dei cmdlet consente infine di omettere il nome dei parametri comuni. Con Get\-WmiObject, se non viene specificato alcun nome per il primo parametro, Windows PowerShell considererà quest'ultimo come parametro **Class**. Ciò significa che l'ultimo comando avrebbe potuto essere emesso digitando:

```
Get-WmiObject Win32_OperatingSystem
```

La classe **Win32\_OperatingSystem** ha molte più proprietà di quelle illustrate in questo articolo. Per visualizzare tutte le proprietà, è possibile usare Get\-Member. Le proprietà di una classe WMI sono disponibili automaticamente come altre proprietà dell'oggetto:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Get-Member -MemberType Property

   TypeName: System.Management.ManagementObject#root\cimv2\Win32_OperatingSyste
m

Name                                      MemberType Definition
----                                      ---------- ----------
__CLASS                                   Property   System.String __CLASS {...
...
BootDevice                                Property   System.String BootDevic...
BuildNumber                               Property   System.String BuildNumb...
...
```

#### Visualizzazione di proprietà non predefinite con i cmdlet Format
Se sono necessarie informazioni contenute nella classe **Win32\_OperatingSystem** ma non visualizzate per impostazione predefinita, è possibile visualizzarle usando i cmdlet **Format**. Se ad esempio si vogliono visualizzare i dati disponibili relativi alla memoria, digitare:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMem FreePhysicalMem FreeVirtualMemo FreeSpaceInPagi
                              ory              ry         ngFiles
--------------- --------------- --------------- --------------- ---------------
        2097024          785904          305808         2056724         1558232
```

> [!NOTE]
> I caratteri jolly possono essere usati con i nomi delle proprietà in **Format\-Table**, pertanto l'elemento finale della pipeline può essere ridotto a **Format\-Table \-Property TotalV\&#42;,Free\&#42;**

I dati relativi alla memoria potrebbero essere più leggibili se si formattano come elenco digitando:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```




<!--HONumber=Jun16_HO4-->


