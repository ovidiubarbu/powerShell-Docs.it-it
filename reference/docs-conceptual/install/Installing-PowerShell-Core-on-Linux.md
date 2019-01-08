---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 08/06/2018
ms.openlocfilehash: afb11f053517af592fe42754d543f9f4a9966c5b
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401513"
---
# <a name="installing-powershell-core-on-linux"></a>Installazione di PowerShell Core in Linux

Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].

Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare il [pacchetto Snap di PowerShell][snap].
È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.

Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.
Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.

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

## <a name="installing-preview-releases"></a>Installazione di versioni di anteprima

Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.

L'installazione tramite download diretto non cambia, tranne per il nome del file.

Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:

|Distribuzione/i|Comando pacchetto stabile | Comando pacchetto anteprima |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Ubuntu 14.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Come utente con privilegi avanzati, registrare il repository di Microsoft.
A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Ubuntu 14.04: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.14.04_amd64.deb`
dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.14.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.
> Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---ubuntu-1404"></a>Ubuntu 14.04: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Ubuntu 16.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installazione tramite download diretto - Ubuntu 16.04

Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.16.04_amd64.deb`
dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.
> Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Ubuntu 16.04: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

> [!NOTE]
> Il supporto di Ubuntu 18.04 è stato aggiunto dopo `6.1.0-preview.2`

### <a name="installation-via-package-repository---ubuntu-1804"></a>Ubuntu 18.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Ubuntu 18.04: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.1.0-1.ubuntu.18.04_amd64.deb`
dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.
> Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Ubuntu 18.04: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

> [!NOTE]
> Il supporto di Ubuntu 18.10 è stato aggiunto dopo `6.1.0-preview.3`.
> Poiché la versione 18.10 è una build giornaliera, è supportata solo dalla community.

L'installazione nella versione 18.10 è supportata tramite `snapd`. Per istruzioni complete, vedere [Pacchetto Snap][snap].

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Debian 8: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---debian-8"></a>Debian 8: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.8_amd64.deb`
dalla pagina delle [versioni][] nel computer Debian.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.8_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte.
> Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---debian-8"></a>Debian 8: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Debian 9: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---debian-9"></a>Debian 9: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.1.0-1.debian.9_amd64.deb`
dalla pagina delle [versioni][] nel computer Debian.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Debian 9: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Questo pacchetto funziona anche in Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>CentOS 7: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.

### <a name="installation-via-direct-download---centos-7"></a>CentOS 7: installazione tramite download diretto

Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
dalla pagina delle [versioni][] nel computer CentOS.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>CentOS 7: disinstallazione

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è necessario usare semplicemente `sudo yum update powershell` per aggiornare PowerShell.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto

Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo yum install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: disinstallazione

```sh
sudo yum remove powershell
```

## <a name="opensuse"></a>openSUSE

### <a name="installation---opensuse-423"></a>Installazione - openSUSE 42.3

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

### <a name="installation---opensuse-leap-15"></a>Installazione - openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Disinstallazione - openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 è supportato solo in PowerShell Core 6.1 e versioni successive.

### <a name="installation-via-package-repository-preferred---fedora-27-fedora-28"></a>Installazione tramite repository dei pacchetti (preferenziale) - Fedora 27, Fedora 28

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.

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

### <a name="installation-via-direct-download---fedora-27-fedora-28"></a>Installazione tramite download diretto - Fedora 27, Fedora 28

Scaricare il pacchetto RPM `powershell-6.1.0-1.rhel.7.x86_64.rpm`
dalla pagina delle [versioni][] nel computer Fedora.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.1.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.1.0/powershell-6.1.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-27-fedora-28"></a>Disinstallazione - Fedora 27, Fedora 28

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Il supporto di Arch è sperimentale.

PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).

* Può essere compilato con la [versione con tag più recente][arch-release]
* Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]
* Può essere compilato usando il [pacchetto di file binari della versione più recente][arch-bin]

I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.

Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Pacchetto Snap

### <a name="getting-snapd"></a>Recupero di snapd

`snapd` è necessario per l'esecuzione di pacchetti Snap.
Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.

### <a name="installation-via-snap"></a>Installazione tramite Snap

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).
Questo è il metodo preferito.

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Se si vuole installare la versione di anteprima, usare il metodo seguente.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Dopo l'installazione, Snap eseguirà automaticamente l'aggiornamento, ma è possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Disinstallazione

```sh
sudo snap remove powershell
```

o

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

### <a name="installation---kali"></a>Kali: installazione

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

### <a name="uninstallation---kali"></a>Kali: disinstallazione

```sh
# Uninstall PowerShell package
apt-get remove -y powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Il supporto di Raspbian è sperimentale.

Attualmente, PowerShell è supportato solo in Raspbian Stretch.

Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.

Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.

### <a name="installation---raspbian"></a>Raspbian: installazione

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

Facoltativamente, è possibile creare un collegamento simbolico per poter avviare PowerShell senza specificare il percorso del file binario "pwsh"

```sh
# Start PowerShell from bash with sudo to create a symbolic link
sudo ~/powershell/pwsh -c New-Item -ItemType SymbolicLink -Path "/usr/bin/pwsh" -Target "\$PSHOME/pwsh" -Force

# alternatively you can run following to create a symbolic link
# sudo ln -s ~/powershell/pwsh /usr/bin/pwsh

# Now to start PowerShell you can just run "pwsh"
```

### <a name="uninstallation---raspbian"></a>Raspbian: disinstallazione

```sh
rm -rf ~/powershell
```

## <a name="binary-archives"></a>Archivi di file binari

Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.

### <a name="dependencies"></a>Dipendenze

PowerShell compila file binari portabili per tutte le distribuzioni di Linux.
Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse in varie distribuzioni e pertanto PowerShell richiede lo stesso comportamento.

La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.

| Sistema operativo                 | Dipendenze |
| ------------------ | ------------ |
| Ubuntu 14.04       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Ubuntu 16.04       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.
Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Archivi di file binari: installazione

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Disinstallazione degli archivi binari

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Percorsi

* `$PSHOME` è `/opt/microsoft/powershell/6.1.0/`
* I profili utente vengono letti da `~/.config/powershell/profile.ps1`
* I profili predefiniti vengono letti da `$PSHOME/profile.ps1`
* I moduli utente vengono letti da `~/.local/share/powershell/Modules`
* I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`
* I moduli predefiniti vengono letti da `$PSHOME/Modules`
* La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.

PowerShell rispetta la [specifica della directory Base XDG][xdg-bds] in Linux.

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
