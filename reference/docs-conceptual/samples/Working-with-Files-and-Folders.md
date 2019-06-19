---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Utilizzo di file e cartelle
ms.openlocfilehash: 0f7cb233918b59475417ec49b611ecc25a94ebe1
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030697"
---
# <a name="working-with-files-and-folders"></a>Utilizzo di file e cartelle

Gli spostamenti nelle unità di Windows PowerShell e la modifica degli elementi in tali unità è simile alla modifica di file e cartelle nelle unità disco fisiche di Windows. Questa sezione illustra come gestire attività specifiche di manipolazione di file e cartelle usando PowerShell.

## <a name="listing-all-the-files-and-folders-within-a-folder"></a>Elenco di tutti i file e le cartelle all'interno di una cartella

È possibile usare **Get-ChildItem** per ottenere tutti gli elementi direttamente all'interno di una cartella. Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema. Ad esempio, questo comando visualizza il contenuto diretto dell'unità C di Windows PowerShell, che corrisponde all'unità fisica di Windows C:

```powershell
Get-ChildItem -Path C:\ -Force
```

Il comando consente di elencare solo gli elementi contenuti direttamente, in modo molto simile al comando **DIR** di Cmd.exe o a **ls** in una shell UNIX. Per visualizzare gli elementi contenuti, è necessario specificare anche il parametro **-Recurse**. (L'esecuzione di questo comando può richiedere tempi estremamente lunghi.) Per elencare tutti gli elementi nell'unità C:

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

**Get-ChildItem** consente di filtrare gli elementi tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome. È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi tramite il cmdlet **Where-Object**.

Il comando seguente consente di trovare tutti i file eseguibili all'interno della cartella Programmi modificati per l'ultima volta dopo il 1 ottobre 2005 e che non hanno dimensioni minori di 1 o maggiori di 10 MB:

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a>Copia di file e cartelle

La copia viene eseguita con **Copy-Item**. Il comando seguente esegue il backup di C:\\boot.ini in C:\\boot.bak:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

Se il file di destinazione esiste già, il tentativo di copia non riesce. Per sovrascrivere una destinazione preesistente, usare il parametro **Force**:

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

Questo comando funziona anche quando la destinazione è di sola lettura.

La copia di cartelle funziona allo stesso modo. Questo comando copia la cartella C:\\temp\\test1 in modo ricorsivo nella nuova cartella C:\\temp\\DeleteMe:

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

È anche possibile copiare una selezione di elementi. Il comando seguente copia tutti i file con estensione txt contenuti in un punto qualsiasi in c:\\data: in c:\\temp\\text:

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

Per eseguire copie nel file system, è comunque possibile usare altri strumenti. XCOPY, ROBOCOPY e gli oggetti COM, come **Scripting.FileSystemObject**, funzionano tutti in Windows PowerShell. Ad esempio, è possibile usare la classe **Scripting.FileSystem COM** di Windows Script Host per eseguire il backup di C:\\boot.ini in C:\\boot.bak:

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a>Creazione di file e cartelle

La creazione di nuovi elementi funziona allo stesso modo in tutti i provider di Windows PowerShell. Se un provider di Windows PowerShell include più di un tipo di elemento, ad esempio, il provider FileSystem di Windows PowerShell distingue tra file e directory, è necessario specificare il tipo di elemento.

Questo comando crea una nuova cartella C:\\temp\\New Folder:

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

Questo comando crea un nuovo file vuoto C:\\temp\\New Folder\\file.txt

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a>Rimozione di tutti i file e le cartelle all'interno di una cartella

È possibile rimuovere gli elementi contenuti tramite **Remove-Item**, ma verrà richiesto di confermare la rimozione, se l'elemento contiene altri elementi. Ad esempio, se si tenta di eliminare la cartella C:\\temp\\DeleteMe che contiene altri elementi, Windows PowerShell richiede una conferma prima di eliminare la cartella:

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Se si preferisce evitare la richiesta di conferma per ogni elemento di contenuto, specificare il parametro **Recurse**:

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a>Mapping di una cartella locale come unità accessibile di Windows

È anche possibile mappare una cartella locale, usando il comando **subst**. Il comando seguente crea un'unità locale P: con radice nella directory Programmi locale:

```powershell
subst p: $env:programfiles
```

Come per le unità di rete, le unità mappate all'interno di Windows PowerShell con **subst** diventano immediatamente visibili nella shell di Windows PowerShell.

## <a name="reading-a-text-file-into-an-array"></a>Lettura di un file di testo in una matrice

Uno dei formati di archiviazione più comuni per i dati di testo è un file con righe separate considerate come elementi di dati distinti. Il cmdlet **Get-Content** può essere usato per leggere un intero file in un unico passaggio, come illustrato di seguito:

```
PS> Get-Content -Path C:\boot.ini
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional"
 /noexecute=AlwaysOff /fastdetect
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS=" Microsoft Windows XP Professional
with Data Execution Prevention" /noexecute=optin /fastdetect
```

**Get-Content** gestisce già i dati letti dal file come matrice, con un elemento per ogni riga del contenuto del file. È possibile verificarlo controllando il valore **Length** del contenuto restituito:

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

Questo comando è particolarmente utile per ottenere elenchi di informazioni in Windows PowerShell direttamente. Ad esempio, è possibile archiviare un elenco di nomi di computer o indirizzi IP in un file C:\\temp\\domainMembers.tx, con un nome in ogni riga del file. È possibile usare **Get-Content** per recuperare il contenuto del file e inserirlo nella variabile **$Computers**:

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

**$Computers** è ora una matrice contenente un nome di computer in ogni elemento.
