---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Introduzione a DSC (Desired State Configuration) per Linux
ms.openlocfilehash: 4fd8460bc5d2564cab291904b60a1a0c26c3e5a7
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="get-started-with-desired-state-configuration-dsc-for-linux"></a>Introduzione a DSC (Desired State Configuration) per Linux

Questo argomento illustra come iniziare a usare PowerShell DSC (Desired State Configuration) per Linux. Per informazioni generali su DSC, vedere [Introduzione a Windows PowerShell DSC (Desired State Configuration)](overview.md).

## <a name="supported-linux-operation-system-versions"></a>Versioni del sistema operativo Linux supportate

DSC per Linux supporta le versioni seguenti del sistema operativo Linux.
- CentOS 5, 6 e 7 (x86/x64)
- Debian GNU/Linux 6, 7 e 8 (x86/x64)
- Oracle Linux 5, 6 e 7 (x86/x64)
- Red Hat Enterprise Linux Server 5, 6 e 7 (x86/x64)
- SUSE Linux Enterprise Server 10, 11 e 12 (x86/x64)
- Ubuntu Server 12.04 LTS, 14.04 LTS e 16.04 LTS (x86/x64)

La tabella seguente descrive le dipendenze dei pacchetti necessarie per DSC per Linux.

|  Pacchetto necessario |  Description |  Versione minima | 
|---|---|---|
| glibc| Libreria GNU| 2…4 - 31.30| 
| python| Python| 2.4 - 3.4| 
| omiserver| OMI (Open Management Infrastructure)| 1.0.8.1| 
| openssl| Librerie OpenSSL| 0.9.8 o 1.0| 
| ctypes| Libreria Python CTypes| La versione deve corrispondere a quella di Python| 
| libcurl| Libreria client HTTP cURL| 7.15.1| 

## <a name="installing-dsc-for-linux"></a>Installazione di DSC per Linux

Prima di installare DSC per Linux, è necessario installare [OMI (Open Management Infrastructure)](https://github.com/Microsoft/omi).

### <a name="installing-omi"></a>Installazione di OMI

DSC (Desired State Configuration) per Linux richiede il server CIM OMI (Open Management Infrastructure), versione 1.0.8.1 o successive. È possibile scaricare OMI dal sito The Open Group: [Open Management Infrastructure (OMI)](https://github.com/Microsoft/omi).

Per installare OMI, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86). I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server. I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.

> **Nota**: per determinare la versione di OpenSSL installata, eseguire il comando `openssl version`.

Eseguire il comando seguente per installare OMI in un sistema CentOS 7 x64.

`# sudo rpm -Uvh omiserver-1.0.8.ssl_100.rpm`

### <a name="installing-dsc"></a>Installazione di DSC

DSC per Linux è disponibile per il download [qui](https://github.com/Microsoft/PowerShell-DSC-for-Linux/releases/latest). 

Per installare DSC, installare il pacchetto appropriato per il sistema Linux (RPM o DEB), la versione OpenSSL (ssl_098 o ssl_100) e l'architettura (x64/x86). I pacchetti RPM sono appropriati per CentOS, Red Hat Enterprise Linux, SUSE Linux Enterprise Server e Oracle Linux. I pacchetti DEB sono appropriati per Debian GNU/Linux e Ubuntu Server. I pacchetti ssl_098 sono appropriati per i computer in cui è installato OpenSSL 0.9.8, mentre i pacchetti ssl_100 sono appropriati per i computer in cui è installato OpenSSL 1.0.

> **Nota**: per determinare la versione di OpenSSL installata, eseguire il comando openssl version.
 
Eseguire il comando seguente per installare DSC in un sistema CentOS 7 x64.

`# sudo rpm -Uvh dsc-1.0.0-254.ssl_100.x64.rpm`


## <a name="using-dsc-for-linux"></a>Uso di DSC per Linux

Le sezioni seguenti illustrano come creare ed eseguire configurazioni DSC nei computer Linux.

### <a name="creating-a-configuration-mof-document"></a>Creazione di un documento MOF di configurazione

La parola chiave Configuration di Windows PowerShell viene usata per creare una configurazione per i computer Linux, esattamente come per i computer Windows. I passaggi seguenti descrivono la creazione di un documento di configurazione per un computer Linux con Windows PowerShell.

1. Importare il modulo nx. Il modulo nx di Windows PowerShell contiene lo schema per le risorse incorporate per DSC per Linux e deve essere installato nel computer locale e importato nella configurazione.

    - Per installare il modulo nx, copiare la directory del modulo nx in `$env:USERPROFILE\Documents\WindowsPowerShell\Modules\` o `$PSHOME\Modules`. Il modulo nx è incluso nel pacchetto di installazione (MSI) di DSC per Linux. Per importare il modulo nx nella configurazione, usare il comando __Import-DSCResource__:
    
```powershell
Configuration ExampleConfiguration{
   
    Import-DSCResource -Module nx

}
```
2. Definire una configurazione e generare il documento di configurazione:

```powershell
Configuration ExampleConfiguration{
   
    Import-DscResource -Module nx
 
    Node  "linuxhost.contoso.com"{
    nxFile ExampleFile {

        DestinationPath = "/tmp/example"
        Contents = "hello world `n"
        Ensure = "Present"
        Type = "File"
    }

    }
}
ExampleConfiguration -OutputPath:"C:\temp" 
```

### <a name="push-the-configuration-to-the-linux-computer"></a>Effettuare il push della configurazione nel computer Linux

È possibile effettuare il push dei documenti di configurazione (file MOF) nel computer Linux usando il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Per usare questo cmdlet, insieme ai cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx) o [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx), in remoto in un computer Linux, è necessario usare una sessione CIMSession. Il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967) viene usato per creare una sessione CIMSession nel computer Linux.

Il codice seguente illustra come creare una sessione CIMSession per DSC per Linux.

```powershell
$Node = "ostc-dsc-01"
$Credential = Get-Credential -UserName:"root" -Message:"Enter Password:"

#Ignore SSL certificate validation
#$opt = New-CimSessionOption -UseSsl:$true -SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true

#Options for a trusted SSL certificate
$opt = New-CimSessionOption -UseSsl:$true 
$Sess=New-CimSession -Credential:$credential -ComputerName:$Node -Port:5986 -Authentication:basic -SessionOption:$opt -OperationTimeoutSec:90 
```

> **Nota**:
* Per la modalità "Push", le credenziali dell'utente devono corrispondere all'utente ROOT nel computer Linux.
* DSC per Linux supporta solo le connessioni SSL/TLS. Il cmdlet New-CimSession deve essere usato con il parametro –UseSSL impostato su $true.
* Il certificato SSL usato da OMI (per DSC) è specificato nel file: `/opt/omi/etc/omiserver.conf` con le proprietà: pemfile e keyfile.
Se il certificato non è considerato attendibile dal computer Windows in cui si esegue il cmdlet [New-CimSession](http://go.microsoft.com/fwlink/?LinkId=227967), è possibile scegliere di ignorare la convalida del certificato con le opzioni di CIMSession: `-SkipCACheck:$true -SkipCNCheck:$true -SkipRevocationCheck:$true`

Eseguire il comando seguente per effettuare il push della configurazione DSC nel nodo Linux.

`Start-DscConfiguration -Path:"C:\temp" -CimSession:$Sess -Wait -Verbose`

### <a name="distribute-the-configuration-with-a-pull-server"></a>Distribuire la configurazione con un server di pull

Le configurazioni possono essere distribuite in un computer Linux con un server di pull, esattamente come per i computer Windows. Per informazioni sull'uso di un server di pull, vedere [Server di pull Windows PowerShell DSC (Desired Configuration Pull)](pullServer.md). Per altre informazioni e per conoscere le limitazioni relative all'uso di computer Linux con un server di pull, vedere le note sulla versione per DSC per Linux.

### <a name="working-with-configurations-locally"></a>Uso di configurazioni in locale

DSC per Linux include gli script per usare la configurazione dal computer Linux locale. Questi script si trovano in `/opt/microsoft/dsc/Scripts` e includono quanto segue:
* GetDscConfiguration.py

 Restituisce la configurazione corrente applicata al computer. Simile al cmdlet Get-DscConfiguration di Windows PowerShell.

`# sudo ./GetDscConfiguration.py`

* GetDscLocalConfigurationManager.py

 Restituisce la metaconfigurazione corrente applicata al computer. Simile al cmdlet [Get-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn407378.aspx).

`# sudo ./GetDscLocalConfigurationManager.py`

* InstallModule.py

 Installa un modulo di risorse DSC personalizzato. Richiede il percorso di un file ZIP contenente la libreria di oggetti condivisi del modulo e i file MOF dello schema.

`# sudo ./InstallModule.py /tmp/cnx_Resource.zip`

* RemoveModule.py

 Rimuove un modulo di risorse DSC personalizzato. Richiede il nome del modulo da rimuovere.

`# sudo ./RemoveModule.py cnx_Resource`

* StartDscLocalConfigurationManager.py 

 Applica un file MOF di configurazione al computer. Simile al cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx). Richiede il percorso del file MOF di configurazione da applicare.

`# sudo ./StartDscLocalConfigurationManager.py –configurationmof /tmp/localhost.mof`

* SetDscLocalConfigurationManager.py

 Applica un file MOF di metaconfigurazione al computer. Simile al cmdlet [Set-DSCLocalConfigurationManager](https://technet.microsoft.com/en-us/library/dn521621.aspx). Richiede il percorso del file MOF di metaconfigurazione da applicare.

`# sudo ./SetDscLocalConfigurationManager.py –configurationmof /tmp/localhost.meta.mof`

## <a name="powershell-desired-state-configuration-for-linux-log-files"></a>File di registro di PowerShell DSC (Desired State Configuration) per Linux

I file di registro seguenti vengono generati per i messaggi di DSC per Linux.

|File di registro|Directory|Description|
|---|---|---|
|omiserver.log|/var/opt/omi/log|Messaggi relativi al funzionamento del server CIM OMI.|
|dsc.log|/var/opt/omi/log|Messaggi relativi al funzionamento delle operazioni delle risorse DSC e di Gestione configurazione locale.|

