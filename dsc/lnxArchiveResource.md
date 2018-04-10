---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxArchive DSC per Linux
ms.openlocfilehash: 142f0317914f1bd3a0523d706b19662f3f64c8b6
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxarchive-resource"></a>Risorsa nxArchive DSC per Linux

La risorsa **nxArchive** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (TAR) in un percorso specifico in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxArchive <string> #ResourceName
{
    SourcePath = <string>
    DestinationPath = <string>
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Force = <bool> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà |  Description |
|---|---|
| SourcePath| Specifica il percorso di origine del file di archivio. Può essere un file con estensione tar, zip o tar.gz. |
| DestinationPath| Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.|
| Checksum| Definisce il tipo da usare per determinare se l'archivio di origine è stato aggiornato. I valori sono: "ctime", "mtime" e "md5". Il valore predefinito è "md5".|
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà **Force**, tali errori vengono ignorati. Il valore predefinito è **$false**.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| Ensure| Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**. Impostare questa proprietà su "Present" per specificare che il contenuto esiste. Impostarla su "Absent" per specificare che il contenuto non esiste. Il valore predefinito è "Present".|

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa **nxArchive** per specificare che il contenuto di un file di archivio denominato `website.tar` esiste e viene estratto in una determinata destinazione.

```
Import-DSCResource -Module nx

nxFile SyncArchiveFromWeb
{
   Ensure = "Present"
   SourcePath = “http://release.contoso.com/releases/website.tar”
   DestinationPath = "/usr/release/staging/website.tar"
   Type = "File"
   Checksum = “mtime”
}

nxArchive SyncWebDir
{
   SourcePath = “/usr/release/staging/website.tar”
   DestinationPath = “/usr/local/apache2/htdocs/”
   Force = $false
   DependsOn = "[nxFile]SyncArchiveFromWeb"
}
```