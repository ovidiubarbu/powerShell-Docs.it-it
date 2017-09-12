---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Creazione di un controllo grafico di selezione data
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 7be72be7e9732737f00b15b6b2b83adcca4393ae
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="creating-a-graphical-date-picker"></a>Creazione di un controllo grafico di selezione data
Usare Windows PowerShell 3.0 e versioni successive per creare un modulo con un controllo grafico di tipo calendario che consente agli utenti di selezionare un giorno del mese.

## <a name="create-a-graphical-date-picker-control"></a>Creare un controllo grafico di selezione data
Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form 

$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"

$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar) 

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$form.Topmost = $True

$result = $form.ShowDialog() 

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```
$form = New-Object Windows.Forms.Form
```

Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.

- **Testo** Questo valore diventa il titolo della finestra.

- **Size.** Le dimensioni del modulo, in pixel. Lo script precedente crea un modulo di 243 pixel in larghezza per 230 pixel in altezza.

- **StartingPosition.** Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente. Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

Quindi creare e aggiungere un controllo calendario nel modulo. In questo esempio il giorno corrente non è evidenziato né cerchiato. Gli utenti possono selezionare un solo giorno del calendario alla volta.

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 165 pixel dal bordo superiore del modulo e di 38 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Analogamente, creare un pulsante **Cancel**. Il pulsante **Cancel** è posizionato a 165 pixel di distanza dal bordo superiore, ma a 113 pixel dal bordo sinistro della finestra.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Impostare la proprietà **Topmost** su **$True** per forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.

```
$form.Topmost = $True
```

Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.

```
$result = $form.ShowDialog()
```

Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona un giorno del calendario e quindi fa clic su **OK** o preme **INVIO**. Windows PowerShell visualizza la data selezionata.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Vedere anche
- [Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates di Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Suggerimento della settimana su Windows PowerShell: Creazione di un controllo grafico di selezione data](http://technet.microsoft.com/library/ff730942.aspx)

