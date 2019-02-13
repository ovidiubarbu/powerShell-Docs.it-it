---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle voci del Registro di sistema
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681542"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="75cbf-103">Gestione delle voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-103">Working with Registry Entries</span></span>

<span data-ttu-id="75cbf-104">Poiché le voci del Registro di sistema sono proprietà di chiavi e, in quanto tali, non possono essere esplorate direttamente, è necessario adottare un approccio leggermente diverso per gestirle.</span><span class="sxs-lookup"><span data-stu-id="75cbf-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="75cbf-105">Visualizzazione di un elenco di voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-105">Listing Registry Entries</span></span>

<span data-ttu-id="75cbf-106">Esistono molti modi diversi per esaminare le voci del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="75cbf-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="75cbf-107">Il modo più semplice consiste nell'ottenere i nomi di proprietà associati a una chiave.</span><span class="sxs-lookup"><span data-stu-id="75cbf-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="75cbf-108">Ad esempio, per visualizzare i nomi delle voci nella chiave del Registro di sistema `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, usare `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="75cbf-109">Le chiavi del Registro di sistema hanno una proprietà con il nome generico "Property" che corrisponde a un elenco delle voci contenute al loro interno.</span><span class="sxs-lookup"><span data-stu-id="75cbf-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="75cbf-110">Il comando seguente seleziona la proprietà Property ed espande gli elementi in modo che vengano visualizzati in un elenco:</span><span class="sxs-lookup"><span data-stu-id="75cbf-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="75cbf-111">Per visualizzare le voci del Registro di sistema in un formato più leggibile, usare `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="75cbf-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="75cbf-112">Le proprietà correlate a Windows PowerShell per la chiave sono precedute tutte dal prefisso "PS", ad esempio **PSPath**, **PSParentPath**, **PSChildName** e **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="75cbf-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="75cbf-113">È possibile usare la notazione "`*.*`." per fare riferimento al percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="75cbf-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="75cbf-114">È possibile usare `Set-Location` per modificare il **CurrentVersion** contenitore del Registro di sistema prima:</span><span class="sxs-lookup"><span data-stu-id="75cbf-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="75cbf-115">In alternativa, è possibile usare la proprietà predefinita HKLM PSDrive con `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="75cbf-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="75cbf-116">È quindi possibile usare la notazione "`*.*`." del percorso corrente per elencare le proprietà senza specificare un percorso completo:</span><span class="sxs-lookup"><span data-stu-id="75cbf-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="75cbf-117">Espansione di percorso funziona allo stesso modo che nel file system, in modo da questo percorso è possibile ottenere il **ItemProperty** listato `HKLM:\SOFTWARE\Microsoft\Windows\Help` usando `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="75cbf-118">Recupero di una singola voce del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="75cbf-119">Per recuperare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili.</span><span class="sxs-lookup"><span data-stu-id="75cbf-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="75cbf-120">In questo esempio viene trovato il valore di **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="75cbf-121">Usando `Get-ItemProperty`, usare il **percorso** parametro per specificare il nome della chiave e il **nome** parametro per specificare il nome del **DevicePath** voce.</span><span class="sxs-lookup"><span data-stu-id="75cbf-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="75cbf-122">Questo comando restituisce le proprietà standard di Windows PowerShell oltre alla proprietà **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="75cbf-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="75cbf-123">Sebbene `Get-ItemProperty` ha **filtro**, **inclusione**, e **escludere** parametri, non possono essere usati per filtrare in base al nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="75cbf-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="75cbf-124">Questi parametri fanno riferimento alle chiavi del Registro di sistema, quali sono i percorsi degli elementi e non le voci del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="75cbf-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="75cbf-125">Voci del Registro di sistema che sono proprietà degli elementi.</span><span class="sxs-lookup"><span data-stu-id="75cbf-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="75cbf-126">Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="75cbf-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="75cbf-127">Per informazioni su reg.exe, digitare `reg.exe /?` un prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="75cbf-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="75cbf-128">Per trovare la voce DevicePath, usare reg.exe come illustrato nel comando seguente:</span><span class="sxs-lookup"><span data-stu-id="75cbf-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="75cbf-129">È anche possibile usare l'oggetto **WshShell COM** per trovare alcune voci del Registro di sistema, ma questo metodo non funziona con dati binari di grandi dimensioni o con nomi di voci del Registro di sistema che includono caratteri come "\\".</span><span class="sxs-lookup"><span data-stu-id="75cbf-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="75cbf-130">Aggiungere il nome di proprietà al percorso dell'elemento con un separatore \\:</span><span class="sxs-lookup"><span data-stu-id="75cbf-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a><span data-ttu-id="75cbf-131">L'impostazione di una voce del Registro di sistema Single</span><span class="sxs-lookup"><span data-stu-id="75cbf-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="75cbf-132">Se si desidera modificare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci possibili.</span><span class="sxs-lookup"><span data-stu-id="75cbf-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="75cbf-133">Questo esempio viene modificata la **tracciato** voce sotto `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="75cbf-134">Il **percorso** voce specifica dove trovare i file eseguibili.</span><span class="sxs-lookup"><span data-stu-id="75cbf-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="75cbf-135">Recuperare il valore corrente del **tracciato** voce usando `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="75cbf-136">Aggiungere il nuovo valore, separandolo con una `;`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="75cbf-137">Usare `Set-ItemProperty` con la chiave specificata, nome e valore per modificare la voce del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="75cbf-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="75cbf-138">Sebbene `Set-ItemProperty` ha **filtro**, **inclusione**, e **escludere** parametri, non possono essere usati per filtrare in base al nome della proprietà.</span><span class="sxs-lookup"><span data-stu-id="75cbf-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="75cbf-139">Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi, e non a voci del Registro di sistema, che sono invece proprietà di elementi.</span><span class="sxs-lookup"><span data-stu-id="75cbf-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="75cbf-140">Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="75cbf-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="75cbf-141">Per informazioni su reg.exe, digitare **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="75cbf-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="75cbf-142">al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="75cbf-142">at a command prompt.</span></span>

<span data-ttu-id="75cbf-143">Nell'esempio seguente il **percorso** voce rimuovendo il percorso aggiunto nell'esempio precedente.</span><span class="sxs-lookup"><span data-stu-id="75cbf-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="75cbf-144">`Get-ItemProperty` viene ancora usato per recuperare il valore corrente per evitare la necessità di analizzare la stringa restituita dal `reg query`.</span><span class="sxs-lookup"><span data-stu-id="75cbf-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="75cbf-145">Il **sottostringa** e **LastIndexOf** vengono utilizzati metodi per recuperare l'ultimo percorso aggiunto per il **percorso** voce.</span><span class="sxs-lookup"><span data-stu-id="75cbf-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="75cbf-146">Creazione di nuove voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-146">Creating New Registry Entries</span></span>

<span data-ttu-id="75cbf-147">Per aggiungere una nuova voce denominata "PowerShellPath" per il **CurrentVersion** l'uso delle chiavi, `New-ItemProperty` con il percorso della chiave, il nome della voce e il valore della voce.</span><span class="sxs-lookup"><span data-stu-id="75cbf-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="75cbf-148">In questo esempio verrà usato il valore della variabile di Windows PowerShell `$PSHome`, cui è archiviato il percorso della directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="75cbf-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="75cbf-149">È possibile aggiungere la nuova voce alla chiave usando il comando seguente, che restituisce anche informazioni sulla nuova voce:</span><span class="sxs-lookup"><span data-stu-id="75cbf-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="75cbf-150">**PropertyType** deve essere il nome di un membro dell'enumerazione **Microsoft.Win32.RegistryValueKind** della tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="75cbf-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="75cbf-151">Valore di PropertyType</span><span class="sxs-lookup"><span data-stu-id="75cbf-151">PropertyType Value</span></span>|<span data-ttu-id="75cbf-152">Significato</span><span class="sxs-lookup"><span data-stu-id="75cbf-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="75cbf-153">Binary</span><span class="sxs-lookup"><span data-stu-id="75cbf-153">Binary</span></span>|<span data-ttu-id="75cbf-154">Dati binari</span><span class="sxs-lookup"><span data-stu-id="75cbf-154">Binary data</span></span>|
|<span data-ttu-id="75cbf-155">DWord</span><span class="sxs-lookup"><span data-stu-id="75cbf-155">DWord</span></span>|<span data-ttu-id="75cbf-156">Numero che corrisponde a un valore UInt32 valido</span><span class="sxs-lookup"><span data-stu-id="75cbf-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="75cbf-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="75cbf-157">ExpandString</span></span>|<span data-ttu-id="75cbf-158">Stringa che può contenere variabili di ambiente espanse dinamicamente</span><span class="sxs-lookup"><span data-stu-id="75cbf-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="75cbf-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="75cbf-159">MultiString</span></span>|<span data-ttu-id="75cbf-160">Stringa su più righe</span><span class="sxs-lookup"><span data-stu-id="75cbf-160">A multiline string</span></span>|
|<span data-ttu-id="75cbf-161">String</span><span class="sxs-lookup"><span data-stu-id="75cbf-161">String</span></span>|<span data-ttu-id="75cbf-162">Qualsiasi valore di stringa</span><span class="sxs-lookup"><span data-stu-id="75cbf-162">Any string value</span></span>|
|<span data-ttu-id="75cbf-163">QWord</span><span class="sxs-lookup"><span data-stu-id="75cbf-163">QWord</span></span>|<span data-ttu-id="75cbf-164">8 byte di dati binari</span><span class="sxs-lookup"><span data-stu-id="75cbf-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="75cbf-165">È possibile aggiungere una voce del Registro di sistema in più posizioni specificando una matrice di valori nel parametro **Path**:</span><span class="sxs-lookup"><span data-stu-id="75cbf-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="75cbf-166">È anche possibile sovrascrivere un valore preesistente di voce del Registro di sistema aggiungendo il **Force** parametro per qualsiasi `New-ItemProperty` comando.</span><span class="sxs-lookup"><span data-stu-id="75cbf-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="75cbf-167">Ridenominazione delle voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-167">Renaming Registry Entries</span></span>

<span data-ttu-id="75cbf-168">Per rinominare la **PowerShellPath** voce in "PSHome", usare `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="75cbf-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="75cbf-169">Per visualizzare il valore rinominato, aggiungere il parametro **PassThru** al comando.</span><span class="sxs-lookup"><span data-stu-id="75cbf-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="75cbf-170">Eliminazione di voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="75cbf-170">Deleting Registry Entries</span></span>

<span data-ttu-id="75cbf-171">Per eliminare le voci del Registro di sistema PSHome e PowerShellPath, usare `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="75cbf-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
