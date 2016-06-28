---
title: Risorsa nxFile DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 2ba44df5dd6c91371cbbfe95d48184a4ff4a7738

---

# Risorsa nxFile DSC per Linux

La risorsa **nxFile** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e directory in un nodo Linux.

## Sintassi

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| DestinationPath| Indica il percorso in cui si vuole specificare lo stato di un file o una directory.| 
| SourcePath| Specifica il percorso da cui copiare la risorsa file o cartella. Questo percorso può essere un percorso locale o un URL `http/https/ftp`. Gli URL `http/https/ftp` remoti sono supportati solo quando il valore della proprietà **Type** è file.| 
| Ensure| Determina se verificare l'esistenza del file. Impostare questa proprietà su "Present" per specificare che il file esiste. Impostarla su "Absent" per specificare che il file non esiste. Il valore predefinito è "Present".| 
| Type| Specifica se la risorsa configurata è una directory o un file. Impostare questa proprietà su "directory" per indicare che la risorsa è una directory. Impostarla su "file" per indicare che la risorsa è un file. Il valore predefinito è "file".| 
| Contents| Specifica il contenuto di un file, ad esempio una determinata stringa.| 
| Checksum| Definisce il tipo da usare per determinare se due file sono uguali. Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori sono: "ctime", "mtime" e "md5".| 
| Recurse| Indica se le sottodirectory sono incluse. Impostare questa proprietà su **$true** per indicare che le sottodirectory devono essere incluse. Il valore predefinito è **$false**. **Nota:** questa proprietà è valida solo quando la proprietà **Type** è impostata su directory.| 
| Force| Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà **Force**, tali errori vengono ignorati. Il valore predefinito è **$false**.| 
| Links| Specifica il comportamento desiderato per i collegamenti simbolici. Impostare questa proprietà su "follow" per seguire i collegamenti simbolici e agire sulla destinazione dei collegamenti (ad esempio, copiare il file invece del collegamento). Impostare questa proprietà su "manage" per agire sul collegamento (ad esempio, copiare il collegamento stesso). Impostare questa proprietà su "ignore" per ignorare i collegamenti simbolici.| 
| Group| Nome del **gruppo** proprietario del file o della directory.| 
| Mode| Specifica le autorizzazioni desiderate per la risorsa, in notazione ottale o simbolica (ad esempio, 777 o rwxrwxrwx). Se si usa la notazione simbolica, non fornire il primo carattere che indica una directory o un file.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## Informazioni aggiuntive


Linux e Windows usano per impostazione predefinita caratteri di interruzione di riga diversi nei file di testo e questo può causare risultati imprevisti quando si configurano alcuni file in un computer Linux con __nxFile__. Ci sono diversi modi per gestire il contenuto di un file di Linux evitando i problemi causati da caratteri di interruzione di riga imprevisti:

Passaggio 1: copiare il file da un'origine remota (http, https o ftp). Creare un file in Linux con il contenuto desiderato e metterlo su un server Web o FTP accessibile dai nodi che verranno configurati. Definire la proprietà __SourcePath__ nella risorsa __nxFile__ con l'URL Web o FTP del file.

```
Import-DSCResource -Module nx
Node $Node
{
nxFile resolvConf
{
    SourcePath = "http://10.185.85.11/conf/resolv.conf"
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    
}
        
}
```


Passaggio 2: leggere il contenuto del file nello script di PowerShell con [Get-Content](https://technet.microsoft.com/en-us/library/hh849787.aspx) dopo avere impostato la proprietà __$OFS__ per usare il carattere di interruzione di riga di Linux.


```
Import-DSCResource -Module nx
Node $Node
{
$OFS = "`n"
$Contents = Get-Content C:\temp\resolv.conf

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = "$Contents"
}

}
```


Passaggio 3: usare una funzione di PowerShell per sostituire le interruzioni di riga di Windows con caratteri di interruzione di riga di Linux.

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
    Return $outputStr
}

Import-DSCResource -Module nx
Node $Node
{

$Contents = @'
search contoso.com
domain contoso.com
nameserver 10.185.85.11
'@

$Contents = LinuxString $Contents

nxFile resolvConf
{
    DestinationPath = "/etc/resolv.conf"
    Mode = "644"        
    Type = "file"
    Contents = $Contents
    
}
}
```

## Esempio

L'esempio seguente specifica che la directory `/opt/mydir` esiste e che nella directory è presente un file con il contenuto specificato.

```
Import-DSCResource -Module nx 

Node $node {
nxFile DirectoryExample
{
   Ensure = "Present"
   DestinationPath = "/opt/mydir"
   Type = "Directory"
}

nxFile FileExample
{
    Ensure = "Present"
    Destinationpath = "/opt/mydir/myfile"
    Contents=@"
#!/bin/bash`necho "hello world"`n
"@ 
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
} 
}
```




<!--HONumber=Jun16_HO4-->


