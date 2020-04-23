---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Utilizzo delle chiavi del Registro di sistema
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736846"
---
# <a name="working-with-registry-keys"></a><span data-ttu-id="196bf-103">Utilizzo delle chiavi del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="196bf-103">Working with Registry Keys</span></span>

<span data-ttu-id="196bf-104">Dato che le chiavi del Registro di sistema sono elementi nelle unità PowerShell, il loro uso è molto simile a quello di file e cartelle.</span><span class="sxs-lookup"><span data-stu-id="196bf-104">Because registry keys are items on PowerShell drives, working with them is very similar to working with files and folders.</span></span> <span data-ttu-id="196bf-105">Una differenza fondamentale è che ogni elemento in un'unità PowerShell basata sul Registro di sistema è un contenitore, come una cartella in un'unità del file system.</span><span class="sxs-lookup"><span data-stu-id="196bf-105">One critical difference is that every item on a registry-based PowerShell drive is a container, just like a folder on a file system drive.</span></span> <span data-ttu-id="196bf-106">Tuttavia, le voci del Registro di sistema e i relativi valori associati sono proprietà degli elementi e non elementi distinti.</span><span class="sxs-lookup"><span data-stu-id="196bf-106">However, registry entries and their associated values are properties of the items, not distinct items.</span></span>

## <a name="listing-all-subkeys-of-a-registry-key"></a><span data-ttu-id="196bf-107">Elenco di tutte le sottochiavi di una chiave del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="196bf-107">Listing All Subkeys of a Registry Key</span></span>

<span data-ttu-id="196bf-108">È possibile visualizzare tutti gli elementi direttamente all'interno di una chiave del Registro di sistema usando `Get-ChildItem`.</span><span class="sxs-lookup"><span data-stu-id="196bf-108">You can show all items directly within a registry key by using `Get-ChildItem`.</span></span> <span data-ttu-id="196bf-109">Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema.</span><span class="sxs-lookup"><span data-stu-id="196bf-109">Add the optional **Force** parameter to display hidden or system items.</span></span> <span data-ttu-id="196bf-110">Questo comando, ad esempio, visualizza gli elementi direttamente all'interno dell'unità PowerShell `HKCU:`, che corrisponde all'hive del Registro di sistema `HKEY_CURRENT_USER`:</span><span class="sxs-lookup"><span data-stu-id="196bf-110">For example, this command displays the items directly within PowerShell drive `HKCU:`, which corresponds to the `HKEY_CURRENT_USER` registry hive:</span></span>

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

<span data-ttu-id="196bf-111">Si tratta delle chiavi di primo livello visibili in `HKEY_CURRENT_USER` nell'editor del Registro di sistema (Regedit.exe).</span><span class="sxs-lookup"><span data-stu-id="196bf-111">These are the top-level keys visible under `HKEY_CURRENT_USER` in the Registry Editor (Regedit.exe).</span></span>

<span data-ttu-id="196bf-112">È possibile specificare questo percorso del Registro di sistema anche specificando il nome del provider del Registro di sistema, seguito da `::`.</span><span class="sxs-lookup"><span data-stu-id="196bf-112">You can also specify this registry path by specifying the registry provider's name, followed by `::`.</span></span> <span data-ttu-id="196bf-113">Il nome completo del provider del Registro di sistema è `Microsoft.PowerShell.Core\Registry`, ma può essere abbreviato semplicemente in `Registry`.</span><span class="sxs-lookup"><span data-stu-id="196bf-113">The registry provider's full name is `Microsoft.PowerShell.Core\Registry`, but this can be shortened to just `Registry`.</span></span> <span data-ttu-id="196bf-114">I comandi seguenti consentono di elencare il contenuto direttamente in `HKCU:`.</span><span class="sxs-lookup"><span data-stu-id="196bf-114">Any of the following commands will list the contents directly under `HKCU:`.</span></span>

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

<span data-ttu-id="196bf-115">Questi comandi consentono di elencare solo gli elementi contenuti direttamente, in modo molto simile a `DIR` in **Cmd.exe** o `ls` in una shell UNIX.</span><span class="sxs-lookup"><span data-stu-id="196bf-115">These commands list only the directly contained items, much like using `DIR` in **Cmd.exe** or `ls` in a UNIX shell.</span></span> <span data-ttu-id="196bf-116">Per visualizzare gli elementi contenuti, è necessario specificare il parametro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="196bf-116">To show contained items, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="196bf-117">Per elencare tutte le chiavi del Registro di sistema in `HKCU:`, usare il comando seguente.</span><span class="sxs-lookup"><span data-stu-id="196bf-117">To list all registry keys in `HKCU:`, use the following command.</span></span>

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

<span data-ttu-id="196bf-118">`Get-ChildItem` consente di applicare funzionalità di filtro complesse tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome.</span><span class="sxs-lookup"><span data-stu-id="196bf-118">`Get-ChildItem` can perform complex filtering capabilities through its **Path**, **Filter**, **Include**, and **Exclude** parameters, but those parameters are typically based only on name.</span></span> <span data-ttu-id="196bf-119">È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi usando il cmdlet `Where-Object`.</span><span class="sxs-lookup"><span data-stu-id="196bf-119">You can perform complex filtering based on other properties of items by using the `Where-Object` cmdlet.</span></span> <span data-ttu-id="196bf-120">Il comando seguente consente di trovare tutte le chiavi all'interno di `HKCU:\Software` che hanno non più di una sottochiave e hanno inoltre esattamente quattro valori:</span><span class="sxs-lookup"><span data-stu-id="196bf-120">The following command finds all keys within `HKCU:\Software` that have no more than one subkey and also have exactly four values:</span></span>

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a><span data-ttu-id="196bf-121">Copia di chiavi</span><span class="sxs-lookup"><span data-stu-id="196bf-121">Copying Keys</span></span>

<span data-ttu-id="196bf-122">La copia viene eseguita con `Copy-Item`.</span><span class="sxs-lookup"><span data-stu-id="196bf-122">Copying is done with `Copy-Item`.</span></span> <span data-ttu-id="196bf-123">Nell'esempio seguente viene copiata la sottochiave `CurrentVersion` di `HKLM:\SOFTWARE\Microsoft\Windows\` e tutte le relative proprietà in `HKCU:\`.</span><span class="sxs-lookup"><span data-stu-id="196bf-123">The following example copies the `CurrentVersion` subkey of `HKLM:\SOFTWARE\Microsoft\Windows\` and all of its properties to `HKCU:\`.</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

<span data-ttu-id="196bf-124">Se si esamina questa nuova chiave nell'editor del Registro di sistema o tramite `Get-ChildItem`, si noterà che nella nuova posizione non sono presenti copie delle sottochiavi contenute.</span><span class="sxs-lookup"><span data-stu-id="196bf-124">If you examine this new key in the registry editor or by using `Get-ChildItem`, you notice that you do not have copies of the contained subkeys in the new location.</span></span> <span data-ttu-id="196bf-125">Per copiare tutto il contenuto di un contenitore, è necessario specificare il parametro **Recurse**.</span><span class="sxs-lookup"><span data-stu-id="196bf-125">In order to copy all of the contents of a container, you need to specify the **Recurse** parameter.</span></span> <span data-ttu-id="196bf-126">Per rendere ricorsivo il comando di copia precedente, è possibile usare questo comando:</span><span class="sxs-lookup"><span data-stu-id="196bf-126">To make the preceding copy command recursive, you would use this command:</span></span>

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

<span data-ttu-id="196bf-127">Per eseguire copie nel file system, è comunque possibile continuare a usare altri strumenti già disponibili.</span><span class="sxs-lookup"><span data-stu-id="196bf-127">You can still use other tools you already have available to perform filesystem copies.</span></span> <span data-ttu-id="196bf-128">In Windows PowerShell è possibile usare qualsiasi strumento di modifica del Registro di sistema, tra cui **reg.exe**, **regini.exe**, **regedit.exe** e gli oggetti COM che supportano la modifica del Registro di sistema, ad esempio **WScript.Shell** e la classe **StdRegProv** di WMI.</span><span class="sxs-lookup"><span data-stu-id="196bf-128">Any registry editing tools—including **reg.exe**, **regini.exe**, **regedit.exe**, and COM objects that support registry editing, such as **WScript.Shell** and WMI's **StdRegProv** class can be used from within Windows PowerShell.</span></span>

## <a name="creating-keys"></a><span data-ttu-id="196bf-129">Creazione di chiavi</span><span class="sxs-lookup"><span data-stu-id="196bf-129">Creating Keys</span></span>

<span data-ttu-id="196bf-130">La creazione di nuove chiavi nel Registro di sistema è più semplice rispetto alla creazione di un nuovo elemento in un file system.</span><span class="sxs-lookup"><span data-stu-id="196bf-130">Creating new keys in the registry is simpler than creating a new item in a file system.</span></span> <span data-ttu-id="196bf-131">Dato che tutte le chiavi del Registro di sistema sono contenitori, non è necessario specificare il tipo di elemento, ma è sufficiente indicare un percorso esplicito, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="196bf-131">Because all registry keys are containers, you do not need to specify the item type; you simply supply an explicit path, such as:</span></span>

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

<span data-ttu-id="196bf-132">Per specificare una chiave, è anche possibile usare un percorso basato su provider:</span><span class="sxs-lookup"><span data-stu-id="196bf-132">You can also use a provider-based path to specify a key:</span></span>

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a><span data-ttu-id="196bf-133">Eliminazione di chiavi</span><span class="sxs-lookup"><span data-stu-id="196bf-133">Deleting Keys</span></span>

<span data-ttu-id="196bf-134">L'eliminazione di elementi è un'attività fondamentalmente identica per tutti i provider.</span><span class="sxs-lookup"><span data-stu-id="196bf-134">Deleting items is essentially the same for all providers.</span></span> <span data-ttu-id="196bf-135">I comandi seguenti consentono di rimuovere elementi in modo invisibile all'utente:</span><span class="sxs-lookup"><span data-stu-id="196bf-135">The following commands will silently remove items:</span></span>

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a><span data-ttu-id="196bf-136">Rimozione di tutte le chiavi in una chiave specifica</span><span class="sxs-lookup"><span data-stu-id="196bf-136">Removing All Keys Under a Specific Key</span></span>

<span data-ttu-id="196bf-137">È possibile rimuovere gli elementi contenuti tramite `Remove-Item`, ma verrà richiesto di confermare la rimozione se l'elemento ne contiene altri.</span><span class="sxs-lookup"><span data-stu-id="196bf-137">You can remove contained items by using `Remove-Item`, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="196bf-138">Ad esempio, se si tenta di eliminare la sottochiave `HKCU:\CurrentVersion` creata, verrà visualizzato il messaggio seguente:</span><span class="sxs-lookup"><span data-stu-id="196bf-138">For example, if we attempt to delete the `HKCU:\CurrentVersion` subkey we created, we see this:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

<span data-ttu-id="196bf-139">Per eliminare gli elementi contenuti senza che venga richiesta la conferma dell'eliminazione, specificare il parametro **Recurse**:</span><span class="sxs-lookup"><span data-stu-id="196bf-139">To delete contained items without prompting, specify the **Recurse** parameter:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

<span data-ttu-id="196bf-140">Per rimuovere tutti gli elementi all'interno di `HKCU:\CurrentVersion` ma non lo stesso `HKCU:\CurrentVersion`, è invece possibile usare:</span><span class="sxs-lookup"><span data-stu-id="196bf-140">If you wanted to remove all items within `HKCU:\CurrentVersion` but not `HKCU:\CurrentVersion` itself, you could instead use:</span></span>

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
