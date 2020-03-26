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
# <a name="installing-powershell-on-linux"></a>Installazione di PowerShell in Linux

Supporta [Ubuntu 16.04][u16], [Ubuntu 18.04][u1804], [Ubuntu 18.10][u1810], [Ubuntu 19.04][u1904], [Debian 8][deb8], [Debian 9][deb9], [Debian 10][deb10], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [openSUSE 42.3][opensuse], [openSUSE Leap 15][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].

Per le distribuzioni Linux non supportate ufficialmente, è possibile provare a installare PowerShell con il [pacchetto PowerShell Snap][snap]. È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'archivio [`tar.gz`][tar] di Linux ma sarà necessario configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.

Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub. Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale. Eseguire `pwsh-preview` se è stata installata una [versione di anteprima](#installing-preview-releases).

> [!NOTE]
> PowerShell 7.x è un aggiornamento sul posto che rimuove PowerShell Core 6.x.
>
> La cartella `/usr/local/microsoft/powershell/6` viene sostituita da `/usr/local/microsoft/powershell/7`.
>
> Se è necessario avere PowerShell 6 insieme a PowerShell 7, reinstallare PowerShell 6 usando il metodo degli [archivi di file binari](#binary-archives).

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


## <a name="installing-preview-releases"></a>Installazione di versioni di anteprima

Quando si installa una versione di anteprima di PowerShell per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.

L'installazione tramite download diretto non cambia, tranne per il nome del file.

La tabella seguente contiene i comandi per installare i pacchetti stabili e di anteprima usando diversi strumenti di gestione dei pacchetti:

| Distribuzione/i |            Comando pacchetto stabile            |               Comando pacchetto anteprima                |
| --------------- | ------------------------------------ | -------------------------------------------- |
| Ubuntu, Debian  | `sudo apt-get install -y powershell` | `sudo apt-get install -y powershell-preview` |
| CentOS, RedHat  | `sudo yum install -y powershell`     | `sudo yum install -y powershell-preview`     |
| Fedora          | `sudo dnf install -y powershell`     | `sudo dnf install -y powershell-preview`     |

## <a name="ubuntu-1604"></a>Ubuntu 16.04

### <a name="installation-via-package-repository---ubuntu-1604"></a>Ubuntu 16.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.

Il metodo preferito è il seguente:

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

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installazione tramite download diretto - Ubuntu 16.04

Scaricare il pacchetto Debian `powershell_7.0.0-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.16.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---ubuntu-1604"></a>Ubuntu 16.04: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1804"></a>Ubuntu 18.04

### <a name="installation-via-package-repository---ubuntu-1804"></a>Ubuntu 18.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.

Il metodo preferito è il seguente:

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

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Ubuntu 18.04: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_7.0.0-1.ubuntu.18.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo dpkg -i powershell_7.0.0-1.ubuntu.18.04_amd64.deb
sudo apt-get install -f
```

> [!NOTE]
> Il comando `dpkg -i` ha esito negativo con dipendenze non soddisfatte. Il comando successivo `apt-get install -f` risolve tali problemi e completa la configurazione del pacchetto PowerShell.

### <a name="uninstallation---ubuntu-1804"></a>Ubuntu 18.04: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="ubuntu-1810"></a>Ubuntu 18.10

L'installazione è supportata tramite `snapd`. Per le istruzioni, vedere [Pacchetto Snap][snap].

> [!NOTE]
> Ubuntu 18.10 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle)[supportata dalla community](../powershell-support-lifecycle.md).

## <a name="ubuntu-1904"></a>Ubuntu 19.04

L'installazione è supportata tramite `snapd`. Per le istruzioni, vedere [Pacchetto Snap][snap].

> [!NOTE]
> Ubuntu 19.04 è una [versione provvisoria](https://www.ubuntu.com/about/release-cycle)[supportata dalla community](../powershell-support-lifecycle.md).

## <a name="debian-8"></a>Debian 8

### <a name="installation-via-package-repository---debian-8"></a>Debian 8: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.

Il metodo preferito è il seguente:

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

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.

## <a name="debian-9"></a>Debian 9

### <a name="installation-via-package-repository---debian-9"></a>Debian 9: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository dei pacchetti.

Il metodo preferito è il seguente:

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

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo apt-get upgrade powershell`.

### <a name="installation-via-direct-download---debian-9"></a>Debian 9: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_7.0.0-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo dpkg -i powershell_7.0.0-1.debian.9_amd64.deb
sudo apt-get install -f
```

### <a name="uninstallation---debian-9"></a>Debian 9: disinstallazione

```sh
sudo apt-get remove powershell
```

## <a name="debian-10"></a>Debian 10

> [!NOTE]
> Debian 10 è supportato solo in PowerShell 7.0 e versioni successive.

### <a name="installation-via-direct-download---debian-10"></a>Debian 10: installazione tramite download diretto

Scaricare il pacchetto tar. gz `powershell_7.0.0-linux-x64.tar.gz` dalla pagina delle [versioni][] nel computer Debian.

Nel terminale eseguire quindi i comandi seguenti:

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

## <a name="alpine-39-and-310"></a>Alpine 3.9 e 3.10

> [!NOTE]
> Alpine 3.9 e 3.10 sono supportati solo in PowerShell 7.0 e versioni successive.

### <a name="installation-via-direct-download---alpine-39-and-310"></a>Alpine 3.9 e 3.10: installazione tramite download diretto

Scaricare il pacchetto tar.gz `powershell-7.0.0-linux-alpine-x64.tar.gz` dalla pagina delle [versioni][] nel computer Alpine.

Nel terminale eseguire quindi i comandi seguenti:

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

## <a name="centos-7"></a>CentOS 7

> [!NOTE]
> Questo pacchetto funziona in Oracle Linux 7.

### <a name="installation-via-package-repository-preferred---centos-7"></a>CentOS 7: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.

### <a name="installation-via-direct-download---centos-7"></a>CentOS 7: installazione tramite download diretto

Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---centos-7"></a>CentOS 7: disinstallazione

```sh
sudo yum remove powershell
```

[CentOS 7]: https://www.centos.org/download/

## <a name="red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7

### <a name="installation-via-package-repository-preferred---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: installazione tramite repository dei pacchetti (scelta consigliata)

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.

```sh
# Register the Microsoft RedHat repository
curl https://packages.microsoft.com/config/rhel/7/prod.repo | sudo tee /etc/yum.repos.d/microsoft.repo

# Install PowerShell
sudo yum install -y powershell

# Start PowerShell
pwsh
```

Come utente con privilegi avanzati, registrare il repository di Microsoft una volta. Dopo la registrazione, è possibile aggiornare PowerShell con `sudo yum update powershell`.

### <a name="installation-via-direct-download---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: installazione tramite download diretto

Scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo yum install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
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

### <a name="installation---opensuse-leap-15"></a>Installazione - openSUSE Leap 15

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

### <a name="uninstallation---opensuse-423-opensuse-leap-15"></a>Disinstallazione - openSUSE 42.3, openSUSE Leap 15

```sh
rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="fedora"></a>Fedora

> [!NOTE]
> Fedora 28 è supportato solo in PowerShell 6.1 e versioni successive.

> [!NOTE]
> Fedora 29 e 30 sono supportati solo in PowerShell 7.0 e versioni successive.

### <a name="installation-via-package-repository-preferred---fedora-28-29-and-30"></a>Fedora 28, 29 e 30: installazione tramite repository dei pacchetti (scelta consigliata)

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nei repository Microsoft ufficiali.

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

### <a name="installation-via-direct-download---fedora-28-29-and-30"></a>Fedora 28, 29 e 30: installazione tramite download diretto

Scaricare il pacchetto RPM `powershell-7.0.0-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.

Nel terminale eseguire quindi i comandi seguenti:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-7.0.0-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v7.0.0/powershell-7.0.0-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---fedora-28-29-and-30"></a>Fedora 28, 29 e 30: disinstallazione

```sh
sudo dnf remove powershell
```

## <a name="arch-linux"></a>Arch Linux

> [!NOTE]
> Il supporto Arch non è ufficialmente supportato da Microsoft e viene gestito dalla community.

PowerShell è disponibile nell'[Arch Linux][] User Repository (AUR).

* Può essere compilato con la [versione con tag più recente][arch-release]
* Può essere compilato dall'[ultima esecuzione del commit al master][arch-git]
* Può essere installato usando il [file binario della versione più recente][arch-bin]

I pacchetti disponibili in AUR sono gestiti dalla community. Non esiste supporto ufficiale.

Per altre informazioni sull'installazione dei pacchetti da AUR, vedere il [wiki Arch Linux](https://wiki.archlinux.org/index.php/Arch_User_Repository#Installing_packages) o fare riferimento alla community [DockerFile](https://github.com/PowerShell/PowerShell/blob/master/docker/community/archlinux/Dockerfile).

[Arch Linux]: https://www.archlinux.org/download/
[arch-release]: https://aur.archlinux.org/packages/powershell/
[arch-git]: https://aur.archlinux.org/packages/powershell-git/
[arch-bin]: https://aur.archlinux.org/packages/powershell-bin/

## <a name="snap-package"></a>Pacchetto Snap

### <a name="getting-snapd"></a>Recupero di snapd

`snapd` è necessario per l'esecuzione di pacchetti Snap. Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.

### <a name="installation-via-snap"></a>Installazione tramite Snap

Per semplificare l'installazione e gli aggiornamenti, PowerShell per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).

Il metodo preferito è il seguente:

```sh
# Install PowerShell
sudo snap install powershell --classic

# Start PowerShell
pwsh
```

Per installare una versione di anteprima, usare il metodo seguente:

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Dopo l'installazione, Snap verrà aggiornato automaticamente. È possibile attivare un aggiornamento usando `sudo snap refresh powershell` o `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Disinstallazione

```sh
sudo snap remove powershell
```

o

```sh
sudo snap remove powershell-preview
```

## <a name="kali"></a>Kali

> [!NOTE]
> Il supporto Kali non è ufficialmente supportato da Microsoft e viene gestito dalla community.

### <a name="installation---kali"></a>Kali: installazione

```sh
# Install PowerShell package
apt update && apt -y install powershell

# Start PowerShell
pwsh
```

### <a name="uninstallation---kali"></a>Kali: disinstallazione

```sh
# Uninstall PowerShell package
apt -y remove powershell
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Il supporto di Raspbian è sperimentale.

Attualmente, PowerShell è supportato solo in Raspbian Stretch.

CoreCLR e PowerShell funzionano solo nei dispositivi Pi 2 e Pi 3, perché altri dispositivi come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605) hanno un processore non supportato.

Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.

### <a name="installation---raspbian"></a>Raspbian: installazione

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

Facoltativamente, è possibile creare un collegamento simbolico per avviare PowerShell senza specificare il percorso del file binario `pwsh`.

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

## <a name="install-as-a-net-global-tool"></a>Installare come strumento globale .NET

Se [.NET Core SDK](/dotnet/core/sdk) è già installato, è facile installare PowerShell come [strumento globale .NET](/dotnet/core/tools/global-tools).

```
dotnet tool install --global PowerShell
```

Il programma di installazione dello strumento DotNet aggiunge `~/.dotnet/tools` alla variabile di ambiente `PATH`. La shell attualmente in esecuzione non dispone tuttavia del parametro `PATH` aggiornato. Dovrebbe essere possibile avviare PowerShell da una nuova shell digitando `pwsh`.

## <a name="binary-archives"></a>Archivi di file binari

Gli archivi `tar.gz` di file binari di PowerShell possono essere usati per le piattaforme Linux per abilitare scenari di distribuzione avanzati.

### <a name="dependencies"></a>Dependencies

PowerShell compila file binari portabili per tutte le distribuzioni di Linux. Per il runtime di .NET Core sono tuttavia necessarie dipendenze diverse nelle varie distribuzioni, così come per PowerShell.

La tabella seguente illustra le dipendenze di .NET Core 2.0 ufficialmente supportate in varie distribuzioni di Linux.

| OS                 | Dependencies |
| ------------------ | ------------ |
| Ubuntu 16.04       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu55 |
| Ubuntu 17.10       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu57 |
| Ubuntu 18.04       | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu60 |
| Debian 8 (Jessie)  | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.0, libicu52 |
| Debian 9 (Stretch) | libc6, libgcc1, 2, krb5 libgssapi liblttng-ust0, libstdc + + 6, <br> libcurl3, libunwind8, libuuid1, zlib1g, libssl1.0.2, libicu57 |
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 | libunwind, libcurl, openssl-libs, libicu |
| openSUSE 42.3 | libcurl4, libopenssl1_0_0, libicu52_1 |
| openSUSE Leap 15 | libcurl4, libopenssl1_0_0, libicu60_2 |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie per il sistema operativo di destinazione in passaggi distinti. Ad esempio, il [Dockerfile Linux di Amazon][amazon-dockerfile] installa prima le dipendenze e quindi estrae l'archivio `tar.gz` di Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell-Docker/blob/master/release/community-stable/amazonlinux/docker/Dockerfile

### <a name="installation---binary-archives"></a>Archivi di file binari: installazione

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Disinstallazione degli archivi binari

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Percorsi

- `$PSHOME` è `/opt/microsoft/powershell/7/`
- I profili utente vengono letti da `~/.config/powershell/profile.ps1`
- I profili predefiniti vengono letti da `$PSHOME/profile.ps1`
- I moduli utente vengono letti da `~/.local/share/powershell/Modules`
- I moduli condivisi vengono letti da `/usr/local/share/powershell/Modules`
- I moduli predefiniti vengono letti da `$PSHOME/Modules`
- La cronologia PSReadline viene registrata in `~/.local/share/powershell/PSReadLine/ConsoleHost_history.txt`

I profili di rispettano la configurazione per ogni host di PowerShell, pertanto i profili predefiniti specifici per l'host si trovano in `Microsoft.PowerShell_profile.ps1` negli stessi percorsi.

PowerShell rispetta la [specifica XDG Base Directory][xdg-bds] in Linux.

[versioni]: https://github.com/PowerShell/PowerShell/releases/latest
[xdg-bds]: https://specifications.freedesktop.org/basedir-spec/basedir-spec-latest.html
