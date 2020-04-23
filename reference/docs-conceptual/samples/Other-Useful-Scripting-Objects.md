---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Altri oggetti di scripting utili
ms.openlocfilehash: 4f236246714b0608658bbd535851489912430336
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71325151"
---
# <a name="other-useful-scripting-objects"></a><span data-ttu-id="551b7-103">Altri oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="551b7-103">Other Useful Scripting Objects</span></span>

<span data-ttu-id="551b7-104">Gli oggetti seguenti forniscono ulteriori funzionalità di scripting in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="551b7-104">The following objects provide additional scripting functionality in Windows PowerShell ISE.</span></span> <span data-ttu-id="551b7-105">Non fanno parte della gerarchia **$psISE**.</span><span class="sxs-lookup"><span data-stu-id="551b7-105">They are not part of the **$psISE** hierarchy.</span></span>

## <a name="useful-scripting-objects"></a><span data-ttu-id="551b7-106">Oggetti di scripting utili</span><span class="sxs-lookup"><span data-stu-id="551b7-106">Useful Scripting objects</span></span>

### <a name="psunsupportedconsoleapplications"></a><span data-ttu-id="551b7-107">$psUnsupportedConsoleApplications</span><span class="sxs-lookup"><span data-stu-id="551b7-107">$psUnsupportedConsoleApplications</span></span>

<span data-ttu-id="551b7-108">Esistono alcune limitazioni sull'interazione tra Windows PowerShell ISE e le applicazioni console.</span><span class="sxs-lookup"><span data-stu-id="551b7-108">There are some limitations on how Windows PowerShell ISE interacts with console applications.</span></span> <span data-ttu-id="551b7-109">Un comando o uno script di automazione che richiede l'intervento dell'utente potrebbe non funzionare nel modo giusto dalla console di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="551b7-109">A command or an automation script that requires user intervention might not work the way it works from the Windows PowerShell console.</span></span> <span data-ttu-id="551b7-110">È consigliabile bloccare l'esecuzione di tali comandi o script nel riquadro dei comandi di Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="551b7-110">You might want to block these commands or scripts from running in the Windows PowerShell ISE Command pane.</span></span> <span data-ttu-id="551b7-111">L'oggetto **$psUnsupportedConsoleApplications** conserva un elenco di tali comandi.</span><span class="sxs-lookup"><span data-stu-id="551b7-111">The **$psUnsupportedConsoleApplications** object keeps a list of such commands.</span></span> <span data-ttu-id="551b7-112">Se si prova a eseguire i comandi in questo elenco, viene visualizzato un messaggio che indica che non sono supportati.</span><span class="sxs-lookup"><span data-stu-id="551b7-112">If you try to run the commands in this list, you get a message that they are not supported.</span></span> <span data-ttu-id="551b7-113">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="551b7-113">The following script adds an entry to the list.</span></span>

```powershell
# List the unsupported commands
$psUnsupportedConsoleApplications

# Add a command to this list
$psUnsupportedConsoleApplications.Add('Mycommand')

# Show the augmented list of commands
$psUnsupportedConsoleApplications
```

### <a name="pslocalhelp"></a><span data-ttu-id="551b7-114">$psLocalHelp</span><span class="sxs-lookup"><span data-stu-id="551b7-114">$psLocalHelp</span></span>

<span data-ttu-id="551b7-115">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra gli argomenti della Guida e i relativi collegamenti associati nel file della Guida HTML compilato locale.</span><span class="sxs-lookup"><span data-stu-id="551b7-115">This is a dictionary object that maintains a context-sensitive mapping between Help topics and their associated links in the local compiled HTML Help file.</span></span> <span data-ttu-id="551b7-116">Viene usato per trovare la Guida locale per un determinato argomento.</span><span class="sxs-lookup"><span data-stu-id="551b7-116">It is used to locate the local Help for a particular topic.</span></span> <span data-ttu-id="551b7-117">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="551b7-117">You can add or delete topics from this list.</span></span> <span data-ttu-id="551b7-118">L'esempio di codice seguente mostra alcune coppie chiave-valore di esempio contenute in `$psLocalHelp`.</span><span class="sxs-lookup"><span data-stu-id="551b7-118">The following code example shows some example key-value pairs that are contained in `$psLocalHelp`.</span></span>

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

<span data-ttu-id="551b7-119">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="551b7-119">The following script adds an entry to the list.</span></span>

```powershell
$psLocalHelp.Add("get-myNoun", "c:\MyFolder\MyHelpChm.chm::/html/0198854a-1298-57ae-aa0c-87b5e5a84712.htm")
```

### <a name="psonlinehelp"></a><span data-ttu-id="551b7-120">$psOnlineHelp</span><span class="sxs-lookup"><span data-stu-id="551b7-120">$psOnlineHelp</span></span>

<span data-ttu-id="551b7-121">Si tratta di un oggetto Dictionary che conserva un mapping sensibile al contesto tra i titoli degli argomenti della Guida e i relativi URL esterni associati.</span><span class="sxs-lookup"><span data-stu-id="551b7-121">This is a dictionary object that maintains a context-sensitive mapping between topic titles of Help topics and their associated external URLs.</span></span> <span data-ttu-id="551b7-122">Viene usato per trovare la Guida per un determinato argomento nel Web.</span><span class="sxs-lookup"><span data-stu-id="551b7-122">It is used to locate the Help for a particular topic on the web.</span></span> <span data-ttu-id="551b7-123">È possibile aggiungere o eliminare argomenti da questo elenco.</span><span class="sxs-lookup"><span data-stu-id="551b7-123">You can add or delete topics from this list.</span></span>

```powershell
$psOnlineHelp | Format-List
```

```output
Key   : Add-Computer
Value : https://go.microsoft.com/fwlink/p/?LinkID=135194

Key   : Add-Content
Value : https://go.microsoft.com/fwlink/p/?LinkID=113278
```

<span data-ttu-id="551b7-124">Lo script seguente aggiunge una voce all'elenco.</span><span class="sxs-lookup"><span data-stu-id="551b7-124">The following script adds an entry to the list.</span></span>

```powershell
$psOnlineHelp.Add("get-myNoun", "https://www.mydomain.com/MyNoun.html")
```

## <a name="see-also"></a><span data-ttu-id="551b7-125">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="551b7-125">See Also</span></span>

[<span data-ttu-id="551b7-126">Scopo del modello a oggetti di scripting di Windows PowerShell ISE</span><span class="sxs-lookup"><span data-stu-id="551b7-126">Purpose of the Windows PowerShell ISE Scripting Object Model</span></span>](../components/ise/object-model/Purpose-of-the-Windows-PowerShell-ISE-Scripting-Object-Model.md)
