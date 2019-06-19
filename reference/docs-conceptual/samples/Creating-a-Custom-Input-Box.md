---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione di una casella di input personalizzata
ms.openlocfilehash: 9c1c3c72482157e849c0259e7d2e25ed969a4aab
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030236"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="a18a8-103">Creazione di una casella di input personalizzata</span><span class="sxs-lookup"><span data-stu-id="a18a8-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="a18a8-104">Scrivere lo script di una casella di input grafica personalizzata usando le funzionalità di creazione moduli di Microsoft .NET Framework in Windows PowerShell 3.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="a18a8-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="a18a8-105">Creare una casella di input grafica personalizzata</span><span class="sxs-lookup"><span data-stu-id="a18a8-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="a18a8-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="a18a8-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)

$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)

$form.Topmost = $true

$form.Add_Shown({$textBox.Select()})
$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

<span data-ttu-id="a18a8-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="a18a8-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="a18a8-108">Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="a18a8-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="a18a8-109">Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="a18a8-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="a18a8-110">**Testo**</span><span class="sxs-lookup"><span data-stu-id="a18a8-110">**Text.**</span></span> <span data-ttu-id="a18a8-111">Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="a18a8-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="a18a8-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="a18a8-112">**Size.**</span></span> <span data-ttu-id="a18a8-113">Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="a18a8-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="a18a8-114">Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="a18a8-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="a18a8-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="a18a8-115">**StartingPosition.**</span></span> <span data-ttu-id="a18a8-116">Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.</span><span class="sxs-lookup"><span data-stu-id="a18a8-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="a18a8-117">Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="a18a8-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="a18a8-118">Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="a18a8-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="a18a8-119">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="a18a8-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="a18a8-120">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="a18a8-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="a18a8-121">In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="a18a8-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="a18a8-122">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="a18a8-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="a18a8-123">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="a18a8-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = 'OK'
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="a18a8-124">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="a18a8-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="a18a8-125">Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="a18a8-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = 'Cancel'
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="a18a8-126">Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.</span><span class="sxs-lookup"><span data-stu-id="a18a8-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="a18a8-127">Aggiungere il controllo, in questo caso una casella di testo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="a18a8-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="a18a8-128">Oltre alle caselle di testo, è possibile applicare molti altri controlli. Per altre informazioni, vedere [Spazio dei nomi System.Windows.Forms](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.</span><span class="sxs-lookup"><span data-stu-id="a18a8-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](https://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="a18a8-129">Impostare la proprietà **Topmost** su **$true** per forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.</span><span class="sxs-lookup"><span data-stu-id="a18a8-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="a18a8-130">Aggiungere quindi questa riga di codice per attivare il modulo e impostare lo stato attivo sulla casella di testo creata.</span><span class="sxs-lookup"><span data-stu-id="a18a8-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="a18a8-131">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="a18a8-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="a18a8-132">Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente immette testo nella casella e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="a18a8-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="a18a8-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="a18a8-133">See Also</span></span>

- [<span data-ttu-id="a18a8-134">Hey Scripting Guy:  Perché questi esempi di GUI di PowerShell non funzionano?</span><span class="sxs-lookup"><span data-stu-id="a18a8-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](https://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="a18a8-135">GitHub: WinFormsExampleUpdates di Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="a18a8-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="a18a8-136">[Windows PowerShell Tip of the Week:  Creating a Custom Input Box](https://technet.microsoft.com/library/ff730941.aspx) (Suggerimento della settimana per Windows PowerShell: Creazione di una casella di input personalizzata)</span><span class="sxs-lookup"><span data-stu-id="a18a8-136">[Windows PowerShell Tip of the Week:  Creating a Custom Input Box](https://technet.microsoft.com/library/ff730941.aspx)</span></span>
