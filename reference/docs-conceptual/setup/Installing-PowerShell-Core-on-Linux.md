---
title: Installazione di PowerShell Core in Linux
description: Informazioni sull'installazione di PowerShell Core in varie distribuzioni Linux
ms.date: 08/06/2018
ms.openlocfilehash: a6b0e3003f84ea6dc99cffcc7edf1b5b6963aa21
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587449"
---
# <a name="installing-powershell-core-on-linux"></a>Installazione di PowerShell Core in Linux

Supporta [Ubuntu 14.04][u14], [Ubuntu 16.04][u16], [Ubuntu 18.10][u18], [Debian 8][deb8], [Debian 9][deb9], [CentOS 7][cos], [Red Hat Enterprise Linux (RHEL) 7][rhel7], [OpenSUSE 42.3][opensuse], [Fedora 27][fedora], [Fedora 28][fedora] e [Arch Linux][arch].

Per le distribuzioni di Linux non supportate ufficialmente, è possibile provare a usare il [pacchetto Snap di PowerShell][snap].
È anche possibile provare a distribuire i file binari di PowerShell direttamente usando l'[`tar.gz`archivio][tar] di Linux. Si devono comunque configurare le dipendenze necessarie in base al sistema operativo in passaggi distinti.

Tutti i pacchetti sono disponibili nella pagina delle [versioni][] di GitHub.
Dopo aver installato il pacchetto, eseguire `pwsh` da un terminale.

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

## <a name="installing-preview-releases"></a>Installazione di versioni di anteprima

Quando si installa una versione di anteprima di PowerShell Core per Linux tramite un repository dei pacchetti, il nome del pacchetto viene modificato da `powershell` a `powershell-preview`.

L'installazione tramite download diretto non cambia, tranne per il nome del file.

Segue una tabella dei comandi per installare i pacchetti stabili e anteprima usando diversi strumenti di Gestione pacchetti:

|Distribuzione/i|Comando pacchetto stabile | Comando pacchetto anteprima |
|---------------|---------------|-----------------|
| Ubuntu, Debian |`sudo apt-get install -y powershell`| `sudo apt-get install -y powershell-preview`|
| CentOS, RedHat |`sudo yum install -y powershell` | `sudo yum install -y powershell-preview`|
| OpenSUSE |`sudo zypper install powershell` | `sudo zypper install powershell-preview`|
| Fedora   |`sudo dnf install -y powershell` | `sudo dnf install -y powershell-preview`|

## <a name="ubuntu-1404"></a>Ubuntu 14.04

### <a name="installation-via-package-repository---ubuntu-1404"></a>Ubuntu 14.04: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository dei pacchetti.
Questo è il metodo preferito.

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

Come utente con privilegi avanzati, registrare il repository di Microsoft.
A questo punto, è sufficiente usare `sudo apt-get upgrade powershell` per aggiornare l'installazione.

### <a name="installation-via-direct-download---ubuntu-1404"></a>Ubuntu 14.04: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.14.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.14.04_amd64.deb
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

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---ubuntu-1604"></a>Installazione tramite download diretto - Ubuntu 16.04

Scaricare il pacchetto Debian `powershell_6.0.2-1.ubuntu.16.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.0.2-1.ubuntu.16.04_amd64.deb
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
# Import the public repository GPG keys
curl https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -

# Register the Microsoft Ubuntu repository
sudo curl -o /etc/apt/sources.list.d/microsoft.list https://packages.microsoft.com/config/ubuntu/18.04/prod.list

# Update the list of products
sudo apt-get update

# Install PowerShell
sudo apt-get install -y powershell-preview

# Start PowerShell
pwsh-preview
```

Dopo essersi registrati una volta come utente con privilegi avanzati nel repository di Microsoft, è sufficiente usare `sudo apt-get upgrade powershell` per eseguirne l'aggiornamento.

### <a name="installation-via-direct-download---ubuntu-1804"></a>Ubuntu 18.04: installazione tramite download diretto

Scaricare il pacchetto Debian `powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb` dalla pagina delle [versioni][] nel computer Ubuntu.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.1.0-preview.3-1.ubuntu.18.04_amd64.deb
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

Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.8_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.8_amd64.deb
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

Scaricare il pacchetto Debian `powershell_6.0.2-1.debian.9_amd64.deb` dalla pagina delle [versioni][] nel computer Debian.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dpkg -i powershell_6.0.2-1.debian.9_amd64.deb
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

Usando [CentOS 7][], scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer CentOS.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Red Hat Enterprise Linux.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo yum install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo yum install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---red-hat-enterprise-linux-rhel-7"></a>Red Hat Enterprise Linux (RHEL) 7: disinstallazione

```sh
sudo yum remove powershell
```

## <a name="opensuse-423"></a>OpenSUSE 42.3

Durante l'installazione di PowerShell Core, `zypper` può segnalare l'errore seguente:

```Output
Problem: nothing provides libcurl needed by powershell-6.0.1-1.rhel.7.x86_64
 Solution 1: do not install powershell-6.0.1-1.rhel.7.x86_64
 Solution 2: break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies
```

In questo caso, verificare che sia presente una libreria `libcurl` compatibile assicurandosi che il comando seguente indichi il pacchetto `libcurl4` come installato:

```sh
zypper search --file-list --match-exact '/usr/lib64/libcurl.so.4'
```

Scegliere quindi la soluzione `break powershell-6.0.1-1.rhel.7.x86_64 by ignoring some of its dependencies` quando si installa il pacchetto PowerShell.

### <a name="installation-via-package-repository-preferred---opensuse-423"></a>OpenSUSE 42.3: installazione tramite repository dei pacchetti

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nei repository Microsoft ufficiali.

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

### <a name="installation-via-direct-download---opensuse-423"></a>OpenSUSE 42.3: installazione tramite download diretto

Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer OpenSUSE.

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo zypper install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
```

### <a name="uninstallation---opensuse-423"></a>OpenSUSE 42.3: disinstallazione

```sh
sudo zypper remove powershell
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

Scaricare il pacchetto RPM `powershell-6.0.2-1.rhel.7.x86_64.rpm` dalla pagina delle [versioni][] nel computer Fedora.

A questo punto eseguire quanto segue nel terminale:

```sh
sudo dnf install compat-openssl10
sudo dnf install powershell-6.0.2-1.rhel.7.x86_64.rpm
```

È possibile installare il pacchetto RPM anche senza eseguire il passaggio intermedio di download del pacchetto:

```sh
sudo dnf install compat-openssl10
sudo dnf install https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-1.rhel.7.x86_64.rpm
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

`snapd` è necessario per l'esecuzione di pacchetti Snap.  Usare [queste istruzioni](https://docs.snapcraft.io/core/install) per assicurarsi di avere installato `snapd`.

### <a name="installation-via-snap"></a>Installazione tramite Snap

Per semplificare l'installazione e gli aggiornamenti, PowerShell Core per Linux è pubblicato nello [store Snap](https://snapcraft.io/store).
Questo è il metodo preferito.

```sh
# Install PowerShell
sudo snap install powershell-preview --classic

# Start PowerShell
pwsh-preview
```

Dopo l'installazione, Snap eseguirà automaticamente l'aggiornamento, ma è possibile attivare un aggiornamento usando `sudo snap refresh powershell-preview`.

### <a name="uninstallation"></a>Disinstallazione

```sh
sudo snap remove powershell-preview
```

## <a name="linux-appimage"></a>Linux AppImage

> [!NOTE]
> Il supporto di AppImage è sperimentale.

Usando una distribuzione Linux recente, scaricare `powershell-6.0.1-x86_64.AppImage` di AppImage dalla pagina delle [versioni][] nel computer Linux.

A questo punto eseguire quanto segue nel terminale:

```bash
chmod a+x powershell-6.0.1-x86_64.AppImage
./powershell-6.0.1-x86_64.AppImage
```

[AppImage][] consente di eseguire PowerShell senza doverlo installare.
È un'applicazione portabile che aggiunge PowerShell e le relative dipendenze (incluse le dipendenze di sistema di .NET Core) a un pacchetto integrato.
Questo pacchetto è un singolo file binario che funziona indipendentemente dalla distribuzione di Linux dell'utente.

[appimage]: http://appimage.org/

## <a name="kali"></a>Kali

> [!NOTE]
> Il supporto di Kali è sperimentale.

### <a name="installation"></a>Installazione

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

### <a name="run-powershell-in-latest-kali-kali-gnulinux-rolling-without-installing-it"></a>Eseguire PowerShell nella versione Kali più recente (GNU/Linux Kali Rolling) senza eseguire l'installazione

```sh
# Grab the latest App Image
wget https://github.com/PowerShell/PowerShell/releases/download/v6.0.2/powershell-6.0.2-x86_64.AppImage

# Make executable
chmod a+x powershell-6.0.2-x86_64.AppImage

# Start PowerShell
./powershell-6.0.2-x86_64.AppImage
```

### <a name="uninstallation---kali"></a>Kali: disinstallazione

```sh
sudo dpkg -r powershell_6.0.2-1.ubuntu.16.04_amd64.deb
```

## <a name="raspbian"></a>Raspbian

> [!NOTE]
> Il supporto di Raspbian è sperimentale.

Attualmente, PowerShell è supportato solo in Raspbian Stretch.

Inoltre, CoreCLR (e quindi PowerShell Core) funziona solo sui dispositivi Pi 2 e 3 Pi, perché altri dispositivi, come [Pi Zero](https://github.com/dotnet/coreclr/issues/10605), dispongono di un processore non supportato.

Scaricare [Raspbian Stretch](https://www.raspberrypi.org/downloads/raspbian/) e seguire le [istruzioni di installazione](https://www.raspberrypi.org/documentation/installation/installing-images/README.md) per installarlo nel dispositivo Pi.

### <a name="installation"></a>Installazione

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
| CentOS 7 <br> Oracle Linux 7 <br> RHEL 7 <br> OpenSUSE OpenSUSE 42.3 | libunwind, libcurl, openssl-libs, libicu |
| Fedora 27 <br> Fedora 28 | libunwind, libcurl, openssl-libs, libicu, compat-openssl10 |

Per distribuire i file binari di PowerShell in distribuzioni di Linux non ufficialmente supportate, si devono installare le dipendenze necessarie al sistema operativo di destinazione in due passaggi distinti.
Ad esempio, il [dockerfile di Amazon Linux ][amazon-dockerfile] installa prima le dipendenze e poi estrae l'archivio `tar.gz` di Linux.

[amazon-dockerfile]: https://github.com/PowerShell/PowerShell/blob/master/docker/community/amazonlinux/Dockerfile

### <a name="installation---binary-archives"></a>Archivi di file binari: installazione

#### <a name="linux"></a>Linux

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

### <a name="uninstalling-binary-archives"></a>Disinstallazione degli archivi binari

```sh
sudo rm -rf /usr/bin/pwsh /opt/microsoft/powershell
```

## <a name="paths"></a>Percorsi

* `$PSHOME` è `/opt/microsoft/powershell/6.0.2/`
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
