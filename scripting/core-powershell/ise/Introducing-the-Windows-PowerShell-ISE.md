---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Introduzione a Windows PowerShell ISE
ms.assetid: a0de70ca-909a-4807-94d1-6da86e5b52a0
ms.openlocfilehash: 61d31fc2555d91bc7872d7b90cfb1f2a9832ff9c
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="introducing-the-windows-powershell-ise"></a><span data-ttu-id="8ffa5-103">Introduzione a Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8ffa5-103">Introducing the Windows PowerShell ISE</span></span>
<span data-ttu-id="8ffa5-104">Windows PowerShell Integrated Scripting Environment (ISE) è un'applicazione host per Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-104">The Windows PowerShell Integrated Scripting Environment (ISE) is a host application for Windows PowerShell.</span></span> <span data-ttu-id="8ffa5-105">In Windows PowerShell ISE è possibile eseguire comandi, nonché scrivere script, testarli e sottoporli a debug in una singola interfaccia utente grafica basata su Windows con funzionalità di modifica su più righe, completamento tramite tasto TAB, colorazione della sintassi, esecuzione selettiva, Guida sensibile al contesto e supporto per lingue da destra a sinistra.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-105">In Windows PowerShell ISE, you can run commands and write, test, and debug scripts in a single Windows-based graphic user interface with multiline editing, tab completion, syntax coloring, selective execution, context-sensitive help, and support for right-to-left languages.</span></span>
<span data-ttu-id="8ffa5-106">È possibile usare voci di menu e tasti di scelta rapida per completare molte delle stesse attività eseguibili nella console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-106">You can use menu items and keyboard shortcuts to perform many of the same tasks that you would perform in the Windows PowerShell console.</span></span>  <span data-ttu-id="8ffa5-107">Ad esempio, durante il debug di uno script in Windows PowerShell ISE, per impostare un punto di interruzione riga in uno script, fare clic con il pulsante destro del mouse sulla riga di codice e quindi fare clic su **Attiva/disattiva punto di interruzione**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-107">For example, when you debug a script in the Windows PowerShell ISE, to set a line breakpoint in a script, right-click the line of code, and then click **Toggle Breakpoint**.</span></span>

<span data-ttu-id="8ffa5-108">Provare queste funzionalità in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-108">Try these features in Windows PowerShell ISE.</span></span>

-   <span data-ttu-id="8ffa5-109">Modifica su più righe: per inserire una riga vuota sotto la riga corrente nel riquadro dei comandi, premere MAIUSC+INVIO.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-109">Multiline editing: To insert a blank line under the current line in the Command pane, press SHIFT+ENTER.</span></span>

-   <span data-ttu-id="8ffa5-110">Esecuzione selettiva: per eseguire parte di uno script, selezionare il testo da eseguire e quindi fare clic sul pulsante **Esegui script**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-110">Selective execution: To run part of a script, select the text you want to run, and then click the **Run Script** button.</span></span> <span data-ttu-id="8ffa5-111">Oppure premere F5.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-111">Or, press F5.</span></span>

-   <span data-ttu-id="8ffa5-112">Guida sensibile al contesto: digitare **Invoke-Item** e quindi premere F1.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-112">Context-sensitive help: Type **Invoke-Item**, and then press F1.</span></span> <span data-ttu-id="8ffa5-113">Il file della Guida si apre in corrispondenza dell'argomento relativo al cmdlet **Invoke-Item**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-113">The Help file opens to the Help topic for the **Invoke-Item** cmdlet.</span></span>

<span data-ttu-id="8ffa5-114">Windows PowerShell ISE consente di personalizzarne l'aspetto in vari modi.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-114">The Windows PowerShell ISE lets you customize some aspects of its appearance.</span></span> <span data-ttu-id="8ffa5-115">Include anche uno specifico profilo di Windows PowerShell in cui è possibile archiviare funzioni, alias, variabili e comandi da usare in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-115">It also has its own Windows PowerShell profile, where you can store functions, aliases, variables, and commands you use in the Windows PowerShell ISE.</span></span>

### <a name="to-start-the-windows-powershell-ise"></a><span data-ttu-id="8ffa5-116">Per avviare Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8ffa5-116">To start the Windows PowerShell ISE</span></span>

1.  <span data-ttu-id="8ffa5-117">Eseguire una delle operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="8ffa5-117">Do one of the following:</span></span>

    -   <span data-ttu-id="8ffa5-118">Fare clic sul pulsante **Start**, selezionare **Tutti i programmi**, selezionare **Windows PowerShell V2** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-118">Click **Start**, point to **All Programs**, point to **Windows PowerShell V2**, and then click **Windows PowerShell ISE**.</span></span>

    -   <span data-ttu-id="8ffa5-119">In Cmd.exe della console di Windows PowerShell oppure nella casella Esegui digitare **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-119">In the Windows PowerShell console Cmd.exe, or in the Run box, type, **powershell_ise.exe**.</span></span>

### <a name="to-get-help-in-the-windows-powershell-ise"></a><span data-ttu-id="8ffa5-120">Per visualizzare la Guida in Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="8ffa5-120">To get Help in the Windows PowerShell ISE</span></span>

-   <span data-ttu-id="8ffa5-121">Nel menu **?** fare clic su **Guida di Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-121">On the **Help** menu, click **Windows PowerShell Help**.</span></span> <span data-ttu-id="8ffa5-122">Oppure premere F1.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-122">Or, press F1.</span></span> <span data-ttu-id="8ffa5-123">Si apre un file che descrive Windows PowerShell ISE e Windows PowerShell, con tutti gli argomenti disponibili tramite il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="8ffa5-123">The file that opens describes Windows PowerShell ISE and Windows PowerShell, including all of the help available from the Get-Help cmdlet.</span></span>

