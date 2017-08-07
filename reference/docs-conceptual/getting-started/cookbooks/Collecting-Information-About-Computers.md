---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Raccolta di informazioni sui computer
ms.assetid: 9e7b6a2d-34f7-4731-a92c-8b3382eb51bb
ms.openlocfilehash: c0b7ec9ed7d2b07c66d2b1cf3342f971d71da481
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="collecting-information-about-computers"></a><span data-ttu-id="63f39-103">Raccolta di informazioni sui computer</span><span class="sxs-lookup"><span data-stu-id="63f39-103">Collecting Information About Computers</span></span>
<span data-ttu-id="63f39-104">**Get-WmiObject** è il cmdlet più importante per le attività generali di gestione del sistema.</span><span class="sxs-lookup"><span data-stu-id="63f39-104">**Get-WmiObject** is the most important cmdlet for general system management tasks.</span></span> <span data-ttu-id="63f39-105">Tutte le impostazioni del sottosistema cruciali sono esposte tramite WMI.</span><span class="sxs-lookup"><span data-stu-id="63f39-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="63f39-106">WMI gestisce inoltre i dati come oggetti inclusi in raccolte di uno o più elementi.</span><span class="sxs-lookup"><span data-stu-id="63f39-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="63f39-107">Dato che anche Windows PowerShell funziona con oggetti e usa una pipeline che consente di gestire uno o più oggetti nello stesso modo, l'accesso WMI generico consente di eseguire alcune attività avanzate con un impegno minimo.</span><span class="sxs-lookup"><span data-stu-id="63f39-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

<span data-ttu-id="63f39-108">Gli esempi seguenti dimostrano come raccogliere informazioni specifiche tramite **Get-WmiObject** su un computer arbitrario.</span><span class="sxs-lookup"><span data-stu-id="63f39-108">The following examples demonstrate how to collect specific information by using **Get-WmiObject** against an arbitrary computer.</span></span> <span data-ttu-id="63f39-109">Viene specificato il parametro **ComputerName** con il valore punto (**.**), che rappresenta il computer locale.</span><span class="sxs-lookup"><span data-stu-id="63f39-109">We specify the **ComputerName** parameter with the dot value (**.**), which represents the local computer.</span></span> <span data-ttu-id="63f39-110">È possibile specificare un nome o indirizzo IP associato a qualsiasi computer raggiungibile tramite WMI.</span><span class="sxs-lookup"><span data-stu-id="63f39-110">You can specify a name or IP address associated with any computer you can reach through WMI.</span></span> <span data-ttu-id="63f39-111">Per recuperare informazioni sul computer locale, è possibile omettere **-ComputerName.**</span><span class="sxs-lookup"><span data-stu-id="63f39-111">To retrieve information about the local computer, you could omit the **-ComputerName.**</span></span>

### <a name="listing-desktop-settings"></a><span data-ttu-id="63f39-112">Elenco delle impostazioni dei desktop</span><span class="sxs-lookup"><span data-stu-id="63f39-112">Listing Desktop Settings</span></span>
<span data-ttu-id="63f39-113">Inizieremo con un comando che raccoglie informazioni sui desktop nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="63f39-113">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName .
```

<span data-ttu-id="63f39-114">Questo comando restituisce informazioni per tutti i desktop, indipendentemente dal fatto che siano in uso o meno.</span><span class="sxs-lookup"><span data-stu-id="63f39-114">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="63f39-115">Le informazioni restituite da alcune classi WMI possono essere molto dettagliate e spesso includono i metadati sulla classe WMI.</span><span class="sxs-lookup"><span data-stu-id="63f39-115">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span> <span data-ttu-id="63f39-116">Dato che la maggior parte di queste proprietà dei metadati ha nomi che iniziano con un carattere di sottolineatura doppio, è possibile filtrare le proprietà con Select-Object.</span><span class="sxs-lookup"><span data-stu-id="63f39-116">Because most of these metadata properties have names that begin with a double underscore, you can filter the properties using Select-Object.</span></span> <span data-ttu-id="63f39-117">È possibile specificare solo le proprietà che iniziano con i caratteri alfabetici usando **[a-z]*** come valore di Property.</span><span class="sxs-lookup"><span data-stu-id="63f39-117">Specify only properties that begin with alphabetic characters by using **[a-z]*** as the Property value.</span></span> <span data-ttu-id="63f39-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="63f39-118">For example:</span></span>

```
Get-WmiObject -Class Win32_Desktop -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="63f39-119">Per escludere i metadati, usare un operatore pipeline (|) per inviare i risultati del comando Get-WmiObject a **Select-Object -Property [a-z]***.</span><span class="sxs-lookup"><span data-stu-id="63f39-119">To filter out the metadata, use a pipeline operator (|) to send the results of the Get-WmiObject command to **Select-Object -Property [a-z]***.</span></span>

### <a name="listing-bios-information"></a><span data-ttu-id="63f39-120">Elenco delle informazioni sul BIOS</span><span class="sxs-lookup"><span data-stu-id="63f39-120">Listing BIOS Information</span></span>
<span data-ttu-id="63f39-121">La classe WMI Win32_BIOS restituisce informazioni piuttosto compatte e complete sul BIOS di sistema nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="63f39-121">The WMI Win32_BIOS class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```
Get-WmiObject -Class Win32_BIOS -ComputerName .
```

### <a name="listing-processor-information"></a><span data-ttu-id="63f39-122">Elenco delle informazioni sul processore</span><span class="sxs-lookup"><span data-stu-id="63f39-122">Listing Processor Information</span></span>
<span data-ttu-id="63f39-123">È possibile recuperare informazioni generali sul processore tramite la classe WMI **Win32_Processor**, anche se è probabile che si preferisca filtrare le informazioni:</span><span class="sxs-lookup"><span data-stu-id="63f39-123">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```
Get-WmiObject -Class Win32_Processor -ComputerName . | Select-Object -Property [a-z]*
```

<span data-ttu-id="63f39-124">Per ottenere una stringa di descrizione generica della famiglia di processori, è possibile restituire semplicemente la proprietà **SystemType**:</span><span class="sxs-lookup"><span data-stu-id="63f39-124">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem -ComputerName . | Select-Object -Property SystemType
SystemType
----------
X86-based PC
```

### <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="63f39-125">Elenco di produttore e modello del computer</span><span class="sxs-lookup"><span data-stu-id="63f39-125">Listing Computer Manufacturer and Model</span></span>
<span data-ttu-id="63f39-126">Le informazioni sul modello di computer sono disponibili anche da **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="63f39-126">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="63f39-127">Non sarà necessario filtrare l'output visualizzato standard per fornire dati OEM:</span><span class="sxs-lookup"><span data-stu-id="63f39-127">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```
PS> Get-WmiObject -Class Win32_ComputerSystem
Domain              : WORKGROUP
Manufacturer        : Compaq Presario 06
Model               : DA243A-ABA 6415cl NA910
Name                : MyPC
PrimaryOwnerName    : Jane Doe
TotalPhysicalMemory : 804765696
```

<span data-ttu-id="63f39-128">La validità dell'output di comandi come questo, che restituiscono informazioni direttamente dai componenti hardware, dipende esclusivamente dai dati disponibili.</span><span class="sxs-lookup"><span data-stu-id="63f39-128">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="63f39-129">Alcune informazioni non sono configurate correttamente dai produttori dell'hardware e pertanto potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="63f39-129">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

### <a name="listing-installed-hotfixes"></a><span data-ttu-id="63f39-130">Elenco degli hotfix installati</span><span class="sxs-lookup"><span data-stu-id="63f39-130">Listing Installed Hotfixes</span></span>
<span data-ttu-id="63f39-131">È possibile ottenere un elenco di tutti gli hotfix installati tramite **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="63f39-131">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```
Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName .
```

<span data-ttu-id="63f39-132">Questa classe restituisce un elenco di hotfix simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="63f39-132">This class returns a list of hotfixes that looks like this:</span></span>

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

<span data-ttu-id="63f39-133">Per ottenere un output più conciso, è possibile escludere alcune proprietà.</span><span class="sxs-lookup"><span data-stu-id="63f39-133">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="63f39-134">Anche se è possibile usare il parametro Property di **Get-WmiObject** per scegliere solo **HotFixID**, in questo modo si otterranno in effetti più informazioni, perché vengono visualizzati per impostazione predefinita tutti i metadati:</span><span class="sxs-lookup"><span data-stu-id="63f39-134">Although you can use the **Get-WmiObject's Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property HotFixID
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

<span data-ttu-id="63f39-135">Vengono restituiti dati aggiuntivi perché il parametro Property in **Get-WmiObject** limita le proprietà restituite da istanze della classe WMI e non l'oggetto restituito a Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63f39-135">The additional data is returned, because the Property parameter in **Get-WmiObject** restricts the properties returned from WMI class instances, not the object returned to Windows PowerShell.</span></span> <span data-ttu-id="63f39-136">Per ridurre l'output, usare **Select-Object**:</span><span class="sxs-lookup"><span data-stu-id="63f39-136">To reduce the output, use **Select-Object**:</span></span>

```
PS> Get-WmiObject -Class Win32_QuickFixEngineering -ComputerName . -Property Hot
FixId | Select-Object -Property HotFixId
HotFixId
--------
KB910437
```

### <a name="listing-operating-system-version-information"></a><span data-ttu-id="63f39-137">Elenco di informazioni sulla versione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="63f39-137">Listing Operating System Version Information</span></span>
<span data-ttu-id="63f39-138">Le proprietà della classe **Win32_OperatingSystem** includono informazioni sulla versione e sui Service Pack.</span><span class="sxs-lookup"><span data-stu-id="63f39-138">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="63f39-139">È possibile selezionare esplicitamente queste proprietà per ottenere un riepilogo delle informazioni sulla versione da **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="63f39-139">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="63f39-140">È anche possibile usare caratteri jolly con il parametro Property di **Select-Object**.</span><span class="sxs-lookup"><span data-stu-id="63f39-140">You can also use wildcards with the **Select-Object's Property** parameter.</span></span> <span data-ttu-id="63f39-141">Dato che in questo caso è importante usare tutte le proprietà che iniziano con **Build** o **ServicePack**, è possibile abbreviare il comando in questo modo:</span><span class="sxs-lookup"><span data-stu-id="63f39-141">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property Build*,OSType,ServicePack*

BuildNumber             : 2600
BuildType               : Uniprocessor Free
OSType                  : 18
ServicePackMajorVersion : 2
ServicePackMinorVersion : 0
```

### <a name="listing-local-users-and-owner"></a><span data-ttu-id="63f39-142">Elenco di utenti locali e proprietario</span><span class="sxs-lookup"><span data-stu-id="63f39-142">Listing Local Users and Owner</span></span>
<span data-ttu-id="63f39-143">È possibile trovare informazioni generali e locali sugli utenti (numero di utenti con licenza, numero corrente di utenti e nome del proprietario) con una selezione delle proprietà di **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="63f39-143">Local general user information—number of licensed users, current number of users, and owner name—can be found with a selection of **Win32_OperatingSystem** properties.</span></span> <span data-ttu-id="63f39-144">È possibile selezionare in modo esplicito le proprietà da visualizzare come segue:</span><span class="sxs-lookup"><span data-stu-id="63f39-144">You can explicitly select the properties to display like this:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="63f39-145">Questa è una versione più concisa con caratteri jolly:</span><span class="sxs-lookup"><span data-stu-id="63f39-145">A more succinct version using wildcards is:</span></span>

```
Get-WmiObject -Class Win32_OperatingSystem -ComputerName . | Select-Object -Property *user*
```

### <a name="getting-available-disk-space"></a><span data-ttu-id="63f39-146">Recupero dello spazio su disco disponibile</span><span class="sxs-lookup"><span data-stu-id="63f39-146">Getting Available Disk Space</span></span>
<span data-ttu-id="63f39-147">Per visualizzare lo spazio su disco e lo spazio disponibile per le unità locali, è possibile usare la classe WMI Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="63f39-147">To see the disk space and free space for local drives, you can use the WMI Win32_LogicalDisk class.</span></span> <span data-ttu-id="63f39-148">È necessario visualizzare solo le istanze con DriveType 3, ovvero il valore usato da WMI per i dischi rigidi fissi.</span><span class="sxs-lookup"><span data-stu-id="63f39-148">You need to see only instances with a DriveType of 3—the value WMI uses for fixed hard disks.</span></span>

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

Get-WmiObject -Class Win32_LogicalDisk -Filter "DriveType=3" -ComputerName . | Measure-Object -Property FreeSpace,Size -Sum | Select-Object -Property Property,Sum
```

### <a name="getting-logon-session-information"></a><span data-ttu-id="63f39-149">Recupero di informazioni sulle sessioni di accesso</span><span class="sxs-lookup"><span data-stu-id="63f39-149">Getting Logon Session Information</span></span>
<span data-ttu-id="63f39-150">È possibile ottenere informazioni generali sulle sessioni di accesso associate agli utenti tramite la classe WMI Win32_LogonSession:</span><span class="sxs-lookup"><span data-stu-id="63f39-150">You can get general information about logon sessions associated with users through the WMI Win32_LogonSession class:</span></span>

```
Get-WmiObject -Class Win32_LogonSession -ComputerName .
```

### <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="63f39-151">Recupero dell'utente connesso a un computer</span><span class="sxs-lookup"><span data-stu-id="63f39-151">Getting the User Logged on to a Computer</span></span>
<span data-ttu-id="63f39-152">È possibile visualizzare l'utente connesso a un computer specifico con Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="63f39-152">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="63f39-153">Questo comando restituisce solo l'utente connesso al desktop di sistema:</span><span class="sxs-lookup"><span data-stu-id="63f39-153">This command returns only the user logged on to the system desktop:</span></span>

```
Get-WmiObject -Class Win32_ComputerSystem -Property UserName -ComputerName .
```

### <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="63f39-154">Recupero dell'ora locale da un computer</span><span class="sxs-lookup"><span data-stu-id="63f39-154">Getting Local Time from a Computer</span></span>
<span data-ttu-id="63f39-155">È possibile recuperare l'ora locale corrente in un computer specifico con la classe WMI Win32_LocalTime.</span><span class="sxs-lookup"><span data-stu-id="63f39-155">You can retrieve the current local time on a specific computer by using the WMI Win32_LocalTime class.</span></span> <span data-ttu-id="63f39-156">Dato che questa classe visualizza per impostazione predefinita tutti i metadati, è possibile usare **Select-Object** per filtrare le informazioni:</span><span class="sxs-lookup"><span data-stu-id="63f39-156">Because this class by default displays all metadata, you may want to filter it using **Select-Object**:</span></span>

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

### <a name="displaying-service-status"></a><span data-ttu-id="63f39-157">Visualizzazione dello stato dei servizi</span><span class="sxs-lookup"><span data-stu-id="63f39-157">Displaying Service Status</span></span>
<span data-ttu-id="63f39-158">Per visualizzare lo stato di tutti i servizi in un computer specifico, è possibile usare in locale il cmdlet **Get-Service** come indicato in precedenza.</span><span class="sxs-lookup"><span data-stu-id="63f39-158">To view the status of all services on a specific computer, you can locally use the **Get-Service** cmdlet as mentioned earlier.</span></span> <span data-ttu-id="63f39-159">Per i sistemi remoti, è possibile usare la classe WMI Win32_Service.</span><span class="sxs-lookup"><span data-stu-id="63f39-159">For remote systems, you can use the WMI Win32_Service class.</span></span> <span data-ttu-id="63f39-160">Se si usa anche **Select-Object** per filtrare i risultati per **Status**, **Name** e **DisplayName**, il formato dell'output sarà praticamente identico a quello ottenuto da **Get-Service**:</span><span class="sxs-lookup"><span data-stu-id="63f39-160">If you also use **Select-Object** to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from **Get-Service**:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="63f39-161">Per consentire la visualizzazione completa dei nomi per i servizi occasionali con nomi estremamente lunghi, è possibile usare **Format-Table** con i parametri **AutoSize** e **Wrap**, per ottimizzare la larghezza della colonna e consentire il ritorno a capo dei nomi lunghi anziché il troncamento:</span><span class="sxs-lookup"><span data-stu-id="63f39-161">To allow the complete display of names for the occasional services with extremely long names, you may want to use **Format-Table** with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```
Get-WmiObject -Class Win32_Service -ComputerName . | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```

