---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Gestione delle voci del Registro di sistema
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 039203a1a6549d4ba33424a278e4803a5e143d4d
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="07644-103">Gestione delle voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-103">Working with Registry Entries</span></span>
<span data-ttu-id="07644-104">Poiché le voci del Registro di sistema sono proprietà di chiavi e, in quanto tali, non possono essere esplorate direttamente, è necessario adottare un approccio leggermente diverso per gestirle.</span><span class="sxs-lookup"><span data-stu-id="07644-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="07644-105">Visualizzazione di un elenco di voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-105">Listing Registry Entries</span></span>
<span data-ttu-id="07644-106">Esistono molti modi diversi per esaminare le voci del Registro di sistema.</span><span class="sxs-lookup"><span data-stu-id="07644-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="07644-107">Il modo più semplice consiste nell'ottenere i nomi di proprietà associati a una chiave.</span><span class="sxs-lookup"><span data-stu-id="07644-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="07644-108">Ad esempio, per visualizzare i nomi delle voci nella chiave del Registro di sistema **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, usare **Get-Item**.</span><span class="sxs-lookup"><span data-stu-id="07644-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="07644-109">Le chiavi del Registro di sistema hanno una proprietà con il nome generico "Property" che corrisponde a un elenco delle voci contenute al loro interno.</span><span class="sxs-lookup"><span data-stu-id="07644-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="07644-110">Il comando seguente seleziona la proprietà Property ed espande gli elementi in modo che vengano visualizzati in un elenco:</span><span class="sxs-lookup"><span data-stu-id="07644-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="07644-111">Per visualizzare le voci del Registro di sistema in un formato più leggibile, usare **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="07644-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

<span data-ttu-id="07644-112">Le proprietà correlate a Windows PowerShell per la chiave sono precedute tutte dal prefisso "PS", ad esempio **PSPath**, **PSParentPath**, **PSChildName** e **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="07644-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="07644-113">È possibile usare la notazione "**.**" per fare riferimento al percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="07644-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="07644-114">È possibile usare **Set-Location** per passare prima al contenitore del Registro di sistema **CurrentVersion**:</span><span class="sxs-lookup"><span data-stu-id="07644-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="07644-115">In alternativa è possibile usare la proprietà predefinita HKLM PSDrive con **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="07644-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="07644-116">È quindi possibile usare la notazione "**.**" del percorso corrente per elencare le proprietà senza specificare un percorso completo:</span><span class="sxs-lookup"><span data-stu-id="07644-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="07644-117">L'espansione del percorso funziona come nel file system, quindi da questo percorso è possibile ottenere l'elenco **ItemProperty** per **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** usando **Get-ItemProperty -Path ..\\Help**.</span><span class="sxs-lookup"><span data-stu-id="07644-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="07644-118">Recupero di una singola voce del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-118">Getting a Single Registry Entry</span></span>
<span data-ttu-id="07644-119">Per recuperare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili.</span><span class="sxs-lookup"><span data-stu-id="07644-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="07644-120">In questo esempio viene trovato il valore di **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="07644-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="07644-121">Usare **Get-ItemProperty** con il parametro **Path** per specificare il nome della chiave e il parametro **Name** per specificare il nome della voce **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="07644-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="07644-122">Questo comando restituisce le proprietà standard di Windows PowerShell oltre alla proprietà **DevicePath**.</span><span class="sxs-lookup"><span data-stu-id="07644-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="07644-123">Anche se **Get-ItemProperty** include i parametri **Filter**, **Include** ed **Exclude**, non è possibile usarli per applicare un filtro in base al nome di proprietà.</span><span class="sxs-lookup"><span data-stu-id="07644-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="07644-124">Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi, e non a voci del Registro di sistema, che sono invece proprietà di elementi.</span><span class="sxs-lookup"><span data-stu-id="07644-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="07644-125">Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="07644-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="07644-126">Per informazioni su reg.exe, digitare **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="07644-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="07644-127">al prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="07644-127">at a command prompt.</span></span> <span data-ttu-id="07644-128">Per trovare la voce DevicePath, usare reg.exe come illustrato nel comando seguente:</span><span class="sxs-lookup"><span data-stu-id="07644-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="07644-129">È anche possibile usare l'oggetto **WshShell COM** per trovare alcune voci del Registro di sistema, ma questo metodo non funziona con dati binari di grandi dimensioni o con nomi di voci del Registro di sistema che includono caratteri come "\\".</span><span class="sxs-lookup"><span data-stu-id="07644-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="07644-130">Aggiungere il nome di proprietà al percorso dell'elemento con un separatore \\:</span><span class="sxs-lookup"><span data-stu-id="07644-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="07644-131">Creazione di nuove voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-131">Creating New Registry Entries</span></span>
<span data-ttu-id="07644-132">Per aggiungere una nuova voce denominata "PowerShellPath" alla chiave **CurrentVersion**, usare **New-ItemProperty** con il percorso della chiave e il nome e il valore della voce.</span><span class="sxs-lookup"><span data-stu-id="07644-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="07644-133">Per questo esempio, verrà usato il valore della variabile **$PSHome** di Windows PowerShell, in cui è archiviato il percorso della directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="07644-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="07644-134">È possibile aggiungere la nuova voce alla chiave usando il comando seguente, che restituisce anche informazioni sulla nuova voce:</span><span class="sxs-lookup"><span data-stu-id="07644-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="07644-135">**PropertyType** deve essere il nome di un membro dell'enumerazione **Microsoft.Win32.RegistryValueKind** della tabella seguente:</span><span class="sxs-lookup"><span data-stu-id="07644-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="07644-136">Valore di PropertyType</span><span class="sxs-lookup"><span data-stu-id="07644-136">PropertyType Value</span></span>|<span data-ttu-id="07644-137">Significato</span><span class="sxs-lookup"><span data-stu-id="07644-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="07644-138">Binary</span><span class="sxs-lookup"><span data-stu-id="07644-138">Binary</span></span>|<span data-ttu-id="07644-139">Dati binari</span><span class="sxs-lookup"><span data-stu-id="07644-139">Binary data</span></span>|
|<span data-ttu-id="07644-140">DWord</span><span class="sxs-lookup"><span data-stu-id="07644-140">DWord</span></span>|<span data-ttu-id="07644-141">Numero che corrisponde a un valore UInt32 valido</span><span class="sxs-lookup"><span data-stu-id="07644-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="07644-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="07644-142">ExpandString</span></span>|<span data-ttu-id="07644-143">Stringa che può contenere variabili di ambiente espanse dinamicamente</span><span class="sxs-lookup"><span data-stu-id="07644-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="07644-144">MultiString</span><span class="sxs-lookup"><span data-stu-id="07644-144">MultiString</span></span>|<span data-ttu-id="07644-145">Stringa su più righe</span><span class="sxs-lookup"><span data-stu-id="07644-145">A multiline string</span></span>|
|<span data-ttu-id="07644-146">String</span><span class="sxs-lookup"><span data-stu-id="07644-146">String</span></span>|<span data-ttu-id="07644-147">Qualsiasi valore di stringa</span><span class="sxs-lookup"><span data-stu-id="07644-147">Any string value</span></span>|
|<span data-ttu-id="07644-148">QWord</span><span class="sxs-lookup"><span data-stu-id="07644-148">QWord</span></span>|<span data-ttu-id="07644-149">8 byte di dati binari</span><span class="sxs-lookup"><span data-stu-id="07644-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="07644-150">È possibile aggiungere una voce del Registro di sistema in più posizioni specificando una matrice di valori nel parametro **Path**:</span><span class="sxs-lookup"><span data-stu-id="07644-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="07644-151">È anche possibile sovrascrivere un valore preesistente di una voce del Registro di sistema aggiungendo il parametro **Force** a qualsiasi comando **New-ItemProperty**.</span><span class="sxs-lookup"><span data-stu-id="07644-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="07644-152">Ridenominazione delle voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-152">Renaming Registry Entries</span></span>
<span data-ttu-id="07644-153">Per rinominare la voce **PowerShellPath** in "PSHome", usare **Rename-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="07644-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="07644-154">Per visualizzare il valore rinominato, aggiungere il parametro **PassThru** al comando.</span><span class="sxs-lookup"><span data-stu-id="07644-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="07644-155">Eliminazione di voci del Registro di sistema</span><span class="sxs-lookup"><span data-stu-id="07644-155">Deleting Registry Entries</span></span>
<span data-ttu-id="07644-156">Per eliminare le voci del Registro di sistema PSHome e PowerShellPath, usare **Remove-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="07644-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
