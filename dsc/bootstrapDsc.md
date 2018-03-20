---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Configurare una macchina virtuale all'avvio iniziale tramite DSC
ms.openlocfilehash: ff06aafa6db49d93a9b42e38ac7c3e9a11657bd5
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
>Si applica a: Windows PowerShell 5.0

>**Nota:** la chiave del Registro di sistema **DSCAutomationHostEnabled** descritta in questo argomento non è disponibile in PowerShell 4.0.
Per informazioni su come configurare nuove macchine virtuali all'avvio iniziale di PowerShell 4.0, vedere [Want to Automatically Configure Your Machines Using DSC at Initial Boot-up?](https://blogs.msdn.microsoft.com/powershell/2014/02/28/want-to-automatically-configure-your-machines-using-dsc-at-initial-boot-up/) (Configurare automaticamente le macchine virtuali usando DSC all'avvio iniziale)

# <a name="configure-a-virtual-machines-at-initial-boot-up-by-using-dsc"></a>Configurare una macchina virtuale all'avvio iniziale tramite DSC

## <a name="requirements"></a>Requisiti

Per eseguire questi esempi, è necessario:

- Un disco rigido virtuale di avvio. È possibile scaricare un'immagine ISO con una copia di valutazione di Windows Server 2016 in [TechNet Evaluation Center](https://www.microsoft.com/evalcenter/evaluate-windows-server-2016). È possibile trovare istruzioni su come creare un disco rigido virtuale da un'immagine ISO in [Creating Bootable Virtual Hard Disks](https://technet.microsoft.com/library/gg318049.aspx) (Creazione di dischi rigidi virtuali di avvio).
- Un computer host con Hyper-V abilitato. Per altre informazioni, vedere [Panoramica di Hyper-V](https://technet.microsoft.com/library/hh831531.aspx).

Tramite DSC, è possibile automatizzare l'installazione del software e la configurazione di un computer all'avvio iniziale.
A tale scopo, inserire un documento di configurazione MOF o una metaconfigurazione nei supporti di avvio (ad esempio, un disco rigido Virtuale) in modo che vengano eseguiti durante il processo di avvio iniziale.
Questo comportamento viene specificato dalla [chiave del Registro di sistema DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies**.
Per impostazione predefinita, il valore di questa chiave è 2, che consente l'esecuzione di DSC all'avvio.

Se si preferisce che DSC non venga eseguito all'avvio, impostare il valore della [chiave del Registro di sistema DSCAutomationHostEnabled](DSCAutomationHostEnabled.md) su 0.

- Inserire un documento MOF in un disco rigido virtuale
- Inserire una metaconfigurazione DSC in un disco rigido virtuale
- Disabilitare DSC in fase di avvio

>**Nota:** è possibile inserire `Pending.mof` e `MetaConfig.mof` in un computer contemporaneamente.
Se entrambi i file sono presenti, le impostazioni specificate in `MetaConfig.mof` hanno la precedenza.

## <a name="inject-a-configuration-mof-document-into-a-vhd"></a>Inserire un documento MOF in un disco rigido virtuale

Per applicare una configurazione all'avvio iniziale, è possibile inserire un documento di configurazione MOF compilato nel disco rigido virtuale come file `Pending.mof`.
Se la chiave del Registro di sistema **DSCAutomationHostEnabled** è impostata su 2 (valore predefinito), DSC applicherà la configurazione definita da `Pending.mof` quando il computer viene avviato per la prima volta.

Per questo esempio, verrà usata la configurazione seguente, che consente di installare IIS nel nuovo computer:

```powershell
Configuration SampleIISInstall
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    node ('localhost')
    {
        WindowsFeature IIS
        {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
    }
}
```

### <a name="to-inject-the-configuration-mof-document-on-the-vhd"></a>Per inserire il documento di configurazione MOF nel disco rigido virtuale

1. Montare il disco rigido virtuale in cui si vuole inserire la configurazione mediante la chiamata al cmdlet [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx). Ad esempio:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```
2. In un computer che esegue PowerShell 5.0 o versione successiva salvare la configurazione precedente (**SampleIISInstall**) come file di script PowerShell (con estensione ps1).

3. Nella console di PowerShell, passare alla cartella in cui è stato salvato il file con estensione ps1.

4. Eseguire i comandi PowerShell seguenti per compilare il documento MOF. Per informazioni sulla compilazione delle configurazioni DSC, vedere [Configurazioni DSC](configurations.md):

    ```powershell
    . .\SampleIISInstall.ps1
    SampleIISInstall
    ```

5. Verrà creato un file `localhost.mof` in una nuova cartella denominata `SampleIISInstall`.
Spostare il file nella posizione corretta del disco rigido virtuale e rinominarlo come `Pending.mof` usando il cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx). Ad esempio:

    ```powershell
        Move-Item -Path C:\DSCTest\SampleIISInstall\localhost.mof -Destination E:\Windows\System32\Configuration\Pending.mof
    ```
6. Smontare il disco rigido virtuale tramite la chiamata al cmdlet [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx). Ad esempio:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

7. Creare una macchina virtuale usando il disco rigido virtuale in cui è installato il documento MOF di DSC. Dopo l'avvio iniziale e l'installazione del sistema operativo, verrà installato IIS.
È possibile verificare questo aspetto chiamando il cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="inject-a-dsc-metaconfiguration-into-a-vhd"></a>Inserire una metaconfigurazione DSC in un disco rigido virtuale

È inoltre possibile configurare un computer per eseguire il pull di una configurazione all'avvio iniziale inserendo una metaconfigurazione (vedere [Configurazione di Gestione configurazione locale](metaConfig.md)) nel disco rigido virtuale come file `MetaConfig.mof`.
Se la chiave del Registro di sistema **DSCAutomationHostEnabled** è impostata su 2 (valore predefinito), DSC applicherà la metaconfigurazione definita da `MetaConfig.mof` a Gestione configurazione locale quando il computer viene avviato per la prima volta.
Se la metaconfigurazione specifica che Gestione configurazione locale deve inserire le configurazioni da un server di pull, il computer tenterà di estrarre una configurazione da tale server di pull all'avvio iniziale.
Per informazioni sulla configurazione di un server di pull DSC, vedere [Configurazione di un server di pull Web DSC](pullServer.md).

Per questo esempio, verranno usate la configurazione descritta nella sezione precedente (**SampleIISInstall**) e la metaconfigurazione seguente:

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientBootstrap
{
    Node localhost
    {
        Settings
        {
            RefreshMode = 'Pull'
            RefreshFrequencyMins = 30
            RebootNodeIfNeeded = $true
        }
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('SampleIISInstall')
        }
    }
}
```

### <a name="to-inject-the-metaconfiguration-mof-document-on-the-vhd"></a>Per inserire il documento di metaconfigurazione MOF nel disco rigido virtuale

1. Montare il disco rigido virtuale in cui si vuole inserire la metaconfigurazione mediante la chiamata al cmdlet [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx). Ad esempio:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. [Configurare un server di pull Web DSC](pullServer.md) e salvare la configurazione **SampleIISInistall** nella cartella appropriata.

3. In un computer che esegue PowerShell 5.0 o versione successiva salvare la metaconfigurazione precedente (**PullClientBootstrap**) come file di script PowerShell (con estensione ps1).

4. Nella console di PowerShell passare alla cartella in cui è stato salvato il file con estensione ps1.

5. Eseguire i comandi PowerShell seguenti per compilare il documento di metaconfigurazione MOF. Per informazioni sulla compilazione delle configurazioni DSC, vedere [Configurazioni DSC](configurations.md):

    ```powershell
    . .\PullClientBootstrap.ps1
    PullClientBootstrap
    ```

6. Verrà creato un file `localhost.meta.mof` in una nuova cartella denominata `PullClientBootstrap`.
Spostare il file nella posizione corretta del disco rigido virtuale e rinominarlo come `MetaConfig.mof` usando il cmdlet [Move-Item](https://technet.microsoft.comlibrary/hh849852.aspx).

    ```powershell
    Move-Item -Path C:\DSCTest\PullClientBootstrap\localhost.meta.mof -Destination E:\Windows\Sytem32\Configuration\MetaConfig.mof
    ```

7. Smontare il disco rigido virtuale tramite la chiamata al cmdlet [Dismount-VHD](https://technet.microsoft.com/library/hh848562.aspx). Ad esempio:

    ```powershell
    Dismount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

8. Creare una macchina virtuale usando il disco rigido virtuale in cui è installato il documento MOF di DSC.
Dopo l'avvio iniziale e l'installazione del sistema operativo, DSC effettuerà il pull della configurazione dal server di pull e verrà installato IIS.
È possibile verificare questo aspetto chiamando il cmdlet [Get-WindowsFeature](https://technet.microsoft.com/library/jj205469.aspx).

## <a name="disable-dsc-at-boot-time"></a>Disabilitare DSC in fase di avvio

Per impostazione predefinita, il valore della chiave **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\DSCAutomationHostEnabled** è impostato su 2, che consente l'esecuzione di una configurazione DSC se il computer è in stato in sospeso o corrente. Se non si vuole far eseguire una configurazione all'avvio iniziale, è necessario impostare il valore di questa chiave su 0:

1. Montare il disco rigido virtuale tramite la chiamata al cmdlet [Mount-VHD](https://technet.microsoft.com/library/hh848551.aspx). Ad esempio:

    ```powershell
    Mount-VHD -Path C:\users\public\documents\vhd\Srv16.vhd
    ```

2. Caricare la sottochiave del Registro di sistema **HKLM\Software** dal disco rigido virtuale chiamando `reg load`.

    ```
    reg load HKLM\Vhd E:\Windows\System32\Config\Software`
    ```

3. Passare a **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\*** tramite il provider del Registro di sistema di PowerShell.

    ```powershell
    Set-Location HKLM:\Software\Microsoft\Windows\CurrentVersion\Policies`
    ```

4. Modificare il valore di `DSCAutomationHostEnabled` in 0.

    ```powershell
    Set-ItemProperty -Path . -Name DSCAutomationHostEnabled -Value 0
    ```

5. Scaricare il Registro di sistema eseguendo i comandi seguenti:

    ```powershell
    [gc]::Collect()
    reg unload HKLM\Vhd
    ```

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Chiave del Registro di sistema DSCAutomationHostEnabled](DSCAutomationHostEnabled.md)
- [Configurazione di Gestione configurazione locale](metaConfig.md)
- [Configurazione di un server di pull Web DSC](pullServer.md)

