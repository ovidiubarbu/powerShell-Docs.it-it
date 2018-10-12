---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 08/06/2018
ms.openlocfilehash: 042c933dfa83f3ab52e315036e4f817145116d00
ms.sourcegitcommit: aa41249f153bbc6e11667ade60c878980c15abc6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/14/2018
ms.locfileid: "45611488"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="def75-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="def75-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="def75-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="def75-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="def75-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="def75-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="def75-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="def75-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="def75-107">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="def75-107">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="def75-108">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="def75-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="def75-109">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="def75-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="def75-110">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="def75-110">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="def75-111">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="def75-111">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="def75-112">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="def75-112">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="def75-113">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="def75-113">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="def75-114">e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="def75-114">and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="def75-115">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="def75-115">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="def75-116">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="def75-116">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="def75-117">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="def75-117">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="def75-118">Dopo aver installato Homebrew, installare PowerShell sarà semplice.</span><span class="sxs-lookup"><span data-stu-id="def75-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="def75-119">Per prima cosa installare [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="def75-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="def75-120">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="def75-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="def75-121">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="def75-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="def75-122">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="def75-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="def75-123">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="def75-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="def75-124">e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="def75-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="def75-125">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="def75-125">Installation via Direct Download</span></span>

<span data-ttu-id="def75-126">Scaricare il pacchetto PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="def75-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="def75-127">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="def75-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="def75-128">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="def75-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

## <a name="binary-archives"></a><span data-ttu-id="def75-129">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="def75-129">Binary Archives</span></span>

<span data-ttu-id="def75-130">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="def75-130">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="def75-131">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="def75-131">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.1.0/pwsh /usr/local/bin/pwsh
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="def75-132">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="def75-132">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="def75-133">Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:</span><span class="sxs-lookup"><span data-stu-id="def75-133">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="def75-134">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="def75-134">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="def75-135">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="def75-135">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="def75-136">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="def75-136">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="def75-137">Percorsi</span><span class="sxs-lookup"><span data-stu-id="def75-137">Paths</span></span>

* <span data-ttu-id="def75-138">`$PSHOME` è `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="def75-138">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="def75-139">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="def75-139">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="def75-140">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="def75-140">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="def75-141">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="def75-141">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="def75-142">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="def75-142">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="def75-143">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="def75-143">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="def75-144">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="def75-144">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="def75-145">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="def75-145">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="def75-146">Di conseguenza, i profili specifici dell'host predefinito sono presenti in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="def75-146">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="def75-147">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="def75-147">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="def75-148">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="def75-148">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="def75-149">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.1.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="def75-149">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="def75-150">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="def75-150">Additional Resources</span></span>

* <span data-ttu-id="def75-151">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="def75-151">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="def75-152">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="def75-152">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="def75-153">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="def75-153">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
