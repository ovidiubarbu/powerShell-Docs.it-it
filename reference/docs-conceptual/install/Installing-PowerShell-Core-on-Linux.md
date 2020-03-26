---
title: Installazione di PowerShell in Linux
description: Informazioni sull'installazione di PowerShell in varie distribuzioni Linux
ms.date: 03/09/2020
ms.openlocfilehash: 13b8583ed45f1201e61225b377112a59d2b26cb2
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082806"
---
# <a name="installing-powershell-on-linux"></a><span data-ttu-id="80957-103">Installazione di PowerShell in Linux</span><span class="sxs-lookup"><span data-stu-id="80957-103">Installing PowerShell on Linux</span></span>

<span data-ttu-id="80957-104">Supporta [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="80957-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="80957-105">Per le distribuzioni Linux non supportate ufficialmente, è possibile provare a installare PowerShell con il [pacchetto PowerShell Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="80957-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="80957-106">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'archivio [`tar.gz`][tar] di Linux ma sarà necessario configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="80957-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="80957-107">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="80957-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="80957-108">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="80957-108">After the package is installed, run `pwsh` from a terminal.</span></span> <span data-ttu-id="80957-109">Eseguire `pwsh-preview` se è stata installata una [versione di anteprima](#installing-preview-releases).</span><span class="sxs-lookup"><span data-stu-id="80957-109">Run `pwsh-preview` if you installed a [Preview release](#installing-preview-releases).</span></span>

> [!NOTE]
> <span data-ttu-id="80957-110">PowerShell 7.x è un aggiornamento sul posto che rimuove PowerShell Core 6.x.</span><span class="sxs-lookup"><span data-stu-id="80957-110">PowerShell 7 is an in-place upgrade that removes PowerShell Core 6.x.</span></span>
>
> <span data-ttu-id="80957-111">La cartella `/usr/local/microsoft/powershell/6` viene sostituita da `/usr/local/microsoft/powershell/7`.</span><span class="sxs-lookup"><span data-stu-id="80957-111">The `/usr/local/microsoft/powershell/6` folder is replaced by `/usr/local/microsoft/powershell/7`.</span></span>
>
> <span data-ttu-id="80957-112">Se è necessario avere PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo degli [archivi di file binari](#binary-archives).</span><span class="sxs-lookup"><span data-stu-id="80957-112">If you need to run PowerShell 6 side-by-side with PowerShell 7, reinstall PowerShell 6 using the [binary archive](#binary-archives) method.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[u1904]: #ubuntu-1904
[deb8]: #debian-8
[deb9]: #debian-9
[deb10]: #debian-10
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives


## <a name="installing-preview-releases"></a><span data-ttu-id="80957-113">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="80957-113">Installing Preview Releases</span></span>

<span data-ttu-id="80957-114">Quando si installa una versione di anteprima di PowerShell per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="80957-114">When installing a PowerShell Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="80957-115">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="80957-115">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="80957-116">La tabella seguente contiene i comandi per installare i pacchetti stabili e di anteprima usando diversi strumenti di gestione dei pacchetti:</span><span class="sxs-lookup"><span data-stu-id="80957-116">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

| <span data-ttu-id="80957-117">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="80957-117">Distribution(s)</span></span> |            <span data-ttu-id="80957-118">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="80957-118">Stable Command</span></span>            |               <span data-ttu-id="80957-119">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="80957-119">Preview Command</span></span>                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| <span data-ttu-id="80957-120">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="80957-120">Ubuntu, Debian</span></span>  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| <span data-ttu-id="80957-121">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="80957-121">CentOS, RedHat</span></span>  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| <span data-ttu-id="80957-122">Fedora</span><span class="sxs-lookup"><span data-stu-id="80957-122">Fedora</span></span>          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a><span data-ttu-id="80957-123">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80957-123">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="80957-124">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="80957-124">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="80957-125">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="80957-125">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="80957-126">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-126">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/16.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-127">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-127">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-128">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-128">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="80957-129">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80957-129">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="80957-130">Scaricare il pacchetto Debian `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="80957-130">Download the Debian package `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="80957-131">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-131">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80957-132">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="80957-132">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="80957-133">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80957-133">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="80957-134">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-134">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="80957-135">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80957-135">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="80957-136">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="80957-136">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="80957-137">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="80957-137">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="80957-138">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-138">The preferred method is as follows:</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Enable the "universe" repositories
sudo add-apt-repository universe

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-139">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-139">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-140">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-140">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="80957-141">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-141">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="80957-142">Scaricare il pacchetto Debian `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="80957-142">Download the Debian package `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="80957-143">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-143">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="80957-144">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="80957-144">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="80957-145">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80957-145">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="80957-146">Ubuntu 18.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-146">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="80957-147">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="80957-147">Ubuntu 18.10</span></span>

<span data-ttu-id="80957-148">L'installazione è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="80957-148">Installation is supported via `snapd`.</span></span> <span data-ttu-id="80957-149">Per le istruzioni, vedere [Pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="80957-149">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="80957-150">Ubuntu 18.10 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle)[supportata dalla community](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="80957-150">Ubuntu 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="ubuntu-1904"></a><span data-ttu-id="80957-151">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="80957-151">Ubuntu 19.04</span></span>

<span data-ttu-id="80957-152">L'installazione è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="80957-152">Installation is supported via `snapd`.</span></span> <span data-ttu-id="80957-153">Per le istruzioni, vedere [Pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="80957-153">For instructions, see [Snap Package][snap].</span></span>

> [!NOTE]
> <span data-ttu-id="80957-154">Ubuntu 19.04 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle)[supportata dalla community](../powershell-support-lifecycle.md).</span><span class="sxs-lookup"><span data-stu-id="80957-154">Ubuntu 19.04 is an [interim release](https://www.ubuntu.com/about/release-cycle) that's [community supported](../powershell-support-lifecycle.md).</span></span>

## <a name="debian-8"></a><span data-ttu-id="80957-155">Debian 8</span><span class="sxs-lookup"><span data-stu-id="80957-155">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="80957-156">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="80957-156">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="80957-157">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="80957-157">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="80957-158">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-158">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-jessie-prod jessie main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-159">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-159">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-160">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-160">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="80957-161">Debian 9</span><span class="sxs-lookup"><span data-stu-id="80957-161">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="80957-162">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="80957-162">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="80957-163">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="80957-163">PowerShell for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="80957-164">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-164">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install -y curl gnupg apt-transport-https

# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" > /etc/apt/sources.list.d/microsoft.list'

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-165">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-165">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-166">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-166">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="80957-167">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-167">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="80957-168">Scaricare il pacchetto Debian `powershell_7.0.0-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="80957-168">Download the Debian package `powershell_7.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="80957-169">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-169">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="80957-170">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-170">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a><span data-ttu-id="80957-171">Debian 10</span><span class="sxs-lookup"><span data-stu-id="80957-171">Debian 10</span></span>

> [!NOTE]
> <span data-ttu-id="80957-172">Debian 10 è supportato solo in PowerShell 7.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="80957-172">Debian 10 is only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---debian-10"></a><span data-ttu-id="80957-173">Debian 10: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-173">Installation via Direct Download - Debian 10</span></span>

<span data-ttu-id="80957-174">Scaricare il pacchetto tar. gz `powershell_7.0.0-linux-x64.tar.gz` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="80957-174">Download the tar.gz package `powershell_7.0.0-linux-x64.tar.gz` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="80957-175">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-175">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo apt-get update
# install the requirements
sudo apt-get install -y \
        less \
        locales \
        ca-certificates \
        libicu63 \
        libssl1.1 \
        libc6 \
        libgcc1 \
        libgssapi-krb5-2 \
        liblttng-ust0 \
        libstdc++6 \
        zlib1g \
        curl

# Download the powershell '.tar.gz' archive
curl -L  https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="alpine-39-and-310"></a><span data-ttu-id="80957-176">Alpine 3.9 e 3.10</span><span class="sxs-lookup"><span data-stu-id="80957-176">Alpine 3.9 and 3.10</span></span>

> [!NOTE]
> <span data-ttu-id="80957-177">Alpine 3.9 e 3.10 sono supportati solo in PowerShell 7.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="80957-177">Alpine 3.9 and 3.10 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-direct-download---alpine-39-and-310"></a><span data-ttu-id="80957-178">Alpine 3.9 e 3.10: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-178">Installation via Direct Download - Alpine 3.9 and 3.10</span></span>

<span data-ttu-id="80957-179">Scaricare il pacchetto tar.gz `powershell-7.0.0-linux-alpine-x64.tar.gz` dalla pagina delle [versioni][] nel computer Alpine.</span><span class="sxs-lookup"><span data-stu-id="80957-179">Download the tar.gz package `powershell-7.0.0-linux-alpine-x64.tar.gz` from the [releases][] page onto the Alpine machine.</span></span>

<span data-ttu-id="80957-180">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-180">Then, in the terminal, execute the following commands:</span></span>

```sh
# install the requirements
sudo apk add --no-cache \
    ca-certificates \
    less \
    ncurses-terminfo-base \
    krb5-libs \
    libgcc \
    libintl \
    libssl1.1 \
    libstdc++ \
    tzdata \
    userspace-rcu \
    zlib \
    icu-libs \
    curl

sudo apk -X https://dl-cdn.alpinelinux.org/alpine/edge/main add --no-cache \
    lttng-ust

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-alpine-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

## <a name="centos-7"></a><span data-ttu-id="80957-181">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80957-181">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="80957-182">Questo pacchetto funziona in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="80957-182">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="80957-183">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="80957-183">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="80957-184">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="80957-184">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-185">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-185">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-186">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-186">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="80957-187">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="80957-188">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="80957-188">Using [CentOS 7][], download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="80957-189">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-189">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80957-190">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="80957-190">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="80957-191">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-191">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80957-193">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="80957-193">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80957-194">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="80957-194">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="80957-195">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="80957-195">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-196">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="80957-196">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="80957-197">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="80957-197">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80957-198">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="80957-199">Scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="80957-199">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="80957-200">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-200">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80957-201">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="80957-201">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="80957-202">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-202">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="80957-203">openSUSE</span><span class="sxs-lookup"><span data-stu-id="80957-203">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="80957-204">Installazione - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="80957-204">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="80957-205">Installazione - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="80957-205">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="80957-206">Disinstallazione - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="80957-206">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="80957-207">Fedora</span><span class="sxs-lookup"><span data-stu-id="80957-207">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="80957-208">Fedora 28 è supportato solo in PowerShell 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="80957-208">Fedora 28 is only supported in PowerShell 6.1 and newer.</span></span>

> [!NOTE]
> <span data-ttu-id="80957-209">Fedora 29 e 30 sono supportati solo in PowerShell 7.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="80957-209">Fedora 29 and 30 are only supported in PowerShell 7.0 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a><span data-ttu-id="80957-210">Fedora 28, 29 e 30: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="80957-210">Installation via Package Repository (preferred) - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="80957-211">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="80957-211">PowerShell for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install a system component
sudo dnf install compat-openssl10

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a><span data-ttu-id="80957-212">Fedora 28, 29 e 30: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="80957-212">Installation via Direct Download - Fedora 28, 29, and 30</span></span>

<span data-ttu-id="80957-213">Scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="80957-213">Download the RPM package `powershell-7.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="80957-214">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="80957-214">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="80957-215">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="80957-215">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a><span data-ttu-id="80957-216">Fedora 28, 29 e 30: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-216">Uninstallation - Fedora 28, 29, and 30</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="80957-217">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="80957-217">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="80957-218">Il supporto Arch non è ufficialmente supportato da Microsoft e viene gestito dalla community.</span><span class="sxs-lookup"><span data-stu-id="80957-218">Arch support is not officially supported by Microsoft and is maintained by the community.</span></span>

<span data-ttu-id="80957-219">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="80957-219">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="80957-220">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="80957-220">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="80957-221">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="80957-221">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="80957-222">Può essere installato usando il [file binario della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="80957-222">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="80957-223">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="80957-223">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="80957-224">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="80957-224">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="80957-226">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="80957-226">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="80957-227">Recupero di snapd</span><span class="sxs-lookup"><span data-stu-id="80957-227">Getting snapd</span></span>

<span data-ttu-id="80957-228">`snapd` è necessario per l'esecuzione di pacchetti Snap.</span><span class="sxs-lookup"><span data-stu-id="80957-228">`snapd` is required to run snaps.</span></span> <span data-ttu-id="80957-229">Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.</span><span class="sxs-lookup"><span data-stu-id="80957-229">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="80957-230">Installazione tramite Snap</span><span class="sxs-lookup"><span data-stu-id="80957-230">Installation via Snap</span></span>

<span data-ttu-id="80957-231">Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).</span><span class="sxs-lookup"><span data-stu-id="80957-231">PowerShell for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="80957-232">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-232">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="80957-233">Per installare una versione di anteprima, usare il metodo seguente:</span><span class="sxs-lookup"><span data-stu-id="80957-233">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="80957-234">Dopo l'installazione, Snap verrà aggiornato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="80957-234">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="80957-235">È possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="80957-235">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="80957-236">Disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="80957-237">o</span><span class="sxs-lookup"><span data-stu-id="80957-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="80957-238">Kali</span><span class="sxs-lookup"><span data-stu-id="80957-238">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="80957-239">Il supporto Kali non è ufficialmente supportato da Microsoft e viene gestito dalla community.</span><span class="sxs-lookup"><span data-stu-id="80957-239">Kali support is not officially supported by Microsoft and is maintained by the community.</span></span>

### <a name="installation---kali"></a><span data-ttu-id="80957-240">Kali: installazione</span><span class="sxs-lookup"><span data-stu-id="80957-240">Installation - Kali</span></span>

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="80957-241">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-241">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a><span data-ttu-id="80957-242">Raspbian</span><span class="sxs-lookup"><span data-stu-id="80957-242">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="80957-243">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="80957-243">Raspbian support is experimental.</span></span>

<span data-ttu-id="80957-244">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="80957-244">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="80957-245">CoreCLR e PowerShell funzionano solo nei dispositivi Pi 2 e Pi 3, perché altri dispositivi come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) hanno un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="80957-245">CoreCLR and PowerShell will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="80957-246">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="80957-246">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="80957-247">Raspbian: installazione</span><span class="sxs-lookup"><span data-stu-id="80957-247">Installation - Raspbian</span></span>

```sh
###################################
# Prerequisites

# Update package lists
sudo apt-get update

# Install libunwind8 and libssl1.0
# Regex is used to ensure that we do not install libssl1.0-dev, as it is a variant that is not required
sudo apt-get install '^libssl1.0.[0-9]$' libunwind8 -y

###################################
# Download and extract PowerShell

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-7.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="80957-248">Facoltativamente, è possibile creare un collegamento simbolico per avviare PowerShell senza specificare il percorso del file binario `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="80957-248">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="80957-249">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="80957-249">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="install-as-a-net-global-tool"></a><span data-ttu-id="80957-250">Installare come strumento globale .NET</span><span class="sxs-lookup"><span data-stu-id="80957-250">Install as a .NET Global tool</span></span>

<span data-ttu-id="80957-251">Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).</span><span class="sxs-lookup"><span data-stu-id="80957-251">If you already have the [.NET Core SDK](/dotnet/core/sdk) installed, it's easy to install PowerShell as a [.NET Global tool](/dotnet/core/tools/global-tools).</span></span>

```
dotnet tool install --global PowerShell
```

<span data-ttu-id="80957-252">Il programma di installazione dello strumento DotNet aggiunge `~/.dotnet/tools` alla variabile di ambiente `PATH`.</span><span class="sxs-lookup"><span data-stu-id="80957-252">The dotnet tool installer adds `~/.dotnet/tools` to your `PATH` environment variable.</span></span> <span data-ttu-id="80957-253">La shell attualmente in esecuzione non dispone tuttavia del parametro `PATH` aggiornato.</span><span class="sxs-lookup"><span data-stu-id="80957-253">However, the currently running shell does not have the updated `PATH`.</span></span> <span data-ttu-id="80957-254">Dovrebbe essere possibile avviare PowerShell da una nuova shell digitando `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="80957-254">You should be able to start PowerShell from a new shell by typing `pwsh`.</span></span>

## <a name="binary-archives"></a><span data-ttu-id="80957-255">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="80957-255">Binary Archives</span></span>

<span data-ttu-id="80957-256">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="80957-256">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="80957-257">Dependencies</span><span class="sxs-lookup"><span data-stu-id="80957-257">Dependencies</span></span>

<span data-ttu-id="80957-258">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="80957-258">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="80957-259">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse nelle varie distribuzioni, così come per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="80957-259">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="80957-260">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="80957-260">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="80957-261">OS</span><span class="sxs-lookup"><span data-stu-id="80957-261">OS</span></span>                 | <span data-ttu-id="80957-262">Dependencies</span><span class="sxs-lookup"><span data-stu-id="80957-262">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="80957-263">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="80957-263">Ubuntu 16.04</span></span>       | <span data-ttu-id="80957-264">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="80957-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80957-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="80957-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="80957-266">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="80957-266">Ubuntu 17.10</span></span>       | <span data-ttu-id="80957-267">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="80957-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80957-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="80957-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="80957-269">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="80957-269">Ubuntu 18.04</span></span>       | <span data-ttu-id="80957-270">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="80957-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80957-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="80957-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="80957-272">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="80957-272">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="80957-273">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="80957-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80957-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="80957-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="80957-275">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="80957-275">Debian 9 (Stretch)</span></span> | <span data-ttu-id="80957-276">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="80957-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="80957-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="80957-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="80957-278">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="80957-278">CentOS 7</span></span> <br> <span data-ttu-id="80957-279">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="80957-279">Oracle Linux 7</span></span> <br> <span data-ttu-id="80957-280">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="80957-280">RHEL 7</span></span> | <span data-ttu-id="80957-281">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="80957-281">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="80957-282">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="80957-282">openSUSE 42.3</span></span> | <span data-ttu-id="80957-283">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="80957-283">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="80957-284">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="80957-284">openSUSE Leap 15</span></span> | <span data-ttu-id="80957-285">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="80957-285">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="80957-286">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="80957-286">Fedora 27</span></span> <br> <span data-ttu-id="80957-287">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="80957-287">Fedora 28</span></span> | <span data-ttu-id="80957-288">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="80957-288">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="80957-289">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie per il sistema operativo di destinazione in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="80957-289">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="80957-290">Ad esempio, il [Dockerfile Linux di Amazon][amazon-dockerfile] installa prima le dipendenze e quindi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="80957-290">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="80957-291">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="80957-291">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="80957-292">Linux</span><span class="sxs-lookup"><span data-stu-id="80957-292">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/7

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/7

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/7/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/7/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="80957-293">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="80957-293">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="80957-294">Percorsi</span><span class="sxs-lookup"><span data-stu-id="80957-294">Paths</span></span>

- <span data-ttu-id="80957-295">`$PSHOME` è `/opt/microsoft/powershell/7/`</span><span class="sxs-lookup"><span data-stu-id="80957-295">`$PSHOME` is `/opt/microsoft/powershell/7/`</span></span>
- <span data-ttu-id="80957-296">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="80957-296">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
- <span data-ttu-id="80957-297">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="80957-297">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
- <span data-ttu-id="80957-298">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="80957-298">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
- <span data-ttu-id="80957-299">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="80957-299">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
- <span data-ttu-id="80957-300">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="80957-300">Default modules will be read from `$PSHOME/Modules`</span></span>
- <span data-ttu-id="80957-301">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="80957-301">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="80957-302">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="80957-302">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="80957-303">PowerShell rispetta la [specifica XDG Base Directory][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="80957-303">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
