---
title: Installazione di PowerShell in macOS
description: Informazioni sull'installazione di PowerShell in macOS
ms.date: 12/12/2018
ms.openlocfilehash: 3a5e71d0f69d0c39f9b7f3fa667863d7ec0a31dd
ms.sourcegitcommit: bf71c8c5e2a4fc7d5c3a67a537db1285089d03a7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/30/2020
ms.locfileid: "80395003"
---
# <a name="installing-powershell-on-macos"></a><span data-ttu-id="38f55-103">Installazione di PowerShell in macOS</span><span class="sxs-lookup"><span data-stu-id="38f55-103">Installing PowerShell on macOS</span></span>

<span data-ttu-id="38f55-104">PowerShell supporta macOS 10.12 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="38f55-104">PowerShell supports macOS 10.12 and higher.</span></span>
<span data-ttu-id="38f55-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="38f55-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="38f55-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="38f55-106">After the package is installed, run `pwsh` from a terminal.</span></span>

> [!NOTE]
> <span data-ttu-id="38f55-107">PowerShell Core 7.x è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="38f55-107">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="38f55-108">La cartella `/usr/local/microsoft/powershell/6` viene sostituita da `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="38f55-108">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="38f55-109">Se è necessario disporre di PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo degli [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="38f55-109">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

## <a name="about-brew"></a><span data-ttu-id="38f55-110">Informazioni su Brew</span><span class="sxs-lookup"><span data-stu-id="38f55-110">About Brew</span></span>

<span data-ttu-id="38f55-111">[Homebrew][brew] è la soluzione di gestione pacchetti più diffusa per macOS.</span><span class="sxs-lookup"><span data-stu-id="38f55-111">[Homebrew][brew] is the preferred package manager for macOS.</span></span> <span data-ttu-id="38f55-112">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni specifiche][brew].</span><span class="sxs-lookup"><span data-stu-id="38f55-112">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span> <span data-ttu-id="38f55-113">In alternativa, è possibile installare PowerShell tramite [download diretto](#installation-via-direct-download) o da [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="38f55-113">Otherwise you may install PowerShell via [Direct Download](#installation-via-direct-download) or from [Binary Archives](#binary-archives).</span></span>

## <a name="installation-of-latest-stable-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="38f55-114">Installazione della versione stabile più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="38f55-114">Installation of latest stable release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="38f55-115">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="38f55-115">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="38f55-116">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="38f55-116">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="38f55-117">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="38f55-117">Finally, verify that your install is working properly:</span></span>

```sh
pwsh
```

<span data-ttu-id="38f55-118">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="38f55-118">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell
```

> [!NOTE]
> <span data-ttu-id="38f55-119">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario uscire da PowerShell e riavviare la shell per completare l'aggiornamento e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="38f55-119">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade and refresh the values shown in `$PSVersionTable`.</span></span>

[brew]: https://brew.sh/

## <a name="installation-of-latest-preview-release-via-homebrew-on-macos-1012-or-higher"></a><span data-ttu-id="38f55-120">Installazione della versione di anteprima più recente con Homebrew in macOS 10.12 o versione successiva</span><span class="sxs-lookup"><span data-stu-id="38f55-120">Installation of latest preview release via Homebrew on macOS 10.12 or higher</span></span>

<span data-ttu-id="38f55-121">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="38f55-121">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="38f55-122">Dopo aver installato Homebrew, è possibile installare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="38f55-122">After you've installed Homebrew, you can install PowerShell.</span></span>
<span data-ttu-id="38f55-123">Per prima cosa installare il pacchetto [Cask-Versions][cask-versions] che consente di installare le versioni alternative dei pacchetti cask:</span><span class="sxs-lookup"><span data-stu-id="38f55-123">First, install the [Cask-Versions][cask-versions] package that lets you install alternative versions of cask packages:</span></span>

```sh
brew tap homebrew/cask-versions
```

<span data-ttu-id="38f55-124">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="38f55-124">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell-preview
```

<span data-ttu-id="38f55-125">Infine, verificare che l'installazione funzioni correttamente:</span><span class="sxs-lookup"><span data-stu-id="38f55-125">Finally, verify that your install is working properly:</span></span>

```sh
pwsh-preview
```

<span data-ttu-id="38f55-126">Quando vengono rilasciate nuove versioni di PowerShell, aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="38f55-126">When new versions of PowerShell are released, update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask upgrade powershell-preview
```

> [!NOTE]
> <span data-ttu-id="38f55-127">I comandi precedenti possono essere chiamati dall'interno di un host PowerShell (pwsh), ma in tal caso è necessario chiudere e riavviare la shell di PowerShell per completare l'aggiornamento</span><span class="sxs-lookup"><span data-stu-id="38f55-127">The commands above can be called from within a PowerShell (pwsh) host, but then the PowerShell shell must be exited and restarted to complete the upgrade.</span></span>
> <span data-ttu-id="38f55-128">e aggiornare i valori visualizzati in `$PSVersionTable`.</span><span class="sxs-lookup"><span data-stu-id="38f55-128">and refresh the values shown in `$PSVersionTable`.</span></span>

## <a name="installation-via-direct-download"></a><span data-ttu-id="38f55-129">Installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="38f55-129">Installation via Direct Download</span></span>

<span data-ttu-id="38f55-130">Scaricare il pacchetto PKG `powershell-lts-7.0.0-osx-x64.pkg`</span><span class="sxs-lookup"><span data-stu-id="38f55-130">Download the PKG package `powershell-lts-7.0.0-osx-x64.pkg`</span></span>
<span data-ttu-id="38f55-131">dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="38f55-131">from the [releases][] page onto your macOS machine.</span></span>

<span data-ttu-id="38f55-132">È possibile fare doppio clic sul file e seguire le istruzioni oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="38f55-132">You can double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-lts-7.0.0-osx-x64.pkg -target /
```

<span data-ttu-id="38f55-133">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="38f55-133">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="38f55-134">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="38f55-134">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="38f55-135">Installare PowerShell come strumento globale .NET</span><span class="sxs-lookup"><span data-stu-id="38f55-135">Install as a .NET Global tool</span></span>

<span data-ttu-id="38f55-136">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="38f55-136">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="38f55-137">Il programma di installazione dello strumento DotNet aggiunge `~/.dotnet/tools` alla variabile di ambiente `PATH`.</span><span class="sxs-lookup"><span data-stu-id="38f55-137">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="38f55-138">La shell attualmente in esecuzione non dispone tuttavia del parametro `PATH` aggiornato.</span><span class="sxs-lookup"><span data-stu-id="38f55-138">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="38f55-139">Dovrebbe essere possibile avviare PowerShell da una nuova shell digitando `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="38f55-139">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="38f55-140">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="38f55-140">Binary Archives</span></span>

<span data-ttu-id="38f55-141">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per la piattaforma macOS per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="38f55-141">PowerShell binary `tar.gz` archives are provided for the macOS platform to enable advanced deployment scenarios.</span></span>

### <a name="installing-binary-archives-on-macos"></a><span data-ttu-id="38f55-142">Installazione degli archivi binari in macOS</span><span class="sxs-lookup"><span data-stu-id="38f55-142">Installing binary archives on macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/7.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/7.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/7.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/7.0.0/pwsh /usr/local/bin/pwsh
```

<span data-ttu-id="38f55-143">Installare [OpenSSL](#install-openssl).</span><span class="sxs-lookup"><span data-stu-id="38f55-143">Install [OpenSSL](#install-openssl).</span></span> <span data-ttu-id="38f55-144">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="38f55-144">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span>

## <a name="installing-dependencies"></a><span data-ttu-id="38f55-145">Installazione delle dipendenze</span><span class="sxs-lookup"><span data-stu-id="38f55-145">Installing dependencies</span></span>

### <a name="install-xcode-command-line-tools"></a><span data-ttu-id="38f55-146">Installare gli strumenti della riga di comando XCode</span><span class="sxs-lookup"><span data-stu-id="38f55-146">Install XCode command-line tools</span></span>

```sh
xcode-select --install
```

### <a name="install-openssl"></a><span data-ttu-id="38f55-147">Installare OpenSSL</span><span class="sxs-lookup"><span data-stu-id="38f55-147">Install OpenSSL</span></span>

<span data-ttu-id="38f55-148">OpenSSL è necessario per la comunicazione remota di PowerShell e le operazioni CIM.</span><span class="sxs-lookup"><span data-stu-id="38f55-148">OpenSSL is needed for PowerShell remoting and CIM operations.</span></span> <span data-ttu-id="38f55-149">È possibile eseguire l'installazione tramite MacPorts o Brew.</span><span class="sxs-lookup"><span data-stu-id="38f55-149">You can install via MacPorts or Brew.</span></span>

#### <a name="install-openssl-via-brew"></a><span data-ttu-id="38f55-150">Installare OpenSSL tramite Brew</span><span class="sxs-lookup"><span data-stu-id="38f55-150">Install OpenSSL via Brew</span></span>

<span data-ttu-id="38f55-151">Vedere [Informazioni su Brew](#about-brew) per informazioni su Brew.</span><span class="sxs-lookup"><span data-stu-id="38f55-151">See [About Brew](#about-brew) for information about Brew.</span></span>

<span data-ttu-id="38f55-152">Per installare OpenSSL, eseguire `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="38f55-152">To install OpenSSL, run `brew install openssl`.</span></span>

#### <a name="install-openssl-via-macports"></a><span data-ttu-id="38f55-153">Installare OpenSSL tramite MacPorts</span><span class="sxs-lookup"><span data-stu-id="38f55-153">Install OpenSSL via MacPorts</span></span>

1. <span data-ttu-id="38f55-154">Installare gli [strumenti della riga di comando XCode](#install-xcode-command-line-tools).</span><span class="sxs-lookup"><span data-stu-id="38f55-154">Install the [XCode command line tools](#install-xcode-command-line-tools).</span></span>
1. <span data-ttu-id="38f55-155">Installare MacPorts.</span><span class="sxs-lookup"><span data-stu-id="38f55-155">Install MacPorts.</span></span>
   <span data-ttu-id="38f55-156">Se sono necessarie istruzioni, vedere la [guida all'installazione](https://guide.macports.org/chunked/installing.macports.html).</span><span class="sxs-lookup"><span data-stu-id="38f55-156">If you need instructions, refer to the [installation guide](https://guide.macports.org/chunked/installing.macports.html).</span></span>
1. <span data-ttu-id="38f55-157">Aggiornare MacPorts eseguendo `sudo port selfupdate`.</span><span class="sxs-lookup"><span data-stu-id="38f55-157">Update MacPorts by running `sudo port selfupdate`.</span></span>
1. <span data-ttu-id="38f55-158">Aggiornare i pacchetti MacPorts eseguendo `sudo port upgrade outdated`.</span><span class="sxs-lookup"><span data-stu-id="38f55-158">Upgrade MacPorts packages by running `sudo port upgrade outdated`.</span></span>
1. <span data-ttu-id="38f55-159">Installare OpenSSL eseguendo `sudo port install openssl`.</span><span class="sxs-lookup"><span data-stu-id="38f55-159">Install OpenSSL by running `sudo port install openssl`.</span></span>
1. <span data-ttu-id="38f55-160">Collegare le librerie per renderle disponibili per PowerShell:</span><span class="sxs-lookup"><span data-stu-id="38f55-160">Link the libraries to make them available to PowerShell:</span></span>

```sh
sudo mkdir -p /usr/local/opt/openssl
sudo ln -s /opt/local/lib /usr/local/opt/openssl/lib
```

## <a name="uninstalling-powershell"></a><span data-ttu-id="38f55-161">Disinstallazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="38f55-161">Uninstalling PowerShell</span></span>

<span data-ttu-id="38f55-162">Se PowerShell è stato installato con Homebrew, usare il comando seguente per la disinstallazione:</span><span class="sxs-lookup"><span data-stu-id="38f55-162">If you installed PowerShell with Homebrew, use the following command to uninstall:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="38f55-163">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="38f55-163">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="38f55-164">Per rimuovere i percorsi aggiuntivi di PowerShell, vedere la sezione [Percorsi](#paths) in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="38f55-164">To remove the additional PowerShell paths, refer to the [paths](#paths) section in this document and remove the paths using `sudo rm`.</span></span>

> [!NOTE]
> <span data-ttu-id="38f55-165">Questo passaggio non è necessario se PowerShell è stato installato con Homebrew.</span><span class="sxs-lookup"><span data-stu-id="38f55-165">This is not necessary if you installed with Homebrew.</span></span>

## <a name="paths"></a><span data-ttu-id="38f55-166">Percorsi</span><span class="sxs-lookup"><span data-stu-id="38f55-166">Paths</span></span>

* <span data-ttu-id="38f55-167">`$PSHOME` è `/usr/local/microsoft/powershell/7.0.0/`</span><span class="sxs-lookup"><span data-stu-id="38f55-167">`$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`</span></span>
* <span data-ttu-id="38f55-168">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="38f55-168">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="38f55-169">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="38f55-169">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="38f55-170">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="38f55-170">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="38f55-171">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="38f55-171">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="38f55-172">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="38f55-172">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="38f55-173">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="38f55-173">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="38f55-174">I profili rispettano la configurazione di PowerShell per ogni host.</span><span class="sxs-lookup"><span data-stu-id="38f55-174">The profiles respect PowerShell's per-host configuration.</span></span>
<span data-ttu-id="38f55-175">Di conseguenza, il profilo specifico dell'host predefinito è presente in `Microsoft.PowerShell_profile.ps1` nelle stesse posizioni.</span><span class="sxs-lookup"><span data-stu-id="38f55-175">So the default host-specific profile exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="38f55-176">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in macOS.</span><span class="sxs-lookup"><span data-stu-id="38f55-176">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on macOS.</span></span>

<span data-ttu-id="38f55-177">Poiché macOS è una derivazione di BSD, viene usato il prefisso `/usr/local` invece di `/opt`.</span><span class="sxs-lookup"><span data-stu-id="38f55-177">Because macOS is a derivation of BSD, the prefix `/usr/local` is used instead of `/opt`.</span></span>
<span data-ttu-id="38f55-178">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/7.0.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="38f55-178">So, `$PSHOME` is `/usr/local/microsoft/powershell/7.0.0/`, and the symbolic link is placed at `/usr/local/bin/pwsh`.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="38f55-179">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="38f55-179">Additional Resources</span></span>

* <span data-ttu-id="38f55-180">[Sito Web di Homebrew][brew]</span><span class="sxs-lookup"><span data-stu-id="38f55-180">[Homebrew Web][brew]</span></span>
* <span data-ttu-id="38f55-181">[Repository Github di Homebrew][GitHub]</span><span class="sxs-lookup"><span data-stu-id="38f55-181">[Homebrew Github Repository][GitHub]</span></span>
* <span data-ttu-id="38f55-182">[Homebrew-Cask][cask]</span><span class="sxs-lookup"><span data-stu-id="38f55-182">[Homebrew-Cask][cask]</span></span>

[brew]: http://brew.sh/
[Cask]: https://github.com/Homebrew/homebrew-cask
[cask-versions]: https://github.com/Homebrew/homebrew-cask-versions
[GitHub]: https://github.com/Homebrew
[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
