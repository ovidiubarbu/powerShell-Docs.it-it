---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione del percorso corrente
ms.openlocfilehash: 42ab56759dec882d140f813c8614e578957722b3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030193"
---
# <a name="managing-current-location"></a><span data-ttu-id="6bc40-103">Gestione del percorso corrente</span><span class="sxs-lookup"><span data-stu-id="6bc40-103">Managing Current Location</span></span>

<span data-ttu-id="6bc40-104">Nei sistemi di cartelle in Esplora file è in genere presente un percorso di lavoro specifico, ossia la cartella attualmente aperta.</span><span class="sxs-lookup"><span data-stu-id="6bc40-104">When navigating folder systems in File Explorer, you usually have a specific working location - namely, the current open folder.</span></span> <span data-ttu-id="6bc40-105">Per manipolare gli elementi della cartella, è sufficiente fare clic su di essi.</span><span class="sxs-lookup"><span data-stu-id="6bc40-105">Items in the current folder can be manipulated easily by clicking them.</span></span> <span data-ttu-id="6bc40-106">Per le interfacce della riga di comando come Cmd.exe, quando ci si trova nella stessa cartella di un determinato file è possibile accedervi specificando un nome relativamente breve, invece dell'intero percorso del file.</span><span class="sxs-lookup"><span data-stu-id="6bc40-106">For command-line interfaces such as Cmd.exe, when you are in the same folder as a particular file, you can access it by specifying a relatively short name, rather than needing to specify the entire path to the file.</span></span> <span data-ttu-id="6bc40-107">La directory corrente si chiama directory di lavoro.</span><span class="sxs-lookup"><span data-stu-id="6bc40-107">The current directory is called the working directory.</span></span>

<span data-ttu-id="6bc40-108">Windows PowerShell usa il sostantivo **Location** per fare riferimento alla directory di lavoro e implementa una famiglia di cmdlet per esaminare e manipolare questo percorso.</span><span class="sxs-lookup"><span data-stu-id="6bc40-108">Windows PowerShell uses the noun **Location** to refer to the working directory, and implements a family of cmdlets to examine and manipulate your location.</span></span>

## <a name="getting-your-current-location-get-location"></a><span data-ttu-id="6bc40-109">Recupero del percorso corrente (Get-Location)</span><span class="sxs-lookup"><span data-stu-id="6bc40-109">Getting Your Current Location (Get-Location)</span></span>

<span data-ttu-id="6bc40-110">Per determinare il percorso della directory corrente, immettere il comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6bc40-110">To determine the path of your current directory location, enter the **Get-Location** command:</span></span>

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="6bc40-111">Il cmdlet Get-Location è simile al comando **pwd** della shell BASH.</span><span class="sxs-lookup"><span data-stu-id="6bc40-111">The Get-Location cmdlet is similar to the **pwd** command in the BASH shell.</span></span> <span data-ttu-id="6bc40-112">Il cmdlet Set-Location è simile al comando **cd** di Cmd.exe.</span><span class="sxs-lookup"><span data-stu-id="6bc40-112">The Set-Location cmdlet is similar to the **cd** command in Cmd.exe.</span></span>

## <a name="setting-your-current-location-set-location"></a><span data-ttu-id="6bc40-113">Impostazione del percorso corrente (Set-Location)</span><span class="sxs-lookup"><span data-stu-id="6bc40-113">Setting Your Current Location (Set-Location)</span></span>

<span data-ttu-id="6bc40-114">Il comando **Get-Location** viene usato con il comando **Set-Location**.</span><span class="sxs-lookup"><span data-stu-id="6bc40-114">The **Get-Location** command is used with the **Set-Location** command.</span></span> <span data-ttu-id="6bc40-115">Il comando **Set-Location** consente di specificare il percorso della directory corrente.</span><span class="sxs-lookup"><span data-stu-id="6bc40-115">The **Set-Location** command allows you to specify your current directory location.</span></span>

```powershell
Set-Location -Path C:\Windows
```

<span data-ttu-id="6bc40-116">Dopo aver immesso il comando non si riceve nessun feedback diretto sul relativo effetto.</span><span class="sxs-lookup"><span data-stu-id="6bc40-116">After you enter the command, you will notice that you do not receive any direct feedback about the effect of the command.</span></span> <span data-ttu-id="6bc40-117">La maggior parte dei comandi di Windows PowerShell che esegue un'azione produce un output nullo o irrilevante, perché non è sempre utile riceverlo.</span><span class="sxs-lookup"><span data-stu-id="6bc40-117">Most Windows PowerShell commands that perform an action produce little or no output because the output is not always useful.</span></span> <span data-ttu-id="6bc40-118">Per verificare se il cambio di directory è stato completato correttamente quando si immette il comando **Set-Location**, includere il parametro **-PassThru** insieme al comando **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="6bc40-118">To verify that a successful directory change has occurred when you enter the **Set-Location** command, include the **-PassThru** parameter when you enter the **Set-Location** command:</span></span>

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

<span data-ttu-id="6bc40-119">Il parametro **-PassThru** può essere usato con molti comandi Set in Windows PowerShell per restituire informazioni sul risultato nei casi in cui non ci sia un output predefinito.</span><span class="sxs-lookup"><span data-stu-id="6bc40-119">The **-PassThru** parameter can be used with many Set commands in Windows PowerShell to return information about the result in cases in which there is no default output.</span></span>

<span data-ttu-id="6bc40-120">È possibile specificare percorsi relativi al percorso corrente con la stessa procedura richiesta dalla maggior parte delle shell di comandi di UNIX e Windows.</span><span class="sxs-lookup"><span data-stu-id="6bc40-120">You can specify paths relative to your current location in the same way as you would in most UNIX and Windows command shells.</span></span> <span data-ttu-id="6bc40-121">Nella notazione standard dei percorsi relativi un punto ( **.** ) rappresenta la cartella corrente e un doppio punto ( **..** ) rappresenta la directory padre del percorso corrente.</span><span class="sxs-lookup"><span data-stu-id="6bc40-121">In standard notation for relative paths, a period (**.**)represents your current folder, and a doubled period (**..**) represents the parent directory of your current location.</span></span>

<span data-ttu-id="6bc40-122">Ad esempio, nel percorso della cartella **C:\\Windows** un punto ( **.** ) rappresenta **C:\\Windows** e un doppio punto ( **..** ) rappresenta **C:** .</span><span class="sxs-lookup"><span data-stu-id="6bc40-122">For example, if you are in the **C:\\Windows** folder, a period (**.**)represents **C:\\Windows** and double periods (**..**) represent **C:**.</span></span> <span data-ttu-id="6bc40-123">Per passare dal percorso corrente alla radice dell'unità C:, digitare:</span><span class="sxs-lookup"><span data-stu-id="6bc40-123">You can change from your current location to the root of the C: drive by typing:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

<span data-ttu-id="6bc40-124">La stessa tecnica funziona nelle unità di Windows PowerShell diverse dalle unità di file system, ad esempio **HKLM:** .</span><span class="sxs-lookup"><span data-stu-id="6bc40-124">The same technique works on Windows PowerShell drives that are not file system drives, such as **HKLM:**.</span></span> <span data-ttu-id="6bc40-125">Per impostare il percorso sulla chiave \\Software nel Registro di sistema, digitare:</span><span class="sxs-lookup"><span data-stu-id="6bc40-125">You can set your location to the HKLM\\Software key in the registry by typing:</span></span>

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

<span data-ttu-id="6bc40-126">È quindi possibile impostare il percorso sulla directory padre, che è la radice dell'unità HKLM: di Windows PowerShell usando un percorso relativo:</span><span class="sxs-lookup"><span data-stu-id="6bc40-126">You can then change the directory location to the parent directory, which is the root of the Windows PowerShell HKLM: drive, by using a relative path:</span></span>

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

<span data-ttu-id="6bc40-127">È possibile digitare Set-Location o usare uno degli alias predefiniti di Windows PowerShell per Set-Location (cd, chdir, sl).</span><span class="sxs-lookup"><span data-stu-id="6bc40-127">You can type Set-Location or use any of the built-in Windows PowerShell aliases for Set-Location (cd, chdir, sl).</span></span> <span data-ttu-id="6bc40-128">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="6bc40-128">For example:</span></span>

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a><span data-ttu-id="6bc40-129">Salvataggio e richiamo dei percorsi recenti (Push-Location e Pop-Location)</span><span class="sxs-lookup"><span data-stu-id="6bc40-129">Saving and Recalling Recent Locations (Push-Location and Pop-Location)</span></span>

<span data-ttu-id="6bc40-130">Quando si cambia percorso, risulta utile tenere traccia del percorso precedente e avere la possibilità di tornarci.</span><span class="sxs-lookup"><span data-stu-id="6bc40-130">When changing locations, it is helpful to keep track of where you have been and to be able to return to your previous location.</span></span> <span data-ttu-id="6bc40-131">Il cmdlet **Push-Location** di Windows PowerShell crea una cronologia ordinata ("stack") dei percorsi di directory visitati ed è possibile risalire in questa cronologia usando il cmdlet complementare **Pop-Location**.</span><span class="sxs-lookup"><span data-stu-id="6bc40-131">The **Push-Location** cmdlet in Windows PowerShell creates a ordered history (a "stack") of directory paths where you have been, and you can step back through the history of directory paths by using the complementary **Pop-Location** cmdlet.</span></span>

<span data-ttu-id="6bc40-132">Ad esempio, Windows PowerShell viene in genere avviato nella home directory dell'utente.</span><span class="sxs-lookup"><span data-stu-id="6bc40-132">For example, Windows PowerShell typically starts in the user's home directory.</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> <span data-ttu-id="6bc40-133">Il termine *stack* ha un significato speciale in molte impostazioni di programmazione, tra cui .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6bc40-133">The word *stack* has a special meaning in many programming settings, including .NET Framework.</span></span> <span data-ttu-id="6bc40-134">L'ultimo elemento inserito nello stack è il primo che è possibile prelevare.</span><span class="sxs-lookup"><span data-stu-id="6bc40-134">Like a physical stack of items, the last item you put onto the stack is the first item that you can pull off the stack.</span></span> <span data-ttu-id="6bc40-135">L'aggiunta di un elemento allo stack si definisce normalmente con il termine "push".</span><span class="sxs-lookup"><span data-stu-id="6bc40-135">Adding an item to a stack is colloquially known as "pushing" the item onto the stack.</span></span> <span data-ttu-id="6bc40-136">Il prelievo di un elemento dallo stack è invece noto come operazione "pop".</span><span class="sxs-lookup"><span data-stu-id="6bc40-136">Pulling an item off the stack is colloquially known as "popping" the item off the stack.</span></span>

<span data-ttu-id="6bc40-137">Per effettuare il push del percorso corrente nello stack e quindi passare alla cartella Local Settings, digitare:</span><span class="sxs-lookup"><span data-stu-id="6bc40-137">To push the current location onto the stack, and then move to the Local Settings folder, type:</span></span>

```powershell
Push-Location -Path "Local Settings"
```

<span data-ttu-id="6bc40-138">È quindi possibile effettuare il push del percorso Local Settings nello stack e passare alla cartella Temp digitando:</span><span class="sxs-lookup"><span data-stu-id="6bc40-138">You can then push the Local Settings location onto the stack and move to the Temp folder by typing:</span></span>

```powershell
Push-Location -Path Temp
```

<span data-ttu-id="6bc40-139">Per verificare se il cambio di directory è stato effettuato, immettere il comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6bc40-139">You can verify that you changed directories by entering the **Get-Location** command:</span></span>

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

<span data-ttu-id="6bc40-140">È quindi possibile prelevare la directory visitata più di recente immettendo il comando **Pop-Location** e verificare se il cambio è stato effettuato con il comando **Get-Location**:</span><span class="sxs-lookup"><span data-stu-id="6bc40-140">You can then pop back into the most recently visited directory by entering the **Pop-Location** command, and verify the change by entering the **Get-Location** command:</span></span>

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

<span data-ttu-id="6bc40-141">Come per il cmdlet **Set-Location**, è possibile includere il parametro **-PassThru** quando si immette il cmdlet **Pop-Location** per visualizzare la directory a cui si è passati:</span><span class="sxs-lookup"><span data-stu-id="6bc40-141">Just as with the **Set-Location** cmdlet, you can include the **-PassThru** parameter when you enter the **Pop-Location** cmdlet to display the directory that you entered:</span></span>

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

<span data-ttu-id="6bc40-142">È possibile usare i cmdlet Location anche con i percorsi di rete.</span><span class="sxs-lookup"><span data-stu-id="6bc40-142">You can also use the Location cmdlets with network paths.</span></span> <span data-ttu-id="6bc40-143">Se si ha un server denominato FS01 con una condivisione denominata Public, è possibile cambiare percorso digitando</span><span class="sxs-lookup"><span data-stu-id="6bc40-143">If you have a server named FS01 with an share named Public, you can change your location by typing</span></span>

```powershell
Set-Location \\FS01\Public
```

<span data-ttu-id="6bc40-144">o</span><span class="sxs-lookup"><span data-stu-id="6bc40-144">or</span></span>

```powershell
Push-Location \\FS01\Public
```

<span data-ttu-id="6bc40-145">È possibile usare i comandi **Push-Location** e **Set-Location** per passare a una delle unità disponibili.</span><span class="sxs-lookup"><span data-stu-id="6bc40-145">You can use the **Push-Location** and **Set-Location** commands to change the location to any available drive.</span></span> <span data-ttu-id="6bc40-146">Ad esempio, se si ha un'unità CD-ROM locale con la lettera di unità D che contiene un CD dati, è possibile passare all'unità CD immettendo il comando **Set-Location D:** .</span><span class="sxs-lookup"><span data-stu-id="6bc40-146">For example, if you have a local CD-ROM drive with drive letter D that contains a data CD, you can change the location to the CD drive by entering the **Set-Location D:** command.</span></span>

<span data-ttu-id="6bc40-147">Se l'unità è vuota, verrà visualizzato il messaggio di errore seguente:</span><span class="sxs-lookup"><span data-stu-id="6bc40-147">If the drive is empty, you will get the following error message:</span></span>

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

<span data-ttu-id="6bc40-148">Se si usa un'interfaccia della riga di comando, non è consigliabile usare Esplora file per esaminare le unità fisiche disponibili.</span><span class="sxs-lookup"><span data-stu-id="6bc40-148">When you are using a command-line interface, it is not convenient to use File Explorer to examine the available physical drives.</span></span> <span data-ttu-id="6bc40-149">Inoltre, Esplora file non visualizza tutte le unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6bc40-149">Also, File Explorer would not show you the all of the Windows PowerShell drives.</span></span> <span data-ttu-id="6bc40-150">Windows PowerShell prevede un set di comandi per manipolare le unità di Windows PowerShell, che verranno descritti in seguito.</span><span class="sxs-lookup"><span data-stu-id="6bc40-150">Windows PowerShell provides a set of commands for manipulating Windows PowerShell drives, and we will talk about these next.</span></span>
