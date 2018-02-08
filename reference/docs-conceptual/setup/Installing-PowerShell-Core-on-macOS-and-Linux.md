# <a name="installing-powershell-core-on-macos-and-linux"></a><span data-ttu-id="e2b3c-101">Installazione di PowerShell Core in macOS e Linux</span><span class="sxs-lookup"><span data-stu-id="e2b3c-101">Installing PowerShell Core on macOS and Linux</span></span>

<span data-ttu-id="e2b3c-102">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch] e [macOS 10.12][mac].</span><span class="sxs-lookup"><span data-stu-id="e2b3c-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 25][fed25], [Fedora 26][fed26], [Arch Linux][arch], and [macOS 10.12][mac].</span></span>

<span data-ttu-id="e2b3c-103">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="e2b3c-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span> <span data-ttu-id="e2b3c-104">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="e2b3c-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-105">All packages are available on our GitHub [releases][] page.</span></span> <span data-ttu-id="e2b3c-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fed25]: #fedora-25
[fed26]: #fedora-26
[arch]: #arch-linux
[lai]: #linux-appimage
[mac]: #macos-1012
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="e2b3c-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="e2b3c-108">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="e2b3c-109">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span> <span data-ttu-id="e2b3c-110">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-110">This is the preferred method.</span></span>

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

<span data-ttu-id="e2b3c-111">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-111">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="e2b3c-112">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-112">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="e2b3c-113">Scaricare il pacchetto Debian `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-113">Download the Debian package `powershell_6.0.0-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.14.04_amd64.deb
```

<span data-ttu-id="e2b3c-114">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-114">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e2b3c-115">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-115">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="e2b3c-116">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-116">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="e2b3c-117">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-117">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="e2b3c-118">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-118">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="e2b3c-119">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-119">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e2b3c-120">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-120">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/16.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e2b3c-121">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-121">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="e2b3c-122">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-122">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="e2b3c-123">Scaricare il pacchetto Debian `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-123">Download the Debian package `powershell_6.0.0-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
```

<span data-ttu-id="e2b3c-124">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-124">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e2b3c-125">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-125">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="e2b3c-126">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-126">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="e2b3c-127">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-127">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="e2b3c-128">Ubuntu 17.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-128">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="e2b3c-129">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-129">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e2b3c-130">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-130">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
curl https://packages.microsoft.com/config/ubuntu/17.04/prod.list | sudo tee /etc/apt/sources.list.d/microsoft.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e2b3c-131">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-131">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="e2b3c-132">Ubuntu 17.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-132">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="e2b3c-133">Scaricare il pacchetto Debian `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-133">Download the Debian package `powershell_6.0.0-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.17.04_amd64.deb
```

<span data-ttu-id="e2b3c-134">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-134">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e2b3c-135">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-135">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="e2b3c-136">Ubuntu 17.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-136">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="e2b3c-137">Debian 8</span><span class="sxs-lookup"><span data-stu-id="e2b3c-137">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="e2b3c-138">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-138">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="e2b3c-139">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-139">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e2b3c-140">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-140">This is the preferred method.</span></span>

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

<span data-ttu-id="e2b3c-141">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-141">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="e2b3c-142">Debian 8: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-142">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="e2b3c-143">Scaricare il pacchetto Debian `powershell_6.0.0-1.debian.8_amd64.deb` dalla pagina delle [versioni][] nel computer Debian:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-143">Download the Debian package `powershell_6.0.0-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.8_amd64.deb
```

<span data-ttu-id="e2b3c-144">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-144">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e2b3c-145">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-145">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="e2b3c-146">Debian 8: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-146">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="e2b3c-147">Debian 9</span><span class="sxs-lookup"><span data-stu-id="e2b3c-147">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="e2b3c-148">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-148">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="e2b3c-149">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-149">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="e2b3c-150">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-150">This is the preferred method.</span></span>

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

<span data-ttu-id="e2b3c-151">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-151">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="e2b3c-152">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-152">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="e2b3c-153">Scaricare il pacchetto Debian `powershell_6.0.0-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-153">Download the Debian package `powershell_6.0.0-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="e2b3c-154">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-154">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="e2b3c-155">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-155">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="e2b3c-156">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-156">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="e2b3c-157">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e2b3c-157">CentOS 7</span></span>

> <span data-ttu-id="e2b3c-158">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-158">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="e2b3c-159">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-159">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="e2b3c-160">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-160">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e2b3c-161">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-161">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="e2b3c-162">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-162">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="e2b3c-163">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-163">Using [CentOS 7][], download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-164">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-164">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-165">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-165">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="e2b3c-166">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-166">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e2b3c-168">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="e2b3c-168">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e2b3c-169">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="e2b3c-169">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e2b3c-170">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-170">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="e2b3c-171">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-171">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e2b3c-172">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-172">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="e2b3c-173">Scaricare il pacchetto RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-173">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.debian.9_amd64.deb
```

<span data-ttu-id="e2b3c-174">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-174">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-175">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-175">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="e2b3c-176">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-176">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="e2b3c-177">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e2b3c-177">OpenSUSE 42.2</span></span>

> <span data-ttu-id="e2b3c-178">**Nota:** quando si installa PowerShell Core, è possibile che OpenSUSE segnali l'assenza di `libcurl`.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-178">**Note:** When installing PowerShell Core, OpenSUSE may report that nothing provides `libcurl`.</span></span>
<span data-ttu-id="e2b3c-179">L'oggetto `libcurl` deve essere già installato nelle versioni supportate di OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-179">`libcurl` should already be installed on supported versions of OpenSUSE.</span></span>
<span data-ttu-id="e2b3c-180">Eseguire `zypper search libcurl` per confermare.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-180">Run `zypper search libcurl` to confirm.</span></span>
<span data-ttu-id="e2b3c-181">L'errore conterrà due soluzioni.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-181">The error will present 2 'solutions'.</span></span> <span data-ttu-id="e2b3c-182">Scegliere la soluzione 2 per proseguire con l'installazione di PowerShell Core.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-182">Choose 'Solution 2' to continue installing PowerShell Core.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="e2b3c-183">OpenSUSE 42.2: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-183">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="e2b3c-184">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-184">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="e2b3c-185">OpenSUSE 42.2: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-185">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="e2b3c-186">Scaricare il pacchetto RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer OpenSUSE:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-186">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-187">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-187">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="e2b3c-188">OpenSUSE 42.2: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-188">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora-25"></a><span data-ttu-id="e2b3c-189">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e2b3c-189">Fedora 25</span></span>

### <a name="installation-via-package-repository-preferred---fedora-25"></a><span data-ttu-id="e2b3c-190">Fedora 25: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-190">Installation via Package Repository (preferred) - Fedora 25</span></span>

<span data-ttu-id="e2b3c-191">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-191">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft signature key
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc

# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Update the list of products
sudo dnf update

# Install PowerShell
sudo dnf install -y powershell

# Start PowerShell
pwsh
```

### <a name="installation-via-direct-download---fedora-25"></a><span data-ttu-id="e2b3c-192">Fedora 25: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-192">Installation via Direct Download - Fedora 25</span></span>

<span data-ttu-id="e2b3c-193">Scaricare il pacchetto RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-193">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-194">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-194">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-195">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-195">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-25"></a><span data-ttu-id="e2b3c-196">Fedora 25: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-196">Uninstallation - Fedora 25</span></span>

```sh
sudo dnf remove powershell
```

## <a name="fedora-26"></a><span data-ttu-id="e2b3c-197">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e2b3c-197">Fedora 26</span></span>

### <a name="installation-via-package-repository-preferred---fedora-26"></a><span data-ttu-id="e2b3c-198">Fedora 26: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="e2b3c-198">Installation via Package Repository (preferred) - Fedora 26</span></span>

<span data-ttu-id="e2b3c-199">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-199">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-26"></a><span data-ttu-id="e2b3c-200">Fedora 26: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-200">Installation via Direct Download - Fedora 26</span></span>

<span data-ttu-id="e2b3c-201">Scaricare il pacchetto RPM `powershell-6.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-201">Download the RPM package `powershell-6.0.0-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine:</span></span>

```sh
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-202">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-202">Then execute the following in the terminal:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.0-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="e2b3c-203">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-203">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf update
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-26"></a><span data-ttu-id="e2b3c-204">Fedora 26: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-204">Uninstallation - Fedora 26</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="e2b3c-205">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="e2b3c-205">Arch Linux</span></span>

<span data-ttu-id="e2b3c-206">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="e2b3c-206">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="e2b3c-207">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="e2b3c-207">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="e2b3c-208">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="e2b3c-208">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="e2b3c-209">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="e2b3c-209">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="e2b3c-210">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-210">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="e2b3c-211">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="e2b3c-211">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="e2b3c-213">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="e2b3c-213">Linux AppImage</span></span>

<span data-ttu-id="e2b3c-214">Usando una distribuzione Linux recente, scaricare `powershell-6.0.0-x86_64.AppImage` di AppImage dalla pagina delle [versioni][] nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-214">Using a recent Linux distribution, download the AppImage `powershell-6.0.0-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="e2b3c-215">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-215">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.0-x86_64.AppImage
./powershell-6.0.0-x86_64.AppImage
```

<span data-ttu-id="e2b3c-216">[AppImage][] consente di eseguire PowerShell senza doverlo installare.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-216">The [AppImage][] lets you run PowerShell without installing it.</span></span> <span data-ttu-id="e2b3c-217">È un'applicazione portabile che aggiunge PowerShell e le relative dipendenze (incluse le dipendenze di sistema di .NET Core) a un pacchetto integrato.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-217">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span> <span data-ttu-id="e2b3c-218">Questo pacchetto funziona indipendentemente dalla distribuzione di Linux dell'utente ed è un singolo file binario.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-218">This package works independently of the user's Linux distribution, and is a single binary.</span></span>

[appimage]: http://appimage.org/

## <a name="macos-1012"></a><span data-ttu-id="e2b3c-220">MacOS 10.12</span><span class="sxs-lookup"><span data-stu-id="e2b3c-220">macOS 10.12</span></span>

### <a name="installation-via-homebrew-preferred---macos-1012"></a><span data-ttu-id="e2b3c-221">MacOS 10.12: installazione tramite Homebrew (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="e2b3c-221">Installation via Homebrew (preferred) - macOS 10.12</span></span>

<span data-ttu-id="e2b3c-222">[Homebrew][brew] rappresenta la gestione pacchetti mancante per macOS.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-222">[Homebrew][brew] is the missing package manager for macOS.</span></span> <span data-ttu-id="e2b3c-223">Se il comando `brew` non viene trovato, è necessario installare Homebrew seguendo [le istruzioni][brew].</span><span class="sxs-lookup"><span data-stu-id="e2b3c-223">If the `brew` command is not found, you need to install Homebrew following [their instructions][brew].</span></span>

<span data-ttu-id="e2b3c-224">Dopo aver installato Homebrew, installare PowerShell sarà semplice.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-224">Once you've installed Homebrew, installing PowerShell is easy.</span></span> <span data-ttu-id="e2b3c-225">Prima installare [Homebrew-Cask][cask] in modo da poter installare più pacchetti:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-225">First, install [Homebrew-Cask][cask], so you can install more packages:</span></span>

```sh
brew tap caskroom/cask
```

<span data-ttu-id="e2b3c-226">A questo punto, è possibile installare PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-226">Now, you can install PowerShell:</span></span>

```sh
brew cask install powershell
```

<span data-ttu-id="e2b3c-227">Quando vengono rilasciate nuove versioni di PowerShell, è sufficiente aggiornare le formule di Homebrew ed eseguire l'aggiornamento di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-227">When new versions of PowerShell are released, simply update Homebrew's formulae and upgrade PowerShell:</span></span>

```sh
brew update
brew cask reinstall powershell
```

> <span data-ttu-id="e2b3c-228">Nota: a causa di [questo problema in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), attualmente è necessario ripetere l'installazione per eseguire l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-228">Note: because of [this issue in Cask](https://github.com/caskroom/homebrew-cask/issues/29301), you currently have to do a reinstall to upgrade.</span></span>

[brew]: http://brew.sh/
[cask]: https://caskroom.github.io/

### <a name="installation-via-direct-download---macos-1012"></a><span data-ttu-id="e2b3c-229">MacOS 10.12: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="e2b3c-229">Installation via Direct Download - macOS 10.12</span></span>

<span data-ttu-id="e2b3c-230">Usando macOS 10.12, scaricare il pacchetto PKG `powershell-6.0.0-osx.10.12-x64.pkg` dalla pagina delle [versioni][] nel computer macOS.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-230">Using macOS 10.12, download the PKG package `powershell-6.0.0-osx.10.12-x64.pkg` from the [releases][] page onto the macOS machine.</span></span>

<span data-ttu-id="e2b3c-231">Fare doppio clic sul file e seguire i prompt oppure eseguire l'installazione dal terminale:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-231">Either double-click the file and follow the prompts, or install it from the terminal:</span></span>

```sh
sudo installer -pkg powershell-6.0.0-osx.10.12-x64.pkg -target /
```

### <a name="uninstallation---macos-1012"></a><span data-ttu-id="e2b3c-232">MacOS 10.12: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-232">Uninstallation - macOS 10.12</span></span>

<span data-ttu-id="e2b3c-233">Se PowerShell è stato installato con Homebrew, disinstallarlo è semplice:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-233">If you installed PowerShell with Homebrew, uninstallation is easy:</span></span>

```sh
brew cask uninstall powershell
```

<span data-ttu-id="e2b3c-234">Se PowerShell è stato installato tramite download diretto, PowerShell deve essere rimosso manualmente:</span><span class="sxs-lookup"><span data-stu-id="e2b3c-234">If you installed PowerShell via direct download, PowerShell must be removed manually:</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

<span data-ttu-id="e2b3c-235">Per disinstallare i percorsi aggiuntivi di PowerShell, ad esempio il percorso del profilo utente, vedere la sezione [Percorsi][paths] riportata di seguito in questo documento e rimuovere i percorsi con `sudo rm`.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-235">To uninstall the additional PowerShell paths (such as the user profile path) please see the [paths][paths] section below in this document and remove the desired the paths with `sudo rm`.</span></span> <span data-ttu-id="e2b3c-236">(Nota: questo passaggio non è necessario se PowerShell è stato installato con Homebrew.)</span><span class="sxs-lookup"><span data-stu-id="e2b3c-236">(Note: this is not necessary if you installed with Homebrew.)</span></span>

[paths]:#paths

## <a name="kali"></a><span data-ttu-id="e2b3c-237">Kali</span><span class="sxs-lookup"><span data-stu-id="e2b3c-237">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="e2b3c-238">Installazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-238">Installation</span></span>

```sh
# Download & Install prerequisites
sudo apt-get install libunwind8 libicu55
wget http://security.debian.org/debian-security/pool/updates/main/o/openssl/libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb
sudo dpkg -i libssl1.0.0_1.0.1t-1+deb8u6_amd64.deb

# Download & Install PowerShell
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell_6.0.0-1.ubuntu.16.04_amd64.deb
sudo dpkg -i powershell_6.0.0-1.ubuntu.16.04_amd64.deb

# Start PowerShell
pwsh
```

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="e2b3c-239">Eseguire PowerShell nella versione Kali più recente (GNU/Linux Kali Rolling) senza eseguire l'installazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-239">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.0-x86_64.AppImage

# Start PowerShell
./powershell-6.0.0-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="e2b3c-240">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-240">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell-6.0.0-x86_64.AppImage
```

## <a name="raspbian"></a><span data-ttu-id="e2b3c-241">Raspbian</span><span class="sxs-lookup"><span data-stu-id="e2b3c-241">Raspbian</span></span>

<span data-ttu-id="e2b3c-242">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-242">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

### <a name="installation"></a><span data-ttu-id="e2b3c-243">Installazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-243">Installation</span></span>

```sh
# Install prerequisites
sudo apt-get install libunwind8

# Grab the latest tar.gz
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-arm32.tar.gz

# Make folder to put powershell
mkdir ~/powershell

# Unpack the tar.gz file
tar -xvf ./powershell-6.0.0-linux-arm32.tar.gz -C ~/powershell

# Start PowerShell
~/powershell/pwsh
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="e2b3c-244">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-244">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="e2b3c-245">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="e2b3c-245">Binary Archives</span></span>

<span data-ttu-id="e2b3c-246">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme macOS e Linux per abilitano scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-246">PowerShell binary `tar.gz` archives are provided for macOS and Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="e2b3c-247">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e2b3c-247">Dependencies</span></span>

<span data-ttu-id="e2b3c-248">Per Linux, PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-248">For Linux, PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="e2b3c-249">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-249">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="e2b3c-250">La tabella seguente illustra le dipendenze di .NET Core 2.0 in varie distribuzioni di Linux ufficialmente supportate.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-250">The following chart shows the .NET Core 2.0 dependencies on different Linux distributions that are officially supported.</span></span>

| <span data-ttu-id="e2b3c-251">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="e2b3c-251">OS</span></span>                 | <span data-ttu-id="e2b3c-252">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="e2b3c-252">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="e2b3c-253">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-253">Ubuntu 14.04</span></span>       | <span data-ttu-id="e2b3c-254">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e2b3c-254">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e2b3c-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e2b3c-255">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e2b3c-256">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-256">Ubuntu 16.04</span></span>       | <span data-ttu-id="e2b3c-257">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e2b3c-257">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e2b3c-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="e2b3c-258">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="e2b3c-259">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="e2b3c-259">Ubuntu 17.04</span></span>       | <span data-ttu-id="e2b3c-260">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e2b3c-260">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e2b3c-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="e2b3c-261">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="e2b3c-262">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="e2b3c-262">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="e2b3c-263">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e2b3c-263">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e2b3c-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="e2b3c-264">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="e2b3c-265">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="e2b3c-265">Debian 9 (Stretch)</span></span> | <span data-ttu-id="e2b3c-266">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="e2b3c-266">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="e2b3c-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="e2b3c-267">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="e2b3c-268">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="e2b3c-268">CentOS 7</span></span> <br> <span data-ttu-id="e2b3c-269">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="e2b3c-269">Oracle Linux 7</span></span> <br> <span data-ttu-id="e2b3c-270">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="e2b3c-270">RHEL 7</span></span> <br> <span data-ttu-id="e2b3c-271">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="e2b3c-271">OpenSUSE 42.2</span></span> <br> <span data-ttu-id="e2b3c-272">Fedora 25</span><span class="sxs-lookup"><span data-stu-id="e2b3c-272">Fedora 25</span></span> | <span data-ttu-id="e2b3c-273">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="e2b3c-273">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="e2b3c-274">Fedora 26</span><span class="sxs-lookup"><span data-stu-id="e2b3c-274">Fedora 26</span></span>          | <span data-ttu-id="e2b3c-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="e2b3c-275">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="e2b3c-276">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-276">In order to deploy PowerShell binaries on Linux distributions that are not officially supported, you would need to install the necessary dependencies for the target OS in separate steps.</span></span> <span data-ttu-id="e2b3c-277">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-277">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="e2b3c-278">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-278">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e2b3c-279">Linux</span><span class="sxs-lookup"><span data-stu-id="e2b3c-279">Linux</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-linux-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /opt/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /opt/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /opt/microsoft/powershell/6.0.0/pwsh /usr/bin/pwsh
```

#### <a name="macos"></a><span data-ttu-id="e2b3c-280">macOS</span><span class="sxs-lookup"><span data-stu-id="e2b3c-280">macOS</span></span>

```sh
# Download the powershell '.tar.gz' archive
curl -L -o /tmp/powershell.tar.gz https://github.com/PowerShell/PowerShell/releases/download/v6.0.0/powershell-6.0.0-osx-x64.tar.gz

# Create the target folder where powershell will be placed
sudo mkdir -p /usr/local/microsoft/powershell/6.0.0

# Expand powershell to the target folder
sudo tar zxf /tmp/powershell.tar.gz -C /usr/local/microsoft/powershell/6.0.0

# Set execute permissions
sudo chmod +x /usr/local/microsoft/powershell/6.0.0/pwsh

# Create the symbolic link that points to pwsh
sudo ln -s /usr/local/microsoft/powershell/6.0.0/pwsh /usr/local/bin/pwsh
```

### <a name="uninstallation---binary-archives"></a><span data-ttu-id="e2b3c-281">Archivi di file binari: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="e2b3c-281">Uninstallation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="e2b3c-282">Linux</span><span class="sxs-lookup"><span data-stu-id="e2b3c-282">Linux</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

#### <a name="macos"></a><span data-ttu-id="e2b3c-283">macOS</span><span class="sxs-lookup"><span data-stu-id="e2b3c-283">macOS</span></span>

```sh
sudo rm -rf /usr/local/bin/pwsh /usr/local/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="e2b3c-284">Percorsi</span><span class="sxs-lookup"><span data-stu-id="e2b3c-284">Paths</span></span>

* <span data-ttu-id="e2b3c-285">`$PSHOME` è `/opt/microsoft/powershell/6.0.0/`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-285">`$PSHOME` is `/opt/microsoft/powershell/6.0.0/`</span></span>
* <span data-ttu-id="e2b3c-286">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-286">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="e2b3c-287">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-287">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="e2b3c-288">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-288">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e2b3c-289">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-289">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="e2b3c-290">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-290">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="e2b3c-291">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="e2b3c-291">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="e2b3c-292">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-292">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="e2b3c-293">In Linux e macOS viene rispettata la [specifica della directory Base XDG][xdg-bds].</span><span class="sxs-lookup"><span data-stu-id="e2b3c-293">On Linux and macOS, the [XDG Base Directory Specification][xdg-bds] is respected.</span></span>

<span data-ttu-id="e2b3c-294">Si noti che poiché macOS è una derivazione di BSD, invece di `/opt` si usa il prefisso `/usr/local`.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-294">Note that because macOS is a derivation of BSD, instead of `/opt`, the prefix used is `/usr/local`.</span></span> <span data-ttu-id="e2b3c-295">Di conseguenza, `$PSHOME` è `/usr/local/microsoft/powershell/6.0.0/` e il collegamento simbolico viene posizionato in `/usr/local/bin/pwsh`.</span><span class="sxs-lookup"><span data-stu-id="e2b3c-295">Thus, `$PSHOME` is `/usr/local/microsoft/powershell/6.0.0/`, and the symlink is placed at `/usr/local/bin/pwsh`.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
