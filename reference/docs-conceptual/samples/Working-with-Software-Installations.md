---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Gestione delle installazioni di software
ms.openlocfilehash: f3023d8819d6cdcc9f55befcfedb21e6ff9d282c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "76996116"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="9f2e4-103">Gestione delle installazioni di software</span><span class="sxs-lookup"><span data-stu-id="9f2e4-103">Working with Software Installations</span></span>

<span data-ttu-id="9f2e4-104">Le applicazioni progettate per l'uso di Windows Installer sono accessibili tramite la classe **Win32_Product** di WMI, ma non tutte le applicazioni oggi disponibili prevedono l'uso di Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span>
<span data-ttu-id="9f2e4-105">Le applicazioni che prevedono l'uso di procedure di installazione alternative non vengono in genere gestite da Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-105">Applications that use alternate setup routines are not usually managed by the Windows Installer.</span></span>
<span data-ttu-id="9f2e4-106">Le tecniche specifiche per la gestione di queste applicazioni variano in base al software del programma di installazione e alle decisioni prese dallo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-106">Specific techniques for working with those applications depends on the installer software and decisions made by the application developer.</span></span> <span data-ttu-id="9f2e4-107">Ad esempio, le applicazioni istallate copiando i file in una cartella sul computer non possono in genere essere gestite con le tecniche descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-107">For example, applications installed by copying the files to a folder on the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="9f2e4-108">È possibile gestire tali applicazioni come file e cartelle usando le tecniche descritte in [Gestione di file e cartelle](Working-with-Files-and-Folders.md).</span><span class="sxs-lookup"><span data-stu-id="9f2e4-108">You can manage these applications as files and folders by using the techniques discussed in [Working With Files and Folders](Working-with-Files-and-Folders.md).</span></span>

> [!CAUTION]
> <span data-ttu-id="9f2e4-109">La classe **Win32_Product** non è ottimizzata per le query.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-109">The **Win32_Product** class is not query optimized.</span></span> <span data-ttu-id="9f2e4-110">Le query che usano filtri con caratteri jolly fanno in modo che WMI usi il provider MSI per enumerare tutti i prodotti installati e quindi analizzare l'elenco completo in sequenza per gestire il filtro.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-110">Queries that use wildcard filters cause WMI to use the MSI provider to enumerate all installed products then parse the full list sequentially to handle the filter.</span></span> <span data-ttu-id="9f2e4-111">Verrà anche avviata una verifica coerenza dei pacchetti installati, che verificherà e ripristinerà l'installazione.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-111">This also initiates a consistency check of packages installed, verifying and repairing the install.</span></span> <span data-ttu-id="9f2e4-112">La convalida è un processo lento che potrebbe restituire errori nei registri eventi.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-112">The validation is a slow process and may result in errors in the event logs.</span></span> <span data-ttu-id="9f2e4-113">Per altre informazioni, vedere l' [articolo 974524 della Microsoft Knowledge Base](https://support.microsoft.com/help/974524).</span><span class="sxs-lookup"><span data-stu-id="9f2e4-113">For more information seek [KB article 974524](https://support.microsoft.com/help/974524).</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="9f2e4-114">Visualizzazione di un elenco di applicazioni di Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9f2e4-114">Listing Windows Installer Applications</span></span>

<span data-ttu-id="9f2e4-115">Per elencare le applicazioni installate con Windows Installer in un sistema locale o remoto, usare la semplice query WMI seguente:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-115">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)"
```

```Output
Name             Caption                   Vendor                    Version       IdentifyingNumber
----             -------                   ------                    -------       -----------------
Microsoft .NET … Microsoft .NET Core Runt… Microsoft Corporation     16.84.26919   {BEB59D04-C6DD-4926-AFE…
```

<span data-ttu-id="9f2e4-116">Per visualizzare tutte le proprietà dell'oggetto **Win32_Product**, usare il parametro **Properties** dei cmdlet di formattazione, ad esempio il cmdlet `Format-List`, con il valore `*` (tutti).</span><span class="sxs-lookup"><span data-stu-id="9f2e4-116">To display all the properties of the **Win32_Product** object to the display, use the **Properties** parameter of the formatting cmdlets, such as the `Format-List` cmdlet, with a value of `*` (all).</span></span>

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.5 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.5 (x64)
Version               : 16.84.26919
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.5 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.5 (x64)
IdentifyingNumber     : {BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20181105
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{BEB59D04-C6DD-4926-AFEB-410CBE2EBCE4}v16.84.26919\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\4f97a771.msi
PackageCache          : C:\WINDOWS\Installer\4f97a771.msi
PackageCode           : {9A271A10-039D-49EA-8D24-043D91B9F915}
PackageName           : dotnet-runtime-2.1.5-win-x64.msi
ProductID             :
RegCompany            :
RegOwner              :
Transforms            :
URLInfoAbout          :
URLUpdateInfo         :
WordCount             : 0
PSComputerName        :
CimClass              : root/cimv2:Win32_Product
CimInstanceProperties : {Caption, Description, IdentifyingNumber, Name...}
CimSystemProperties   : Microsoft.Management.Infrastructure.CimSystemProperties
```

<span data-ttu-id="9f2e4-117">Oppure è possibile usare il parametro **Filter** di `Get-CimInstance` per selezionare solo Microsoft .NET 2.0 Runtime.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-117">Or, you could use the `Get-CimInstance` **Filter** parameter to select only Microsoft .NET 2.0 Runtime.</span></span> <span data-ttu-id="9f2e4-118">Il valore del parametro **Filter** usa la sintassi WQL (WMI Query Language), non la sintassi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-118">The value of the **Filter** parameter uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="9f2e4-119">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-119">For example:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property *
```

<span data-ttu-id="9f2e4-120">Per elencare solo le proprietà desiderate, usare il parametro **Property** dei cmdlet di formattazione.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-120">To list only the properties that interest you, use the **Property** parameter of the formatting cmdlets to list the desired properties.</span></span>

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.5 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.5 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\4f97a771.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="9f2e4-121">Visualizzazione di un elenco di tutte le applicazioni disinstallabili</span><span class="sxs-lookup"><span data-stu-id="9f2e4-121">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="9f2e4-122">Poiché la maggior parte delle applicazioni standard registra un programma di disinstallazione con Windows, è possibile gestirle localmente trovandole nel Registro di sistema di Windows.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-122">Because most standard applications register an uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span> <span data-ttu-id="9f2e4-123">Non esiste un modo certo per trovare tutte le applicazioni in un sistema.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-123">There is no guaranteed way to find every application on a system.</span></span> <span data-ttu-id="9f2e4-124">È tuttavia possibile trovare tutti i programmi con gli elenchi visualizzati in **Installazione applicazioni** nella chiave del Registro di sistema seguente:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-124">However, it is possible to find all programs with listings displayed in **Add or Remove Programs** in the following registry key:</span></span>

<span data-ttu-id="9f2e4-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-125">`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.</span></span>

<span data-ttu-id="9f2e4-126">È possibile esaminare questa chiave per trovare applicazioni.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-126">We can examine this key to find applications.</span></span> <span data-ttu-id="9f2e4-127">Per semplificare la visualizzazione della chiave Uninstall, è possibile eseguire il mapping di un'unità di PowerShell a questo percorso del Registro di sistema:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-127">To make it easier to view the Uninstall key, we can map a PowerShell drive to this registry location:</span></span>

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

<span data-ttu-id="9f2e4-128">In questo caso diventa disponibile un'unità "Uninstall:" che è possibile usare per cercare le applicazioni installate in modo rapido e immediato.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-128">We now have a drive named "Uninstall:" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="9f2e4-129">È possibile trovare il numero di applicazioni installate contando il numero delle chiavi del Registro di sistema nell'unità di PowerShell Uninstall:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-129">We can find the number of installed applications by counting the number of registry keys in the Uninstall: PowerShell drive:</span></span>

```powershell
(Get-ChildItem -Path Uninstall:).Count
```

```Output
459
```

<span data-ttu-id="9f2e4-130">È possibile eseguire altre ricerche nell'elenco di applicazioni usando varie tecniche, a partire da `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-130">We can search this list of applications further by using a variety of techniques, beginning with `Get-ChildItem`.</span></span> <span data-ttu-id="9f2e4-131">Per ottenere un elenco di applicazioni e salvarlo nella variabile `$UninstallableApplications`, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-131">To get a list of applications and save them in the `$UninstallableApplications` variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

<span data-ttu-id="9f2e4-132">Per visualizzare i valori delle voci del Registro di sistema nelle chiavi sotto Uninstall, usare il metodo GetValue delle chiavi del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-132">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="9f2e4-133">Il valore del metodo corrisponde al nome della voce del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-133">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="9f2e4-134">Per trovare ad esempio i nomi visualizzati delle applicazioni nella chiave Uninstall, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-134">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="9f2e4-135">Non c'è nessuna garanzia che questi valori siano univoci.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-135">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="9f2e4-136">Nell'esempio seguente due elementi installati vengono visualizzati come "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="9f2e4-136">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```powershell
$UninstallableApplications | Where-Object -FilterScript {
  $_.GetValue("DisplayName") -eq "Microsoft Silverlight"
}
```

```Output
    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name                           Property
----                           --------
{89F4137D-6C26-4A84-BDB8-2E5A4 AuthorizedCDFPrefix :
BB71E00}                       Comments            :
                               Contact             :
                               DisplayVersion      : 5.1.50918.0
                               HelpLink            : https://go.microsoft.com/fwlink/?LinkID=91955
                               HelpTelephone       :
                               InstallDate         : 20190115
                               InstallLocation     : C:\Program Files\Microsoft Silverlight\
                               InstallSource       : c:\ef64c54526db9c34cd477c103e68a254\
                               ModifyPath          : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               NoModify            : 1
                               NoRepair            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 236432
                               UninstallString     : MsiExec.exe /X{89F4137D-6C26-4A84-BDB8-2E5A4BB71E00}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 5
                               VersionMinor        : 1
                               WindowsInstaller    : 1
                               Version             : 84002534
                               Language            : 1033
                               DisplayName         : Microsoft Silverlight
                               sEstimatedSize2     : 79214
```

## <a name="installing-applications"></a><span data-ttu-id="9f2e4-137">Installazione di applicazioni</span><span class="sxs-lookup"><span data-stu-id="9f2e4-137">Installing Applications</span></span>

<span data-ttu-id="9f2e4-138">È possibile usare la classe **Win32_Product** per installare i pacchetti di Windows Installer, in remoto o in locale.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-138">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="9f2e4-139">Per installare un'applicazione, è necessario avviare PowerShell con l'opzione "Esegui come amministratore".</span><span class="sxs-lookup"><span data-stu-id="9f2e4-139">To install an application, you must start PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="9f2e4-140">Per l'installazione in remoto, usare un percorso di rete UNC (Universal Naming Convention) per specificare il percorso del pacchetto MSI, perché il sottosistema WMI non riconosce i percorsi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-140">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand PowerShell paths.</span></span> <span data-ttu-id="9f2e4-141">Ad esempio, per installare il pacchetto NewPackage.msi situato nella condivisione di rete `\\AppServ\dsp` nel computer remoto PC01, digitare il comando seguente al prompt di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-141">For example, to install the NewPackage.msi package located in the network share `\\AppServ\dsp` on the remote computer PC01, type the following command at the PowerShell prompt:</span></span>

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

<span data-ttu-id="9f2e4-142">Per le applicazioni che non usano la tecnologia Windows Installer possono essere disponibili metodi specifici per la distribuzione automatizzata.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-142">Applications that do not use Windows Installer technology may have application-specific methods for automated deployment.</span></span> <span data-ttu-id="9f2e4-143">Vedere la documentazione dell'applicazione o usare il sistema di supporto del vendor dell'applicazione.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-143">Check the documentation for the application or consult the application vendor's support system.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="9f2e4-144">Rimozione di applicazioni</span><span class="sxs-lookup"><span data-stu-id="9f2e4-144">Removing Applications</span></span>

<span data-ttu-id="9f2e4-145">La procedura per rimuovere un pacchetto Windows Installer usando PowerShell è molto simile a quella per installarlo.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-145">Removing a Windows Installer package using PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="9f2e4-146">Ecco un esempio in cui il pacchetto da disinstallare viene selezionato in base al nome. In alcuni casi può risultare più semplice applicare un filtro con **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-146">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

<span data-ttu-id="9f2e4-147">La rimozione di altre applicazioni non è altrettanto semplice, neanche se viene eseguita in locale.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-147">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="9f2e4-148">Per trovare le stringhe di disinstallazione dalla riga di comando per queste applicazioni, estrarre la proprietà **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-148">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span>
<span data-ttu-id="9f2e4-149">Questo metodo funziona per le applicazioni di Windows Installer e per i programmi meno recenti visualizzati nella chiave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-149">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9f2e4-150">Se si preferisce, è possibile filtrare l'output in base al nome visualizzato:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-150">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="9f2e4-151">Tuttavia, queste stringhe potrebbero non essere utilizzabili direttamente al prompt di PowerShell senza apportare alcune modifiche.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-151">However, these strings may not be directly usable from the PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="9f2e4-152">Aggiornamento delle applicazioni di Windows Installer</span><span class="sxs-lookup"><span data-stu-id="9f2e4-152">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="9f2e4-153">Per aggiornare un'applicazione, è necessario conoscerne il nome e il percorso del pacchetto di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="9f2e4-153">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="9f2e4-154">Con queste informazioni, è possibile aggiornare un'applicazione con un singolo comando di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="9f2e4-154">With that information, you can upgrade an application with a single PowerShell command:</span></span>

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
