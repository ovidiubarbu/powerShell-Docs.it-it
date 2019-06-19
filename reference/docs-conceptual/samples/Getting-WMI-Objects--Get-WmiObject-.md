---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Recupero di oggetti WMI Get WmiObject
ms.openlocfilehash: 93276ce12135342af2d6f238976e65e5d8bdde7a
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030222"
---
# <a name="getting-wmi-objects-get-wmiobject"></a>Recupero di oggetti WMI (Get-WmiObject)

## <a name="getting-wmi-objects-get-wmiobject"></a>Recupero di oggetti WMI (Get-WmiObject)

Strumentazione gestione Windows (WMI) è una tecnologia fondamentale per l'amministrazione del sistema Windows poiché espone un'ampia gamma di informazioni in modo uniforme. Considerando le potenzialità d'uso di WMI, il cmdlet di Windows PowerShell per l'accesso agli oggetti WMI, **Get-WmiObject**, è uno dei più utili per eseguire il lavoro effettivo. Verrà illustrato come usare Get-WmiObject per accedere agli oggetti WMI e quindi in che modo usare tali oggetti per eseguire operazioni specifiche.

### <a name="listing-wmi-classes"></a>Elenco delle classi WMI

Il primo problema che la maggior parte degli utenti di WMI si trova ad affrontare è scoprire che cosa si può fare con WMI. Le classi WMI descrivono le risorse che possono essere gestite. Sono disponibili centinaia di classi WMI, alcune delle quali contengono decine di proprietà.

**Get-WmiObject** affronta questo problema rendendo individuabile Strumentazione gestione Windows (WMI). È possibile ottenere un elenco delle classi WMI disponibili nel computer locale digitando:

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
> Quando si usa Get-WmiObject per connettersi a un computer remoto, nel computer remoto deve essere in esecuzione WMI e, in base alla configurazione predefinita, l'account in uso deve appartenere al gruppo Administrators locale nel computer remoto. Non è necessario che nel sistema remoto sia installato Windows PowerShell. In questo modo è possibile amministrare i sistemi operativi che non eseguono Windows PowerShell, ma che dispongono di WMI.

È anche possibile includere ComputerName quando ci si connette al sistema locale. È possibile usare il nome del computer locale, il relativo indirizzo IP (o l'indirizzo di loopback 127.0.0.1) o il punto ("."), a indicare il nome del computer in formato WMI. Se si esegue Windows PowerShell in un computer denominato Admin01 con indirizzo IP 192.168.1.90, i comandi seguenti restituiranno tutti l'elenco delle classi WMI per tale computer:

```powershell
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

Per impostazione predefinita, Get-WmiObject usa lo spazio dei nomi root/cimv2. Se si vuole specificare un altro spazio dei nomi WMI, usare il parametro **Namespace** e specificare il percorso dello spazio dei nomi corrispondente:

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a>Visualizzazione dei dettagli della classe WMI

Se si conosce già il nome di una classe WMI, è possibile usarlo per ottenere immediatamente informazioni. Una delle classi WMI comunemente usate per il recupero di informazioni su un computer è ad esempio **Win32_OperatingSystem**.

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

Anche se vengono mostrati tutti i parametri, il comando può essere espresso in modo più conciso. Il parametro **ComputerName** non è necessario quando ci si connette al sistema locale. Viene mostrato solo per dimostrare il caso più generale e ricordare l'esistenza del parametro. Il valore predefinito di **Namespace** è root/cimv2 e anche questo parametro può essere omesso. La maggior parte dei cmdlet consente infine di omettere il nome dei parametri comuni. Con Get-WmiObject, se non viene specificato alcun nome per il primo parametro, Windows PowerShell lo considererà come parametro **Class**. Ciò significa che l'ultimo comando avrebbe potuto essere emesso digitando:

```powershell
Get-WmiObject Win32_OperatingSystem
```

La classe **Win32_OperatingSystem** ha molte più proprietà di quelle mostrate in questo articolo. È possibile usare Get-Member per visualizzare tutte le proprietà. Le proprietà di una classe WMI sono disponibili automaticamente come altre proprietà dell'oggetto:

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visualizzazione di proprietà non predefinite con i cmdlet Format

Se si necessita di informazioni contenute nella classe **Win32_OperatingSystem** che non sono visualizzate per impostazione predefinita, è possibile visualizzarle usando i cmdlet **Format**. Se ad esempio si vogliono visualizzare i dati disponibili relativi alla memoria, digitare:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> I caratteri jolly possono essere usati con i nomi delle proprietà in **Format-Table**, pertanto l'elemento finale della pipeline può essere ridotto a `Format-Table -Property Total,Free`

I dati relativi alla memoria potrebbero essere più leggibili se si formattano come elenco digitando:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```
