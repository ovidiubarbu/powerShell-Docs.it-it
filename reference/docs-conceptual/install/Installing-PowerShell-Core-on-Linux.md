---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 08/06/2018
ms.openlocfilehash: 06194550f4e73f9dd38f8cdc25f6c7f698cafce2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086562"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e78f6-103">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="e78f6-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e78f6-104">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e78f6-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810],  [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e78f6-105">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare il [pacchetto Snap di PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="e78f6-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="e78f6-106">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e78f6-107">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="e78f6-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e78f6-108">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="e78f6-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
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

## <a name="installing-preview-releases"></a><span data-ttu-id="e78f6-109">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="e78f6-109">Installing Preview Releases</span></span>

<span data-ttu-id="e78f6-110">Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e78f6-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e78f6-111">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="e78f6-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e78f6-112">Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:</span><span class="sxs-lookup"><span data-stu-id="e78f6-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e78f6-113">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="e78f6-113">Distribution(s)</span></span>|<span data-ttu-id="e78f6-114">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="e78f6-114">Stable Command</span></span> | <span data-ttu-id="e78f6-115">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="e78f6-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e78f6-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e78f6-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e78f6-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e78f6-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e78f6-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e78f6-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e78f6-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e78f6-120">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e78f6-121">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-122">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-122">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/14.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e78f6-123">Come utente con privilegi avanzati, registrare il repository di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e78f6-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e78f6-124">A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.</span><span class="sxs-lookup"><span data-stu-id="e78f6-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e78f6-125">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e78f6-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e78f6-126">Scaricare il pacchetto Debian `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e78f6-126">Download the Debian package `powershell_6.2.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="e78f6-127">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e78f6-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e78f6-128">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e78f6-129">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e78f6-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e78f6-130">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e78f6-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e78f6-131">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e78f6-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e78f6-133">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e78f6-134">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-135">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-135">This is the preferred method.</span></span>

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

<span data-ttu-id="e78f6-136">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e78f6-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e78f6-137">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e78f6-138">Scaricare il pacchetto Debian `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e78f6-138">Download the Debian package `powershell_6.2.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="e78f6-139">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e78f6-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e78f6-140">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e78f6-141">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e78f6-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e78f6-142">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e78f6-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e78f6-143">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e78f6-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e78f6-145">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e78f6-146">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-147">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-147">This is the preferred method.</span></span>

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

<span data-ttu-id="e78f6-148">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e78f6-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e78f6-149">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e78f6-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e78f6-150">Scaricare il pacchetto Debian `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e78f6-150">Download the Debian package `powershell_6.2.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="e78f6-151">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e78f6-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e78f6-152">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e78f6-153">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e78f6-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e78f6-154">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e78f6-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e78f6-155">Ubuntu 18.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e78f6-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e78f6-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="e78f6-157">Poiché la versione 18.10 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle), la versione è [supportata solo dalla community](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="e78f6-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="e78f6-158">L'installazione nella versione 18.10 è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e78f6-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="e78f6-159">Per istruzioni complete, vedere [Pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="e78f6-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="e78f6-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e78f6-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e78f6-161">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e78f6-162">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-163">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-163">This is the preferred method.</span></span>

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

<span data-ttu-id="e78f6-164">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e78f6-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

## <a name="debian-9"></a><span data-ttu-id="e78f6-165">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e78f6-165">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e78f6-166">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-166">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e78f6-167">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-168">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-168">This is the preferred method.</span></span>

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

<span data-ttu-id="e78f6-169">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e78f6-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e78f6-170">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e78f6-170">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e78f6-171">Scaricare il pacchetto Debian `powershell_6.2.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e78f6-171">Download the Debian package `powershell_6.2.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="e78f6-172">dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="e78f6-172">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e78f6-173">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-173">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.2.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e78f6-174">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-174">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e78f6-175">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e78f6-175">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e78f6-176">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e78f6-176">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e78f6-177">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e78f6-177">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e78f6-178">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e78f6-178">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e78f6-179">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e78f6-179">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e78f6-180">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e78f6-180">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e78f6-181">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e78f6-181">Using [CentOS 7][], download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e78f6-182">dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="e78f6-182">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e78f6-183">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-183">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e78f6-184">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e78f6-184">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e78f6-185">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-185">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e78f6-187">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e78f6-187">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e78f6-188">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="e78f6-188">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e78f6-189">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e78f6-189">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e78f6-190">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e78f6-190">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e78f6-191">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e78f6-191">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e78f6-192">Scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e78f6-192">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e78f6-193">dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e78f6-193">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e78f6-194">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-194">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e78f6-195">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e78f6-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e78f6-196">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-196">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e78f6-197">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e78f6-197">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e78f6-198">Installazione - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e78f6-198">Installation - openSUSE 42.3</span></span>

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

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e78f6-199">Installazione - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e78f6-199">Installation - openSUSE Leap 15</span></span>

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e78f6-200">Disinstallazione - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e78f6-200">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e78f6-201">Fedora</span><span class="sxs-lookup"><span data-stu-id="e78f6-201">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e78f6-202">Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e78f6-202">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e78f6-203">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e78f6-203">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e78f6-204">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e78f6-204">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e78f6-205">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e78f6-205">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e78f6-206">Scaricare il pacchetto RPM `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e78f6-206">Download the RPM package `powershell-6.2.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e78f6-207">dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="e78f6-207">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e78f6-208">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e78f6-208">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.2.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e78f6-209">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e78f6-209">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e78f6-210">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e78f6-210">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e78f6-211">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e78f6-211">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e78f6-212">Il supporto di Arch è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="e78f6-212">Arch support is experimental.</span></span>

<span data-ttu-id="e78f6-213">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="e78f6-213">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e78f6-214">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e78f6-214">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e78f6-215">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e78f6-215">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e78f6-216">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e78f6-216">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e78f6-217">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="e78f6-217">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e78f6-218">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e78f6-218">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e78f6-220">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="e78f6-220">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e78f6-221">Recupero di snapd</span><span class="sxs-lookup"><span data-stu-id="e78f6-221">Getting snapd</span></span>

<span data-ttu-id="e78f6-222">`snapd` è necessario per l'esecuzione di pacchetti Snap.</span><span class="sxs-lookup"><span data-stu-id="e78f6-222">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="e78f6-223">Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e78f6-223">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e78f6-224">Installazione tramite Snap</span><span class="sxs-lookup"><span data-stu-id="e78f6-224">Installation via Snap</span></span>

<span data-ttu-id="e78f6-225">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).</span><span class="sxs-lookup"><span data-stu-id="e78f6-225">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="e78f6-226">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e78f6-226">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e78f6-227">Se si vuole installare la versione di anteprima, usare il metodo seguente.</span><span class="sxs-lookup"><span data-stu-id="e78f6-227">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e78f6-228">Dopo l'installazione, Snap eseguirà automaticamente l'aggiornamento, ma è possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e78f6-228">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e78f6-229">Disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-229">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e78f6-230">o</span><span class="sxs-lookup"><span data-stu-id="e78f6-230">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e78f6-231">Kali</span><span class="sxs-lookup"><span data-stu-id="e78f6-231">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e78f6-232">Kali: installazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-232">Installation - Kali</span></span>

```sh
# Download & Install prerequisites
wget http://ftp.us.debian.org/debian/pool/main/i/icu/libicu57_57.1-9_amd64.deb
dpkg -i libicu57_57.1-9_amd64.deb
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

### <a name="uninstallation---kali"></a><span data-ttu-id="e78f6-233">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-233">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e78f6-234">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e78f6-234">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e78f6-235">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="e78f6-235">Raspbian support is experimental.</span></span>

<span data-ttu-id="e78f6-236">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e78f6-236">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e78f6-237">Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="e78f6-237">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e78f6-238">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="e78f6-238">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e78f6-239">Raspbian: installazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-239">Installation - Raspbian</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.2.0/powershell-6.2.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.2.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="e78f6-240">Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"</span><span class="sxs-lookup"><span data-stu-id="e78f6-240">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e78f6-241">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-241">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e78f6-242">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="e78f6-242">Binary Archives</span></span>

<span data-ttu-id="e78f6-243">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="e78f6-243">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e78f6-244">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e78f6-244">Dependencies</span></span>

<span data-ttu-id="e78f6-245">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="e78f6-245">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e78f6-246">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="e78f6-246">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e78f6-247">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="e78f6-247">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e78f6-248">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e78f6-248">OS</span></span>                 | <span data-ttu-id="e78f6-249">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e78f6-249">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e78f6-250">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-250">Ubuntu 14.04</span></span>       | <span data-ttu-id="e78f6-251">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-251">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e78f6-252">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e78f6-253">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-253">Ubuntu 16.04</span></span>       | <span data-ttu-id="e78f6-254">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e78f6-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e78f6-256">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e78f6-256">Ubuntu 17.10</span></span>       | <span data-ttu-id="e78f6-257">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e78f6-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e78f6-259">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e78f6-259">Ubuntu 18.04</span></span>       | <span data-ttu-id="e78f6-260">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e78f6-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e78f6-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e78f6-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e78f6-263">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e78f6-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e78f6-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e78f6-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e78f6-266">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e78f6-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e78f6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e78f6-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e78f6-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e78f6-268">CentOS 7</span></span> <br> <span data-ttu-id="e78f6-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e78f6-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="e78f6-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e78f6-270">RHEL 7</span></span> | <span data-ttu-id="e78f6-271">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e78f6-271">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e78f6-272">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e78f6-272">openSUSE 42.3</span></span> | <span data-ttu-id="e78f6-273">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e78f6-273">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e78f6-274">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e78f6-274">openSUSE Leap 15</span></span> | <span data-ttu-id="e78f6-275">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e78f6-275">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e78f6-276">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e78f6-276">Fedora 27</span></span> <br> <span data-ttu-id="e78f6-277">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e78f6-277">Fedora 28</span></span> | <span data-ttu-id="e78f6-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e78f6-278">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e78f6-279">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e78f6-279">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e78f6-280">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="e78f6-280">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e78f6-281">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="e78f6-281">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e78f6-282">Linux</span><span class="sxs-lookup"><span data-stu-id="e78f6-282">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e78f6-283">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="e78f6-283">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e78f6-284">Percorsi</span><span class="sxs-lookup"><span data-stu-id="e78f6-284">Paths</span></span>

* <span data-ttu-id="e78f6-285">`$PSHOME` è `/opt/microsoft/powershell/6.2.0/`</span><span class="sxs-lookup"><span data-stu-id="e78f6-285">`$PSHOME` is `/opt/microsoft/powershell/6.2.0/`</span></span>
* <span data-ttu-id="e78f6-286">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e78f6-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e78f6-287">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e78f6-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e78f6-288">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e78f6-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e78f6-289">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e78f6-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e78f6-290">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e78f6-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e78f6-291">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e78f6-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e78f6-292">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="e78f6-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e78f6-293">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="e78f6-293">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
