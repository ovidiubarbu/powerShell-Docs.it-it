---
ms.date: 10/17/2017
contributor: keithb
keywords: raccolta,powershell,cmdlet,psget
title: Versioni non definitive degli script
ms.openlocfilehash: 7d4cec9d2b4ee5ad0b19ad5d9c68bb68747abd57
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093849"
---
# <a name="prerelease-versions-of-scripts"></a>Versioni non definitive degli script

A partire dalla versione 1.6.0, PowerShellGet e PowerShell Gallery consentono di contrassegnare le versioni successive alla versione 1.0.0 come versioni non definitive. In precedenza, gli elementi non definitivi potevano avere solo una versione che iniziasse con 0. L'obiettivo di queste funzionalità è quello di offrire un maggior supporto per la convenzione di controllo delle versioni [SemVer v1.0.0](http://semver.org/spec/v1.0.0.html) senza interrompere la compatibilità con le versioni precedenti con PowerShell versioni 3 e successive o le versioni esistenti di PowerShellGet. Questo argomento illustra le funzionalità specifiche degli script. Le funzionalità equivalenti per i moduli sono descritte nell'argomento [Versioni di modulo non definitive](module-prerelease-support.md). Usando queste funzionalità, i server di pubblicazione possono identificare uno script come versione 2.5.0-alpha e rilasciare in seguito una versione pronta per la produzione 2.5.0 che sostituisce la versione non definitiva.

In generale, le funzionalità di script non definitivo includono:

- Aggiunta di un suffisso PrereleaseString alla stringa di versione nel manifesto dello script. Quando gli script vengono pubblicati in PowerShell Gallery, i dati vengono estratti dal manifesto e usati per identificare gli elementi di versione non definitiva.
- L'acquisizione degli elementi di versione non definitiva richiede l'aggiunta del flag -AllowPrerelease ai comandi di PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script. Se il flag non viene specificato, gli elementi di versione non definitiva non vengono visualizzati.
- Le versioni di script visualizzate da Find-Script, Get-InstalledScript e in PowerShell Gallery vengono visualizzate con PrereleaseString, come in 2.5.0-alpha.

Di seguito sono descritti i dettagli delle funzionalità.

## <a name="identifying-a-script-version-as-a-prerelease"></a>Identificazione di una versione di script come versione non definitiva

Il supporto di PowerShellGet per le versioni non definitive è più semplice per gli script rispetto ai moduli. Poiché il controllo delle versioni degli script è supportato solo da PowerShellGet, non si verificano problemi di compatibilità causati dall'aggiunta della stringa di versione non definitiva. Per identificare uno script in PowerShell Gallery come versione non definitiva, aggiungere un suffisso di versione non definitiva a una stringa di versione formattata correttamente nei metadati dello script.

Una sezione di esempio del manifesto di uno script con una versione non definitiva apparirà come segue:

```powershell
<#PSScriptInfo

.VERSION 3.2.1-alpha12

.GUID

...

#>
```

Per usare un suffisso di versione non definitiva, la stringa di versione deve soddisfare i requisiti seguenti:

- È possibile specificare un suffisso di versione non definitiva solo quando la versione è 3 segmenti per Major.Minor.Build.
  Ciò è conforme alla convenzione SemVer v1.0.0
- Il suffisso di versione non definitiva è una stringa che inizia con un segno meno e può contenere caratteri alfanumerici ASCII [0-9A-Za-z-]
- Poiché attualmente sono supportate solo stringhe di versione non definitiva SemVer v1.0.0, il suffisso di versione non definitiva __non deve__ contenere punti o + [. +], consentiti in SemVer 2.0
- Esempi di stringhe PrereleaseString supportate includono: -alpha, -alpha1, -BETA, -update20171020

__Impatto del controllo delle versioni non definitive sull'ordinamento e sulle cartelle di installazione__

Quando viene usata una versione non definitiva l'ordinamento viene modificato, un aspetto importante durante la pubblicazione in PowerShell Gallery e l'installazione di script con i comandi di PowerShellGet. Se sono presenti due versioni di script con numero di versione, l'ordinamento è basato sulla parte della stringa che segue il segno meno. Di conseguenza, la versione 2.5.0-alpha è precedente alla versione 2.5.0-beta che è a sua volta precedente alla versione 2.5.0-gamma. Se due script hanno lo stesso numero di versione e uno solo include PrereleaseString, lo script __senza__ il suffisso di versione non definitiva viene considerato la versione pronta per la produzione e viene ordinato come versione successiva alla versione non definitiva. Ad esempio, quando viene eseguito il confronto delle versioni 2.5.0 e 2.5.0-beta, la versione 2.5.0 viene considerata la più recente.

Durante la pubblicazione in PowerShell Gallery, per impostazione predefinita la versione dello script in fase di pubblicazione deve essere successiva a qualsiasi versione pubblicata precedentemente presente in PowerShell Gallery. Un server di pubblicazione può aggiornare la versione 2.5.0-alpha con la versione 2.5.0-beta o con la versione 2.5.0 (senza suffisso di versione non definitiva).

## <a name="finding-and-acquiring-prerelease-items-using-powershellget-commands"></a>Ricerca e acquisizione di elementi di versione non definitiva mediante i comandi di PowerShellGet

L'uso di elementi di versione non definitiva con i comandi di PowerShellGet Find-Script, Install-Script, Update-Script e Save-Script richiede l'aggiunta del flag -AllowPrerelease. Se il flag -AllowPrerelease è specificato, gli elementi di versione non definitiva, se presenti, vengono visualizzati. Se il flag -AllowPrerelease non è specificato, gli elementi di versione non definitiva non vengono visualizzati.

Le uniche eccezioni nei comandi di script di PowerShellGet sono rappresentate da Get-InstalledScript e da alcuni casi di utilizzo di Uninstall-Script.

- Get-InstalledScript visualizza sempre automaticamente le informazioni di versione non definitiva nella stringa di versione, se presente.
- Uninstall-Script disinstalla per impostazione predefinita la versione più recente di uno script, se non è specificata __alcuna versione__. Questo comportamento non è stato modificato. Tuttavia, se una versione non definitiva viene specificata usando -RequiredVersion, è necessario specificare -AllowPrerelease.

## <a name="examples"></a>Esempi

```powershell
# Assume the PowerShell Gallery has TestPackage versions 1.8.0 and 1.9.0-alpha.
# If -AllowPrerelease is not specified, only version 1.8.0 will be returned.
C:\windows\system32> Find-Script TestPackage

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.8.0          TestPackage                         PSGallery            Package used to validate changes to the PowerShe...

C:\windows\system32> Find-Script TestPackage -AllowPrerelease

Version        Name                                Repository           Description
-------        ----                                ----------           -----------
1.9.0-alpha    TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# To install a prerelease, you must specify -AllowPrerelease. Specifying a prerelease version string is not sufficient.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha
PackageManagement\Find-Package : No match was found for the specified search criteria and script name 'TestPackage'.
Try Get-PSRepository to see all available registered script repositories.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.6.0\PSModule.psm1:1455 char:3
+         PackageManagement\Find-Package @PSBoundParameters | Microsoft ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...ets.FindPackage:FindPackage) [Find-Package], Exceptio
   n
    + FullyQualifiedErrorId : NoMatchFoundForCriteria,Microsoft.PowerShell.PackageManagement.Cmdlets.FindPackage

# The previous command failed because -AllowPrerelease was not specified.
# Adding -AllowPrerelease will result in success.

C:\windows\system32> Install-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

# Note that Get-InstalledScript shows the prerelease version.
# If -RequiredVersion is not specified, all installed scripts will be displayed by Get-InstalledScript
```

Uninstall-Script rimuove la versione corrente di uno script quando non viene specificato -RequiredVersion.
Se -RequiredVersion è specificato e si tratta di una versione non definitiva, è necessario aggiungere -AllowPrerelease al comando.

``` powershell
C:\windows\system32> Get-InstalledScript TestPackage

Version         Name                                Repository           Description
-------         ----                                ----------           -----------
1.9.0-alpha     TestPackage                         PSGallery            Package used to validate changes to PowerShe...

C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha
Uninstall-Script: The '-AllowPrerelease' parameter must be specified when using the Prerelease string in
MinimumVersion, MaximumVersion, or RequiredVersion.
At line:1 char:1
+ Unnstall-Script TestPackage -RequiredVersion 1.9.0-beta
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : InvalidArgument: (:) [Uninstall-Script], ArgumentException
    + FullyQualifiedErrorId : AllowPrereleaseRequiredToUsePrereleaseStringInVersion,Uninnstall-script


C:\windows\system32> Uninstall-Script TestPackage -RequiredVersion 1.9.0-alpha -AllowPrerelease
# Since script versions are not installed side-by-side, the above could be simply "Uninstall-Script TestPackage"

C:\windows\system32> Get-Installedscript TestPackage
PackageManagement\Get-Package : No match was found for the specified search criteria and script names 'testpackage'.
At C:\Program Files\WindowsPowerShell\Modules\PowerShellGet\1.5.0.0\PSModule.psm1:4088 char:9
+         PackageManagement\Get-Package @PSBoundParameters | Microsoft. ...
+         ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (Microsoft.Power...lets.GetPackage:GetPackage) [Get-Package], Exception
    + FullyQualifiedErrorId : NoMatchFound,Microsoft.PowerShell.PackageManagement.Cmdlets.GetPackage
```

## <a name="more-details"></a>Altri dettagli

- [Versioni di modulo non definitive](module-prerelease-support.md)
- [Find-script](/powershell/module/powershellget/find-script)
- [Install-script](/powershell/module/powershellget/install-script)
- [Save-script](/powershell/module/powershellget/save-script)
- [Update-script](/powershell/module/powershellget/update-script)
- [Get-Installedscript](/powershell/module/powershellget/get-installedscript)
- [UnInstall-script](/powershell/module/powershellget/uninstall-script)