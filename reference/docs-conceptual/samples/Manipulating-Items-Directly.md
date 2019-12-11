---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Manipolazione diretta di elementi
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030134"
---
# <a name="manipulating-items-directly"></a>Manipolazione diretta di elementi

Gli elementi visualizzati nelle unità di Windows PowerShell, ad esempio file e cartelle nelle unità di file system, e le chiavi del Registro di sistema nelle unità del Registro di sistema di Windows PowerShell sono denominati *elementi* in Windows PowerShell. I cmdlet per gestire gli elementi includono il sostantivo **Item** nei relativi nomi.

L'output del comando **Get-Command -Noun Item** indica che ci sono nove cmdlet di tipo elemento in Windows PowerShell.

```
PS> Get-Command -Noun Item

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Clear-Item                      Clear-Item [-Path] <String[]...
Cmdlet          Copy-Item                       Copy-Item [-Path] <String[]>...
Cmdlet          Get-Item                        Get-Item [-Path] <String[]> ...
Cmdlet          Invoke-Item                     Invoke-Item [-Path] <String[...
Cmdlet          Move-Item                       Move-Item [-Path] <String[]>...
Cmdlet          New-Item                        New-Item [-Path] <String[]> ...
Cmdlet          Remove-Item                     Remove-Item [-Path] <String[...
Cmdlet          Rename-Item                     Rename-Item [-Path] <String>...
Cmdlet          Set-Item                        Set-Item [-Path] <String[]> ...
```

## <a name="creating-new-items-new-item"></a>Creazione di nuovi elementi (New-Item)

Per creare un nuovo elemento nel file system, usare il cmdlet **New-Item**. Includere il parametro **Path** con il percorso dell'elemento e il parametro **ItemType** con il valore "file" o "directory".

Ad esempio, per creare una nuova directory denominata "New.Directory" nella directory C:\\Temp, digitare:

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

Per creare un file, cambiare il valore del parametro **ItemType** in "file". Ad esempio, per creare un file denominato "file1.txt" nella directory New.Directory, digitare:

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

È possibile usare la stessa tecnica per creare una nuova chiave del Registro di sistema. In realtà, una chiave è più facile da creare perché si tratta dell'unico tipo di elemento del Registro di sistema di Windows. Le voci del Registro di sistema corrispondono invece a *proprietà* elemento. Ad esempio, per creare una chiave denominata "_Test" nella sottochiave CurrentVersion, digitare:

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

Quando si digita un percorso del Registro di sistema, assicurarsi di includere i due punti ( **:** ) nei nomi delle unità di Windows PowerShell, HKLM: e HKCU:. Senza i due punti, Windows PowerShell non riconosce il nome dell'unità nel percorso.

## <a name="why-registry-values-are-not-items"></a>Perché i valori del Registro di sistema non sono elementi

Quando si usa il cmdlet **Get-ChildItem** per trovare gli elementi di una chiave del Registro di sistema, in realtà non si vedranno mai le voci effettive del Registro di sistema o i relativi valori.

Ad esempio, la chiave del Registro di sistema **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** contiene in genere diverse voci del Registro di sistema che rappresentano le applicazioni eseguite all'avvio del sistema.

Tuttavia, quando si usa **Get-ChildItem** per cercare gli elementi figlio nella chiave, si vedrà solo la sottochiave **OptionalComponents**:

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

Anche se sarebbe comodo trattare le voci del Registro di sistema come elementi, non è possibile specificare un percorso di una voce in modo da assicurarsi che sia univoco. La notazione del percorso non distingue la sottochiave del Registro di sistema denominata **Run** dalla voce del Registro di sistema **(Default)** nella sottochiave **Run**. Si noti anche che, poiché i nomi delle voci del Registro di sistema possono contenere il carattere barra rovesciata ( **\\** ), se le voci fossero elementi non si potrebbe usare la notazione del percorso per distinguere una voce del Registro di sistema denominata **Windows\\CurrentVersion\\Run** dalla sottochiave situata in tale percorso.

## <a name="renaming-existing-items-rename-item"></a>Ridenominazione di elementi esistenti (Rename-Item)

Per cambiare il nome di un file o di una cartella, usare il cmdlet **Rename-Item**. Il comando seguente cambia il nome del file **file1.txt** in **fileOne.txt**.

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

Il cmdlet **Rename-Item** è in grado di cambiare il nome di un file o di una cartella, ma non di spostare un elemento. Il comando seguente non riesce perché tenta di spostare il file dalla directory New.Directory alla directory Temp.

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a>Spostamento di elementi (Move-Item)

Per spostare un file o una cartella, usare il cmdlet **Move-Item**.

Ad esempio, il comando seguente sposta la directory New.Directory dalla directory C:\\temp alla radice dell'unità C:. Per verificare che l'elemento sia stato spostato, includere il parametro **PassThru** del cmdlet **Move-Item**. Senza il parametro **Passthru**, il cmdlet **Move-Item** non visualizza i risultati.

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a>Copia di elementi (Copy-Item)

Se si ha familiarità con le operazioni di copia in altre shell, il comportamento del cmdlet **Copy-Item** in Windows PowerShell potrebbe risultare insolito. Quando si copia un elemento da una posizione a un'altra, Copy-Item non ne copia il contenuto per impostazione predefinita.

Ad esempio, se si copia la directory **New.Directory** dall'unità C: nella directory C:\\temp, il comando riesce, ma i file della directory New.Directory non vengono copiati.

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

Se si visualizza il contenuto di **C:\\temp\\New.Directory**, si scoprirà che la directory non contiene file:

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

Perché il cmdlet **Copy-Item** non copia il contenuto nella nuova posizione?

Il cmdlet **Copy-Item** è stato progettato per essere generico, non per la copia di file e cartelle. Inoltre, anche se si copiano file e cartelle, si potrebbe scegliere di copiare solo il contenitore e non gli elementi al suo interno.

Per copiare tutto il contenuto di una cartella, includere il parametro **Recurse** del cmdlet **Copy-Item** nel comando. Se è già stata copiata la directory senza il suo contenuto, aggiungere il parametro **Force**, che consente di sovrascrivere la cartella vuota.

```
PS> Copy-Item -Path C:\New.Directory -Destination C:\temp -Recurse -Force -Passthru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18   1:53 PM            New.Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

## <a name="deleting-items-remove-item"></a>Eliminazione di elementi (Remove-Item)

Per eliminare file e cartelle, usare il cmdlet **Remove-Item**. I cmdlet di Windows PowerShell, come **Remove-Item**, che possono apportare modifiche significative e irreversibili spesso chiedono conferma quando si immettono i relativi comandi. Se ad esempio si prova a rimuovere la cartella **New.Directory**, verrà chiesto di confermare il comando perché la cartella contiene file:

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Poiché la risposta predefinita è **Sì**, per eliminare la cartella e i relativi file premere **INVIO**. Per rimuovere la cartella senza confermare, usare il parametro **-Recurse**.

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a>Esecuzione di elementi (Invoke-Item)

Windows PowerShell usa il cmdlet **Invoke-Item** per eseguire un'azione predefinita per un file o una cartella. L'azione predefinita è determinata dal gestore dell'applicazione predefinito nel Registro di sistema. L'effetto è identico a quello che si ottiene facendo doppio clic sull'elemento in Esplora file.

Si supponga ad esempio di eseguire il comando seguente:

```powershell
Invoke-Item C:\WINDOWS
```

Viene visualizzata una finestra di Esplora risorse situata in C:\\Windows, come se fosse stato fatto doppio clic sulla cartella C:\\Windows.

Se si esegue l'invoke del file **Boot.ini** in un sistema precedente a Windows Vista:

```powershell
Invoke-Item C:\boot.ini
```

Se il tipo di file con estensione ini è associato al Blocco note, il file boot.ini si aprirà nel Blocco note.
