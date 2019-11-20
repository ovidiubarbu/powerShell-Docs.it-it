---
title: Installazione di un modulo di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb82827e-fdb7-4cbf-b3d4-093e72b3ff0e
caps.latest.revision: 28
ms.openlocfilehash: 60ac4bf9089232a9fa879e835e32da53422489fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367070"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="69d26-102">Installazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d26-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="69d26-103">Dopo aver creato il modulo di PowerShell, è probabile che si voglia installare il modulo in un sistema, in modo che l'utente o altri utenti possano usarlo.</span><span class="sxs-lookup"><span data-stu-id="69d26-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="69d26-104">In generale, è costituito dalla copia dei file di modulo (ad esempio, psm1 o dell'assembly binario, del manifesto del modulo e di qualsiasi altro file associato) in una directory del computer.</span><span class="sxs-lookup"><span data-stu-id="69d26-104">Generally speaking, this consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="69d26-105">Per un progetto di dimensioni molto ridotte, può essere semplice copiare e incollare i file con Esplora risorse in un singolo computer remoto. Tuttavia, per soluzioni di dimensioni maggiori è consigliabile usare un processo di installazione più sofisticato.</span><span class="sxs-lookup"><span data-stu-id="69d26-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="69d26-106">Indipendentemente dal modo in cui si ottiene il modulo nel sistema, PowerShell può usare diverse tecniche che consentono agli utenti di trovare e usare i moduli.</span><span class="sxs-lookup"><span data-stu-id="69d26-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="69d26-107">Pertanto, il problema principale per l'installazione è garantire che PowerShell sia in grado di trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-107">Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span> <span data-ttu-id="69d26-108">Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).</span><span class="sxs-lookup"><span data-stu-id="69d26-108">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="69d26-109">Regole per l'installazione dei moduli</span><span class="sxs-lookup"><span data-stu-id="69d26-109">Rules for Installing Modules</span></span>

<span data-ttu-id="69d26-110">Le informazioni seguenti riguardano tutti i moduli, inclusi i moduli creati per uso personale, i moduli che si ottengono da altre parti e i moduli distribuiti ad altri utenti.</span><span class="sxs-lookup"><span data-stu-id="69d26-110">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="69d26-111">Installare i moduli in PSModulePath</span><span class="sxs-lookup"><span data-stu-id="69d26-111">Install Modules in PSModulePath</span></span>

<span data-ttu-id="69d26-112">Quando possibile, installare tutti i moduli in un percorso elencato nella variabile di ambiente **PSModulePath** o aggiungere il percorso del modulo al valore della variabile di ambiente **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="69d26-112">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="69d26-113">La variabile di ambiente **PSModulePath** ($ENV:P smodulepath) contiene le posizioni dei moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69d26-113">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="69d26-114">I cmdlet si basano sul valore di questa variabile di ambiente per trovare i moduli.</span><span class="sxs-lookup"><span data-stu-id="69d26-114">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="69d26-115">Per impostazione predefinita, il valore della variabile di ambiente **PSModulePath** contiene le seguenti directory dei moduli di sistema e utente, ma è possibile aggiungere e modificare il valore.</span><span class="sxs-lookup"><span data-stu-id="69d26-115">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="69d26-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="69d26-116">`$PSHome\Modules` (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="69d26-117">Questo percorso è riservato ai moduli forniti con Windows.</span><span class="sxs-lookup"><span data-stu-id="69d26-117">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="69d26-118">Non installare i moduli in questo percorso.</span><span class="sxs-lookup"><span data-stu-id="69d26-118">Do not install modules to this location.</span></span>

- <span data-ttu-id="69d26-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="69d26-119">`$Home\Documents\WindowsPowerShell\Modules` (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="69d26-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="69d26-120">`$Env:ProgramFiles\WindowsPowerShell\Modules` (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="69d26-121">Per ottenere il valore della variabile di ambiente **PSModulePath** , usare uno dei comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="69d26-121">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="69d26-122">Per aggiungere un percorso del modulo al valore del valore della variabile di ambiente **PSModulePath** , usare il seguente formato di comando.</span><span class="sxs-lookup"><span data-stu-id="69d26-122">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="69d26-123">Questo formato usa il metodo **nell'SetEnvironmentVariable** della classe **System. Environment** per apportare una modifica indipendente dalla sessione alla variabile di ambiente **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="69d26-123">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell
  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="69d26-124">Una volta aggiunto il percorso di **PSModulePath**, è necessario trasmettere un messaggio di ambiente sulla modifica.</span><span class="sxs-lookup"><span data-stu-id="69d26-124">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="69d26-125">La trasmissione della modifica consente ad altre applicazioni, ad esempio la shell, di prelevare la modifica.</span><span class="sxs-lookup"><span data-stu-id="69d26-125">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="69d26-126">Per trasmettere la modifica, fare in modo che il codice di installazione del prodotto invii un messaggio **WM_SETTINGCHANGE** con `lParam` impostato sulla stringa "Environment".</span><span class="sxs-lookup"><span data-stu-id="69d26-126">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="69d26-127">Assicurarsi di inviare il messaggio dopo l'aggiornamento del codice di installazione del modulo **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="69d26-127">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="69d26-128">Usa il nome di directory del modulo corretto</span><span class="sxs-lookup"><span data-stu-id="69d26-128">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="69d26-129">Un modulo ben formato è un modulo archiviato in una directory con lo stesso nome del nome di base di almeno un file nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-129">A well-formed module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="69d26-130">Se un modulo non è ben formato, Windows PowerShell non lo riconosce come modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-130">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="69d26-131">Il nome di base di un file è il nome senza l'estensione del nome file.</span><span class="sxs-lookup"><span data-stu-id="69d26-131">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="69d26-132">In un modulo ben formato, il nome della directory che contiene i file di modulo deve corrispondere al nome di base di almeno un file nel modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-132">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="69d26-133">Nel modulo Fabrikam di esempio, ad esempio, la directory che contiene i file di modulo è denominata "Fabrikam" e almeno un file ha il nome di base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="69d26-133">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="69d26-134">In questo caso, sia Fabrikam. psd1 che Fabrikam. dll hanno il nome di base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="69d26-134">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="69d26-135">Effetto dell'installazione non corretta</span><span class="sxs-lookup"><span data-stu-id="69d26-135">Effect of Incorrect Installation</span></span>

<span data-ttu-id="69d26-136">Se il modulo non è ben formato e la relativa posizione non è inclusa nel valore della variabile di ambiente **PSModulePath** , le funzionalità di individuazione di base di Windows PowerShell, ad esempio le seguenti, non funzionano.</span><span class="sxs-lookup"><span data-stu-id="69d26-136">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="69d26-137">La funzionalità di caricamento automatico del modulo non è in grado di importare il modulo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="69d26-137">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="69d26-138">Il parametro `ListAvailable` del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) non riesce a trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-138">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="69d26-139">Il cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) non è in grado di trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-139">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="69d26-140">Per importare il modulo, è necessario specificare il percorso completo del file del modulo radice o del file manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-140">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="69d26-141">Le funzionalità aggiuntive, come quelle riportate di seguito, non funzionano a meno che il modulo non venga importato nella sessione.</span><span class="sxs-lookup"><span data-stu-id="69d26-141">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="69d26-142">Nei moduli ben formati della variabile di ambiente **PSModulePath** , queste funzionalità funzionano anche quando il modulo non viene importato nella sessione.</span><span class="sxs-lookup"><span data-stu-id="69d26-142">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="69d26-143">Il cmdlet [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) non è in grado di trovare comandi nel modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-143">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="69d26-144">I cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) non possono aggiornare o salvare la guida per il modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-144">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="69d26-145">Il cmdlet [show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) non riesce a trovare e visualizzare i comandi nel modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-145">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="69d26-146">I comandi nel modulo non sono presenti nella finestra `Show-Command` in Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="69d26-146">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="69d26-147">Posizione in cui installare i moduli</span><span class="sxs-lookup"><span data-stu-id="69d26-147">Where to Install Modules</span></span>

<span data-ttu-id="69d26-148">Questa sezione illustra il punto in cui file system installare i moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="69d26-148">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="69d26-149">Il percorso dipende dalla modalità di utilizzo del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-149">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="69d26-150">Installazione dei moduli per un utente specifico</span><span class="sxs-lookup"><span data-stu-id="69d26-150">Installing Modules for a Specific User</span></span>

<span data-ttu-id="69d26-151">Se si crea un modulo personalizzato o si ottiene un modulo da un'altra parte, ad esempio un sito Web della community di Windows PowerShell e si vuole che il modulo sia disponibile solo per l'account utente, installare il modulo nella directory dei moduli specifici dell'utente.</span><span class="sxs-lookup"><span data-stu-id="69d26-151">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

`$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

<span data-ttu-id="69d26-152">Per impostazione predefinita, la directory dei moduli specifici dell'utente viene aggiunta al valore della variabile di ambiente **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="69d26-152">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="69d26-153">Installazione dei moduli per tutti gli utenti nei file di programma</span><span class="sxs-lookup"><span data-stu-id="69d26-153">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="69d26-154">Se si vuole che un modulo sia disponibile per tutti gli account utente nel computer, installare il modulo nel percorso dei file di programma.</span><span class="sxs-lookup"><span data-stu-id="69d26-154">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

`$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>`

> [!NOTE]
> <span data-ttu-id="69d26-155">Il percorso dei file di programma viene aggiunto per impostazione predefinita al valore della variabile di ambiente PSModulePath in Windows PowerShell 4,0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="69d26-155">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="69d26-156">Per le versioni precedenti di Windows PowerShell, è possibile creare manualmente il percorso dei file di programma ((%ProgramFiles%\WindowsPowerShell\Modules) e aggiungere questo percorso alla variabile di ambiente PSModulePath come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="69d26-156">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="69d26-157">Installazione di moduli in una directory di prodotto</span><span class="sxs-lookup"><span data-stu-id="69d26-157">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="69d26-158">Se si distribuisce il modulo ad altre parti, utilizzare il percorso predefinito dei file di programma descritto in precedenza oppure creare una sottodirectory specifica per l'azienda o per il prodotto della directory% ProgramFiles%.</span><span class="sxs-lookup"><span data-stu-id="69d26-158">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="69d26-159">Ad esempio, le tecnologie Fabrikam, una società fittizia, sta spedendo un modulo di Windows PowerShell per il proprio prodotto di gestione fabrikam.</span><span class="sxs-lookup"><span data-stu-id="69d26-159">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="69d26-160">Il programma di installazione del modulo crea una sottodirectory Modules nella sottodirectory Product Manager di Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="69d26-160">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="69d26-161">Per abilitare le funzionalità di individuazione dei moduli di Windows PowerShell per trovare il modulo Fabrikam, il programma di installazione del modulo Fabrikam aggiunge il percorso del modulo al valore della variabile di ambiente **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="69d26-161">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="69d26-162">Installazione dei moduli nella directory dei file comuni</span><span class="sxs-lookup"><span data-stu-id="69d26-162">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="69d26-163">Se un modulo viene usato da più componenti di un prodotto o da più versioni di un prodotto, installare il modulo in una sottodirectory specifica del modulo della sottodirectory%programmi%\Common Files\Modules</span><span class="sxs-lookup"><span data-stu-id="69d26-163">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="69d26-164">Nell'esempio seguente il modulo Fabrikam viene installato in una sottodirectory Fabrikam della sottodirectory `%ProgramFiles%\Common Files\Modules`.</span><span class="sxs-lookup"><span data-stu-id="69d26-164">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the `%ProgramFiles%\Common Files\Modules` subdirectory.</span></span> <span data-ttu-id="69d26-165">Si noti che ogni modulo risiede nella propria sottodirectory nella sottodirectory modules.</span><span class="sxs-lookup"><span data-stu-id="69d26-165">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)
```

<span data-ttu-id="69d26-166">Quindi, il programma di installazione garantisce che il valore della variabile di ambiente **PSModulePath** includa il percorso della sottodirectory dei moduli di file comuni.</span><span class="sxs-lookup"><span data-stu-id="69d26-166">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

```powershell
$m = $env:ProgramFiles + '\Common Files\Modules'
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$q = $p -split ';'
if ($q -notContains $m) {
    $q += ";$m"
}
$p = $q -join ';'
[Environment]::SetEnvironmentVariable("PSModulePath", $p)
```

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="69d26-167">Installazione di più versioni di un modulo</span><span class="sxs-lookup"><span data-stu-id="69d26-167">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="69d26-168">Per installare più versioni dello stesso modulo, attenersi alla procedura riportata di seguito.</span><span class="sxs-lookup"><span data-stu-id="69d26-168">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="69d26-169">Creare una directory per ogni versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-169">Create a directory for each version of the module.</span></span> <span data-ttu-id="69d26-170">Includere il numero di versione nel nome della directory.</span><span class="sxs-lookup"><span data-stu-id="69d26-170">Include the version number in the directory name.</span></span>
2. <span data-ttu-id="69d26-171">Creare un manifesto del modulo per ogni versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-171">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="69d26-172">Nel valore della chiave **ModuleVersion** nel manifesto, immettere il numero di versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-172">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="69d26-173">Salvare il file manifesto (con estensione psd1) nella directory specifica della versione per il modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-173">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>
3. <span data-ttu-id="69d26-174">Aggiungere il percorso della cartella radice del modulo al valore della variabile di ambiente **PSModulePath** , come illustrato negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="69d26-174">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="69d26-175">Per importare una versione specifica del modulo, l'utente finale può usare i parametri `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="69d26-175">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="69d26-176">Se, ad esempio, il modulo Fabrikam è disponibile nelle versioni 8,0 e 9,0, la struttura di directory del modulo Fabrikam potrebbe essere simile alla seguente.</span><span class="sxs-lookup"><span data-stu-id="69d26-176">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

 ```
C:\Program Files
Fabrikam Manager
  Fabrikam8
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "8.0")
      Fabrikam.dll (module assembly)
  Fabrikam9
    Fabrikam
      Fabrikam.psd1 (module manifest: ModuleVersion = "9.0")
      Fabrikam.dll (module assembly)
```

<span data-ttu-id="69d26-177">Il programma di installazione aggiunge entrambi i percorsi del modulo al valore della variabile di ambiente **PSModulePath** .</span><span class="sxs-lookup"><span data-stu-id="69d26-177">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="69d26-178">Una volta completati questi passaggi, il parametro **ListAvailable** del cmdlet [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) ottiene entrambi i moduli fabrikam.</span><span class="sxs-lookup"><span data-stu-id="69d26-178">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="69d26-179">Per importare un particolare modulo, usare i parametri `MinimumVersion` o `RequiredVersion` del cmdlet [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) .</span><span class="sxs-lookup"><span data-stu-id="69d26-179">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="69d26-180">Se entrambi i moduli vengono importati nella stessa sessione e i moduli contengono cmdlet con gli stessi nomi, i cmdlet importati per ultimi sono validi nella sessione.</span><span class="sxs-lookup"><span data-stu-id="69d26-180">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="69d26-181">Gestione dei conflitti di nomi di comando</span><span class="sxs-lookup"><span data-stu-id="69d26-181">Handling Command Name Conflicts</span></span>

<span data-ttu-id="69d26-182">I conflitti di nomi di comando possono verificarsi quando i comandi esportati da un modulo hanno lo stesso nome dei comandi della sessione dell'utente.</span><span class="sxs-lookup"><span data-stu-id="69d26-182">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="69d26-183">Quando una sessione contiene due comandi con lo stesso nome, Windows PowerShell esegue il tipo di comando che ha la precedenza.</span><span class="sxs-lookup"><span data-stu-id="69d26-183">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="69d26-184">Quando una sessione contiene due comandi che hanno lo stesso nome e lo stesso tipo, Windows PowerShell esegue il comando aggiunto alla sessione più di recente.</span><span class="sxs-lookup"><span data-stu-id="69d26-184">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="69d26-185">Per eseguire un comando che non viene eseguito per impostazione predefinita, gli utenti possono qualificare il nome del comando con il nome del modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-185">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="69d26-186">Se, ad esempio, la sessione contiene una funzione `Get-Date` e il cmdlet `Get-Date`, Windows PowerShell esegue la funzione per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="69d26-186">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="69d26-187">Per eseguire il cmdlet, anteporre il comando al nome del modulo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="69d26-187">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="69d26-188">Per evitare conflitti di nomi, gli autori di moduli possono usare la chiave **DefaultCommandPrefix** nel manifesto del modulo per specificare un prefisso sostantivo per tutti i comandi esportati dal modulo.</span><span class="sxs-lookup"><span data-stu-id="69d26-188">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="69d26-189">Gli utenti possono usare il parametro **Prefix** del cmdlet `Import-Module` per usare un prefisso alternativo.</span><span class="sxs-lookup"><span data-stu-id="69d26-189">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="69d26-190">Il valore del parametro **Prefix** ha la precedenza sul valore della chiave **DefaultCommandPrefix** .</span><span class="sxs-lookup"><span data-stu-id="69d26-190">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="69d26-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="69d26-191">See Also</span></span>

[<span data-ttu-id="69d26-192">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="69d26-192">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="69d26-193">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="69d26-193">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)