---
ms.date: 09/26/2017
contributor: keithb
keywords: raccolta,powershell,cmdlet,psget
title: Versioni di modulo non definitive
ms.openlocfilehash: eced067dd21082de0db653daf3b838217154f1dd
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328142"
---
# <a name="prerelease-module-versions"></a>Versioni di modulo non definitive

A partire dalla versione 1.6.0, PowerShellGet e PowerShell Gallery consentono di contrassegnare le versioni successive alla versione 1.0.0 come versioni non definitive. In precedenza, i pacchetti non definitivi potevano avere solo una versione che iniziava con 0. L'obiettivo di queste funzionalità è quello di offrire un maggior supporto per la convenzione di controllo delle versioni [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) senza interrompere la compatibilità con le versioni precedenti con PowerShell versioni 3 e successive o le versioni esistenti di PowerShellGet. Questo argomento illustra le funzionalità specifiche dei moduli. Le funzionalità equivalenti per gli script sono descritte nell'argomento [Versioni non definitive degli script](script-prerelease-support.md). Usando queste funzionalità, i server di pubblicazione possono identificare un modulo o uno script come versione 2.5.0-alpha e rilasciare in seguito una versione pronta per la produzione 2.5.0 che sostituisce la versione non definitiva.

In generale, le funzionalità di modulo non definitivo includono:

- L'aggiunta di una stringa Prerelease alla sezione PSData del manifesto del modulo identifica il modulo come versione non definitiva. Quando il modulo viene pubblicato in PowerShell Gallery, i dati vengono estratti dal manifesto e usati per identificare i pacchetti in versione non definitiva.
- L'acquisizione di pacchetti in versione non definitiva richiede l'aggiunta del flag `-AllowPrerelease` ai comandi di PowerShellGet `Find-Module`, `Install-Module`, `Update-Module` e `Save-Module`. Se il flag non viene specificato, i pacchetti in versione non definitiva non vengono visualizzati.
- Le versioni di modulo visualizzate da `Find-Module`, `Get-InstalledModule` e in PowerShell Gallery vengono visualizzate come stringa singola con la stringa Prerelease aggiunta alla fine, come nella versione 2.5.0-alpha.

Di seguito sono descritti i dettagli delle funzionalità.

Queste modifiche non influiscono sul supporto della versione di modulo in PowerShell e sono compatibili con PowerShell 3.0, 4.0 e 5.

## <a name="identifying-a-module-version-as-a-prerelease"></a>Identificazione di una versione di modulo come versione non definitiva

Il supporto di PowerShellGet per le versioni non definitive richiede l'uso di due campi all'interno del manifesto del modulo:

- ModuleVersion incluso nel manifesto del modulo deve essere una versione di 3 parti se viene usata una versione non definitiva e deve essere conforme al controllo delle versioni di PowerShell esistente. Il formato della versione è A.B.C, dove A, B e C sono tutti numeri interi.
- La stringa Prerelease è specificata nel manifesto del modulo, nella sezione PSData di PrivateData.

Di seguito sono descritti nel dettaglio i requisiti della stringa Prerelease.

Una sezione di esempio del manifesto di un modulo che definisce il modulo come versione non definitiva sarà simile alla seguente:

```powershell
@{
    ModuleVersion = '2.5.0'
    #---
    PrivateData = @{
        PSData = @{
            Prerelease = 'alpha'
        }
    }
}
```

I requisiti della stringa Prerelease sono i seguenti:

- È possibile specificare una stringa Prerelease solo quando ModuleVersion è 3 segmenti per Major.Minor.Build. Ciò è conforme alla convenzione SemVer v1.0.0.
- Un segno meno è il delimitatore tra il numero di build e la stringa Prerelease. È possibile includere un segno meno nella stringa Prerelease solo come primo carattere.
- La stringa Prerelease può contenere solo caratteri alfanumerici ASCII [0-9A-Za-z-]. È consigliabile fare in modo che la stringa Prerelease inizi con un carattere alfabetico per rendere più semplice l'identificazione di una versione non definitiva durante la ricerca in un elenco di pacchetti.
- Attualmente sono supportate solo stringhe Prerelease SemVer v1.0.0. La stringa Prerelease **non deve** contenere punti o + [.+], consentiti in SemVer 2.0.
- Esempi di stringhe Prerelease supportate includono: -alpha, -alpha1, -BETA, -update20171020

### <a name="prerelease-versioning-impact-on-sort-order-and-installation-folders"></a>Impatto del controllo delle versioni non definitive sull'ordinamento e sulle cartelle di installazione

Quando viene usata una versione non definitiva l'ordinamento viene modificato, un aspetto importante durante la pubblicazione in PowerShell Gallery e l'installazione di moduli con i comandi di PowerShellGet. Se la stringa Prerelease è specificata per due moduli, l'ordinamento è basato sulla parte di stringa che segue il segno meno. Di conseguenza, la versione 2.5.0-alpha è precedente alla versione 2.5.0-beta che è a sua volta precedente alla versione 2.5.0-gamma. Se due moduli hanno lo stesso ModuleVersion e uno solo include una stringa Prerelease, il modulo senza la stringa Prerelease viene considerato la versione pronta per la produzione e viene ordinato come versione successiva alla versione non definitiva (che include la stringa Prerelease). Ad esempio, quando viene eseguito il confronto delle versioni 2.5.0 e 2.5.0-beta, la versione 2.5.0 viene considerata la più recente.

Durante la pubblicazione in PowerShell Gallery, per impostazione predefinita la versione del modulo in fase di pubblicazione deve essere successiva a qualsiasi versione pubblicata precedentemente presente in PowerShell Gallery.

## <a name="finding-and-acquiring-prerelease-packages-using-powershellget-commands"></a>Ricerca e acquisizione di pacchetti in versione non definitiva mediante i comandi di PowerShellGet

L'uso di pacchetti in versione non definitiva con i comandi di PowerShellGet Find-Module, Install-Module, Update-Module e Save-Module richiede l'aggiunta del flag -AllowPrerelease. Se il flag -AllowPrerelease è specificato, i pacchetti in versione non definitiva verranno inclusi, se presenti. Se il flag -AllowPrerelease non è specificato, i pacchetti in versione non definitiva non verranno visualizzati.

Le uniche eccezioni nei comandi di modulo di PowerShellGet sono rappresentate da Get-InstalledModule e da alcuni casi di utilizzo di Uninstall-Module.

- Get-InstalledModule visualizza sempre automaticamente le informazioni di versione non definitiva nella stringa di versione per i moduli.
- Uninstall-Module disinstalla per impostazione predefinita la versione più recente di un modulo, se non è specificata __alcuna versione__. Questo comportamento non è stato modificato. Tuttavia, se una versione non definitiva viene specificata usando -RequiredVersion, è necessario specificare -AllowPrerelease.

## <a name="examples"></a>Esempi

Si supponga che PowerShell Gallery includa le versioni del modulo TestPackage 1.8.0 e 1.9.0-alpha. Se non si specifica `-AllowPrerelease`, verrà restituita solo la versione 1.8.0.

```powershell
find-module TestPackage
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.8.0          TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

```powershell
find-module TestPackage -AllowPrerelease
```

```output
Version        Name           Repository  Description
-------        ----           ----------  -----------
1.9.0-alpha    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
```

Per installare una versione non definitiva, specificare sempre -AllowPrerelease. Non è sufficiente specificare una stringa di versione non definitiva.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha
```

```output
PackageManagement\Find-Package : No match was found for the specified search criteria and module name 'TestPackage'.
Try Get-PSRepository to see all available registered module repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exception
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage
```

Il comando precedente non riesce perché non viene specificato -AllowPrerelease. L'aggiunta di `-AllowPrerelease` consentirà di completare correttamente l'operazione.

```powershell
Install-module TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
Get-InstalledModule TestPackage
```

```output
Version         Name          Repository  Description
-------         ----          ----------  -----------
1.9.0-alpha     TestPackage   PSGallery   Package used to validate changes to the PowerShe...
```

L'installazione side-by-side di versioni di un modulo che si differenziano solo per la versione non definitiva specificata non è supportata. Quando si installa un modulo con PowerShellGet, versioni diverse dello stesso modulo vengono installate side-by-side creando un nome di cartella con ModuleVersion. Per il nome di cartella viene usato ModuleVersion, senza la stringa Prerelease. Se un utente installa MyModule versione 2.5.0-alpha, il modulo viene installato nella cartella `MyModule\2.5.0`. Se l'utente installa quindi la versione 2.5.0-beta, la versione 2.5.0-beta **sovrascriverà** il contenuto della cartella `MyModule\2.5.0`. Uno dei vantaggi di questo approccio è rappresentato dal fatto che non è necessario disinstallare la versione non definitiva dopo aver installato la versione pronta per la produzione. L'esempio seguente mostra cosa accade:

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-alpha     TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> find-module TestPackage -AllowPrerelease

Version        Name            Repository  Description
-------        ----            ----------  -----------
1.9.0-beta     TestPackage     PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Update-Module TestPackage -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

```

Uninstall-Module rimuove la versione più recente di un modulo quando non viene specificato -RequiredVersion.
Se -RequiredVersion è specificato e si tratta di una versione non definitiva, è necessario aggiungere -AllowPrerelease al comando.

``` powershell
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name           Repository  Description
-------         ----           ----------  -----------
2.0.0-alpha1    TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.9.0-beta      TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.8.0           TestPackage    PSGallery   Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage    PSGallery   Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta

Uninstall-Module : The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Module], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninstall-Module

C:\windows\system32> Uninstall-Module TestPackage -RequiredVersion 1.9.0-beta -AllowPrerelease
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
2.0.0-alpha1    TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...

C:\windows\system32> Uninstall-Module TestPackage
C:\windows\system32> Get-InstalledModule TestPackage -AllVersions

Version         Name          Repository   Description
-------         ----          ----------   -----------
1.8.0           TestPackage   PSGallery    Package used to validate changes to the PowerShe...
1.1.3.2         TestPackage   PSGallery    Package used to validate changes to the PowerShe...
```

## <a name="more-details"></a>Altre informazioni

- [Versioni non definitive degli script](script-prerelease-support.md)
- [Find-Module](/powershell/module/powershellget/find-module)
- [Install-Module](/powershell/module/powershellget/install-module)
- [Save-Module](/powershell/module/powershellget/save-module)
- [Update-Module](/powershell/module/powershellget/Update-Module)
- [Get-InstalledModule](/powershell/module/powershellget/get-installedmodule)
- [UnInstall-Module](/powershell/module/powershellget/uninstall-module)
