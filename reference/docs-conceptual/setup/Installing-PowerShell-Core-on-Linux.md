# <a name="installing-powershell-core-on-linux"></a><span data-ttu-id="13c05-101">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="13c05-101">Installing PowerShell Core on Linux</span></span>

<span data-ttu-id="13c05-102">Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].</span><span class="sxs-lookup"><span data-stu-id="13c05-102">Supports [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 17.04][u17], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.2][opensuse], [Fedora 27][fedora], [Fedora 28][fedora], and [Arch Linux][arch].</span></span>

<span data-ttu-id="13c05-103">Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare [PowerShell AppImage][lai].</span><span class="sxs-lookup"><span data-stu-id="13c05-103">For Linux distributions that are not officially supported, you can try using the [PowerShell AppImage][lai].</span></span>
<span data-ttu-id="13c05-104">È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="13c05-104">You can also try deploying PowerShell binaries directly using the Linux [`tar.gz` archive][tar], but you would need to set up the necessary dependencies based on the OS in separate steps.</span></span>

<span data-ttu-id="13c05-105">Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.</span><span class="sxs-lookup"><span data-stu-id="13c05-105">All packages are available on our GitHub [releases][] page.</span></span>
<span data-ttu-id="13c05-106">Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.</span><span class="sxs-lookup"><span data-stu-id="13c05-106">Once the package is installed, run `pwsh` from a terminal.</span></span>

[u14]: #ubuntu-1404
[u16]: #ubuntu-1604
[u17]: #ubuntu-1704
[deb8]: #debian-8
[deb9]: #debian-9
[cos]: #centos-7
[rhel7]: #red-hat-enterprise-linux-rhel-7
[opensuse]: #opensuse-422
[fedora]: #fedora
[arch]: #arch-linux
[lai]: #linux-appimage
[tar]: #binary-archives

## <a name="ubuntu-1404"></a><span data-ttu-id="13c05-107">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="13c05-107">Ubuntu 14.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1404"></a><span data-ttu-id="13c05-108">Ubuntu 14.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-108">Installation via Package Repository - Ubuntu 14.04</span></span>

<span data-ttu-id="13c05-109">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13c05-109">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="13c05-110">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="13c05-110">This is the preferred method.</span></span>

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

<span data-ttu-id="13c05-111">Come utente con privilegi avanzati, registrare il repository di Microsoft.</span><span class="sxs-lookup"><span data-stu-id="13c05-111">As superuser, register the Microsoft repository.</span></span>
<span data-ttu-id="13c05-112">A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.</span><span class="sxs-lookup"><span data-stu-id="13c05-112">From then on, you just need to use `sudo apt-get upgrade powershell` to update the installation.</span></span>

### <a name="installation-via-direct-download---ubuntu-1404"></a><span data-ttu-id="13c05-113">Ubuntu 14.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-113">Installation via Direct Download - Ubuntu 14.04</span></span>

<span data-ttu-id="13c05-114">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="13c05-114">Download the Debian package `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="13c05-115">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-115">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="13c05-116">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-116">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1404"></a><span data-ttu-id="13c05-117">Ubuntu 14.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-117">Uninstallation - Ubuntu 14.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a><span data-ttu-id="13c05-118">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="13c05-118">Ubuntu 16.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1604"></a><span data-ttu-id="13c05-119">Ubuntu 16.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-119">Installation via Package Repository - Ubuntu 16.04</span></span>

<span data-ttu-id="13c05-120">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13c05-120">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="13c05-121">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="13c05-121">This is the preferred method.</span></span>

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

<span data-ttu-id="13c05-122">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="13c05-122">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1604"></a><span data-ttu-id="13c05-123">Installazione tramite download diretto - Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="13c05-123">Installation via Direct Download - Ubuntu 16.04</span></span>

<span data-ttu-id="13c05-124">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="13c05-124">Download the Debian package `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="13c05-125">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-125">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="13c05-126">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-126">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1604"></a><span data-ttu-id="13c05-127">Ubuntu 16.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-127">Uninstallation - Ubuntu 16.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1704"></a><span data-ttu-id="13c05-128">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="13c05-128">Ubuntu 17.04</span></span>

### <a name="installation-via-package-repository---ubuntu-1704"></a><span data-ttu-id="13c05-129">Ubuntu 17.04: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-129">Installation via Package Repository - Ubuntu 17.04</span></span>

<span data-ttu-id="13c05-130">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13c05-130">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="13c05-131">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="13c05-131">This is the preferred method.</span></span>

```sh
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/17.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="13c05-132">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="13c05-132">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---ubuntu-1704"></a><span data-ttu-id="13c05-133">Ubuntu 17.04: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-133">Installation via Direct Download - Ubuntu 17.04</span></span>

<span data-ttu-id="13c05-134">Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="13c05-134">Download the Debian package `powershell_6.0.2-1.ubuntu.17.04_amd64.deb` from the [releases][] page onto the Ubuntu machine.</span></span>

<span data-ttu-id="13c05-135">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-135">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.17.04_amd64.deb
sudo apt-get install -f
```

> <span data-ttu-id="13c05-136">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-136">Please note that `dpkg -i` will fail with unmet dependencies; the next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---ubuntu-1704"></a><span data-ttu-id="13c05-137">Ubuntu 17.04: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-137">Uninstallation - Ubuntu 17.04</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-8"></a><span data-ttu-id="13c05-138">Debian 8</span><span class="sxs-lookup"><span data-stu-id="13c05-138">Debian 8</span></span>

### <a name="installation-via-package-repository---debian-8"></a><span data-ttu-id="13c05-139">Debian 8: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-139">Installation via Package Repository - Debian 8</span></span>

<span data-ttu-id="13c05-140">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13c05-140">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="13c05-141">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="13c05-141">This is the preferred method.</span></span>

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

<span data-ttu-id="13c05-142">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="13c05-142">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-8"></a><span data-ttu-id="13c05-143">Debian 8: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-143">Installation via Direct Download - Debian 8</span></span>

<span data-ttu-id="13c05-144">Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.8_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="13c05-144">Download the Debian package `powershell_6.0.2-1.debian.8_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="13c05-145">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-145">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="13c05-146">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="13c05-146">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="13c05-147">Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-147">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-8"></a><span data-ttu-id="13c05-148">Debian 8: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-148">Uninstallation - Debian 8</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a><span data-ttu-id="13c05-149">Debian 9</span><span class="sxs-lookup"><span data-stu-id="13c05-149">Debian 9</span></span>

### <a name="installation-via-package-repository---debian-9"></a><span data-ttu-id="13c05-150">Debian 9: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-150">Installation via Package Repository - Debian 9</span></span>

<span data-ttu-id="13c05-151">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="13c05-151">PowerShell Core, for Linux, is published to package repositories for easy installation (and updates).</span></span>
<span data-ttu-id="13c05-152">Questo è il metodo preferito.</span><span class="sxs-lookup"><span data-stu-id="13c05-152">This is the preferred method.</span></span>

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

<span data-ttu-id="13c05-153">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.</span><span class="sxs-lookup"><span data-stu-id="13c05-153">After registering the Microsoft repository once as superuser, from then on, you just need to use `sudo apt-get upgrade powershell` to update it.</span></span>

### <a name="installation-via-direct-download---debian-9"></a><span data-ttu-id="13c05-154">Debian 9: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-154">Installation via Direct Download - Debian 9</span></span>

<span data-ttu-id="13c05-155">Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.</span><span class="sxs-lookup"><span data-stu-id="13c05-155">Download the Debian package `powershell_6.0.2-1.debian.9_amd64.deb` from the [releases][] page onto the Debian machine.</span></span>

<span data-ttu-id="13c05-156">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-156">Then execute the following in the terminal:</span></span>

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> <span data-ttu-id="13c05-157">Si noti che `dpkg -i` avrà esito negativo in caso di dipendenze non soddisfatte.</span><span class="sxs-lookup"><span data-stu-id="13c05-157">Please note that `dpkg -i` will fail with unmet dependencies.</span></span>
> <span data-ttu-id="13c05-158">Il comando successivo `apt-get install -f` risolve tali dipendenze e completa la configurazione del pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-158">The next command, `apt-get install -f` resolves these and then finishes configuring the PowerShell package.</span></span>

### <a name="uninstallation---debian-9"></a><span data-ttu-id="13c05-159">Debian 9: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-159">Uninstallation - Debian 9</span></span>

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a><span data-ttu-id="13c05-160">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="13c05-160">CentOS 7</span></span>

> <span data-ttu-id="13c05-161">Questo pacchetto funziona anche in Oracle Linux 7.</span><span class="sxs-lookup"><span data-stu-id="13c05-161">This package also works on Oracle Linux 7.</span></span>

### <a name="installation-via-package-repository-preferred---centos-7"></a><span data-ttu-id="13c05-162">CentOS 7: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-162">Installation via Package Repository (preferred) - CentOS 7</span></span>

<span data-ttu-id="13c05-163">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="13c05-163">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="13c05-164">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-164">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---centos-7"></a><span data-ttu-id="13c05-165">CentOS 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-165">Installation via Direct Download - CentOS 7</span></span>

<span data-ttu-id="13c05-166">Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.</span><span class="sxs-lookup"><span data-stu-id="13c05-166">Using [CentOS 7][], download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the CentOS machine.</span></span>

<span data-ttu-id="13c05-167">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-167">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="13c05-168">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="13c05-168">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a><span data-ttu-id="13c05-169">CentOS 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-169">Uninstallation - CentOS 7</span></span>

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="13c05-171">Red Hat Enterprise Linux (RHEL) 7</span><span class="sxs-lookup"><span data-stu-id="13c05-171">Red Hat Enterprise Linux (RHEL) 7</span></span>

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="13c05-172">Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)</span><span class="sxs-lookup"><span data-stu-id="13c05-172">Installation via Package Repository (preferred) - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="13c05-173">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="13c05-173">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

<span data-ttu-id="13c05-174">Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-174">After registering the Microsoft repository once as superuser, you just need to use `sudo yum update powershell` to update PowerShell.</span></span>

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="13c05-175">Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-175">Installation via Direct Download - Red Hat Enterprise Linux (RHEL) 7</span></span>

<span data-ttu-id="13c05-176">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-176">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Red Hat Enterprise Linux machine.</span></span>

<span data-ttu-id="13c05-177">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-177">Then execute the following in the terminal:</span></span>

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="13c05-178">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="13c05-178">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a><span data-ttu-id="13c05-179">Red Hat Enterprise Linux (RHEL) 7: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-179">Uninstallation - Red Hat Enterprise Linux (RHEL) 7</span></span>

```sh
sudo yum remove powershell
```

## <a name="opensuse-422"></a><span data-ttu-id="13c05-180">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="13c05-180">OpenSUSE 42.2</span></span>

> [!NOTE]
> <span data-ttu-id="13c05-181">Durante l'installazione di PowerShell Core, `zypper` può segnalare l'errore seguente:</span><span class="sxs-lookup"><span data-stu-id="13c05-181">When installing PowerShell Core, `zypper` may report the following error:</span></span>
>
> ```Output
> Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
>  Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
>  Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
> ```
>
> <span data-ttu-id="13c05-182">In questo caso, verificare che sia presente una libreria `libcurl` compatibile assicurandosi che il comando seguente indichi il pacchetto `libcurl4` come installato:</span><span class="sxs-lookup"><span data-stu-id="13c05-182">In this case, verify that a compatible `libcurl` library is present by checking that the following command shows the `libcurl4` package as installed:</span></span>
>
> ```sh
> zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
> ```
>
> <span data-ttu-id="13c05-183">Scegliere quindi la soluzione `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quando si installa il pacchetto PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13c05-183">Then choose the `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` solution when installing the PowerShell package.</span></span>

### <a name="installation-via-package-repository-preferred---opensuse-422"></a><span data-ttu-id="13c05-184">OpenSUSE 42.2: installazione tramite repository dei pacchetti</span><span class="sxs-lookup"><span data-stu-id="13c05-184">Installation via Package Repository (preferred) - OpenSUSE 42.2</span></span>

<span data-ttu-id="13c05-185">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="13c05-185">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---opensuse-422"></a><span data-ttu-id="13c05-186">OpenSUSE 42.2: installazione tramite download diretto</span><span class="sxs-lookup"><span data-stu-id="13c05-186">Installation via Direct Download - OpenSUSE 42.2</span></span>

<span data-ttu-id="13c05-187">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer OpenSUSE.</span><span class="sxs-lookup"><span data-stu-id="13c05-187">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the OpenSUSE machine.</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="13c05-188">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="13c05-188">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-422"></a><span data-ttu-id="13c05-189">OpenSUSE 42.2: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-189">Uninstallation - OpenSUSE 42.2</span></span>

```sh
sudo zypper remove powershell
```

## <a name="fedora"></a><span data-ttu-id="13c05-190">Fedora</span><span class="sxs-lookup"><span data-stu-id="13c05-190">Fedora</span></span>

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a><span data-ttu-id="13c05-191">Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="13c05-191">Installation via Package Repository (preferred) - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="13c05-192">Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.</span><span class="sxs-lookup"><span data-stu-id="13c05-192">PowerShell Core for Linux is published to official Microsoft repositories for easy installation (and updates).</span></span>

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a><span data-ttu-id="13c05-193">Installazione tramite download diretto - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="13c05-193">Installation via Direct Download - Fedora 27, Fedora 28</span></span>

<span data-ttu-id="13c05-194">Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.</span><span class="sxs-lookup"><span data-stu-id="13c05-194">Download the RPM package `powershell-6.0.2-1.rhel.7.x86_64.rpm` from the [releases][] page onto the Fedora machine.</span></span>

<span data-ttu-id="13c05-195">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-195">Then execute the following in the terminal:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

<span data-ttu-id="13c05-196">È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:</span><span class="sxs-lookup"><span data-stu-id="13c05-196">You can also install the RPM without the intermediate step of downloading it:</span></span>

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a><span data-ttu-id="13c05-197">Disinstallazione - Fedora 27, Fedora 28</span><span class="sxs-lookup"><span data-stu-id="13c05-197">Uninstallation - Fedora 27, Fedora 28</span></span>

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a><span data-ttu-id="13c05-198">Arch Linux</span><span class="sxs-lookup"><span data-stu-id="13c05-198">Arch Linux</span></span>

<span data-ttu-id="13c05-199">PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).</span><span class="sxs-lookup"><span data-stu-id="13c05-199">PowerShell is available from the [Arch Linux][] User Repository (AUR).</span></span>

* <span data-ttu-id="13c05-200">Può essere compilato con la [versione con tag più recente][arch-release]</span><span class="sxs-lookup"><span data-stu-id="13c05-200">It can be compiled with the [latest tagged release][arch-release]</span></span>
* <span data-ttu-id="13c05-201">Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]</span><span class="sxs-lookup"><span data-stu-id="13c05-201">It can be compiled from the [latest commit to master][arch-git]</span></span>
* <span data-ttu-id="13c05-202">Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]</span><span class="sxs-lookup"><span data-stu-id="13c05-202">It can be installed using the [latest release binary][arch-bin]</span></span>

<span data-ttu-id="13c05-203">I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.</span><span class="sxs-lookup"><span data-stu-id="13c05-203">Packages in the AUR are community maintained - there is no official support.</span></span>

<span data-ttu-id="13c05-204">Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span><span class="sxs-lookup"><span data-stu-id="13c05-204">For more information on installing packages from the AUR, see the [Arch Linux wiki](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) or the community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).</span></span>

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="linux-appimage"></a><span data-ttu-id="13c05-206">Linux AppImage</span><span class="sxs-lookup"><span data-stu-id="13c05-206">Linux AppImage</span></span>

<span data-ttu-id="13c05-207">Usando una distribuzione Linux recente, scaricare `powershell-6.0.1-x86_64.AppImage` di AppImage dalla pagina delle [versioni][] nel computer Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-207">Using a recent Linux distribution, download the AppImage `powershell-6.0.1-x86_64.AppImage` from the [releases][] page onto the Linux machine.</span></span>

<span data-ttu-id="13c05-208">A questo punto eseguire quanto segue nel terminale:</span><span class="sxs-lookup"><span data-stu-id="13c05-208">Then execute the following in the terminal:</span></span>

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

<span data-ttu-id="13c05-209">[AppImage][] consente di eseguire PowerShell senza doverlo installare.</span><span class="sxs-lookup"><span data-stu-id="13c05-209">The [AppImage][] lets you run PowerShell without installing it.</span></span>
<span data-ttu-id="13c05-210">È un'applicazione portabile che aggiunge PowerShell e le relative dipendenze (incluse le dipendenze di sistema di .NET Core) a un pacchetto integrato.</span><span class="sxs-lookup"><span data-stu-id="13c05-210">It is a portable application that bundles PowerShell and its dependencies (including .NET Core's system dependencies) into one cohesive package.</span></span>
<span data-ttu-id="13c05-211">Questo pacchetto è un singolo file binario che funziona indipendentemente dalla distribuzione di Linux dell'utente.</span><span class="sxs-lookup"><span data-stu-id="13c05-211">This package  is a single binary that works independently of the user's Linux distribution.</span></span>

[appimage]: http://appimage.org/

## <a name="kali"></a><span data-ttu-id="13c05-213">Kali</span><span class="sxs-lookup"><span data-stu-id="13c05-213">Kali</span></span>

### <a name="installation"></a><span data-ttu-id="13c05-214">Installazione</span><span class="sxs-lookup"><span data-stu-id="13c05-214">Installation</span></span>

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a><span data-ttu-id="13c05-215">Eseguire PowerShell nella versione Kali più recente (GNU/Linux Kali Rolling) senza eseguire l'installazione</span><span class="sxs-lookup"><span data-stu-id="13c05-215">Run PowerShell in latest Kali (Kali GNU/Linux Rolling) without installing it</span></span>

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a><span data-ttu-id="13c05-216">Kali: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-216">Uninstallation - Kali</span></span>

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a><span data-ttu-id="13c05-217">Raspbian</span><span class="sxs-lookup"><span data-stu-id="13c05-217">Raspbian</span></span>

<span data-ttu-id="13c05-218">Attualmente, PowerShell è supportato solo in Raspbian Stretch.</span><span class="sxs-lookup"><span data-stu-id="13c05-218">Currently, PowerShell is only supported on Raspbian Stretch.</span></span>

<span data-ttu-id="13c05-219">Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.</span><span class="sxs-lookup"><span data-stu-id="13c05-219">Also CoreCLR (and thus PowerShell Core) will only work on Pi 2 and Pi 3 devices as other devices, like [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), have an unsupported processor.</span></span>

<span data-ttu-id="13c05-220">Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.</span><span class="sxs-lookup"><span data-stu-id="13c05-220">Download [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) and follow the [installation instructions](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) to get it onto your Pi.</span></span>

### <a name="installation"></a><span data-ttu-id="13c05-221">Installazione</span><span class="sxs-lookup"><span data-stu-id="13c05-221">Installation</span></span>

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

<span data-ttu-id="13c05-222">Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"</span><span class="sxs-lookup"><span data-stu-id="13c05-222">Optionally you can create a symbolic link to be able to start PowerShell without specifying path to the "pwsh" binary</span></span>

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a><span data-ttu-id="13c05-223">Raspbian: disinstallazione</span><span class="sxs-lookup"><span data-stu-id="13c05-223">Uninstallation - Raspbian</span></span>

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a><span data-ttu-id="13c05-224">Archivi di file binari</span><span class="sxs-lookup"><span data-stu-id="13c05-224">Binary Archives</span></span>

<span data-ttu-id="13c05-225">Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.</span><span class="sxs-lookup"><span data-stu-id="13c05-225">PowerShell binary `tar.gz` archives are provided for Linux platforms to enable advanced deployment scenarios.</span></span>

### <a name="dependencies"></a><span data-ttu-id="13c05-226">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="13c05-226">Dependencies</span></span>

<span data-ttu-id="13c05-227">PowerShell compila file binari portabili per tutte le distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-227">PowerShell builds portable binaries for all Linux distributions.</span></span>
<span data-ttu-id="13c05-228">Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="13c05-228">But .NET Core runtime requires different dependencies on different distributions, and hence PowerShell does the same.</span></span>

<span data-ttu-id="13c05-229">La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-229">The following chart shows the .NET Core 2.0 dependencies that are officially supported on different Linux distributions.</span></span>

| <span data-ttu-id="13c05-230">Sistema operativo</span><span class="sxs-lookup"><span data-stu-id="13c05-230">OS</span></span>                 | <span data-ttu-id="13c05-231">Dipendenze</span><span class="sxs-lookup"><span data-stu-id="13c05-231">Dependencies</span></span> |
| ------------------ | ------------ |
| <span data-ttu-id="13c05-232">Ubuntu 14.04</span><span class="sxs-lookup"><span data-stu-id="13c05-232">Ubuntu 14.04</span></span>       | <span data-ttu-id="13c05-233">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="13c05-233">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="13c05-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="13c05-234">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="13c05-235">Ubuntu 16.04</span><span class="sxs-lookup"><span data-stu-id="13c05-235">Ubuntu 16.04</span></span>       | <span data-ttu-id="13c05-236">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="13c05-236">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="13c05-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span><span class="sxs-lookup"><span data-stu-id="13c05-237">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55</span></span> |
| <span data-ttu-id="13c05-238">Ubuntu 17.04</span><span class="sxs-lookup"><span data-stu-id="13c05-238">Ubuntu 17.04</span></span>       | <span data-ttu-id="13c05-239">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="13c05-239">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="13c05-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span><span class="sxs-lookup"><span data-stu-id="13c05-240">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57</span></span> |
| <span data-ttu-id="13c05-241">Debian 8 (Jessie)</span><span class="sxs-lookup"><span data-stu-id="13c05-241">Debian 8 (Jessie)</span></span>  | <span data-ttu-id="13c05-242">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="13c05-242">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="13c05-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span><span class="sxs-lookup"><span data-stu-id="13c05-243">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52</span></span> |
| <span data-ttu-id="13c05-244">Debian 9 (Stretch)</span><span class="sxs-lookup"><span data-stu-id="13c05-244">Debian 9 (Stretch)</span></span> | <span data-ttu-id="13c05-245">libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6,</span><span class="sxs-lookup"><span data-stu-id="13c05-245">libc6, libgcc1, libgssapi-krb5-2, liblttng-ust0, libstdc++6,</span></span> <br> <span data-ttu-id="13c05-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span><span class="sxs-lookup"><span data-stu-id="13c05-246">libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57</span></span> |
| <span data-ttu-id="13c05-247">CentOS 7</span><span class="sxs-lookup"><span data-stu-id="13c05-247">CentOS 7</span></span> <br> <span data-ttu-id="13c05-248">Oracle Linux 7</span><span class="sxs-lookup"><span data-stu-id="13c05-248">Oracle Linux 7</span></span> <br> <span data-ttu-id="13c05-249">RHEL 7</span><span class="sxs-lookup"><span data-stu-id="13c05-249">RHEL 7</span></span> <br> <span data-ttu-id="13c05-250">OpenSUSE 42.2</span><span class="sxs-lookup"><span data-stu-id="13c05-250">OpenSUSE 42.2</span></span> | <span data-ttu-id="13c05-251">libunwind, libcurl, openssl-libs, libicu</span><span class="sxs-lookup"><span data-stu-id="13c05-251">libunwind, libcurl, openssl-libs, libicu</span></span> |
| <span data-ttu-id="13c05-252">Fedora 27</span><span class="sxs-lookup"><span data-stu-id="13c05-252">Fedora 27</span></span> <br> <span data-ttu-id="13c05-253">Fedora 28</span><span class="sxs-lookup"><span data-stu-id="13c05-253">Fedora 28</span></span> | <span data-ttu-id="13c05-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span><span class="sxs-lookup"><span data-stu-id="13c05-254">libunwind, libcurl, openssl-libs, libicu, compat-openssl10</span></span> |

<span data-ttu-id="13c05-255">Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.</span><span class="sxs-lookup"><span data-stu-id="13c05-255">To deploy PowerShell binaries on Linux distributions that are not officially supported, you need to install the necessary dependencies for the target OS in separate steps.</span></span>
<span data-ttu-id="13c05-256">Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-256">For example, our [Amazon Linux dockerfile][amazon-dockerfile] installs dependencies first, and then extracts the Linux `tar.gz` archive.</span></span>

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a><span data-ttu-id="13c05-257">Archivi di file binari: installazione</span><span class="sxs-lookup"><span data-stu-id="13c05-257">Installation - Binary Archives</span></span>

#### <a name="linux"></a><span data-ttu-id="13c05-258">Linux</span><span class="sxs-lookup"><span data-stu-id="13c05-258">Linux</span></span>

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

### <a name="uninstalling-binary-archives"></a><span data-ttu-id="13c05-259">Disinstallazione degli archivi binari</span><span class="sxs-lookup"><span data-stu-id="13c05-259">Uninstalling binary archives</span></span>

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a><span data-ttu-id="13c05-260">Percorsi</span><span class="sxs-lookup"><span data-stu-id="13c05-260">Paths</span></span>

* <span data-ttu-id="13c05-261">`$PSHOME` è `/opt/microsoft/powershell/6.0.2/`</span><span class="sxs-lookup"><span data-stu-id="13c05-261">`$PSHOME` is `/opt/microsoft/powershell/6.0.2/`</span></span>
* <span data-ttu-id="13c05-262">I profili utente vengono letti da `~/.config/powershell/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="13c05-262">User profiles will be read from `~/.config/powershell/profile.ps1`</span></span>
* <span data-ttu-id="13c05-263">I profili predefiniti vengono letti da `$PSHOME/profile.ps1`</span><span class="sxs-lookup"><span data-stu-id="13c05-263">Default profiles will be read from `$PSHOME/profile.ps1`</span></span>
* <span data-ttu-id="13c05-264">I moduli utente vengono letti da `~/.local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="13c05-264">User modules will be read from `~/.local/share/powershell/Modules`</span></span>
* <span data-ttu-id="13c05-265">I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`</span><span class="sxs-lookup"><span data-stu-id="13c05-265">Shared modules will be read from `/usr/local/share/powershell/Modules`</span></span>
* <span data-ttu-id="13c05-266">I moduli predefiniti vengono letti da `$PSHOME/Modules`</span><span class="sxs-lookup"><span data-stu-id="13c05-266">Default modules will be read from `$PSHOME/Modules`</span></span>
* <span data-ttu-id="13c05-267">La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span><span class="sxs-lookup"><span data-stu-id="13c05-267">PSReadline history will be recorded to `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`</span></span>

<span data-ttu-id="13c05-268">I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.</span><span class="sxs-lookup"><span data-stu-id="13c05-268">The profiles respect PowerShell's per-host configuration, so the default host-specific profiles exists at `Microsoft.PowerShell_profile.ps1` in the same locations.</span></span>

<span data-ttu-id="13c05-269">PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.</span><span class="sxs-lookup"><span data-stu-id="13c05-269">PowerShell respects the [XDG Base Directory Specification][xdg-bds] on Linux.</span></span>

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[releases]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
