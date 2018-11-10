---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 11/02/2018
ms.openlocfilehash: 162e841bf71d708e9db84ea1bb2dbef13924783b
ms.sourcegitcommit: f4247d3f91d06ec392c4cd66921ce7d0456a2bd9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/05/2018
ms.locfileid: "50998504"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="8c4fd-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="8c4fd-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="8c4fd-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="8c4fd-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="8c4fd-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="8c4fd-107">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="8c4fd-107">About Brew</span></span>

<span data-ttu-id="8c4fd-108">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="8c4fd-109">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="8c4fd-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8c4fd-110">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="8c4fd-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8c4fd-111">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="8c4fd-112">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="8c4fd-113">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="8c4fd-114">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-114">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="8c4fd-115">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire e riavviare la shell di PowerShell per completare l'aggiornamento e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in $PSVersionTable.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="8c4fd-116">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="8c4fd-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="8c4fd-117">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="8c4fd-118">Dopo aver installato Homebrew, installare PowerShell sarà semplice.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-118">Once you've installed Homebrew, installing PowerShell is easy.</span></span>
<span data-ttu-id="8c4fd-119">Per prima cosa installare [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-119">First, install [Cask-Versions][cask-versions] which lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="8c4fd-120">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="8c4fd-121">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="8c4fd-122">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-122">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="8c4fd-123">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="8c4fd-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="8c4fd-124">e aggiornare i valori visualizzati in $PSVersionTable.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-124">and refresh the values shown in $PSVersionTable.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="8c4fd-125">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="8c4fd-125">Installation via Direct Download</span></span>

<span data-ttu-id="8c4fd-126">Scaricare il pacchetto PKG `powershell-6.1.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-126">Download the PKG package `powershell-6.1.0-osx-x64.pkg`</span></span>
<span data-ttu-id="8c4fd-127">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="8c4fd-128">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.1.0-osx-x64.pkg -target /
```

<span data-ttu-id="8c4fd-129">Installare [OpenSSL](#install-openssl) perché è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-129">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="8c4fd-130">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="8c4fd-130">Binary Archives</span></span>

<span data-ttu-id="8c4fd-131">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-131">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="8c4fd-132">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="8c4fd-132">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="8c4fd-133">Installare [OpenSSL](#install-openssl) perché è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-133">Install [OpenSSL](#install-openssl) as this is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="8c4fd-134">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="8c4fd-134">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="8c4fd-135">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="8c4fd-135">Install XCode command line tools</span></span>

```shell
xcode-select -install
```

### <a name="install-openssl"></a><span data-ttu-id="8c4fd-136">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="8c4fd-136">Install OpenSSL</span></span>

<span data-ttu-id="8c4fd-137">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>  <span data-ttu-id="8c4fd-138">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-138">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="8c4fd-139">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="8c4fd-139">Install OpenSSL via Brew</span></span>

<span data-ttu-id="8c4fd-140">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-140">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="8c4fd-141">Eseguire `brew install openssl` per installare OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-141">Run `brew install openssl` to install OpenSSL.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="8c4fd-142">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="8c4fd-142">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="8c4fd-143">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools)</span><span class="sxs-lookup"><span data-stu-id="8c4fd-143">Instal the [XCode command line tools](#install-xcode-command-line-tools)</span></span>
1. <span data-ttu-id="8c4fd-144">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-144">Install MacPorts.</span></span>
   <span data-ttu-id="8c4fd-145">Vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html) se sono necessarie istruzioni.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-145">See the [installation guide](https://guide.macports.org/chunked/installing.macports.html) if you need instructions.</span></span>
1. <span data-ttu-id="8c4fd-146">Aggiornare MacPorts eseguendo `sudo port selfupdate`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-146">Update MacPorts by running `sudo port selfupdate`</span></span>
1. <span data-ttu-id="8c4fd-147">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-147">Upgrade MacPorts packages by running `sudo port upgrade outdated`</span></span>
1. <span data-ttu-id="8c4fd-148">Installare OpenSSL eseguendo `sudo port instal openssl`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-148">Install OpenSSL by running by running `sudo port instal openssl`</span></span>
1. <span data-ttu-id="8c4fd-149">Collegare le librerie in modo che PowerShell possa usarle.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-149">Link the libraries so that PowerShell can use it.</span></span>

```shell
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="8c4fd-150">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="8c4fd-150">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="8c4fd-151">Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-151">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="8c4fd-152">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="8c4fd-152">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="8c4fd-153">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-153">To remove the additional PowerShell paths, please see the [paths](#paths) section in this document and remove the desired the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="8c4fd-154">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-154">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="8c4fd-155">Percorsi</span><span class="sxs-lookup"><span data-stu-id="8c4fd-155">Paths</span></span>

* <span data-ttu-id="8c4fd-156">`$PSHOME` è `/usr/local/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-156">`$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="8c4fd-157">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-157">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="8c4fd-158">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-158">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="8c4fd-159">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-159">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8c4fd-160">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-160">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="8c4fd-161">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-161">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="8c4fd-162">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="8c4fd-162">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="8c4fd-163">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-163">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="8c4fd-164">Di conseguenza, i profili specifici dell'host predefinito sono presenti in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-164">So the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="8c4fd-165">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-165">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="8c4fd-166">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-166">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="8c4fd-167">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.1.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="8c4fd-167">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.1.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8c4fd-168">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="8c4fd-168">Additional Resources</span></span>

* <span data-ttu-id="8c4fd-169">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="8c4fd-169">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="8c4fd-170">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="8c4fd-170">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="8c4fd-171">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="8c4fd-171">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
