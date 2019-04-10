---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle unità di Windows PowerShell
ms.assetid: bd809e38-8de9-437a-a250-f30a667d11b4
ms.openlocfilehash: 9ac5136fb28b450ea6397cab2f36082c50f22e1f
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293249"
---
# <a name="managing-windows-powershell-drives"></a><span data-ttu-id="ca909-103">Gestione delle unità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca909-103">Managing Windows PowerShell Drives</span></span>

<span data-ttu-id="ca909-104">Un'*unità di Windows PowerShell* è un percorso di archivio dati a cui è possibile accedere come un'unità di file system in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-104">A *Windows PowerShell drive* is a data store location that you can access like a file system drive in Windows PowerShell.</span></span> <span data-ttu-id="ca909-105">I provider di Windows PowerShell creano automaticamente alcune unità, ad esempio le unità di file system (incluse C: e D:), le unità del Registro di sistema (HKCU: e HKLM:) e l'unità dei certificati (Cert:). È inoltre possibile creare unità di Windows PowerShell personalizzate.</span><span class="sxs-lookup"><span data-stu-id="ca909-105">The Windows PowerShell providers create some drives for you, such as the file system drives (including C: and D:), the registry drives (HKCU: and HKLM:), and the certificate drive (Cert:), and you can create your own Windows PowerShell drives.</span></span> <span data-ttu-id="ca909-106">Queste unità sono molto utili, ma sono disponibili solo all'interno di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-106">These drives are very useful, but they are available only within Windows PowerShell.</span></span> <span data-ttu-id="ca909-107">Non è possibile accedervi con altri strumenti di Windows, ad esempio Esplora file o Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="ca909-107">You cannot access them by using other Windows tools, such as File Explorer or Cmd.exe.</span></span>

<span data-ttu-id="ca909-108">Windows PowerShell usa il sostantivo **PSDrive** per i comandi da usare con le unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-108">Windows PowerShell uses the noun, **PSDrive**, for commands that work with Windows PowerShell drives.</span></span> <span data-ttu-id="ca909-109">Per visualizzare un elenco delle unità di Windows PowerShell presenti nella propria sessione di Windows PowerShell, usare il cmdlet **Get-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="ca909-109">For a list of the Windows PowerShell drives in your Windows PowerShell session, use the **Get-PSDrive** cmdlet.</span></span>

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

<span data-ttu-id="ca909-110">Anche se le unità visualizzate variano in base a quelle disponibili nel sistema, l'elenco sarà simile all'output del comando **Get-PSDrive** illustrato sopra.</span><span class="sxs-lookup"><span data-stu-id="ca909-110">Although the drives in the display vary with the drives on your system, the listing will look similar to the output of the **Get-PSDrive** command shown above.</span></span>

<span data-ttu-id="ca909-111">Le unità di file system sono un sottoinsieme delle unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-111">File system drives are a subset of the Windows PowerShell drives.</span></span> <span data-ttu-id="ca909-112">È possibile identificarle dalla voce FileSystem nella colonna Provider.</span><span class="sxs-lookup"><span data-stu-id="ca909-112">You can identify the file system drives by the FileSystem entry in the Provider column.</span></span> <span data-ttu-id="ca909-113">Le unità di file system di Windows PowerShell sono supportate dal provider FileSystem.</span><span class="sxs-lookup"><span data-stu-id="ca909-113">(The file system drives in Windows PowerShell are supported by the Windows PowerShell FileSystem provider.)</span></span>

<span data-ttu-id="ca909-114">Per visualizzare la sintassi del cmdlet **Get-PSDrive**, digitare un comando **Get-Command** con il parametro **Syntax**:</span><span class="sxs-lookup"><span data-stu-id="ca909-114">To see the syntax of the **Get-PSDrive** cmdlet, type a **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

<span data-ttu-id="ca909-115">Il parametro **PSProvider** consente di visualizzare solo le unità di Windows PowerShell supportate da uno specifico provider.</span><span class="sxs-lookup"><span data-stu-id="ca909-115">The **PSProvider** parameter lets you display only the Windows PowerShell drives that are supported by a particular provider.</span></span> <span data-ttu-id="ca909-116">Ad esempio, per visualizzare solo le unità di Windows PowerShell supportate dal provider FileSystem di Windows PowerShell, digitare il comando **Get-PSDrive** con il parametro **PSProvider** e il valore **FileSystem**:</span><span class="sxs-lookup"><span data-stu-id="ca909-116">For example, to display only the Windows PowerShell drives that are supported by the Windows PowerShell FileSystem provider, type a **Get-PSDrive** command with the **PSProvider** parameter and the **FileSystem** value:</span></span>

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

<span data-ttu-id="ca909-117">Per visualizzare le unità di Windows PowerShell che rappresentano hive del Registro di sistema, usare il parametro **PSProvider** in modo da visualizzare solo le unità di Windows PowerShell supportate dal provider Registry di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ca909-117">To view the Windows PowerShell drives that represent registry hives, use the **PSProvider** parameter to display only the Windows PowerShell drives that are supported by the Windows PowerShell Registry provider:</span></span>

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

<span data-ttu-id="ca909-118">È anche possibile usare i cmdlet Location standard con le unità di Windows PowerShell:</span><span class="sxs-lookup"><span data-stu-id="ca909-118">You can also use the standard Location cmdlets with the Windows PowerShell drives:</span></span>

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a><span data-ttu-id="ca909-119">Aggiunta di nuove unità di Windows PowerShell (New-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="ca909-119">Adding New Windows PowerShell Drives (New-PSDrive)</span></span>

<span data-ttu-id="ca909-120">È possibile aggiungere unità di Windows PowerShell personalizzate tramite il comando **New-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="ca909-120">You can add your own Windows PowerShell drives by using the **New-PSDrive** command.</span></span> <span data-ttu-id="ca909-121">Per ottenere la sintassi del comando **New-PSDrive**, immettere il comando **Get-Command** con il parametro **Syntax**:</span><span class="sxs-lookup"><span data-stu-id="ca909-121">To get the syntax for the **New-PSDrive** command, enter the **Get-Command** command with the **Syntax** parameter:</span></span>

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

<span data-ttu-id="ca909-122">Per creare una nuova unità di Windows PowerShell, è necessario specificare tre parametri:</span><span class="sxs-lookup"><span data-stu-id="ca909-122">To create a new Windows PowerShell drive, you must supply three parameters:</span></span>

- <span data-ttu-id="ca909-123">Il nome dell'unità (è possibile usare qualsiasi nome valido di Windows PowerShell)</span><span class="sxs-lookup"><span data-stu-id="ca909-123">A name for the drive (you can use any valid Windows PowerShell name)</span></span>

- <span data-ttu-id="ca909-124">Il PSProvider (usare "FileSystem" per i percorsi del file system e "Registry" per i percorsi del Registro di sistema)</span><span class="sxs-lookup"><span data-stu-id="ca909-124">The PSProvider (use "FileSystem" for file system locations and "Registry" for registry locations)</span></span>

- <span data-ttu-id="ca909-125">La radice, ossia il percorso della radice della nuova unità</span><span class="sxs-lookup"><span data-stu-id="ca909-125">The root, that is, the path to the root of the new drive</span></span>

<span data-ttu-id="ca909-126">Ad esempio, è possibile creare un'unità denominata "Office" mappata alla cartella contenente le applicazioni Microsoft Office nel computer, ad esempio **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span><span class="sxs-lookup"><span data-stu-id="ca909-126">For example, you can create a drive named "Office" that is mapped to the folder that contains the Microsoft Office applications on your computer, such as **C:\\Program Files\\Microsoft Office\\OFFICE11**.</span></span> <span data-ttu-id="ca909-127">Per creare l'unità, digitare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ca909-127">To create the drive, type the following command:</span></span>

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Micr
osoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> <span data-ttu-id="ca909-128">In generale, per i percorsi non viene fatta distinzione tra maiuscole e minuscole.</span><span class="sxs-lookup"><span data-stu-id="ca909-128">In general, paths are not case-sensitive.</span></span>

<span data-ttu-id="ca909-129">È possibile fare riferimento alla nuova unità di Windows PowerShell come di consueto, ossia specificando il nome seguito da due punti (**:**).</span><span class="sxs-lookup"><span data-stu-id="ca909-129">You refer to the new Windows PowerShell drive as you do all Windows PowerShell drives -- by its name followed by a colon (**:**).</span></span>

<span data-ttu-id="ca909-130">Le unità di Windows PowerShell semplificano notevolmente molte attività.</span><span class="sxs-lookup"><span data-stu-id="ca909-130">A Windows PowerShell drive can make many tasks much simpler.</span></span> <span data-ttu-id="ca909-131">Ad esempio, alcune delle chiavi più importanti del Registro di sistema hanno percorsi estremamente lunghi, che sono complicati da accedere e difficili da ricordare.</span><span class="sxs-lookup"><span data-stu-id="ca909-131">For example, some of the most important keys in the Windows registry have extremely long paths, making them cumbersome to access and difficult to remember.</span></span> <span data-ttu-id="ca909-132">Le informazioni di configurazione critiche si trovano in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="ca909-132">Critical configuration information resides under **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span> <span data-ttu-id="ca909-133">Per visualizzare e cambiare elementi nella chiave del Registro di sistema CurrentVersion, è possibile creare un'unità di Windows PowerShell la cui radice si trova in tale chiave digitando:</span><span class="sxs-lookup"><span data-stu-id="ca909-133">To view and change items in the CurrentVersion registry key, you can create a Windows PowerShell drive that is rooted in that key by typing:</span></span>

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\W
indows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

<span data-ttu-id="ca909-134">È quindi possibile passare all'unità **cvkey:** come si farebbe per qualsiasi altra unità:</span><span class="sxs-lookup"><span data-stu-id="ca909-134">You can then change location to the **cvkey:** drive as you would any other drive:\`\`</span></span>

`PS> cd cvkey:`

<span data-ttu-id="ca909-135">oppure:</span><span class="sxs-lookup"><span data-stu-id="ca909-135">or:</span></span>

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

<span data-ttu-id="ca909-136">Il cmdlet New-PsDrive aggiunge la nuova unità solo nella sessione corrente di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-136">The New-PsDrive cmdlet adds the new drive only to the current Windows PowerShell session.</span></span> <span data-ttu-id="ca909-137">Se si chiude la finestra di Windows PowerShell, la nuova unità va persa.</span><span class="sxs-lookup"><span data-stu-id="ca909-137">If you close the Windows PowerShell window, the new drive is lost.</span></span> <span data-ttu-id="ca909-138">Per salvare un'unità di Windows PowerShell, usare il cmdlet Export-Console per esportare la sessione corrente di Windows PowerShell e quindi il parametro **PSConsoleFile** di PowerShell.exe per importarla.</span><span class="sxs-lookup"><span data-stu-id="ca909-138">To save a Windows PowerShell drive, use the Export-Console cmdlet to export the current Windows PowerShell session, and then use the PowerShell.exe **PSConsoleFile** parameter to import it.</span></span> <span data-ttu-id="ca909-139">In alternativa, aggiungere la nuova unità nel proprio profilo Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ca909-139">Or, add the new drive to your Windows PowerShell profile.</span></span>

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a><span data-ttu-id="ca909-140">Eliminazione di unità di Windows PowerShell (Remove-PSDrive)</span><span class="sxs-lookup"><span data-stu-id="ca909-140">Deleting Windows PowerShell Drives (Remove-PSDrive)</span></span>

<span data-ttu-id="ca909-141">Per eliminare unità da Windows PowerShell, è possibile usare il cmdlet **Remove-PSDrive**.</span><span class="sxs-lookup"><span data-stu-id="ca909-141">You can delete drives from Windows PowerShell by using the **Remove-PSDrive** cmdlet.</span></span> <span data-ttu-id="ca909-142">Il cmdlet **Remove-PSDrive** è facile da usare. Per eliminare una specifica unità di Windows PowerShell, è sufficiente specificare il relativo nome.</span><span class="sxs-lookup"><span data-stu-id="ca909-142">The **Remove-PSDrive** cmdlet is easy to use; to delete a specific Windows PowerShell drive, you just supply the Windows PowerShell drive name.</span></span>

<span data-ttu-id="ca909-143">Ad esempio, se è stata aggiunta l'unità **Office:** di Windows PowerShell, come illustrato nell'argomento **New-PSDrive**, è possibile eliminarla digitando:</span><span class="sxs-lookup"><span data-stu-id="ca909-143">For example, if you added the **Office:** Windows PowerShell drive, as shown in the **New-PSDrive** topic, you can delete it by typing:</span></span>

```powershell
Remove-PSDrive -Name Office
```

<span data-ttu-id="ca909-144">Per eliminare l'unità **cvkey:** di Windows PowerShell, anch'essa illustrata nell'argomento **New-PSDrive**, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="ca909-144">To delete the **cvkey:** Windows PowerShell drive, also shown in the **New-PSDrive** topic, use the following command:</span></span>

```powershell
Remove-PSDrive -Name cvkey
```

<span data-ttu-id="ca909-145">Anche se l'eliminazione di unità è un'operazione facile, non è possibile eseguirla sulle unità al momento attive.</span><span class="sxs-lookup"><span data-stu-id="ca909-145">It's easy to delete a Windows PowerShell drive, but you can't delete it while you are in the drive.</span></span> <span data-ttu-id="ca909-146">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="ca909-146">For example:</span></span>

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a><span data-ttu-id="ca909-147">Aggiunta e rimozione di unità all'esterno di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ca909-147">Adding and Removing Drives Outside Windows PowerShell</span></span>

<span data-ttu-id="ca909-148">Windows PowerShell rileva le unità di file system aggiunte o rimosse da Windows, incluse le unità di rete mappate, le unità USB collegate e le unità eliminate con il comando **net use** o con i metodi **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** di uno script WSH (Windows Script Host).</span><span class="sxs-lookup"><span data-stu-id="ca909-148">Windows PowerShell detects file system drives that are added or removed in Windows, including network drives that are mapped, USB drives that are attached, and drives that are deleted by using either the **net use** command or the **WScript.NetworkMapNetworkDrive** and **RemoveNetworkDrive** methods from a Windows Script Host (WSH) script.</span></span>