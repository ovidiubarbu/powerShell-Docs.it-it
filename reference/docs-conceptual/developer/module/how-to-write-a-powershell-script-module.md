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
# <a name="how-to-write-a-powershell-script-module"></a>Come scrivere un modulo di script di PowerShell

Un modulo di script è essenzialmente qualsiasi script di PowerShell valido salvato in un'estensione psm1. Questa estensione consente al motore di PowerShell di usare una serie di regole e cmdlet per il file. La maggior parte di queste funzionalità è disponibile per facilitare l'installazione del codice su altri sistemi, nonché per gestire l'ambito. È anche possibile usare un file manifesto del modulo, che può descrivere installazioni e soluzioni ancora più complesse.

## <a name="writing-a-powershell-script-module"></a>Scrittura di un modulo di script di PowerShell

Per creare un modulo di script, salvare uno script di PowerShell valido in un file con estensione psm1 e quindi salvare il file in una directory in cui è possibile trovare PowerShell. In tale cartella è anche possibile inserire tutte le risorse necessarie per eseguire lo script, nonché un file manifesto che descrive il funzionamento del modulo in PowerShell.

#### <a name="to-create-a-basic-powershell-module"></a>Per creare un modulo di PowerShell di base

1. Usare uno script di PowerShell esistente e salvare lo script con estensione psm1.

   Il salvataggio di uno script con estensione psm1 significa che è possibile usare i cmdlet Module, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), su di esso. Questi cmdlet esistono principalmente per poter importare ed esportare facilmente il codice nei sistemi di altri utenti. (La soluzione alternativa consiste nel caricare il codice su altri sistemi e quindi impostarlo come punto di origine nella memoria attiva, che non è una soluzione particolarmente scalabile). Per altre informazioni, vedere la sezione **cmdlet e variabili del modulo** nei [moduli di Windows PowerShell](./understanding-a-windows-powershell-module.md) . per impostazione predefinita, tutte le funzioni nello script sono accessibili agli utenti che importano il file con estensione psm1, ma non le proprietà.

   Alla fine di questo argomento è disponibile uno script di PowerShell di esempio, denominato `Show-Calendar`.

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

2. Per controllare l'accesso degli utenti a determinate funzioni o proprietà, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.

   Il codice di esempio nella parte inferiore della pagina ha una sola funzione, che per impostazione predefinita verrebbe esposta. Tuttavia, si consiglia di richiamare in modo esplicito le funzioni che si desidera esporre, come descritto nel codice seguente:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   È anche possibile limitare gli elementi importati usando un manifesto del modulo. Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo di PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Se sono presenti moduli che devono essere caricati dal modulo, è possibile usarli con una chiamata a `Import-Module`, nella parte superiore del modulo.

   `Import-Module` è un cmdlet che importa un modulo di destinazione in un sistema. Di conseguenza, viene usato anche in un secondo momento nella procedura di installazione del modulo personalizzato. Il codice di esempio nella parte inferiore della pagina non usa alcun modulo di importazione. In caso contrario, verranno elencati all'inizio del file, come descritto nel codice seguente:

   ```powershell
   Import-Module GenericModule
   ```

4. Per descrivere il modulo al sistema della Guida di PowerShell, è possibile usare i commenti della guida standard all'interno del file oppure creare un file della Guida aggiuntivo.

   Nell'esempio di codice riportato nella parte inferiore di questo argomento sono incluse le informazioni della guida contenute nei commenti. È anche possibile scrivere file XML espansi che contengono contenuto della Guida aggiuntivo. Per ulteriori informazioni, vedere [la pagina relativa alla scrittura della Guida per i moduli di Windows PowerShell](./writing-help-for-windows-powershell-modules.md).

5. Se si hanno moduli aggiuntivi, file XML o altro contenuto che si vuole includere nel modulo, è possibile eseguire questa operazione con un manifesto del modulo.

   Un manifesto del modulo è un file che contiene i nomi di altri moduli, layout di directory, numeri di controllo delle versioni, dati dell'autore e altre informazioni. PowerShell usa il file manifesto del modulo per organizzare e distribuire la soluzione. Tuttavia, a causa della natura relativamente semplice di questo esempio, non è necessario un file manifesto. Per altre informazioni, vedere [manifesti dei moduli](./how-to-write-a-powershell-module-manifest.md).

6. Per installare ed eseguire il modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati ed effettuare una chiamata a `Import-Module`.

   I percorsi in cui è possibile installare il modulo si trovano nella variabile globale `$env:PSModulePath`. Un percorso comune per il salvataggio di un modulo in un sistema, ad esempio, sarebbe `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Assicurarsi di creare una cartella in cui è presente il modulo, anche se si tratta solo di un file con estensione psm1. Se il modulo non è stato salvato in uno di questi percorsi, è necessario passare il percorso del modulo nella chiamata a `Import-Module`. In caso contrario, PowerShell non riuscirà a trovarlo. A partire da PowerShell 3,0, se il modulo è stato inserito in uno dei percorsi dei moduli di PowerShell, non è necessario importarlo in modo esplicito. Il modulo viene caricato automaticamente quando un utente chiama la funzione.
   Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e di una [variabile di ambiente PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Per rimuovere un modulo dal servizio attivo, effettuare una chiamata a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

   Si noti che [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) rimuove il modulo dalla memoria attiva, ma non lo elimina dalla posizione in cui sono stati salvati i file del modulo.

### <a name="show-calendar-code-example"></a>Esempio di codice Show-Calendar

L'esempio seguente è un modulo di script semplice che contiene una singola funzione denominata `Show-Calendar`.
Questa funzione Visualizza una rappresentazione visiva di un calendario. Inoltre, l'esempio contiene le stringhe della Guida di PowerShell per la sinossia, la descrizione, i valori dei parametri e l'esempio. Si noti che l'ultima riga di codice garantisce che la funzione `Show-Calendar` venga esportata come membro del modulo quando viene importato il modulo.

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
