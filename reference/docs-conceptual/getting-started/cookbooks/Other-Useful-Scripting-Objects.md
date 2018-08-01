---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Altri oggetti di scripting utili
ms.assetid: 4d781196-720b-4ccc-90d2-c570e5e719f5
ms.openlocfilehash: 04e94f858b568928b3910dd0ee85a912a6afc264
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39268501"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="57224-103">Altri oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="57224-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="57224-104">Gli oggetti seguenti forniscono ulteriori funzionalità di scripting in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="57224-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="57224-105">Non fanno parte della gerarchia **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="57224-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="57224-106">Oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="57224-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="57224-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="57224-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="57224-108">Esistono alcune limitazioni sull'interazione tra Windows PowerShell ISE e le applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="57224-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="57224-109">Un comando o uno script di automazione che richiede l'intervento dell'utente potrebbe non funzionare nel modo giusto dalla console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="57224-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="57224-110">È consigliabile bloccare l'esecuzione di tali comandi o script nel riquadro dei comandi di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="57224-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="57224-111">L'oggetto **$psUnsupportedConsoleApplications** conserva un elenco di tali comandi.</span><span class="sxs-lookup"><span data-stu-id="57224-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="57224-112">Se si prova a eseguire i comandi in questo elenco, viene visualizzato un messaggio che indica che non sono supportati.</span><span class="sxs-lookup"><span data-stu-id="57224-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="57224-113">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="57224-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="57224-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="57224-114">$psLocalHelp</span></span>

<span data-ttu-id="57224-115">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra gli argomenti della Guida e i relativi collegamenti associati nel file della Guida HTML compilato locale.</span><span class="sxs-lookup"><span data-stu-id="57224-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="57224-116">Viene usato per trovare la Guida locale per un determinato argomento.</span><span class="sxs-lookup"><span data-stu-id="57224-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="57224-117">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="57224-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="57224-118">L'esempio di codice seguente mostra alcune coppie chiave-valore di esempio contenute in `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="57224-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

```powershell
# See the local help map
$psLocalHelp | Format-List
```

```output
Key   : Add-Computer
Value : WindowsPowerShellHelp.chm::/html/093f660c-b8d5-43cf-aa0c-54e5e54e76f9.htm

Key   : Add-Content
Value : WindowsPowerShellHelp.chm::/html/0c836a1b-f389-4e9a-9325-0f415686d194.htm
```

<span data-ttu-id="57224-119">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="57224-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="57224-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="57224-120">$psOnlineHelp</span></span>

<span data-ttu-id="57224-121">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra i titoli degli argomenti della Guida e i relativi URL esterni associati.</span><span class="sxs-lookup"><span data-stu-id="57224-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="57224-122">Viene usato per trovare la Guida per un determinato argomento nel Web.</span><span class="sxs-lookup"><span data-stu-id="57224-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="57224-123">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="57224-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : http://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : http://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="57224-124">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="57224-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "http://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="57224-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="57224-125">See Also</span></span>

[<span data-ttu-id="57224-126">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="57224-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../../core-powershell/ise/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)