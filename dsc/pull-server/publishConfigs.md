---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)
ms.openlocfilehash: c258814f480b91eba75c7ce9abf70c558f1f469e
ms.sourcegitcommit: 5a004064f33acc0145ccd414535763e95f998c89
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/23/2019
ms.locfileid: "69986579"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Pubblicare in un server di pull usando gli ID di configurazione (v4/v5)

Le sezioni seguenti presuppongono che sia già stato configurato un server di pull. Per configurare un server di pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato in modo che possa scaricare configurazioni e risorse e persino segnalare il proprio stato. Questo articolo illustra come caricare risorse in modo che siano disponibili per essere scaricate e come configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** o **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale (LCM).

## <a name="compile-configurations"></a>Compilare le configurazioni

Il primo passaggio per l'archiviazione delle [configurazioni](../configurations/configurations.md) in un server di pull è di compilarle in file `.mof`. Per rendere una configurazione generica e applicabili a più client, usare `localhost` nel blocco di nodo. L'esempio seguente mostra una shell di configurazione che usa `localhost` anziché un nome specifico di client.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Dopo aver compilato la configurazione generica, si dovrebbe avere un file `localhost.mof`.

## <a name="renaming-the-mof-file"></a>Rinominare il file MOF

È possibile archiviare i file di configurazione `.mof` in un server di pull in base a **ConfigurationName** o **ConfigurationID**. A seconda del modo in cui si prevede di configurare i client di pull, è possibile scegliere una delle sezioni seguenti per rinominare in modo corretto i file `.mof` compilati.

### <a name="configuration-ids-guid"></a>ID di configurazione (GUID)

Sarà necessario rinominare il file `localhost.mof` in un file `<GUID>.mof`. È possibile creare un **GUID** casuale usando l'esempio che segue o tramite il cmdlet [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid).

```powershell
[System.Guid]::NewGuid()
```

Output di esempio

```Output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Sarà quindi possibile rinominare il file `.mof` usando qualsiasi metodo accettabile. Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Per altre informazioni sull'uso di **GUID** nell'ambiente in uso, vedere [Pianificare per i GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nomi di configurazione

Sarà necessario rinominare il file `localhost.mof` in un file `<Configuration Name>.mof`. Nell'esempio seguente viene usato il nome della configurazione della sezione precedente. Sarà quindi possibile rinominare il file `.mof` usando qualsiasi metodo accettabile. Nell'esempio riportato di seguito, viene usato il cmdlet [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item).

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Creare il file CheckSum

Ogni file `.mof` archiviato in un server di pull o una condivisione SMB deve avere un file `.checksum` associato.
Questo file consente ai client di sapere quando il file `.mof` associato è stato modificato e deve essere scaricato nuovamente.

È possibile creare un **CheckSum** con il cmdlet [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum). È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il parametro `-Path`.
Se esiste già un checksum, è possibile forzare la nuova creazione con il parametro `-Force`. L'esempio seguente specifica una directory contenente il file `.mof` della sezione precedente e usa il parametro `-Force`.

```powershell
New-DscChecksum -Path '.\' -Force
```

Non verrà visualizzato alcun output, ma a questo punto dovrebbe essere visualizzato un file `<GUID or Configuration Name>.mof.checksum`.

## <a name="where-to-store-mof-files-and-checksums"></a>Posizione in cui archiviare i file MOF e CheckSum

### <a name="on-a-dsc-http-pull-server"></a>In un server di pull HTTP DSC

Quando si configura il server di pull HTTP, come illustrato in [Configurare un server di pull HTTP DSC](pullServer.md), si specificano le directory per le chiavi **ModulePath** e **ConfigurationPath**. La chiave **ModulePath** indica dove devono essere archiviati i file `.zip` di un modulo. **ConfigurationPath** indica dove devono essere archiviati eventuali file `.mof` e `.checksum`.

```powershell
    xDscWebService PSDSCPullServer
    {
    ...
        ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
        ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
    ...
    }

```

### <a name="on-an-smb-share"></a>In una condivisione SMB

Quando si configura un client di pull per usare una condivisione SMB, si specifica **ConfigurationRepositoryShare**.
Tutti i file `.mof` e `.checksum` devono quindi essere archiviati nella directory **SourcePath** del blocco **ConfigurationRepositoryShare**.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Passaggi successivi

Successivamente verranno configurati i client pull per eseguire il pull della configurazione specificata. Per altre informazioni, vedere le seguenti guide:

- [Configurare un client di pull usando gli ID di configurazione (v4)](pullClientConfigId4.md)
- [Configurare un client di pull usando gli ID di configurazione (v5)](pullClientConfigId.md)
- [Configurare un client di pull usando i nomi di configurazione (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)
- [Creare un pacchetto e caricare le risorse in un server di pull](package-upload-resources.md)
