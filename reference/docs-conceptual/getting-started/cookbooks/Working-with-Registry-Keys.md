---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Utilizzo delle chiavi del Registro di sistema
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: efb2c016afa2212c2907c0740ad26c4e4cddd3af
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="463f2-103">Utilizzo delle chiavi del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="463f2-103">Working with Registry Keys</span></span>
<span data-ttu-id="463f2-104">Dato che le chiavi del Registro di sistema sono elementi nelle unità di Windows PowerShell, il loro utilizzo è molto simile a quello di file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="463f2-104">Because registry keys are items on Windows PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="463f2-105">Una differenza fondamentale è che ogni elemento in un'unità di Windows PowerShell basata sul Registro di sistema è un contenitore, come una cartella in un'unità del file system.</span><span class="sxs-lookup"><span data-stu-id="463f2-105">One critical difference is that every item on a registry-based Windows PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="463f2-106">Tuttavia, le voci del Registro di sistema e i relativi valori associati sono proprietà degli elementi e non elementi distinti.</span><span class="sxs-lookup"><span data-stu-id="463f2-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

### <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="463f2-107">Elenco di tutte le sottochiavi di una chiave del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="463f2-107">Listing All Subkeys of a Registry Key</span></span>
<span data-ttu-id="463f2-108">È possibile usare **Get-ChildItem** per visualizzare tutti gli elementi direttamente all'interno di una chiave del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="463f2-108">You can show all items directly within a registry key by using **Get-ChildItem**.</span></span> <span data-ttu-id="463f2-109">Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema.</span><span class="sxs-lookup"><span data-stu-id="463f2-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="463f2-110">Questo comando, ad esempio, visualizza gli elementi direttamente all'interno dell'unità di Windows PowerShell HKCU:, che corrisponde all'hive del Registro di sistema HKEY_CURRENT_USER:</span><span class="sxs-lookup"><span data-stu-id="463f2-110">For example, this command displays the items directly within Windows PowerShell drive HKCU:, which corresponds to the HKEY_CURRENT_USER registry hive:</span></span>

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

<span data-ttu-id="463f2-111">Si tratta delle chiavi di primo livello visibili in HKEY_CURRENT_USER nell'editor del Registro di sistema (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="463f2-111">These are the top-level keys visible under HKEY_CURRENT_USER in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="463f2-112">È possibile specificare questo percorso del Registro di sistema anche specificando il nome del provider del Registro di sistema, seguito da "**::**".</span><span class="sxs-lookup"><span data-stu-id="463f2-112">You can also specify this registry path by specifying the registry provider's name, followed by "**::**".</span></span> <span data-ttu-id="463f2-113">Il nome completo del provider del Registro di sistema è **Microsoft.PowerShell.Core\\Registry**, ma può essere abbreviato semplicemente in **Registry**.</span><span class="sxs-lookup"><span data-stu-id="463f2-113">The registry provider's full name is **Microsoft.PowerShell.Core\\Registry**, but this can be shortened to just **Registry**.</span></span> <span data-ttu-id="463f2-114">I comandi seguenti consentono di elencare il contenuto direttamente in HKCU:</span><span class="sxs-lookup"><span data-stu-id="463f2-114">Any of the following commands will list the contents directly under HKCU:</span></span>

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="463f2-115">Questi comandi consentono di elencare solo gli elementi contenuti direttamente, in modo molto simile al comando **DIR** di Cmd.exe o a **ls** in una shell UNIX.</span><span class="sxs-lookup"><span data-stu-id="463f2-115">These commands list only the directly contained items, much like using Cmd.exe's **DIR** command or **ls** in a UNIX shell.</span></span> <span data-ttu-id="463f2-116">Per visualizzare gli elementi contenuti, è necessario specificare il parametro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="463f2-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="463f2-117">Per elencare tutte le chiavi del Registro di sistema in HKCU, usare il comando seguente (questa operazione può richiedere tempi estremamente lunghi):</span><span class="sxs-lookup"><span data-stu-id="463f2-117">To list all registry keys in HKCU, use the following command (This operation can take an extremely long time.):</span></span>

```
Get-ChildItem -Path hkcu:\ -Recurse
```

<span data-ttu-id="463f2-118">**Get-ChildItem** consente di applicare funzionalità di filtro complesse tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome.</span><span class="sxs-lookup"><span data-stu-id="463f2-118">**Get-ChildItem** can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="463f2-119">È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi tramite il cmdlet **Where-Object**.</span><span class="sxs-lookup"><span data-stu-id="463f2-119">You can perform complex filtering based on other properties of items by using the **Where-Object**cmdlet.</span></span> <span data-ttu-id="463f2-120">Il comando seguente consente di trovare tutte le chiavi all'interno di HKCU:\\Software che non hanno più di una sottochiave e hanno inoltre esattamente quattro valori:</span><span class="sxs-lookup"><span data-stu-id="463f2-120">The following command finds all keys within HKCU:\\Software that have no more than one subkey and also have exactly four values:</span></span>

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a><span data-ttu-id="463f2-121">Copia di chiavi</span><span class="sxs-lookup"><span data-stu-id="463f2-121">Copying Keys</span></span>
<span data-ttu-id="463f2-122">La copia viene eseguita con **Copy-Item**.</span><span class="sxs-lookup"><span data-stu-id="463f2-122">Copying is done with **Copy-Item**.</span></span> <span data-ttu-id="463f2-123">Il comando seguente copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e tutte le relative proprietà in HKCU:\\, creando una nuova chiave denominata "CurrentVersion":</span><span class="sxs-lookup"><span data-stu-id="463f2-123">The following command copies HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion and all of its properties to HKCU:\\, creating a new key named "CurrentVersion":</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

<span data-ttu-id="463f2-124">Se si esamina questa nuova chiave nell'editor del Registro di sistema o tramite **Get-ChildItem**, si noterà che non sono disponibili copie delle sottochiavi contenute nella nuova posizione.</span><span class="sxs-lookup"><span data-stu-id="463f2-124">If you examine this new key in the registry editor or by using **Get-ChildItem**, you will notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="463f2-125">Per copiare tutto il contenuto di un contenitore, è necessario specificare il parametro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="463f2-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="463f2-126">Per rendere ricorsivo il comando di copia precedente, è possibile usare questo comando:</span><span class="sxs-lookup"><span data-stu-id="463f2-126">To make the preceding copy command recursive, you would use this command:</span></span>

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

<span data-ttu-id="463f2-127">Per eseguire copie nel file system, è comunque possibile continuare a usare altri strumenti già disponibili.</span><span class="sxs-lookup"><span data-stu-id="463f2-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="463f2-128">È possibile usare dall'interno di Windows PowerShell qualsiasi strumento di modifica del Registro di sistema (tra cui reg.exe, regini.exe e regedit.exe) e gli oggetti COM che supportano la modifica del Registro di sistema (come WScript.Shell e la classe WMI StdRegProv).</span><span class="sxs-lookup"><span data-stu-id="463f2-128">Any registry editing tools—including reg.exe, regini.exe, and regedit.exe—and COM objects that support registry editing (such as WScript.Shell and WMI's StdRegProv class) can be used from within Windows PowerShell.</span></span>

### <a name="creating-keys"></a><span data-ttu-id="463f2-129">Creazione di chiavi</span><span class="sxs-lookup"><span data-stu-id="463f2-129">Creating Keys</span></span>
<span data-ttu-id="463f2-130">La creazione di nuove chiavi nel Registro di sistema è più semplice rispetto alla creazione di un nuovo elemento in un file system.</span><span class="sxs-lookup"><span data-stu-id="463f2-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="463f2-131">Dato che tutte le chiavi del Registro di sistema sono contenitori, non è necessario specificare il tipo di elemento, ma è sufficiente indicare un percorso esplicito, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="463f2-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```
New-Item -Path hkcu:\software_DeleteMe
```

<span data-ttu-id="463f2-132">Per specificare una chiave, è anche possibile usare un percorso basato su provider:</span><span class="sxs-lookup"><span data-stu-id="463f2-132">You can also use a provider-based path to specify a key:</span></span>

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a><span data-ttu-id="463f2-133">Eliminazione di chiavi</span><span class="sxs-lookup"><span data-stu-id="463f2-133">Deleting Keys</span></span>
<span data-ttu-id="463f2-134">L'eliminazione di elementi è un'attività fondamentalmente identica per tutti i provider.</span><span class="sxs-lookup"><span data-stu-id="463f2-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="463f2-135">I comandi seguenti consentono di rimuovere elementi in modo invisibile all'utente:</span><span class="sxs-lookup"><span data-stu-id="463f2-135">The following commands will silently remove items:</span></span>

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="463f2-136">Rimozione di tutte le chiavi in una chiave specifica</span><span class="sxs-lookup"><span data-stu-id="463f2-136">Removing All Keys Under a Specific Key</span></span>
<span data-ttu-id="463f2-137">È possibile rimuovere gli elementi contenuti tramite **Remove-Item**, ma verrà richiesto di confermare la rimozione, se l'elemento contiene altri elementi.</span><span class="sxs-lookup"><span data-stu-id="463f2-137">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="463f2-138">Ad esempio, se si tenta di eliminare la sottochiave HKCU:\\CurrentVersion creata, verrà visualizzato il messaggio seguente:</span><span class="sxs-lookup"><span data-stu-id="463f2-138">For example, if we attempt to delete the HKCU:\\CurrentVersion subkey we created, we see this:</span></span>

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="463f2-139">Per eliminare gli elementi contenuti senza che venga richiesta la conferma dell'eliminazione, specificare il parametro **-Recurse**:</span><span class="sxs-lookup"><span data-stu-id="463f2-139">To delete contained items without prompting, specify the **-Recurse** parameter:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="463f2-140">Per rimuovere tutti gli elementi all'interno di HKCU:\\CurrentVersion ma non la cartella HKCU:\\CurrentVersion stessa, è possibile invece usare:</span><span class="sxs-lookup"><span data-stu-id="463f2-140">If you wanted to remove all items within HKCU:\\CurrentVersion but not HKCU:\\CurrentVersion itself, you could instead use:</span></span>

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

