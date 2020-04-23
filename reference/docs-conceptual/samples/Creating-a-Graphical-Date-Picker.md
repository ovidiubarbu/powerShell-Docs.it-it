---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione di un controllo grafico di selezione data
ms.openlocfilehash: b748e301b24ed643488079b547e2da1a5a7a6551
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706131"
---
# <a name="creating-a-graphical-date-picker"></a>Creazione di un controllo grafico di selezione data

Usare Windows PowerShell 3.0 e versioni successive per creare un modulo con un controllo grafico di tipo calendario che consente agli utenti di selezionare un giorno del mese.

## <a name="create-a-graphical-date-picker-control"></a>Creare un controllo grafico di selezione data

Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}

$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)

$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$result = $form.ShowDialog()

if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

In questo esempio vengono assegnati valori a quattro proprietà di questa classe usando la proprietà **Property** e la tabella hash.

1. **StartPosition**: Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando questa proprietà su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

2. **Size**: Le dimensioni del modulo, in pixel.
   Lo script precedente crea un modulo di 243 pixel in larghezza per 230 pixel in altezza.

3. **Text**: Questo valore diventa il titolo della finestra.

4. **Topmost**: impostando questa proprietà su `$true` è possibile forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.

Quindi creare e aggiungere un controllo calendario nel modulo.
In questo esempio il giorno corrente non è evidenziato né cerchiato.
Gli utenti possono selezionare un solo giorno del calendario alla volta.

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 165 pixel dal bordo superiore del modulo e di 38 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```powershell
$okButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 38, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'OK'
    DialogResult = [Windows.Forms.DialogResult]::OK
}
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

Analogamente, creare un pulsante **Cancel**.
Il pulsante **Cancel** è posizionato a 165 pixel di distanza dal bordo superiore, ma a 113 pixel dal bordo sinistro della finestra.

```powershell
$cancelButton = New-Object Windows.Forms.Button -Property @{
    Location     = New-Object Drawing.Point 113, 165
    Size         = New-Object Drawing.Size 75, 23
    Text         = 'Cancel'
    DialogResult = [Windows.Forms.DialogResult]::Cancel
}
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.

```powershell
$result = $form.ShowDialog()
```

Infine, il codice all'interno del blocco `if` indica a Windows cosa fare con il modulo dopo che l'utente seleziona un giorno del calendario e quindi fa clic su **OK** o preme **INVIO**. Windows PowerShell visualizza la data selezionata.

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a>Vedere anche

- [GitHub: WinFormsExampleUpdates di Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10)) (Creazione di un controllo grafico di selezione data)
