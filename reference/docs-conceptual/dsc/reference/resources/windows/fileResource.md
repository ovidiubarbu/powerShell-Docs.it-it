---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa File DSC
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954678"
---
# <a name="dsc-file-resource"></a>Risorsa File DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **File** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione. **DestinationPath** e **SourcePath** devono entrambi essere accessibili per il nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|DestinationPath |Il percorso, nel nodo di destinazione, per il quale ci si vuole assicurare che sia **Present** o **Absent** con **Ensure**. |
|Attributi |Lo stato desiderato degli attributi per il file o la directory di destinazione. I valori validi sono _Archive_, _Hidden_, _ReadOnly_ e _System_. |
|Checksum |Il tipo di checksum da usare per determinare se due file sono uguali. I valori validi includono: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**. |
|Contenuti |Valido solo se usato con **Type** **File**. Indica il contenuto per il quale ci si vuole assicurare (**Ensure**) che sia **Present** o **Absent** nel file di destinazione. |
|Credential |Le credenziali necessarie per accedere alle risorse, ad esempio i file di origine. |
|Force |Esegue l'override di operazioni di accesso che genererebbero un errore, ad esempio quando si sovrascrive un file o si elimina una directory non vuota. Il valore predefinito è `$false`. |
|Recurse |Valido solo se usato con **Type** **Directory**. Esegue in modo ricorsivo l'operazione di stato per tutte le sottodirectory. Il valore predefinito è `$false`. |
|SourcePath |Il percorso da cui copiare la risorsa file o cartella. |
|Type |Il tipo di risorsa configurata. I valori validi sono **Directory** e **File**. Il valore predefinito è **File**. |
|MatchSource |Determina se la risorsa deve monitorare i nuovi file aggiunti alla directory di origine dopo la copia iniziale. Un valore di `$true` indica che, dopo la copia iniziale, i nuovi file di origine devono essere copiati nella destinazione. Se impostato su `$false`, la risorsa memorizza nella cache il contenuto della directory di origine e ignora eventuali file aggiunti dopo la copia iniziale. Il valore predefinito è `$false`. |

> [!WARNING]
> Se non si specifica un valore per **Credential** o **PSRunAsCredential**, la risorsa userà l'account computer del nodo di destinazione per accedere a **SourcePath**. Quando **SourcePath** è una condivisione UNC, ciò potrebbe causare un errore di "Accesso negato". Assicurarsi che le autorizzazioni siano impostate di conseguenza o usino le proprietà **Credential** o **PSRunAsCredential** per specificare l'account da usare.

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se il file e **Contents** in **Destination** devono esistere o meno. Impostare questa proprietà su **Present** per assicurarsi che il file esista. Impostarla su **Absent** per specificare che il contenuto non esiste. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

### <a name="additional-information"></a>Altre informazioni

- Quando si specifica solo un **DestinationPath**, la risorsa garantisce che il percorso esista se **Present** o non esista se **Absent**.
- Quando si specifica un **SourcePath** e un **DestinationPath** con un valore **Type** **Directory**, la risorsa copia la directory di origine nel percorso di destinazione. Le proprietà **Recurse**, **Force** e **MatchSource** modificano il tipo di operazione di copia eseguita, mentre **Credential** determina quale account usare per accedere alla directory di origine.
- Se si specifica il valore **ReadOnly** per la proprietà **Attributes** insieme a un **DestinationPath**, **Ensure** **Present** crea il percorso specificato, mentre **Contents** imposta il contenuto del file. Con l'impostazione **Absent** per **Ensure** la proprietà **Attributes** verrebbe ignorata interamente e verrebbe rimosso qualsiasi file nel percorso specificato.

## <a name="example"></a>Esempio

L'esempio copia una directory e le relative sottodirectory da un server di pull a un nodo di destinazione usando la risorsa File. Se l'operazione ha esito positivo, la risorsa Log scrive un messaggio di conferma nel registro eventi.

La directory di origine è un percorso UNC (`\\PullServer\DemoSource`) condiviso dal server di pull. La proprietà **Recurse** garantisce che vengano copiate anche tutte le sottodirectory.

> [!IMPORTANT]
> La gestione configurazione locale (LCM) nel nodo di destinazione viene eseguita per impostazione predefinita nel contesto dell'account di sistema locale. Per concedere l'accesso a **SourcePath**, assegnare autorizzazioni appropriate all'account computer del nodo di destinazione. **Credential** e **PSDSCRunAsCredential** modificano entrambi il contesto usato da Gestione configurazione locale (LCM) per accedere a **SourcePath**. È comunque necessario concedere l'accesso all'account che verrà usato per l'accesso a **SourcePath**.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

Per altre informazioni sull'uso delle **Credenziali** in DSC, [Usare credenziali con risorse DSC](../../../configurations/runAsUser.md) o [Opzioni delle credenziali nei dati di configurazione](../../../configurations/configDataCredentials.md).