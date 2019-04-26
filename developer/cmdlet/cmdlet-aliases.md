---
title: Alias di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0d70864-33fb-49ce-8054-c41ba19fd554
caps.latest.revision: 11
ms.openlocfilehash: 32f45702cc0d28e6652ef61ebdbe085291013408
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068720"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="3565d-102">Alias dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="3565d-102">Cmdlet Aliases</span></span>

<span data-ttu-id="3565d-103">È possibile usare gli alias di cmdlet per migliorare l'esperienza utente di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3565d-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="3565d-104">È possibile aggiungere alias al cmdlet usati di frequente per ridurre la digitazione e consentono di semplificare per completare le attività rapidamente.</span><span class="sxs-lookup"><span data-stu-id="3565d-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="3565d-105">È possibile includere gli alias incorporati in dei cmdlet o gli utenti possono definire i propri alias personalizzati.</span><span class="sxs-lookup"><span data-stu-id="3565d-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="3565d-106">Ad esempio, il [Get-Command](/powershell/module/microsoft.powershell.core/get-command) include un cmdlet `gcm` alias.</span><span class="sxs-lookup"><span data-stu-id="3565d-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="3565d-107">È anche possibile usare gli alias per aggiungere i nomi dei comandi da altri linguaggi, in modo che gli utenti non sono necessario apprendere nuovi comandi.</span><span class="sxs-lookup"><span data-stu-id="3565d-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="3565d-108">Linee guida di alias</span><span class="sxs-lookup"><span data-stu-id="3565d-108">Alias Guidelines</span></span>

<span data-ttu-id="3565d-109">Seguire queste linee guida quando si crea l'alias predefiniti per i cmdlet:</span><span class="sxs-lookup"><span data-stu-id="3565d-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="3565d-110">Prima di assegnare alias, avviare Windows PowerShell e quindi eseguire la [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet per visualizzare gli alias che sono già in uso.</span><span class="sxs-lookup"><span data-stu-id="3565d-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="3565d-111">Includere un prefisso di alias che fa riferimento il verbo del nome del cmdlet e un suffisso di alias che fa riferimento il sostantivo del nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3565d-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="3565d-112">Ad esempio, l'alias per il `Import-Module` cmdlet è "ipmo".</span><span class="sxs-lookup"><span data-stu-id="3565d-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="3565d-113">Per un elenco di tutti i verbi e i relativi alias, vedere [verbi dei Cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="3565d-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="3565d-114">Per i cmdlet che contengono il verbo stesso, includere lo stesso prefisso di alias.</span><span class="sxs-lookup"><span data-stu-id="3565d-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="3565d-115">Gli alias per tutti i cmdlet di Windows PowerShell che contengono il verbo "Get" nel loro nome, ad esempio, usano il prefisso "g".</span><span class="sxs-lookup"><span data-stu-id="3565d-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="3565d-116">Per i cmdlet che contengono il sostantivo stesso, includere lo stesso suffisso di alias.</span><span class="sxs-lookup"><span data-stu-id="3565d-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="3565d-117">Gli alias per tutti i cmdlet di Windows PowerShell che contengono il sostantivo "Sessione" nel nome, ad esempio, usano il suffisso "NS".</span><span class="sxs-lookup"><span data-stu-id="3565d-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="3565d-118">Per i cmdlet che sono equivalenti ai comandi in altre lingue, usare il nome del comando.</span><span class="sxs-lookup"><span data-stu-id="3565d-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="3565d-119">In generale, verificare gli alias più brevi possibile.</span><span class="sxs-lookup"><span data-stu-id="3565d-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="3565d-120">Assicurarsi che l'alias di dispone di almeno un carattere distinto del verbo e un carattere distinto per il sostantivo.</span><span class="sxs-lookup"><span data-stu-id="3565d-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="3565d-121">Aggiungere più caratteri in base alle esigenze per rendere l'alias univoco.</span><span class="sxs-lookup"><span data-stu-id="3565d-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="3565d-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="3565d-122">See Also</span></span>

[<span data-ttu-id="3565d-123">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="3565d-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
