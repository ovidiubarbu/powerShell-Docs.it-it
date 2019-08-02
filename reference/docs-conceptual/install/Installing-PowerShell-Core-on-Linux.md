---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 07/19/2019
ms.openlocfilehash: 929b153ef784f3203cd31a0e2fc52e744a07532f
ms.sourcegitcommit: 118eb294d5a84a772e6449d42a9d9324e18ef6b9
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2019
ms.locfileid: "68372190"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="049e5-103">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="049e5-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="049e5-104">Supporta [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="049e5-104">Supports [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="049e5-105">Per le distribuzioni Linux non supportate ufficialmente, è possibile provare a installare PowerShell con il [pacchetto PowerShell Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="049e5-105">For Linux distributions that aren't officially supported, you can try to install PowerShell using the [PowerShell Snap Package][snap].</span></span> <span data-ttu-id="049e5-106">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'archivio [`tar.gz`][tar] di Linux ma sarà necessario configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="049e5-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="049e5-107">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="049e5-107">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="049e5-108">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="049e5-108">After the package is installed, run `pwsh` from a terminal.</span></span>

[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="049e5-109">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="049e5-109">Installing Preview Releases</span></span>

<span data-ttu-id="049e5-110">Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="049e5-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="049e5-111">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="049e5-111">Installing via direct download doesn't change, other than the file name.</span></span>

<span data-ttu-id="049e5-112">La tabella seguente contiene i comandi per installare i pacchetti stabili e di anteprima usando diversi strumenti di gestione dei pacchetti:</span><span class="sxs-lookup"><span data-stu-id="049e5-112">The following table contains the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="049e5-113">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="049e5-113">Distribution(s)</span></span>|<span data-ttu-id="049e5-114">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="049e5-114">Stable Command</span></span> | <span data-ttu-id="049e5-115">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="049e5-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="049e5-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="049e5-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="049e5-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="049e5-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="049e5-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="049e5-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1604"></a><span data-ttu-id="049e5-119">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="049e5-119">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="049e5-120">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="049e5-120">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="049e5-121">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="049e5-121">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="049e5-122">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-122">The preferred method is as follows:</span></span>

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

<span data-ttu-id="049e5-123">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-123">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-124">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-124">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="049e5-125">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="049e5-125">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="049e5-126">Scaricare il pacchetto Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="049e5-126">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="049e5-127">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-127">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="049e5-128">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="049e5-128">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="049e5-129">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="049e5-129">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="049e5-130">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-130">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="049e5-131">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="049e5-131">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="049e5-132">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="049e5-132">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="049e5-133">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="049e5-133">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="049e5-134">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-134">The preferred method is as follows:</span></span>

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

<span data-ttu-id="049e5-135">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-135">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-136">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-136">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="049e5-137">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="049e5-137">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="049e5-138">Scaricare il pacchetto Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="049e5-138">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="049e5-139">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-139">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="049e5-140">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="049e5-140">The `dpkg -i` command fails with unmet dependencies.</span></span> <span data-ttu-id="049e5-141">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="049e5-141">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="049e5-142">Ubuntu 18.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-142">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="049e5-143">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="049e5-143">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="049e5-144">Poiché la versione 18.10 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle), la versione è [supportata solo dalla community](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="049e5-144">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="049e5-145">L'installazione nella versione 18.10 è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="049e5-145">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="049e5-146">Per istruzioni complete, vedere [Pacchetto Snap][snap];</span><span class="sxs-lookup"><span data-stu-id="049e5-146">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="049e5-147">Debian 8</span><span class="sxs-lookup"><span data-stu-id="049e5-147">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="049e5-148">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="049e5-148">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="049e5-149">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="049e5-149">PowerShell Core, for Linux, is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="049e5-150">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-150">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl apt-transport-https

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

<span data-ttu-id="049e5-151">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-151">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-152">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-152">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

## <a name="debian-9"></a><span data-ttu-id="049e5-153">Debian 9</span><span class="sxs-lookup"><span data-stu-id="049e5-153">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="049e5-154">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="049e5-154">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="049e5-155">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="049e5-155">PowerShell Core for Linux is published to package repositories for easy installation and updates.</span></span>

<span data-ttu-id="049e5-156">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-156">The preferred method is as follows:</span></span>

```sh
# Install system components
sudo apt-get update
sudo apt-get install curl gnupg apt-transport-https

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

<span data-ttu-id="049e5-157">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-157">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-158">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-158">After registration, you can update PowerShell with `sudo apt-get upgrade powershell`.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="049e5-159">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="049e5-159">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="049e5-160">Scaricare il pacchetto Debian `powershell_6.2.0-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="049e5-160">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="049e5-161">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-161">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="049e5-162">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-162">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="049e5-163">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="049e5-163">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="049e5-164">Questo pacchetto funziona in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="049e5-164">This package works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="049e5-165">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="049e5-165">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="049e5-166">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="049e5-166">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="049e5-167">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-167">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-168">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-168">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="049e5-169">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="049e5-169">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="049e5-170">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="049e5-170">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="049e5-171">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-171">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="049e5-172">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="049e5-172">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="049e5-173">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-173">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="049e5-175">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="049e5-175">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="049e5-176">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="049e5-176">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="049e5-177">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="049e5-177">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="049e5-178">Come utente con privilegi avanzati, registrare il repository di Microsoft una volta.</span><span class="sxs-lookup"><span data-stu-id="049e5-178">As superuser, register the Microsoft repository once.</span></span> <span data-ttu-id="049e5-179">Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.</span><span class="sxs-lookup"><span data-stu-id="049e5-179">After registration, you can update PowerShell with `sudo yum update powershell`.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="049e5-180">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="049e5-180">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="049e5-181">Scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="049e5-181">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="049e5-182">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-182">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="049e5-183">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="049e5-183">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="049e5-184">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-184">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="049e5-185">openSUSE</span><span class="sxs-lookup"><span data-stu-id="049e5-185">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="049e5-186">Installazione - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="049e5-186">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="049e5-187">Installazione - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="049e5-187">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="049e5-188">Disinstallazione - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="049e5-188">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="049e5-189">Fedora</span><span class="sxs-lookup"><span data-stu-id="049e5-189">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="049e5-190">Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="049e5-190">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="049e5-191">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="049e5-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="049e5-192">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="049e5-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation and updates.</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="049e5-193">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="049e5-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="049e5-194">Scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="049e5-194">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="049e5-195">Nel terminale eseguire quindi i comandi seguenti:</span><span class="sxs-lookup"><span data-stu-id="049e5-195">Then, in the terminal, execute the following commands:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="049e5-196">È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="049e5-196">You can install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="049e5-197">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="049e5-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="049e5-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="049e5-198">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="049e5-199">Il supporto di Arch è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="049e5-199">Arch support is experimental.</span></span>

<span data-ttu-id="049e5-200">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="049e5-200">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="049e5-201">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="049e5-201">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="049e5-202">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="049e5-202">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="049e5-203">Può essere installato usando il [file binario della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="049e5-203">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="049e5-204">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="049e5-204">Packages in the AUR are community maintained; there's no official support.</span></span>

<span data-ttu-id="049e5-205">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="049e5-205">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="049e5-207">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="049e5-207">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="049e5-208">Recupero di snapd</span><span class="sxs-lookup"><span data-stu-id="049e5-208">Getting snapd</span></span>

<span data-ttu-id="049e5-209">`snapd` è necessario per l'esecuzione di pacchetti Snap.</span><span class="sxs-lookup"><span data-stu-id="049e5-209">`snapd` is required to run snaps.</span></span> <span data-ttu-id="049e5-210">Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.</span><span class="sxs-lookup"><span data-stu-id="049e5-210">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="049e5-211">Installazione tramite Snap</span><span class="sxs-lookup"><span data-stu-id="049e5-211">Installation via Snap</span></span>

<span data-ttu-id="049e5-212">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).</span><span class="sxs-lookup"><span data-stu-id="049e5-212">PowerShell Core for Linux is published to the [Snap store](https://snapcraft.io/store) for easy installation and updates.</span></span>

<span data-ttu-id="049e5-213">Il metodo preferito è il seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-213">The preferred method is as follows:</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="049e5-214">Per installare una versione di anteprima, usare il metodo seguente:</span><span class="sxs-lookup"><span data-stu-id="049e5-214">To install a preview version, use the following method:</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="049e5-215">Dopo l'installazione, Snap verrà aggiornato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="049e5-215">After installation, Snap will automatically upgrade.</span></span> <span data-ttu-id="049e5-216">È possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="049e5-216">You can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="049e5-217">Disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-217">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="049e5-218">o</span><span class="sxs-lookup"><span data-stu-id="049e5-218">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="049e5-219">Kali</span><span class="sxs-lookup"><span data-stu-id="049e5-219">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="049e5-220">Kali: installazione</span><span class="sxs-lookup"><span data-stu-id="049e5-220">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-6+deb9u2_amd64.deb
dpkg -i libicu57_57.1-6+deb9u2_amd64.deb
apt-get update && apt-get install -y curl gnupg apt-transport-https

# Add Microsoft public repository key to APT
curl https://packages.microsoft.com/keys/microsoft.asc | apt-key add -

# Add Microsoft package repository to the source list
echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-debian-stretch-prod stretch main" | tee /etc/apt/sources.list.d/powershell.list

# Install PowerShell package
apt-get update && apt-get install -y powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="049e5-221">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-221">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="049e5-222">Raspbian</span><span class="sxs-lookup"><span data-stu-id="049e5-222">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="049e5-223">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="049e5-223">Raspbian support is experimental.</span></span>

<span data-ttu-id="049e5-224">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="049e5-224">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="049e5-225">CoreCLR e PowerShell Core funzionano solo nei dispositivi Pi 2 e Pi 3, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), hanno un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="049e5-225">CoreCLR and PowerShell Core will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="049e5-226">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="049e5-226">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="049e5-227">Raspbian: installazione</span><span class="sxs-lookup"><span data-stu-id="049e5-227">Installation - Raspbian</span></span>

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
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="049e5-228">Facoltativamente, è possibile creare un collegamento simbolico per avviare PowerShell senza specificare il percorso del file binario `pwsh`.</span><span class="sxs-lookup"><span data-stu-id="049e5-228">Optionally, you can create a symbolic link to start PowerShell without specifying the path to the `pwsh` binary.</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="049e5-229">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="049e5-229">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="049e5-230">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="049e5-230">Binary Archives</span></span>

<span data-ttu-id="049e5-231">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="049e5-231">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="049e5-232">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="049e5-232">Dependencies</span></span>

<span data-ttu-id="049e5-233">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="049e5-233">PowerShell builds portable binaries for all Linux distributions.</span></span> <span data-ttu-id="049e5-234">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse nelle varie distribuzioni, così come per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="049e5-234">But, .NET Core runtime requires different dependencies on different distributions, and PowerShell does too.</span></span>

<span data-ttu-id="049e5-235">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="049e5-235">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="049e5-236">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="049e5-236">OS</span></span>                 | <span data-ttu-id="049e5-237">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="049e5-237">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="049e5-238">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="049e5-238">Ubuntu 16.04</span></span>       | <span data-ttu-id="049e5-239">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="049e5-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="049e5-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="049e5-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="049e5-241">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="049e5-241">Ubuntu 17.10</span></span>       | <span data-ttu-id="049e5-242">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="049e5-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="049e5-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="049e5-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="049e5-244">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="049e5-244">Ubuntu 18.04</span></span>       | <span data-ttu-id="049e5-245">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="049e5-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="049e5-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="049e5-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="049e5-247">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="049e5-247">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="049e5-248">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="049e5-248">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="049e5-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="049e5-249">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="049e5-250">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="049e5-250">Debian 9 (Stretch)</span></span> | <span data-ttu-id="049e5-251">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="049e5-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="049e5-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="049e5-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="049e5-253">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="049e5-253">CentOS 7</span></span> <br> <span data-ttu-id="049e5-254">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="049e5-254">Oracle Linux 7</span></span> <br> <span data-ttu-id="049e5-255">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="049e5-255">RHEL 7</span></span> | <span data-ttu-id="049e5-256">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="049e5-256">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="049e5-257">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="049e5-257">openSUSE 42.3</span></span> | <span data-ttu-id="049e5-258">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="049e5-258">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="049e5-259">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="049e5-259">openSUSE Leap 15</span></span> | <span data-ttu-id="049e5-260">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="049e5-260">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="049e5-261">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="049e5-261">Fedora 27</span></span> <br> <span data-ttu-id="049e5-262">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="049e5-262">Fedora 28</span></span> | <span data-ttu-id="049e5-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="049e5-263">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="049e5-264">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie per il sistema operativo di destinazione in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="049e5-264">To deploy PowerShell binaries on Linux distributions that aren't officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="049e5-265">Ad esempio, il [Dockerfile Linux di Amazon][amazon-dockerfile] installa prima le dipendenze e quindi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="049e5-265">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="049e5-266">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="049e5-266">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="049e5-267">Linux</span><span class="sxs-lookup"><span data-stu-id="049e5-267">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.2.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.2.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.2.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.2.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="049e5-268">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="049e5-268">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="049e5-269">Percorsi</span><span class="sxs-lookup"><span data-stu-id="049e5-269">Paths</span></span>

* <span data-ttu-id="049e5-270">`$PSHOME` è `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="049e5-270">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="049e5-271">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="049e5-271">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="049e5-272">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="049e5-272">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="049e5-273">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="049e5-273">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="049e5-274">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="049e5-274">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="049e5-275">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="049e5-275">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="049e5-276">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="049e5-276">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="049e5-277">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="049e5-277">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="049e5-278">PowerShell rispetta la [specifica XDG Base Directory][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="049e5-278">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
