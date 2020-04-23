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
# <a name="creating-a-graphical-date-picker"></a><span data-ttu-id="7df15-103">Creazione di un controllo grafico di selezione data</span><span class="sxs-lookup"><span data-stu-id="7df15-103">Creating a Graphical Date Picker</span></span>

<span data-ttu-id="7df15-104">Usare Windows PowerShell 3.0 e versioni successive per creare un modulo con un controllo grafico di tipo calendario che consente agli utenti di selezionare un giorno del mese.</span><span class="sxs-lookup"><span data-stu-id="7df15-104">Use Windows PowerShell 3.0 and later releases to create a form with a graphical, calendar-style control that lets users select a day of the month.</span></span>

## <a name="create-a-graphical-date-picker-control"></a><span data-ttu-id="7df15-105">Creare un controllo grafico di selezione data</span><span class="sxs-lookup"><span data-stu-id="7df15-105">Create a graphical date-picker control</span></span>

<span data-ttu-id="7df15-106">Copiare e incollare il codice seguente in Windows PowerShell ISE, quindi salvarlo come script di Windows PowerShell (ps1).</span><span class="sxs-lookup"><span data-stu-id="7df15-106">Copy and then paste the following into Windows PowerShell ISE, and then save it as a Windows PowerShell script (.ps1).</span></span>

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

<span data-ttu-id="7df15-107">Lo script inizia caricando due classi di .NET Framework: **System.Drawing** e **System.Windows.Forms**.</span><span class="sxs-lookup"><span data-stu-id="7df15-107">The script begins by loading two .NET Framework classes: **System.Drawing** and **System.Windows.Forms**.</span></span> <span data-ttu-id="7df15-108">Viene quindi avviata una nuova istanza della classe **Windows.Forms.Form** di .NET Framework che fornisce una finestra o un modulo vuoto in cui è possibile iniziare ad aggiungere controlli.</span><span class="sxs-lookup"><span data-stu-id="7df15-108">You then start a new instance of the .NET Framework class **Windows.Forms.Form**; that provides a blank form or window to which you can start adding controls.</span></span>

```powershell
$form = New-Object Windows.Forms.Form -Property @{
    StartPosition = [Windows.Forms.FormStartPosition]::CenterScreen
    Size          = New-Object Drawing.Size 243, 230
    Text          = 'Select a Date'
    Topmost       = $true
}
```

<span data-ttu-id="7df15-109">In questo esempio vengono assegnati valori a quattro proprietà di questa classe usando la proprietà **Property** e la tabella hash.</span><span class="sxs-lookup"><span data-stu-id="7df15-109">This example assigns values to four properties of this class by using the **Property** property and hashtable.</span></span>

1. <span data-ttu-id="7df15-110">**StartPosition**: Se non viene aggiunta, Windows seleziona una posizione quando il modulo viene aperto.</span><span class="sxs-lookup"><span data-stu-id="7df15-110">**StartPosition**: If you don’t add this property, Windows selects a location when the form is opened.</span></span> <span data-ttu-id="7df15-111">Impostando questa proprietà su **CenterScreen**, il modulo viene automaticamente visualizzato al centro dello schermo ogni volta che viene caricato.</span><span class="sxs-lookup"><span data-stu-id="7df15-111">By setting this property to **CenterScreen**, you’re automatically displaying the form in the middle of the screen each time it loads.</span></span>

2. <span data-ttu-id="7df15-112">**Size**: Le dimensioni del modulo, in pixel.</span><span class="sxs-lookup"><span data-stu-id="7df15-112">**Size**: This is the size of the form, in pixels.</span></span>
   <span data-ttu-id="7df15-113">Lo script precedente crea un modulo di 243 pixel in larghezza per 230 pixel in altezza.</span><span class="sxs-lookup"><span data-stu-id="7df15-113">The preceding script creates a form that’s 243 pixels wide by 230 pixels tall.</span></span>

3. <span data-ttu-id="7df15-114">**Text**: Questo valore diventa il titolo della finestra.</span><span class="sxs-lookup"><span data-stu-id="7df15-114">**Text**: This becomes the title of the window.</span></span>

4. <span data-ttu-id="7df15-115">**Topmost**: impostando questa proprietà su `$true` è possibile forzare l'apertura della finestra sopra altre finestre e finestre di dialogo aperte.</span><span class="sxs-lookup"><span data-stu-id="7df15-115">**Topmost**: By setting this property to `$true`, you can force the window to open atop other open windows and dialog boxes.</span></span>

<span data-ttu-id="7df15-116">Quindi creare e aggiungere un controllo calendario nel modulo.</span><span class="sxs-lookup"><span data-stu-id="7df15-116">Next, create and then add a calendar control in your form.</span></span>
<span data-ttu-id="7df15-117">In questo esempio il giorno corrente non è evidenziato né cerchiato.</span><span class="sxs-lookup"><span data-stu-id="7df15-117">In this example, the current day is not highlighted or circled.</span></span>
<span data-ttu-id="7df15-118">Gli utenti possono selezionare un solo giorno del calendario alla volta.</span><span class="sxs-lookup"><span data-stu-id="7df15-118">Users can select only one day on the calendar at one time.</span></span>

```powershell
$calendar = New-Object Windows.Forms.MonthCalendar -Property @{
    ShowTodayCircle   = $false
    MaxSelectionCount = 1
}
$form.Controls.Add($calendar)
```

<span data-ttu-id="7df15-119">Creare quindi un pulsante **OK** per il modulo.</span><span class="sxs-lookup"><span data-stu-id="7df15-119">Next, create an **OK** button for your form.</span></span> <span data-ttu-id="7df15-120">Specificare le dimensioni e il comportamento del pulsante **OK**.</span><span class="sxs-lookup"><span data-stu-id="7df15-120">Specify the size and behavior of the **OK** button.</span></span> <span data-ttu-id="7df15-121">In questo esempio il pulsante è posizionato a una distanza di 165 pixel dal bordo superiore del modulo e di 38 pixel dal bordo sinistro.</span><span class="sxs-lookup"><span data-stu-id="7df15-121">In this example, the button position is 165 pixels from the form’s top edge, and 38 pixels from the left edge.</span></span> <span data-ttu-id="7df15-122">L'altezza del pulsante è di 23 pixel, mentre la lunghezza è di 75 pixel.</span><span class="sxs-lookup"><span data-stu-id="7df15-122">The button height is 23 pixels, while the button length is 75 pixels.</span></span> <span data-ttu-id="7df15-123">Lo script usa i tipi predefiniti di Windows Form per determinare i comportamenti del pulsante.</span><span class="sxs-lookup"><span data-stu-id="7df15-123">The script uses predefined Windows Forms types to determine the button behaviors.</span></span>

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

<span data-ttu-id="7df15-124">Analogamente, creare un pulsante **Cancel**.</span><span class="sxs-lookup"><span data-stu-id="7df15-124">Similarly, you create a **Cancel** button.</span></span>
<span data-ttu-id="7df15-125">Il pulsante **Cancel** è posizionato a 165 pixel di distanza dal bordo superiore, ma a 113 pixel dal bordo sinistro della finestra.</span><span class="sxs-lookup"><span data-stu-id="7df15-125">The **Cancel** button is 165 pixels from the top, but 113 pixels from the left edge of the window.</span></span>

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

<span data-ttu-id="7df15-126">Aggiungere la riga di codice seguente per visualizzare il modulo in Windows.</span><span class="sxs-lookup"><span data-stu-id="7df15-126">Add the following line of code to display the form in Windows.</span></span>

```powershell
$result = $form.ShowDialog()
```

<span data-ttu-id="7df15-127">Infine, il codice all'interno del blocco `if` indica a Windows cosa fare con il modulo dopo che l'utente seleziona un giorno del calendario e quindi fa clic su **OK** o preme **INVIO**.</span><span class="sxs-lookup"><span data-stu-id="7df15-127">Finally, the code inside the `if` block instructs Windows what to do with the form after users select a day on the calendar, and then click the **OK** button or press the **Enter** key.</span></span> <span data-ttu-id="7df15-128">Windows PowerShell visualizza la data selezionata.</span><span class="sxs-lookup"><span data-stu-id="7df15-128">Windows PowerShell displays the selected date to users.</span></span>

```powershell
if ($result -eq [Windows.Forms.DialogResult]::OK) {
    $date = $calendar.SelectionStart
    Write-Host "Date selected: $($date.ToShortDateString())"
}
```

## <a name="see-also"></a><span data-ttu-id="7df15-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="7df15-129">See Also</span></span>

- [<span data-ttu-id="7df15-130">GitHub: WinFormsExampleUpdates di Dave Wyatt</span><span class="sxs-lookup"><span data-stu-id="7df15-130">GitHub: Dave Wyatt's WinFormsExampleUpdates</span></span>](https://github.com/dlwyatt/WinFormsExampleUpdates)
- <span data-ttu-id="7df15-131">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10)) (Creazione di un controllo grafico di selezione data)</span><span class="sxs-lookup"><span data-stu-id="7df15-131">[Windows PowerShell Tip of the Week:  Creating a Graphical Date Picker](/previous-versions/windows/it-pro/windows-powershell-1.0/ff730942(v=technet.10))</span></span>
