---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 08/06/2018
ms.openlocfilehash: 718be0f03f136d6eb7d78fff51abdc36f6a8f0c2
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795726"
---
# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="e179f-103">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="e179f-103">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="e179f-104">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="e179f-104">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="e179f-105">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare il [pacchetto Snap di PowerShell][snap].</span><span class="sxs-lookup"><span data-stu-id="e179f-105">For Linux distributions that are not officially supported, you can try using the [PowerShell Snap Package][snap].</span></span>
<span data-ttu-id="e179f-106">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e179f-106">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e179f-107">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="e179f-107">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="e179f-108">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="e179f-108">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u1804]: #ubuntu-1804
[u1810]: #ubuntu-1810
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse
[fedora]: #fedora
[arch]: #arch-linux
[snap]: #snap-package
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="e179f-109">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="e179f-109">Installing Preview Releases</span></span>

<span data-ttu-id="e179f-110">Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e179f-110">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="e179f-111">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="e179f-111">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="e179f-112">Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:</span><span class="sxs-lookup"><span data-stu-id="e179f-112">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="e179f-113">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="e179f-113">Distribution(s)</span></span>|<span data-ttu-id="e179f-114">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="e179f-114">Stable Command</span></span> | <span data-ttu-id="e179f-115">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="e179f-115">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="e179f-116">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="e179f-116">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="e179f-117">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="e179f-117">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="e179f-118">Fedora</span><span class="sxs-lookup"><span data-stu-id="e179f-118">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="e179f-119">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e179f-119">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e179f-120">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-120">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e179f-121">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e179f-121">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-122">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-122">This is the preferred method.</span></span>

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

<span data-ttu-id="e179f-123">Come utente con privilegi avanzati, registrare il repository di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="e179f-123">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="e179f-124">A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.</span><span class="sxs-lookup"><span data-stu-id="e179f-124">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e179f-125">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-125">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e179f-126">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e179f-126">Download the Debian package `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`</span></span>
<span data-ttu-id="e179f-127">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e179f-127">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e179f-128">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-128">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e179f-129">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e179f-129">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e179f-130">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-130">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e179f-131">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-131">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e179f-132">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e179f-132">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e179f-133">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-133">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e179f-134">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e179f-134">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-135">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-135">This is the preferred method.</span></span>

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

<span data-ttu-id="e179f-136">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e179f-136">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e179f-137">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e179f-137">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e179f-138">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e179f-138">Download the Debian package `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`</span></span>
<span data-ttu-id="e179f-139">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e179f-139">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e179f-140">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-140">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e179f-141">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e179f-141">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e179f-142">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-142">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e179f-143">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-143">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="e179f-144">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e179f-144">Ubuntu 18.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="e179f-145">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-145">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="e179f-146">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e179f-146">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-147">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-147">This is the preferred method.</span></span>

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

<span data-ttu-id="e179f-148">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e179f-148">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="e179f-149">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-149">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="e179f-150">Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e179f-150">Download the Debian package `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`</span></span>
<span data-ttu-id="e179f-151">dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e179f-151">from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="e179f-152">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-152">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e179f-153">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e179f-153">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e179f-154">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-154">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1804"></a><span data-ttu-id="e179f-155">Ubuntu 18.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-155">Uninstallation - Ubuntu 18.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a><span data-ttu-id="e179f-156">Ubuntu 18.10</span><span class="sxs-lookup"><span data-stu-id="e179f-156">Ubuntu 18.10</span></span>

> [!NOTE]
> <span data-ttu-id="e179f-157">Poiché la versione 18.10 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle), la versione è [supportata solo dalla community](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span><span class="sxs-lookup"><span data-stu-id="e179f-157">As 18.10 is an [interim release](https://www.ubuntu.com/about/release-cycle), it is only [community supported](https://docs.microsoft.com/en-us/powershell/scripting/powershell-support-lifecycle?view=powershell-6).</span></span>

<span data-ttu-id="e179f-158">L'installazione nella versione 18.10 è supportata tramite `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e179f-158">Installing on 18.10 is supported via `snapd`.</span></span> <span data-ttu-id="e179f-159">Per istruzioni complete, vedere [Pacchetto Snap][snap].</span><span class="sxs-lookup"><span data-stu-id="e179f-159">See [Snap Package][snap] for full instructions;</span></span>

## <a name="debian-8"></a><span data-ttu-id="e179f-160">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e179f-160">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e179f-161">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-161">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e179f-162">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e179f-162">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-163">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-163">This is the preferred method.</span></span>

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

<span data-ttu-id="e179f-164">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e179f-164">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e179f-165">Debian 8: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-165">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e179f-166">Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.8_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e179f-166">Download the Debian package `powershell_6.1.0-1.debian.8_amd64.deb`</span></span>
<span data-ttu-id="e179f-167">dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="e179f-167">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e179f-168">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-168">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="e179f-169">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="e179f-169">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="e179f-170">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-170">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e179f-171">Debian 8: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-171">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e179f-172">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e179f-172">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e179f-173">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-173">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e179f-174">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e179f-174">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-175">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-175">This is the preferred method.</span></span>

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

<span data-ttu-id="e179f-176">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e179f-176">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e179f-177">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-177">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e179f-178">Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.9_amd64.deb`</span><span class="sxs-lookup"><span data-stu-id="e179f-178">Download the Debian package `powershell_6.1.0-1.debian.9_amd64.deb`</span></span>
<span data-ttu-id="e179f-179">dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="e179f-179">from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="e179f-180">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-180">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e179f-181">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-181">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e179f-182">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e179f-182">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="e179f-183">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e179f-183">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e179f-184">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e179f-184">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e179f-185">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e179f-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e179f-186">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-186">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e179f-187">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-187">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e179f-188">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e179f-188">Using [CentOS 7][], download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e179f-189">dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="e179f-189">from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="e179f-190">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-190">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e179f-191">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e179f-191">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e179f-192">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-192">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e179f-194">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e179f-194">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e179f-195">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="e179f-195">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e179f-196">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e179f-196">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e179f-197">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e179f-197">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e179f-198">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e179f-198">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e179f-199">Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e179f-199">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e179f-200">dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="e179f-200">from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="e179f-201">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-201">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e179f-202">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e179f-202">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e179f-203">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-203">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a><span data-ttu-id="e179f-204">openSUSE</span><span class="sxs-lookup"><span data-stu-id="e179f-204">openSUSE</span></span>

### <a name="installation---opensuse-423"></a><span data-ttu-id="e179f-205">Installazione - openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e179f-205">Installation - openSUSE 42.3</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar libicu52_1

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="installation---opensuse-leap-15"></a><span data-ttu-id="e179f-206">Installazione - openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e179f-206">Installation - openSUSE Leap 15</span></span>

```sh
# Install dependencies
zypper update && zypper --non-interactive install curl tar gzip libopenssl1_0_0 libicu60_2

# Download the powershell '.tar.gz' archive
curl -L https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-linux-x64.tar.gz -o /tmp/powershell.tar.gz

# Create the target folder where powershell will be placed
mkdir -p /opt/microsoft/powershell/6.1.0

# Expand powershell to the target folder
tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.1.0

# Set execute permissions
chmod +x /opt/microsoft/powershell/6.1.0/pwsh

# Create the symbolic link that points to pwsh
ln -s /opt/microsoft/powershell/6.1.0/pwsh /usr/bin/pwsh

# Start PowerShell
pwsh
```

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a><span data-ttu-id="e179f-207">Disinstallazione - openSUSE 42.3, openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e179f-207">Uninstallation - openSUSE 42.3, openSUSE Leap 15</span></span>

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a><span data-ttu-id="e179f-208">Fedora</span><span class="sxs-lookup"><span data-stu-id="e179f-208">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="e179f-209">Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e179f-209">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="e179f-210">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e179f-210">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e179f-211">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e179f-211">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="e179f-212">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e179f-212">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="e179f-213">Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span><span class="sxs-lookup"><span data-stu-id="e179f-213">Download the RPM package `powershell-6.1.0-1.rhel.7.x86_64.rpm`</span></span>
<span data-ttu-id="e179f-214">dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="e179f-214">from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="e179f-215">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e179f-215">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e179f-216">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e179f-216">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="e179f-217">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e179f-217">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e179f-218">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e179f-218">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="e179f-219">Il supporto di Arch è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="e179f-219">Arch support is experimental.</span></span>

<span data-ttu-id="e179f-220">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="e179f-220">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e179f-221">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e179f-221">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e179f-222">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e179f-222">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e179f-223">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e179f-223">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e179f-224">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="e179f-224">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e179f-225">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e179f-225">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a><span data-ttu-id="e179f-227">Pacchetto Snap</span><span class="sxs-lookup"><span data-stu-id="e179f-227">Snap Package</span></span>

### <a name="getting-snapd"></a><span data-ttu-id="e179f-228">Recupero di snapd</span><span class="sxs-lookup"><span data-stu-id="e179f-228">Getting snapd</span></span>

<span data-ttu-id="e179f-229">`snapd` è necessario per l'esecuzione di pacchetti Snap.</span><span class="sxs-lookup"><span data-stu-id="e179f-229">`snapd` is required to run snaps.</span></span>
<span data-ttu-id="e179f-230">Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.</span><span class="sxs-lookup"><span data-stu-id="e179f-230">Use [these instructions](https://docs.snapcraft.io/core/install) to make sure you have `snapd` installed.</span></span>

### <a name="installation-via-snap"></a><span data-ttu-id="e179f-231">Installazione tramite Snap</span><span class="sxs-lookup"><span data-stu-id="e179f-231">Installation via Snap</span></span>

<span data-ttu-id="e179f-232">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).</span><span class="sxs-lookup"><span data-stu-id="e179f-232">PowerShell Core, for Linux, is published to the [Snap store](https://snapcraft.io/store) for easy installation (and updates).</span></span>
<span data-ttu-id="e179f-233">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e179f-233">This is the preferred method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

<span data-ttu-id="e179f-234">Se si vuole installare la versione di anteprima, usare il metodo seguente.</span><span class="sxs-lookup"><span data-stu-id="e179f-234">If you want to install preview version, use following method.</span></span>

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

<span data-ttu-id="e179f-235">Dopo l'installazione, Snap eseguirà automaticamente l'aggiornamento, ma è possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="e179f-235">After installing Snap will automatically upgrade, but you can trigger an upgrade using `sudo snap refresh powershell` or `sudo snap refresh powershell-preview`.</span></span>

### <a name="uninstallation"></a><span data-ttu-id="e179f-236">Disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-236">Uninstallation</span></span>

```sh
sudo snap remove powershell
```

<span data-ttu-id="e179f-237">o</span><span class="sxs-lookup"><span data-stu-id="e179f-237">or</span></span>

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a><span data-ttu-id="e179f-238">Kali</span><span class="sxs-lookup"><span data-stu-id="e179f-238">Kali</span></span>

### <a name="installation---kali"></a><span data-ttu-id="e179f-239">Kali: installazione</span><span class="sxs-lookup"><span data-stu-id="e179f-239">Installation - Kali</span></span>

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

### <a name="uninstallation---kali"></a><span data-ttu-id="e179f-240">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-240">Uninstallation - Kali</span></span>

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a><span data-ttu-id="e179f-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e179f-241">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="e179f-242">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="e179f-242">Raspbian support is experimental.</span></span>

<span data-ttu-id="e179f-243">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e179f-243">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="e179f-244">Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="e179f-244">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="e179f-245">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="e179f-245">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation---raspbian"></a><span data-ttu-id="e179f-246">Raspbian: installazione</span><span class="sxs-lookup"><span data-stu-id="e179f-246">Installation - Raspbian</span></span>

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

<span data-ttu-id="e179f-247">Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"</span><span class="sxs-lookup"><span data-stu-id="e179f-247">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e179f-248">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e179f-248">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e179f-249">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="e179f-249">Binary Archives</span></span>

<span data-ttu-id="e179f-250">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="e179f-250">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e179f-251">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e179f-251">Dependencies</span></span>

<span data-ttu-id="e179f-252">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="e179f-252">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e179f-253">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="e179f-253">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e179f-254">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="e179f-254">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="e179f-255">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e179f-255">OS</span></span>                 | <span data-ttu-id="e179f-256">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e179f-256">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e179f-257">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e179f-257">Ubuntu 14.04</span></span>       | <span data-ttu-id="e179f-258">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-258">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e179f-259">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e179f-260">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e179f-260">Ubuntu 16.04</span></span>       | <span data-ttu-id="e179f-261">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-261">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e179f-262">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e179f-263">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="e179f-263">Ubuntu 17.10</span></span>       | <span data-ttu-id="e179f-264">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-264">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e179f-265">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e179f-266">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="e179f-266">Ubuntu 18.04</span></span>       | <span data-ttu-id="e179f-267">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-267">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="e179f-268">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="e179f-269">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e179f-269">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e179f-270">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-270">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e179f-271">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e179f-272">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e179f-272">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e179f-273">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e179f-273">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e179f-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e179f-274">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e179f-275">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e179f-275">CentOS 7</span></span> <br> <span data-ttu-id="e179f-276">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e179f-276">Oracle Linux 7</span></span> <br> <span data-ttu-id="e179f-277">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e179f-277">RHEL 7</span></span> | <span data-ttu-id="e179f-278">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e179f-278">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e179f-279">openSUSE 42.3</span><span class="sxs-lookup"><span data-stu-id="e179f-279">openSUSE 42.3</span></span> | <span data-ttu-id="e179f-280">libcurl4, libopenssl1_0_0, libicu52_1</span><span class="sxs-lookup"><span data-stu-id="e179f-280">libcurl4, libopenssl1_0_0, libicu52_1</span></span> |
| <span data-ttu-id="e179f-281">openSUSE Leap 15</span><span class="sxs-lookup"><span data-stu-id="e179f-281">openSUSE Leap 15</span></span> | <span data-ttu-id="e179f-282">libcurl4, libopenssl1_0_0, libicu60_2</span><span class="sxs-lookup"><span data-stu-id="e179f-282">libcurl4, libopenssl1_0_0, libicu60_2</span></span> |
| <span data-ttu-id="e179f-283">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="e179f-283">Fedora 27</span></span> <br> <span data-ttu-id="e179f-284">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="e179f-284">Fedora 28</span></span> | <span data-ttu-id="e179f-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e179f-285">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e179f-286">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e179f-286">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="e179f-287">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="e179f-287">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e179f-288">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="e179f-288">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e179f-289">Linux</span><span class="sxs-lookup"><span data-stu-id="e179f-289">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="e179f-290">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="e179f-290">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e179f-291">Percorsi</span><span class="sxs-lookup"><span data-stu-id="e179f-291">Paths</span></span>

* <span data-ttu-id="e179f-292">`$PSHOME` è `/opt/microsoft/powershell/6.1.0/`</span><span class="sxs-lookup"><span data-stu-id="e179f-292">`$PSHOME` is `/opt/microsoft/powershell/6.1.0/`</span></span>
* <span data-ttu-id="e179f-293">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e179f-293">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e179f-294">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e179f-294">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e179f-295">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e179f-295">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e179f-296">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e179f-296">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e179f-297">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e179f-297">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e179f-298">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e179f-298">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e179f-299">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="e179f-299">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e179f-300">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="e179f-300">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
