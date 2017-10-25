---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Altri oggetti di scripting utili
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 8334d0b346e59dea3643a93bf52b780b361d1945
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="66dbd-103">Altri oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="66dbd-103">Other Useful Scripting Objects</span></span>
  <span data-ttu-id="66dbd-104">Gli oggetti seguenti forniscono ulteriori funzionalità di scripting in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66dbd-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="66dbd-105">Non fanno parte della gerarchia **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="66dbd-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="66dbd-106">Oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="66dbd-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="66dbd-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="66dbd-107">$psUnsupportedConsoleApplications</span></span>
 <span data-ttu-id="66dbd-108">Esistono alcune limitazioni sull'interazione tra Windows PowerShell ISE e le applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="66dbd-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="66dbd-109">Un comando o uno script di automazione che richiede l'intervento dell'utente potrebbe non funzionare nel modo giusto dalla console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66dbd-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="66dbd-110">È consigliabile bloccare l'esecuzione di tali comandi o script nel riquadro dei comandi di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="66dbd-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="66dbd-111">L'oggetto **$psUnsupportedConsoleApplications** conserva un elenco di tali comandi.</span><span class="sxs-lookup"><span data-stu-id="66dbd-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="66dbd-112">Se si prova a eseguire i comandi in questo elenco, viene visualizzato un messaggio che indica che non sono supportati.</span><span class="sxs-lookup"><span data-stu-id="66dbd-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="66dbd-113">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="66dbd-113">The following script adds an entry to the list.</span></span>

```
# List the unsupported commands
psUnsupportedConsoleApplications
# Add a command to this list
psUnsupportedConsoleApplications.Add(“Mycommand”)
#Show the augmented list of commands
psUnsupportedConsoleApplications

```

### <a name="pslocalhelp"></a><span data-ttu-id="66dbd-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="66dbd-114">$psLocalHelp</span></span>
 <span data-ttu-id="66dbd-115">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra gli argomenti della Guida e i relativi collegamenti associati nel file della Guida HTML compilato locale.</span><span class="sxs-lookup"><span data-stu-id="66dbd-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="66dbd-116">Viene usato per trovare la Guida locale per un determinato argomento.</span><span class="sxs-lookup"><span data-stu-id="66dbd-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="66dbd-117">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="66dbd-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="66dbd-118">L'esempio di codice seguente mostra alcune coppie chiave-valore contenute in **$psLocalHelp**.</span><span class="sxs-lookup"><span data-stu-id="66dbd-118">The following code example shows some example key-value pairs that are contained in **$psLocalHelp**.</span></span>

```
# See the local help map
$psLocalHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="66dbd-119">Output di esempio</span><span class="sxs-lookup"><span data-stu-id="66dbd-119">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="66dbd-120">Chiave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="66dbd-120">Key : Add-Computer</span></span>|<span data-ttu-id="66dbd-121">Valore: WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span><span class="sxs-lookup"><span data-stu-id="66dbd-121">Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm</span></span>|
|<span data-ttu-id="66dbd-122">Chiave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="66dbd-122">Key : Add-Content</span></span>|<span data-ttu-id="66dbd-123">Valore: WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span><span class="sxs-lookup"><span data-stu-id="66dbd-123">Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm</span></span>|

 <span data-ttu-id="66dbd-124">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="66dbd-124">The following script adds an entry to the list.</span></span>

```
$psLocalHelp.Add("get-myNoun","c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="66dbd-125">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="66dbd-125">$psOnlineHelp</span></span>
 <span data-ttu-id="66dbd-126">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra i titoli degli argomenti della Guida e i relativi URL esterni associati.</span><span class="sxs-lookup"><span data-stu-id="66dbd-126">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="66dbd-127">Viene usato per trovare la Guida per un determinato argomento nel Web.</span><span class="sxs-lookup"><span data-stu-id="66dbd-127">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="66dbd-128">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="66dbd-128">You can add or delete topics from this list.</span></span>

```
$psOnlineHelp | Format-List

```

### <a name="sample-output"></a><span data-ttu-id="66dbd-129">Output di esempio</span><span class="sxs-lookup"><span data-stu-id="66dbd-129">Sample Output</span></span>

|||
|-|-|
|<span data-ttu-id="66dbd-130">Chiave: Add-Computer</span><span class="sxs-lookup"><span data-stu-id="66dbd-130">Key : Add-Computer</span></span>|<span data-ttu-id="66dbd-131">Valore : http://go.microsoft.com/fwlink/p/?LinkID=135194</span><span class="sxs-lookup"><span data-stu-id="66dbd-131">Value : http://go.microsoft.com/fwlink/p/?LinkID=135194</span></span>|
|<span data-ttu-id="66dbd-132">Chiave: Add-Content</span><span class="sxs-lookup"><span data-stu-id="66dbd-132">Key : Add-Content</span></span>|<span data-ttu-id="66dbd-133">Valore: http://go.microsoft.com/fwlink/p/?LinkID=113278</span><span class="sxs-lookup"><span data-stu-id="66dbd-133">Value : http://go.microsoft.com/fwlink/p/?LinkID=113278</span></span>|

 <span data-ttu-id="66dbd-134">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="66dbd-134">The following script adds an entry to the list.</span></span>

```
$psOnlineHelp.Add("get-myNoun","http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="66dbd-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="66dbd-135">See Also</span></span>
- [<span data-ttu-id="66dbd-136">Modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="66dbd-136">The Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/The-Windows-PowerShell-ISE-Scripting-Object-Model.md)

  
