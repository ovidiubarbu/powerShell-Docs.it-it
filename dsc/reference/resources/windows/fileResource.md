---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa File DSC
ms.openlocfilehash: b5bc2c305b8cfccbd044274811df631264a24279
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682699"
---
# <a name="dsc-file-resource"></a>Risorsa File DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa File in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione. Il **DestinationPath** e **SourcePath** devono essere entrambi accessibili dal nodo di destinazione.

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
|DestinationPath|La posizione, nel nodo di destinazione, si desidera assicurarsi che sia `Present` o `Absent`.|Sì|No|
|Attributes     |Lo stato desiderato degli attributi per il file di destinazione o la directory. I valori validi sono **Archive**, **Hidden**, **ReadOnly**, e **sistema**.|No|Nessuno|
|Checksum      |Il tipo di checksum da usare per determinare se due file sono uguali. I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|No|Viene confrontato solo il nome file o directory.|
|Contents       |Valido solo se usato con `File` tipo. Indica il contenuto per assicurarsi che sia `Present` o `Absent` dal file di destinazione. |No|Nessuno|
|Credential     |Le credenziali necessarie per accedere alle risorse, ad esempio i file di origine.|No|Account Computer del nodo di destinazione. (*vedere la nota*)|
|Ensure         |Lo stato desiderato del file di destinazione o della directory. |No|**Presente**|
|Force          |Esegue l'override di operazioni di accesso che comporterebbero un errore (ad esempio sovrascrivere un file o l'eliminazione di una directory non vuota).|No|`$false`|
|Recurse        |Valido solo se usato con `Directory` tipo. Esegue in modo ricorsivo operazione di stato per tutte le sottodirectory.|No|`$false`|
|DependsOn      |Imposta una dipendenza su risorse specificate. Questa risorsa verrà eseguita solo dopo la corretta esecuzione di tutte le risorse dipendenti. È possibile specificare le risorse dipendenti utilizzando la sintassi `"[ResourceType]ResourceName"`. Vedere [about_DependsOn](../../../configurations/resource-depends-on.md)|No|Nessuno|
|SourcePath     |Il percorso da cui copiare la risorsa file o cartella.|No|Nessuno|
|Tipo           |Tipo di risorsa configurata. I valori validi sono `Directory` e `File`.|No|`File`|
|MatchSource    |Determina se la risorsa deve monitorare i nuovi file aggiunti alla directory di origine dopo la copia iniziale. Un valore di `$true` indica che, dopo la copia iniziale, i nuovi file di origine devono essere copiati nella destinazione. Se impostato su `$False`, la risorsa memorizzata nella cache il contenuto della directory di origine e ignora eventuali file aggiunti dopo la copia iniziale.|No|`$false`|

> [!WARNING]
> Se non si specifica un valore per `Credential` oppure `PSRunAsCredential` (PS v. 5), la risorsa verrà utilizzato l'account computer del nodo di destinazione per accedere la `SourcePath`.  Quando il `SourcePath` è una condivisione UNC, ciò potrebbe causare un errore "Accesso negato". Assicurarsi che le autorizzazioni vengono impostate di conseguenza o usano il `Credential` o `PSRunAsCredential` proprietà per specificare l'account da usare.

## <a name="present-vs-absent"></a>Visual Studio presente. Assente

Ogni risorsa DSC consente di eseguire diverse operazioni in base al valore specificato per il `Ensure` proprietà. I valori specificati per la proprietà sopra menzionate determina l'operazione dello stato eseguita.

### <a name="existence"></a>Esistenza

Quando si specifica solo un `DestinationPath`, la risorsa garantisce che il percorso esista (`Present`) o non esiste (`Absent`).

### <a name="copy-operations"></a>Operazioni di copia

Quando si specifica un `SourcePath` e una `DestinationPath` con un `Type` pari a **Directory**, la directory di origine di copie di risorse nel percorso di destinazione. La proprietà `Recurse`, `Force`, e `MatchSource` modificare il tipo di operazione di copia eseguite, mentre `Credential` determina quale account usare per accedere alla directory di origine.

### <a name="limitations"></a>Limitazioni

Se si specifica un valore `ReadOnly` per il `Attributes` proprietà insieme a un `DestinationPath`, `Ensure = "Present"` creerà il percorso specificato, mentre `Contents` imposterebbe il contenuto del file.  Un' `Absent` avrebbe ignorato l'operazione dello stato di `Attributes` proprietà interamente e rimuovere qualsiasi file nel percorso specificato.

## <a name="example"></a>Esempio

Nell'esempio seguente copia una directory e nelle relative sottodirectory da un server di pull a un nodo di destinazione usando la risorsa del File. Se l'operazione ha esito positivo, la risorsa Log scrive un messaggio di conferma nel registro eventi.

La directory di origine è un percorso UNC (`\\PullServer\DemoSource`) condiviso dal Server di Pull. Il `Recurse` proprietà garantisce che tutte le sottodirectory vengono copiate anche.

> [!IMPORTANT]
> Gestione configurazione locale nel nodo di destinazione viene eseguita nel contesto dell'account di sistema locale per impostazione predefinita. Per concedere l'accesso per il **SourcePath**, assegnare le autorizzazioni appropriate di account computer del nodo di destinazione. Il **credenziale** e **PSDSCRunAsCredential** (v5) sia change viene utilizzato il contesto di Gestione configurazione locale per accedere la **SourcePath**. È comunque necessario concedere l'accesso all'account che verrà usato per l'accesso di **SourcePath**.

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

Per l'uso in ulteriori **credenziali** vedere DSC [Run As User](../../../configurations/runAsUser.md) o [le credenziali di dati di configurazione](../../../configurations/configDataCredentials.md).
