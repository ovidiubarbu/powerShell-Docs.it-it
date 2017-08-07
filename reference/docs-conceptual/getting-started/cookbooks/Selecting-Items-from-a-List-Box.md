---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Selezione di elementi di una casella di riepilogo
ms.assetid: 327c7cc5-21d0-4ace-b151-aa1491d1d3c2
ms.openlocfilehash: 39a5375b7f00c4b8332b28bf6ead011c4b21883e
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="selecting-items-from-a-list-box"></a><span data-ttu-id="31b27-103">Selezione di elementi di una casella di riepilogo</span><span class="sxs-lookup"><span data-stu-id="31b27-103">Selecting Items from a List Box</span></span>
<span data-ttu-id="31b27-104">Usare Windows PowerShell 3.0 e versioni successive per creare una finestra di dialogo che consente agli utenti di selezionare gli elementi da un controllo casella di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="31b27-104">Use Windows PowerShell 3.0 and later releases to create a dialog box that lets users select items from a list box control.</span></span>

## <a name="create-a-list-box-control-and-select-items-from-it"></a><span data-ttu-id="31b27-105">Creare un controllo casella di riepilogo e selezionare i relativi elementi</span><span class="sxs-lookup"><span data-stu-id="31b27-105">Create a list box control, and select items from it</span></span>
<span data-ttu-id="31b27-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="31b27-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing

$form = New-Object System.Windows.Forms.Form 
$form.Text = "Select a Computer"
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
$label.Text = "Please select a computer:"
$form.Controls.Add($label) 

$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80

[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")

$form.Controls.Add($listBox) 

$form.Topmost = $True

$result = $form.ShowDialog()

if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

<span data-ttu-id="31b27-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="31b27-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="31b27-108">Viene quindi avviata una nuova istanza della classe **System.Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="31b27-108">You then start a new instance of the .NET Framework class **System.Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
Add-Type -AssemblyName System.Windows.Forms
Add-Type -AssemblyName System.Drawing
```

<span data-ttu-id="31b27-109">Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="31b27-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

-   <span data-ttu-id="31b27-110">**Testo**</span><span class="sxs-lookup"><span data-stu-id="31b27-110">**Text.**</span></span> <span data-ttu-id="31b27-111">Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="31b27-111">This becomes the title of the window.</span></span>

-   <span data-ttu-id="31b27-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="31b27-112">**Size.**</span></span> <span data-ttu-id="31b27-113">Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="31b27-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="31b27-114">Lo script precedente crea un modulo di 300 pixel in larghezza per 200 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="31b27-114">The preceding script creates a form that’s 300 pixels wide by 200 pixels tall.</span></span>

-   <span data-ttu-id="31b27-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="31b27-115">**StartingPosition.**</span></span> <span data-ttu-id="31b27-116">Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.</span><span class="sxs-lookup"><span data-stu-id="31b27-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="31b27-117">Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="31b27-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="31b27-118">Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="31b27-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Computer"
$form.Size = New-Object System.Drawing.Size(300,200) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="31b27-119">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="31b27-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="31b27-120">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="31b27-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="31b27-121">In questo esempio il pulsante è posizionato a una distanza di 120 pixel dal bordo superiore del modulo e di 75 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="31b27-121">In this example, the button position is 120 pixels from the form’s top edge, and 75 pixels from the left edge.</span></span> <span data-ttu-id="31b27-122">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="31b27-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="31b27-123">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="31b27-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(75,120)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="31b27-124">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="31b27-124">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="31b27-125">Il pulsante **Cancel** è posizionato a 120 pixel di distanza dal bordo superiore, ma a 150 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="31b27-125">The **Cancel** button is 120 pixels from the top, but 150 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(150,120)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="31b27-126">Fornire quindi il testo di un'etichetta nella finestra che descrive le informazioni che gli utenti dovranno specificare.</span><span class="sxs-lookup"><span data-stu-id="31b27-126">Next, provide label text on your window that describes the information you want users to provide.</span></span> <span data-ttu-id="31b27-127">In questo caso, si vuole che gli utenti selezionino un computer.</span><span class="sxs-lookup"><span data-stu-id="31b27-127">In this case, you want users to select a computer.</span></span>

```
$label = New-Object System.Windows.Forms.Label
$label.Location = New-Object System.Drawing.Point(10,20) 
$label.Size = New-Object System.Drawing.Size(280,20) 
$label.Text = "Please select a computer:"
$form.Controls.Add($label)
```

<span data-ttu-id="31b27-128">Aggiungere il controllo, in questo caso una casella di riepilogo, che consente agli utenti di specificare le informazioni descritte nel testo dell'etichetta.</span><span class="sxs-lookup"><span data-stu-id="31b27-128">Add the control (in this case, a list box) that lets users provide the information you’ve described in your label text.</span></span> <span data-ttu-id="31b27-129">Oltre alle caselle di riepilogo, è possibile applicare molti altri controlli. Per altri controlli, vedere [Spazio dei nomi System.Windows.Forms](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) in MSDN.</span><span class="sxs-lookup"><span data-stu-id="31b27-129">There are many other controls you can apply besides list boxes; for more controls, see [System.Windows.Forms Namespace](http://msdn.microsoft.com/library/k50ex0x9(v=vs.110).aspx) on MSDN.</span></span>

```
$listBox = New-Object System.Windows.Forms.ListBox 
$listBox.Location = New-Object System.Drawing.Point(10,40) 
$listBox.Size = New-Object System.Drawing.Size(260,20) 
$listBox.Height = 80
```

<span data-ttu-id="31b27-130">Nella sezione seguente, specificare i valori che si vuole vengano visualizzati nella casella di riepilogo.</span><span class="sxs-lookup"><span data-stu-id="31b27-130">In the next section, you specify the values you want the list box to display to users.</span></span>

> [!NOTE]
> <span data-ttu-id="31b27-131">La casella di riepilogo creata da questo script consente di effettuare un'unica selezione.</span><span class="sxs-lookup"><span data-stu-id="31b27-131">The list box created by this script allows only one selection.</span></span> <span data-ttu-id="31b27-132">Per creare un controllo casella di riepilogo che consenta di eseguire selezioni multiple, specificare un valore per la proprietà **SelectionMode**, in modo simile al seguente:  `$listBox.SelectionMode = "MultiExtended"`.</span><span class="sxs-lookup"><span data-stu-id="31b27-132">To create a list box control that allows multiple selections, specify a value for the **SelectionMode** property, similarly to the following:  `$listBox.SelectionMode = "MultiExtended"`.</span></span> <span data-ttu-id="31b27-133">Per altre informazioni, vedere [Caselle di riepilogo a selezione multipla](Multiple-selection-List-Boxes.md).</span><span class="sxs-lookup"><span data-stu-id="31b27-133">For more information, see [Multiple-selection List Boxes](Multiple-selection-List-Boxes.md).</span></span>

```
[void] $listBox.Items.Add("atl-dc-001")
[void] $listBox.Items.Add("atl-dc-002")
[void] $listBox.Items.Add("atl-dc-003")
[void] $listBox.Items.Add("atl-dc-004")
[void] $listBox.Items.Add("atl-dc-005")
[void] $listBox.Items.Add("atl-dc-006")
[void] $listBox.Items.Add("atl-dc-007")
```

<span data-ttu-id="31b27-134">Aggiungere il controllo casella di riepilogo nel modulo e indicare a Windows di aprire il modulo sopra altre finestre e finestre di dialogo.</span><span class="sxs-lookup"><span data-stu-id="31b27-134">Add the list box control to your form, and instruct Windows to open the form atop other windows and dialog boxes when it’s opened.</span></span>

```
$form.Controls.Add($listBox) 
$form.Topmost = $True
```

<span data-ttu-id="31b27-135">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="31b27-135">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="31b27-136">Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona un'opzione della casella di riepilogo e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="31b27-136">Finally, the code inside the **If** block instructs Windows what to do with the form after users select an option from the list box, and then click the **OK** button or press the **Enter** key.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $x = $listBox.SelectedItem
    $x
}
```

## <a name="see-also"></a><span data-ttu-id="31b27-137">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="31b27-137">See Also</span></span>
- [<span data-ttu-id="31b27-138">Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?</span><span class="sxs-lookup"><span data-stu-id="31b27-138">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="31b27-139">GitHub: WinFormsExampleUpdates di Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="31b27-139">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="31b27-140">Suggerimento della settimana su Windows PowerShell: Selezione di elementi di una casella di riepilogo</span><span class="sxs-lookup"><span data-stu-id="31b27-140">Windows PowerShell Tip of the Week:  Selecting Items from a List Box</span></span>](http://technet.microsoft.com/library/ff730949.aspx)

