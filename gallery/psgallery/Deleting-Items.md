---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Eliminazione di elementi
ms.openlocfilehash: f82d80a35f51227c4671bd2b15a7d1c16f0ba0a8
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="deleting-items"></a><span data-ttu-id="24a85-103">Eliminazione di elementi</span><span class="sxs-lookup"><span data-stu-id="24a85-103">Deleting items</span></span>

<span data-ttu-id="24a85-104">PowerShell Gallery non supporta l'eliminazione permanente di elementi perché questo impedirebbe la disponibilità di altri elementi dipendenti da quelli eliminati.</span><span class="sxs-lookup"><span data-stu-id="24a85-104">The PowerShell Gallery does not support permanent deletion of items, because that would break anyone who is depending on it remaining available.</span></span>

<span data-ttu-id="24a85-105">PowerShell Gallery supporta invece un modo per "escludere dall'elenco" un elemento, operazione che può essere eseguita nella pagina di gestione dell'elemento sul sito Web.</span><span class="sxs-lookup"><span data-stu-id="24a85-105">Instead, the PowerShell Gallery supports a way to 'unlist' an item, which can be done in the item management page on the web site.</span></span>
<span data-ttu-id="24a85-106">Quando un elemento viene escluso dall'elenco, non viene più individuato dalle ricerche e non viene visualizzato in nessun elenco di elementi, né in PowerShell Gallery né usando i comandi PowerShellGet.</span><span class="sxs-lookup"><span data-stu-id="24a85-106">When an item is unlisted, it no longer shows up in search and in any item listing, both on the PowerShell Gallery and using PowerShellGet commands.</span></span>
<span data-ttu-id="24a85-107">È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.</span><span class="sxs-lookup"><span data-stu-id="24a85-107">However, it remains downloadable by specifying its exact version, which is what allows the automated scripts to continue working.</span></span>

<span data-ttu-id="24a85-108">Se si verifica una situazione eccezionale che richiede l'eliminazione di un elemento, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="24a85-108">If you run into an exceptional situation where you think one of your items must be deleted, this can be handled manually by the PowerShell Gallery team.</span></span>
<span data-ttu-id="24a85-109">Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione.</span><span class="sxs-lookup"><span data-stu-id="24a85-109">For example, if there is a copyright infringement issue, or potentially harmful content, that could be a valid reason to delete it.</span></span>
<span data-ttu-id="24a85-110">In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery] (http://www.PowerShellGallery.com).</span><span class="sxs-lookup"><span data-stu-id="24a85-110">You should submit a support request through [PowerShell Gallery] (http://www.PowerShellGallery.com) in that case.</span></span>