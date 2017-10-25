---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa File DSC
ms.openlocfilehash: f16bfbc31489ef7d1b0e5e4ec3a4f30069c24c79
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-file-resource"></a>Risorsa File DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa File in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione.

>**Nota:** se la proprietà **MatchSource** è impostata su **$false**, che è il valore predefinito, i contenuti che devono essere copiati vengono memorizzati nella cache la prima volta in cui viene applicata la configurazione. 
>Alle applicazioni successive della configurazione non verrà eseguito il controllo dei file o delle cartelle aggiornati nel percorso specificato in **SourcePath**. Se si vuole cercare gli aggiornamenti per il file o le cartelle in **SourcePath** ogni volta che viene applicata la configurazione, impostare **MatchSource** su **$true**. 

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

|  Proprietà  |  Descrizione   | 
|---|---| 
| DestinationPath| Indica il percorso in cui si vuole specificare lo stato di un file o una directory.| 
| Attributes| Specifica lo stato desiderato degli attributi per il file o la directory di destinazione.| 
| Checksum| Indica il tipo di checksum da usare per determinare se due file sono uguali. Se la proprietà __Checksum__ non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.| 
| Contents| Specifica il contenuto di un file, ad esempio una determinata stringa.| 
| Credential| Indica le credenziali necessarie per accedere alle risorse, ad esempio i file di origine, se tale accesso è necessario.| 
| Ensure| Indica se il file o la directory esiste. Impostare questa proprietà su "Absent" per specificare che il file o la directory non esiste. Impostarla su "Present" per specificare che il file o la directory esiste. Il valore predefinito è "Present".| 
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà Force, tali errori vengono ignorati. Il valore predefinito è __$false__.| 
| Recurse| Indica se le sottodirectory sono incluse. Impostare questa proprietà su __$true__ per indicare che le sottodirectory devono essere incluse. Il valore predefinito è __$false__. **Nota**: questa proprietà è valida solo quando la proprietà Type è impostata su Directory.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| SourcePath| Indica il percorso da cui copiare la risorsa file o cartella.| 
| Tipo| Indica se la risorsa configurata è una directory o un file. Impostare questa proprietà su "Directory" per indicare che la risorsa è una directory. Impostarla su "File" per indicare che la risorsa è un file. Il valore predefinito è "File".| 
| MatchSource| Se questa proprietà è impostata sul valore predefinito __$false__, tutti i file nell'origine (ad esempio i file A, B e C) verranno aggiunti nella destinazione la prima volta che viene applicata la configurazione. Se viene aggiunto un nuovo file (D) nell'origine, non verrà aggiunto nella destinazione, anche quando la configurazione viene applicata di nuovo in un secondo momento. Se il valore è __$true__, ogni volta che la configurazione viene applicata, i nuovi file trovati successivamente nell'origine (ad esempio il file D in questo esempio) vengono aggiunti nella destinazione. Il valore predefinito è **$false**.| 

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa File per specificare che una cartella con il percorso `C:\Users\Public\Documents\DSCDemo\DemoSource` in un computer di origine (ad esempio, il server di pull) deve essere presente anche (insieme a tutte le sottodirectory) nel nodo di destinazione. Viene anche scritto nel registro un messaggio di conferma al termine dell'operazione e viene inclusa un'istruzione per specificare che l'operazione di controllo dei file venga eseguita prima dell'operazione di registrazione.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```

