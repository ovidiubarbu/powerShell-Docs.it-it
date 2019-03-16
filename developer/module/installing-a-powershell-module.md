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
ms.openlocfilehash: 7c2bfca50de4645676eafc01bbf23d9797e8b758
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059780"
---
# <a name="installing-a-powershell-module"></a><span data-ttu-id="4e046-102">Installazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e046-102">Installing a PowerShell Module</span></span>

<span data-ttu-id="4e046-103">Dopo aver creato il modulo di PowerShell, è opportuno installare il modulo in un sistema, in modo che può essere utilizzata o da altri.</span><span class="sxs-lookup"><span data-stu-id="4e046-103">After you have created your PowerShell module, you will likely want to install the module on a system, so that you or others may use it.</span></span> <span data-ttu-id="4e046-104">In generale, si tratta semplicemente di Sto copiando il modulo (Internet Explorer, psm1, o l'assieme binario, il manifesto del modulo e tutti gli altri file associati) in una directory in tale computer.</span><span class="sxs-lookup"><span data-stu-id="4e046-104">Generally speaking, this simply consists of copying the module files (ie, the .psm1, or the binary assembly, the module manifest, and any other associated files) onto a directory on that computer.</span></span> <span data-ttu-id="4e046-105">Per un progetto molto piccolo, potrebbe essere semplice come copiare e incollare i file con Windows Explorer in un singolo computer remoto. Tuttavia, per soluzioni di maggiori dimensioni si consiglia di usare un processo di installazione più sofisticato.</span><span class="sxs-lookup"><span data-stu-id="4e046-105">For a very small project, this may be as simple as copying and pasting the files with Windows Explorer onto a single remote computer; however, for larger solutions you may wish to use a more sophisticated installation process.</span></span> <span data-ttu-id="4e046-106">Indipendentemente dal modo in cui viene visualizzato un modulo di sistema, PowerShell può utilizzare una serie di tecniche che permettono agli utenti di trovare e usare i moduli.</span><span class="sxs-lookup"><span data-stu-id="4e046-106">Regardless of how you get your module onto the system, PowerShell can use a number of techniques that will let users find and use your modules.</span></span> <span data-ttu-id="4e046-107">(Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md).) Pertanto, il problema principale per l'installazione consiste nel garantire che PowerShell sarà in grado di trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-107">(For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md).) Therefore, the main issue for installation is ensuring that PowerShell will be able to find your module.</span></span>

<span data-ttu-id="4e046-108">Questo argomento include le sezioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="4e046-108">This topic contains the following sections:</span></span>

- <span data-ttu-id="4e046-109">Regole per l'installazione dei moduli</span><span class="sxs-lookup"><span data-stu-id="4e046-109">Rules for Installing Modules</span></span>

- <span data-ttu-id="4e046-110">Percorso in cui installare i moduli</span><span class="sxs-lookup"><span data-stu-id="4e046-110">Where to Install Modules</span></span>

- <span data-ttu-id="4e046-111">Installazione di più versioni di un modulo</span><span class="sxs-lookup"><span data-stu-id="4e046-111">Installing Multiple Versions of a Module</span></span>

- <span data-ttu-id="4e046-112">Conflitti di nomi di comando di gestione</span><span class="sxs-lookup"><span data-stu-id="4e046-112">Handling Command Name Conflicts</span></span>

## <a name="rules-for-installing-modules"></a><span data-ttu-id="4e046-113">Regole per l'installazione dei moduli</span><span class="sxs-lookup"><span data-stu-id="4e046-113">Rules for Installing Modules</span></span>

<span data-ttu-id="4e046-114">Le informazioni seguenti si riferiscono a tutti i moduli, tra cui moduli che si creano per il proprio utilizzo, i moduli che si ottengono da altre parti e i moduli distribuiti agli altri utenti.</span><span class="sxs-lookup"><span data-stu-id="4e046-114">The following information pertains to all modules, including modules that you create for your own use, modules that you get from other parties, and modules that you distribute to others.</span></span>

### <a name="install-modules-in-psmodulepath"></a><span data-ttu-id="4e046-115">Installare i moduli in PSModulePath</span><span class="sxs-lookup"><span data-stu-id="4e046-115">Install Modules in PSModulePath</span></span>

<span data-ttu-id="4e046-116">Quando possibile, installare tutti i moduli in un percorso elencato nella **PSModulePath** variabile di ambiente o aggiungere il percorso del modulo per il **PSModulePath** valore variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="4e046-116">Whenever possible, install all modules in a path that is listed in the **PSModulePath** environment variable or add the module path to the **PSModulePath** environment variable value.</span></span>

<span data-ttu-id="4e046-117">Il **PSModulePath** variabile di ambiente ($Env: PSModulePath) contiene i percorsi dei moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e046-117">The **PSModulePath** environment variable ($Env:PSModulePath) contains the locations of Windows PowerShell modules.</span></span> <span data-ttu-id="4e046-118">I cmdlet si basano sul valore di questa variabile di ambiente per trovare i moduli.</span><span class="sxs-lookup"><span data-stu-id="4e046-118">Cmdlets rely on the value of this environment variable to find modules.</span></span>

<span data-ttu-id="4e046-119">Per impostazione predefinita, il **PSModulePath** valore variabile ambiente contiene il sistema seguente e le directory modulo utente, ma è possibile aggiungere e modificare il valore.</span><span class="sxs-lookup"><span data-stu-id="4e046-119">By default, the **PSModulePath** environment variable value contains the following system and user module directories, but you can add to and edit the value.</span></span>

- <span data-ttu-id="4e046-120">$PSHome\Modules (% Windir%\System32\WindowsPowerShell\v1.0\Modules)</span><span class="sxs-lookup"><span data-stu-id="4e046-120">$PSHome\Modules (%Windir%\System32\WindowsPowerShell\v1.0\Modules)</span></span>

  > [!WARNING]
  > <span data-ttu-id="4e046-121">Questo percorso è riservato per i moduli forniti con Windows.</span><span class="sxs-lookup"><span data-stu-id="4e046-121">This location is reserved for modules that ship with Windows.</span></span> <span data-ttu-id="4e046-122">È necessario installare i moduli in questo percorso.</span><span class="sxs-lookup"><span data-stu-id="4e046-122">Do not install modules to this location.</span></span>

- <span data-ttu-id="4e046-123">$Home\Documents\WindowsPowerShell\Modules (% UserProfile%\Documents\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4e046-123">$Home\Documents\WindowsPowerShell\Modules (%UserProfile%\Documents\WindowsPowerShell\Modules)</span></span>

- <span data-ttu-id="4e046-124">$Env: ProgramFiles\WindowsPowerShell\Modules (% ProgramFiles%\WindowsPowerShell\Modules)</span><span class="sxs-lookup"><span data-stu-id="4e046-124">$Env:ProgramFiles\WindowsPowerShell\Modules (%ProgramFiles%\WindowsPowerShell\Modules)</span></span>

  <span data-ttu-id="4e046-125">Per ottenere il valore della **PSModulePath** variabile di ambiente, usare uno dei comandi seguenti.</span><span class="sxs-lookup"><span data-stu-id="4e046-125">To get the value of the **PSModulePath** environment variable, use either of the following commands.</span></span>

  ```powershell
  $Env:PSModulePath
  [Environment]::GetEnvironmentVariable("PSModulePath")
  ```

  <span data-ttu-id="4e046-126">Per aggiungere un percorso del modulo al valore di **PSModulePath** variabile di ambiente valore, utilizzare il comando nel formato seguente.</span><span class="sxs-lookup"><span data-stu-id="4e046-126">To add a module path to value of the **PSModulePath** environment variable value, use the following command format.</span></span> <span data-ttu-id="4e046-127">Questo formato utilizza il **SetEnvironmentVariable** metodo del **System. Environment** classe apportare una modifica di sessione indipendente per il **PSModulePath** ambiente variabile.</span><span class="sxs-lookup"><span data-stu-id="4e046-127">This format uses the **SetEnvironmentVariable** method of the **System.Environment** class to make a session-independent change to the **PSModulePath** environment variable.</span></span>

  ```powershell

  #Save the current value in the $p variable.
  $p = [Environment]::GetEnvironmentVariable("PSModulePath")

  #Add the new path to the $p variable. Begin with a semi-colon separator.
  $p += ";C:\Program Files (x86)\MyCompany\Modules\"

  #Add the paths in $p to the PSModulePath value.
  [Environment]::SetEnvironmentVariable("PSModulePath",$p)

  ```

  > [!IMPORTANT]
  > <span data-ttu-id="4e046-128">Dopo aver aggiunto il percorso **PSModulePath**, si deve trasmettere un messaggio di ambiente sulla modifica.</span><span class="sxs-lookup"><span data-stu-id="4e046-128">Once you have added the path to **PSModulePath**, you should broadcast an environment message about the change.</span></span> <span data-ttu-id="4e046-129">La modifica di trasmissione consente ad altre applicazioni, come la shell, rilevi la modifica.</span><span class="sxs-lookup"><span data-stu-id="4e046-129">Broadcasting the change allows other applications, such as the shell, to pick up the change.</span></span> <span data-ttu-id="4e046-130">Per trasmettere la modifica, che il codice di installazione del prodotto invii un **WM_SETTINGCHANGE** dei messaggi con `lParam` impostato sulla stringa "Ambiente".</span><span class="sxs-lookup"><span data-stu-id="4e046-130">To broadcast the change, have your product installation code send a **WM_SETTINGCHANGE** message with `lParam` set to the string "Environment".</span></span> <span data-ttu-id="4e046-131">Assicurarsi di inviare il messaggio dopo che il codice di installazione del modulo è aggiornati **PSModulePath**.</span><span class="sxs-lookup"><span data-stu-id="4e046-131">Be sure to send the message after your module installation code has updated **PSModulePath**.</span></span>

### <a name="use-the-correct-module-directory-name"></a><span data-ttu-id="4e046-132">Usare il nome di Directory di modulo corretto</span><span class="sxs-lookup"><span data-stu-id="4e046-132">Use the Correct Module Directory Name</span></span>

<span data-ttu-id="4e046-133">Un "corretto" è un modulo che viene archiviato in una directory che ha lo stesso nome come nome di base di almeno un file nella directory del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-133">A "well-formed" module is a module that is stored in a directory that has the same name as the base name of at least one file in the module directory.</span></span> <span data-ttu-id="4e046-134">Se un modulo non è corretto, Windows PowerShell non riconosce lo come modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-134">If a module is not well-formed, Windows PowerShell does not recognize it as a module.</span></span>

<span data-ttu-id="4e046-135">Il nome"base" di un file è il nome senza l'estensione del nome file.</span><span class="sxs-lookup"><span data-stu-id="4e046-135">The "base name" of a file is the name without the file name extension.</span></span> <span data-ttu-id="4e046-136">In un modulo in formato corretto, il nome della directory che contiene i file di modulo deve corrispondere al nome di base di almeno un file nel modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-136">In a well-formed module, the name of the directory that contains the module files must match the base name of at least one file in the module.</span></span>

<span data-ttu-id="4e046-137">Ad esempio, nel modulo esempio Fabrikam, la directory che contiene i file di modulo è denominata "Fabrikam" e almeno un file con il nome di base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="4e046-137">For example, in the sample Fabrikam module, the directory that contains the module files is named "Fabrikam" and at least one file has the "Fabrikam" base name.</span></span> <span data-ttu-id="4e046-138">In questo caso sia Fabrikam.psd1 Fabrikam.dll hanno il nome di base "Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="4e046-138">In this case, both Fabrikam.psd1 and Fabrikam.dll have the "Fabrikam" base name.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

### <a name="effect-of-incorrect-installation"></a><span data-ttu-id="4e046-139">Effetto dell'installazione non corretta</span><span class="sxs-lookup"><span data-stu-id="4e046-139">Effect of Incorrect Installation</span></span>

<span data-ttu-id="4e046-140">Se il modulo non è ben formato e il percorso non è incluso nel valore della **PSModulePath** variabile di ambiente, le funzionalità di individuazione di base di Windows PowerShell, ad esempio il comando seguente, non funzionano.</span><span class="sxs-lookup"><span data-stu-id="4e046-140">If the module is not well-formed and its location is not included in the value of the **PSModulePath** environment variable, basic discovery features of Windows PowerShell, such as the following, do not work.</span></span>

- <span data-ttu-id="4e046-141">La funzionalità di modulo Auto-caricamento non è possibile importare il modulo automaticamente.</span><span class="sxs-lookup"><span data-stu-id="4e046-141">The Module Auto-Loading feature cannot import the module automatically.</span></span>

- <span data-ttu-id="4e046-142">Il `ListAvailable` parametro il [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet non è possibile trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-142">The `ListAvailable` parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet cannot find the module.</span></span>

- <span data-ttu-id="4e046-143">Il [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet non è possibile trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-143">The [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet cannot find the module.</span></span> <span data-ttu-id="4e046-144">Per importare il modulo, è necessario specificare il percorso completo del file di modulo radice o di un file manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-144">To import the module, you must provide the full path to the root module file or module manifest file.</span></span>

  <span data-ttu-id="4e046-145">Funzionalità aggiuntive, ad esempio il comando seguente, non funzionano a meno che non viene importato il modulo nella sessione.</span><span class="sxs-lookup"><span data-stu-id="4e046-145">Additional features, such as the following, do not work unless the module is imported into the session.</span></span> <span data-ttu-id="4e046-146">Nei moduli in formato corretto nel **PSModulePath** variabile di ambiente, queste funzionalità a funzionare anche quando il modulo non viene importato nella sessione.</span><span class="sxs-lookup"><span data-stu-id="4e046-146">In well-formed modules in the **PSModulePath** environment variable, these features work even when the module is not imported into the session.</span></span>

- <span data-ttu-id="4e046-147">Il [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet non è possibile trovare i comandi del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-147">The [Get-Command](/powershell/module/Microsoft.PowerShell.Core/Get-Command) cmdlet cannot find commands in the module.</span></span>

- <span data-ttu-id="4e046-148">Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet non può aggiornare o salvare la Guida per il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-148">The [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) and [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlets cannot update or save help for the module.</span></span>

- <span data-ttu-id="4e046-149">Il [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet non è possibile trovare e visualizzare i comandi nel modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-149">The [Show-Command](/powershell/module/Microsoft.PowerShell.Utility/Show-Command) cmdlet cannot find and display the commands in the module.</span></span>

  <span data-ttu-id="4e046-150">I comandi del modulo non sono presenti il `Show-Command` finestra in Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="4e046-150">The commands in the module are missing from the `Show-Command` window in Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="where-to-install-modules"></a><span data-ttu-id="4e046-151">Percorso in cui installare i moduli</span><span class="sxs-lookup"><span data-stu-id="4e046-151">Where to Install Modules</span></span>

<span data-ttu-id="4e046-152">Questa sezione descrive la posizione nel file system per installare i moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4e046-152">This section explains where in the file system to install Windows PowerShell modules.</span></span> <span data-ttu-id="4e046-153">Il percorso dipende dal modo in cui viene usato il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-153">The location depends on how the module is used.</span></span>

### <a name="installing-modules-for-a-specific-user"></a><span data-ttu-id="4e046-154">Installazione dei moduli per un utente specifico</span><span class="sxs-lookup"><span data-stu-id="4e046-154">Installing Modules for a Specific User</span></span>

<span data-ttu-id="4e046-155">Se si crea un modulo personalizzato o ottiene un modulo da un'altra entità, ad esempio un sito Web della community di Windows PowerShell, e si vuole che il modulo sia disponibile per l'account utente solo, installare il modulo nella directory di moduli specifici dell'utente.</span><span class="sxs-lookup"><span data-stu-id="4e046-155">If you create your own module or get a module from another party, such as a Windows PowerShell community website, and you want the module to be available for your user account only, install the module in your user-specific Modules directory.</span></span>

```
$home\Documents\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

<span data-ttu-id="4e046-156">Directory dei moduli specifici dell'utente viene aggiunto al valore della **PSModulePath** variabile di ambiente per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4e046-156">The user-specific Modules directory is added to the value of the **PSModulePath** environment variable by default.</span></span>

### <a name="installing-modules-for-all-users-in-program-files"></a><span data-ttu-id="4e046-157">Installazione dei moduli per tutti gli utenti nei file di programma</span><span class="sxs-lookup"><span data-stu-id="4e046-157">Installing Modules for all Users in Program Files</span></span>

<span data-ttu-id="4e046-158">Se si desidera che un modulo sia disponibile per tutti gli account utente nel computer, installare il modulo nel percorso di file di programma.</span><span class="sxs-lookup"><span data-stu-id="4e046-158">If you want a module to be available to all user accounts on the computer, install the module in the Program Files location.</span></span>

```
$Env:ProgramFiles\WindowsPowerShell\Modules\<Module Folder>\<Module Files>
```

> [!NOTE]
> <span data-ttu-id="4e046-159">Per impostazione predefinita in Windows PowerShell 4.0 e versioni successive, il percorso di file di programma viene aggiunto al valore della variabile di ambiente PSModulePath.</span><span class="sxs-lookup"><span data-stu-id="4e046-159">The Program Files location is added to the value of the PSModulePath environment variable by default in Windows PowerShell 4.0 and later.</span></span> <span data-ttu-id="4e046-160">Per le versioni precedenti di Windows PowerShell, è possibile creare ((%ProgramFiles%\WindowsPowerShell\Modules) il percorso file di programma manualmente e Aggiungi il percorso alla variabile di ambiente PSModulePath, come descritto in precedenza.</span><span class="sxs-lookup"><span data-stu-id="4e046-160">For earlier versions of Windows PowerShell, you can manually create the Program Files location ((%ProgramFiles%\WindowsPowerShell\Modules) and add this path to your PSModulePath environment variable as described above.</span></span>

### <a name="installing-modules-in-a-product-directory"></a><span data-ttu-id="4e046-161">Installazione dei moduli in una Directory di prodotto</span><span class="sxs-lookup"><span data-stu-id="4e046-161">Installing Modules in a Product Directory</span></span>

<span data-ttu-id="4e046-162">Se si prevede di distribuire il modulo ad altri soggetti, usare il percorso di file del programma predefinito descritto in precedenza oppure creare proprie sottodirectory specifiche della società o specifici del prodotto della directory % ProgramFiles %.</span><span class="sxs-lookup"><span data-stu-id="4e046-162">If you are distributing the module to other parties, use the default Program Files location described above, or create your own company-specific or product-specific subdirectory of the %ProgramFiles% directory.</span></span>

<span data-ttu-id="4e046-163">Tecnologie di Fabrikam, una società fittizia, ad esempio, è destinato ad un modulo di Windows PowerShell per il prodotto di gestione Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="4e046-163">For example, Fabrikam Technologies, a fictitious company, is shipping a Windows PowerShell module for their Fabrikam Manager product.</span></span> <span data-ttu-id="4e046-164">Il programma di installazione del modulo viene creata una sottodirectory di moduli nella sottodirectory product Manager di Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="4e046-164">Their module installer creates a Modules subdirectory in the Fabrikam Manager product subdirectory.</span></span>

```
C:\Program Files
  Fabrikam Technologies
    Fabrikam Manager
      Modules
        Fabrikam
          Fabrikam.psd1 (module manifest)
          Fabrikam.dll (module assembly)

```

<span data-ttu-id="4e046-165">Per abilitare le funzionalità di individuazione del modulo Windows PowerShell trovare il modulo di Fabrikam, il programma di installazione di modulo di Fabrikam aggiunge il percorso del modulo per il valore della **PSModulePath** variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="4e046-165">To enable the Windows PowerShell module discovery features to find the Fabrikam module, the Fabrikam module installer adds the module location to the value of the **PSModulePath** environment variable.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += "C:\Program Files\Fabrikam Technologies\Fabrikam Manager\Modules\"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

### <a name="installing-modules-in-the-common-files-directory"></a><span data-ttu-id="4e046-166">Installazione dei moduli nella Directory di file comuni</span><span class="sxs-lookup"><span data-stu-id="4e046-166">Installing Modules in the Common Files Directory</span></span>

<span data-ttu-id="4e046-167">Se un modulo è utilizzato da più componenti di un prodotto o da più versioni di un prodotto, installare il modulo in una sottodirectory specifiche dei moduli della sottodirectory Files\Modules %ProgramFiles%\Common.</span><span class="sxs-lookup"><span data-stu-id="4e046-167">If a module is used by multiple components of a product or by multiple versions of a product, install the module in a module-specific subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span>

<span data-ttu-id="4e046-168">Nell'esempio seguente, in una sottodirectory di Fabrikam della sottodirectory Files\Modules %ProgramFiles%\Common è installato il modulo di Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="4e046-168">In the following example, the Fabrikam module is installed in a Fabrikam subdirectory of the %ProgramFiles%\Common Files\Modules subdirectory.</span></span> <span data-ttu-id="4e046-169">Si noti che ogni modulo si trovi in una sottodirectory nella sottodirectory moduli.</span><span class="sxs-lookup"><span data-stu-id="4e046-169">Note that each module resides in its own subdirectory in the Modules subdirectory.</span></span>

```
C:\Program Files
  Common Files
    Modules
      Fabrikam
        Fabrikam.psd1 (module manifest)
        Fabrikam.dll (module assembly)

```

<span data-ttu-id="4e046-170">Quindi, il programma di installazione verifica che il valore della **PSModulePath** variabile di ambiente include il percorso della sottodirectory moduli file comuni.</span><span class="sxs-lookup"><span data-stu-id="4e046-170">Then, the installer assures the value of the **PSModulePath** environment variable includes the path of the common files modules subdirectory.</span></span>

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

## <a name="installing-multiple-versions-of-a-module"></a><span data-ttu-id="4e046-171">Installazione di più versioni di un modulo</span><span class="sxs-lookup"><span data-stu-id="4e046-171">Installing Multiple Versions of a Module</span></span>

<span data-ttu-id="4e046-172">Per installare più versioni dello stesso modulo, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="4e046-172">To install multiple versions of the same module, use the following procedure.</span></span>

1. <span data-ttu-id="4e046-173">Creare una directory per ogni versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-173">Create a directory for each version of the module.</span></span> <span data-ttu-id="4e046-174">Includere il numero di versione nel nome della directory.</span><span class="sxs-lookup"><span data-stu-id="4e046-174">Include the version number in the directory name.</span></span>

2. <span data-ttu-id="4e046-175">Creare un manifesto del modulo per ogni versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-175">Create a module manifest for each version of the module.</span></span> <span data-ttu-id="4e046-176">Nel valore della **ModuleVersion** chiave nel manifesto, immettere il numero di versione del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-176">In the value of the **ModuleVersion** key in the manifest, enter the module version number.</span></span> <span data-ttu-id="4e046-177">Salvare il file manifesto (psd1) nella directory specifica della versione per il modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-177">Save the manifest file (.psd1) in the version-specific directory for the module.</span></span>

3. <span data-ttu-id="4e046-178">Aggiungere il percorso della cartella radice modulo il valore di **PSModulePath** variabile di ambiente, come illustrato negli esempi seguenti.</span><span class="sxs-lookup"><span data-stu-id="4e046-178">Add the module root folder path to the value of the **PSModulePath** environment variable, as shown in the following examples.</span></span>

<span data-ttu-id="4e046-179">Per importare una particolare versione del modulo, l'utente finale può usare il `MinimumVersion` oppure `RequiredVersion` i parametri del [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e046-179">To import a particular version of the module, the end-user can use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4e046-180">Ad esempio, se il modulo di Fabrikam è disponibile nelle versioni 8.0 e 9.0, la struttura di directory del modulo Fabrikam potrebbe essere simile al seguente.</span><span class="sxs-lookup"><span data-stu-id="4e046-180">For example, if the Fabrikam module is available in versions 8.0 and 9.0, the Fabrikam module directory structure might resemble the following.</span></span>

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

<span data-ttu-id="4e046-181">Il programma di installazione aggiunge entrambi i percorsi dei moduli per la **PSModulePath** valore variabile di ambiente.</span><span class="sxs-lookup"><span data-stu-id="4e046-181">The installer adds both of the module paths to the **PSModulePath** environment variable value.</span></span>

```powershell
$p = [Environment]::GetEnvironmentVariable("PSModulePath")
$p += ";C:\Program Files\Fabrikam\Fabrikam8;C:\Program Files\Fabrikam\Fabrikam9"
[Environment]::SetEnvironmentVariable("PSModulePath",$p)
```

<span data-ttu-id="4e046-182">Quando questi passaggi sono stati completati, il **ListAvailable** parametro delle [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet recupera entrambi i moduli di Fabrikam.</span><span class="sxs-lookup"><span data-stu-id="4e046-182">When these steps are complete, the **ListAvailable** parameter of the [Get-Module](/powershell/module/Microsoft.PowerShell.Core/Get-Module) cmdlet gets both of the Fabrikam modules.</span></span> <span data-ttu-id="4e046-183">Per importare un modulo specifico, usare il `MinimumVersion` oppure `RequiredVersion` i parametri delle [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e046-183">To import a particular module, use the `MinimumVersion` or `RequiredVersion` parameters of the [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module) cmdlet.</span></span>

<span data-ttu-id="4e046-184">Se entrambi i moduli vengono importati nella stessa sessione e i moduli contengono cmdlet con gli stessi nomi, i cmdlet che vengano importati per ultimo vengono applicati nella sessione.</span><span class="sxs-lookup"><span data-stu-id="4e046-184">If both modules are imported into the same session, and the modules contain cmdlets with the same names, the cmdlets that are imported last are effective in the session.</span></span>

## <a name="handling-command-name-conflicts"></a><span data-ttu-id="4e046-185">Conflitti di nomi di comando di gestione</span><span class="sxs-lookup"><span data-stu-id="4e046-185">Handling Command Name Conflicts</span></span>

<span data-ttu-id="4e046-186">Quando i comandi esportati da un modulo hanno lo stesso nome di comandi nella sessione dell'utente, possono verificarsi conflitti di nome di comando.</span><span class="sxs-lookup"><span data-stu-id="4e046-186">Command name conflicts can occur when the commands that a module exports have the same name as commands in the user's session.</span></span>

<span data-ttu-id="4e046-187">Quando una sessione contiene due comandi che hanno lo stesso nome, Windows PowerShell viene eseguito il tipo di comando che ha la precedenza.</span><span class="sxs-lookup"><span data-stu-id="4e046-187">When a session contains two commands that have the same name, Windows PowerShell runs the command type that takes precedence.</span></span> <span data-ttu-id="4e046-188">Quando una sessione contiene due comandi che hanno lo stesso nome e lo stesso tipo, Windows PowerShell esegue il comando che è stato aggiunto alla sessione più recente.</span><span class="sxs-lookup"><span data-stu-id="4e046-188">When a session contains two commands that have the same name and the same type, Windows PowerShell runs the command that was added to the session most recently.</span></span> <span data-ttu-id="4e046-189">Per eseguire un comando che non viene eseguito per impostazione predefinita, gli utenti possono qualificare il nome di comando con il nome del modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-189">To run a command that is not run by default, users can qualify the command name with the module name.</span></span>

<span data-ttu-id="4e046-190">Ad esempio, se la sessione contiene una `Get-Date` funzione e `Get-Date` cmdlet di Windows PowerShell esegue la funzione per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4e046-190">For example, if the session contains a `Get-Date` function and the `Get-Date` cmdlet, Windows PowerShell runs the function by default.</span></span> <span data-ttu-id="4e046-191">Per eseguire il cmdlet, anteporre il comando con il nome del modulo, ad esempio:</span><span class="sxs-lookup"><span data-stu-id="4e046-191">To run the cmdlet, preface the command with the module name, such as:</span></span>

```powershell
Microsoft.PowerShell.Utility\Get-Date
```

<span data-ttu-id="4e046-192">Per evitare conflitti di nomi, gli autori di moduli è possono usare la **DefaultCommandPrefix** chiave nel manifesto del modulo per specificare un prefisso per tutti i comandi esportati dal modulo.</span><span class="sxs-lookup"><span data-stu-id="4e046-192">To prevent name conflicts, module authors can use the **DefaultCommandPrefix** key in the module manifest to specify a noun prefix for all commands exported from the module.</span></span>

<span data-ttu-id="4e046-193">Gli utenti possono usare la **prefisso** parametro del `Import-Module` cmdlet da usare un prefisso alternativo.</span><span class="sxs-lookup"><span data-stu-id="4e046-193">Users can use the **Prefix** parameter of the `Import-Module` cmdlet to use an alternate prefix.</span></span> <span data-ttu-id="4e046-194">Il valore della **Prefix** parametro ha la precedenza sul valore della **DefaultCommandPrefix** chiave.</span><span class="sxs-lookup"><span data-stu-id="4e046-194">The value of the **Prefix** parameter takes precedence over the value of the **DefaultCommandPrefix** key.</span></span>

## <a name="see-also"></a><span data-ttu-id="4e046-195">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4e046-195">See Also</span></span>

[<span data-ttu-id="4e046-196">about_Command_Precedence</span><span class="sxs-lookup"><span data-stu-id="4e046-196">about_Command_Precedence</span></span>](/powershell/module/microsoft.powershell.core/about/about_command_precedence)

[<span data-ttu-id="4e046-197">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4e046-197">Writing a Windows PowerShell Module</span></span>](./writing-a-windows-powershell-module.md)
