---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Raccolta di informazioni sui computer
ms.openlocfilehash: 9407ff15b3c3ca6b3adab60d4d01d957c599e79e
ms.sourcegitcommit: 058a6e86eac1b27ca57a11687019df98709ed709
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/08/2020
ms.locfileid: "75737237"
---
# <a name="collecting-information-about-computers"></a>Raccolta di informazioni sui computer

I cmdlet nel modulo **CimCmdlets** sono i più importanti per le attività di gestione generali del sistema. Tutte le impostazioni del sottosistema cruciali sono esposte tramite WMI. WMI gestisce inoltre i dati come oggetti inclusi in raccolte di uno o più elementi. Dato che anche Windows PowerShell funziona con oggetti e usa una pipeline che consente di gestire uno o più oggetti nello stesso modo, l'accesso WMI generico consente di eseguire alcune attività avanzate con un impegno minimo.

## <a name="listing-desktop-settings"></a>Elenco delle impostazioni dei desktop

Inizieremo con un comando che raccoglie informazioni sui desktop nel computer locale.

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

Questo comando restituisce informazioni per tutti i desktop, indipendentemente dal fatto che siano in uso o meno.

> [!NOTE]
> Le informazioni restituite da alcune classi WMI possono essere molto dettagliate e spesso includono i metadati sulla classe WMI.

Dato che la maggior parte delle proprietà di questi metadati ha nomi che iniziano con **Cim**, è possibile filtrare le proprietà usando `Select-Object`. Specificare il parametro **- ExcludeProperty** usando "Cim *" come valore. Ad esempio:

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

Per escludere i metadati, usare un operatore pipeline (|) per inviare i risultati del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.

## <a name="listing-bios-information"></a>Elenco delle informazioni sul BIOS

La classe WMI **Win32_BIOS** restituisce informazioni piuttosto compatte e complete sul BIOS di sistema nel computer locale:

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a>Elenco delle informazioni sul processore

È possibile recuperare informazioni generali sul processore tramite la classe WMI **Win32_Processor**, anche se è probabile che si preferisca filtrare le informazioni:

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

Per ottenere una stringa di descrizione generica della famiglia di processori, è possibile restituire semplicemente la proprietà **SystemType**:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a>Elenco di produttore e modello del computer

Le informazioni sul modello di computer sono disponibili anche da **Win32_ComputerSystem**. Non sarà necessario filtrare l'output visualizzato standard per fornire dati OEM:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

La validità dell'output di comandi come questo, che restituiscono informazioni direttamente dai componenti hardware, dipende esclusivamente dai dati disponibili. Alcune informazioni non sono configurate correttamente dai produttori dell'hardware e pertanto potrebbero non essere disponibili.

## <a name="listing-installed-hotfixes"></a>Elenco degli hotfix installati

È possibile ottenere un elenco di tutti gli hotfix installati tramite **Win32_QuickFixEngineering**:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

Questa classe restituisce un elenco di hotfix simile al seguente:

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

Per ottenere un output più conciso, è possibile escludere alcune proprietà. Anche se è possibile usare il parametro **Property** di `Get-CimInstance` per scegliere solo **HotFixID**, in questo modo si otterranno in realtà più informazioni, perché per impostazione predefinita vengono visualizzati tutti i metadati:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixID
```

```Output
InstalledOn           :
Caption               :
Description           :
InstallDate           :
Name                  :
Status                :
CSName                :
FixComments           :
HotFixID              : KB4533002
InstalledBy           :
ServicePackInEffect   :
PSComputerName        :
CimClass              : root/cimv2:Win32_QuickFixEngineering
CimInstanceProperties : {Caption, Description, InstallDate, Name…}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
...
```

Vengono restituiti dati aggiuntivi perché il parametro **Property** in `Get-CimInstance` limita le proprietà restituite dalle istanze della classe WMI, non l'oggetto restituito a PowerShell. Per ridurre l'output, usare `Select-Object`:

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a>Elenco di informazioni sulla versione del sistema operativo

Le proprietà della classe **Win32_OperatingSystem** includono informazioni sulla versione e sui Service Pack. È possibile selezionare esplicitamente queste proprietà per ottenere un riepilogo delle informazioni sulla versione da **Win32_OperatingSystem**:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

È anche possibile usare caratteri jolly con il parametro **Property** di `Select-Object`. Dato che in questo caso è importante usare tutte le proprietà che iniziano con **Build** o **ServicePack**, è possibile abbreviare il comando in questo modo:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property Build*,OSType,ServicePack*
```

```Output
BuildNumber             : 18362
BuildType               : Multiprocessor Free
OSType                  : 18
ServicePackMajorVersion : 0
ServicePackMinorVersion : 0
```

## <a name="listing-local-users-and-owner"></a>Elenco di utenti locali e proprietario

Selezionando le proprietà della classe **Win32_OperatingSystem** è possibile trovare informazioni locali generali sugli utenti, ad esempio il numero di utenti con licenza, il numero corrente di utenti e il nome del proprietario. È possibile selezionare in modo esplicito le proprietà da visualizzare come segue:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Questa è una versione più concisa con caratteri jolly:

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a>Recupero dello spazio su disco disponibile

Per visualizzare lo spazio su disco e lo spazio disponibile per le unità locali, è possibile usare la classe WMI Win32_LogicalDisk.
È necessario visualizzare solo le istanze con DriveType 3, ovvero il valore usato dalla classe WMI per i dischi rigidi fissi.

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3"
```

```Output
DeviceID DriveType ProviderName VolumeName Size         FreeSpace   PSComputerName
-------- --------- ------------ ---------- ----         ---------   --------------
C:       3                      Local Disk 203912880128 65541357568 .
Q:       3                      New Volume 122934034432 44298250240 .
```

```powershell
Get-CimInstance -ClassName Win32_LogicalDisk -Filter "DriveType=3" |
  Measure-Object -Property FreeSpace,Size -Sum |
    Select-Object -Property Property,Sum
```

```Output
Property           Sum
--------           ---
FreeSpace 109839607808
Size      326846914560
```

## <a name="getting-logon-session-information"></a>Recupero di informazioni sulle sessioni di accesso

È possibile ottenere informazioni generali sulle sessioni di accesso associate agli utenti tramite la classe WMI **Win32_LogonSession**:

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a>Recupero dell'utente connesso a un computer

È possibile visualizzare l'utente connesso a un computer specifico con Win32_ComputerSystem. Questo comando restituisce solo l'utente connesso al desktop di sistema:

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a>Recupero dell'ora locale da un computer

È possibile recuperare l'ora locale corrente in un computer specifico con la classe WMI **Win32_LocalTime**.

```powershell
Get-CimInstance -ClassName Win32_LocalTime
```

```Output
Day            : 23
DayOfWeek      : 1
Hour           : 8
Milliseconds   :
Minute         : 52
Month          : 12
Quarter        : 4
Second         : 55
WeekInMonth    : 4
Year           : 2019
PSComputerName :
```

## <a name="displaying-service-status"></a>Visualizzazione dello stato dei servizi

Per visualizzare lo stato di tutti i servizi in un computer specifico, è possibile usare in locale il cmdlet `Get-Service`. Per i sistemi remoti, è possibile usare la classe WMI **Win32_Service**. Se si usa `Select-Object` anche per filtrare i risultati per **Status**, **Name** e **DisplayName**, il formato dell'output sarà quasi identico a quello ottenuto da `Get-Service`:

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

Per consentire la visualizzazione completa dei nomi nei casi occasionali di servizi con nomi estremamente lunghi e ottimizzare la larghezza della colonna consentendo il ritorno a capo dei nomi lunghi anziché il troncamento, è possibile usare `Format-Table` con i parametri **AutoSize** e **Wrap**:

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
