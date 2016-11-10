---
title: Creazione di una casella di input personalizzata
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 0b12e56c-299f-40ee-afbf-d30d23ed2565
translationtype: Human Translation
ms.sourcegitcommit: f891988cce205b5729d0da6c4ce23da5fbd53b7f
ms.openlocfilehash: 6fffd6406a7570e06fc4403cd238804ef0f51360

---

# Creazione di una casella di input personalizzata
Scrivere lo script di una casella di input grafica personalizzata usando le funzionalità di creazione moduli di Microsoft .NET Framework in Windows PowerShell 3.0 e versioni successive.

## Creare una casella di input grafica personalizzata
Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"

$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)

$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)

$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label) 

$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox) 

$form.Topmost = $True

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**. Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.

```
$form = New-Object System.Windows.Forms.Form
```

Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.

-   **Text.** Questo valore diventa il titolo della finestra.

-   **Size.** Le dimensioni del modulo, in pixel. Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.

-   **StartingPosition.** Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente. Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto. Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

Creare quindi un pulsante **OK** per il modulo. Specificare le dimensioni e il comportamento del pulsante **OK**. In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro. L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel. Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

Analogamente, creare un pulsante **Cancel**. Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please enter the information in the space below:"
$form.Controls.Add($label)
```

Aggiungere il controllo, in questo caso una casella di testo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta. Oltre alle caselle di testo, è possibile applicare molti altri controlli. Per altre informazioni, vedere [Spazio dei nomi System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.

```
$textBox = New-Object System.Windows.Forms.TextBox 
$textBox.Location = New-Object System.Drawing.Point(10,40) 
$textBox.Size = New-Object System.Drawing.Size(260,20) 
$form.Controls.Add($textBox)
```

Impostare la proprietà **Topmost** su **$True** per forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.

```
$form.Topmost = $True
```

Aggiungere quindi questa riga di codice per attivare il modulo e impostare lo stato attivo sulla casella di testo creata.

```
$form.Add_Shown({$textBox.Select()})
```

Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.

```
$result = $form.ShowDialog()
```

Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente immette testo nella casella e quindi fa clic su **OK** o preme **INVIO**.

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## Vedere anche
- [Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?](http://go.microsoft.com/fwlink/?LinkId=506644)
- [GitHub: WinFormsExampleUpdates di Dave Wyatt](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [Suggerimento della settimana su Windows PowerShell: Creazione di una casella di input personalizzata](http://technet.microsoft.com/library/ff730941.aspx)




<!--HONumber=Oct16_HO3-->


