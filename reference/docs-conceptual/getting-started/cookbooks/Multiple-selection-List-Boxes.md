---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Caselle di riepilogo a selezione multipla
ms.assetid: f74cd5d9-da57-4802-b614-0b194a7bc8f8
ms.openlocfilehash: 122014888bc5cf93c1c709b9d534d572037f5ffe
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="multiple-selection-list-boxes"></a><span data-ttu-id="43cdc-103">Caselle di riepilogo a selezione multipla</span><span class="sxs-lookup"><span data-stu-id="43cdc-103">Multiple-selection List Boxes</span></span>
<span data-ttu-id="43cdc-104">Usare Windows PowerShell 3.0 e versioni successive per creare un controllo casella di riepilogo a selezione multipla in un Windows Form personalizzato.</span><span class="sxs-lookup"><span data-stu-id="43cdc-104">Use Windows PowerShell 3.0 and later releases to create a multiple-selection list box control in a custom Windows Form.</span></span>

## <a name="create-list-box-controls-that-allow-multiple-selections"></a><span data-ttu-id="43cdc-105">Creare controlli casella di riepilogo che consentono selezioni multiple</span><span class="sxs-lookup"><span data-stu-id="43cdc-105">Create list box controls that allow multiple selections</span></span>
<span data-ttu-id="43cdc-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="43cdc-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 

$listBox.SelectionMode = "MultiExtended"

[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")

$listBox.Height = 70
$form.Controls.Add($listBox) 
$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

<span data-ttu-id="43cdc-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="43cdc-108">Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="43cdc-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object System.Windows.Forms.Form
```

<span data-ttu-id="43cdc-109">Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="43cdc-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

- <span data-ttu-id="43cdc-110">**Testo**</span><span class="sxs-lookup"><span data-stu-id="43cdc-110">**Text.**</span></span> <span data-ttu-id="43cdc-111">Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="43cdc-111">This becomes the title of the window.</span></span>

- <span data-ttu-id="43cdc-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="43cdc-112">**Size.**</span></span> <span data-ttu-id="43cdc-113">Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="43cdc-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="43cdc-114">Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="43cdc-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

- <span data-ttu-id="43cdc-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="43cdc-115">**StartingPosition.**</span></span> <span data-ttu-id="43cdc-116">Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.</span><span class="sxs-lookup"><span data-stu-id="43cdc-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="43cdc-117">Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="43cdc-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="43cdc-118">Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="43cdc-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Data Entry Form"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="43cdc-119">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="43cdc-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="43cdc-120">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="43cdc-121">In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="43cdc-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="43cdc-122">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="43cdc-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="43cdc-123">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="43cdc-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Size(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="43cdc-124">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="43cdc-125">Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="43cdc-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="43cdc-126">Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.</span><span class="sxs-lookup"><span data-stu-id="43cdc-126">Next, provide label text on your window that describes the information you want users to provide.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please make a selection from the list below:"
$form.Controls.Add($label)
```

<span data-ttu-id="43cdc-127">Aggiungere il controllo, in questo caso una casella di riepilogo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="43cdc-127">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="43cdc-128">Oltre alle caselle di testo, è possibile applicare molti altri controlli. Per altre informazioni, vedere [Spazio dei nomi System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.</span><span class="sxs-lookup"><span data-stu-id="43cdc-128">There are many other controls you can apply besides text boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.Listbox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20)
```


<span data-ttu-id="43cdc-129">Ecco come specificare che si vuole consentire agli utenti di selezionare più valori nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="43cdc-129">Here’s how you specify that you want to allow users to select multiple values from the list.</span></span>

```
$listBox.SelectionMode = "MultiExtended"
```

<span data-ttu-id="43cdc-130">Nella sezione seguente, specificare i valori che si vuole vengano visualizzati nella casella di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="43cdc-130">In the next section, you specify the values you want the list box to display to users.</span></span>

```
[void] $listBox.Items.Add("Item 1")
[void] $listBox.Items.Add("Item 2")
[void] $listBox.Items.Add("Item 3")
[void] $listBox.Items.Add("Item 4")
[void] $listBox.Items.Add("Item 5")
```

<span data-ttu-id="43cdc-131">Specificare l'altezza massima del controllo casella di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="43cdc-131">Specify the maximum height of the list box control.</span></span>

```
$listBox.Height = 70
```

<span data-ttu-id="43cdc-132">Aggiungere il controllo casella di riepilogo nel modulo e indicare a Windows di aprire il modulo sopra altre finestre e finestre di dialogo.</span><span class="sxs-lookup"><span data-stu-id="43cdc-132">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="43cdc-133">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="43cdc-133">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="43cdc-134">Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona una o più opzioni della casella di riepilogo e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="43cdc-134">Finally, the code inside the **If** block instructs Windows what to do with the form after users select one or more options from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItems
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="43cdc-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="43cdc-135">See Also</span></span>
- [<span data-ttu-id="43cdc-136">Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?</span><span class="sxs-lookup"><span data-stu-id="43cdc-136">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="43cdc-137">GitHub: WinFormsExampleUpdates di Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="43cdc-137">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="43cdc-138">Suggerimento della settimana su Windows PowerShell: caselle di riepilogo a selezione multipla e altro ancora!</span><span class="sxs-lookup"><span data-stu-id="43cdc-138">Windows PowerShell Tip of the Week:  Multi-Select List Boxes - And More!</span></span>](http://technet.microsoft.com/library/ff730950.aspx)

