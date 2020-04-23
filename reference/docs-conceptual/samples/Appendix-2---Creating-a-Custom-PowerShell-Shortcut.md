---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Appendice 2 Creazione di un collegamento personalizzato per PowerShell
ms.openlocfilehash: 6f1a6a8187b1797103e3620b2cf9155978807ea5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030295"
---
# <a name="appendix-2---creating-a-custom-powershell-shortcut"></a><span data-ttu-id="02db0-103">Appendice 2 - Creazione di un collegamento personalizzato per PowerShell</span><span class="sxs-lookup"><span data-stu-id="02db0-103">Appendix 2 - Creating a Custom PowerShell Shortcut</span></span>

<span data-ttu-id="02db0-104">La procedura seguente descrive come creare un collegamento a Windows PowerShell con diverse opzioni utili personalizzate.</span><span class="sxs-lookup"><span data-stu-id="02db0-104">The following procedure describes how to create a shortcut to Windows PowerShell that has several convenient options customized.</span></span>

1. <span data-ttu-id="02db0-105">Creare un collegamento che punta a Powershell.exe.</span><span class="sxs-lookup"><span data-stu-id="02db0-105">Create a shortcut that points to Powershell.exe.</span></span>

2. <span data-ttu-id="02db0-106">Fare clic con il pulsante destro del mouse sul collegamento e quindi scegliere **Proprietà**.</span><span class="sxs-lookup"><span data-stu-id="02db0-106">Right-click the shortcut, and then click **Properties**.</span></span>

3. <span data-ttu-id="02db0-107">Scegliere la scheda **Options (Opzioni)** .</span><span class="sxs-lookup"><span data-stu-id="02db0-107">Click the **Options** tab.</span></span>

4. <span data-ttu-id="02db0-108">Nella sezione **Opzioni di modifica** selezionare la casella di controllo **Modifica rapida**.</span><span class="sxs-lookup"><span data-stu-id="02db0-108">In the **Edit Options** section, select the **QuickEdit** check box.</span></span>

    <span data-ttu-id="02db0-109">Questa impostazione consente di selezionare testo nella finestra della console di Windows PowerShell trascinando il pulsante sinistro del mouse e consente di copiare il testo negli Appunti premendo INVIO oppure facendo clic con il pulsante destro del mouse.</span><span class="sxs-lookup"><span data-stu-id="02db0-109">This setting lets you select text in the Windows PowerShell console window by dragging the left mouse button, and it lets you copy text to the clipboard by pressing ENTER or by right-clicking the mouse.</span></span>

5. <span data-ttu-id="02db0-110">Nella sezione **Opzioni di modifica** selezionare la casella di controllo **Modalità inserimento**.</span><span class="sxs-lookup"><span data-stu-id="02db0-110">In the **Edit Options** section, select the **Insert Mode** check box.</span></span> <span data-ttu-id="02db0-111">Questa impostazione consente di fare clic con il pulsante destro del mouse nella finestra della console per incollare automaticamente il testo dagli Appunti.</span><span class="sxs-lookup"><span data-stu-id="02db0-111">This setting lets you right-click in the console window to automatically paste text from the clipboard.</span></span>

6. <span data-ttu-id="02db0-112">Nella sezione **Cronologia comandi** digitare o selezionare un numero compreso tra 1 e 999 nella casella **Dimensioni buffer**.</span><span class="sxs-lookup"><span data-stu-id="02db0-112">In the **Command History** section, type or select a number between 1 and 999 in the **Buffer Size** box.</span></span> <span data-ttu-id="02db0-113">Questa opzione consente di impostare il numero di comandi digitati che verranno conservati nel buffer della console.</span><span class="sxs-lookup"><span data-stu-id="02db0-113">This sets the number of typed commands that will be kept in the console buffer.</span></span>

7. <span data-ttu-id="02db0-114">Nella sezione **Cronologia comandi** selezionare la casella di controllo **Elimina vecchi duplicati** per eliminare i comandi ripetuti dal buffer della console.</span><span class="sxs-lookup"><span data-stu-id="02db0-114">In the **Command History** section, select the **Discard Old Duplicates** check box to eliminate repeated commands from the console buffer.</span></span>

8. <span data-ttu-id="02db0-115">Fare clic sulla scheda **Layout**.</span><span class="sxs-lookup"><span data-stu-id="02db0-115">Click the **Layout** tab.</span></span>

9. <span data-ttu-id="02db0-116">Nella sezione **Dimensioni buffer dello schermo** digitare un numero compreso trai 1 e 9999 nella casella **Altezza**.</span><span class="sxs-lookup"><span data-stu-id="02db0-116">In the **Screen Buffer** section, type a number between 1 and 9999 in the **Height** box.</span></span> <span data-ttu-id="02db0-117">L'altezza rappresenta il numero di righe di output inserite nel buffer.</span><span class="sxs-lookup"><span data-stu-id="02db0-117">The height represents the number of lines of output that are buffered.</span></span> <span data-ttu-id="02db0-118">Questo è il numero massimo di righe mantenute per la visualizzazione quando si scorre la finestra della console.</span><span class="sxs-lookup"><span data-stu-id="02db0-118">This is the maximum number of lines retained for viewing when you scroll through the console window.</span></span> <span data-ttu-id="02db0-119">Se il numero è inferiore rispetto all'altezza indicata nella sezione **Dimensioni finestra**, l'altezza della finestra verrà ridotta automaticamente allo stesso valore.</span><span class="sxs-lookup"><span data-stu-id="02db0-119">If this number is lower than the height shown in the **Window size** section, the window size height will automatically be reduced to the same value.</span></span>

10. <span data-ttu-id="02db0-120">Nella sezione **Dimensioni finestra** digitare un numero compreso tra 1 e 9999 per la larghezza.</span><span class="sxs-lookup"><span data-stu-id="02db0-120">In the **Window Size** section, type a number between 1 and 9999 for the width.</span></span> <span data-ttu-id="02db0-121">Questo è il numero di caratteri visualizzati in senso orizzontale nella finestra della console.</span><span class="sxs-lookup"><span data-stu-id="02db0-121">This represents the number of characters that are displayed across the console window.</span></span> <span data-ttu-id="02db0-122">La larghezza predefinita è 80 e la formattazione dell'output di Windows PowerShell è progettata per questa larghezza.</span><span class="sxs-lookup"><span data-stu-id="02db0-122">The default width is 80, and Windows PowerShell's output formatting is designed for this width.</span></span>

11. <span data-ttu-id="02db0-123">Se si vuole posizionare la console in un particolare punto sul desktop all'apertura, deselezionare la casella di controllo **Posizionamento automatico** nella sezione **Posizione finestra** e quindi modificare i valori nelle caselle **Sinistra** e **Alto** nella sezione **Posizione finestra**.</span><span class="sxs-lookup"><span data-stu-id="02db0-123">If you want to place the console at a particular point on the desktop when it is opened, clear the **Let system position window** check box in the **Window position** section, and then change the values in the **Left** and **Top** boxes in the **Window position** section.</span></span>

12. <span data-ttu-id="02db0-124">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="02db0-124">Click **OK**.</span></span>
