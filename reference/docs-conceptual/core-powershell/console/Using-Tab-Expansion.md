---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso dell'espansione dei nomi tramite TAB
ms.assetid: c8730471-bf6a-43b8-ab1d-f9ef5a74f04e
ms.openlocfilehash: 3d047bf0691c8a304d7637aa50fba6ae99709a82
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
ms.locfileid: "30949231"
---
# <a name="using-tab-expansion"></a><span data-ttu-id="61c09-103">Uso dell'espansione dei nomi tramite TAB</span><span class="sxs-lookup"><span data-stu-id="61c09-103">Using Tab Expansion</span></span>

<span data-ttu-id="61c09-104">Le shell da riga di comando offrono spesso un modo per completare automaticamente i nomi di file o comandi lunghi, velocizzando l'immissione dei comandi e visualizzando suggerimenti.</span><span class="sxs-lookup"><span data-stu-id="61c09-104">Command-line shells often provide a way to complete the names of long files or commands automatically, speeding up command entry and providing .</span></span> <span data-ttu-id="61c09-105">Windows PowerShell consente di usare il tasto **TAB** per immettere nomi di file e di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="61c09-105">Windows PowerShell allows you to fill in file names and cmdlet names by pressing the **Tab** key.</span></span>

> [!NOTE]
> <span data-ttu-id="61c09-106">L'espansione tramite TAB è controllata dalla funzione interna TabExpansion o TabExpansion2.</span><span class="sxs-lookup"><span data-stu-id="61c09-106">Tab expansion is controlled by the internal function TabExpansion or TabExpansion2.</span></span> <span data-ttu-id="61c09-107">Poiché questa funzione può essere modificata o sottoposta a override, le informazioni seguenti sono da intendersi come una guida al comportamento della configurazione predefinita di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61c09-107">Since this function can be modified or overridden, this discussion is a guide to the behavior of the default PowerShell configuration.</span></span>

<span data-ttu-id="61c09-108">Per immettere automaticamente un nome di file o un percorso usando le scelte disponibili, digitare parte del nome e premere **TAB**.</span><span class="sxs-lookup"><span data-stu-id="61c09-108">To fill in a filename or path from the available choices automatically, type part of the name and press the **Tab** key.</span></span> <span data-ttu-id="61c09-109">PowerShell espanderà automaticamente il nome usando la prima corrispondenza trovata.</span><span class="sxs-lookup"><span data-stu-id="61c09-109">PowerShell will automatically expand the name to the first match that it finds.</span></span> <span data-ttu-id="61c09-110">Premendo più volte **TAB** è possibile visualizzare in sequenza tutte le scelte disponibili.</span><span class="sxs-lookup"><span data-stu-id="61c09-110">Pressing the **Tab** key repeatedly will cycle through all of the available choices.</span></span>

<span data-ttu-id="61c09-111">L'espansione tramite TAB dei nomi di cmdlet è leggermente diversa.</span><span class="sxs-lookup"><span data-stu-id="61c09-111">The tab expansion of cmdlet names is slightly different.</span></span> <span data-ttu-id="61c09-112">Per usare l'espansione tramite TAB per un nome di cmdlet, digitare per intero la prima parte del nome (il verbo) e il trattino che segue.</span><span class="sxs-lookup"><span data-stu-id="61c09-112">To use tab expansion on a cmdlet name, type the entire first part of the name (the verb) and the hyphen that follows it.</span></span> <span data-ttu-id="61c09-113">È possibile immettere anche una parte più lunga del nome per ottenere una corrispondenza parziale.</span><span class="sxs-lookup"><span data-stu-id="61c09-113">You can fill in more of the name for a partial match.</span></span> <span data-ttu-id="61c09-114">Ad esempio, se si digita **get-co** e si preme **TAB**, PowerShell proporrà automaticamente l'espansione al cmdlet **Get-Command**. Notare che viene cambiata anche la combinazione di maiuscole/minuscole in base al formato standard.</span><span class="sxs-lookup"><span data-stu-id="61c09-114">For example, if you type **get-co** and then press the **Tab** key, PowerShell will automatically expand this to the **Get-Command** cmdlet (notice that it also changes the case of letters to their standard form).</span></span> <span data-ttu-id="61c09-115">Se si preme di nuovo **TAB**, PowerShell lo sostituisce con l'unico altro nome di cmdlet corrispondente, ossia **Get-Content**.</span><span class="sxs-lookup"><span data-stu-id="61c09-115">If you press **Tab** key again, PowerShell replaces this with the only other matching cmdlet name, **Get-Content**.</span></span>

<span data-ttu-id="61c09-116">È possibile usare l'espansione dei nomi tramite TAB più volte sulla stessa riga.</span><span class="sxs-lookup"><span data-stu-id="61c09-116">You can use tab expansion repeatedly on the same line.</span></span> <span data-ttu-id="61c09-117">Ad esempio, è possibile usare l'espansione tramite TAB per il nome del cmdlet **Get-Content** cmdlet immettendo:</span><span class="sxs-lookup"><span data-stu-id="61c09-117">For example, you can use tab expansion on the name of the **Get-Content** cmdlet by entering:</span></span>

```
PS> Get-Con<Tab>
```

<span data-ttu-id="61c09-118">Quando si preme **TAB**, il comando viene espanso in:</span><span class="sxs-lookup"><span data-stu-id="61c09-118">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content
```

<span data-ttu-id="61c09-119">È quindi possibile specificare parzialmente il percorso del file di log di installazione (Active Setup) e usare nuovamente la sostituzione tramite TAB:</span><span class="sxs-lookup"><span data-stu-id="61c09-119">You can then partially specify the path to the Active Setup log file and use tab expansion again:</span></span>

```
PS> Get-Content c:\windows\acts<Tab>
```

<span data-ttu-id="61c09-120">Quando si preme **TAB**, il comando viene espanso in:</span><span class="sxs-lookup"><span data-stu-id="61c09-120">When you press the **Tab** key, the command expands to:</span></span>

```
PS> Get-Content C:\windows\actsetup.log
```

> [!NOTE]
> <span data-ttu-id="61c09-121">Uno dei limiti del processo di espansione dei nomi tramite TAB è che le pressioni di TAB vengono sempre interpretate come il tentativo di completare una parola.</span><span class="sxs-lookup"><span data-stu-id="61c09-121">One limitation of the tab expansion process is that tabs are always interpreted as attempts to complete a word.</span></span> <span data-ttu-id="61c09-122">Se si copiano e incollano esempi di comando in una console di PowerShell, assicurarsi che l'esempio non contenga tabulazioni. In caso contrario, i risultati potrebbero essere imprevedibili e quasi certamente diversi da quelli previsti.</span><span class="sxs-lookup"><span data-stu-id="61c09-122">If you copy and paste command examples into a PowerShell console, make sure that the sample does not contain tabs; if it does, the results will be unpredictable and will almost certainly not be what you intended.</span></span>