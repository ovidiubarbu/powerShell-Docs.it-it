---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Archive DSC
ms.openlocfilehash: ddabe1a623783fe213b8059f47851184d5253fc5
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954768"
---
# <a name="dsc-archive-resource"></a>Risorsa Archive DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa Archive in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per decomprimere file di archivio (ZIP) in un percorso specifico.

## <a name="syntax"></a>Sintassi

```Syntax
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
    [ Ensure = [string] { Absent | Present } ]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Destination |Indica il percorso in cui si vuole specificare di estrarre il contenuto dell'archivio. |
|Path |Specifica il percorso di origine del file di archivio. |
|Checksum |Definisce il tipo da usare per determinare se due file sono uguali. Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori validi includono: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. Se si specifica **Checksum** senza **Validate**, la configurazione non riesce. |
|Force |Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà **Force**, tali errori vengono ignorati. Il valore predefinito è **False**. |
|Validate| Usa la proprietà **Checksum** per determinare se l'archivio corrisponde alla firma. Se si specifica **Checksum** senza **Validate**, la configurazione non riesce. Se si specifica **Validate** senza **Checksum**, per impostazione predefinita viene usato un _checksum_ **SHA-256**. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se verificare l'esistenza del contenuto dell'archivio in **Destination**. Impostare questa proprietà su **Present** per specificare che il contenuto esiste. Impostarla su **Absent** per specificare che il contenuto non esiste. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa Archive per assicurarsi che il contenuto di un file di archivio denominato `Test.zip` esista e venga estratto in una destinazione specificata.

```powershell
Archive ArchiveExample {
    Ensure = "Present"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```