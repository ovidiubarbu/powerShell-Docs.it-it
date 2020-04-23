---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Manipolazione diretta di elementi
ms.openlocfilehash: 50aed569cf6b876297abe3cf1544eba70f6279ce
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030134"
---
# <a name="manipulating-items-directly"></a><span data-ttu-id="ec621-103">Manipolazione diretta di elementi</span><span class="sxs-lookup"><span data-stu-id="ec621-103">Manipulating Items Directly</span></span>

<span data-ttu-id="ec621-104">Gli elementi visualizzati nelle unità di Windows PowerShell, ad esempio file e cartelle nelle unità di file system, e le chiavi del Registro di sistema nelle unità del Registro di sistema di Windows PowerShell sono denominati *elementi* in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec621-104">The elements that you see in Windows PowerShell drives, such as the files and folders in the file system drives, and the registry keys in the Windows PowerShell registry drives, are called *items* in Windows PowerShell.</span></span> <span data-ttu-id="ec621-105">I cmdlet per gestire gli elementi includono il sostantivo **Item** nei relativi nomi.</span><span class="sxs-lookup"><span data-stu-id="ec621-105">The cmdlets for working with them item have the noun **Item** in their names.</span></span>

<span data-ttu-id="ec621-106">L'output del comando **Get-Command -Noun Item** indica che ci sono nove cmdlet di tipo elemento in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ec621-106">The output of the **Get-Command -Noun Item** command shows that there are nine Windows PowerShell item cmdlets.</span></span>

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

## <a name="creating-new-items-new-item"></a><span data-ttu-id="ec621-107">Creazione di nuovi elementi (New-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-107">Creating New Items (New-Item)</span></span>

<span data-ttu-id="ec621-108">Per creare un nuovo elemento nel file system, usare il cmdlet **New-Item**.</span><span class="sxs-lookup"><span data-stu-id="ec621-108">To create a new item in the file system, use the **New-Item** cmdlet.</span></span> <span data-ttu-id="ec621-109">Includere il parametro **Path** con il percorso dell'elemento e il parametro **ItemType** con il valore "file" o "directory".</span><span class="sxs-lookup"><span data-stu-id="ec621-109">Include the **Path** parameter with path to the item, and the **ItemType** parameter with a value of "file" or "directory".</span></span>

<span data-ttu-id="ec621-110">Ad esempio, per creare una nuova directory denominata "New.Directory" nella directory C:\\Temp, digitare:</span><span class="sxs-lookup"><span data-stu-id="ec621-110">For example, to create a new directory named "New.Directory"in the C:\\Temp directory,  type:</span></span>

```
PS> New-Item -Path c:\temp\New.Directory -ItemType Directory

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  11:29 AM            New.Directory
```

<span data-ttu-id="ec621-111">Per creare un file, cambiare il valore del parametro **ItemType** in "file".</span><span class="sxs-lookup"><span data-stu-id="ec621-111">To create a file, change the value of the **ItemType** parameter to "file".</span></span> <span data-ttu-id="ec621-112">Ad esempio, per creare un file denominato "file1.txt" nella directory New.Directory, digitare:</span><span class="sxs-lookup"><span data-stu-id="ec621-112">For example, to create a file named "file1.txt" in the New.Directory directory, type:</span></span>

```
PS> New-Item -Path C:\temp\New.Directory\file1.txt -ItemType file

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\temp\New.Directory

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-18  11:44 AM          0 file1
```

<span data-ttu-id="ec621-113">È possibile usare la stessa tecnica per creare una nuova chiave del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="ec621-113">You can use the same technique to create a new registry key.</span></span> <span data-ttu-id="ec621-114">In realtà, una chiave è più facile da creare perché si tratta dell'unico tipo di elemento del Registro di sistema di Windows.</span><span class="sxs-lookup"><span data-stu-id="ec621-114">In fact, a registry key is easier to create because the only item type in the Windows registry is a key.</span></span> <span data-ttu-id="ec621-115">Le voci del Registro di sistema corrispondono invece a *proprietà* elemento. Ad esempio, per creare una chiave denominata "_Test" nella sottochiave CurrentVersion, digitare:</span><span class="sxs-lookup"><span data-stu-id="ec621-115">(Registry entries are item *properties*.) For example, to create a key named "_Test" in the CurrentVersion subkey, type:</span></span>

```
PS> New-Item -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion_Test

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Micros
oft\Windows\CurrentVersion

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 _Test                          {}
```

<span data-ttu-id="ec621-116">Quando si digita un percorso del Registro di sistema, assicurarsi di includere i due punti ( **:** ) nei nomi delle unità di Windows PowerShell, HKLM: e HKCU:.</span><span class="sxs-lookup"><span data-stu-id="ec621-116">When typing a registry path, be sure to include the colon (**:**) in the Windows PowerShell drive names, HKLM: and HKCU:.</span></span> <span data-ttu-id="ec621-117">Senza i due punti, Windows PowerShell non riconosce il nome dell'unità nel percorso.</span><span class="sxs-lookup"><span data-stu-id="ec621-117">Without the colon, Windows PowerShell does not recognize the drive name in the path.</span></span>

## <a name="why-registry-values-are-not-items"></a><span data-ttu-id="ec621-118">Perché i valori del Registro di sistema non sono elementi</span><span class="sxs-lookup"><span data-stu-id="ec621-118">Why Registry Values are not Items</span></span>

<span data-ttu-id="ec621-119">Quando si usa il cmdlet **Get-ChildItem** per trovare gli elementi di una chiave del Registro di sistema, in realtà non si vedranno mai le voci effettive del Registro di sistema o i relativi valori.</span><span class="sxs-lookup"><span data-stu-id="ec621-119">When you use the **Get-ChildItem** cmdlet to find the items in a registry key, you will never see actual registry entries or their values.</span></span>

<span data-ttu-id="ec621-120">Ad esempio, la chiave del Registro di sistema **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** contiene in genere diverse voci del Registro di sistema che rappresentano le applicazioni eseguite all'avvio del sistema.</span><span class="sxs-lookup"><span data-stu-id="ec621-120">For example, the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion\\Run** usually contains several registry entries that represent applications that run when the system starts.</span></span>

<span data-ttu-id="ec621-121">Tuttavia, quando si usa **Get-ChildItem** per cercare gli elementi figlio nella chiave, si vedrà solo la sottochiave **OptionalComponents**:</span><span class="sxs-lookup"><span data-stu-id="ec621-121">However, when you use **Get-ChildItem** to look for child items in the key, all you will see is the **OptionalComponents** subkey of the key:</span></span>

```
PS> Get-ChildItem HKLM:\Software\Microsoft\Windows\CurrentVersion\Run

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\Micros
oft\Windows\CurrentVersion\Run
SKC  VC Name                           Property
---  -- ----                           --------
  3   0 OptionalComponents             {}
```

<span data-ttu-id="ec621-122">Anche se sarebbe comodo trattare le voci del Registro di sistema come elementi, non è possibile specificare un percorso di una voce in modo da assicurarsi che sia univoco.</span><span class="sxs-lookup"><span data-stu-id="ec621-122">Although it would be convenient to treat registry entries as items, you cannot specify a path to a registry entry in a way that ensures that it is unique.</span></span> <span data-ttu-id="ec621-123">La notazione del percorso non distingue la sottochiave del Registro di sistema denominata **Run** dalla voce del Registro di sistema **(Default)** nella sottochiave **Run**.</span><span class="sxs-lookup"><span data-stu-id="ec621-123">The path notation does not distinguish between the registry subkey named **Run** and the **(Default)** registry entry in the **Run** subkey.</span></span> <span data-ttu-id="ec621-124">Si noti anche che, poiché i nomi delle voci del Registro di sistema possono contenere il carattere barra rovesciata ( **\\** ), se le voci fossero elementi non si potrebbe usare la notazione del percorso per distinguere una voce del Registro di sistema denominata **Windows\\CurrentVersion\\Run** dalla sottochiave situata in tale percorso.</span><span class="sxs-lookup"><span data-stu-id="ec621-124">Furthermore, because registry entry names can contain the backslash character (**\\**), if registry entries were items, then you could not use the path notation to distinguish a registry entry named **Windows\\CurrentVersion\\Run** from the subkey that is located in that path.</span></span>

## <a name="renaming-existing-items-rename-item"></a><span data-ttu-id="ec621-125">Ridenominazione di elementi esistenti (Rename-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-125">Renaming Existing Items (Rename-Item)</span></span>

<span data-ttu-id="ec621-126">Per cambiare il nome di un file o di una cartella, usare il cmdlet **Rename-Item**.</span><span class="sxs-lookup"><span data-stu-id="ec621-126">To change the name of a file or folder, use the **Rename-Item** cmdlet.</span></span> <span data-ttu-id="ec621-127">Il comando seguente cambia il nome del file **file1.txt** in **fileOne.txt**.</span><span class="sxs-lookup"><span data-stu-id="ec621-127">The following command changes the name of the **file1.txt** file to **fileOne.txt**.</span></span>

```powershell
Rename-Item -Path C:\temp\New.Directory\file1.txt fileOne.txt
```

<span data-ttu-id="ec621-128">Il cmdlet **Rename-Item** è in grado di cambiare il nome di un file o di una cartella, ma non di spostare un elemento.</span><span class="sxs-lookup"><span data-stu-id="ec621-128">The **Rename-Item** cmdlet can change the name of a file or a folder, but it cannot move an item.</span></span> <span data-ttu-id="ec621-129">Il comando seguente non riesce perché tenta di spostare il file dalla directory New.Directory alla directory Temp.</span><span class="sxs-lookup"><span data-stu-id="ec621-129">The following command fails because it attempts to move the file from the New.Directory directory to the Temp directory.</span></span>

```
PS> Rename-Item -Path C:\temp\New.Directory\fileOne.txt c:\temp\fileOne.txt
Rename-Item : Cannot rename because the target specified is not a path.
At line:1 char:12
+ Rename-Item  <<<< -Path C:\temp\New.Directory\fileOne c:\temp\fileOne.txt
```

## <a name="moving-items-move-item"></a><span data-ttu-id="ec621-130">Spostamento di elementi (Move-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-130">Moving Items (Move-Item)</span></span>

<span data-ttu-id="ec621-131">Per spostare un file o una cartella, usare il cmdlet **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="ec621-131">To move a file or folder, use the **Move-Item** cmdlet.</span></span>

<span data-ttu-id="ec621-132">Ad esempio, il comando seguente sposta la directory New.Directory dalla directory C:\\temp alla radice dell'unità C:.</span><span class="sxs-lookup"><span data-stu-id="ec621-132">For example, the following command moves the New.Directory directory from the C:\\temp directory to the root of the C: drive.</span></span> <span data-ttu-id="ec621-133">Per verificare che l'elemento sia stato spostato, includere il parametro **PassThru** del cmdlet **Move-Item**.</span><span class="sxs-lookup"><span data-stu-id="ec621-133">To verify that the item was moved, include the **PassThru** parameter of the **Move-Item** cmdlet.</span></span> <span data-ttu-id="ec621-134">Senza il parametro **Passthru**, il cmdlet **Move-Item** non visualizza i risultati.</span><span class="sxs-lookup"><span data-stu-id="ec621-134">Without **Passthru**, the **Move-Item** cmdlet does not display any results.</span></span>

```
PS> Move-Item -Path C:\temp\New.Directory -Destination C:\ -PassThru

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
d----        2006-05-18  12:14 PM            New.Directory
```

## <a name="copying-items-copy-item"></a><span data-ttu-id="ec621-135">Copia di elementi (Copy-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-135">Copying Items (Copy-Item)</span></span>

<span data-ttu-id="ec621-136">Se si ha familiarità con le operazioni di copia in altre shell, il comportamento del cmdlet **Copy-Item** in Windows PowerShell potrebbe risultare insolito.</span><span class="sxs-lookup"><span data-stu-id="ec621-136">If you are familiar with the copy operations in other shells, you might find the behavior of the **Copy-Item** cmdlet in Windows PowerShell to be unusual.</span></span> <span data-ttu-id="ec621-137">Quando si copia un elemento da una posizione a un'altra, Copy-Item non ne copia il contenuto per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="ec621-137">When you copy an item from one location to another, Copy-Item does not copy its contents by default.</span></span>

<span data-ttu-id="ec621-138">Ad esempio, se si copia la directory **New.Directory** dall'unità C: nella directory C:\\temp, il comando riesce, ma i file della directory New.Directory non vengono copiati.</span><span class="sxs-lookup"><span data-stu-id="ec621-138">For example, if you copy the **New.Directory** directory from the C: drive to the C:\\temp directory, the command succeeds, but the files in the New.Directory directory are not copied.</span></span>

```powershell
Copy-Item -Path C:\New.Directory -Destination C:\temp
```

<span data-ttu-id="ec621-139">Se si visualizza il contenuto di **C:\\temp\\New.Directory**, si scoprirà che la directory non contiene file:</span><span class="sxs-lookup"><span data-stu-id="ec621-139">If you display the contents of **C:\\temp\\New.Directory**, you will find that it contains no files:</span></span>

```
PS> Get-ChildItem -Path C:\temp\New.Directory
PS>
```

<span data-ttu-id="ec621-140">Perché il cmdlet **Copy-Item** non copia il contenuto nella nuova posizione?</span><span class="sxs-lookup"><span data-stu-id="ec621-140">Why doesn't the **Copy-Item** cmdlet copy the contents to the new location?</span></span>

<span data-ttu-id="ec621-141">Il cmdlet **Copy-Item** è stato progettato per essere generico, non per la copia di file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="ec621-141">The **Copy-Item** cmdlet was designed to be generic; it is not just for copying files and folders.</span></span> <span data-ttu-id="ec621-142">Inoltre, anche se si copiano file e cartelle, si potrebbe scegliere di copiare solo il contenitore e non gli elementi al suo interno.</span><span class="sxs-lookup"><span data-stu-id="ec621-142">Also, even when copying files and folders, you might want to copy only the container and not the items within it.</span></span>

<span data-ttu-id="ec621-143">Per copiare tutto il contenuto di una cartella, includere il parametro **Recurse** del cmdlet **Copy-Item** nel comando.</span><span class="sxs-lookup"><span data-stu-id="ec621-143">To copy all of the contents of a folder, include the **Recurse** parameter of the **Copy-Item** cmdlet in the command.</span></span> <span data-ttu-id="ec621-144">Se è già stata copiata la directory senza il suo contenuto, aggiungere il parametro **Force**, che consente di sovrascrivere la cartella vuota.</span><span class="sxs-lookup"><span data-stu-id="ec621-144">If you have already copied the directory without its contents, add the **Force** parameter, which allows you to overwrite the empty folder.</span></span>

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

## <a name="deleting-items-remove-item"></a><span data-ttu-id="ec621-145">Eliminazione di elementi (Remove-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-145">Deleting Items (Remove-Item)</span></span>

<span data-ttu-id="ec621-146">Per eliminare file e cartelle, usare il cmdlet **Remove-Item**.</span><span class="sxs-lookup"><span data-stu-id="ec621-146">To delete files and folders, use the **Remove-Item** cmdlet.</span></span> <span data-ttu-id="ec621-147">I cmdlet di Windows PowerShell, come **Remove-Item**, che possono apportare modifiche significative e irreversibili spesso chiedono conferma quando si immettono i relativi comandi.</span><span class="sxs-lookup"><span data-stu-id="ec621-147">Windows PowerShell cmdlets, such as **Remove-Item**, that can make significant, irreversible changes will often prompt for confirmation when you enter its commands.</span></span> <span data-ttu-id="ec621-148">Se ad esempio si prova a rimuovere la cartella **New.Directory**, verrà chiesto di confermare il comando perché la cartella contiene file:</span><span class="sxs-lookup"><span data-stu-id="ec621-148">For example, if you try to remove the **New.Directory** folder, you will be prompted to confirm the command, because the folder contains files:</span></span>

```
PS> Remove-Item C:\New.Directory

Confirm
The item at C:\temp\New.Directory has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
 sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="ec621-149">Poiché la risposta predefinita è **Sì**, per eliminare la cartella e i relativi file premere **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="ec621-149">Because **Yes** is the default response, to delete the folder and its files, press the **Enter** key.</span></span> <span data-ttu-id="ec621-150">Per rimuovere la cartella senza confermare, usare il parametro **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="ec621-150">To remove the folder without confirming, use the **-Recurse** parameter.</span></span>

```powershell
Remove-Item C:\temp\New.Directory -Recurse
```

## <a name="executing-items-invoke-item"></a><span data-ttu-id="ec621-151">Esecuzione di elementi (Invoke-Item)</span><span class="sxs-lookup"><span data-stu-id="ec621-151">Executing Items (Invoke-Item)</span></span>

<span data-ttu-id="ec621-152">Windows PowerShell usa il cmdlet **Invoke-Item** per eseguire un'azione predefinita per un file o una cartella.</span><span class="sxs-lookup"><span data-stu-id="ec621-152">Windows PowerShell uses the **Invoke-Item** cmdlet to perform a default action for a file or folder.</span></span> <span data-ttu-id="ec621-153">L'azione predefinita è determinata dal gestore dell'applicazione predefinito nel Registro di sistema. L'effetto è identico a quello che si ottiene facendo doppio clic sull'elemento in Esplora file.</span><span class="sxs-lookup"><span data-stu-id="ec621-153">This default action is determined by the default application handler in the registry; the effect is the same as if you double-click the item in File Explorer.</span></span>

<span data-ttu-id="ec621-154">Si supponga ad esempio di eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ec621-154">For example, suppose you run the following command:</span></span>

```powershell
Invoke-Item C:\WINDOWS
```

<span data-ttu-id="ec621-155">Viene visualizzata una finestra di Esplora risorse situata in C:\\Windows, come se fosse stato fatto doppio clic sulla cartella C:\\Windows.</span><span class="sxs-lookup"><span data-stu-id="ec621-155">An Explorer window that is located in C:\\Windows appears, just as if you had double-clicked the C:\\Windows folder.</span></span>

<span data-ttu-id="ec621-156">Se si esegue l'invoke del file **Boot.ini** in un sistema precedente a Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="ec621-156">If you invoke the **Boot.ini** file on a system prior to Windows Vista:</span></span>

```powershell
Invoke-Item C:\boot.ini
```

<span data-ttu-id="ec621-157">Se il tipo di file con estensione ini è associato al Blocco note, il file boot.ini si aprirà nel Blocco note.</span><span class="sxs-lookup"><span data-stu-id="ec621-157">If the .ini file type is associated with Notepad, the boot.ini file opens in Notepad.</span></span>
