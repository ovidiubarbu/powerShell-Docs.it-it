---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Creazione di un controllo grafico di selezione data
ms.assetid: c1cb722c-41e9-4baa-be83-59b4653222e9
ms.openlocfilehash: 5cb952264092d345945318968cf0b3028b11f3e9
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="54db5-103">Creazione di un controllo grafico di selezione data</span><span class="sxs-lookup"><span data-stu-id="54db5-103">Creating a Graphical Date Picker</span></span>
<span data-ttu-id="54db5-104">Usare Windows PowerShell 3.0 e versioni successive per creare un modulo con un controllo grafico di tipo calendario che consente agli utenti di selezionare un giorno del mese.</span><span class="sxs-lookup"><span data-stu-id="54db5-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="54db5-105">Creare un controllo grafico di selezione data</span><span class="sxs-lookup"><span data-stu-id="54db5-105">Create a graphical date-picker control</span></span>
<span data-ttu-id="54db5-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="54db5-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="54db5-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="54db5-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="54db5-108">Viene quindi avviata una nuova istanza della classe **Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="54db5-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```
$form = New-Object Windows.Forms.Form
```

<span data-ttu-id="54db5-109">Dopo aver creato un'istanza della classe Form, assegnare valori alle tre proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="54db5-109">After you create an instance of the Form class, assign values to three properties of this class.</span></span>

-   <span data-ttu-id="54db5-110">**Testo**</span><span class="sxs-lookup"><span data-stu-id="54db5-110">**Text.**</span></span> <span data-ttu-id="54db5-111">Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="54db5-111">This becomes the title of the window.</span></span>

-   <span data-ttu-id="54db5-112">**Size.**</span><span class="sxs-lookup"><span data-stu-id="54db5-112">**Size.**</span></span> <span data-ttu-id="54db5-113">Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="54db5-113">This is the size of the form, in pixels.</span></span> <span data-ttu-id="54db5-114">Lo script precedente crea un modulo di 243 pixel in larghezza per 230 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="54db5-114">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

-   <span data-ttu-id="54db5-115">**StartingPosition.**</span><span class="sxs-lookup"><span data-stu-id="54db5-115">**StartingPosition.**</span></span> <span data-ttu-id="54db5-116">Questa proprietà facoltativa è impostata su **CenterScreen** nello script precedente.</span><span class="sxs-lookup"><span data-stu-id="54db5-116">This optional property is set to **CenterScreen** in the preceding script.</span></span> <span data-ttu-id="54db5-117">Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="54db5-117">If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="54db5-118">Impostando **StartingPosition** su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="54db5-118">By setting the **StartingPosition** to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

```
$form.Text = "Select a Date" 
$form.Size = New-Object Drawing.Size @(243,230) 
$form.StartPosition = "CenterScreen"
```

<span data-ttu-id="54db5-119">Quindi creare e aggiungere un controllo calendario nel modulo.</span><span class="sxs-lookup"><span data-stu-id="54db5-119">Next, create and then add a calendar control in your form.</span></span> <span data-ttu-id="54db5-120">In questo esempio il giorno corrente non è evidenziato né cerchiato.</span><span class="sxs-lookup"><span data-stu-id="54db5-120">In this example, the current day is not highlighted or circled.</span></span> <span data-ttu-id="54db5-121">Gli utenti possono selezionare un solo giorno del calendario alla volta.</span><span class="sxs-lookup"><span data-stu-id="54db5-121">Users can select only one day on the calendar at one time.</span></span>

```
$calendar = New-Object System.Windows.Forms.MonthCalendar 
$calendar.ShowTodayCircle = $False
$calendar.MaxSelectionCount = 1
$form.Controls.Add($calendar)
```

<span data-ttu-id="54db5-122">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="54db5-122">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="54db5-123">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="54db5-123">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="54db5-124">In questo esempio il pulsante è posizionato a una distanza di 165 pixel dal bordo superiore del modulo e di 38 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="54db5-124">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="54db5-125">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="54db5-125">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="54db5-126">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="54db5-126">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

```
$OKButton = New-Object System.Windows.Forms.Button
$OKButton.Location = New-Object System.Drawing.Point(38,165)
$OKButton.Size = New-Object System.Drawing.Size(75,23)
$OKButton.Text = "OK"
$OKButton.DialogResult = [System.Windows.Forms.DialogResult]::OK
$form.AcceptButton = $OKButton
$form.Controls.Add($OKButton)
```

<span data-ttu-id="54db5-127">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="54db5-127">Similarly, you create a **Cancel** button.</span></span> <span data-ttu-id="54db5-128">Il pulsante **Cancel** è posizionato a 165 pixel di distanza dal bordo superiore, ma a 113 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="54db5-128">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

```
$CancelButton = New-Object System.Windows.Forms.Button
$CancelButton.Location = New-Object System.Drawing.Point(113,165)
$CancelButton.Size = New-Object System.Drawing.Size(75,23)
$CancelButton.Text = "Cancel"
$CancelButton.DialogResult = [System.Windows.Forms.DialogResult]::Cancel
$form.CancelButton = $CancelButton
$form.Controls.Add($CancelButton)
```

<span data-ttu-id="54db5-129">Impostare la proprietà **Topmost** su **$True** per forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.</span><span class="sxs-lookup"><span data-stu-id="54db5-129">Set the **Topmost** property to **$True** to force the window to open atop other open windows and dialog boxes.</span></span>

```
$form.Topmost = $True
```

<span data-ttu-id="54db5-130">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="54db5-130">Add the following line of code to display the form in Windows.</span></span>

```
$result = $form.ShowDialog()
```

<span data-ttu-id="54db5-131">Infine, il codice all'interno del blocco **If** indica a Windows cosa fare con il modulo dopo che l'utente seleziona un giorno del calendario e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="54db5-131">Finally, the code inside the **If** block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="54db5-132">Windows PowerShell visualizza la data selezionata.</span><span class="sxs-lookup"><span data-stu-id="54db5-132">Windows PowerShell displays the selected date to users.</span></span>

```
if ($result -eq [System.Windows.Forms.DialogResult]::OK)
{
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="54db5-133">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="54db5-133">See Also</span></span>
- [<span data-ttu-id="54db5-134">Blog Hey Scripting Guy: perché questi esempi di GUI di PowerShell non funzionano?</span><span class="sxs-lookup"><span data-stu-id="54db5-134">Hey Scripting Guy:  Why don’t these PowerShell GUI examples work?</span></span>](http://go.microsoft.com/fwlink/?LinkId=506644)
- [<span data-ttu-id="54db5-135">GitHub: WinFormsExampleUpdates di Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="54db5-135">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- [<span data-ttu-id="54db5-136">Suggerimento della settimana su Windows PowerShell: Creazione di un controllo grafico di selezione data</span><span class="sxs-lookup"><span data-stu-id="54db5-136">Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker</span></span>](http://technet.microsoft.com/library/ff730942.aspx)

