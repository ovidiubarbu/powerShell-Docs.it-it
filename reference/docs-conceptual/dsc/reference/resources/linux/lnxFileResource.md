---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxFile DSC per Linux
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954828"
---
# <a name="dsc-for-linux-nxfile-resource"></a>Risorsa nxFile DSC per Linux

La risorsa **nxFile** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e directory in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|DestinationPath |Indica il percorso in cui si vuole specificare lo stato di un file o una directory. |
|SourcePath |Specifica il percorso da cui copiare la risorsa file o cartella. Questo percorso può essere un percorso locale o un URL `http/https/ftp`. Gli URL `http/https/ftp` remoti sono supportati solo quando il valore della proprietà **Type** è **file**. |
|Type |Specifica se la risorsa configurata è una directory o un file. Impostare questa proprietà su **directory** per indicare che la risorsa è una directory. Impostarla su **file** per indicare che la risorsa è un file. Il valore predefinito è **file**. |
|Sommario |Specifica il contenuto di un file, ad esempio una determinata stringa. |
|Checksum |Definisce il tipo da usare per determinare se due file sono uguali. Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory. I valori sono: **ctime**, **mtime** o **md5**. |
|Recurse |Indica se le sottodirectory sono incluse. Impostare questa proprietà su `$true` per indicare che le sottodirectory devono essere incluse. Il valore predefinito è `$false`. Questa proprietà è valida solo quando la proprietà **Type** è impostata su **directory**. |
|Force |Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore. Usando la proprietà **Force**, tali errori vengono ignorati. Il valore predefinito è `$false`. |
|Collegamenti |Specifica il comportamento desiderato per i collegamenti simbolici. Impostare questa proprietà su **follow** per seguire i collegamenti simbolici e agire sulla destinazione dei collegamenti. Ad esempio, copiare il file invece del collegamento. Impostare questa proprietà su **manage** per agire sul collegamento. Ad esempio, copiare il collegamento stesso. Impostare questa proprietà su **ignore** per ignorare i collegamenti simbolici. |
|Gruppo |Nome del **Group** che avrà le autorizzazioni per il file o la directory. |
|Mode |Specifica le autorizzazioni desiderate per la risorsa, in notazione ottale o simbolica Ad esempio, **777** o **rwxrwxrwx**. Se si usa la notazione simbolica, non fornire il primo carattere che indica una directory o un file. |
|Proprietario |Nome del gruppo proprietario del file o della directory. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se verificare l'esistenza del file. Impostare questa proprietà su **Present** per assicurarsi che il file esista. Impostarla su **Absent** per assicurarsi che il file non esista. Il valore predefinito è **Present**. |

## <a name="additional-information"></a>Informazioni aggiuntive

Linux e Windows usano per impostazione predefinita caratteri di interruzione di riga diversi nei file di testo e questo può causare risultati imprevisti quando si configurano alcuni file in un computer Linux con **nxFile**. Ci sono diversi modi per gestire il contenuto di un file di Linux evitando i problemi causati da caratteri di interruzione di riga imprevisti:

1. Copiare il file da un'origine remota (HTTP, HTTPS o FTP)

   Creare un file in Linux con il contenuto desiderato e metterlo su un server Web o FTP accessibile dai nodi che verranno configurati. Definire la proprietà **SourcePath** nella risorsa **nxFile** con l'URL Web o FTP del file.

   ```powershell
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

1. leggere il contenuto del file nello script di PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) dopo avere impostato la proprietà **$OFS** per usare il carattere di interruzione di riga di Linux.

   ```powershell
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

1. usare una funzione di PowerShell per sostituire le interruzioni di riga di Windows con caratteri di interruzione di riga di Linux.

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
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

## <a name="example"></a>Esempio

L'esempio seguente specifica che la directory `/opt/mydir` esiste e che nella directory è presente un file con il contenuto specificato.

```powershell
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
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```