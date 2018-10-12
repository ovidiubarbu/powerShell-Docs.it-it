---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 08/06/2018
ms.openlocfilehash: acd88f686ce6a657c9ccda9d2615d4ab355ddcbe
ms.sourcegitcommit: 601609575a3214ea7086a3bcb586ae0d1df3d418
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532953"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="cc131-103">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="cc131-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="cc131-104">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="cc131-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="cc131-105">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare il [pacchetto Snap di PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="cc131-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="cc131-106">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="cc131-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="cc131-107">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="cc131-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="cc131-108">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="cc131-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u18]: #ubuntu-1810
[u18]: #ubuntu-1804
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-423
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="cc131-109">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="cc131-109">Installing Preview Releases</span></span>

<span data-ttu-id="cc131-110">Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cc131-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="cc131-111">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="cc131-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="cc131-112">Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:</span><span class="sxs-lookup"><span data-stu-id="cc131-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="cc131-113">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="cc131-113">Distribution(s)</span></span>|<span data-ttu-id="cc131-114">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="cc131-114">Stable Command</span></span> | <span data-ttu-id="cc131-115">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="cc131-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="cc131-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="cc131-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="cc131-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="cc131-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="cc131-118">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="cc131-118">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="cc131-119">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc131-119">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="cc131-120">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cc131-120">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="cc131-121">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-121">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="cc131-122">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="cc131-122">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-123">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-123">This is the preferred method.</span></span>

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

<span data-ttu-id="cc131-124">Come utente con privilegi avanzati, registrare il repository di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="cc131-124">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="cc131-125">A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.</span><span class="sxs-lookup"><span data-stu-id="cc131-125">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="cc131-126">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-126">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="cc131-127">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cc131-127">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="cc131-128">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cc131-128">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cc131-129">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-129">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cc131-130">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="cc131-130">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cc131-131">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-131">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="cc131-132">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-132">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="cc131-133">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cc131-133">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="cc131-134">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-134">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="cc131-135">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="cc131-135">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-136">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-136">This is the preferred method.</span></span>

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

<span data-ttu-id="cc131-137">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="cc131-137">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="cc131-138">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cc131-138">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="cc131-139">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cc131-139">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="cc131-140">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cc131-140">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cc131-141">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-141">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cc131-142">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="cc131-142">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cc131-143">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-143">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="cc131-144">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-144">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="cc131-145">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cc131-145">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-146">Il supporto di Ubuntu 18.04 è stato aggiunto dopo `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="cc131-146">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="cc131-147">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-147">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="cc131-148">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="cc131-148">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-149">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-149">This is the preferred method.</span></span>

```sh
# Download the Microsoft repository GPG keys
wget -q https://packages.microsoft.com/config/ubuntu/18.04/packages-microsoft-prod.deb

# Register the Microsoft repository GPG keys
sudo dpkg -i packages-microsoft-prod.deb

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cc131-150">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="cc131-150">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="cc131-151">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-151">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="cc131-152">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cc131-152">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="cc131-153">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="cc131-153">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="cc131-154">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cc131-155">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="cc131-155">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cc131-156">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-156">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="cc131-157">Ubuntu 18.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-157">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="cc131-158">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="cc131-158">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-159">Il supporto di Ubuntu 18.10 è stato aggiunto dopo `6.1.0-preview.3`.</span><span class="sxs-lookup"><span data-stu-id="cc131-159">Support for Ubuntu 18.10 was added after `6.1.0-preview.3`.</span></span>
> <span data-ttu-id="cc131-160">Poiché la versione 18.10 è una build giornaliera, è supportata solo dalla community.</span><span class="sxs-lookup"><span data-stu-id="cc131-160">As 18.10 is a daily build, it is only community supported.</span></span>

<span data-ttu-id="cc131-161">L'installazione nella versione 18.10 è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cc131-161">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="cc131-162">Per istruzioni complete, vedere [Pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="cc131-162">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="cc131-163">Debian 8</span><span class="sxs-lookup"><span data-stu-id="cc131-163">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="cc131-164">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-164">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="cc131-165">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="cc131-165">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-166">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-166">This is the preferred method.</span></span>

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

<span data-ttu-id="cc131-167">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="cc131-167">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="cc131-168">Debian 8: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-168">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="cc131-169">Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cc131-169">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="cc131-170">dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="cc131-170">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cc131-171">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-171">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="cc131-172">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="cc131-172">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="cc131-173">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-173">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="cc131-174">Debian 8: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-174">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="cc131-175">Debian 9</span><span class="sxs-lookup"><span data-stu-id="cc131-175">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="cc131-176">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-176">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="cc131-177">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="cc131-177">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-178">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-178">This is the preferred method.</span></span>

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

<span data-ttu-id="cc131-179">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="cc131-179">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="cc131-180">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-180">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="cc131-181">Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="cc131-181">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="cc131-182">dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="cc131-182">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="cc131-183">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="cc131-184">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="cc131-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cc131-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-186">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="cc131-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="cc131-187">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="cc131-188">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="cc131-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cc131-189">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="cc131-190">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="cc131-191">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cc131-191">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cc131-192">dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="cc131-192">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="cc131-193">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-193">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cc131-194">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cc131-194">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="cc131-195">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-195">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cc131-197">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="cc131-197">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cc131-198">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="cc131-198">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cc131-199">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="cc131-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="cc131-200">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-200">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cc131-201">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-201">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="cc131-202">Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cc131-202">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cc131-203">dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="cc131-203">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="cc131-204">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-204">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cc131-205">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cc131-205">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="cc131-206">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-206">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a><span data-ttu-id="cc131-207">OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cc131-207">OpenSUSE 42.3</span></span>

<span data-ttu-id="cc131-208">Durante l'installazione di PowerShell Core, `zypper` può segnalare l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="cc131-208">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.1.0-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.1.0-1.rhel.7.x86_64
 Solution 2: break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="cc131-209">In questo caso, verificare che sia presente una libreria `libcurl` compatibile assicurandosi che il comando seguente indichi il pacchetto `libcurl4` come installato:</span><span class="sxs-lookup"><span data-stu-id="cc131-209">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="cc131-210">Scegliere quindi la soluzione `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` quando si installa il pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cc131-210">Then choose the `break powershell-6.1.0-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-423"></a><span data-ttu-id="cc131-211">OpenSUSE 42.3: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="cc131-211">Installation via Package Repository (preferred) - OpenSUSE 42.3</span></span>

<span data-ttu-id="cc131-212">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="cc131-212">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Repository
zypper ar https://packages.microsoft.com/rhel/7/prod/

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-423"></a><span data-ttu-id="cc131-213">OpenSUSE 42.3: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="cc131-213">Installation via Direct Download - OpenSUSE 42.3</span></span>

<span data-ttu-id="cc131-214">Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="cc131-214">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cc131-215">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cc131-215">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a><span data-ttu-id="cc131-216">OpenSUSE 42.3: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-216">Uninstallation - OpenSUSE 42.3</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="cc131-217">Fedora</span><span class="sxs-lookup"><span data-stu-id="cc131-217">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-218">Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="cc131-218">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="cc131-219">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cc131-219">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="cc131-220">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="cc131-220">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="cc131-221">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cc131-221">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="cc131-222">Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="cc131-222">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="cc131-223">dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="cc131-223">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="cc131-224">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="cc131-224">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="cc131-225">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="cc131-225">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="cc131-226">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cc131-226">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="cc131-227">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="cc131-227">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-228">Il supporto di Arch è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="cc131-228">Arch support is experimental.</span></span>

<span data-ttu-id="cc131-229">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="cc131-229">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="cc131-230">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="cc131-230">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="cc131-231">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="cc131-231">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="cc131-232">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="cc131-232">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="cc131-233">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="cc131-233">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="cc131-234">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="cc131-234">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="cc131-236">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="cc131-236">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="cc131-237">Recupero di snapd</span><span class="sxs-lookup"><span data-stu-id="cc131-237">Getting snapd</span></span>

<span data-ttu-id="cc131-238">`snapd` è necessario per l'esecuzione di pacchetti Snap.</span><span class="sxs-lookup"><span data-stu-id="cc131-238">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="cc131-239">Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.</span><span class="sxs-lookup"><span data-stu-id="cc131-239">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="cc131-240">Installazione tramite Snap</span><span class="sxs-lookup"><span data-stu-id="cc131-240">Installation via Snap</span></span>

<span data-ttu-id="cc131-241">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).</span><span class="sxs-lookup"><span data-stu-id="cc131-241">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="cc131-242">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="cc131-242">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="cc131-243">Dopo l'installazione, Snap eseguirà automaticamente l'aggiornamento, ma è possibile attivare un aggiornamento usando `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="cc131-243">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="cc131-244">Disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-244">Uninstallation</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="cc131-245">Kali</span><span class="sxs-lookup"><span data-stu-id="cc131-245">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-246">Il supporto di Kali attualmente non funziona.</span><span class="sxs-lookup"><span data-stu-id="cc131-246">Kali support is not currently working.</span></span> <span data-ttu-id="cc131-247">Usare il [pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="cc131-247">Please use the [Snap package][snap] instead.</span></span>

### <a name="installation"></a><span data-ttu-id="cc131-248">Installazione</span><span class="sxs-lookup"><span data-stu-id="cc131-248">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a><span data-ttu-id="cc131-249">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-249">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="cc131-250">Raspbian</span><span class="sxs-lookup"><span data-stu-id="cc131-250">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="cc131-251">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="cc131-251">Raspbian support is experimental.</span></span>

<span data-ttu-id="cc131-252">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="cc131-252">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="cc131-253">Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="cc131-253">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="cc131-254">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="cc131-254">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="cc131-255">Installazione</span><span class="sxs-lookup"><span data-stu-id="cc131-255">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.1.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="cc131-256">Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"</span><span class="sxs-lookup"><span data-stu-id="cc131-256">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="cc131-257">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="cc131-257">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="cc131-258">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="cc131-258">Binary Archives</span></span>

<span data-ttu-id="cc131-259">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="cc131-259">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="cc131-260">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="cc131-260">Dependencies</span></span>

<span data-ttu-id="cc131-261">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="cc131-261">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="cc131-262">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="cc131-262">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="cc131-263">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="cc131-263">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="cc131-264">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="cc131-264">OS</span></span>                 | <span data-ttu-id="cc131-265">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="cc131-265">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="cc131-266">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="cc131-266">Ubuntu 14.04</span></span>       | <span data-ttu-id="cc131-267">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cc131-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cc131-269">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="cc131-269">Ubuntu 16.04</span></span>       | <span data-ttu-id="cc131-270">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="cc131-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="cc131-272">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="cc131-272">Ubuntu 17.10</span></span>       | <span data-ttu-id="cc131-273">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="cc131-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="cc131-275">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="cc131-275">Ubuntu 18.04</span></span>       | <span data-ttu-id="cc131-276">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-276">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="cc131-277">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="cc131-278">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="cc131-278">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="cc131-279">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-279">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="cc131-280">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="cc131-281">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="cc131-281">Debian 9 (Stretch)</span></span> | <span data-ttu-id="cc131-282">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="cc131-282">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="cc131-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="cc131-283">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="cc131-284">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="cc131-284">CentOS 7</span></span> <br> <span data-ttu-id="cc131-285">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="cc131-285">Oracle Linux 7</span></span> <br> <span data-ttu-id="cc131-286">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="cc131-286">RHEL 7</span></span> <br> <span data-ttu-id="cc131-287">OpenSUSE OpenSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="cc131-287">OpenSUSE OpenSUSE 42.3</span></span> | <span data-ttu-id="cc131-288">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="cc131-288">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="cc131-289">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="cc131-289">Fedora 27</span></span> <br> <span data-ttu-id="cc131-290">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="cc131-290">Fedora 28</span></span> | <span data-ttu-id="cc131-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="cc131-291">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="cc131-292">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="cc131-292">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="cc131-293">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="cc131-293">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="cc131-294">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="cc131-294">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="cc131-295">Linux</span><span class="sxs-lookup"><span data-stu-id="cc131-295">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="cc131-296">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="cc131-296">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="cc131-297">Percorsi</span><span class="sxs-lookup"><span data-stu-id="cc131-297">Paths</span></span>

* <span data-ttu-id="cc131-298">`$PSHOME` è `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="cc131-298">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="cc131-299">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cc131-299">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="cc131-300">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="cc131-300">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="cc131-301">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cc131-301">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cc131-302">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="cc131-302">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="cc131-303">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="cc131-303">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="cc131-304">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="cc131-304">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="cc131-305">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="cc131-305">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="cc131-306">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="cc131-306">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
