---
ms.date: 06/03/2019
keywords: powershell,cmdlet
title: Gestione delle installazioni di software
ms.openlocfilehash: 6d2111a332f0e8c1b545186d3d950e936aed1834
ms.sourcegitcommit: 4ec9e10647b752cc62b1eabb897ada3dc03c93eb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/11/2019
ms.locfileid: "66830296"
---
# <a name="working-with-software-installations"></a>Gestione delle installazioni di software

Le applicazioni progettate per l'uso di Windows Installer sono accessibili tramite la classe **Win32_Product** di WMI, ma non tutte le applicazioni oggi disponibili prevedono l'uso di Windows Installer.
Le applicazioni che prevedono l'uso di procedure di installazione alternative non vengono in genere gestite da Windows Installer.
Le tecniche specifiche per la gestione di queste applicazioni variano in base al software del programma di installazione e alle decisioni prese dallo sviluppatore. Ad esempio, le applicazioni istallate copiando i file in una cartella sul computer non possono in genere essere gestite con le tecniche descritte in questo articolo. È possibile gestire tali applicazioni come file e cartelle usando le tecniche descritte in [Gestione di file e cartelle](Working-with-Files-and-Folders.md).

> [!CAUTION]
> La classe **Win32_Product** non è ottimizzata per le query. Le query che usano filtri con caratteri jolly fanno in modo che WMI usi il provider MSI per enumerare tutti i prodotti installati e quindi analizzare l'elenco completo in sequenza per gestire il filtro. Verrà anche avviata una verifica coerenza dei pacchetti installati, che verificherà e ripristinerà l'installazione. La convalida è un processo lento che potrebbe restituire errori nei registri eventi. Per altre informazioni, vedere l' [articolo 974524 della Microsoft Knowledge Base](https://support.microsoft.com/help/974524).

## <a name="listing-windows-installer-applications"></a>Visualizzazione di un elenco di applicazioni di Windows Installer

Per elencare le applicazioni installate con Windows Installer in un sistema locale o remoto, usare la semplice query WMI seguente:

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)"
```

```Output
Name               Caption                     Vendor                 Version      IdentifyingNumber
----               -------                     ------                 -------      -----------------
Microsoft .NET ... Microsoft .NET Core Runt... Microsoft Corporation  16.72.26629  {ACC73072-9AD5-416C-94B...
```

Per visualizzare tutte le proprietà dell'oggetto **Win32_Product**, usare il parametro **Properties** dei cmdlet di formattazione, ad esempio il cmdlet `Format-List`, con il valore `*` (tutti).

```powershell
Get-CimInstance -Class Win32_Product |
  Where-Object Name -eq "Microsoft .NET Core Runtime - 2.1.2 (x64)" |
    Format-List -Property *
```

```Output
Name                  : Microsoft .NET Core Runtime - 2.1.2 (x64)
Version               : 16.72.26629
InstallState          : 5
Caption               : Microsoft .NET Core Runtime - 2.1.2 (x64)
Description           : Microsoft .NET Core Runtime - 2.1.2 (x64)
IdentifyingNumber     : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
SKUNumber             :
Vendor                : Microsoft Corporation
AssignmentType        : 1
HelpLink              :
HelpTelephone         :
InstallDate           : 20180816
InstallDate2          :
InstallLocation       :
InstallSource         : C:\ProgramData\Package Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
Language              : 1033
LocalPackage          : C:\WINDOWS\Installer\414c96e.msi
PackageCache          : C:\WINDOWS\Installer\414c96e.msi
PackageCode           : {D20AC783-1EC5-4A58-9277-F452F5EB9AD9}
PackageName           : dotnet-runtime-2.1.2-win-x64.msi
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

In alternativa, è possibile usare il parametro **Filter** di `Get-CimInstance` per selezionare solo Microsoft .NET Framework 2.0. Il valore del parametro **Filter** usa la sintassi WQL (WMI Query Language), non la sintassi di Windows PowerShell. Ad esempio:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property *
```

Per elencare solo le proprietà desiderate, usare il parametro **Property** dei cmdlet di formattazione.

```powershell
Get-CimInstance -Class Win32_Product  -Filter "Name='Microsoft .NET Core Runtime - 2.1.2 (x64)'" |
  Format-List -Property Name,InstallDate,InstallLocation,PackageCache,Vendor,Version,IdentifyingNumber
```

```Output
Name              : Microsoft .NET Core Runtime - 2.1.2 (x64)
InstallDate       : 20180816
InstallLocation   :
PackageCache      : C:\WINDOWS\Installer\414c96e.msi
Vendor            : Microsoft Corporation
Version           : 16.72.26629
IdentifyingNumber : {ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
```

## <a name="listing-all-uninstallable-applications"></a>Visualizzazione di un elenco di tutte le applicazioni disinstallabili

Poiché la maggior parte delle applicazioni standard registra un programma di disinstallazione con Windows, è possibile gestirle localmente trovandole nel Registro di sistema di Windows. Non esiste un modo certo per trovare tutte le applicazioni in un sistema. È tuttavia possibile trovare tutti i programmi con gli elenchi visualizzati in **Installazione applicazioni**. **Installazione applicazioni** trova queste applicazioni nella chiave del Registro di sistema seguente:

`HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion\Uninstall`.

È possibile esaminare questa chiave per trovare applicazioni. Per semplificare la visualizzazione della chiave Uninstall, è possibile eseguire il mapping di un'unità di PowerShell a questo percorso del Registro di sistema:

```powershell
New-PSDrive -Name Uninstall -PSProvider Registry -Root HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall
```

```Output
Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Uninstall  Registry      HKEY_LOCAL_MACHINE\SOFTWARE\Micr...
```
In questo caso diventa disponibile un'unità "Uninstall:" che è possibile usare per cercare le applicazioni installate in modo rapido e immediato. È possibile trovare il numero di applicazioni installate contando il numero delle chiavi del Registro di sistema nell'unità di PowerShell Uninstall:

```
(Get-ChildItem -Path Uninstall:).Count
459
```

È possibile eseguire altre ricerche nell'elenco di applicazioni usando varie tecniche, a partire da **Get-ChildItem**. Per ottenere un elenco di applicazioni e salvarlo nella variabile **$UninstallableApplications**, usare il comando seguente:

```powershell
$UninstallableApplications = Get-ChildItem -Path Uninstall:
```

Per visualizzare i valori delle voci del Registro di sistema nelle chiavi sotto Uninstall, usare il metodo GetValue delle chiavi del Registro di sistema. Il valore del metodo corrisponde al nome della voce del Registro di sistema.

Per trovare ad esempio i nomi visualizzati delle applicazioni nella chiave Uninstall, usare il comando seguente:

```powershell
$UninstallableApplications | ForEach-Object -Process { $_.GetValue('DisplayName') }
```

Non c'è nessuna garanzia che questi valori siano univoci. Nell'esempio seguente due elementi installati vengono visualizzati come "Windows Media Encoder 9 Series":

```powershell
$UninstallableApplications | Where-Object -FilterScript { $_.GetValue("DisplayName") -eq "Windows Media Encoder 9 Series"}
```

```Output
Name                           Property
----                           --------
{ACC73072-9AD5-416C-94BF-D82DD AuthorizedCDFPrefix :
CEA0F1B}                       Comments            :
                               Contact             :
                               DisplayVersion      : 16.72.26629
                               HelpLink            :
                               HelpTelephone       :
                               InstallDate         : 20180816
                               InstallLocation     :
                               InstallSource       : C:\ProgramData\Package
                               Cache\{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}v16.72.26629\
                               ModifyPath          : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               NoModify            : 1
                               Publisher           : Microsoft Corporation
                               Readme              :
                               Size                :
                               EstimatedSize       : 67156
                               SystemComponent     : 1
                               UninstallString     : MsiExec.exe /X{ACC73072-9AD5-416C-94BF-D82DDCEA0F1B}
                               URLInfoAbout        :
                               URLUpdateInfo       :
                               VersionMajor        : 16
                               VersionMinor        : 72
                               WindowsInstaller    : 1
                               Version             : 273180677
                               Language            : 1033
                               DisplayName         : Microsoft .NET Core Runtime - 2.1.2 (x64)
```

## <a name="installing-applications"></a>Installazione di applicazioni

È possibile usare la classe **Win32_Product** per installare i pacchetti di Windows Installer, in remoto o in locale.

> [!NOTE]
> Per installare un'applicazione, è necessario avviare PowerShell con l'opzione "Esegui come amministratore".

Per l'installazione in remoto, usare un percorso di rete UNC (Universal Naming Convention) per specificare il percorso del pacchetto MSI, perché il sottosistema WMI non riconosce i percorsi di PowerShell. Ad esempio, per installare il pacchetto NewPackage.msi situato nella condivisione di rete `\\AppServ\dsp` nel computer remoto PC01, digitare il comando seguente al prompt di PowerShell:

```powershell
Invoke-CimMethod -ClassName Win32_Product -MethodName Install -Arguments @{PackageLocation='\\AppSrv\dsp\NewPackage.msi'}
```

Per le applicazioni che non usano la tecnologia Windows Installer possono essere disponibili metodi specifici per la distribuzione automatizzata. Vedere la documentazione dell'applicazione o usare il sistema di supporto del vendor dell'applicazione.

## <a name="removing-applications"></a>Rimozione di applicazioni

La procedura per rimuovere un pacchetto Windows Installer usando PowerShell è molto simile a quella per installarlo. Ecco un esempio in cui il pacchetto da disinstallare viene selezionato in base al nome. In alcuni casi può risultare più semplice applicare un filtro con **IdentifyingNumber**:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='ILMerge'" | Invoke-CimMethod -MethodName Uninstall
```

La rimozione di altre applicazioni non è altrettanto semplice, neanche se viene eseguita in locale. Per trovare le stringhe di disinstallazione dalla riga di comando per queste applicazioni, estrarre la proprietà **UninstallString**.
Questo metodo funziona per le applicazioni di Windows Installer e per i programmi meno recenti visualizzati nella chiave Uninstall:

```powershell
Get-ChildItem -Path Uninstall: | ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Se si preferisce, è possibile filtrare l'output in base al nome visualizzato:

```powershell
Get-ChildItem -Path Uninstall: |
    Where-Object -FilterScript { $_.GetValue('DisplayName') -like 'Win*'} |
        ForEach-Object -Process { $_.GetValue('UninstallString') }
```

Tuttavia, queste stringhe potrebbero non essere utilizzabili direttamente al prompt di PowerShell senza apportare alcune modifiche.

## <a name="upgrading-windows-installer-applications"></a>Aggiornamento delle applicazioni di Windows Installer

Per aggiornare un'applicazione, è necessario conoscerne il nome e il percorso del pacchetto di aggiornamento. Con queste informazioni, è possibile aggiornare un'applicazione con un singolo comando di PowerShell:

```powershell
Get-CimInstance -Class Win32_Product -Filter "Name='OldAppName'" |
  Invoke-CimMethod -MethodName Upgrade -Arguments @{PackageLocation='\\AppSrv\dsp\OldAppUpgrade.msi'}
```
