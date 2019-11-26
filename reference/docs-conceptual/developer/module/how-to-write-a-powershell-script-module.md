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
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/23/2019
ms.locfileid: "74416271"
---
# <a name="how-to-write-a-powershell-script-module"></a>Come scrivere un modulo di script di PowerShell

Un modulo di script è qualsiasi script di PowerShell valido salvato in un'estensione `.psm1`. Questa estensione consente al motore di PowerShell di usare le regole e i cmdlet del modulo sul file. La maggior parte di queste funzionalità è disponibile per facilitare l'installazione del codice su altri sistemi, nonché per gestire l'ambito. È anche possibile usare un file manifesto del modulo, che descrive installazioni e soluzioni più complesse.

## <a name="writing-a-powershell-script-module"></a>Scrittura di un modulo di script di PowerShell

Per creare un modulo di script, salvare uno script di PowerShell valido in un file di `.psm1`. Lo script e la directory in cui è archiviato devono usare lo stesso nome. Ad esempio, uno script denominato `MyPsScript.psm1` viene archiviato in una directory denominata `MyPsScript`.

La directory del modulo deve trovarsi in un percorso specificato in `$env:PSModulePath`. La directory del modulo può contenere tutte le risorse necessarie per eseguire lo script e un file manifesto del modulo che descrive a PowerShell come funziona il modulo.

## <a name="create-a-basic-powershell-module"></a>Creare un modulo di PowerShell di base

I passaggi seguenti descrivono come creare un modulo di PowerShell.

1. Salvare uno script di PowerShell con un'estensione `.psm1`. Usare lo stesso nome per lo script e la directory in cui viene salvato lo script.

   Il salvataggio di uno script con l'estensione `.psm1` significa che è possibile usare i cmdlet del modulo, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module). I cmdlet del modulo esistono principalmente per poter importare ed esportare il codice nei sistemi di altri utenti. La soluzione alternativa consiste nel caricare il codice su altri sistemi e quindi assegnarlo al punto di origine nella memoria attiva, che non è una soluzione scalabile. Per ulteriori informazioni, vedere informazioni su [un modulo di Windows PowerShell](./understanding-a-windows-powershell-module.md#module-cmdlets-and-variables).
   Per impostazione predefinita, quando gli utenti importano il file di `.psm1`, tutte le funzioni nello script sono accessibili, ma le variabili non lo sono.

   Un esempio di script di PowerShell, denominato `Show-Calendar`, è disponibile alla fine di questo articolo.

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

2. Per controllare l'accesso degli utenti a determinate funzioni o variabili, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.

   Il codice di esempio nella parte inferiore dell'articolo ha una sola funzione, che per impostazione predefinita verrebbe esposta. Tuttavia, è consigliabile chiamare esplicitamente le funzioni che si desidera esporre, come descritto nel codice seguente:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   È possibile limitare gli elementi importati usando un manifesto del modulo. Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo di PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Se sono presenti moduli che devono essere caricati dal modulo, è possibile usare `Import-Module`nella parte superiore del modulo.

   Il cmdlet `Import-Module` importa un modulo di destinazione in un sistema e può essere usato in un secondo momento nella procedura per installare un modulo personalizzato. Il codice di esempio nella parte inferiore di questo articolo non usa alcun modulo di importazione. In caso contrario, verranno elencati all'inizio del file, come illustrato nel codice seguente:

   ```powershell
   Import-Module GenericModule
   ```

4. Per descrivere il modulo al sistema della Guida di PowerShell, è possibile usare i commenti della guida standard all'interno del file oppure creare un file della Guida aggiuntivo.

   L'esempio di codice nella parte inferiore di questo articolo include le informazioni della guida nei commenti. È anche possibile scrivere file XML espansi che contengono contenuto della Guida aggiuntivo. Per ulteriori informazioni, vedere [la pagina relativa alla scrittura della Guida per i moduli di Windows PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Se si hanno moduli aggiuntivi, file XML o altro contenuto che si vuole creare nel pacchetto con il modulo, è possibile usare un manifesto del modulo.

   Un manifesto del modulo è un file che contiene i nomi di altri moduli, layout di directory, numeri di controllo delle versioni, dati dell'autore e altre informazioni. PowerShell usa il file manifesto del modulo per organizzare e distribuire la soluzione. Per ulteriori informazioni, vedere [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

6. Per installare ed eseguire il modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati e usare `Import-Module`.

   I percorsi in cui è possibile installare il modulo si trovano nella variabile globale `$env:PSModulePath`. Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%/users/<user>/Documents/PowerShell/Modules/<moduleName>`. Assicurarsi di creare una directory per il modulo che usa lo stesso nome del modulo di script, anche se si tratta solo di un singolo file di `.psm1`. Se il modulo non è stato salvato in uno di questi percorsi, è necessario specificare il percorso del modulo nel comando `Import-Module`. In caso contrario, PowerShell non sarà in grado di trovare il modulo.

   A partire da PowerShell 3,0, se il modulo è stato inserito in uno dei percorsi dei moduli di PowerShell, non è necessario importarlo in modo esplicito. Il modulo viene caricato automaticamente quando un utente chiama la funzione. Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [modifica del percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Per rimuovere un modulo dal servizio attivo nella sessione corrente di PowerShell, usare [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   > [!NOTE]
   > `Remove-Module` rimuove un modulo dalla sessione corrente di PowerShell, ma non disinstalla il modulo o Elimina i file del modulo.

## <a name="show-calendar-code-example"></a>Esempio di codice Show-Calendar

L'esempio seguente è un modulo di script che contiene una singola funzione denominata `Show-Calendar`. Questa funzione Visualizza una rappresentazione visiva di un calendario. L'esempio contiene le stringhe della Guida di PowerShell per la sinossia, la descrizione, i valori dei parametri e il codice. Quando il modulo viene importato, il comando `Export-ModuleMember` garantisce che la funzione `Show-Calendar` venga esportata come membro del modulo.

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
