---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa Archive DSC
ms.openlocfilehash: 035f7cc1b7f21f7a0df2d72db0ba83bc0688356c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-archive-resource" class="xliff"></a>
# Risorsa Archive DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa Archive in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.

<a id="syntax" class="xliff"></a>
## Sintassi 
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

<a id="properties" class="xliff"></a>
## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| Destination| Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio.| 
| Path| Specifica il percorso di origine del file di archivio.| 
| __Checksum__| Definisce il tipo da usare per determinare se due file sono uguali. Se la proprietà __Checksum__ non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate e none (predefinito). Se si specifica __Checksum__ senza __Validate__, la configurazione non riesce.| 
| Ensure| Determina se verificare l'esistenza del contenuto dell'archivio in __Destination__. Impostare questa proprietà su __Present__ per specificare che il contenuto esiste. Impostarla su __Absent__ per specificare che il contenuto non esiste. Il valore predefinito è __Present__.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| Validate| Usa la proprietà Checksum per determinare se l'archivio corrisponde alla firma. Se si specifica Checksum senza Validate, la configurazione non riesce. Se si specifica Validate senza Checksum, per impostazione predefinita viene usato un checksum SHA-256.| 
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà Force, tali errori vengono ignorati. Il valore predefinito è False.| 

<a id="example" class="xliff"></a>
## Esempio

L'esempio seguente mostra come usare la risorsa Archive per specificare che il contenuto di un file di archivio denominato Test.zip esiste e viene estratto in una determinata destinazione.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
} 
```

