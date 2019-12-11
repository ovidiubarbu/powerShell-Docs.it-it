---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Esclusione di pacchetti dall'elenco
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328272"
---
# <a name="unlisting-packages"></a><span data-ttu-id="c34ab-103">Esclusione di pacchetti dall'elenco</span><span class="sxs-lookup"><span data-stu-id="c34ab-103">Unlisting Packages</span></span>

<span data-ttu-id="c34ab-104">**Perché la rimozione di un pacchetto da PowerShell Gallery non è disponibile come opzione?**</span><span class="sxs-lookup"><span data-stu-id="c34ab-104">**Why is removing a package from PowerShell Gallery not exposed as an option?**</span></span>

<span data-ttu-id="c34ab-105">PowerShell Gallery non supporta l'eliminazione permanente di pacchetti da parte degli utenti.</span><span class="sxs-lookup"><span data-stu-id="c34ab-105">The PowerShell Gallery does not support users permanently deleting their packages.</span></span>
<span data-ttu-id="c34ab-106">Questo consente ad altre persone di creare dipendenze dai pacchetti di un utente senza preoccupazioni per possibili interruzioni nel futuro.</span><span class="sxs-lookup"><span data-stu-id="c34ab-106">This enables others to take dependencies on your packages without worrying about possible breaks in the future.</span></span>
<span data-ttu-id="c34ab-107">Se, ad esempio, il modulo Pester dipende dal modulo Azure e quest'ultimo viene rimosso da PowerShell Gallery, l'utente non può più usare il modulo Pester.</span><span class="sxs-lookup"><span data-stu-id="c34ab-107">For example, if the Pester module depends on the Azure module and the Azure module is removed from the gallery, then user can no longer uses the Pester module.</span></span>

<span data-ttu-id="c34ab-108">Anziché rimuovere un pacchetto, tuttavia, è possibile escluderlo dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="c34ab-108">Instead of removing an package, however, you can unlist it instead.</span></span>

<span data-ttu-id="c34ab-109">**Quali sono le conseguenze dell'esclusione di un pacchetto dall'elenco in PowerShell Gallery?**</span><span class="sxs-lookup"><span data-stu-id="c34ab-109">**What does unlisting a package on PowerShell Gallery do?**</span></span>

<span data-ttu-id="c34ab-110">L'esclusione di un pacchetto dall'elenco, ad esempio un modulo o uno script, in PowerShell Gallery determina la rimozione di tale elemento dalla scheda Packages (Pacchetti). I pacchetti esclusi dall'elenco, inoltre, non possono essere individuati usando la barra di ricerca.</span><span class="sxs-lookup"><span data-stu-id="c34ab-110">Unlisting a package such as module or script on PowerShell Gallery will remove it from the Packages tab. In addition, unlisted packages will not be discoverable using the search bar.</span></span>
<span data-ttu-id="c34ab-111">Il solo modo per scaricare un pacchetto escluso dall'elenco consiste nello specificarne esattamente il nome e la versione.</span><span class="sxs-lookup"><span data-stu-id="c34ab-111">The only way to download an unlisted package is to specify the exact name and version of the package.</span></span>
<span data-ttu-id="c34ab-112">Per questo motivo, l'esclusione di un pacchetto dall'elenco non causa interruzioni per altri moduli o script dipendenti.</span><span class="sxs-lookup"><span data-stu-id="c34ab-112">Because of this, the unlisting of an package will not break other modules or scripts that depend on it.</span></span>

<span data-ttu-id="c34ab-113">Per escludere il pacchetto dall'elenco, visitare la pagina dei dettagli del pacchetto e selezionare 'Delete Module' (Elimina modulo).</span><span class="sxs-lookup"><span data-stu-id="c34ab-113">To unlist your package, visit the package details page and select 'Delete Module'.</span></span> <span data-ttu-id="c34ab-114">Deselezionare la casella di controllo 'Listed' (Elencato) e fare clic su Salva.</span><span class="sxs-lookup"><span data-stu-id="c34ab-114">Uncheck the 'Listed' checkbox, and click Save.</span></span>

<span data-ttu-id="c34ab-115">**In che modo è possibile rimuovere un pacchetto?**</span><span class="sxs-lookup"><span data-stu-id="c34ab-115">**How can I remove an package?**</span></span>

<span data-ttu-id="c34ab-116">Se si verifica uno scenario in cui è necessario eliminare un pacchetto, contattare gli amministratori di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="c34ab-116">If you experience a scenario where package deletion is necessary, contact the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="c34ab-117">Gli scenari di eliminazione validi sono i seguenti:</span><span class="sxs-lookup"><span data-stu-id="c34ab-117">Valid deletion scenarios are:</span></span>
- <span data-ttu-id="c34ab-118">Problemi relativi alla violazione del copyright.</span><span class="sxs-lookup"><span data-stu-id="c34ab-118">Issues of copyright infringement.</span></span>
- <span data-ttu-id="c34ab-119">Pacchetti con contenuto potenzialmente dannoso.</span><span class="sxs-lookup"><span data-stu-id="c34ab-119">Package contains potentially harmful content.</span></span>
- <span data-ttu-id="c34ab-120">Pacchetti contenenti dati sensibili.</span><span class="sxs-lookup"><span data-stu-id="c34ab-120">Package contains sensitive data.</span></span>

<span data-ttu-id="c34ab-121">Per inviare una richiesta di eliminazione di un pacchetto agli amministratori di PowerShell Gallery, visitare la pagina dei dettagli del pacchetto e selezionare Contact Support (Contattare il supporto tecnico).</span><span class="sxs-lookup"><span data-stu-id="c34ab-121">To submit a Delete Package Request to the PowerShell Gallery Administrators, visit your package's detail page and select Contact Support.</span></span>
