---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Selezione di elementi di una casella di riepilogo
ms.openlocfilehash: 048bccd403e01e2290a8930a0faba30d4c7caa73
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706173"
---
# <a name="selecting-items-from-a-list-box"></a>Selezione di elementi di una casella di riepilogo

Usare Windows PowerShell 3.0 e versioni successive per creare una finestra di dialogo che consente agli utenti di selezionare gli elementi da un controllo casella di riepilogo.

## <a name="create-a-list-box-control-and-select-items-from-it"></a>Creare un controllo casella di riepilogo e selezionare i relativi elementi

Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'

$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)

$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)

$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80

[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')

$form.Controls.Add($listBox)

$form.Topmost = $true

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.

- **Testo** Questo valore diventa il titolo della finestra.

- **Size.** Le dimensioni del modulo, in pixel. Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.

- **StartingPosition.** Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.
  Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

```powershell
$form.Text = 'Select a Computer'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $okButton
$form.Controls.Add($okButton)
```

Analogamente, creare un pulsante **Cancel**. Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare. In questo caso, si vuole che gli utenti selezionino un computer.

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please select a computer:'
$form.Controls.Add($label)
```

Aggiungere il controllo, in questo caso una casella di riepilogo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta. Oltre alle caselle di riepilogo, è possibile applicare molti altri controlli. Per altri controlli, vedere [Spazio dei nomi System.Windows.Forms](/dotnet/api/system.windows.forms) in MSDN.

```powershell
$listBox = New-Object System.Windows.Forms.ListBox
$listBox.Location = New-Object System.Drawing.Point(10,40)
$listBox.Size = New-Object System.Drawing.Size(260,20)
$listBox.Height = 80
```

Nella sezione seguente, specificare i valori che si vuole vengano visualizzati nella casella di riepilogo.

> [!NOTE]
> La casella di riepilogo creata da questo script consente di effettuare un'unica selezione. Per creare un controllo casella di riepilogo che consenta di eseguire selezioni multiple, specificare un valore per la proprietà **SelectionMode**, in modo simile al seguente: `$listBox.SelectionMode = 'MultiExtended'`. Per altre informazioni, vedere [Caselle di riepilogo a selezione multipla](Multiple-selection-List-Boxes.md).

```powershell
[void] $listBox.Items.Add('atl-dc-001')
[void] $listBox.Items.Add('atl-dc-002')
[void] $listBox.Items.Add('atl-dc-003')
[void] $listBox.Items.Add('atl-dc-004')
[void] $listBox.Items.Add('atl-dc-005')
[void] $listBox.Items.Add('atl-dc-006')
[void] $listBox.Items.Add('atl-dc-007')
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

Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona un'opzione della casella di riepilogo e quindi fa clic su **OK** o preme **INVIO**.

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a>Vedere anche

- [GitHub: WinFormsExampleUpdates di Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Suggerimento della settimana su Windows PowerShell: Selezione di elementi di una casella di riepilogo](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730949(v=technet.10))
