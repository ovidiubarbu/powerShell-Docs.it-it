---
title: Raccolta di informazioni sui computer
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: d45fbf8a7ddaf7c1176dc09386f96b4f0c0da8f6

---

# Raccolta di informazioni sui computer
**Get\-WmiObject** è il cmdlet più importante per le attività generali di gestione del sistema. Tutte le impostazioni del sottosistema cruciali sono esposte tramite WMI. WMI gestisce inoltre i dati come oggetti inclusi in raccolte di uno o più elementi. Dato che anche Windows PowerShell funziona con oggetti e usa una pipeline che consente di gestire uno o più oggetti nello stesso modo, l'accesso WMI generico consente di eseguire alcune attività avanzate con un impegno minimo.

Gli esempi seguenti dimostrano come raccogliere informazioni specifiche tramite **Get\-WmiObject** per un computer arbitrario. Viene specificato il parametro **ComputerName** con il valore punto (**.**), che rappresenta il computer locale. È possibile specificare un nome o indirizzo IP associato a qualsiasi computer raggiungibile tramite WMI. Per recuperare informazioni sul computer locale, è possibile omettere **\-ComputerName.**

### Elenco delle impostazioni dei desktop
Inizieremo con un comando che raccoglie informazioni sui desktop nel computer locale.

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

Questo comando restituisce informazioni per tutti i desktop, indipendentemente dal fatto che siano in uso o meno.

> [!NOTE]
> Le informazioni restituite da alcune classi WMI possono essere molto dettagliate e spesso includono i metadati sulla classe WMI. Dato che la maggior parte delle proprietà di questi metadati ha nomi che iniziano con un carattere di sottolineatura doppio, è possibile filtrare le proprietà con Select\-Object. È possibile specificare solo le proprietà che iniziano con caratteri alfabetici usando **\[a\-z]\&#42;** come valore di Property. Ad esempio:

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

Per escludere i metadati, usare un operatore pipeline (|) per inviare i risultati del comando Get\-WmiObject a **Select\-Object \-Property \[a\-z]\&#42;**.

### Elenco delle informazioni sul BIOS
La classe Win32\_BIOS restituisce informazioni piuttosto compatte e complete sul BIOS di sistema nel computer locale:

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### Elenco delle informazioni sul processore
È possibile recuperare informazioni generali sul processore tramite la classe WMI **Win32\_Processor**, anche se probabilmente è preferibile filtrare le informazioni:

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

Per ottenere una stringa di descrizione generica della famiglia di processori, è possibile restituire semplicemente la proprietà **Win32\_ComputerSystemSystemType**:

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### Elenco di produttore e modello del computer
Le informazioni sul modello di computer sono disponibili anche in **Win32\_ComputerSystem**. Non sarà necessario filtrare l'output visualizzato standard per fornire dati OEM:

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

La validità dell'output di comandi come questo, che restituiscono informazioni direttamente dai componenti hardware, dipende esclusivamente dai dati disponibili. Alcune informazioni non sono configurate correttamente dai produttori dell'hardware e pertanto potrebbero non essere disponibili.

### Elenco degli hotfix installati
È possibile ottenere un elenco di tutti gli hotfix installati tramite **Win32\_QuickFixEngineering**:

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

Questa classe restituisce un elenco di hotfix simile al seguente:

```
Description         : Update for Windows XP (KB910437)
FixComments         : Update
HotFixID            : KB910437
Install Date        :
InstalledBy         : Administrator
InstalledOn         : 12/16/2005
Name                :
ServicePackInEffect : SP3
Status              :
```

Per ottenere un output più conciso, è possibile escludere alcune proprietà. Anche se è possibile usare il parametro **Get\-WmiObject Property** per scegliere solo **HotFixID**, in questo modo si otterranno in realtà più informazioni, perché per impostazione predefinita vengono visualizzati tutti i metadati:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixId
HotFixID         : KB910437
__GENUS          : 2
__CLASS          : Win32_QuickFixEngineering
__SUPERCLASS     :
__DYNASTY        :
__RELPATH        :
__PROPERTY_COUNT : 1
__DERIVATION     : {}
__SERVER         :
__NAMESPACE      :
__PATH           :
```

Vengono restituiti dati aggiuntivi perché il parametro Property in **Get\-WmiObject** limita le proprietà restituite da istanze della classe WMI, non l'oggetto restituito a Windows PowerShell. Per ridurre l'output, usare **Select\-Object**:

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### Elenco di informazioni sulla versione del sistema operativo
Le proprietà della classe **Win32\_OperatingSystem** includono informazioni sulla versione e sui Service Pack. È possibile selezionare esplicitamente solo queste proprietà per ottenere un riepilogo delle informazioni sulla versione da **Win32\_OperatingSystem**:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

Con il parametro **Select\-Object Property** è anche possibile usare caratteri jolly. Dato che in questo caso è importante usare tutte le proprietà che iniziano con **Build** o **ServicePack**, è possibile abbreviare il comando in questo modo:

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### Elenco di utenti locali e proprietario
È possibile trovare informazioni generali e locali sugli utenti (numero di utenti con licenza, numero corrente di utenti e nome del proprietario) con una selezione delle proprietà di **Win32\_OperatingSystem**. È possibile selezionare in modo esplicito le proprietà da visualizzare come segue:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

Questa è una versione più concisa con caratteri jolly:

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### Recupero dello spazio su disco disponibile
Per visualizzare lo spazio su disco e lo spazio disponibile per le unità locali, è possibile usare la classe WMI Win32\_LogicalDisk. È necessario visualizzare solo le istanze con DriveType 3, ovvero il valore usato da WMI per i dischi rigidi fissi.

```
Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName .

DeviceID     : C:
DriveType    : 3
ProviderName :
FreeSpace    : 65541357568
Size         : 203912880128
VolumeName   : Local Disk

DeviceID     : Q:
DriveType    : 3
ProviderName :
FreeSpace    : 44298250240
Size         : 122934034432
VolumeName   : New Volume

PS> Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### Recupero di informazioni sulle sessioni di accesso
È possibile ottenere informazioni generali sulle sessioni di accesso associate agli utenti tramite la classe WMI Win32\_LogonSession:

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### Recupero dell'utente connesso a un computer
È possibile visualizzare l'utente connesso a un computer specifico con Win32\_ComputerSystem. Questo comando restituisce solo l'utente connesso al desktop di sistema:

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### Recupero dell'ora locale da un computer
È possibile recuperare l'ora locale corrente in un computer specifico con la classe WMI Win32\_LocalTime. Per impostazione predefinita questa classe visualizza tutti i metadati. È quindi necessario filtrare questi ultimi tramite **Select\-Object**:

```
PS> Get-WmiObject -Class Win32_LocalTime -ComputerName . | Select-Object -Property [a-z]*

Day          : 15
DayOfWeek    : 4
Hour         : 12
Milliseconds :
Minute       : 11
Month        : 6
Quarter      : 2
Second       : 52
WeekInMonth  : 3
Year         : 2006
```

### Visualizzazione dello stato dei servizi
Per visualizzare lo stato di tutti i servizi in un computer specifico, è possibile usare in locale il cmdlet **Get\-Service** come indicato in precedenza. Per i sistemi remoti, è possibile usare la classe WMI Win32\_Service. Se si usa **Select\-Object** anche per filtrare i risultati per **Status**, **Name** e **DisplayName**, il formato dell'output sarà quasi identico a quello ottenuto da **Get\-Service**:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

Per consentire la visualizzazione completa dei nomi nei casi occasionali di servizi con nomi estremamente lunghi e ottimizzare la larghezza della colonna consentendo il ritorno a capo dei nomi lunghi anziché il troncamento, è possibile usare **Format\-Table** con i parametri **AutoSize** e **Wrap**:

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```




<!--HONumber=Jun16_HO4-->


