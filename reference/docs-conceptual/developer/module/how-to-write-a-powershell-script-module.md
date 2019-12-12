---
title: Come scrivere un modulo di script di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 11/21/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: 7742eedd67283535b9e5898adc74d0d48faf68fe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74416271"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="cb125-102">Come scrivere un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb125-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="cb125-103">Un modulo di script è qualsiasi script di PowerShell valido salvato in un'estensione `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="cb125-103">A script module is any valid PowerShell script saved in a `.psm1` extension.</span></span> <span data-ttu-id="cb125-104">Questa estensione consente al motore di PowerShell di usare le regole e i cmdlet del modulo sul file.</span><span class="sxs-lookup"><span data-stu-id="cb125-104">This extension allows the PowerShell engine to use rules and module cmdlets on your file.</span></span> <span data-ttu-id="cb125-105">La maggior parte di queste funzionalità è disponibile per facilitare l'installazione del codice su altri sistemi, nonché per gestire l'ambito.</span><span class="sxs-lookup"><span data-stu-id="cb125-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="cb125-106">È anche possibile usare un file manifesto del modulo, che descrive installazioni e soluzioni più complesse.</span><span class="sxs-lookup"><span data-stu-id="cb125-106">You can also use a module manifest file, which describes more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="cb125-107">Scrittura di un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="cb125-107">Writing a PowerShell script module</span></span>

<span data-ttu-id="cb125-108">Per creare un modulo di script, salvare uno script di PowerShell valido in un file di `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="cb125-108">To create a script module, save a valid PowerShell script to a `.psm1` file.</span></span> <span data-ttu-id="cb125-109">Lo script e la directory in cui è archiviato devono usare lo stesso nome.</span><span class="sxs-lookup"><span data-stu-id="cb125-109">The script and the directory where it's stored must use the same name.</span></span> <span data-ttu-id="cb125-110">Ad esempio, uno script denominato `MyPsScript.psm1` viene archiviato in una directory denominata `MyPsScript`.</span><span class="sxs-lookup"><span data-stu-id="cb125-110">For example, a script named `MyPsScript.psm1` is stored in a directory named `MyPsScript`.</span></span>

<span data-ttu-id="cb125-111">La directory del modulo deve trovarsi in un percorso specificato in `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="cb125-111">The module's directory needs to be in a path specified in `$env:PSModulePath`.</span></span> <span data-ttu-id="cb125-112">La directory del modulo può contenere tutte le risorse necessarie per eseguire lo script e un file manifesto del modulo che descrive a PowerShell come funziona il modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-112">The module's directory can contain any resources that are needed to run the script, and a module manifest file that describes to PowerShell how your module works.</span></span>

## <a name="create-a-basic-powershell-module"></a><span data-ttu-id="cb125-113">Creare un modulo di PowerShell di base</span><span class="sxs-lookup"><span data-stu-id="cb125-113">Create a basic PowerShell module</span></span>

<span data-ttu-id="cb125-114">I passaggi seguenti descrivono come creare un modulo di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="cb125-114">The following steps describe how to create a PowerShell module.</span></span>

1. <span data-ttu-id="cb125-115">Salvare uno script di PowerShell con un'estensione `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="cb125-115">Save a PowerShell script with a `.psm1` extension.</span></span> <span data-ttu-id="cb125-116">Usare lo stesso nome per lo script e la directory in cui viene salvato lo script.</span><span class="sxs-lookup"><span data-stu-id="cb125-116">Use the same name for the script and the directory where the script is saved.</span></span>

   <span data-ttu-id="cb125-117">Il salvataggio di uno script con l'estensione `.psm1` significa che è possibile usare i cmdlet del modulo, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span><span class="sxs-lookup"><span data-stu-id="cb125-117">Saving a script with the `.psm1` extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module).</span></span> <span data-ttu-id="cb125-118">I cmdlet del modulo esistono principalmente per poter importare ed esportare il codice nei sistemi di altri utenti.</span><span class="sxs-lookup"><span data-stu-id="cb125-118">The module cmdlets exist primarily so that you can import and export your code onto other user's systems.</span></span> <span data-ttu-id="cb125-119">La soluzione alternativa consiste nel caricare il codice su altri sistemi e quindi assegnarlo al punto di origine nella memoria attiva, che non è una soluzione scalabile.</span><span class="sxs-lookup"><span data-stu-id="cb125-119">The alternate solution would be to load your code on other systems and then dot-source it into active memory, which isn't a scalable solution.</span></span> <span data-ttu-id="cb125-120">Per ulteriori informazioni, vedere informazioni su [un modulo di Windows PowerShell](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span><span class="sxs-lookup"><span data-stu-id="cb125-120">For more information, see [Understanding a Windows PowerShell Module](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).</span></span>
   <span data-ttu-id="cb125-121">Per impostazione predefinita, quando gli utenti importano il file di `.psm1`, tutte le funzioni nello script sono accessibili, ma le variabili non lo sono.</span><span class="sxs-lookup"><span data-stu-id="cb125-121">By default, when users import your `.psm1` file, all functions in your script are accessible, but variables aren't.</span></span>

   <span data-ttu-id="cb125-122">Un esempio di script di PowerShell, denominato `Show-Calendar`, è disponibile alla fine di questo articolo.</span><span class="sxs-lookup"><span data-stu-id="cb125-122">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this article.</span></span>

   ```powershell
   function Show-Calendar {
   param(
       [DateTime] $start = [DateTime]::Today,
       [DateTime] $end = $start,
       $firstDayOfWeek,
       [int[]] $highlightDay,
       [string[]] $highlightDate = [DateTime]::Today.ToString()
       )

       #actual code for the function goes here see the end of the topic for the complete code sample
   }
   ```

2. <span data-ttu-id="cb125-123">Per controllare l'accesso degli utenti a determinate funzioni o variabili, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.</span><span class="sxs-lookup"><span data-stu-id="cb125-123">To control user access to certain functions or variables, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="cb125-124">Il codice di esempio nella parte inferiore dell'articolo ha una sola funzione, che per impostazione predefinita verrebbe esposta.</span><span class="sxs-lookup"><span data-stu-id="cb125-124">The example code at the bottom of the article has only one function, which by default would be exposed.</span></span> <span data-ttu-id="cb125-125">Tuttavia, è consigliabile chiamare esplicitamente le funzioni che si desidera esporre, come descritto nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="cb125-125">However, it's recommended you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="cb125-126">È possibile limitare gli elementi importati usando un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-126">You can restrict what's imported using a module manifest.</span></span> <span data-ttu-id="cb125-127">Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo di PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cb125-127">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="cb125-128">Se sono presenti moduli che devono essere caricati dal modulo, è possibile usare `Import-Module`nella parte superiore del modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-128">If you have modules that your own module needs to load, you can use `Import-Module`, at the top of your module.</span></span>

   <span data-ttu-id="cb125-129">Il cmdlet `Import-Module` importa un modulo di destinazione in un sistema e può essere usato in un secondo momento nella procedura per installare un modulo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="cb125-129">The `Import-Module` cmdlet imports a targeted module onto a system, and can be used at a later point in the procedure to install your own module.</span></span> <span data-ttu-id="cb125-130">Il codice di esempio nella parte inferiore di questo articolo non usa alcun modulo di importazione.</span><span class="sxs-lookup"><span data-stu-id="cb125-130">The sample code at the bottom of this article doesn't use any import modules.</span></span> <span data-ttu-id="cb125-131">In caso contrario, verranno elencati all'inizio del file, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="cb125-131">But if it did, they would be listed at the top of the file, as shown in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="cb125-132">Per descrivere il modulo al sistema della Guida di PowerShell, è possibile usare i commenti della guida standard all'interno del file oppure creare un file della Guida aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="cb125-132">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="cb125-133">L'esempio di codice nella parte inferiore di questo articolo include le informazioni della guida nei commenti.</span><span class="sxs-lookup"><span data-stu-id="cb125-133">The code sample at the bottom of this article includes the help information in the comments.</span></span> <span data-ttu-id="cb125-134">È anche possibile scrivere file XML espansi che contengono contenuto della Guida aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="cb125-134">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="cb125-135">Per ulteriori informazioni, vedere [la pagina relativa alla scrittura della Guida per i moduli di Windows PowerShell](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="cb125-135">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="cb125-136">Se si hanno moduli aggiuntivi, file XML o altro contenuto che si vuole creare nel pacchetto con il modulo, è possibile usare un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-136">If you have additional modules, XML files, or other content you want to package with your module, you can use a module manifest.</span></span>

   <span data-ttu-id="cb125-137">Un manifesto del modulo è un file che contiene i nomi di altri moduli, layout di directory, numeri di controllo delle versioni, dati dell'autore e altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="cb125-137">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="cb125-138">PowerShell usa il file manifesto del modulo per organizzare e distribuire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="cb125-138">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="cb125-139">Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="cb125-139">For more information, see [How to write a PowerShell module manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="cb125-140">Per installare ed eseguire il modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati e usare `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cb125-140">To install and run your module, save the module to one of the appropriate PowerShell paths, and use `Import-Module`.</span></span>

   <span data-ttu-id="cb125-141">I percorsi in cui è possibile installare il modulo si trovano nella variabile globale `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="cb125-141">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="cb125-142">Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="cb125-142">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="cb125-143">Assicurarsi di creare una directory per il modulo che usa lo stesso nome del modulo di script, anche se si tratta solo di un singolo file di `.psm1`.</span><span class="sxs-lookup"><span data-stu-id="cb125-143">Be sure to create a directory for your module that uses the same name as the script module, even if it's only a single `.psm1` file.</span></span> <span data-ttu-id="cb125-144">Se il modulo non è stato salvato in uno di questi percorsi, è necessario specificare il percorso del modulo nel comando `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="cb125-144">If you didn't save your module to one of these paths, you would have to specify the module's location in the `Import-Module` command.</span></span> <span data-ttu-id="cb125-145">In caso contrario, PowerShell non sarà in grado di trovare il modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-145">Otherwise, PowerShell wouldn't be able to find the module.</span></span>

   <span data-ttu-id="cb125-146">A partire da PowerShell 3,0, se il modulo è stato inserito in uno dei percorsi dei moduli di PowerShell, non è necessario importarlo in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="cb125-146">Starting with PowerShell 3.0, if you've placed your module in one of the PowerShell module paths, you don't need to explicitly import it.</span></span> <span data-ttu-id="cb125-147">Il modulo viene caricato automaticamente quando un utente chiama la funzione.</span><span class="sxs-lookup"><span data-stu-id="cb125-147">Your module is automatically loaded when a user calls your function.</span></span> <span data-ttu-id="cb125-148">Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [modifica del percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="cb125-148">For more information about the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [Modifying the PSModulePath Installation Path](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="cb125-149">Per rimuovere un modulo dal servizio attivo nella sessione corrente di PowerShell, usare [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="cb125-149">To remove a module from active service in the current PowerShell session, use [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   > [!NOTE]
   > <span data-ttu-id="cb125-150">`Remove-Module` rimuove un modulo dalla sessione corrente di PowerShell, ma non disinstalla il modulo o Elimina i file del modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-150">`Remove-Module` removes a module from the current PowerShell session, but doesn't uninstall the module or delete the module's files.</span></span>

## <a name="show-calendar-code-example"></a><span data-ttu-id="cb125-151">Esempio di codice Show-Calendar</span><span class="sxs-lookup"><span data-stu-id="cb125-151">Show-Calendar code example</span></span>

<span data-ttu-id="cb125-152">L'esempio seguente è un modulo di script che contiene una singola funzione denominata `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="cb125-152">The following example is a script module that contains a single function named `Show-Calendar`.</span></span> <span data-ttu-id="cb125-153">Questa funzione Visualizza una rappresentazione visiva di un calendario.</span><span class="sxs-lookup"><span data-stu-id="cb125-153">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="cb125-154">L'esempio contiene le stringhe della Guida di PowerShell per la sinossia, la descrizione, i valori dei parametri e il codice.</span><span class="sxs-lookup"><span data-stu-id="cb125-154">The sample contains the PowerShell Help strings for the synopsis, description, parameter values, and code.</span></span> <span data-ttu-id="cb125-155">Quando il modulo viene importato, il comando `Export-ModuleMember` garantisce che la funzione `Show-Calendar` venga esportata come membro del modulo.</span><span class="sxs-lookup"><span data-stu-id="cb125-155">When the module is imported, the `Export-ModuleMember` command ensures that the `Show-Calendar` function is exported as a module member.</span></span>

```powershell
<#
 .Synopsis
  Displays a visual representation of a calendar.

 .Description
  Displays a visual representation of a calendar. This function supports multiple months
  and lets you highlight specific date ranges or days.

 .Parameter Start
  The first month to display.

 .Parameter End
  The last month to display.

 .Parameter FirstDayOfWeek
  The day of the month on which the week begins.

 .Parameter HighlightDay
  Specific days (numbered) to highlight. Used for date ranges like (25..31).
  Date ranges are specified by the Windows PowerShell range syntax. These dates are
  enclosed in square brackets.

 .Parameter HighlightDate
  Specific days (named) to highlight. These dates are surrounded by asterisks.

 .Example
   # Show a default display of this month.
   Show-Calendar

 .Example
   # Display a date range.
   Show-Calendar -Start "March, 2010" -End "May, 2010"

 .Example
   # Highlight a range of days.
   Show-Calendar -HighlightDay (1..10 + 22) -HighlightDate "December 25, 2008"
#>
function Show-Calendar {
param(
    [DateTime] $start = [DateTime]::Today,
    [DateTime] $end = $start,
    $firstDayOfWeek,
    [int[]] $highlightDay,
    [string[]] $highlightDate = [DateTime]::Today.ToString()
    )

## Determine the first day of the start and end months.
$start = New-Object DateTime $start.Year,$start.Month,1
$end = New-Object DateTime $end.Year,$end.Month,1

## Convert the highlighted dates into real dates.
[DateTime[]] $highlightDate = [DateTime[]] $highlightDate

## Retrieve the DateTimeFormat information so that the
## calendar can be manipulated.
$dateTimeFormat  = (Get-Culture).DateTimeFormat
if($firstDayOfWeek)
{
    $dateTimeFormat.FirstDayOfWeek = $firstDayOfWeek
}

$currentDay = $start

## Process the requested months.
while($start -le $end)
{
    ## Return to an earlier point in the function if the first day of the month
    ## is in the middle of the week.
    while($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek)
    {
        $currentDay = $currentDay.AddDays(-1)
    }

    ## Prepare to store information about this date range.
    $currentWeek = New-Object PsObject
    $dayNames = @()
    $weeks = @()

    ## Continue processing dates until the function reaches the end of the month.
    ## The function continues until the week is completed with
    ## days from the next month.
    while(($currentDay -lt $start.AddMonths(1)) -or
        ($currentDay.DayOfWeek -ne $dateTimeFormat.FirstDayOfWeek))
    {
        ## Determine the day names to use to label the columns.
        $dayName = "{0:ddd}" -f $currentDay
        if($dayNames -notcontains $dayName)
        {
            $dayNames += $dayName
        }

        ## Pad the day number for display, highlighting if necessary.
        $displayDay = " {0,2} " -f $currentDay.Day

        ## Determine whether to highlight a specific date.
        if($highlightDate)
        {
            $compareDate = New-Object DateTime $currentDay.Year,
                $currentDay.Month,$currentDay.Day
            if($highlightDate -contains $compareDate)
            {
                $displayDay = "*" + ("{0,2}" -f $currentDay.Day) + "*"
            }
        }

        ## Otherwise, highlight as part of a date range.
        if($highlightDay -and ($highlightDay[0] -eq $currentDay.Day))
        {
            $displayDay = "[" + ("{0,2}" -f $currentDay.Day) + "]"
            $null,$highlightDay = $highlightDay
        }

        ## Add the day of the week and the day of the month as note properties.
        $currentWeek | Add-Member NoteProperty $dayName $displayDay

        ## Move to the next day of the month.
        $currentDay = $currentDay.AddDays(1)

        ## If the function reaches the next week, store the current week
        ## in the week list and continue.
        if($currentDay.DayOfWeek -eq $dateTimeFormat.FirstDayOfWeek)
        {
            $weeks += $currentWeek
            $currentWeek = New-Object PsObject
        }
    }

    ## Format the weeks as a table.
    $calendar = $weeks | Format-Table $dayNames -AutoSize | Out-String

    ## Add a centered header.
    $width = ($calendar.Split("`n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " `n" + $padding + $header + "`n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
