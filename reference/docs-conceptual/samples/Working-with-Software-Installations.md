---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle installazioni di software
ms.assetid: 51a12fe9-95f6-4ffc-81a5-4fa72a5bada9
ms.openlocfilehash: 9369e3c5ac670895cd4fbd3ebc895c50efd02051
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086273"
---
# <a name="working-with-software-installations"></a><span data-ttu-id="24258-103">Gestione delle installazioni di software</span><span class="sxs-lookup"><span data-stu-id="24258-103">Working with Software Installations</span></span>

<span data-ttu-id="24258-104">Le applicazioni progettate per l'uso di Windows Installer sono accessibili tramite la classe **Win32_Product** di WMI, ma non tutte le applicazioni oggi disponibili prevedono l'uso di Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="24258-104">Applications that are designed to use Windows Installer can be accessed through WMI's **Win32_Product** class, but not all applications in use today use the Windows Installer.</span></span> <span data-ttu-id="24258-105">Poiché Windows Installer offre la gamma più ampia di tecniche standard per la gestione di applicazioni installabili, questo articolo è incentrato principalmente su tali applicazioni.</span><span class="sxs-lookup"><span data-stu-id="24258-105">Because the Windows Installer provides the widest range of standard techniques for working with installable applications, we will focus primarily on those applications.</span></span> <span data-ttu-id="24258-106">Le applicazioni che prevedono l'uso di procedure di installazione alternative non vengono in genere gestite da Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="24258-106">Applications that use alternate setup routines will generally not be managed by the Windows Installer.</span></span> <span data-ttu-id="24258-107">Le tecniche specifiche per la gestione di queste applicazioni variano in base al software del programma di installazione e alle decisioni prese dallo sviluppatore.</span><span class="sxs-lookup"><span data-stu-id="24258-107">Specific techniques for working with those applications will depend on the installer software and decisions made by the application developer.</span></span>

> [!NOTE]
> <span data-ttu-id="24258-108">Le applicazioni istallate tramite la copia dei relativi file nel computer non possono in genere essere gestite con le tecniche descritte in questo articolo.</span><span class="sxs-lookup"><span data-stu-id="24258-108">Applications that are installed by copying the application files to the computer usually cannot be managed by using techniques discussed here.</span></span> <span data-ttu-id="24258-109">È possibile gestire tali applicazioni come file e cartelle usando le tecniche descritte nella sezione "Gestione di file e cartelle".</span><span class="sxs-lookup"><span data-stu-id="24258-109">You can manage these applications as files and folders by using the techniques discussed in the "Working With Files and Folders" section.</span></span>

## <a name="listing-windows-installer-applications"></a><span data-ttu-id="24258-110">Visualizzazione di un elenco di applicazioni di Windows Installer</span><span class="sxs-lookup"><span data-stu-id="24258-110">Listing Windows Installer Applications</span></span>

<span data-ttu-id="24258-111">Per elencare le applicazioni installate con Windows Installer in un sistema locale o remoto, usare la semplice query WMI seguente:</span><span class="sxs-lookup"><span data-stu-id="24258-111">To list the applications installed with the Windows Installer on a local or remote system, use the following simple WMI query:</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName .

IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
Name              : Microsoft .NET Framework 2.0
Vendor            : Microsoft Corporation
Version           : 2.0.50727
Caption           : Microsoft .NET Framework 2.0
```

<span data-ttu-id="24258-112">Per visualizzare tutte le proprietà dell'oggetto Win32_Product, usare il parametro Properties dei cmdlet di formattazione, ad esempio Format-List, con il valore \* (tutti).</span><span class="sxs-lookup"><span data-stu-id="24258-112">To display all of the properties of the Win32_Product object to the display, use the Properties parameter of the formatting cmdlets, such as the Format-List cmdlet, with a value of \* (all).</span></span>

```
PS> Get-WmiObject -Class Win32_Product -ComputerName . | Where-Object -FilterScript {$_.Name -eq "Microsoft .NET Framework 2.0"} | Format-List -Property *

Name              : Microsoft .NET Framework 2.0
Version           : 2.0.50727
InstallState      : 5
Caption           : Microsoft .NET Framework 2.0
Description       : Microsoft .NET Framework 2.0
IdentifyingNumber : {7131646D-CD3C-40F4-97B9-CD9E4E6262EF}
InstallDate       : 20060506
InstallDate2      : 20060506000000.000000-000
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\619ab2.msi
SKUNumber         :
Vendor            : Microsoft Corporation
```

<span data-ttu-id="24258-113">In alternativa, è possibile usare il parametro **Get-WmiObject Filter** per selezionare solo Microsoft .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="24258-113">Or, you could use the **Get-WmiObject Filter** parameter to select only Microsoft .NET Framework 2.0.</span></span> <span data-ttu-id="24258-114">Poiché il filtro usato in questo comando è di WMI, viene usata la sintassi WQL (WMI Query Language) e non quella di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24258-114">Because the filter used in this command is a WMI filter, it uses WMI Query Language (WQL) syntax, not Windows PowerShell syntax.</span></span> <span data-ttu-id="24258-115">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="24258-115">Instead,:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='Microsoft .NET Framework 2.0'"| Format-List -Property *
```

<span data-ttu-id="24258-116">Si noti che le query WQL usano spesso caratteri come spazi o segni di uguale che hanno un significato speciale in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24258-116">Note that WQL queries frequently use characters, such as spaces or equal signs, that have a special meaning in Windows PowerShell.</span></span> <span data-ttu-id="24258-117">Per questo motivo, è consigliabile racchiudere sempre il valore del parametro Filter tra virgolette.</span><span class="sxs-lookup"><span data-stu-id="24258-117">For this reason, it is prudent to always enclose the value of the Filter parameter in quotation marks.</span></span> <span data-ttu-id="24258-118">È anche possibile usare il carattere di escape di Windows PowerShell, un apice inverso (\`), anche se potrebbe influire negativamente sulla leggibilità.</span><span class="sxs-lookup"><span data-stu-id="24258-118">You can also use the Windows PowerShell escape character, a backtick (\`), although it may not improve readability.</span></span> <span data-ttu-id="24258-119">Il comando seguente è equivalente a quello precedente e restituisce gli stessi risultati, ma usa l'apice inverso come escape per i caratteri speciali, invece di racchiudere tra virgolette l'intera stringa di filtro.</span><span class="sxs-lookup"><span data-stu-id="24258-119">The following command is equivalent to the previous command and returns the same results, but uses the backtick to escape special characters, instead of quoting the entire filter string.</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName . -Filter Name`=`'Microsoft` .NET` Framework` 2.0`' | Format-List -Property *
```

<span data-ttu-id="24258-120">Per elencare solo le proprietà desiderate, usare il parametro Property dei cmdlet di formattazione.</span><span class="sxs-lookup"><span data-stu-id="24258-120">To list only the properties that interest you, use the Property parameter of the formatting cmdlets to list the desired properties.</span></span>

```
Get-WmiObject -Class Win32_Product -ComputerName . | Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
...
Name              : HighMAT Extension to Microsoft Windows XP CD Writing Wizard
InstallDate       : 20051022
InstallLocation   : C:\Program Files\HighMAT CD Writing Wizard\
PackageCache      : C:\WINDOWS\Installer\113b54.msi
Vendor            : Microsoft Corporation
Version           : 1.1.1905.1
IdentifyingNumber : {FCE65C4E-B0E8-4FBD-AD16-EDCBE6CD591F}
...
```

<span data-ttu-id="24258-121">Infine, per trovare solo i nomi delle applicazioni installate, una semplice istruzione **Format-Wide** semplifica l'output:</span><span class="sxs-lookup"><span data-stu-id="24258-121">Finally, to find only the names of installed applications, a simple **Format-Wide** statement simplifies the output:</span></span>

```powershell
Get-WmiObject -Class Win32_Product -ComputerName .  | Format-Wide -Column 1
```

<span data-ttu-id="24258-122">A questo punto sono stati illustrati i vari modi in cui è possibile esaminare le applicazioni che usano Windows Installer per l'installazione, mentre non sono state considerate le altre applicazioni.</span><span class="sxs-lookup"><span data-stu-id="24258-122">Although we now have several ways to look at applications that used the Windows Installer for installation, we have not considered other applications.</span></span> <span data-ttu-id="24258-123">Poiché la maggior parte delle applicazioni standard registra il proprio programma di disinstallazione con Windows, è possibile gestirle localmente individuandole nel Registro di sistema di Windows.</span><span class="sxs-lookup"><span data-stu-id="24258-123">Because most standard applications register their uninstaller with Windows, we can work with those locally by finding them in the Windows registry.</span></span>

## <a name="listing-all-uninstallable-applications"></a><span data-ttu-id="24258-124">Visualizzazione di un elenco di tutte le applicazioni disinstallabili</span><span class="sxs-lookup"><span data-stu-id="24258-124">Listing All Uninstallable Applications</span></span>

<span data-ttu-id="24258-125">Anche se non esiste nessun modo garantito per trovare tutte le applicazioni in un sistema, è possibile trovare tutti i programmi con gli elenchi visualizzati nella finestra di dialogo Installazione applicazioni.</span><span class="sxs-lookup"><span data-stu-id="24258-125">Although there is no guaranteed way to find every application on a system, it is possible to find all programs with listings displayed in the Add or Remove Programs dialog box.</span></span> <span data-ttu-id="24258-126">Installazione applicazioni trova queste applicazioni nella seguente chiave del Registro di sistema:</span><span class="sxs-lookup"><span data-stu-id="24258-126">Add or Remove Programs finds these applications in the following registry key:</span></span>

<span data-ttu-id="24258-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span><span class="sxs-lookup"><span data-stu-id="24258-127">**HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Uninstall**.</span></span>

<span data-ttu-id="24258-128">È anche possibile esaminare questa chiave per trovare applicazioni.</span><span class="sxs-lookup"><span data-stu-id="24258-128">We can also examine this key to find applications.</span></span> <span data-ttu-id="24258-129">Per semplificare la visualizzazione della chiave Uninstall, è possibile mappare un'unità di Windows PowerShell a questo percorso del Registro di sistema:</span><span class="sxs-lookup"><span data-stu-id="24258-129">To make it easier to view the Uninstall key, we can map a Windows PowerShell drive to this registry location:</span></span>

```
PS> New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```

> [!NOTE]
> <span data-ttu-id="24258-130">L'unità **HKLM:** viene mappata alla radice di **HKEY_LOCAL_MACHINE**, quindi viene usata questa unità nel percorso della chiave Uninstall.</span><span class="sxs-lookup"><span data-stu-id="24258-130">The **HKLM:** drive is mapped to the root of **HKEY_LOCAL_MACHINE**, so we used that drive in the path to the Uninstall key.</span></span> <span data-ttu-id="24258-131">Invece di usare **HKLM**, è possibile specificare il percorso del Registro di sistema usando **HKLM** o **HKEY_LOCAL_MACHINE**.</span><span class="sxs-lookup"><span data-stu-id="24258-131">Instead of **HKLM:** we could have specified the registry path by using either **HKLM** or **HKEY_LOCAL_MACHINE**.</span></span> <span data-ttu-id="24258-132">L'uso di un'unità esistente del Registro di sistema offre il vantaggio di poter completare i nomi delle chiavi tramite TAB, invece di digitarli.</span><span class="sxs-lookup"><span data-stu-id="24258-132">The advantage of using an existing registry drive is that we can use tab-completion to fill in the keys names, so we do not need to type them.</span></span>

<span data-ttu-id="24258-133">In questo caso diventa disponibile un'unità "Uninstall" che è possibile usare per cercare le applicazioni installate in modo rapido e immediato.</span><span class="sxs-lookup"><span data-stu-id="24258-133">We now have a drive named "Uninstall" that can be used to quickly and conveniently look for application installations.</span></span> <span data-ttu-id="24258-134">È possibile trovare il numero di applicazioni installate contando il numero delle chiavi del Registro di sistema nell'unità di Windows PowerShell Uninstall:</span><span class="sxs-lookup"><span data-stu-id="24258-134">We can find the number of installed applications by counting the number of registry keys in the Uninstall: Windows PowerShell drive:</span></span>

```
PS> (Get-ChildItem -Path Uninstall:).Count
459
```

<span data-ttu-id="24258-135">È possibile eseguire altre ricerche nell'elenco di applicazioni usando varie tecniche, a partire da **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="24258-135">We can search this list of applications further by using a variety of techniques, beginning with **Get-ChildItem**.</span></span> <span data-ttu-id="24258-136">Per ottenere un elenco di applicazioni e salvarlo nella variabile **$UninstallableApplications**, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="24258-136">To get a list of applications and save them in the **$UninstallableApplications** variable, use the following command:</span></span>

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

> [!NOTE]
> <span data-ttu-id="24258-137">In questo caso per chiarezza viene usato un nome di variabile lungo.</span><span class="sxs-lookup"><span data-stu-id="24258-137">We are using a lengthy variable name here for clarity.</span></span> <span data-ttu-id="24258-138">Nell'uso effettivo, non c'è alcun motivo per usare nomi lunghi.</span><span class="sxs-lookup"><span data-stu-id="24258-138">In actual use, there is no reason to use long names.</span></span> <span data-ttu-id="24258-139">Sebbene sia possibile usare il completamento tramite tasto TAB per i nomi delle variabili, è anche possibile usare nomi di 1 o 2 caratteri per operazioni rapide.</span><span class="sxs-lookup"><span data-stu-id="24258-139">Although you can use tab-completion for variable names, you can also use 1-2 character names for speed.</span></span> <span data-ttu-id="24258-140">I nomi descrittivi più lunghi risultano più utili quando si sviluppa codice per il riutilizzo.</span><span class="sxs-lookup"><span data-stu-id="24258-140">Longer, descriptive names are most useful when you are developing code for reuse.</span></span>

<span data-ttu-id="24258-141">Per visualizzare i valori delle voci del Registro di sistema nelle chiavi sotto Uninstall, usare il metodo GetValue delle chiavi del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="24258-141">To display the values of the registry entries in the registry keys under Uninstall, use the GetValue method of the registry keys.</span></span> <span data-ttu-id="24258-142">Il valore del metodo corrisponde al nome della voce del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="24258-142">The value of the method is the name of the registry entry.</span></span>

<span data-ttu-id="24258-143">Per trovare ad esempio i nomi visualizzati delle applicazioni nella chiave Uninstall, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="24258-143">For example, to find the display names of applications in the Uninstall key, use the following command:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

<span data-ttu-id="24258-144">Non c'è nessuna garanzia che questi valori siano univoci.</span><span class="sxs-lookup"><span data-stu-id="24258-144">There is no guarantee that these values are unique.</span></span> <span data-ttu-id="24258-145">Nell'esempio seguente due elementi installati vengono visualizzati come "Windows Media Encoder 9 Series":</span><span class="sxs-lookup"><span data-stu-id="24258-145">In the following example, two installed items appear as "Windows Media Encoder 9 Series":</span></span>

```
PS> Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion\Uninstall

SKC  VC Name                           Property
---  -- ----                           --------
  0   3 Windows Media Encoder 9        {DisplayName, DisplayIcon, UninstallS...
  0  24 {E38C00D0-A68B-4318-A8A6-F7... {AuthorizedCDFPrefix, Comments, Conta...
```

## <a name="installing-applications"></a><span data-ttu-id="24258-146">Installazione di applicazioni</span><span class="sxs-lookup"><span data-stu-id="24258-146">Installing Applications</span></span>

<span data-ttu-id="24258-147">È possibile usare la classe **Win32_Product** per installare i pacchetti di Windows Installer, in remoto o in locale.</span><span class="sxs-lookup"><span data-stu-id="24258-147">You can use the **Win32_Product** class to install Windows Installer packages, remotely or locally.</span></span>

> [!NOTE]
> <span data-ttu-id="24258-148">In Windows Vista, Windows Server 2008 e nelle versioni più recenti di Windows, per installare un'applicazione è necessario avviare Windows PowerShell con l'opzione "Esegui come amministratore".</span><span class="sxs-lookup"><span data-stu-id="24258-148">On Windows Vista, Windows Server 2008, and later versions of Windows, to install an application, you must start Windows PowerShell with the "Run as administrator" option.</span></span>

<span data-ttu-id="24258-149">Per l'installazione in remoto, usare un percorso di rete UNC (Universal Naming Convention) per specificare il percorso del pacchetto MSI, perché il sottosistema WMI non riconosce i percorsi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24258-149">When installing remotely, use a Universal Naming Convention (UNC) network path to specify the path to the .msi package, because the WMI subsystem does not understand Windows PowerShell paths.</span></span> <span data-ttu-id="24258-150">Ad esempio, per installare il pacchetto NewPackage.msi situato nella condivisione di rete \\\\AppServ\\dsp nel computer remoto PC01, digitare il comando seguente al prompt di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="24258-150">For example, to install the NewPackage.msi package located in the network share \\\\AppServ\\dsp on the remote computer PC01, type the following command at the Windows PowerShell prompt:</span></span>

```powershell
(Get-WMIObject -ComputerName PC01 -List | Where-Object -FilterScript {$_.Name -eq 'Win32_Product'}).Install(\\AppSrv\dsp\NewPackage.msi)
```

<span data-ttu-id="24258-151">Per le applicazioni che non usano la tecnologia Windows Installer possono essere disponibili metodi specifici per la distribuzione automatizzata.</span><span class="sxs-lookup"><span data-stu-id="24258-151">Applications that do not use Windows Installer technology may have application-specific methods available for automated deployment.</span></span> <span data-ttu-id="24258-152">Per determinare se esiste un metodo per l'automazione della distribuzione, consultare la documentazione dell'applicazione oppure il sistema di supporto del fornitore.</span><span class="sxs-lookup"><span data-stu-id="24258-152">To determine whether there is a method for deployment automation, check the documentation for the application or consult the application vendor's support system.</span></span> <span data-ttu-id="24258-153">In alcuni casi, anche se il fornitore non progetta specificamente l'applicazione per l'automazione dell'installazione, il produttore del software del programma di installazione potrebbe avere alcune tecniche per l'automazione.</span><span class="sxs-lookup"><span data-stu-id="24258-153">In some cases, even if the application vendor did not specifically design the application for installation automation, the installer software manufacturer may have some techniques for automation.</span></span>

## <a name="removing-applications"></a><span data-ttu-id="24258-154">Rimozione di applicazioni</span><span class="sxs-lookup"><span data-stu-id="24258-154">Removing Applications</span></span>

<span data-ttu-id="24258-155">La procedura per rimuovere un pacchetto Windows Installer tramite Windows PowerShell è molto simile a quella per installarlo.</span><span class="sxs-lookup"><span data-stu-id="24258-155">Removing a Windows Installer package by using Windows PowerShell works in approximately the same way as installing a package.</span></span> <span data-ttu-id="24258-156">Ecco un esempio in cui il pacchetto da disinstallare viene selezionato in base al nome. In alcuni casi può risultare più semplice applicare un filtro con **IdentifyingNumber**:</span><span class="sxs-lookup"><span data-stu-id="24258-156">Here is an example that selects the package to uninstall based on its name; in some cases it may be easier to filter with the **IdentifyingNumber**:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -Filter "Name='ILMerge'" -ComputerName . ).Uninstall()
```

<span data-ttu-id="24258-157">La rimozione di altre applicazioni non è altrettanto semplice, neanche se viene eseguita in locale.</span><span class="sxs-lookup"><span data-stu-id="24258-157">Removing other applications is not quite so simple, even when done locally.</span></span> <span data-ttu-id="24258-158">Per trovare le stringhe di disinstallazione dalla riga di comando per queste applicazioni, estrarre la proprietà **UninstallString**.</span><span class="sxs-lookup"><span data-stu-id="24258-158">We can find the command line uninstallation strings for these applications by extracting the **UninstallString** property.</span></span> <span data-ttu-id="24258-159">Questo metodo funziona per le applicazioni di Windows Installer e per i programmi meno recenti visualizzati nella chiave Uninstall:</span><span class="sxs-lookup"><span data-stu-id="24258-159">This method works for Windows Installer applications and for older programs appearing under the Uninstall key:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="24258-160">Se si preferisce, è possibile filtrare l'output in base al nome visualizzato:</span><span class="sxs-lookup"><span data-stu-id="24258-160">You can filter the output by the display name, if you like:</span></span>

```powershell
Get-ChildItem -Path Uninstall: | Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

<span data-ttu-id="24258-161">Tuttavia, queste stringhe potrebbero non essere utilizzabili direttamente al prompt di Windows PowerShell senza apportare alcune modifiche.</span><span class="sxs-lookup"><span data-stu-id="24258-161">However, these strings may not be directly usable from the Windows PowerShell prompt without some modification.</span></span>

## <a name="upgrading-windows-installer-applications"></a><span data-ttu-id="24258-162">Aggiornamento delle applicazioni di Windows Installer</span><span class="sxs-lookup"><span data-stu-id="24258-162">Upgrading Windows Installer Applications</span></span>

<span data-ttu-id="24258-163">Per aggiornare un'applicazione, è necessario conoscerne il nome e il percorso del pacchetto di aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="24258-163">To upgrade an application, you need to know the name of the application and the path to the application upgrade package.</span></span> <span data-ttu-id="24258-164">Con queste informazioni, è possibile aggiornare un'applicazione con un singolo comando di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="24258-164">With that information, you can upgrade an application with a single Windows PowerShell command:</span></span>

```powershell
(Get-WmiObject -Class Win32_Product -ComputerName . -Filter "Name='OldAppName'").Upgrade(\\AppSrv\dsp\OldAppUpgrade.msi)
```