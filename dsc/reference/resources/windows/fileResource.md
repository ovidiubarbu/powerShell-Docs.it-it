---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa File DSC
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077331"
---
# <a name="dsc-file-resource"></a>Risorsa File DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa File in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione. **DestinationPath** e **SourcePath** devono entrambi essere accessibili per il nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà       |Description                                                                   |Obbligatoria|Default|
|---------------|------------------------------------------------------------------------------|--------|-------|
|DestinationPath|La posizione nel nodo di destinazione che si desidera sia `Present` o `Absent`.|Sì|No|
|Attributes     |Lo stato desiderato degli attributi per il file o la directory di destinazione. I valori validi sono **Archive**, **Hidden**, **ReadOnly** e **System**.|No|Nessuno|
|Checksum      |Il tipo di checksum da usare per determinare se due file sono uguali. I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|No|Viene confrontato solo il nome del file o della directory.|
|Contents       |Valido solo se usato con il tipo `File`. Indica il contenuto per assicurare che sia `Present` o `Absent` dal file di destinazione. |No|Nessuno|
|Credential     |Le credenziali necessarie per accedere alle risorse, ad esempio i file di origine.|No|Account del computer del nodo di destinazione. (*vedere la nota*)|
|Ensure         |Lo stato desiderato del file o della directory di destinazione. |No|**Presente**|
|Force          |Esegue l'override di operazioni di accesso che genererebbero un errore, ad esempio quando si sovrascrive un file o si elimina una directory non vuota.|No|`$false`|
|Recurse        |Valido solo se usato con il tipo `Directory`. Esegue in modo ricorsivo l'operazione di stato per tutte le sottodirectory.|No|`$false`|
|DependsOn      |Imposta una dipendenza sulle risorse specificate. Questa risorsa verrà eseguita solo dopo la corretta esecuzione di tutte le risorse dipendenti. È possibile specificare le risorse dipendenti usando la sintassi `"[ResourceType]ResourceName"`. Vedere [Dipendenze delle risorse con DependsOn](../../../configurations/resource-depends-on.md)|No|Nessuno|
|SourcePath     |Il percorso da cui copiare la risorsa file o cartella.|No|Nessuno|
|Tipo           |Il tipo di risorsa configurata. I valori validi sono `Directory` e `File`.|No|`File`|
|MatchSource    |Determina se la risorsa deve monitorare i nuovi file aggiunti alla directory di origine dopo la copia iniziale. Un valore di `$true` indica che, dopo la copia iniziale, i nuovi file di origine devono essere copiati nella destinazione. Se impostato su `$False`, la risorsa memorizza nella cache il contenuto della directory di origine e ignora eventuali file aggiunti dopo la copia iniziale.|No|`$false`|

> [!WARNING]
> Se non si specifica un valore per `Credential` o per `PSRunAsCredential` (PS v. 5), la risorsa userà l'account computer del nodo di destinazione per accedere a `SourcePath`.  Quando `SourcePath` è una condivisione UNC, ciò potrebbe causare un errore di "Accesso negato". Assicurarsi che le autorizzazioni siano impostate di conseguenza o usino le proprietà `Credential` o `PSRunAsCredential` per specificare l'account da usare.

## <a name="present-vs-absent"></a>Presente rispetto ad Assente

Ogni risorsa DSC consente di eseguire diverse operazioni in base al valore specificato per la proprietà `Ensure`. I valori specificati per le proprietà precedenti determinano l'operazione di stato eseguita.

### <a name="existence"></a>Esistenza

Quando si specifica solo `DestinationPath`, la risorsa garantisce che il percorso esiste (`Present`) o non esiste (`Absent`).

### <a name="copy-operations"></a>Operazioni di copia

Quando si specifica `SourcePath` e `DestinationPath` con un valore `Type` di **Directory**, la risorsa copia la directory di origine nel percorso di destinazione. Le proprietà `Recurse`, `Force` e `MatchSource` modificano il tipo di operazione di copia eseguita, mentre `Credential` determina quale account usare per accedere alla directory di origine.

### <a name="limitations"></a>Limitazioni

Se si specifica un valore `ReadOnly` per la proprietà `Attributes` insieme a `DestinationPath`, `Ensure = "Present"` creerà il percorso specificato, mentre `Contents` imposta il contenuto del file.  Un'operazione di stato `Absent` avrebbe ignorato completamente la proprietà `Attributes` e rimosso qualsiasi file nel percorso specificato.

## <a name="example"></a>Esempio

L'esempio copia una directory e le relative sottodirectory da un server di pull a un nodo di destinazione usando la risorsa File. Se l'operazione ha esito positivo, la risorsa Log scrive un messaggio di conferma nel registro eventi.

La directory di origine è un percorso UNC (`\\PullServer\DemoSource`) condiviso dal server di pull. La proprietà `Recurse` garantisce che vengano copiate anche tutte le sottodirectory.

> [!IMPORTANT]
> La gestione configurazione locale (LCM) nel nodo di destinazione viene eseguita per impostazione predefinita nel contesto dell'account di sistema locale. Per concedere l'accesso a **SourcePath**, assegnare autorizzazioni appropriate all'account computer del nodo di destinazione. **Credential** e **PSDSCRunAsCredential** (v5) modificano entrambi il contesto usato dalla gestione configurazione locale (LCM) per accedere a **SourcePath**. È comunque necessario concedere l'accesso all'account che verrà usato per l'accesso a **SourcePath**.

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
