---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ottenere oggetti WMI (Get CimInstance)
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "77002651"
---
# <a name="getting-wmi-objects-get-ciminstance"></a>Ottenere oggetti WMI (Get CimInstance)

## <a name="getting-wmi-objects-get-ciminstance"></a>Ottenere oggetti WMI (Get CimInstance)

Strumentazione gestione Windows (WMI) è una tecnologia fondamentale per l'amministrazione del sistema Windows poiché espone un'ampia gamma di informazioni in modo uniforme. Considerando le potenzialità d'uso di WMI, il cmdlet di PowerShell per l'accesso agli oggetti WMI, `Get-CimInstance`, è uno dei più utili per eseguire il lavoro effettivo. Verrà illustrato come usare CimCmdlets per accedere agli oggetti WMI e quindi come usare questi oggetti per eseguire operazioni specifiche.

### <a name="listing-wmi-classes"></a>Elenco delle classi WMI

Il primo problema che la maggior parte degli utenti di WMI si trova ad affrontare è scoprire che cosa si può fare con WMI. Le classi WMI descrivono le risorse che possono essere gestite. Sono disponibili centinaia di classi WMI, alcune delle quali contengono decine di proprietà.

`Get-CimClass` risolve questo problema rendendo individuabile WMI. È possibile ottenere un elenco delle classi WMI disponibili nel computer locale digitando:

```powershell
Get-CimClass -Namespace root/CIMV2 |
  Where-Object CimClassName -like Win32* |
    Select-Object CimClassName
```

```Output
CimClassName
------------
Win32_DeviceChangeEvent
Win32_SystemConfigurationChangeEvent
Win32_VolumeChangeEvent
Win32_SystemTrace
Win32_ProcessTrace
Win32_ProcessStartTrace
Win32_ProcessStopTrace
Win32_ThreadTrace
Win32_ThreadStartTrace
Win32_ThreadStopTrace
...
```

È possibile recuperare le stesse informazioni da un computer remoto usando il parametro **ComputerName**, specificando un nome di computer o un indirizzo IP:

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

L'elenco delle classi restituito dai computer remoti può variare in base allo specifico sistema operativo in esecuzione nel computer e alle particolari estensioni di WMI aggiunte dalle applicazioni installate.

> [!NOTE]
> Quando si usano i cmdlet CIM per connettersi a un computer remoto, WMI deve essere in esecuzione nel computer remoto e l'account in uso deve appartenere al gruppo Administrators locale nel computer remoto.
> Non è necessario che PowerShell sia installato nel sistema remoto. In questo modo è possibile amministrare i sistemi operativi che non eseguono PowerShell, ma in cui è disponibile WMI.

### <a name="displaying-wmi-class-details"></a>Visualizzazione dei dettagli della classe WMI

Se si conosce già il nome di una classe WMI, è possibile usarlo per ottenere immediatamente informazioni. Una delle classi WMI comunemente usate per il recupero di informazioni su un computer è ad esempio **Win32_OperatingSystem**.

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

Anche se vengono mostrati tutti i parametri, il comando può essere espresso in modo più conciso.
Il parametro **ComputerName** non è necessario quando ci si connette al sistema locale. Viene mostrato solo per dimostrare il caso più generale e ricordare l'esistenza del parametro. Il valore predefinito di **Namespace** è `root/CIMV2` e può essere anch'esso omesso. La maggior parte dei cmdlet consente infine di omettere il nome dei parametri comuni. Con `Get-CimInstance`, se non viene specificato alcun nome per il primo parametro, PowerShell lo considera come parametro **Class**. Ciò significa che l'ultimo comando avrebbe potuto essere emesso digitando:

```powershell
Get-CimInstance Win32_OperatingSystem
```

La classe **Win32_OperatingSystem** ha molte più proprietà di quelle mostrate in questo articolo. È possibile usare Get-Member per visualizzare tutte le proprietà. Le proprietà di una classe WMI sono disponibili automaticamente come altre proprietà dell'oggetto:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Get-Member -MemberType Property
```

```Output
   TypeName: Microsoft.Management.Infrastructure.CimInstance#root/cimv2/Win32_OperatingSystem
Name                                      MemberType Definition
----                                      ---------- ----------
BootDevice                                Property   string BootDevice {get;}
BuildNumber                               Property   string BuildNumber {get;}
BuildType                                 Property   string BuildType {get;}
Caption                                   Property   string Caption {get;}
CodeSet                                   Property   string CodeSet {get;}
CountryCode                               Property   string CountryCode {get;}
CreationClassName                         Property   string CreationClassName {get;}
CSCreationClassName                       Property   string CSCreationClassName {get;}
CSDVersion                                Property   string CSDVersion {get;}
CSName                                    Property   string CSName {get;}
CurrentTimeZone                           Property   short CurrentTimeZone {get;}
DataExecutionPrevention_32BitApplications Property   bool DataExecutionPrevention_32BitApplications {get;}
DataExecutionPrevention_Available         Property   bool DataExecutionPrevention_Available {get;}
...
```

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a>Visualizzazione di proprietà non predefinite con i cmdlet Format

Se si necessita di informazioni contenute nella classe **Win32_OperatingSystem** che non sono visualizzate per impostazione predefinita, è possibile visualizzarle usando i cmdlet **Format**. Se ad esempio si vogliono visualizzare i dati disponibili relativi alla memoria, digitare:

```powershell
Get-CimInstance -Class Win32_OperatingSystem |
  Format-Table -Property TotalVirtualMemorySize, TotalVisibleMemorySize,
    FreePhysicalMemory, FreeVirtualMemory, FreeSpaceInPagingFiles
```

```Output
TotalVirtualMemorySize TotalVisibleMemorySize FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------------- ------------------ ----------------- ----------------------
              33449088               16671872            6451868          18424496               16285032
```

> [!NOTE]
> I caratteri jolly possono essere usati con i nomi delle proprietà in `Format-Table`, pertanto l'elemento finale della pipeline può essere ridotto a `Format-Table -Property Total*Memory*, Free*`

I dati relativi alla memoria potrebbero essere più leggibili se si formattano come elenco digitando:

```powershell
Get-CimInstance -Class Win32_OperatingSystem | Format-List Total*Memory*, Free*
```

```Output
TotalVirtualMemorySize : 33449088
TotalVisibleMemorySize : 16671872
FreePhysicalMemory     : 6524456
FreeSpaceInPagingFiles : 16285808
FreeVirtualMemory      : 18393668
Name                   : Microsoft Windows 10 Pro|C:\WINDOWS|\Device\Harddisk0\Partition2
```
