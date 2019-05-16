---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: 70f5d64aa8a697a9011d07fbcb2bb821463827e1
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229730"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="daf80-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="daf80-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="daf80-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="daf80-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="daf80-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="daf80-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="daf80-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="daf80-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="daf80-107">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="daf80-107">About Brew</span></span>

<span data-ttu-id="daf80-108">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="daf80-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="daf80-109">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="daf80-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="daf80-110">In alternativa, è possibile installare PowerShell tramite [download diretto](#installation-via-direct-download) o da [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="daf80-110">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="daf80-111">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="daf80-111">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="daf80-112">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="daf80-112">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="daf80-113">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="daf80-113">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="daf80-114">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="daf80-114">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="daf80-115">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="daf80-115">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="daf80-116">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="daf80-116">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="daf80-117">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="daf80-117">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="daf80-118">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="daf80-118">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="daf80-119">Dopo aver installato Homebrew, è possibile installare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="daf80-119">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="daf80-120">Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="daf80-120">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="daf80-121">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="daf80-121">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="daf80-122">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="daf80-122">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="daf80-123">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="daf80-123">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="daf80-124">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="daf80-124">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="daf80-125">e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="daf80-125">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="daf80-126">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="daf80-126">Installation via Direct Download</span></span>

<span data-ttu-id="daf80-127">Scaricare il pacchetto PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="daf80-127">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="daf80-128">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="daf80-128">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="daf80-129">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="daf80-129">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="daf80-130">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="daf80-130">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="daf80-131">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="daf80-131">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="daf80-132">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="daf80-132">Binary Archives</span></span>

<span data-ttu-id="daf80-133">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="daf80-133">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="daf80-134">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="daf80-134">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.2.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="daf80-135">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="daf80-135">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="daf80-136">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="daf80-136">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="daf80-137">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="daf80-137">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="daf80-138">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="daf80-138">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="daf80-139">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="daf80-139">Install OpenSSL</span></span>

<span data-ttu-id="daf80-140">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="daf80-140">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="daf80-141">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="daf80-141">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="daf80-142">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="daf80-142">Install OpenSSL via Brew</span></span>

<span data-ttu-id="daf80-143">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="daf80-143">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="daf80-144">Per installare OpenSSL, eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="daf80-144">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="daf80-145">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="daf80-145">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="daf80-146">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="daf80-146">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="daf80-147">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="daf80-147">Install MacPorts.</span></span>
   <span data-ttu-id="daf80-148">Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="daf80-148">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="daf80-149">Aggiornare MacPorts eseguendo `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="daf80-149">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="daf80-150">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="daf80-150">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="daf80-151">Installare OpenSSL eseguendo `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="daf80-151">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="daf80-152">Collegare le librerie per renderle disponibili per PowerShell:</span><span class="sxs-lookup"><span data-stu-id="daf80-152">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="daf80-153">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="daf80-153">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="daf80-154">Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:</span><span class="sxs-lookup"><span data-stu-id="daf80-154">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="daf80-155">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="daf80-155">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="daf80-156">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="daf80-156">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="daf80-157">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="daf80-157">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="daf80-158">Percorsi</span><span class="sxs-lookup"><span data-stu-id="daf80-158">Paths</span></span>

* <span data-ttu-id="daf80-159">`$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="daf80-159">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="daf80-160">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="daf80-160">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="daf80-161">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="daf80-161">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="daf80-162">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="daf80-162">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="daf80-163">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="daf80-163">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="daf80-164">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="daf80-164">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="daf80-165">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="daf80-165">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="daf80-166">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="daf80-166">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="daf80-167">Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="daf80-167">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="daf80-168">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="daf80-168">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="daf80-169">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="daf80-169">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="daf80-170">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="daf80-170">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="daf80-171">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="daf80-171">Additional Resources</span></span>

* <span data-ttu-id="daf80-172">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="daf80-172">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="daf80-173">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="daf80-173">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="daf80-174">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="daf80-174">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
