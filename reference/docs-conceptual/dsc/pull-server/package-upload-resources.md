---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Creare un pacchetto e caricare le risorse in un server di pull
ms.openlocfilehash: 8aac343d7495ecda94ed76d1d97079397eecd65f
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278503"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Creare un pacchetto e caricare le risorse in un server di pull

Le sezioni seguenti presuppongono che sia già stato configurato un server di pull. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).

## <a name="package-resource-modules"></a>Creare il pacchetto dei moduli delle risorse

Ogni risorsa disponibile per il download da un client deve essere archiviata in un file "ZIP". L'esempio seguente illustra i passaggi necessari usando la risorsa [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0).

> [!NOTE]
> Per eventuali client che usano PowerShell 4.0, sarà necessario appiattire la struttura di cartelle delle risorse e rimuovere eventuali cartelle della versione. Per altre informazioni, vedere [Più versioni di risorse](../configurations/import-dscresource.md#multiple-resource-versions).

È possibile comprimere la directory delle risorse usando qualsiasi utilità, script o metodo che si preferisce. In Windows, è possibile *fare clic con il pulsante destro del mouse* sulla directory "xPSDesiredStateConfiguration" e scegliere "Invia a", quindi "Cartella compressa".

![Fare clic con il pulsante destro del mouse](media/package-upload-resources/right-click.gif)

### <a name="naming-the-resource-archive"></a>Assegnazione di un nome all'archivio delle risorse

L'archivio delle risorse deve essere denominato con il formato seguente:

```
{ModuleName}_{Version}.zip
```

Nell'esempio precedente, "xPSDesiredStateConfiguration.zip" dovrebbe essere rinominato "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Creare i valori di checksum

Dopo aver compresso e rinominato il modulo delle risorse, è necessario creare un **CheckSum**.  Il **CheckSum** viene usato da Gestione configurazione locale nel client per determinare se la risorsa è stata modificata e deve essere scaricata nuovamente. È possibile creare un **CheckSum** con il cmdlet [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum), come mostrato nell'esempio seguente.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Non verrà visualizzato alcun output, ma dovrebbe essere ora disponibile "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il parametro `-Path`. Se esiste già un checksum, è possibile forzare la nuova creazione con il parametro `-Force`.

### <a name="where-to-store-resource-archives"></a>Posizione in cui archiviare gli archivi di risorse

#### <a name="on-a-dsc-http-pull-server"></a>In un server di pull HTTP DSC

Quando si configura il server di pull HTTP, come illustrato in [Configurare un server di pull HTTP DSC](pullServer.md), si specificano le directory per le chiavi **ModulePath** e **ConfigurationPath**. La chiave **ConfigurationPath** indica dove devono essere archiviati eventuali file "MOF". La chiave **ModulePath** indica dove devono essere archiviati eventuali moduli di risorse DSC.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

#### <a name="on-an-smb-share"></a>In una condivisione SMB

Se è stata specificata una **ResourceRepositoryShare** durante la configurazione del client di pull, archiviare gli archivi e i checksum nella directory **SourcePath** dal blocco **ResourceRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Configurations'
}

ResourceRepositoryShare SMBResourceServer
{
    SourcePath = '\\SMBPullServer\Resources'
}
```

Se è stata specificata solo una **ConfigurationRepositoryShare** durante la configurazione del client di pull, archiviare gli archivi e i checksum nella directory **SourcePath** dal blocco **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Aggiornamento delle risorse

È possibile forzare un nodo ad aggiornare le relative risorse modificando il numero di versione nel nome dell'archivio o creando un nuovo checksum. Il client di pull controllerà se sono disponibili versioni più recenti delle risorse necessarie, nonché checksum aggiornati, quando viene aggiornata l'istanza corrispondente di Gestione configurazione locale.

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)
