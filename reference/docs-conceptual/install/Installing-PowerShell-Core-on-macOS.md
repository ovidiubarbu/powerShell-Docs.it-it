---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7db8ca0cb6d13db8ce7f11b4a4b03b7d3f9b6feb
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293402"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="85906-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="85906-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="85906-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="85906-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="85906-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="85906-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="85906-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="85906-106">After the package is installed, run `pwsh` from a terminal.</span></span>

## <a name="about-brew"></a><span data-ttu-id="85906-107">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="85906-107">About Brew</span></span>

<span data-ttu-id="85906-108">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="85906-108">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="85906-109">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="85906-109">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="85906-110">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="85906-110">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="85906-111">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="85906-111">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="85906-112">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85906-112">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="85906-113">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="85906-113">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="85906-114">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85906-114">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="85906-115">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="85906-115">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: http://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="85906-116">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="85906-116">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="85906-117">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="85906-117">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="85906-118">Dopo aver installato Homebrew, è possibile installare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="85906-118">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="85906-119">Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="85906-119">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="85906-120">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85906-120">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="85906-121">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="85906-121">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="85906-122">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85906-122">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="85906-123">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="85906-123">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="85906-124">e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="85906-124">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="85906-125">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="85906-125">Installation via Direct Download</span></span>

<span data-ttu-id="85906-126">Scaricare il pacchetto PKG</span><span class="sxs-lookup"><span data-stu-id="85906-126">Download the PKG package</span></span>
`powershell-6.2.0-osx-x64.pkg`
<span data-ttu-id="85906-127">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="85906-127">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="85906-128">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="85906-128">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="85906-129">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="85906-129">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="85906-130">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="85906-130">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="85906-131">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="85906-131">Binary Archives</span></span>

<span data-ttu-id="85906-132">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="85906-132">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="85906-133">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="85906-133">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="85906-134">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="85906-134">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="85906-135">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="85906-135">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="85906-136">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="85906-136">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="85906-137">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="85906-137">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="85906-138">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="85906-138">Install OpenSSL</span></span>

<span data-ttu-id="85906-139">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="85906-139">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="85906-140">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="85906-140">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="85906-141">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="85906-141">Install OpenSSL via Brew</span></span>

<span data-ttu-id="85906-142">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="85906-142">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="85906-143">Per installare OpenSSL, eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="85906-143">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="85906-144">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="85906-144">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="85906-145">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="85906-145">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="85906-146">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="85906-146">Install MacPorts.</span></span>
   <span data-ttu-id="85906-147">Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="85906-147">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="85906-148">Aggiornare MacPorts eseguendo `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="85906-148">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="85906-149">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="85906-149">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="85906-150">Installare OpenSSL eseguendo `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="85906-150">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="85906-151">Collegare le librerie per renderle disponibili per PowerShell:</span><span class="sxs-lookup"><span data-stu-id="85906-151">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="85906-152">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="85906-152">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="85906-153">Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:</span><span class="sxs-lookup"><span data-stu-id="85906-153">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="85906-154">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="85906-154">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="85906-155">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="85906-155">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="85906-156">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="85906-156">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="85906-157">Percorsi</span><span class="sxs-lookup"><span data-stu-id="85906-157">Paths</span></span>

* `$PSHOME` <span data-ttu-id="85906-158">è impostata su</span><span class="sxs-lookup"><span data-stu-id="85906-158">is</span></span> `/usr/local/microsoft/powershell/6.2.0/`
* <span data-ttu-id="85906-159">I profili utente vengono letti da</span><span class="sxs-lookup"><span data-stu-id="85906-159">User profiles will be read from</span></span> `~/.config/powershell/profile.ps1`
* <span data-ttu-id="85906-160">I profili predefiniti vengono letti da</span><span class="sxs-lookup"><span data-stu-id="85906-160">Default profiles will be read from</span></span> `$PSHOME/profile.ps1`
* <span data-ttu-id="85906-161">I moduli utente vengono letti da</span><span class="sxs-lookup"><span data-stu-id="85906-161">User modules will be read from</span></span> `~/.local/share/powershell/Modules`
* <span data-ttu-id="85906-162">I moduli condivisi vengono letti da</span><span class="sxs-lookup"><span data-stu-id="85906-162">Shared modules will be read from</span></span> `/usr/local/share/powershell/Modules`
* <span data-ttu-id="85906-163">I moduli predefiniti vengono letti da</span><span class="sxs-lookup"><span data-stu-id="85906-163">Default modules will be read from</span></span> `$PSHOME/Modules`
* <span data-ttu-id="85906-164">La cronologia PSReadline viene registrata in</span><span class="sxs-lookup"><span data-stu-id="85906-164">PSReadline history will be recorded to</span></span> `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

<span data-ttu-id="85906-165">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="85906-165">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="85906-166">Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="85906-166">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="85906-167">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="85906-167">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="85906-168">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="85906-168">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="85906-169">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="85906-169">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="85906-170">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="85906-170">Additional Resources</span></span>

* <span data-ttu-id="85906-171">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="85906-171">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="85906-172">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="85906-172">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="85906-173">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="85906-173">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[<span data-ttu-id="85906-174">versioni</span><span class="sxs-lookup"><span data-stu-id="85906-174">releases</span></span>]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
