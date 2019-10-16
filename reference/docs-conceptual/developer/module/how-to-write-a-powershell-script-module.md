---
title: Come scrivere un modulo di script di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: b2a929a1724f77f0516ad24cfd90f6d6053ed19e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360690"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="13bb3-102">Come scrivere un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="13bb3-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="13bb3-103">Un modulo di script è essenzialmente qualsiasi script di PowerShell valido salvato in un'estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="13bb3-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="13bb3-104">Questa estensione consente al motore di PowerShell di usare una serie di regole e cmdlet per il file.</span><span class="sxs-lookup"><span data-stu-id="13bb3-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="13bb3-105">La maggior parte di queste funzionalità è disponibile per facilitare l'installazione del codice su altri sistemi, nonché per gestire l'ambito.</span><span class="sxs-lookup"><span data-stu-id="13bb3-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="13bb3-106">È anche possibile usare un file manifesto del modulo, che può descrivere installazioni e soluzioni ancora più complesse.</span><span class="sxs-lookup"><span data-stu-id="13bb3-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="13bb3-107">Scrittura di un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="13bb3-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="13bb3-108">Per creare un modulo di script, salvare uno script di PowerShell valido in un file con estensione psm1 e quindi salvare il file in una directory in cui è possibile trovare PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13bb3-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="13bb3-109">In tale cartella è anche possibile inserire tutte le risorse necessarie per eseguire lo script, nonché un file manifesto che descrive il funzionamento del modulo in PowerShell.</span><span class="sxs-lookup"><span data-stu-id="13bb3-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="13bb3-110">Per creare un modulo di PowerShell di base</span><span class="sxs-lookup"><span data-stu-id="13bb3-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="13bb3-111">Usare uno script di PowerShell esistente e salvare lo script con estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="13bb3-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="13bb3-112">Il salvataggio di uno script con estensione psm1 significa che è possibile usare i cmdlet Module, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), su di esso.</span><span class="sxs-lookup"><span data-stu-id="13bb3-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="13bb3-113">Questi cmdlet esistono principalmente per poter importare ed esportare facilmente il codice nei sistemi di altri utenti.</span><span class="sxs-lookup"><span data-stu-id="13bb3-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="13bb3-114">(La soluzione alternativa consiste nel caricare il codice su altri sistemi e quindi impostarlo come punto di origine nella memoria attiva, che non è una soluzione particolarmente scalabile). Per altre informazioni, vedere la sezione **cmdlet e variabili del modulo** nei [moduli di Windows PowerShell](./understanding-a-windows-powershell-module.md) . per impostazione predefinita, tutte le funzioni nello script sono accessibili agli utenti che importano il file con estensione psm1, ma non le proprietà.</span><span class="sxs-lookup"><span data-stu-id="13bb3-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script are accessible to users who import your .psm1 file, but properties are not.</span></span>

   <span data-ttu-id="13bb3-115">Alla fine di questo argomento è disponibile uno script di PowerShell di esempio, denominato `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-115">An example PowerShell script, entitled `Show-Calendar`, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="13bb3-116">Per controllare l'accesso degli utenti a determinate funzioni o proprietà, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.</span><span class="sxs-lookup"><span data-stu-id="13bb3-116">To control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="13bb3-117">Il codice di esempio nella parte inferiore della pagina ha una sola funzione, che per impostazione predefinita verrebbe esposta.</span><span class="sxs-lookup"><span data-stu-id="13bb3-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="13bb3-118">Tuttavia, si consiglia di richiamare in modo esplicito le funzioni che si desidera esporre, come descritto nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="13bb3-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="13bb3-119">È anche possibile limitare gli elementi importati usando un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="13bb3-120">Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo di PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="13bb3-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="13bb3-121">Se sono presenti moduli che devono essere caricati dal modulo, è possibile usarli con una chiamata a `Import-Module`, nella parte superiore del modulo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="13bb3-122">`Import-Module` è un cmdlet che importa un modulo di destinazione in un sistema.</span><span class="sxs-lookup"><span data-stu-id="13bb3-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="13bb3-123">Di conseguenza, viene usato anche in un secondo momento nella procedura di installazione del modulo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="13bb3-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="13bb3-124">Il codice di esempio nella parte inferiore della pagina non usa alcun modulo di importazione.</span><span class="sxs-lookup"><span data-stu-id="13bb3-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="13bb3-125">In caso contrario, verranno elencati all'inizio del file, come descritto nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="13bb3-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="13bb3-126">Per descrivere il modulo al sistema della Guida di PowerShell, è possibile usare i commenti della guida standard all'interno del file oppure creare un file della Guida aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-126">To describe your module to the PowerShell Help system, you can either use standard help comments inside the file, or create an additional Help file.</span></span>

   <span data-ttu-id="13bb3-127">Nell'esempio di codice riportato nella parte inferiore di questo argomento sono incluse le informazioni della guida contenute nei commenti.</span><span class="sxs-lookup"><span data-stu-id="13bb3-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="13bb3-128">È anche possibile scrivere file XML espansi che contengono contenuto della Guida aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-128">You could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="13bb3-129">Per ulteriori informazioni, vedere [la pagina relativa alla scrittura della Guida per i moduli di Windows PowerShell](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="13bb3-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="13bb3-130">Se si hanno moduli aggiuntivi, file XML o altro contenuto che si vuole includere nel modulo, è possibile eseguire questa operazione con un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="13bb3-131">Un manifesto del modulo è un file che contiene i nomi di altri moduli, layout di directory, numeri di controllo delle versioni, dati dell'autore e altre informazioni.</span><span class="sxs-lookup"><span data-stu-id="13bb3-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="13bb3-132">PowerShell usa il file manifesto del modulo per organizzare e distribuire la soluzione.</span><span class="sxs-lookup"><span data-stu-id="13bb3-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="13bb3-133">Tuttavia, a causa della natura relativamente semplice di questo esempio, non è necessario un file manifesto.</span><span class="sxs-lookup"><span data-stu-id="13bb3-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="13bb3-134">Per altre informazioni, vedere [manifesti dei moduli](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="13bb3-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="13bb3-135">Per installare ed eseguire il modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati ed effettuare una chiamata a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="13bb3-136">I percorsi in cui è possibile installare il modulo si trovano nella variabile globale `$env:PSModulePath`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="13bb3-137">Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="13bb3-138">Assicurarsi di creare una cartella in cui è presente il modulo, anche se si tratta solo di un file con estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="13bb3-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="13bb3-139">Se il modulo non è stato salvato in uno di questi percorsi, è necessario passare il percorso del modulo nella chiamata a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="13bb3-140">In caso contrario, PowerShell non riuscirà a trovarlo. A partire da PowerShell 3,0, se il modulo è stato inserito in uno dei percorsi dei moduli di PowerShell, non è necessario importarlo in modo esplicito.</span><span class="sxs-lookup"><span data-stu-id="13bb3-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module in one of the PowerShell module paths, you do not need to explicitly import it.</span></span> <span data-ttu-id="13bb3-141">Il modulo viene caricato automaticamente quando un utente chiama la funzione.</span><span class="sxs-lookup"><span data-stu-id="13bb3-141">You module is automatically loaded when a user calls your function.</span></span>
   <span data-ttu-id="13bb3-142">Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e di una [variabile di ambiente PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="13bb3-142">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="13bb3-143">Per rimuovere un modulo dal servizio attivo, effettuare una chiamata a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="13bb3-143">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

   <span data-ttu-id="13bb3-144">Si noti che [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) rimuove il modulo dalla memoria attiva, ma non lo elimina dalla posizione in cui sono stati salvati i file del modulo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-144">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="13bb3-145">Esempio di codice Show-Calendar</span><span class="sxs-lookup"><span data-stu-id="13bb3-145">Show-Calendar code example</span></span>

<span data-ttu-id="13bb3-146">L'esempio seguente è un modulo di script semplice che contiene una singola funzione denominata `Show-Calendar`.</span><span class="sxs-lookup"><span data-stu-id="13bb3-146">The following example is a simple script module that contains a single function named `Show-Calendar`.</span></span>
<span data-ttu-id="13bb3-147">Questa funzione Visualizza una rappresentazione visiva di un calendario.</span><span class="sxs-lookup"><span data-stu-id="13bb3-147">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="13bb3-148">Inoltre, l'esempio contiene le stringhe della Guida di PowerShell per la sinossia, la descrizione, i valori dei parametri e l'esempio.</span><span class="sxs-lookup"><span data-stu-id="13bb3-148">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="13bb3-149">Si noti che l'ultima riga di codice garantisce che la funzione `Show-Calendar` venga esportata come membro del modulo quando viene importato il modulo.</span><span class="sxs-lookup"><span data-stu-id="13bb3-149">Note that the last line of code ensures that the `Show-Calendar` function is exported as a module member when the module is imported.</span></span>

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
