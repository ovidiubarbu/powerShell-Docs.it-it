---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Ottenere oggetti WMI (Get CimInstance)
ms.openlocfilehash: 4ff47844fd367a49f554c7c05c491bdddf28eabc
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "77002651"
---
# <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="cb518-103">Ottenere oggetti WMI (Get CimInstance)</span><span class="sxs-lookup"><span data-stu-id="cb518-103">Getting WMI Objects (Get-CimInstance)</span></span>

## <a name="getting-wmi-objects-get-ciminstance"></a><span data-ttu-id="cb518-104">Ottenere oggetti WMI (Get CimInstance)</span><span class="sxs-lookup"><span data-stu-id="cb518-104">Getting WMI Objects (Get-CimInstance)</span></span>

<span data-ttu-id="cb518-105">Strumentazione gestione Windows (WMI) è una tecnologia fondamentale per l'amministrazione del sistema Windows poiché espone un'ampia gamma di informazioni in modo uniforme.</span><span class="sxs-lookup"><span data-stu-id="cb518-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="cb518-106">Considerando le potenzialità d'uso di WMI, il cmdlet di PowerShell per l'accesso agli oggetti WMI, `Get-CimInstance`, è uno dei più utili per eseguire il lavoro effettivo.</span><span class="sxs-lookup"><span data-stu-id="cb518-106">Because of how much WMI makes possible, the PowerShell cmdlet for accessing WMI objects, `Get-CimInstance`, is one of the most useful for doing real work.</span></span> <span data-ttu-id="cb518-107">Verrà illustrato come usare CimCmdlets per accedere agli oggetti WMI e quindi come usare questi oggetti per eseguire operazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="cb518-107">We are going to discuss how to use the CimCmdlets to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="cb518-108">Elenco delle classi WMI</span><span class="sxs-lookup"><span data-stu-id="cb518-108">Listing WMI Classes</span></span>

<span data-ttu-id="cb518-109">Il primo problema che la maggior parte degli utenti di WMI si trova ad affrontare è scoprire che cosa si può fare con WMI.</span><span class="sxs-lookup"><span data-stu-id="cb518-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="cb518-110">Le classi WMI descrivono le risorse che possono essere gestite.</span><span class="sxs-lookup"><span data-stu-id="cb518-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="cb518-111">Sono disponibili centinaia di classi WMI, alcune delle quali contengono decine di proprietà.</span><span class="sxs-lookup"><span data-stu-id="cb518-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="cb518-112">`Get-CimClass` risolve questo problema rendendo individuabile WMI.</span><span class="sxs-lookup"><span data-stu-id="cb518-112">`Get-CimClass` addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="cb518-113">È possibile ottenere un elenco delle classi WMI disponibili nel computer locale digitando:</span><span class="sxs-lookup"><span data-stu-id="cb518-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

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

<span data-ttu-id="cb518-114">È possibile recuperare le stesse informazioni da un computer remoto usando il parametro **ComputerName**, specificando un nome di computer o un indirizzo IP:</span><span class="sxs-lookup"><span data-stu-id="cb518-114">You can retrieve the same information from a remote computer by using the **ComputerName** parameter, specifying a computer name or IP address:</span></span>

```powershell
Get-CimClass -Namespace root/CIMV2 -ComputerName 192.168.1.29
```

<span data-ttu-id="cb518-115">L'elenco delle classi restituito dai computer remoti può variare in base allo specifico sistema operativo in esecuzione nel computer e alle particolari estensioni di WMI aggiunte dalle applicazioni installate.</span><span class="sxs-lookup"><span data-stu-id="cb518-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="cb518-116">Quando si usano i cmdlet CIM per connettersi a un computer remoto, WMI deve essere in esecuzione nel computer remoto e l'account in uso deve appartenere al gruppo Administrators locale nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="cb518-116">When using CIM cmdlets to connect to a remote computer, the remote computer must be running WMI and the account you are using must be in the local administrators group on the remote computer.</span></span>
> <span data-ttu-id="cb518-117">Non è necessario che PowerShell sia installato nel sistema remoto.</span><span class="sxs-lookup"><span data-stu-id="cb518-117">The remote system does not need to have PowerShell installed.</span></span> <span data-ttu-id="cb518-118">In questo modo è possibile amministrare i sistemi operativi che non eseguono PowerShell, ma in cui è disponibile WMI.</span><span class="sxs-lookup"><span data-stu-id="cb518-118">This allows you to administer operating systems that are not running PowerShell, but do have WMI available.</span></span>

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="cb518-119">Visualizzazione dei dettagli della classe WMI</span><span class="sxs-lookup"><span data-stu-id="cb518-119">Displaying WMI Class Details</span></span>

<span data-ttu-id="cb518-120">Se si conosce già il nome di una classe WMI, è possibile usarlo per ottenere immediatamente informazioni.</span><span class="sxs-lookup"><span data-stu-id="cb518-120">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="cb518-121">Una delle classi WMI comunemente usate per il recupero di informazioni su un computer è ad esempio **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="cb518-121">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```powershell
Get-CimInstance -Class Win32_OperatingSystem
```

```Output
SystemDirectory     Organization BuildNumber RegisteredUser SerialNumber            Version
---------------     ------------ ----------- -------------- ------------            -------
C:\WINDOWS\system32 Microsoft    18362       USER1          00330-80000-00000-AA175 10.0.18362
```

<span data-ttu-id="cb518-122">Anche se vengono mostrati tutti i parametri, il comando può essere espresso in modo più conciso.</span><span class="sxs-lookup"><span data-stu-id="cb518-122">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span>
<span data-ttu-id="cb518-123">Il parametro **ComputerName** non è necessario quando ci si connette al sistema locale.</span><span class="sxs-lookup"><span data-stu-id="cb518-123">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="cb518-124">Viene mostrato solo per dimostrare il caso più generale e ricordare l'esistenza del parametro.</span><span class="sxs-lookup"><span data-stu-id="cb518-124">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="cb518-125">Il valore predefinito di **Namespace** è `root/CIMV2` e può essere anch'esso omesso.</span><span class="sxs-lookup"><span data-stu-id="cb518-125">The **Namespace** defaults to `root/CIMV2`, and can be omitted as well.</span></span> <span data-ttu-id="cb518-126">La maggior parte dei cmdlet consente infine di omettere il nome dei parametri comuni.</span><span class="sxs-lookup"><span data-stu-id="cb518-126">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="cb518-127">Con `Get-CimInstance`, se non viene specificato alcun nome per il primo parametro, PowerShell lo considera come parametro **Class**.</span><span class="sxs-lookup"><span data-stu-id="cb518-127">With `Get-CimInstance`, if no name is specified for the first parameter, PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="cb518-128">Ciò significa che l'ultimo comando avrebbe potuto essere emesso digitando:</span><span class="sxs-lookup"><span data-stu-id="cb518-128">This means the last command could have been issued by typing:</span></span>

```powershell
Get-CimInstance Win32_OperatingSystem
```

<span data-ttu-id="cb518-129">La classe **Win32_OperatingSystem** ha molte più proprietà di quelle mostrate in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="cb518-129">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="cb518-130">È possibile usare Get-Member per visualizzare tutte le proprietà.</span><span class="sxs-lookup"><span data-stu-id="cb518-130">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="cb518-131">Le proprietà di una classe WMI sono disponibili automaticamente come altre proprietà dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="cb518-131">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="cb518-132">Visualizzazione di proprietà non predefinite con i cmdlet Format</span><span class="sxs-lookup"><span data-stu-id="cb518-132">Displaying Non-Default Properties with Format Cmdlets</span></span>

<span data-ttu-id="cb518-133">Se si necessita di informazioni contenute nella classe **Win32_OperatingSystem** che non sono visualizzate per impostazione predefinita, è possibile visualizzarle usando i cmdlet **Format**.</span><span class="sxs-lookup"><span data-stu-id="cb518-133">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="cb518-134">Se ad esempio si vogliono visualizzare i dati disponibili relativi alla memoria, digitare:</span><span class="sxs-lookup"><span data-stu-id="cb518-134">For example, if you want to display available memory data, type:</span></span>

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
> <span data-ttu-id="cb518-135">I caratteri jolly possono essere usati con i nomi delle proprietà in `Format-Table`, pertanto l'elemento finale della pipeline può essere ridotto a `Format-Table -Property Total*Memory*, Free*`</span><span class="sxs-lookup"><span data-stu-id="cb518-135">Wildcards work with property names in `Format-Table`, so the final pipeline element can be reduced to `Format-Table -Property Total*Memory*, Free*`</span></span>

<span data-ttu-id="cb518-136">I dati relativi alla memoria potrebbero essere più leggibili se si formattano come elenco digitando:</span><span class="sxs-lookup"><span data-stu-id="cb518-136">The memory data might be more readable if you format it as a list by typing:</span></span>

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
