---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_unlist_items
ms.openlocfilehash: af48f2ca889dcc101d466e40f2ecbe0cdf62c066
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="unlisting-items"></a><span data-ttu-id="8d3bb-103">Esclusione di elementi dall'elenco</span><span class="sxs-lookup"><span data-stu-id="8d3bb-103">Unlisting items</span></span>

<span data-ttu-id="8d3bb-104">**Perché la rimozione di un elemento da PowerShell Gallery non è disponibile come opzione?**</span><span class="sxs-lookup"><span data-stu-id="8d3bb-104">**Why is removing an item from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="8d3bb-105">PowerShell Gallery non supporta l'eliminazione permanente di elementi da parte degli utenti.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-105">The PowerShell Gallery does not support users permanently deleting their items.</span></span>
<span data-ttu-id="8d3bb-106">Questo consente ad altre persone di creare dipendenze sugli elementi dell'utente senza preoccupazioni per possibili interruzioni nel futuro.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-106">This enables others to take dependencies on your items without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="8d3bb-107">Se, ad esempio, il modulo Pester dipende dal modulo Azure e quest'ultimo viene rimosso da PowerShell Gallery, l'utente non può più usare il modulo Pester.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="8d3bb-108">Anziché rimuovere un elemento, tuttavia, è possibile escluderlo dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-108">Instead of removing an item, however, you can unlist it instead.</span></span>

<span data-ttu-id="8d3bb-109">**Quali sono le conseguenze dell'esclusione di un elemento dall'elenco in PowerShell Gallery?**</span><span class="sxs-lookup"><span data-stu-id="8d3bb-109">**What does unlisting an item on PowerShell Gallery do?**</span></span>

<span data-ttu-id="8d3bb-110">L'esclusione di un elemento dall'elenco, ad esempio un modulo o uno script, in PowerShell Gallery determina la rimozione di tale elemento dalla scheda Elementi. Gli elementi esclusi dall'elenco, inoltre, non possono essere individuati usando la barra di ricerca.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-110">Unlisting an item such as module or script on PowerShell Gallery will remove it from the Items tab. In addition, unlisted items will not be discoverable using the search bar.</span></span>
<span data-ttu-id="8d3bb-111">Il solo modo per scaricare un elemento escluso dall'elenco consiste nello specificarne esattamente il nome e la versione.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-111">The only way to download an unlisted item is to specify the exact name and version of the item.</span></span>
<span data-ttu-id="8d3bb-112">Per questo motivo, l'esclusione di un elemento dall'elenco non interrompe altri moduli o script che dipendono da esso.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-112">Because of this, the unlisting of an item will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="8d3bb-113">Per escludere un elemento dall'elenco, visitare la relativa pagina dei dettagli e selezionare 'Elimina elemento'.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-113">To unlist your item, visit the item details page and select 'Delete Item'.</span></span> <span data-ttu-id="8d3bb-114">Deselezionare la casella di controllo 'Listed' (Elencato) e fare clic su Salva.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="8d3bb-115">**In che modo è possibile rimuovere un elemento?**</span><span class="sxs-lookup"><span data-stu-id="8d3bb-115">**How can I remove an item?**</span></span>

<span data-ttu-id="8d3bb-116">Se si verifica uno scenario in cui è necessario eliminare un elemento, contattare gli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-116">If you experience a scenario where item deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="8d3bb-117">Gli scenari di eliminazione validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="8d3bb-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="8d3bb-118">Problemi relativi alla violazione del copyright.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="8d3bb-119">Elementi con contenuto potenzialmente dannoso.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-119">Item contains potentially harmful content.</span></span>
- <span data-ttu-id="8d3bb-120">Elementi contenenti dati sensibili.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-120">Item contains sensitive data.</span></span>

<span data-ttu-id="8d3bb-121">Per inviare una richiesta di eliminazione di un elemento agli amministratori di PowerShell Gallery, visitare la pagina dei dettagli dell'elemento e selezionare Come contattare il supporto tecnico.</span><span class="sxs-lookup"><span data-stu-id="8d3bb-121">To submit a Delete Item Request to the PowerShell Gallery Administrators, visit your item's detail page and select Contact Support.</span></span>