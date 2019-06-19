---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso di file, cartelle e chiavi del Registro di sistema
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030751"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="9395b-103">Gestione di file, cartelle e chiavi del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="9395b-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="9395b-104">Windows PowerShell usa il sostantivo **Item** per fare riferimento agli elementi presenti in un'unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9395b-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="9395b-105">Nel caso del provider FileSystem di Windows PowerShell, il sostantivo **Item** può fare riferimento a un file, a una cartella o all'unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9395b-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="9395b-106">La visualizzazione e l'uso di questi elementi rappresentano attività di base fondamentali nella maggior parte delle impostazioni amministrative, quindi verranno descritte in dettaglio.</span><span class="sxs-lookup"><span data-stu-id="9395b-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="9395b-107">Enumerazione di file, cartelle e chiavi del Registro di sistema (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="9395b-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="9395b-108">Poiché il recupero di una raccolta di elementi da una specifica posizione è un'attività molto comune, il cmdlet **Get-ChildItem** è stato progettato specificamente per restituire tutti gli elementi presenti in un contenitore, ad esempio una cartella.</span><span class="sxs-lookup"><span data-stu-id="9395b-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="9395b-109">Se si vuole restituire tutti i file e le cartelle contenuti direttamente nella cartella C:\\Windows, digitare:</span><span class="sxs-lookup"><span data-stu-id="9395b-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="9395b-110">L'elenco visualizzato è simile a quello che si otterrebbe immettendo il comando **dir** in **Cmd.exe** o il comando **ls** in una shell di comandi di UNIX.</span><span class="sxs-lookup"><span data-stu-id="9395b-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="9395b-111">È possibile ottenere elenchi molto complessi usando i parametri del cmdlet **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9395b-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="9395b-112">Verranno esaminati alcuni scenari in seguito.</span><span class="sxs-lookup"><span data-stu-id="9395b-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="9395b-113">È possibile visualizzare la sintassi del cmdlet **Get-ChildItem** digitando:</span><span class="sxs-lookup"><span data-stu-id="9395b-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="9395b-114">Questi parametri possono essere combinati in vari modi per ottenere un output estremamente personalizzato.</span><span class="sxs-lookup"><span data-stu-id="9395b-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="9395b-115">Visualizzazione di tutti gli elementi contenuti (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="9395b-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="9395b-116">Per visualizzare sia gli elementi all'interno di una cartella di Windows sia quelli contenuti nelle sottocartelle, usare il parametro **Recurse** di **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9395b-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="9395b-117">L'elenco visualizza tutto il contenuto della cartella di Windows e tutti gli elementi delle relative sottocartelle.</span><span class="sxs-lookup"><span data-stu-id="9395b-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="9395b-118">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9395b-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="9395b-119">Filtraggio degli elementi per nome (-Name)</span><span class="sxs-lookup"><span data-stu-id="9395b-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="9395b-120">Per visualizzare solo i nomi degli elementi, usare il parametro **Name** di **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="9395b-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="9395b-121">Visualizzazione forzata degli elementi nascosti (-Force)</span><span class="sxs-lookup"><span data-stu-id="9395b-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="9395b-122">Gli elementi che sono in genere invisibili in Esplora file o in Cmd.exe non vengono visualizzati nell'output di un comando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9395b-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="9395b-123">Per visualizzare gli elementi nascosti, usare il parametro **Force** di **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9395b-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="9395b-124">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="9395b-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="9395b-125">Questo parametro si chiama Force perché è possibile eseguire forzatamente l'override del normale comportamento del comando **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="9395b-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="9395b-126">Force è un parametro ampiamente usato che forza un'azione che un cmdlet non eseguirebbe normalmente, anche se non esegue nessuna azione che comprometterebbe la sicurezza del sistema.</span><span class="sxs-lookup"><span data-stu-id="9395b-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="9395b-127">Ricerca di corrispondenze con i nomi degli elementi tramite caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="9395b-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="9395b-128">Il comando **Get-ChildItem** accetta i caratteri jolly nel percorso degli elementi da elencare.</span><span class="sxs-lookup"><span data-stu-id="9395b-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="9395b-129">Poiché la corrispondenza tramite caratteri jolly viene gestita dal motore di Windows PowerShell, tutti i cmdlet che accettano caratteri jolly usano la stessa notazione e hanno lo stesso comportamento.</span><span class="sxs-lookup"><span data-stu-id="9395b-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="9395b-130">La notazione dei caratteri jolly di Windows PowerShell include:</span><span class="sxs-lookup"><span data-stu-id="9395b-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="9395b-131">L'asterisco (\*) trova la corrispondenza con zero o più occorrenze di qualsiasi carattere.</span><span class="sxs-lookup"><span data-stu-id="9395b-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="9395b-132">Il punto interrogativo (?) trova la corrispondenza con un unico carattere.</span><span class="sxs-lookup"><span data-stu-id="9395b-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="9395b-133">La parentesi quadra sinistra (\[) e quella destra (]) racchiudono un set di caratteri con cui trovare la corrispondenza.</span><span class="sxs-lookup"><span data-stu-id="9395b-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="9395b-134">Ecco alcuni esempi del funzionamento dei caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="9395b-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="9395b-135">Per trovare tutti i file nella directory Windows con il suffisso **.log** e un nome di base costituito esattamente da cinque caratteri, immettere il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="9395b-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="9395b-136">Per trovare tutti i file che iniziano con la lettera **x** nella directory Windows, digitare:</span><span class="sxs-lookup"><span data-stu-id="9395b-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="9395b-137">Per trovare tutti i file che iniziano con **x** o **z**, digitare:</span><span class="sxs-lookup"><span data-stu-id="9395b-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="9395b-138">Esclusione di elementi (-Exclude)</span><span class="sxs-lookup"><span data-stu-id="9395b-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="9395b-139">È possibile escludere elementi specifici usando il parametro **Exclude** di Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="9395b-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="9395b-140">In questo modo è possibile eseguire complesse operazioni di filtro in un'unica istruzione.</span><span class="sxs-lookup"><span data-stu-id="9395b-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="9395b-141">Si supponga ad esempio di voler trovare la DLL Windows Time Service nella cartella System32 e che non si ricordi il nome della DLL, ma solo che inizia con "W" e che contiene "32".</span><span class="sxs-lookup"><span data-stu-id="9395b-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="9395b-142">Con un'espressione come **w\&#42;32\&#42;.dll** sarà possibile trovare tutte le DLL che soddisfano le condizioni, ma i risultati potrebbero restituire anche le DLL di compatibilità di Windows per Windows 95 e Windows a 16 bit che includono "95" o "16" nei relativi nomi.</span><span class="sxs-lookup"><span data-stu-id="9395b-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="9395b-143">È possibile omettere i file i cui nomi contengono questi numeri usando il parametro **Exclude** con il modello **\&#42;\[9516]\&#42;** :</span><span class="sxs-lookup"><span data-stu-id="9395b-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="9395b-144">Combinazione di parametri Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="9395b-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="9395b-145">È possibile usare diversi parametri del cmdlet **Get-ChildItem** nello stesso comando.</span><span class="sxs-lookup"><span data-stu-id="9395b-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="9395b-146">Prima di combinare i parametri, assicurarsi di comprendere la ricerca di corrispondenze con caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="9395b-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="9395b-147">Ad esempio, il comando seguente non restituisce risultati:</span><span class="sxs-lookup"><span data-stu-id="9395b-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="9395b-148">Non ci sono risultati, nonostante ci siano due DLL che iniziano con la lettera "z" nella cartella Windows.</span><span class="sxs-lookup"><span data-stu-id="9395b-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="9395b-149">Il motivo è che nel percorso è stato specificato il carattere jolly.</span><span class="sxs-lookup"><span data-stu-id="9395b-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="9395b-150">Anche se il comando è ricorsivo, il cmdlet **Get-ChildItem** restituisce solo gli elementi che si trovano nella cartella Windows e i cui nomi terminano con ".dll".</span><span class="sxs-lookup"><span data-stu-id="9395b-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="9395b-151">Per specificare una ricerca ricorsiva dei file i cui nomi corrispondono a un modello specifico, usare il parametro **-Include**.</span><span class="sxs-lookup"><span data-stu-id="9395b-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
