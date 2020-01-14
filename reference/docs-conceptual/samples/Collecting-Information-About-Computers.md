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
# <a name="collecting-information-about-computers"></a><span data-ttu-id="69642-103">Raccolta di informazioni sui computer</span><span class="sxs-lookup"><span data-stu-id="69642-103">Collecting Information About Computers</span></span>

<span data-ttu-id="69642-104">I cmdlet nel modulo **CimCmdlets** sono i più importanti per le attività di gestione generali del sistema.</span><span class="sxs-lookup"><span data-stu-id="69642-104">Cmdlets from **CimCmdlets** module are the most important cmdlets for general system management tasks.</span></span> <span data-ttu-id="69642-105">Tutte le impostazioni del sottosistema cruciali sono esposte tramite WMI.</span><span class="sxs-lookup"><span data-stu-id="69642-105">All critical subsystem settings are exposed through WMI.</span></span> <span data-ttu-id="69642-106">WMI gestisce inoltre i dati come oggetti inclusi in raccolte di uno o più elementi.</span><span class="sxs-lookup"><span data-stu-id="69642-106">Furthermore, WMI treats data as objects that are in collections of one or more items.</span></span> <span data-ttu-id="69642-107">Dato che anche Windows PowerShell funziona con oggetti e usa una pipeline che consente di gestire uno o più oggetti nello stesso modo, l'accesso WMI generico consente di eseguire alcune attività avanzate con un impegno minimo.</span><span class="sxs-lookup"><span data-stu-id="69642-107">Because Windows PowerShell also works with objects and has a pipeline that allows you to treat single or multiple objects in the same way, generic WMI access allows you to perform some advanced tasks with very little work.</span></span>

## <a name="listing-desktop-settings"></a><span data-ttu-id="69642-108">Elenco delle impostazioni dei desktop</span><span class="sxs-lookup"><span data-stu-id="69642-108">Listing Desktop Settings</span></span>

<span data-ttu-id="69642-109">Inizieremo con un comando che raccoglie informazioni sui desktop nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="69642-109">We'll begin with a command that collects information about the desktops on the local computer.</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop
```

<span data-ttu-id="69642-110">Questo comando restituisce informazioni per tutti i desktop, indipendentemente dal fatto che siano in uso o meno.</span><span class="sxs-lookup"><span data-stu-id="69642-110">This returns information for all desktops, whether they are in use or not.</span></span>

> [!NOTE]
> <span data-ttu-id="69642-111">Le informazioni restituite da alcune classi WMI possono essere molto dettagliate e spesso includono i metadati sulla classe WMI.</span><span class="sxs-lookup"><span data-stu-id="69642-111">Information returned by some WMI classes can be very detailed, and often include metadata about the WMI class.</span></span>

<span data-ttu-id="69642-112">Dato che la maggior parte delle proprietà di questi metadati ha nomi che iniziano con **Cim**, è possibile filtrare le proprietà usando `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="69642-112">Because most of these metadata properties have names that begin with **Cim**, you can filter the properties using `Select-Object`.</span></span> <span data-ttu-id="69642-113">Specificare il parametro **- ExcludeProperty** usando "Cim \*" come valore.</span><span class="sxs-lookup"><span data-stu-id="69642-113">Specify the **-ExcludeProperty** parameter with "Cim\*" as the value.</span></span> <span data-ttu-id="69642-114">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="69642-114">For example:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Desktop | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="69642-115">Per escludere i metadati, usare un operatore pipeline (|) per inviare i risultati del comando `Get-CimInstance` a `Select-Object -ExcludeProperty "CIM*"`.</span><span class="sxs-lookup"><span data-stu-id="69642-115">To filter out the metadata, use a pipeline operator (|) to send the results of the `Get-CimInstance` command to `Select-Object -ExcludeProperty "CIM*"`.</span></span>

## <a name="listing-bios-information"></a><span data-ttu-id="69642-116">Elenco delle informazioni sul BIOS</span><span class="sxs-lookup"><span data-stu-id="69642-116">Listing BIOS Information</span></span>

<span data-ttu-id="69642-117">La classe WMI **Win32_BIOS** restituisce informazioni piuttosto compatte e complete sul BIOS di sistema nel computer locale:</span><span class="sxs-lookup"><span data-stu-id="69642-117">The WMI **Win32_BIOS** class returns fairly compact and complete information about the system BIOS on the local computer:</span></span>

```powershell
Get-CimInstance -ClassName Win32_BIOS
```

## <a name="listing-processor-information"></a><span data-ttu-id="69642-118">Elenco delle informazioni sul processore</span><span class="sxs-lookup"><span data-stu-id="69642-118">Listing Processor Information</span></span>

<span data-ttu-id="69642-119">È possibile recuperare informazioni generali sul processore tramite la classe WMI **Win32_Processor**, anche se è probabile che si preferisca filtrare le informazioni:</span><span class="sxs-lookup"><span data-stu-id="69642-119">You can retrieve general processor information by using WMI's **Win32_Processor** class, although you will likely want to filter the information:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Processor | Select-Object -ExcludeProperty "CIM*"
```

<span data-ttu-id="69642-120">Per ottenere una stringa di descrizione generica della famiglia di processori, è possibile restituire semplicemente la proprietà **SystemType**:</span><span class="sxs-lookup"><span data-stu-id="69642-120">For a generic description string of the processor family, you can just return the **SystemType** property:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem | Select-Object -Property SystemType

SystemType
----------
X86-based PC
```

## <a name="listing-computer-manufacturer-and-model"></a><span data-ttu-id="69642-121">Elenco di produttore e modello del computer</span><span class="sxs-lookup"><span data-stu-id="69642-121">Listing Computer Manufacturer and Model</span></span>

<span data-ttu-id="69642-122">Le informazioni sul modello di computer sono disponibili anche da **Win32_ComputerSystem**.</span><span class="sxs-lookup"><span data-stu-id="69642-122">Computer model information is also available from **Win32_ComputerSystem**.</span></span> <span data-ttu-id="69642-123">Non sarà necessario filtrare l'output visualizzato standard per fornire dati OEM:</span><span class="sxs-lookup"><span data-stu-id="69642-123">The standard displayed output will not need any filtering to provide OEM data:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem
```

```Output
Name PrimaryOwnerName Domain    TotalPhysicalMemory Model                   Manufacturer
---- ---------------- ------    ------------------- -----                   ------------
MyPC Jane Doe         WORKGROUP 804765696           DA243A-ABA 6415cl NA910 Compaq Presario 06
```

<span data-ttu-id="69642-124">La validità dell'output di comandi come questo, che restituiscono informazioni direttamente dai componenti hardware, dipende esclusivamente dai dati disponibili.</span><span class="sxs-lookup"><span data-stu-id="69642-124">Your output from commands such as this, which return information directly from some hardware, is only as good as the data you have.</span></span> <span data-ttu-id="69642-125">Alcune informazioni non sono configurate correttamente dai produttori dell'hardware e pertanto potrebbero non essere disponibili.</span><span class="sxs-lookup"><span data-stu-id="69642-125">Some information is not correctly configured by hardware manufacturers and may therefore be unavailable.</span></span>

## <a name="listing-installed-hotfixes"></a><span data-ttu-id="69642-126">Elenco degli hotfix installati</span><span class="sxs-lookup"><span data-stu-id="69642-126">Listing Installed Hotfixes</span></span>

<span data-ttu-id="69642-127">È possibile ottenere un elenco di tutti gli hotfix installati tramite **Win32_QuickFixEngineering**:</span><span class="sxs-lookup"><span data-stu-id="69642-127">You can list all installed hotfixes by using **Win32_QuickFixEngineering**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering
```

<span data-ttu-id="69642-128">Questa classe restituisce un elenco di hotfix simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="69642-128">This class returns a list of hotfixes that looks like this:</span></span>

```Output
Source Description     HotFixID  InstalledBy   InstalledOn PSComputerName
------ -----------     --------  -----------   ----------- --------------
       Security Update KB4048951 Administrator 12/16/2017  .
```

<span data-ttu-id="69642-129">Per ottenere un output più conciso, è possibile escludere alcune proprietà.</span><span class="sxs-lookup"><span data-stu-id="69642-129">For more succinct output, you may want to exclude some properties.</span></span> <span data-ttu-id="69642-130">Anche se è possibile usare il parametro **Property** di `Get-CimInstance` per scegliere solo **HotFixID**, in questo modo si otterranno in realtà più informazioni, perché per impostazione predefinita vengono visualizzati tutti i metadati:</span><span class="sxs-lookup"><span data-stu-id="69642-130">Although you can use the `Get-CimInstance`'s **Property** parameter to choose only the **HotFixID**, doing so will actually return more information, because all the metadata is displayed by default:</span></span>

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

<span data-ttu-id="69642-131">Vengono restituiti dati aggiuntivi perché il parametro **Property** in `Get-CimInstance` limita le proprietà restituite dalle istanze della classe WMI, non l'oggetto restituito a PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69642-131">The additional data is returned, because the **Property** parameter in `Get-CimInstance` restricts the properties returned from WMI class instances, not the object returned to PowerShell.</span></span> <span data-ttu-id="69642-132">Per ridurre l'output, usare `Select-Object`:</span><span class="sxs-lookup"><span data-stu-id="69642-132">To reduce the output, use `Select-Object`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_QuickFixEngineering -Property HotFixId | Select-Object -Property HotFixId
```

```Output
HotFixId
--------
KB4048951
```

## <a name="listing-operating-system-version-information"></a><span data-ttu-id="69642-133">Elenco di informazioni sulla versione del sistema operativo</span><span class="sxs-lookup"><span data-stu-id="69642-133">Listing Operating System Version Information</span></span>

<span data-ttu-id="69642-134">Le proprietà della classe **Win32_OperatingSystem** includono informazioni sulla versione e sui Service Pack.</span><span class="sxs-lookup"><span data-stu-id="69642-134">The **Win32_OperatingSystem** class properties include version and service pack information.</span></span> <span data-ttu-id="69642-135">È possibile selezionare esplicitamente queste proprietà per ottenere un riepilogo delle informazioni sulla versione da **Win32_OperatingSystem**:</span><span class="sxs-lookup"><span data-stu-id="69642-135">You can explicitly select only these properties to get a version information summary from **Win32_OperatingSystem**:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property BuildNumber,BuildType,OSType,ServicePackMajorVersion,ServicePackMinorVersion
```

<span data-ttu-id="69642-136">È anche possibile usare caratteri jolly con il parametro **Property** di `Select-Object`.</span><span class="sxs-lookup"><span data-stu-id="69642-136">You can also use wildcards with the `Select-Object`'s **Property** parameter.</span></span> <span data-ttu-id="69642-137">Dato che in questo caso è importante usare tutte le proprietà che iniziano con **Build** o **ServicePack**, è possibile abbreviare il comando in questo modo:</span><span class="sxs-lookup"><span data-stu-id="69642-137">Because all the properties beginning with either **Build** or **ServicePack** are important to use here, we can shorten this to the following form:</span></span>

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

## <a name="listing-local-users-and-owner"></a><span data-ttu-id="69642-138">Elenco di utenti locali e proprietario</span><span class="sxs-lookup"><span data-stu-id="69642-138">Listing Local Users and Owner</span></span>

<span data-ttu-id="69642-139">Selezionando le proprietà della classe **Win32_OperatingSystem** è possibile trovare informazioni locali generali sugli utenti, ad esempio il numero di utenti con licenza, il numero corrente di utenti e il nome del proprietario.</span><span class="sxs-lookup"><span data-stu-id="69642-139">Local general user information — number of licensed users, current number of users, and owner name — can be found with a selection of **Win32_OperatingSystem** class properties.</span></span> <span data-ttu-id="69642-140">È possibile selezionare in modo esplicito le proprietà da visualizzare come segue:</span><span class="sxs-lookup"><span data-stu-id="69642-140">You can explicitly select the properties to display like this:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem |
  Select-Object -Property NumberOfLicensedUsers,NumberOfUsers,RegisteredUser
```

<span data-ttu-id="69642-141">Questa è una versione più concisa con caratteri jolly:</span><span class="sxs-lookup"><span data-stu-id="69642-141">A more succinct version using wildcards is:</span></span>

```powershell
Get-CimInstance -ClassName Win32_OperatingSystem | Select-Object -Property *user*
```

## <a name="getting-available-disk-space"></a><span data-ttu-id="69642-142">Recupero dello spazio su disco disponibile</span><span class="sxs-lookup"><span data-stu-id="69642-142">Getting Available Disk Space</span></span>

<span data-ttu-id="69642-143">Per visualizzare lo spazio su disco e lo spazio disponibile per le unità locali, è possibile usare la classe WMI Win32_LogicalDisk.</span><span class="sxs-lookup"><span data-stu-id="69642-143">To see the disk space and free space for local drives, you can use the Win32_LogicalDisk WMI class.</span></span>
<span data-ttu-id="69642-144">È necessario visualizzare solo le istanze con DriveType 3, ovvero il valore usato dalla classe WMI per i dischi rigidi fissi.</span><span class="sxs-lookup"><span data-stu-id="69642-144">You need to see only instances with a DriveType of 3 — the value WMI uses for fixed hard disks.</span></span>

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

## <a name="getting-logon-session-information"></a><span data-ttu-id="69642-145">Recupero di informazioni sulle sessioni di accesso</span><span class="sxs-lookup"><span data-stu-id="69642-145">Getting Logon Session Information</span></span>

<span data-ttu-id="69642-146">È possibile ottenere informazioni generali sulle sessioni di accesso associate agli utenti tramite la classe WMI **Win32_LogonSession**:</span><span class="sxs-lookup"><span data-stu-id="69642-146">You can get general information about logon sessions associated with users through the **Win32_LogonSession** WMI class:</span></span>

```powershell
Get-CimInstance -ClassName Win32_LogonSession
```

## <a name="getting-the-user-logged-on-to-a-computer"></a><span data-ttu-id="69642-147">Recupero dell'utente connesso a un computer</span><span class="sxs-lookup"><span data-stu-id="69642-147">Getting the User Logged on to a Computer</span></span>

<span data-ttu-id="69642-148">È possibile visualizzare l'utente connesso a un computer specifico con Win32_ComputerSystem.</span><span class="sxs-lookup"><span data-stu-id="69642-148">You can display the user logged on to a particular computer system using Win32_ComputerSystem.</span></span> <span data-ttu-id="69642-149">Questo comando restituisce solo l'utente connesso al desktop di sistema:</span><span class="sxs-lookup"><span data-stu-id="69642-149">This command returns only the user logged on to the system desktop:</span></span>

```powershell
Get-CimInstance -ClassName Win32_ComputerSystem -Property UserName
```

## <a name="getting-local-time-from-a-computer"></a><span data-ttu-id="69642-150">Recupero dell'ora locale da un computer</span><span class="sxs-lookup"><span data-stu-id="69642-150">Getting Local Time from a Computer</span></span>

<span data-ttu-id="69642-151">È possibile recuperare l'ora locale corrente in un computer specifico con la classe WMI **Win32_LocalTime**.</span><span class="sxs-lookup"><span data-stu-id="69642-151">You can retrieve the current local time on a specific computer by using the **Win32_LocalTime** WMI class.</span></span>

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

## <a name="displaying-service-status"></a><span data-ttu-id="69642-152">Visualizzazione dello stato dei servizi</span><span class="sxs-lookup"><span data-stu-id="69642-152">Displaying Service Status</span></span>

<span data-ttu-id="69642-153">Per visualizzare lo stato di tutti i servizi in un computer specifico, è possibile usare in locale il cmdlet `Get-Service`.</span><span class="sxs-lookup"><span data-stu-id="69642-153">To view the status of all services on a specific computer, you can locally use the `Get-Service` cmdlet.</span></span> <span data-ttu-id="69642-154">Per i sistemi remoti, è possibile usare la classe WMI **Win32_Service**.</span><span class="sxs-lookup"><span data-stu-id="69642-154">For remote systems, you can use the **Win32_Service** WMI class.</span></span> <span data-ttu-id="69642-155">Se si usa `Select-Object` anche per filtrare i risultati per **Status**, **Name** e **DisplayName**, il formato dell'output sarà quasi identico a quello ottenuto da `Get-Service`:</span><span class="sxs-lookup"><span data-stu-id="69642-155">If you also use `Select-Object` to filter the results to **Status**, **Name**, and **DisplayName**, the output format will be almost identical to that from `Get-Service`:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Select-Object -Property Status,Name,DisplayName
```

<span data-ttu-id="69642-156">Per consentire la visualizzazione completa dei nomi nei casi occasionali di servizi con nomi estremamente lunghi e ottimizzare la larghezza della colonna consentendo il ritorno a capo dei nomi lunghi anziché il troncamento, è possibile usare `Format-Table` con i parametri **AutoSize** e **Wrap**:</span><span class="sxs-lookup"><span data-stu-id="69642-156">To allow the complete display of names for the occasional services with extremely long names, you may want to use `Format-Table` with the **AutoSize** and **Wrap** parameters, to optimize column width and allow long names to wrap instead of being truncated:</span></span>

```powershell
Get-CimInstance -ClassName Win32_Service | Format-Table -Property Status,Name,DisplayName -AutoSize -Wrap
```
