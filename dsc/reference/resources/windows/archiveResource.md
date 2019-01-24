---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Archive DSC
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047647"
---
# <a name="dsc-archive-resource"></a>Risorsa Archive DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa Archive in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.

## <a name="syntax"></a>Sintassi
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Destination| Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.|
| Path| Specifica il percorso di origine del file di archivio.|
| __Checksum__| Definisce il tipo da usare per determinare se due file sono uguali. Se la proprietà __Checksum__ non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate e none (predefinito). Se si specifica __Checksum__ senza __Validate__, la configurazione non riesce.|
| Ensure| Determina se verificare l'esistenza del contenuto dell'archivio in __Destination__. Impostare questa proprietà su __Present__ per specificare che il contenuto esiste. Impostarla su __Absent__ per specificare che il contenuto non esiste. Il valore predefinito è __Present__.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| Validate| Usa la proprietà Checksum per determinare se l'archivio corrisponde alla firma. Se si specifica Checksum senza Validate, la configurazione non riesce. Se si specifica Validate senza Checksum, per impostazione predefinita viene usato un checksum SHA-256.|
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà Force, tali errori vengono ignorati. Il valore predefinito è False.|

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa Archive per specificare che il contenuto di un file di archivio denominato Test.zip esiste e viene estratto in una determinata destinazione.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```