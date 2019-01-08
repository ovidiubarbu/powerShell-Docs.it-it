---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Pubblicare in un Server di Pull usando gli ID di configurazione (v4/v5)
ms.openlocfilehash: 0144fec43d7a8d65b79891567cc0dc3952175343
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401314"
---
# <a name="publish-to-a-pull-server-using-configuration-ids-v4v5"></a>Pubblicare in un Server di Pull usando gli ID di configurazione (v4/v5)

Le sezioni seguenti presuppongono che già stato impostato in un Server di Pull. Se non è stato configurato il Server di Pull, è possibile usare le guide seguenti:

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)

Ogni nodo di destinazione può essere configurato per scaricare le configurazioni, risorse e anche segnalare lo stato. Questo articolo illustrerà come caricare risorse in modo che siano disponibili per essere scaricato e configurare i client per scaricare automaticamente le risorse. Quando il nodo riceve una configurazione assegnata, attraverso **Pull** oppure **Push** (v5), scarica automaticamente le risorse richieste dalla configurazione dal percorso specificato in Gestione configurazione locale.

## <a name="compile-configurations"></a>Compilare configurazioni

Il primo passaggio per la memorizzazione [configurazioni](../configurations/configurations.md) in un Server di Pull è per compilarle in file con "estensione MOF". Per rendere una configurazione generica e applicabili a più client, usare `localhost` in blocco di nodo. L'esempio seguente mostra una shell di configurazione che usa `localhost` anziché un nome specifico client.

```powershell
Configuration GenericConfig
{
    Node localhost
    {

    }
}
GenericConfig
```

Dopo aver compilato la configurazione generica, è necessario avere un file "localhost.mof".

## <a name="renaming-the-mof-file"></a>Ridenominazione del file MOF

È possibile archiviare i file di configurazione "MOF" in un Server di Pull da **ConfigurationName** oppure **ConfigurationID**. A seconda del modo in cui si prevede di configurare i client di pull, è possibile scegliere delle sezioni seguenti in modo corretto rinominare i file compilati "MOF".

### <a name="configuration-ids-guid"></a>ID di configurazione (GUID)

Sarà necessario rinominare il file "localhost.mof" a "<GUID>MOF" file. È possibile creare uno casuale **Guid** usando l'esempio sotto, o tramite il [New-Guid](/powershell/module/microsoft.powershell.utility/new-guid) cmdlet.

```powershell
[System.Guid]::NewGuid()
```

Output di esempio

```output
Guid
----
64856475-939e-41fb-aba5-4469f4006059
```

Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile. Nell'esempio riportato di seguito, viene usato il [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName '64856475-939e-41fb-aba5-4469f4006059.mof'
```

Per altre informazioni sull'uso **GUID** nell'ambiente in uso, vedere [pianificare GUID](/powershell/dsc/secureserver#guids).

### <a name="configuration-names"></a>Nomi di configurazione

Sarà necessario rinominare il file "localhost.mof" a "<Configuration Name>MOF" file. Nell'esempio seguente viene utilizzato il nome della configurazione nella sezione precedente. Sarà quindi possibile rinominare il file "MOF" usando qualsiasi metodo accettabile. Nell'esempio riportato di seguito, viene usato il [Rename-Item](/powershell/module/microsoft.powershell.management/rename-item) cmdlet.

```powershell
Rename-Item -Path .\localhost.mof -NewName 'GenericConfig.mof'
```

## <a name="create-the-checksum"></a>Creare il valore di CheckSum

Ogni file "MOF" archiviato in un Server di Pull, o una condivisione SMB deve avere un file associato ".checksum". Questo file consente ai client di sapere quando il file associato "MOF" è stato modificato e deve essere scaricato nuovamente.

È possibile creare un **CheckSum** con il [New-DSCCheckSum](/powershell/module/psdesiredstateconfiguration/new-dscchecksum) cmdlet. È anche possibile eseguire `New-DSCCheckSum` in una directory di file usando il `-Path` parametro. Se esiste già un checksum, è possibile applicarlo a essere ricreate con la `-Force` parametro. Nell'esempio seguente specifica una directory contenente il file "MOF" nella sezione precedente e viene utilizzato il `-Force` parametro.

```powershell
New-DscChecksum -Path '.\' -Force
```

Non verrà visualizzato alcun output, ma si noterà ora un "<GUID or Configuration Name>. mof.checksum" file.

## <a name="where-to-store-mof-files-and-checksums"></a>Posizione in cui archiviare i file MOF e i valori di checksum

### <a name="on-a-dsc-http-pull-server"></a>In un Server di Pull HTTP DSC

Quando si configura il Server di Pull HTTP, come illustrato in [configurare un Server di Pull DSC HTTP](pullServer.md), si specificano directory per il **ModulePath** e **ConfigurationPath** chiavi. Il **ConfigurationPath** chiave indica dove devono essere archiviati i file "MOF". Il **ConfigurationPath** indica dove devono essere archiviati tutti i file "MOF" e ".checksum" file.

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

Quando si configura un Client di Pull per usare una condivisione SMB, si specifica un **ConfigurationRepositoryShare**. Tutti i file "MOF" e ".checksum" quindi devono essere archiviati nel **SourcePath** nella directory le **ConfigurationRepositoryShare** blocco.

```powershell
ConfigurationRepositoryShare SMBPullServer
{
    SourcePath = '\\SMBPullServer\Pull'
}
```

## <a name="next-steps"></a>Passaggi successivi

Successivamente, è consigliabile configurare i client di Pull per eseguire il pull di configurazione specificato. Per altre informazioni, vedere una delle guide seguenti:

- [Configurare un Client di Pull usando un ID di configurazione (v4)](pullClientConfigId4.md)
- [Configurare un Client di Pull usando un ID di configurazione (v5)](pullClientConfigId.md)
- [Configurare un Client di Pull usando nomi di configurazione (v5)](pullClientConfigNames.md)

## <a name="see-also"></a>Vedere anche

- [Configurare un server di pull SMB DSC](pullServerSmb.md)
- [Configurare un server di pull HTTP DSC](pullServer.md)
- [Pacchetti di caricamento delle risorse a un Server di Pull](package-upload-resources.md)
