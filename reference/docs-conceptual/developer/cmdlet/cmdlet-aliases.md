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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369980"
---
# <a name="cmdlet-aliases"></a><span data-ttu-id="065db-102">Alias dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="065db-102">Cmdlet Aliases</span></span>

<span data-ttu-id="065db-103">È possibile utilizzare gli alias dei cmdlet per migliorare l'esperienza utente del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="065db-103">You can use cmdlet aliases to improve the cmdlet user experience.</span></span> <span data-ttu-id="065db-104">È possibile aggiungere alias ai cmdlet usati di frequente per ridurre la digitazione e semplificare il completamento rapido delle attività.</span><span class="sxs-lookup"><span data-stu-id="065db-104">You can add aliases to frequently used cmdlets to reduce typing and to make it easier to complete tasks quickly.</span></span> <span data-ttu-id="065db-105">È possibile includere alias predefiniti nei cmdlet oppure gli utenti possono definire i propri alias personalizzati.</span><span class="sxs-lookup"><span data-stu-id="065db-105">You can include built-in aliases in your cmdlets, or users can define their own custom aliases.</span></span>

<span data-ttu-id="065db-106">Il cmdlet [Get-Command](/powershell/module/microsoft.powershell.core/get-command) dispone ad esempio di un alias `gcm` incorporato.</span><span class="sxs-lookup"><span data-stu-id="065db-106">For example, the [Get-Command](/powershell/module/microsoft.powershell.core/get-command) cmdlet has a built-in `gcm` alias.</span></span> <span data-ttu-id="065db-107">È anche possibile usare alias per aggiungere nomi di comando da altri linguaggi, in modo che gli utenti non debbano apprendere nuovi comandi.</span><span class="sxs-lookup"><span data-stu-id="065db-107">You can also use aliases to add command names from other languages so that users do not have to learn new commands.</span></span>

## <a name="alias-guidelines"></a><span data-ttu-id="065db-108">Linee guida per gli alias</span><span class="sxs-lookup"><span data-stu-id="065db-108">Alias Guidelines</span></span>

<span data-ttu-id="065db-109">Quando si creano alias predefiniti per i cmdlet, seguire queste linee guida:</span><span class="sxs-lookup"><span data-stu-id="065db-109">Follow these guidelines when you create built-in aliases for your cmdlets:</span></span>

- <span data-ttu-id="065db-110">Prima di assegnare gli alias, avviare Windows PowerShell, quindi eseguire il cmdlet [get-alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) per visualizzare gli alias già usati.</span><span class="sxs-lookup"><span data-stu-id="065db-110">Before you assign aliases, start Windows PowerShell, and then run the [Get-Alias](/powershell/module/Microsoft.PowerShell.Utility/Get-Alias) cmdlet to see the aliases that are already used.</span></span>

- <span data-ttu-id="065db-111">Includere un prefisso alias che fa riferimento al verbo del nome del cmdlet e un suffisso alias che fa riferimento al sostantivo nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="065db-111">Include an alias prefix that references the verb of the cmdlet name and an alias suffix that references the noun of the cmdlet name.</span></span> <span data-ttu-id="065db-112">Ad esempio, l'alias per il cmdlet `Import-Module` è "IPMO".</span><span class="sxs-lookup"><span data-stu-id="065db-112">For example, the alias for the `Import-Module` cmdlet is "ipmo".</span></span> <span data-ttu-id="065db-113">Per un elenco di tutti i verbi e dei rispettivi alias, vedere [verbi dei cmdlet](./approved-verbs-for-windows-powershell-commands.md).</span><span class="sxs-lookup"><span data-stu-id="065db-113">For a list of all the verbs and their aliases, see [Cmdlet Verbs](./approved-verbs-for-windows-powershell-commands.md).</span></span>

- <span data-ttu-id="065db-114">Per i cmdlet che hanno lo stesso verbo, includere lo stesso prefisso di alias.</span><span class="sxs-lookup"><span data-stu-id="065db-114">For cmdlets that have the same verb, include the same alias prefix.</span></span> <span data-ttu-id="065db-115">Ad esempio, gli alias per tutti i cmdlet di Windows PowerShell con il verbo "Get" nel nome usano il prefisso "g".</span><span class="sxs-lookup"><span data-stu-id="065db-115">For example, the aliases for all the Windows PowerShell cmdlets that have the "Get" verb in their name use the "g" prefix.</span></span>

- <span data-ttu-id="065db-116">Per i cmdlet che hanno lo stesso nome, includere lo stesso suffisso alias.</span><span class="sxs-lookup"><span data-stu-id="065db-116">For cmdlets that have the same noun, include the same alias suffix.</span></span> <span data-ttu-id="065db-117">Ad esempio, gli alias per tutti i cmdlet di Windows PowerShell che hanno il sostantivo "Session" nel nome usano il suffisso "sn".</span><span class="sxs-lookup"><span data-stu-id="065db-117">For example, the aliases for all the Windows PowerShell cmdlets that have the "Session" noun in their name use the "sn" suffix.</span></span>

- <span data-ttu-id="065db-118">Per i cmdlet equivalenti ai comandi di altri linguaggi, usare il nome del comando.</span><span class="sxs-lookup"><span data-stu-id="065db-118">For cmdlets that are equivalent to commands in other languages, use the name of the command.</span></span>

- <span data-ttu-id="065db-119">In generale, creare gli alias il più breve possibile.</span><span class="sxs-lookup"><span data-stu-id="065db-119">In general, make aliases as short as possible.</span></span> <span data-ttu-id="065db-120">Verificare che l'alias includa almeno un carattere distinto per il verbo e un carattere distinto per il sostantivo.</span><span class="sxs-lookup"><span data-stu-id="065db-120">Make sure the alias has at least one distinct character for the verb and one distinct character for the noun.</span></span> <span data-ttu-id="065db-121">Aggiungere altri caratteri necessari per rendere univoco l'alias.</span><span class="sxs-lookup"><span data-stu-id="065db-121">Add more characters as needed to make the alias unique.</span></span>

## <a name="see-also"></a><span data-ttu-id="065db-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="065db-122">See Also</span></span>

[<span data-ttu-id="065db-123">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="065db-123">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
