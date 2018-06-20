---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Caselle di riepilogo a selezione multipla
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 81708fd5d7204fb7d136e9d8e808303f4d3f4c30
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30954892"
---
# <a name="multiple-selection-list-boxes"></a>Caselle di riepilogo a selezione multipla

Usare Windows PowerShell 3.0 e versioni successive per creare un controllo casella di riepilogo a selezione multipla in un Windows Form personalizzato.

## <a name="create-list-box-controls-that-allow-multiple-selections"></a>Creare controlli casella di riepilogo che consentono selezioni multiple

Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)

$listBox.SelectionMode = 'MultiExtended'

[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')

$listBox.Height = 70
$form.Controls.Add($listBox)
$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```powershell
$form = New-Object System.Windows.Forms.Form
```

Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.

- **Testo** Questo valore diventa il titolo della finestra.

- **Size.** Le dimensioni del modulo, in pixel. Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.

- **StartingPosition.** Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente. Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Analogamente, creare un pulsante **Cancel**. Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please make a selection from the list below:'
$form.Controls.Add($label)
```

Aggiungere il controllo, in questo caso una casella di riepilogo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta. Oltre alle caselle di testo, è possibile applicare molti altri controlli. Per altre informazioni, vedere [Spazio dei nomi System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.Listbox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
```

Ecco come specificare che si vuole consentire agli utenti di selezionare più valori nell'elenco.

```powershell
$listBox.SelectionMode = 'MultiExtended'
```

Nella sezione seguente, specificare i valori che si vuole vengano visualizzati nella casella di riepilogo.

```powershell
[void] $listBox.Items.Add('Item 1')
[void] $listBox.Items.Add('Item 2')
[void] $listBox.Items.Add('Item 3')
[void] $listBox.Items.Add('Item 4')
[void] $listBox.Items.Add('Item 5')
```

Specificare l'altezza massima del controllo casella di riepilogo.

```powershell
$listBox.Height = 70
```

Aggiungere il controllo casella di riepilogo nel modulo e indicare a Windows di aprire il modulo sopra altre finestre e finestre di dialogo.

```powershell
$form.Controls.Add($listBox)
$form.Topmost = $true
```

Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.

```powershell
$result = $form.ShowDialog()
```

Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona una o più opzioni della casella di riepilogo e quindi fa clic su **OK** o preme **INVIO**.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a>Vedere anche

- [Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates di Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Suggerimento della settimana su Windows PowerShell: caselle di riepilogo a selezione multipla e altro ancora!](http://technet.microsoft.com/library/ff730950.aspx)