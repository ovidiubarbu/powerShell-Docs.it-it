---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Come creare una scheda di PowerShell in Windows PowerShell ISE
ms.assetid: c10c18c7-9ece-4fd0-83dc-a19c53d4fd83
ms.openlocfilehash: 3cfeb18babe6b63f0e02da8cf0fd460950f1afce
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="how-to-create-a-powershell-tab-in-windows-powershell-ise"></a><span data-ttu-id="89909-103">Come creare una scheda di PowerShell in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="89909-103">How to Create a PowerShell Tab in Windows PowerShell ISE</span></span>
<span data-ttu-id="89909-104">Le schede in Windows PowerShell Integrated Scripting Environment (ISE) consentono di creare e usare simultaneamente diversi ambienti di esecuzione all'interno della stessa applicazione.</span><span class="sxs-lookup"><span data-stu-id="89909-104">Tabs in the Windows PowerShell Integrated Scripting Environment (ISE) allow you to simultaneously create and use several execution environments within the same application.</span></span>
<span data-ttu-id="89909-105">Ogni scheda di PowerShell corrisponde a una sessione o a un ambiente di esecuzione separato.</span><span class="sxs-lookup"><span data-stu-id="89909-105">Each PowerShell tab corresponds to a separate execution environment or session.</span></span>

> <span data-ttu-id="89909-106">**NOTA**:</span><span class="sxs-lookup"><span data-stu-id="89909-106">**NOTE**:</span></span>
>
> <span data-ttu-id="89909-107">Variabili, funzioni e alias creati in una scheda non vengono riportati in un'altra scheda.</span><span class="sxs-lookup"><span data-stu-id="89909-107">Variables, functions, and aliases that you create in one tab do not carry over to another.</span></span> <span data-ttu-id="89909-108">Si tratta di diverse sessioni di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89909-108">They are different Windows PowerShell sessions.</span></span>

<span data-ttu-id="89909-109">Usare la procedura seguente per aprire o chiudere una scheda in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89909-109">Use the following steps to open or close a tab in Windows PowerShell.</span></span>
<span data-ttu-id="89909-110">Per rinominare una scheda, impostare la proprietà [DisplayName](The-PowerShellTab-Object.md#displayname) nell'oggetto di scripting della scheda di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89909-110">To rename a tab, set the [DisplayName](The-PowerShellTab-Object.md#displayname) property on the Windows PowerShell Tab scripting object.</span></span>

## <a name="to-create-and-use-a-new-powershell-tab"></a><span data-ttu-id="89909-111">Per creare e usare una nuova scheda di PowerShell</span><span class="sxs-lookup"><span data-stu-id="89909-111">To create and use a new PowerShell Tab</span></span>

<span data-ttu-id="89909-112">Nel menu **File** fare clic su **Nuova scheda di PowerShell**. La nuova scheda di PowerShell viene visualizzata sempre come finestra attiva.</span><span class="sxs-lookup"><span data-stu-id="89909-112">On the **File** menu, click **New PowerShell Tab**. The new PowerShell tab always opens as the active window.</span></span>
<span data-ttu-id="89909-113">Le schede di PowerShell sono numerate in modo incrementale nell'ordine di apertura.</span><span class="sxs-lookup"><span data-stu-id="89909-113">PowerShell tabs are incrementally numbered in the order that they are opened.</span></span>
<span data-ttu-id="89909-114">Ogni scheda è associata alla propria finestra della console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89909-114">Each tab is associated with its own Windows PowerShell console window.</span></span>
<span data-ttu-id="89909-115">È possibile tenere aperte fino a 32 schede di PowerShell con le rispettive sessioni per volta. In Windows PowerShell ISE 2.0 questa opzione è limitata a 8 schede.</span><span class="sxs-lookup"><span data-stu-id="89909-115">You can have up to 32 PowerShell tabs with their own session open at a time (this is limited to 8 on Windows PowerShell ISE 2.0.)</span></span>

<span data-ttu-id="89909-116">Tenere presente che, facendo clic sulle icone **Nuova** o **Apri** nella barra degli strumenti, non verrà creata una nuova scheda con una sessione distinta.</span><span class="sxs-lookup"><span data-stu-id="89909-116">Note that clicking the **New** or **Open** icons on the toolbar does not create a new tab with a separate session.</span></span>
<span data-ttu-id="89909-117">Al contrario, questi pulsanti aprono un file di script nuovo o esistente nella scheda attualmente attiva con una sessione.</span><span class="sxs-lookup"><span data-stu-id="89909-117">Instead, those buttons open a new or existing script file on the currently active tab with a session.</span></span>
<span data-ttu-id="89909-118">È possibile tenere aperti più file di script con ogni scheda e sessione.</span><span class="sxs-lookup"><span data-stu-id="89909-118">You can have multiple script files open with each tab and session.</span></span>
<span data-ttu-id="89909-119">Le schede degli script per una sessione vengono visualizzate sotto le schede di sessione solo quando la sessione associata è attiva.</span><span class="sxs-lookup"><span data-stu-id="89909-119">The script tabs for a session only appear below the session tabs when the associated session is active.</span></span>

<span data-ttu-id="89909-120">Per rendere attiva una scheda di PowerShell, fare clic sulla scheda. Per scegliere fra tutte le schede di PowerShell aperte, nel menu **Visualizza** fare clic sulla scheda di PowerShell da usare.</span><span class="sxs-lookup"><span data-stu-id="89909-120">To make a PowerShell tab active, click the tab. To select from all PowerShell tabs that are open, on the **View** menu, click the PowerShell tab you want to use.</span></span>

## <a name="to-create-and-use-a-new-remote-powershell-tab"></a><span data-ttu-id="89909-121">Per creare e usare una nuova scheda di PowerShell remota</span><span class="sxs-lookup"><span data-stu-id="89909-121">To create and use a new Remote PowerShell tab</span></span>

<span data-ttu-id="89909-122">Nel menu **File** fare clic su **Scheda Nuova sessione PowerShell remota** per stabilire una sessione in un computer remoto.</span><span class="sxs-lookup"><span data-stu-id="89909-122">On the **File** menu, click **New Remote PowerShell Tab** to establish a session on a remote computer.</span></span>
<span data-ttu-id="89909-123">Verrà visualizzata una finestra di dialogo che richiede di immettere i dettagli necessari per stabilire la connessione remota.</span><span class="sxs-lookup"><span data-stu-id="89909-123">A dialog box appears and prompts you to enter details required to establish the remote connection.</span></span>
<span data-ttu-id="89909-124">La scheda remota funziona come una scheda di PowerShell locale, ma i comandi e gli script vengono eseguiti nel computer remoto.</span><span class="sxs-lookup"><span data-stu-id="89909-124">The remote tab functions just like a local PowerShell tab, but the commands and scripts are run on the remote computer.</span></span>

## <a name="to-close-a-powershell-tab"></a><span data-ttu-id="89909-125">Per chiudere una scheda di PowerShell</span><span class="sxs-lookup"><span data-stu-id="89909-125">To close a PowerShell Tab</span></span>

<span data-ttu-id="89909-126">Per chiudere una scheda, è possibile usare una delle tecniche seguenti:</span><span class="sxs-lookup"><span data-stu-id="89909-126">To close a tab, you can use any of the following techniques:</span></span>

- <span data-ttu-id="89909-127">Fare clic sulla scheda che si vuole chiudere.</span><span class="sxs-lookup"><span data-stu-id="89909-127">Click the tab that you want to close.</span></span>

- <span data-ttu-id="89909-128">Nel menu **File** fare clic su **Chiudi scheda di PowerShell** o fare clic sul pulsante Chiudi (**X**) in una scheda attiva per chiuderla.</span><span class="sxs-lookup"><span data-stu-id="89909-128">On the **File** menu, click **Close PowerShell Tab**, or click  the Close button  (**X**) on an active tab to close the tab.</span></span>

<span data-ttu-id="89909-129">Se sono presenti file non salvati aperti nella scheda di PowerShell che si vuole chiudere, viene richiesto di salvare o rimuovere tali file.</span><span class="sxs-lookup"><span data-stu-id="89909-129">If you have unsaved files open in the PowerShell tab that you are closing, you are prompted to save or discard them.</span></span>
<span data-ttu-id="89909-130">Per altre informazioni su come salvare uno script, vedere [Come salvare uno script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span><span class="sxs-lookup"><span data-stu-id="89909-130">For more information about how to save a script, see [How to Save a Script](How-to-Write-and-Run-Scripts-in-the-Windows-PowerShell-ISE.md#how-to-save-a-script).</span></span>

## <a name="see-also"></a><span data-ttu-id="89909-131">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="89909-131">See Also</span></span>

- [<span data-ttu-id="89909-132">Uso di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="89909-132">Using the Windows PowerShell ISE</span></span>](Using-the-Windows-PowerShell-ISE.md)
- [<span data-ttu-id="89909-133">Come usare il riquadro della console in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="89909-133">How to Use the Console Pane in the Windows PowerShell ISE</span></span>](How-to-Use-the-Console-Pane-in-the-Windows-PowerShell-ISE.md)

