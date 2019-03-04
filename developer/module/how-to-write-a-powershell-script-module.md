---
title: Come scrivere un modulo di Script di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed7645ea-5e52-4a45-81a7-aa3c2d605cde
caps.latest.revision: 16
ms.openlocfilehash: e8b7151538235cdf7183b78aa8df7e596d6bcfd9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859007"
---
# <a name="how-to-write-a-powershell-script-module"></a><span data-ttu-id="b130e-102">Come scrivere un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b130e-102">How to Write a PowerShell Script Module</span></span>

<span data-ttu-id="b130e-103">Un modulo di script è essenzialmente qualsiasi script di PowerShell valido salvata in un'estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="b130e-103">A script module is essentially any valid PowerShell script saved in a .psm1 extension.</span></span> <span data-ttu-id="b130e-104">Questa estensione consente al motore di PowerShell impostare una serie di regole e i cmdlet per il file.</span><span class="sxs-lookup"><span data-stu-id="b130e-104">This extension allows the PowerShell engine to use a number of rules and cmdlets on your file.</span></span> <span data-ttu-id="b130e-105">La maggior parte di queste funzionalità sono presenti per installare il codice in altri sistemi, nonché la gestione dell'ambito.</span><span class="sxs-lookup"><span data-stu-id="b130e-105">Most of these capabilities are there to help you install your code on other systems, as well as manage scoping.</span></span> <span data-ttu-id="b130e-106">È anche possibile usare un file manifesto del modulo, che può descrivere le installazioni ancora più complesse e soluzioni.</span><span class="sxs-lookup"><span data-stu-id="b130e-106">You can also use a module manifest file, which can describe even more complex installations and solutions.</span></span>

## <a name="writing-a-powershell-script-module"></a><span data-ttu-id="b130e-107">Scrittura di un modulo di Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="b130e-107">Writing a PowerShell Script Module</span></span>

<span data-ttu-id="b130e-108">Si crea un modulo di script dal salvataggio di uno script di PowerShell valido in un file con estensione psm1 e quindi salvare il file in una directory che si trova dove PowerShell possono trovarlo.</span><span class="sxs-lookup"><span data-stu-id="b130e-108">You create a script module by saving a valid PowerShell script to a .psm1 file, and then saving that file in a directory located where PowerShell can find it.</span></span> <span data-ttu-id="b130e-109">In tale cartella che è anche possibile inserire le risorse che necessarie per eseguire lo script, nonché un file manifesto che descrive a PowerShell funzionamento del modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-109">In that folder you can also place any resources you need to run your script, as well as a manifest file that describes to PowerShell how your module works.</span></span>

#### <a name="to-create-a-basic-powershell-module"></a><span data-ttu-id="b130e-110">Per creare un modulo di PowerShell di base</span><span class="sxs-lookup"><span data-stu-id="b130e-110">To create a basic PowerShell Module</span></span>

1. <span data-ttu-id="b130e-111">Eseguire uno script di PowerShell esistente e salvare lo script con estensione psm1.</span><span class="sxs-lookup"><span data-stu-id="b130e-111">Take an existing PowerShell script, and save the script with a .psm1 extension.</span></span>

   <span data-ttu-id="b130e-112">Salvataggio di uno script con il psm1 estensione significa che è possibile usare i cmdlet del modulo, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), su di esso.</span><span class="sxs-lookup"><span data-stu-id="b130e-112">Saving a script with the .psm1 extension means that you can use the module cmdlets, such as [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), on it.</span></span> <span data-ttu-id="b130e-113">Questi cmdlet esistono principalmente in modo che è facilmente possibile importare ed esportare il codice nei sistemi di altri utenti.</span><span class="sxs-lookup"><span data-stu-id="b130e-113">These cmdlets exist primarily so that you can easily import and export your code onto other user's systems.</span></span> <span data-ttu-id="b130e-114">(La soluzione alternativa sarebbe carica il codice in altri sistemi e quindi dot-sourcing in memoria attiva, che non è una soluzione particolarmente scalabile). Per altre informazioni vedere la **cmdlet del modulo e le variabili** sezione [moduli di Windows PowerShell](./understanding-a-windows-powershell-module.md) si noti che, per impostazione predefinita, tutte le funzioni nello script sarà accessibile agli utenti che importa il con estensione psm1 non saranno disponibile file, ma le proprietà.</span><span class="sxs-lookup"><span data-stu-id="b130e-114">(The alternate solution would be to load up your code on other systems and then dot-source it into active memory, which isn't a particularly scalable solution.) For more information see the **Module Cmdlets and Variables** section in [Windows PowerShell Modules](./understanding-a-windows-powershell-module.md) Note that, by default, all functions in your script will be accessible to users who import your .psm1 file, but properties will not.</span></span>

   <span data-ttu-id="b130e-115">Un esempio di script di PowerShell, intitolato Show-Calendar, è disponibile alla fine di questo argomento.</span><span class="sxs-lookup"><span data-stu-id="b130e-115">An example PowerShell script, entitled Show-Calendar, is available at the end of this topic.</span></span>

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

2. <span data-ttu-id="b130e-116">Se si desidera controllare l'accesso a determinate funzioni o le proprietà, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.</span><span class="sxs-lookup"><span data-stu-id="b130e-116">If you wish to control user access to certain functions or properties, call [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) at the end of your script.</span></span>

   <span data-ttu-id="b130e-117">Nell'esempio di codice nella parte inferiore della pagina ha una sola funzione, che per impostazione predefinita viene esposto.</span><span class="sxs-lookup"><span data-stu-id="b130e-117">The example code at the bottom of the page has only one function, which by default would be exposed.</span></span> <span data-ttu-id="b130e-118">Tuttavia, è consigliabile che chiamare in modo esplicito le funzioni che si desidera esporre, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b130e-118">However, it is recommended that you explicitly call out which functions you wish to expose, as described in the following code:</span></span>

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   <span data-ttu-id="b130e-119">È inoltre possibile limitare cosa viene importato tramite un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-119">You can also restrict what is imported using a module manifest.</span></span> <span data-ttu-id="b130e-120">Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b130e-120">For more information, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [How to Write a PowerShell Module Manifest](./how-to-write-a-powershell-module-manifest.md).</span></span>

3. <span data-ttu-id="b130e-121">Se sono presenti moduli che deve avere caricato un modulo personalizzato, è possibile utilizzarli con una chiamata a `Import-Module`, nella parte superiore del modulo personalizzato.</span><span class="sxs-lookup"><span data-stu-id="b130e-121">If you have modules that your own module needs to have loaded, you can use them with a call to `Import-Module`, at the top of your own module.</span></span>

   <span data-ttu-id="b130e-122">`Import-Module` è un cmdlet che importa un modulo in un sistema di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b130e-122">`Import-Module` is a cmdlet that imports a targeted module onto a system.</span></span> <span data-ttu-id="b130e-123">Di conseguenza, viene utilizzato anche in un secondo momento nella procedura per installare anche il proprio modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-123">As such, it is also used at a later point in the procedure to install your own module as well.</span></span> <span data-ttu-id="b130e-124">Il codice di esempio nella parte inferiore della pagina non usa i moduli di importazione.</span><span class="sxs-lookup"><span data-stu-id="b130e-124">The sample code at the bottom of this page does not use any import modules.</span></span> <span data-ttu-id="b130e-125">In caso affermativo, tuttavia, verranno elencati nella parte superiore del file, come illustrato nel codice seguente:</span><span class="sxs-lookup"><span data-stu-id="b130e-125">If it did, however, they would be listed at the top of the file, as described in the following code:</span></span>

   ```powershell
   Import-Module GenericModule
   ```

4. <span data-ttu-id="b130e-126">Se si vuole descrivere il modulo al sistema della Guida di PowerShell, è possibile farlo con commenti all'interno del file della Guida standard o con un file della Guida aggiuntivo.</span><span class="sxs-lookup"><span data-stu-id="b130e-126">If you want to describe your module to the PowerShell Help system, you can do so either with the standard help comments inside the file, or with an additional Help file.</span></span>

   <span data-ttu-id="b130e-127">Nell'esempio di codice nella parte inferiore di questo argomento include le informazioni della Guida nei commenti.</span><span class="sxs-lookup"><span data-stu-id="b130e-127">The code sample at the bottom of this topic includes the help information in the comments.</span></span> <span data-ttu-id="b130e-128">Se si sceglie, è anche possibile scrivere espanso i file XML che contengono il contenuto della Guida aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="b130e-128">If you so choose, you could also write expanded XML files that contain additional help content.</span></span> <span data-ttu-id="b130e-129">Per altre informazioni, vedere [scrivere la Guida per Windows PowerShell moduli](./writing-help-for-windows-powershell-modules.md).</span><span class="sxs-lookup"><span data-stu-id="b130e-129">For more information, see [Writing Help for Windows PowerShell Modules](./writing-help-for-windows-powershell-modules.md).</span></span>

5. <span data-ttu-id="b130e-130">Se si dispone di altri moduli, i file XML o altro contenuto che si desidera creare un pacchetto di con un modulo, è possibile farlo con un manifesto del modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-130">If you have additional modules, XML files, or other content you want to package up with your module, you can do so with a module manifest.</span></span>

   <span data-ttu-id="b130e-131">Un manifesto del modulo è un file che contiene i nomi di altri moduli, i layout di directory, i numeri di controllo delle versioni, i dati dell'autore e altri tipi di informazioni.</span><span class="sxs-lookup"><span data-stu-id="b130e-131">A module manifest is a file that contains the names of other modules, directory layouts, versioning numbers, author data, and other pieces of information.</span></span> <span data-ttu-id="b130e-132">PowerShell Usa il file manifesto del modulo per organizzare e Distribuisci la tua soluzione.</span><span class="sxs-lookup"><span data-stu-id="b130e-132">PowerShell uses the module manifest file to organize and deploy your solution.</span></span> <span data-ttu-id="b130e-133">Tuttavia, a causa della natura relativamente semplice di questo esempio, un file manifesto non necessaria.</span><span class="sxs-lookup"><span data-stu-id="b130e-133">However, due to the relatively simple nature of this example, a manifest file was not needed.</span></span> <span data-ttu-id="b130e-134">Per altre informazioni, vedere [manifesti modulo](./how-to-write-a-powershell-module-manifest.md).</span><span class="sxs-lookup"><span data-stu-id="b130e-134">For more information, see [Module Manifests](./how-to-write-a-powershell-module-manifest.md).</span></span>

6. <span data-ttu-id="b130e-135">Per installare ed eseguire un modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati ed effettuare una chiamata a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="b130e-135">To install and run your module, save the module to one of the appropriate PowerShell paths, and make a call to `Import-Module`.</span></span>

   <span data-ttu-id="b130e-136">I percorsi in cui è possibile installare il modulo si trovano nel `$env:PSModulePath` (variabile globale).</span><span class="sxs-lookup"><span data-stu-id="b130e-136">The paths where you can install your module are located in the `$env:PSModulePath` global variable.</span></span> <span data-ttu-id="b130e-137">Ad esempio, potrebbe essere un percorso comune per salvare un modulo in un sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span><span class="sxs-lookup"><span data-stu-id="b130e-137">For example, a common path to save a module on a system would be `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`.</span></span> <span data-ttu-id="b130e-138">Assicurarsi di creare una cartella per il modulo esistente, anche se è solo un file con estensione psm1 singolo.</span><span class="sxs-lookup"><span data-stu-id="b130e-138">Be sure to create a folder for your module to exist in, even if it is only a single .psm1 file.</span></span> <span data-ttu-id="b130e-139">Se non è stato salvato il modulo a uno di questi percorsi, è necessario passare il percorso del modulo nella chiamata a `Import-Module`.</span><span class="sxs-lookup"><span data-stu-id="b130e-139">If you did not save your module to one of these paths, you would have to pass in the location of your module in the call to `Import-Module`.</span></span> <span data-ttu-id="b130e-140">(In caso contrario, PowerShell non sarebbe in grado di trovarlo.) A partire da PowerShell 3.0, se è stato inserito il modulo in uno dei percorsi dei moduli di PowerShell, non occorre eseguire l'importazione in modo esplicito: è sufficiente che un utente chiama la funzione lo caricherà automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b130e-140">(Otherwise, PowerShell would not be able to find it.) Starting with PowerShell 3.0, if you have placed your module on one of the PowerShell module paths, you do not need to explicitly import it: simply having a user call your function will automatically load it.</span></span> <span data-ttu-id="b130e-141">Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [variabile di ambiente PSModulePath](./modifying-the-psmodulepath-installation-path.md).</span><span class="sxs-lookup"><span data-stu-id="b130e-141">For more information on the module path, see [Importing a PowerShell Module](./importing-a-powershell-module.md) and [PSModulePath Environment Variable](./modifying-the-psmodulepath-installation-path.md).</span></span>

7. <span data-ttu-id="b130e-142">Per rimuovere un modulo da servizi attivi, effettuare una chiamata a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span><span class="sxs-lookup"><span data-stu-id="b130e-142">To remove a module from active service, make a call to [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).</span></span>

<span data-ttu-id="b130e-143">Si noti che [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) rimuove il modulo di memoria attiva - non effettivamente Elimina, dalla quale è stato salvato i file di modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-143">Note that [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) removes your module from active memory - it does not actually delete it from where you saved the module files.</span></span>

### <a name="show-calendar-code-example"></a><span data-ttu-id="b130e-144">Esempio di codice Show-Calendar</span><span class="sxs-lookup"><span data-stu-id="b130e-144">Show-Calendar code example</span></span>

<span data-ttu-id="b130e-145">L'esempio seguente è un modulo di script semplice che contiene una singola funzione denominata Show-Calendar.</span><span class="sxs-lookup"><span data-stu-id="b130e-145">The following example is a simple script module that contains a single function named Show-Calendar.</span></span> <span data-ttu-id="b130e-146">Questa funzione consente di visualizzare una rappresentazione visiva di un calendario.</span><span class="sxs-lookup"><span data-stu-id="b130e-146">This function displays a visual representation of a calendar.</span></span> <span data-ttu-id="b130e-147">Inoltre, l'esempio contiene le stringhe della Guida di PowerShell per il riepilogo, descrizione, i valori dei parametri ed esempio.</span><span class="sxs-lookup"><span data-stu-id="b130e-147">In addition, the sample contains the PowerShell Help strings for the synopsis, description, parameter values, and example.</span></span> <span data-ttu-id="b130e-148">Si noti che l'ultima riga di codice indica che la funzione Show-Calendar verrà esportata come un membro del modulo quando viene importato il modulo.</span><span class="sxs-lookup"><span data-stu-id="b130e-148">Note that the last line of code indicates that the Show-Calendar function will be exported as a module member when the module is imported.</span></span>

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
    $width = ($calendar.Split("'n") | Measure-Object -Maximum Length).Maximum
    $header = "{0:MMMM yyyy}" -f $start
    $padding = " " * (($width - $header.Length) / 2)
    $displayCalendar = " 'n" + $padding + $header + "'n " + $calendar
    $displayCalendar.TrimEnd()

    ## Move to the next month.
    $start = $start.AddMonths(1)

}
}
Export-ModuleMember -Function Show-Calendar
```
