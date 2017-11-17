---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Recupero di oggetti WMI Get WmiObject
ms.assetid: f0ddfc7d-6b5e-4832-82de-2283597ea70d
ms.openlocfilehash: fbaac2797dd62eb03a2be581b3b5f8be6dafc0ad
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="6bbe8-103">Recupero di oggetti WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="6bbe8-103">Getting WMI Objects (Get-WmiObject)</span></span>

## <a name="getting-wmi-objects-get-wmiobject"></a><span data-ttu-id="6bbe8-104">Recupero di oggetti WMI (Get-WmiObject)</span><span class="sxs-lookup"><span data-stu-id="6bbe8-104">Getting WMI Objects (Get-WmiObject)</span></span>
<span data-ttu-id="6bbe8-105">Strumentazione gestione Windows (WMI) è una tecnologia fondamentale per l'amministrazione del sistema Windows poiché espone un'ampia gamma di informazioni in modo uniforme.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-105">Windows Management Instrumentation (WMI) is a core technology for Windows system administration because it exposes a wide range of information in a uniform manner.</span></span> <span data-ttu-id="6bbe8-106">Considerando le potenzialità d'uso di WMI, il cmdlet di Windows PowerShell per l'accesso agli oggetti WMI, **Get-WmiObject**, è uno dei più utili per eseguire il lavoro effettivo.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-106">Because of how much WMI makes possible, the Windows PowerShell cmdlet for accessing WMI objects, **Get-WmiObject**, is one of the most useful for doing real work.</span></span> <span data-ttu-id="6bbe8-107">Verrà illustrato come usare Get-WmiObject per accedere agli oggetti WMI e quindi in che modo usare tali oggetti per eseguire operazioni specifiche.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-107">We are going to discuss how to use Get-WmiObject to access WMI objects and then how to use WMI objects to do specific things.</span></span>

### <a name="listing-wmi-classes"></a><span data-ttu-id="6bbe8-108">Elenco delle classi WMI</span><span class="sxs-lookup"><span data-stu-id="6bbe8-108">Listing WMI Classes</span></span>
<span data-ttu-id="6bbe8-109">Il primo problema che la maggior parte degli utenti di WMI si trova ad affrontare è scoprire che cosa si può fare con WMI.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-109">The first problem most WMI users encounter is trying to find out what can be done with WMI.</span></span> <span data-ttu-id="6bbe8-110">Le classi WMI descrivono le risorse che possono essere gestite.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-110">WMI classes describe the resources that can be managed.</span></span> <span data-ttu-id="6bbe8-111">Sono disponibili centinaia di classi WMI, alcune delle quali contengono decine di proprietà.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-111">There are hundreds of WMI classes, some of which contain dozens of properties.</span></span>

<span data-ttu-id="6bbe8-112">**Get-WmiObject** affronta questo problema rendendo individuabile Strumentazione gestione Windows (WMI).</span><span class="sxs-lookup"><span data-stu-id="6bbe8-112">**Get-WmiObject** addresses this problem by making WMI discoverable.</span></span> <span data-ttu-id="6bbe8-113">È possibile ottenere un elenco delle classi WMI disponibili nel computer locale digitando:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-113">You can get a list of the WMI classes available on the local computer by typing:</span></span>

```
PS> Get-WmiObject -List

__SecurityRelatedClass                  __NTLMUser9X
__PARAMETERS                            __SystemSecurity
__NotifyStatus                          __ExtendedStatus
Win32_PrivilegesStatus                  Win32_TSNetworkAdapterSettingError
Win32_TSRemoteControlSettingError       Win32_TSEnvironmentSettingError
...
```

<span data-ttu-id="6bbe8-114">È possibile recuperare le stesse informazioni da un computer remoto usando il parametro ComputerName, specificando un nome di computer o un indirizzo IP:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-114">You can retrieve the same information from a remote computer by using the ComputerName parameter, specifying a computer name or IP address:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
__ProviderRegistration                  __ObjectProviderRegistration
...
```

<span data-ttu-id="6bbe8-115">L'elenco delle classi restituito dai computer remoti può variare in base allo specifico sistema operativo in esecuzione nel computer e alle particolari estensioni di WMI aggiunte dalle applicazioni installate.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-115">The class listing returned by remote computers may vary due to the specific operating system the computer is running and the particular WMI extensions added by installed applications.</span></span>

> [!NOTE]
> <span data-ttu-id="6bbe8-116">Quando si usa Get-WmiObject per connettersi a un computer remoto, nel computer remoto deve essere in esecuzione WMI e, in base alla configurazione predefinita, l'account in uso deve appartenere al gruppo Administrators locale nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-116">When using Get-WmiObject to connect to a remote computer, the remote computer must be running WMI and, under the default configuration, the account you are using must be in the local administrators group on the remote computer.</span></span> <span data-ttu-id="6bbe8-117">Non è necessario che nel sistema remoto sia installato Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-117">The remote system does not need to have Windows PowerShell installed.</span></span> <span data-ttu-id="6bbe8-118">In questo modo è possibile amministrare i sistemi operativi che non eseguono Windows PowerShell, ma che dispongono di WMI.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-118">This allows you to administer operating systems that are not running Windows PowerShell, but do have WMI available.</span></span>

<span data-ttu-id="6bbe8-119">È anche possibile includere ComputerName quando ci si connette al sistema locale.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-119">You can even include the ComputerName when connecting to the local system.</span></span> <span data-ttu-id="6bbe8-120">È possibile usare il nome del computer locale, il relativo indirizzo IP (o l'indirizzo di loopback 127.0.0.1) o il punto ("."), a indicare il nome del computer in formato WMI.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-120">You can use the local computer's name, its IP address (or the loopback address 127.0.0.1), or the WMI-style '.' as the computer name.</span></span> <span data-ttu-id="6bbe8-121">Se si esegue Windows PowerShell in un computer denominato Admin01 con indirizzo IP 192.168.1.90, i comandi seguenti restituiranno tutti l'elenco delle classi WMI per tale computer:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-121">If you are running Windows PowerShell on a computer named Admin01 with IP address 192.168.1.90, the following commands will all return the WMI class listing for that computer:</span></span>

```
Get-WmiObject -List
Get-WmiObject -List -ComputerName .
Get-WmiObject -List -ComputerName Admin01
Get-WmiObject -List -ComputerName 192.168.1.90
Get-WmiObject -List -ComputerName 127.0.0.1
Get-WmiObject -List -ComputerName localhost
```

<span data-ttu-id="6bbe8-122">Per impostazione predefinita, Get-WmiObject usa lo spazio dei nomi root/cimv2.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-122">Get-WmiObject uses the root/cimv2 namespace by default.</span></span> <span data-ttu-id="6bbe8-123">Se si vuole specificare un altro spazio dei nomi WMI, usare il parametro **Namespace** e specificare il percorso dello spazio dei nomi corrispondente:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-123">If you want to specify another WMI namespace, use the **Namespace** parameter and specify the corresponding namespace path:</span></span>

```
PS> Get-WmiObject -List -ComputerName 192.168.1.29 -Namespace root

__SystemClass                           __NAMESPACE
__Provider                              __Win32Provider
...
```

### <a name="displaying-wmi-class-details"></a><span data-ttu-id="6bbe8-124">Visualizzazione dei dettagli della classe WMI</span><span class="sxs-lookup"><span data-stu-id="6bbe8-124">Displaying WMI Class Details</span></span>
<span data-ttu-id="6bbe8-125">Se si conosce già il nome di una classe WMI, è possibile usarlo per ottenere immediatamente informazioni.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-125">If you already know the name of a WMI class, you can use it to get information immediately.</span></span> <span data-ttu-id="6bbe8-126">Una delle classi WMI comunemente usate per il recupero di informazioni su un computer è ad esempio **Win32_OperatingSystem**.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-126">For example, one of the WMI classes commonly used for retrieving information about a computer is **Win32_OperatingSystem**.</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName .

SystemDirectory : C:\WINDOWS\system32
Organization    : Global Network Solutions
BuildNumber     : 2600
RegisteredUser  : Oliver W. Jones
SerialNumber    : 12345-678-9012345-67890
Version         : 5.1.2600
```

<span data-ttu-id="6bbe8-127">Anche se vengono mostrati tutti i parametri, il comando può essere espresso in modo più conciso.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-127">Although we are showing all of the parameters, the command can be expressed in a more succinct way.</span></span> <span data-ttu-id="6bbe8-128">Il parametro **ComputerName** non è necessario quando ci si connette al sistema locale.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-128">The **ComputerName** parameter is not necessary when connecting to the local system.</span></span> <span data-ttu-id="6bbe8-129">Viene mostrato solo per dimostrare il caso più generale e ricordare l'esistenza del parametro.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-129">We show it to demonstrate the most general case and remind you about the parameter.</span></span> <span data-ttu-id="6bbe8-130">Il valore predefinito di **Namespace** è root/cimv2 e anche questo parametro può essere omesso.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-130">The **Namespace** defaults to root/cimv2, and can be omitted as well.</span></span> <span data-ttu-id="6bbe8-131">La maggior parte dei cmdlet consente infine di omettere il nome dei parametri comuni.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-131">Finally, most cmdlets allow you to omit the name of common parameters.</span></span> <span data-ttu-id="6bbe8-132">Con Get-WmiObject, se non viene specificato alcun nome per il primo parametro, Windows PowerShell lo considererà come parametro **Class**.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-132">With Get-WmiObject, if no name is specified for the first parameter, Windows PowerShell treats it as the **Class** parameter.</span></span> <span data-ttu-id="6bbe8-133">Ciò significa che l'ultimo comando avrebbe potuto essere emesso digitando:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-133">This means the last command could have been issued by typing:</span></span>

```
Get-WmiObject Win32_OperatingSystem
```

<span data-ttu-id="6bbe8-134">La classe **Win32_OperatingSystem** ha molte più proprietà di quelle mostrate in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-134">The **Win32_OperatingSystem** class has many more properties than those displayed here.</span></span> <span data-ttu-id="6bbe8-135">È possibile usare Get-Member per visualizzare tutte le proprietà.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-135">You can use Get-Member to see all the properties.</span></span> <span data-ttu-id="6bbe8-136">Le proprietà di una classe WMI sono disponibili automaticamente come altre proprietà dell'oggetto:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-136">The properties of a WMI class are automatically available like other object properties:</span></span>

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

#### <a name="displaying-non-default-properties-with-format-cmdlets"></a><span data-ttu-id="6bbe8-137">Visualizzazione di proprietà non predefinite con i cmdlet Format</span><span class="sxs-lookup"><span data-stu-id="6bbe8-137">Displaying Non-Default Properties with Format Cmdlets</span></span>
<span data-ttu-id="6bbe8-138">Se si necessita di informazioni contenute nella classe **Win32_OperatingSystem** che non sono visualizzate per impostazione predefinita, è possibile visualizzarle usando i cmdlet **Format**.</span><span class="sxs-lookup"><span data-stu-id="6bbe8-138">If you want information contained in the **Win32_OperatingSystem** class that is not displayed by default, you can display it by using the **Format** cmdlets.</span></span> <span data-ttu-id="6bbe8-139">Se ad esempio si vogliono visualizzare i dati disponibili relativi alla memoria, digitare:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-139">For example, if you want to display available memory data, type:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-Table -Property TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize TotalVisibleMemory FreePhysicalMemory FreeVirtualMemory FreeSpaceInPagingFiles
---------------------- ---------------    ------------------ -==--------------------- ---------------
               2097024          785904                305808           2056724                1558232
```

> [!NOTE]
> <span data-ttu-id="6bbe8-140">I caratteri jolly possono essere usati con i nomi delle proprietà in **Format-Table**, pertanto l'elemento finale della pipeline può essere ridotto a **Format-Table -Property Total*,Free*</span><span class="sxs-lookup"><span data-stu-id="6bbe8-140">Wildcards work with property names in **Format-Table**, so the final pipeline element can be reduced to **Format-Table -Property Total*,Free*</span></span>

<span data-ttu-id="6bbe8-141">I dati relativi alla memoria potrebbero essere più leggibili se si formattano come elenco digitando:</span><span class="sxs-lookup"><span data-stu-id="6bbe8-141">The memory data might be more readable if you format it as a list by typing:</span></span>

```
PS> Get-WmiObject -Class Win32_OperatingSystem -Namespace root/cimv2 -ComputerName . | Format-List TotalVirtualMemorySize,TotalVisibleMemorySize,FreePhysicalMemory,FreeVirtualMemory,FreeSpaceInPagingFiles

TotalVirtualMemorySize : 2097024
TotalVisibleMemorySize : 785904
FreePhysicalMemory     : 301876
FreeVirtualMemory      : 2056724
FreeSpaceInPagingFiles : 1556644
```

