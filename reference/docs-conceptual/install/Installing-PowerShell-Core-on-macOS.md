---
title: Installazione di PowerShell Core in macOS
description: Informazioni sull'installazione di PowerShell Core in macOS
ms.date: 12/12/2018
ms.openlocfilehash: ad1306e99261e8e6e2fd49d3199d863929c31e92
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "73444432"
---
# <a name="installing-powershell-core-on-macos"></a><span data-ttu-id="b985d-103">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="b985d-103">Installing PowerShell Core on macOS</span></span>

<span data-ttu-id="b985d-104">PowerShell Core supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="b985d-104">PowerShell Core supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="b985d-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="b985d-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="b985d-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="b985d-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!TIP]
> <span data-ttu-id="b985d-107">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="b985d-107">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it’s easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>
>
> ```
> dotnet tool install --global PowerShell
> ```

## <a name="about-brew"></a><span data-ttu-id="b985d-108">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="b985d-108">About Brew</span></span>

<span data-ttu-id="b985d-109">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="b985d-109">[Homebrew][brew] is the preferred package manager for macOS.</span></span>
<span data-ttu-id="b985d-110">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni specifiche][brew].</span><span class="sxs-lookup"><span data-stu-id="b985d-110">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>
<span data-ttu-id="b985d-111">In alternativa, è possibile installare PowerShell tramite [download diretto](#installation-via-direct-download) o da [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="b985d-111">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b985d-112">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="b985d-112">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b985d-113">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="b985d-113">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b985d-114">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b985d-114">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="b985d-115">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="b985d-115">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="b985d-116">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b985d-116">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="b985d-117">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b985d-117">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="b985d-118">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="b985d-118">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="b985d-119">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="b985d-119">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b985d-120">Dopo aver installato Homebrew, è possibile installare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b985d-120">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="b985d-121">Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="b985d-121">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="b985d-122">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b985d-122">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="b985d-123">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="b985d-123">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="b985d-124">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b985d-124">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="b985d-125">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="b985d-125">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="b985d-126">e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="b985d-126">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="b985d-127">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="b985d-127">Installation via Direct Download</span></span>

<span data-ttu-id="b985d-128">Scaricare il pacchetto PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="b985d-128">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="b985d-129">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="b985d-129">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="b985d-130">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="b985d-130">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="b985d-131">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b985d-131">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b985d-132">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="b985d-132">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="b985d-133">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="b985d-133">Binary Archives</span></span>

<span data-ttu-id="b985d-134">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="b985d-134">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="b985d-135">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="b985d-135">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="b985d-136">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="b985d-136">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="b985d-137">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="b985d-137">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="b985d-138">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="b985d-138">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="b985d-139">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="b985d-139">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="b985d-140">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="b985d-140">Install OpenSSL</span></span>

<span data-ttu-id="b985d-141">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="b985d-141">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="b985d-142">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="b985d-142">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="b985d-143">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="b985d-143">Install OpenSSL via Brew</span></span>

<span data-ttu-id="b985d-144">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="b985d-144">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="b985d-145">Per installare OpenSSL, eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="b985d-145">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="b985d-146">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="b985d-146">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="b985d-147">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="b985d-147">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="b985d-148">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="b985d-148">Install MacPorts.</span></span>
   <span data-ttu-id="b985d-149">Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="b985d-149">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="b985d-150">Aggiornare MacPorts eseguendo `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="b985d-150">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="b985d-151">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="b985d-151">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="b985d-152">Installare OpenSSL eseguendo `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="b985d-152">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="b985d-153">Collegare le librerie per renderle disponibili per PowerShell:</span><span class="sxs-lookup"><span data-stu-id="b985d-153">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell-core"></a><span data-ttu-id="b985d-154">Disinstallazione di PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="b985d-154">Uninstalling PowerShell Core</span></span>

<span data-ttu-id="b985d-155">Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:</span><span class="sxs-lookup"><span data-stu-id="b985d-155">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="b985d-156">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="b985d-156">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="b985d-157">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="b985d-157">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="b985d-158">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="b985d-158">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="b985d-159">Percorsi</span><span class="sxs-lookup"><span data-stu-id="b985d-159">Paths</span></span>

* <span data-ttu-id="b985d-160">`$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="b985d-160">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="b985d-161">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b985d-161">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="b985d-162">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="b985d-162">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="b985d-163">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b985d-163">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b985d-164">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="b985d-164">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="b985d-165">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="b985d-165">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="b985d-166">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="b985d-166">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="b985d-167">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="b985d-167">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="b985d-168">Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="b985d-168">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="b985d-169">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="b985d-169">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="b985d-170">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="b985d-170">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="b985d-171">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="b985d-171">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="b985d-172">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="b985d-172">Additional Resources</span></span>

* <span data-ttu-id="b985d-173">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="b985d-173">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="b985d-174">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="b985d-174">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="b985d-175">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="b985d-175">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
