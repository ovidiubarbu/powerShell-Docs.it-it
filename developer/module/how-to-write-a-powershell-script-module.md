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
# <a name="how-to-write-a-powershell-script-module"></a>Come scrivere un modulo di script di PowerShell

Un modulo di script è essenzialmente qualsiasi script di PowerShell valido salvata in un'estensione psm1. Questa estensione consente al motore di PowerShell impostare una serie di regole e i cmdlet per il file. La maggior parte di queste funzionalità sono presenti per installare il codice in altri sistemi, nonché la gestione dell'ambito. È anche possibile usare un file manifesto del modulo, che può descrivere le installazioni ancora più complesse e soluzioni.

## <a name="writing-a-powershell-script-module"></a>Scrittura di un modulo di Script di PowerShell

Si crea un modulo di script dal salvataggio di uno script di PowerShell valido in un file con estensione psm1 e quindi salvare il file in una directory che si trova dove PowerShell possono trovarlo. In tale cartella che è anche possibile inserire le risorse che necessarie per eseguire lo script, nonché un file manifesto che descrive a PowerShell funzionamento del modulo.

#### <a name="to-create-a-basic-powershell-module"></a>Per creare un modulo di PowerShell di base

1. Eseguire uno script di PowerShell esistente e salvare lo script con estensione psm1.

   Salvataggio di uno script con il psm1 estensione significa che è possibile usare i cmdlet del modulo, ad esempio [Import-Module](/powershell/module/Microsoft.PowerShell.Core/Import-Module), su di esso. Questi cmdlet esistono principalmente in modo che è facilmente possibile importare ed esportare il codice nei sistemi di altri utenti. (La soluzione alternativa sarebbe carica il codice in altri sistemi e quindi dot-sourcing in memoria attiva, che non è una soluzione particolarmente scalabile). Per altre informazioni vedere la **cmdlet del modulo e le variabili** sezione [moduli di Windows PowerShell](./understanding-a-windows-powershell-module.md) si noti che, per impostazione predefinita, tutte le funzioni nello script sarà accessibile agli utenti che importa il con estensione psm1 non saranno disponibile file, ma le proprietà.

   Un esempio di script di PowerShell, intitolato Show-Calendar, è disponibile alla fine di questo argomento.

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

2. Se si desidera controllare l'accesso a determinate funzioni o le proprietà, chiamare [Export-ModuleMember](/powershell/module/Microsoft.PowerShell.Core/Export-ModuleMember) alla fine dello script.

   Nell'esempio di codice nella parte inferiore della pagina ha una sola funzione, che per impostazione predefinita viene esposto. Tuttavia, è consigliabile che chiamare in modo esplicito le funzioni che si desidera esporre, come illustrato nel codice seguente:

   ```powershell
   function Show-Calendar {
         }
   Export-ModuleMember -Function Show-Calendar
   ```

   È inoltre possibile limitare cosa viene importato tramite un manifesto del modulo. Per altre informazioni, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [come scrivere un manifesto del modulo PowerShell](./how-to-write-a-powershell-module-manifest.md).

3. Se sono presenti moduli che deve avere caricato un modulo personalizzato, è possibile utilizzarli con una chiamata a `Import-Module`, nella parte superiore del modulo personalizzato.

   `Import-Module` è un cmdlet che importa un modulo in un sistema di destinazione. Di conseguenza, viene utilizzato anche in un secondo momento nella procedura per installare anche il proprio modulo. Il codice di esempio nella parte inferiore della pagina non usa i moduli di importazione. In caso affermativo, tuttavia, verranno elencati nella parte superiore del file, come illustrato nel codice seguente:

   ```powershell
   Import-Module GenericModule
   ```

4. Se si vuole descrivere il modulo al sistema della Guida di PowerShell, è possibile farlo con commenti all'interno del file della Guida standard o con un file della Guida aggiuntivo.

   Nell'esempio di codice nella parte inferiore di questo argomento include le informazioni della Guida nei commenti. Se si sceglie, è anche possibile scrivere espanso i file XML che contengono il contenuto della Guida aggiuntivi. Per altre informazioni, vedere [scrivere la Guida per Windows PowerShell moduli](./writing-help-for-windows-powershell-modules.md).

5. Se si dispone di altri moduli, i file XML o altro contenuto che si desidera creare un pacchetto di con un modulo, è possibile farlo con un manifesto del modulo.

   Un manifesto del modulo è un file che contiene i nomi di altri moduli, i layout di directory, i numeri di controllo delle versioni, i dati dell'autore e altri tipi di informazioni. PowerShell Usa il file manifesto del modulo per organizzare e Distribuisci la tua soluzione. Tuttavia, a causa della natura relativamente semplice di questo esempio, un file manifesto non necessaria. Per altre informazioni, vedere [manifesti modulo](./how-to-write-a-powershell-module-manifest.md).

6. Per installare ed eseguire un modulo, salvare il modulo in uno dei percorsi di PowerShell appropriati ed effettuare una chiamata a `Import-Module`.

   I percorsi in cui è possibile installare il modulo si trovano nel `$env:PSModulePath` (variabile globale). Ad esempio, potrebbe essere un percorso comune per salvare un modulo in un sistema `%SystemRoot%/users/<user>/Documents/WindowsPowerShell/Modules/<moduleName>`. Assicurarsi di creare una cartella per il modulo esistente, anche se è solo un file con estensione psm1 singolo. Se non è stato salvato il modulo a uno di questi percorsi, è necessario passare il percorso del modulo nella chiamata a `Import-Module`. (In caso contrario, PowerShell non sarebbe in grado di trovarlo.) A partire da PowerShell 3.0, se è stato inserito il modulo in uno dei percorsi dei moduli di PowerShell, non occorre eseguire l'importazione in modo esplicito: è sufficiente che un utente chiama la funzione lo caricherà automaticamente. Per altre informazioni sul percorso del modulo, vedere [importazione di un modulo di PowerShell](./importing-a-powershell-module.md) e [variabile di ambiente PSModulePath](./modifying-the-psmodulepath-installation-path.md).

7. Per rimuovere un modulo da servizi attivi, effettuare una chiamata a [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module).

Si noti che [Remove-Module](/powershell/module/Microsoft.PowerShell.Core/Remove-Module) rimuove il modulo di memoria attiva - non effettivamente Elimina, dalla quale è stato salvato i file di modulo.

### <a name="show-calendar-code-example"></a>Esempio di codice Show-Calendar

L'esempio seguente è un modulo di script semplice che contiene una singola funzione denominata Show-Calendar. Questa funzione consente di visualizzare una rappresentazione visiva di un calendario. Inoltre, l'esempio contiene le stringhe della Guida di PowerShell per il riepilogo, descrizione, i valori dei parametri ed esempio. Si noti che l'ultima riga di codice indica che la funzione Show-Calendar verrà esportata come un membro del modulo quando viene importato il modulo.

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
