---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione di una casella di input personalizzata
ms.openlocfilehash: ff0588b44169bc276e2833254cec60eda759e2c8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "77706190"
---
# <a name="creating-a-custom-input-box"></a><span data-ttu-id="e753e-103">Creazione di una casella di input personalizzata</span><span class="sxs-lookup"><span data-stu-id="e753e-103">Creating a Custom Input Box</span></span>

<span data-ttu-id="e753e-104">Scrivere lo script di una casella di input grafica personalizzata usando le funzionalità di creazione moduli di Microsoft .NET Framework in Windows PowerShell 3.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="e753e-104">Script a graphical custom input box by using Microsoft .NET Framework form-building features in Windows PowerShell 3.0 and later releases.</span></span>

## <a name="create-a-custom-graphical-input-box"></a><span data-ttu-id="e753e-105">Creare una casella di input grafica personalizzata</span><span class="sxs-lookup"><span data-stu-id="e753e-105">Create a custom, graphical input box</span></span>

<span data-ttu-id="e753e-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="e753e-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```powershell
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form
$form.Text = 'Data Entry Form'
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

<span data-ttu-id="e753e-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="e753e-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="e753e-108">Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="e753e-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="e753e-109">Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="e753e-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="e753e-110">**Testo**</span><span class="sxs-lookup"><span data-stu-id="e753e-110">**Text.**</span></span> <span data-ttu-id="e753e-111">Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="e753e-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="e753e-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="e753e-112">**Size.**</span></span> <span data-ttu-id="e753e-113">Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="e753e-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="e753e-114">Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="e753e-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="e753e-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="e753e-115">**StartingPosition.**</span></span> <span data-ttu-id="e753e-116">Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.</span><span class="sxs-lookup"><span data-stu-id="e753e-116">This optional property is set to **CenterScreen** in the preceding script.</span></span>
  <span data-ttu-id="e753e-117">Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="e753e-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="e753e-118">Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="e753e-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```powershell
$form.Text = 'Data Entry Form'
$form.Size = New-Object System.Drawing.Size(300,200)
$form.StartPosition = 'CenterScreen'
```

<span data-ttu-id="e753e-119">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="e753e-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="e753e-120">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="e753e-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="e753e-121">In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="e753e-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="e753e-122">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="e753e-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="e753e-123">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="e753e-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```powershell
$okButton = New-Object System.Windows.Forms.Button
$okButton.Location = New-Object System.Drawing.Point(75,120)
$okButton.Size = New-Object System.Drawing.Size(75,23)
$okButton.Text = 'OK'
$okButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="e753e-124">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="e753e-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="e753e-125">Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="e753e-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```powershell
$cancelButton = New-Object System.Windows.Forms.Button
$cancelButton.Location = New-Object System.Drawing.Point(150,120)
$cancelButton.Size = New-Object System.Drawing.Size(75,23)
$cancelButton.Text = 'Cancel'
$cancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $cancelButton
$form.Controls.Add($cancelButton)
```

<span data-ttu-id="e753e-126">Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.</span><span class="sxs-lookup"><span data-stu-id="e753e-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```powershell
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20)
$label.Size = New-Object System.Drawing.Size(280,20)
$label.Text = 'Please enter the information in the space below:'
$form.Controls.Add($label)
```

<span data-ttu-id="e753e-127">Aggiungere il controllo, in questo caso una casella di testo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="e753e-127">Add the control (in this case, a text box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="e753e-128">Oltre alle caselle di testo, è possibile applicare molti altri controlli. Per altre informazioni, vedere [Spazio dei nomi System.Windows.Forms](/dotnet/api/system.windows.forms) in MSDN.</span><span class="sxs-lookup"><span data-stu-id="e753e-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](/dotnet/api/system.windows.forms) on MSDN.</span></span>

```powershell
$textBox = New-Object System.Windows.Forms.TextBox
$textBox.Location = New-Object System.Drawing.Point(10,40)
$textBox.Size = New-Object System.Drawing.Size(260,20)
$form.Controls.Add($textBox)
```

<span data-ttu-id="e753e-129">Impostare la proprietà **Topmost** su **$true** per forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.</span><span class="sxs-lookup"><span data-stu-id="e753e-129">Set the **Topmost** property to **$true** to force the window to open atop other open windows and dialog boxes.</span></span>

```powershell
$form.Topmost = $true
```

<span data-ttu-id="e753e-130">Aggiungere quindi questa riga di codice per attivare il modulo e impostare lo stato attivo sulla casella di testo creata.</span><span class="sxs-lookup"><span data-stu-id="e753e-130">Next, add this line of code to activate the form, and set the focus to the text box that you created.</span></span>

```powershell
$form.Add_Shown({$textBox.Select()})
```

<span data-ttu-id="e753e-131">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="e753e-131">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="e753e-132">Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente immette testo nella casella e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="e753e-132">Finally, the code inside the **If** block instructs Windows what to do with the form after users provide text in the text box, and then click the **OK** button or press the **Enter** key.</span></span>

```powershell
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $textBox.Text
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="e753e-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e753e-133">See Also</span></span>

- <span data-ttu-id="e753e-134">[GitHub: WinFormsExampleUpdates di Dave Wyatt](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span><span class="sxs-lookup"><span data-stu-id="e753e-134">[GitHub: Dave Wyatt's WinFormsExampleUpdates](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730941(v=technet.10))</span></span>
- [<span data-ttu-id="e753e-135">Suggerimento della settimana su Windows PowerShell: Creazione di una casella di input personalizzata</span><span class="sxs-lookup"><span data-stu-id="e753e-135">Windows PowerShell Tip of the Week:  Creating a Custom Input Box</span></span>](https://technet.microsoft.com/library/ff730941.aspx)
