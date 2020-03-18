---
title: Installazione di PowerShell in macOS
description: Informazioni sull'installazione di PowerShell in macOS
ms.date: 12/12/2018
ms.openlocfilehash: 7f0d6a1aa275deb39a7d670546ee7e833b8ef315
ms.sourcegitcommit: 4a26c05f162c4fa347a9d67e339f8a33e230b9ba
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/06/2020
ms.locfileid: "78404828"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="c06ee-103">Installazione di PowerShell in macOS</span><span class="sxs-lookup"><span data-stu-id="c06ee-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="c06ee-104">PowerShell supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="c06ee-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="c06ee-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="c06ee-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="c06ee-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="c06ee-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="c06ee-107">PowerShell Core 7.x è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="c06ee-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="c06ee-108">La cartella `/usr/local/microsoft/powershell/6` viene sostituita da `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="c06ee-109">Se è necessario disporre di PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo degli [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="c06ee-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="c06ee-110">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="c06ee-110">About Brew</span></span>

<span data-ttu-id="c06ee-111">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="c06ee-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="c06ee-112">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni specifiche][brew].</span><span class="sxs-lookup"><span data-stu-id="c06ee-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="c06ee-113">In alternativa, è possibile installare PowerShell tramite [download diretto](#installation-via-direct-download) o da [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="c06ee-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="c06ee-114">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="c06ee-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="c06ee-115">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="c06ee-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c06ee-116">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c06ee-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="c06ee-117">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="c06ee-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="c06ee-118">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c06ee-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="c06ee-119">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="c06ee-120">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="c06ee-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="c06ee-121">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="c06ee-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c06ee-122">Dopo aver installato Homebrew, è possibile installare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c06ee-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="c06ee-123">Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="c06ee-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="c06ee-124">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c06ee-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="c06ee-125">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="c06ee-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="c06ee-126">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c06ee-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="c06ee-127">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="c06ee-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="c06ee-128">e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="c06ee-129">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="c06ee-129">Installation via Direct Download</span></span>

<span data-ttu-id="c06ee-130">Scaricare il pacchetto PKG `powershell-6.2.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="c06ee-130">Download the PKG package `powershell-6.2.0-osx-x64.pkg`</span></span>
<span data-ttu-id="c06ee-131">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="c06ee-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="c06ee-132">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="c06ee-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.2.0-osx-x64.pkg -target /
```

<span data-ttu-id="c06ee-133">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="c06ee-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="c06ee-134">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="c06ee-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="c06ee-135">Installare PowerShell come strumento globale .NET</span><span class="sxs-lookup"><span data-stu-id="c06ee-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="c06ee-136">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="c06ee-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

## <a name="binary-archives"></a><span data-ttu-id="c06ee-137">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="c06ee-137">Binary Archives</span></span>

<span data-ttu-id="c06ee-138">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="c06ee-138">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="c06ee-139">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="c06ee-139">Installing binary archives on macOS</span></span>

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

<span data-ttu-id="c06ee-140">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="c06ee-140">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="c06ee-141">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="c06ee-141">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="c06ee-142">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="c06ee-142">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="c06ee-143">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="c06ee-143">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="c06ee-144">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="c06ee-144">Install OpenSSL</span></span>

<span data-ttu-id="c06ee-145">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="c06ee-145">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="c06ee-146">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="c06ee-146">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="c06ee-147">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="c06ee-147">Install OpenSSL via Brew</span></span>

<span data-ttu-id="c06ee-148">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="c06ee-148">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="c06ee-149">Per installare OpenSSL, eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-149">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="c06ee-150">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="c06ee-150">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="c06ee-151">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="c06ee-151">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="c06ee-152">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="c06ee-152">Install MacPorts.</span></span>
   <span data-ttu-id="c06ee-153">Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="c06ee-153">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="c06ee-154">Aggiornare MacPorts eseguendo `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-154">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="c06ee-155">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-155">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="c06ee-156">Installare OpenSSL eseguendo `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-156">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="c06ee-157">Collegare le librerie per renderle disponibili per PowerShell:</span><span class="sxs-lookup"><span data-stu-id="c06ee-157">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="c06ee-158">Disinstallazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c06ee-158">Uninstalling PowerShell</span></span>

<span data-ttu-id="c06ee-159">Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:</span><span class="sxs-lookup"><span data-stu-id="c06ee-159">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="c06ee-160">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="c06ee-160">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="c06ee-161">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-161">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="c06ee-162">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="c06ee-162">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="c06ee-163">Percorsi</span><span class="sxs-lookup"><span data-stu-id="c06ee-163">Paths</span></span>

* <span data-ttu-id="c06ee-164">`$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="c06ee-164">`$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="c06ee-165">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c06ee-165">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="c06ee-166">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="c06ee-166">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="c06ee-167">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c06ee-167">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c06ee-168">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="c06ee-168">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="c06ee-169">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="c06ee-169">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="c06ee-170">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="c06ee-170">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="c06ee-171">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="c06ee-171">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="c06ee-172">Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="c06ee-172">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="c06ee-173">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="c06ee-173">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="c06ee-174">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-174">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="c06ee-175">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.2.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="c06ee-175">So, `$PSHOME` is `/usr/local/microsoft/powershell/6.2.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="c06ee-176">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="c06ee-176">Additional Resources</span></span>

* <span data-ttu-id="c06ee-177">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="c06ee-177">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="c06ee-178">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="c06ee-178">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="c06ee-179">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="c06ee-179">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
