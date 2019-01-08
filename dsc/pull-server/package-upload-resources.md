---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pacchetti di caricamento delle risorse a un Server di Pull
ms.openlocfilehash: 29a62f96393a53c9e7da57a5e51732dcb0937194
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401237"
---
# <a name="package-and-upload-resources-to-a-pull-server"></a>Pacchetti di caricamento delle risorse a un Server di Pull

Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull. Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.

## <a name="package-resource-modules"></a>Moduli delle risorse del pacchetto

Ogni risorsa disponibile per un client di scaricare deve essere archiviato in un file "ZIP". L'esempio seguente verrà illustra i passaggi necessari usando il [xPSDesiredStateConfiguration](https://www.powershellgallery.com/packages/xPSDesiredStateConfiguration/8.4.0.0) risorsa.

> [!NOTE]
> Se si dispone di tutti i client che usano PowerShell 4.0, si sarà necessario flaten la struttura di cartelle di risorse e rimuovere eventuali cartelle della versione. Per altre informazioni, vedere [più versioni di risorse](../configurations/import-dscresource.md#multiple-resource-versions).

È possibile comprimere la directory delle risorse usando qualsiasi utilità, script o metodo che si preferisce. In Windows, è possibile *destro* nella directory "xPSDesiredStateConfiguration" e selezionare "Invia a", quindi "Cartella compressa".

![Fare clic con il pulsante destro del mouse](../media/right-click.gif)

### <a name="naming-the-resource-archive"></a>L'archivio di risorse di denominazione

L'archivio di risorse deve essere denominato con il formato seguente:

```
{ModuleName}_{Version}.zip
```

Nell'esempio precedente, "xPSDesiredStateConfiguration.zip" deve essere rinominato "xPSDesiredStateConfiguration_8.4.4.0.zip".

### <a name="create-checksums"></a>Creare i valori di checksum

Dopo aver compresso ed rinominato il modulo di risorse, è necessario creare un **CheckSum**.  Il **CheckSum** viene usato, da Gestione configurazione locale nel client, per determinare se la risorsa è stata modificata e deve essere scaricato nuovamente. È possibile creare un **CheckSum** con il [New-DSCCheckSum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) cmdlet come mostrato nell'esempio seguente.

```powershell
New-DscChecksum -Path .\xPSDesiredStateConfiguration_8.4.4.0.zip
```

Non verrà visualizzato alcun output, ma si noterà ora un "xPSDesiredStateConfiguration_8.4.4.0.zip.checksum". È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il `-Path` parametro. Se esiste già un checksum, è possibile applicarlo a essere ricreate con la `-Force` parametro.

### <a name="where-to-store-resource-archives"></a>Posizione in cui archiviare gli archivi di risorse

#### <a name="on-a-dsc-http-pull-server"></a>In un Server di Pull HTTP DSC

Quando si configura il Server di Pull HTTP, come illustrato in [configurare un Server di Pull DSC HTTP](pullServer.md), si specificano directory per il **ModulePath** e **ConfigurationPath** chiavi. Il **ConfigurationPath** chiave indica dove devono essere archiviati i file "MOF". Il **ModulePath** indica dove devono essere archiviati tutti i moduli risorsa DSC.

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

Se è stata specificata una **ResourceRepositoryShare**, quando configurare il Client di Pull, archiviare gli archivi e checksum nel **SourcePath** nella directory di **ResourceRepositoryShare** blocco.

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

Se è stata specificata solo una **ConfigurationRepositoryShare**, quando configurare il Client di Pull, archiviare gli archivi e checksum nel **SourcePath** nella directory di  **ConfigurationRepositoryShare** blocco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

#### <a name="updating-resources"></a>Aggiornamento delle risorse

È possibile forzare un nodo per aggiornare le relative risorse modificando il numero di versione nel nome dell'archivio, o creando un nuovo checksum. Il Client di Pull deve ricercare le versioni più recenti delle risorse necessarie, nonché aggiornato i valori di checksum, quando viene aggiornata la gestione configurazione locale.

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)
