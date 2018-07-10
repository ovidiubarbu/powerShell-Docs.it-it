# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="1fcde-101">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="1fcde-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="1fcde-102">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="1fcde-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.10][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="1fcde-103">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="1fcde-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="1fcde-104">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="1fcde-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="1fcde-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="1fcde-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1710
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="installing-preview-releases"></a><span data-ttu-id="1fcde-107">Installazione di versioni di anteprima</span><span class="sxs-lookup"><span data-stu-id="1fcde-107">Installing Preview Releases</span></span>

<span data-ttu-id="1fcde-108">Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.</span><span class="sxs-lookup"><span data-stu-id="1fcde-108">When installing a PowerShell Core Preview release for Linux via a Package Repository, the package name changes from `powershell` to `powershell-preview`.</span></span>

<span data-ttu-id="1fcde-109">L'installazione tramite download diretto non cambia, tranne per il nome del file.</span><span class="sxs-lookup"><span data-stu-id="1fcde-109">Installing via direct download does not change, other than the file name.</span></span>

<span data-ttu-id="1fcde-110">Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:</span><span class="sxs-lookup"><span data-stu-id="1fcde-110">Here is a table of the commands to install the stable and preview packages using the various package managers:</span></span>

|<span data-ttu-id="1fcde-111">Distribuzione/i</span><span class="sxs-lookup"><span data-stu-id="1fcde-111">Distrobution(s)</span></span>|<span data-ttu-id="1fcde-112">Comando pacchetto stabile</span><span class="sxs-lookup"><span data-stu-id="1fcde-112">Stable Command</span></span> | <span data-ttu-id="1fcde-113">Comando pacchetto anteprima</span><span class="sxs-lookup"><span data-stu-id="1fcde-113">Preview Command</span></span> |
|---------------|---------------|-----------------|
| <span data-ttu-id="1fcde-114">Ubuntu, Debian</span><span class="sxs-lookup"><span data-stu-id="1fcde-114">Ubuntu, Debian</span></span> |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| <span data-ttu-id="1fcde-115">CentOS, RedHat</span><span class="sxs-lookup"><span data-stu-id="1fcde-115">CentOS, RedHat</span></span> |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| <span data-ttu-id="1fcde-116">OpenSUSE</span><span class="sxs-lookup"><span data-stu-id="1fcde-116">OpenSUSE</span></span> |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| <span data-ttu-id="1fcde-117">Fedora</span><span class="sxs-lookup"><span data-stu-id="1fcde-117">Fedora</span></span>   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a><span data-ttu-id="1fcde-118">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-118">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="1fcde-119">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-119">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="1fcde-120">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-121">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-121">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/14.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-122">Come utente con privilegi avanzati, registrare il repository di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="1fcde-122">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="1fcde-123">A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.</span><span class="sxs-lookup"><span data-stu-id="1fcde-123">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="1fcde-124">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-124">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="1fcde-125">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1fcde-125">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1fcde-126">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-126">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1fcde-127">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="1fcde-127">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="1fcde-128">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-128">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="1fcde-129">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-129">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="1fcde-130">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-130">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="1fcde-131">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-131">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="1fcde-132">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-132">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-133">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-133">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/16.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-134">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-134">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="1fcde-135">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-135">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="1fcde-136">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1fcde-136">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1fcde-137">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-137">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1fcde-138">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="1fcde-138">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="1fcde-139">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-139">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="1fcde-140">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-140">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1710"></a><span data-ttu-id="1fcde-141">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="1fcde-141">Ubuntu 17.10</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-142">Il supporto di Ubuntu 17.04 è stato aggiunto dopo `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="1fcde-142">Support for Ubuntu 17.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1710"></a><span data-ttu-id="1fcde-143">Ubuntu 17.10: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-143">Installation via Package Repository - Ubuntu 17.10</span></span>

<span data-ttu-id="1fcde-144">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-144">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-145">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-145">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.10/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-146">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-146">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1710"></a><span data-ttu-id="1fcde-147">Ubuntu 17.10: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-147">Installation via Direct Download - Ubuntu 17.10</span></span>

<span data-ttu-id="1fcde-148">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1fcde-148">Download the Debian package `powershell_6.0.2-1.ubuntu.17.10_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1fcde-149">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-149">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.10_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1fcde-150">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="1fcde-150">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="1fcde-151">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-151">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="1fcde-152">Ubuntu 17.10: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-152">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a><span data-ttu-id="1fcde-153">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-153">Ubuntu 18.04</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-154">Il supporto di Ubuntu 18.04 è stato aggiunto dopo `6.1.0-preview.2`</span><span class="sxs-lookup"><span data-stu-id="1fcde-154">Support for Ubuntu 18.04 was added after `6.1.0-preview.2`</span></span>

### <a name="installation-via-package-repository---ubuntu-1804"></a><span data-ttu-id="1fcde-155">Ubuntu 18.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-155">Installation via Package Repository - Ubuntu 18.04</span></span>

<span data-ttu-id="1fcde-156">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-156">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-157">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-157">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-158">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-158">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1804"></a><span data-ttu-id="1fcde-159">Ubuntu 18.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-159">Installation via Direct Download - Ubuntu 18.04</span></span>

<span data-ttu-id="1fcde-160">Scaricare il pacchetto Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="1fcde-160">Download the Debian package `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="1fcde-161">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-161">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1fcde-162">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="1fcde-162">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="1fcde-163">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-163">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1710"></a><span data-ttu-id="1fcde-164">Ubuntu 17.10: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-164">Uninstallation - Ubuntu 17.10</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="1fcde-165">Debian 8</span><span class="sxs-lookup"><span data-stu-id="1fcde-165">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="1fcde-166">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-166">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="1fcde-167">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-167">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-168">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-168">This is the preferred method.</span></span>

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

<span data-ttu-id="1fcde-169">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-169">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="1fcde-170">Debian 8: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-170">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="1fcde-171">Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.8_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="1fcde-171">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1fcde-172">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-172">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="1fcde-173">Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="1fcde-173">The `dpkg -i` command fails with unmet dependencies.</span></span>
> <span data-ttu-id="1fcde-174">Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-174">The next command, `apt-get install -f` resolves these issues then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="1fcde-175">Debian 8: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-175">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="1fcde-176">Debian 9</span><span class="sxs-lookup"><span data-stu-id="1fcde-176">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="1fcde-177">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-177">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="1fcde-178">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-178">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="1fcde-179">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="1fcde-179">This is the preferred method.</span></span>

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

<span data-ttu-id="1fcde-180">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-180">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="1fcde-181">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-181">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="1fcde-182">Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="1fcde-182">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="1fcde-183">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-183">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a><span data-ttu-id="1fcde-184">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-184">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="1fcde-185">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1fcde-185">CentOS 7</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-186">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="1fcde-186">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="1fcde-187">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-187">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="1fcde-188">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="1fcde-188">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-189">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-189">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="1fcde-190">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-190">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="1fcde-191">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="1fcde-191">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="1fcde-192">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-192">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1fcde-193">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="1fcde-193">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="1fcde-194">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-194">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1fcde-196">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="1fcde-196">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1fcde-197">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="1fcde-197">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1fcde-198">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="1fcde-198">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="1fcde-199">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-199">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1fcde-200">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-200">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="1fcde-201">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-201">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="1fcde-202">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-202">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1fcde-203">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="1fcde-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="1fcde-204">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-204">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="1fcde-205">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1fcde-205">OpenSUSE 42.2</span></span>

<span data-ttu-id="1fcde-206">Durante l'installazione di PowerShell Core, `zypper` può segnalare l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="1fcde-206">When installing PowerShell Core, `zypper` may report the following error:</span></span>

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

<span data-ttu-id="1fcde-207">In questo caso, verificare che sia presente una libreria `libcurl` compatibile assicurandosi che il comando seguente indichi il pacchetto `libcurl4` come installato:</span><span class="sxs-lookup"><span data-stu-id="1fcde-207">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

<span data-ttu-id="1fcde-208">Scegliere quindi la soluzione `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quando si installa il pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1fcde-208">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="1fcde-209">OpenSUSE 42.2: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="1fcde-209">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="1fcde-210">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="1fcde-210">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Add the Microsoft Product feed
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/zypp/repos.d/microsoft.repo

# Update the list of products
sudo zypper update

# Install PowerShell
sudo zypper install powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="1fcde-211">OpenSUSE 42.2: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="1fcde-211">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="1fcde-212">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="1fcde-212">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1fcde-213">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="1fcde-213">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="1fcde-214">OpenSUSE 42.2: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-214">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="1fcde-215">Fedora</span><span class="sxs-lookup"><span data-stu-id="1fcde-215">Fedora</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-216">Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="1fcde-216">Fedora 28 is only supported in PowerShell Core 6.1 and newer.</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="1fcde-217">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1fcde-217">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="1fcde-218">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="1fcde-218">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="1fcde-219">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1fcde-219">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="1fcde-220">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="1fcde-220">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="1fcde-221">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-221">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="1fcde-222">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="1fcde-222">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="1fcde-223">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1fcde-223">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="1fcde-224">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="1fcde-224">Arch Linux</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-225">Il supporto di Arch è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-225">Arch support is experimental.</span></span>

<span data-ttu-id="1fcde-226">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="1fcde-226">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="1fcde-227">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="1fcde-227">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="1fcde-228">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="1fcde-228">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="1fcde-229">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="1fcde-229">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="1fcde-230">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-230">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="1fcde-231">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="1fcde-231">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="1fcde-233">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="1fcde-233">Linux AppImage</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-234">Il supporto di AppImage è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-234">AppImage support is experimental</span></span>

<span data-ttu-id="1fcde-235">Usando una distribuzione Linux recente, scaricare `powershell-6.0.1-x86_64.AppImage` di AppImage dalla pagina delle [versioni][] nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-235">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="1fcde-236">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="1fcde-236">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="1fcde-237">[AppImage][] consente di eseguire PowerShell senza doverlo installare.</span><span class="sxs-lookup"><span data-stu-id="1fcde-237">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="1fcde-238">È un'applicazione portabile che aggiunge PowerShell e le relative dipendenze (incluse le dipendenze di sistema di .NET Core) a un pacchetto integrato.</span><span class="sxs-lookup"><span data-stu-id="1fcde-238">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="1fcde-239">Questo pacchetto è un singolo file binario che funziona indipendentemente dalla distribuzione di Linux dell'utente.</span><span class="sxs-lookup"><span data-stu-id="1fcde-239">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="1fcde-241">Kali</span><span class="sxs-lookup"><span data-stu-id="1fcde-241">Kali</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-242">Il supporto di Kali è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-242">Kali support is experimental.</span></span>

### <a name="installation"></a><span data-ttu-id="1fcde-243">Installazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-243">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Install PowerShell
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="1fcde-244">Eseguire PowerShell nella versione Kali più recente (GNU/Linux Kali Rolling) senza eseguire l'installazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-244">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="1fcde-245">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-245">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="1fcde-246">Raspbian</span><span class="sxs-lookup"><span data-stu-id="1fcde-246">Raspbian</span></span>

> [!NOTE]
> <span data-ttu-id="1fcde-247">Il supporto di Raspbian è sperimentale.</span><span class="sxs-lookup"><span data-stu-id="1fcde-247">Raspbian support is experimental.</span></span>

<span data-ttu-id="1fcde-248">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="1fcde-248">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="1fcde-249">Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="1fcde-249">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="1fcde-250">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="1fcde-250">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="1fcde-251">Installazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-251">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.2-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

<span data-ttu-id="1fcde-252">Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"</span><span class="sxs-lookup"><span data-stu-id="1fcde-252">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="1fcde-253">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-253">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="1fcde-254">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="1fcde-254">Binary Archives</span></span>

<span data-ttu-id="1fcde-255">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="1fcde-255">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="1fcde-256">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="1fcde-256">Dependencies</span></span>

<span data-ttu-id="1fcde-257">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-257">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="1fcde-258">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="1fcde-258">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="1fcde-259">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-259">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="1fcde-260">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="1fcde-260">OS</span></span>                 | <span data-ttu-id="1fcde-261">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="1fcde-261">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="1fcde-262">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-262">Ubuntu 14.04</span></span>       | <span data-ttu-id="1fcde-263">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1fcde-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1fcde-265">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-265">Ubuntu 16.04</span></span>       | <span data-ttu-id="1fcde-266">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="1fcde-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="1fcde-268">Ubuntu 17.10</span><span class="sxs-lookup"><span data-stu-id="1fcde-268">Ubuntu 17.10</span></span>       | <span data-ttu-id="1fcde-269">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-269">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="1fcde-270">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="1fcde-271">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="1fcde-271">Ubuntu 18.04</span></span>       | <span data-ttu-id="1fcde-272">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-272">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span><span class="sxs-lookup"><span data-stu-id="1fcde-273">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60</span></span> |
| <span data-ttu-id="1fcde-274">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="1fcde-274">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="1fcde-275">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-275">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="1fcde-276">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="1fcde-277">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="1fcde-277">Debian 9 (Stretch)</span></span> | <span data-ttu-id="1fcde-278">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="1fcde-278">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="1fcde-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="1fcde-279">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="1fcde-280">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="1fcde-280">CentOS 7</span></span> <br> <span data-ttu-id="1fcde-281">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="1fcde-281">Oracle Linux 7</span></span> <br> <span data-ttu-id="1fcde-282">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="1fcde-282">RHEL 7</span></span> <br> <span data-ttu-id="1fcde-283">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="1fcde-283">OpenSUSE 42.2</span></span> | <span data-ttu-id="1fcde-284">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="1fcde-284">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="1fcde-285">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="1fcde-285">Fedora 27</span></span> <br> <span data-ttu-id="1fcde-286">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="1fcde-286">Fedora 28</span></span> | <span data-ttu-id="1fcde-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="1fcde-287">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="1fcde-288">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="1fcde-288">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="1fcde-289">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-289">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="1fcde-290">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="1fcde-290">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="1fcde-291">Linux</span><span class="sxs-lookup"><span data-stu-id="1fcde-291">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.2

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.2

# Set execute permissions
sudo chmod +x /opt/microsoft/powershell/6.0.2/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.2/pwsh /usr/bin/pwsh
```

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="1fcde-292">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="1fcde-292">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="1fcde-293">Percorsi</span><span class="sxs-lookup"><span data-stu-id="1fcde-293">Paths</span></span>

* <span data-ttu-id="1fcde-294">`$PSHOME` è `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="1fcde-294">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="1fcde-295">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1fcde-295">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="1fcde-296">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="1fcde-296">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="1fcde-297">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1fcde-297">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1fcde-298">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="1fcde-298">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="1fcde-299">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="1fcde-299">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="1fcde-300">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="1fcde-300">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="1fcde-301">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="1fcde-301">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="1fcde-302">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="1fcde-302">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
