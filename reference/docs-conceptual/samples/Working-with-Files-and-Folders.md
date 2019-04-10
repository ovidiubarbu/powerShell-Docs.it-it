---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Utilizzo di file e cartelle
ms.assetid: c0ceb96b-e708-45f3-803b-d1f61a48f4c1
ms.openlocfilehash: 393e886a4945222198d9b81019250c5d5b905ad3
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293221"
---
# <a name="working-with-files-and-folders"></a><span data-ttu-id="9a428-103">Utilizzo di file e cartelle</span><span class="sxs-lookup"><span data-stu-id="9a428-103">Working with Files and Folders</span></span>

<span data-ttu-id="9a428-104">Gli spostamenti nelle unità di Windows PowerShell e la modifica degli elementi in tali unità è simile alla modifica di file e cartelle nelle unità disco fisiche di Windows.</span><span class="sxs-lookup"><span data-stu-id="9a428-104">Navigating through Windows PowerShell drives and manipulating the items on them is similar to manipulating files and folders on Windows physical disk drives.</span></span> <span data-ttu-id="9a428-105">Questa sezione illustra come gestire attività specifiche di manipolazione di file e cartelle usando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a428-105">This section discusses how to deal with specific file and folder manipulation tasks using PowerShell.</span></span>

## <a name="listing-all-the-files-and-folders-within-a-folder"></a><span data-ttu-id="9a428-106">Elenco di tutti i file e le cartelle all'interno di una cartella</span><span class="sxs-lookup"><span data-stu-id="9a428-106">Listing All the Files and Folders Within a Folder</span></span>

<span data-ttu-id="9a428-107">È possibile usare **Get-ChildItem** per ottenere tutti gli elementi direttamente all'interno di una cartella.</span><span class="sxs-lookup"><span data-stu-id="9a428-107">You can get all items directly within a folder by using **Get-ChildItem**.</span></span> <span data-ttu-id="9a428-108">Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema.</span><span class="sxs-lookup"><span data-stu-id="9a428-108">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="9a428-109">Ad esempio, questo comando visualizza il contenuto diretto dell'unità C di Windows PowerShell, che corrisponde all'unità fisica di Windows C:</span><span class="sxs-lookup"><span data-stu-id="9a428-109">For example, this command displays the direct contents of Windows PowerShell Drive C (which is the same as the Windows physical drive C):</span></span>

```powershell
Get-ChildItem -Path C:\ -Force
```

<span data-ttu-id="9a428-110">Il comando consente di elencare solo gli elementi contenuti direttamente, in modo molto simile al comando **DIR** di Cmd.exe o a **ls** in una shell UNIX.</span><span class="sxs-lookup"><span data-stu-id="9a428-110">The command lists only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="9a428-111">Per visualizzare gli elementi contenuti, è necessario specificare anche il parametro **-Recurse**.</span><span class="sxs-lookup"><span data-stu-id="9a428-111">In order to show contained items, you need to specify the **-Recurse** parameter as well.</span></span> <span data-ttu-id="9a428-112">(L'esecuzione di questo comando può richiedere tempi estremamente lunghi.) Per elencare tutti gli elementi nell'unità C:</span><span class="sxs-lookup"><span data-stu-id="9a428-112">(This can take an extremely long time to complete.) To list everything on the C drive:</span></span>

```powershell
Get-ChildItem -Path C:\ -Force -Recurse
```

<span data-ttu-id="9a428-113">**Get-ChildItem** consente di filtrare gli elementi tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome.</span><span class="sxs-lookup"><span data-stu-id="9a428-113">**Get-ChildItem** can filter items with its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those are typically based only on name.</span></span> <span data-ttu-id="9a428-114">È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi tramite il cmdlet **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="9a428-114">You can perform complex filtering based on other properties of items by using **Where-Object**.</span></span>

<span data-ttu-id="9a428-115">Il comando seguente consente di trovare tutti i file eseguibili all'interno della cartella Programmi modificati per l'ultima volta dopo il 1 ottobre 2005 e che non hanno dimensioni minori di 1 o maggiori di 10 MB:</span><span class="sxs-lookup"><span data-stu-id="9a428-115">The following command finds all executables within the Program Files folder that were last modified after October 1, 2005 and which are neither smaller than 1 megabyte nor larger than 10 megabytes:</span></span>

```powershell
Get-ChildItem -Path $env:ProgramFiles -Recurse -Include *.exe | Where-Object -FilterScript {($_.LastWriteTime -gt '2005-10-01') -and ($_.Length -ge 1mb) -and ($_.Length -le 10mb)}
```

## <a name="copying-files-and-folders"></a><span data-ttu-id="9a428-116">Copia di file e cartelle</span><span class="sxs-lookup"><span data-stu-id="9a428-116">Copying Files and Folders</span></span>

<span data-ttu-id="9a428-117">La copia viene eseguita con **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="9a428-117">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="9a428-118">Il comando seguente esegue il backup di C:\\boot.ini in C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="9a428-118">The following command backs up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak
```

<span data-ttu-id="9a428-119">Se il file di destinazione esiste già, il tentativo di copia non riesce.</span><span class="sxs-lookup"><span data-stu-id="9a428-119">If the destination file already exists, the copy attempt fails.</span></span> <span data-ttu-id="9a428-120">Per sovrascrivere una destinazione preesistente, usare il parametro **Force**:</span><span class="sxs-lookup"><span data-stu-id="9a428-120">To overwrite a pre-existing destination, use the **Force** parameter:</span></span>

```powershell
Copy-Item -Path C:\boot.ini -Destination C:\boot.bak -Force
```

<span data-ttu-id="9a428-121">Questo comando funziona anche quando la destinazione è di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="9a428-121">This command works even when the destination is read-only.</span></span>

<span data-ttu-id="9a428-122">La copia di cartelle funziona allo stesso modo.</span><span class="sxs-lookup"><span data-stu-id="9a428-122">Folder copying works the same way.</span></span> <span data-ttu-id="9a428-123">Questo comando copia la cartella C:\\temp\\test1 in modo ricorsivo nella nuova cartella C:\\temp\\DeleteMe:</span><span class="sxs-lookup"><span data-stu-id="9a428-123">This command copies the folder C:\\temp\\test1 to the new folder C:\\temp\\DeleteMe recursively:</span></span>

```powershell
Copy-Item C:\temp\test1 -Recurse C:\temp\DeleteMe
```

<span data-ttu-id="9a428-124">È anche possibile copiare una selezione di elementi.</span><span class="sxs-lookup"><span data-stu-id="9a428-124">You can also copy a selection of items.</span></span> <span data-ttu-id="9a428-125">Il comando seguente copia tutti i file con estensione txt contenuti in un punto qualsiasi in c:\\data: in c:\\temp\\text:</span><span class="sxs-lookup"><span data-stu-id="9a428-125">The following command copies all .txt files contained anywhere in c:\\data to c:\\temp\\text:</span></span>

```powershell
Copy-Item -Filter *.txt -Path c:\data -Recurse -Destination C:\temp\text
```

<span data-ttu-id="9a428-126">Per eseguire copie nel file system, è comunque possibile usare altri strumenti.</span><span class="sxs-lookup"><span data-stu-id="9a428-126">You can still use other tools to perform file system copies.</span></span> <span data-ttu-id="9a428-127">XCOPY, ROBOCOPY e gli oggetti COM, come **Scripting.FileSystemObject**, funzionano tutti in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a428-127">XCOPY, ROBOCOPY, and COM objects, such as the **Scripting.FileSystemObject,** all work in Windows PowerShell.</span></span> <span data-ttu-id="9a428-128">Ad esempio, è possibile usare la classe **Scripting.FileSystem COM** di Windows Script Host per eseguire il backup di C:\\boot.ini in C:\\boot.bak:</span><span class="sxs-lookup"><span data-stu-id="9a428-128">For example, you can use the Windows Script Host **Scripting.FileSystem COM** class to back up C:\\boot.ini to C:\\boot.bak:</span></span>

```powershell
(New-Object -ComObject Scripting.FileSystemObject).CopyFile('C:\boot.ini', 'C:\boot.bak')
```

## <a name="creating-files-and-folders"></a><span data-ttu-id="9a428-129">Creazione di file e cartelle</span><span class="sxs-lookup"><span data-stu-id="9a428-129">Creating Files and Folders</span></span>

<span data-ttu-id="9a428-130">La creazione di nuovi elementi funziona allo stesso modo in tutti i provider di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a428-130">Creating new items works the same on all Windows PowerShell providers.</span></span> <span data-ttu-id="9a428-131">Se un provider di Windows PowerShell include più di un tipo di elemento, ad esempio, il provider FileSystem di Windows PowerShell distingue tra file e directory, è necessario specificare il tipo di elemento.</span><span class="sxs-lookup"><span data-stu-id="9a428-131">If a Windows PowerShell provider has more than one type of item—for example, the FileSystem Windows PowerShell provider distinguishes between directories and files—you need to specify the item type.</span></span>

<span data-ttu-id="9a428-132">Questo comando crea una nuova cartella C:\\temp\\New Folder:</span><span class="sxs-lookup"><span data-stu-id="9a428-132">This command creates a new folder C:\\temp\\New Folder:</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder' -ItemType Directory
```

<span data-ttu-id="9a428-133">Questo comando crea un nuovo file vuoto C:\\temp\\New Folder\\file.txt</span><span class="sxs-lookup"><span data-stu-id="9a428-133">This command creates a new empty file C:\\temp\\New Folder\\file.txt</span></span>

```powershell
New-Item -Path 'C:\temp\New Folder\file.txt' -ItemType File
```

## <a name="removing-all-files-and-folders-within-a-folder"></a><span data-ttu-id="9a428-134">Rimozione di tutti i file e le cartelle all'interno di una cartella</span><span class="sxs-lookup"><span data-stu-id="9a428-134">Removing All Files and Folders Within a Folder</span></span>

<span data-ttu-id="9a428-135">È possibile rimuovere gli elementi contenuti tramite **Remove-Item**, ma verrà richiesto di confermare la rimozione, se l'elemento contiene altri elementi.</span><span class="sxs-lookup"><span data-stu-id="9a428-135">You can remove contained items using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="9a428-136">Ad esempio, se si tenta di eliminare la cartella C:\\temp\\DeleteMe che contiene altri elementi, Windows PowerShell richiede una conferma prima di eliminare la cartella:</span><span class="sxs-lookup"><span data-stu-id="9a428-136">For example, if you attempt to delete the folder C:\\temp\\DeleteMe that contains other items, Windows PowerShell prompts you for confirmation before deleting the folder:</span></span>

```
Remove-Item -Path C:\temp\DeleteMe

Confirm
The item at C:\temp\DeleteMe has children and the -recurse parameter was not
specified. If you continue, all children will be removed with the item. Are you
sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="9a428-137">Se si preferisce evitare la richiesta di conferma per ogni elemento di contenuto, specificare il parametro **Recurse**:</span><span class="sxs-lookup"><span data-stu-id="9a428-137">If you do not want to be prompted for each contained item, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path C:\temp\DeleteMe -Recurse
```

## <a name="mapping-a-local-folder-as-a-windows-accessible-drive"></a><span data-ttu-id="9a428-138">Mapping di una cartella locale come unità accessibile di Windows</span><span class="sxs-lookup"><span data-stu-id="9a428-138">Mapping a Local Folder as a Windows Accessible Drive</span></span>

<span data-ttu-id="9a428-139">È anche possibile mappare una cartella locale, usando il comando **subst**.</span><span class="sxs-lookup"><span data-stu-id="9a428-139">You can also map a local folder, using the **subst** command.</span></span> <span data-ttu-id="9a428-140">Il comando seguente crea un'unità locale P: con radice nella directory Programmi locale:</span><span class="sxs-lookup"><span data-stu-id="9a428-140">The following command creates a local drive P: rooted in the local Program Files directory:</span></span>

```powershell
subst p: $env:programfiles
```

<span data-ttu-id="9a428-141">Come per le unità di rete, le unità mappate all'interno di Windows PowerShell con **subst** diventano immediatamente visibili nella shell di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9a428-141">Just as with network drives, drives mapped within Windows PowerShell using **subst** are immediately visible to the Windows PowerShell shell.</span></span>

## <a name="reading-a-text-file-into-an-array"></a><span data-ttu-id="9a428-142">Lettura di un file di testo in una matrice</span><span class="sxs-lookup"><span data-stu-id="9a428-142">Reading a Text File into an Array</span></span>

<span data-ttu-id="9a428-143">Uno dei formati di archiviazione più comuni per i dati di testo è un file con righe separate considerate come elementi di dati distinti.</span><span class="sxs-lookup"><span data-stu-id="9a428-143">One of the more common storage formats for text data is in a file with separate lines treated as distinct data elements.</span></span> <span data-ttu-id="9a428-144">Il cmdlet **Get-Content** può essere usato per leggere un intero file in un unico passaggio, come illustrato di seguito:</span><span class="sxs-lookup"><span data-stu-id="9a428-144">The **Get-Content** cmdlet can be used to read an entire file in one step, as shown here:</span></span>

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

<span data-ttu-id="9a428-145">**Get-Content** gestisce già i dati letti dal file come matrice, con un elemento per ogni riga del contenuto del file.</span><span class="sxs-lookup"><span data-stu-id="9a428-145">**Get-Content** already treats the data read from the file as an array, with one element per line of file content.</span></span> <span data-ttu-id="9a428-146">È possibile verificarlo controllando il valore **Length** del contenuto restituito:</span><span class="sxs-lookup"><span data-stu-id="9a428-146">You can confirm this by checking the **Length** of the returned content:</span></span>

```
PS> (Get-Content -Path C:\boot.ini).Length
6
```

<span data-ttu-id="9a428-147">Questo comando è particolarmente utile per ottenere elenchi di informazioni in Windows PowerShell direttamente.</span><span class="sxs-lookup"><span data-stu-id="9a428-147">This command is most useful for getting lists of information into Windows PowerShell directly.</span></span> <span data-ttu-id="9a428-148">Ad esempio, è possibile archiviare un elenco di nomi di computer o indirizzi IP in un file C:\\temp\\domainMembers.tx, con un nome in ogni riga del file.</span><span class="sxs-lookup"><span data-stu-id="9a428-148">For example, you might store a list of computer names or IP addresses in a file C:\\temp\\domainMembers.txt, with one name on each line of the file.</span></span> <span data-ttu-id="9a428-149">È possibile usare **Get-Content** per recuperare il contenuto del file e inserirlo nella variabile **$Computers**:</span><span class="sxs-lookup"><span data-stu-id="9a428-149">You can use **Get-Content** to retrieve the file contents and put them in the variable **$Computers**:</span></span>

```powershell
$Computers = Get-Content -Path C:\temp\DomainMembers.txt
```

<span data-ttu-id="9a428-150">**$Computers** è ora una matrice contenente un nome di computer in ogni elemento.</span><span class="sxs-lookup"><span data-stu-id="9a428-150">**$Computers** is now an array containing a computer name in each element.</span></span>
