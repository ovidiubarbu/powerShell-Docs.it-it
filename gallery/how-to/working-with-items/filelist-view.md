---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: Funzionalità FileList in PowerShell Gallery
ms.openlocfilehash: d4d78d4eab89b0e3d48d18ed815d8f77327cc81d
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="filelist-feature-in-the-gallery"></a><span data-ttu-id="36fe7-103">Funzionalità FileList in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="36fe7-103">FileList feature in the Gallery</span></span>

<span data-ttu-id="36fe7-104">È possibile visualizzare il contenuto di tutti gli elementi pubblicati in PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="36fe7-104">You are able to view the contents in all items published in the gallery.</span></span>

<span data-ttu-id="36fe7-105">Questa funzionalità è articolata in due parti: elenco dei file all'interno dell'elemento e visualizzazione del contenuto dei file per i tipi di file supportati.</span><span class="sxs-lookup"><span data-stu-id="36fe7-105">This feature includes two parts: listing the files within the item, and displaying file contents for supported file types.</span></span> <span data-ttu-id="36fe7-106">Attualmente è supportata la visualizzazione del contenuto per le estensioni di file seguenti: ps1, psm1, psd1, ps1xml, xml e txt.</span><span class="sxs-lookup"><span data-stu-id="36fe7-106">Currently we support displaying the contents of the following file extensions: .ps1, .psm1, .psd1, .ps1xml, .xml and .txt.</span></span> <span data-ttu-id="36fe7-107">Nelle prossime versioni saranno supportate altre estensioni di file.</span><span class="sxs-lookup"><span data-stu-id="36fe7-107">We will be supporting more file extensions in the next releases.</span></span>

## <a name="where-to-find-filelist"></a><span data-ttu-id="36fe7-108">Posizione di FileList</span><span class="sxs-lookup"><span data-stu-id="36fe7-108">Where to Find FileList</span></span>

<span data-ttu-id="36fe7-109">In ogni singola pagina dell'elemento sono presenti la sezione FileList e il collegamento **Mostra**.</span><span class="sxs-lookup"><span data-stu-id="36fe7-109">On each individual item page, you will be able to find FileList section and a **Show** link.</span></span> <span data-ttu-id="36fe7-110">Fare clic su Mostra per visualizzare l'elenco completo degli elementi contenuti nell'elemento.</span><span class="sxs-lookup"><span data-stu-id="36fe7-110">Click on the Show and you will find a complete list of items contained in the item.</span></span>

<span data-ttu-id="36fe7-111">Ogni tipo di file supportato viene visualizzato come collegamento ipertestuale. Se si fa clic su di esso, viene aperta una nuova pagina con il contenuto dei file con la sintassi PowerShell evidenziata.</span><span class="sxs-lookup"><span data-stu-id="36fe7-111">Each supported file type is displayed as a hyperlink, and clicking it will take you to a new page with file contents displayed in PowerShell syntax highlighting.</span></span> <span data-ttu-id="36fe7-112">Se si fa clic sul titolo o sulla versione dell'elemento, disponibile nella parte superiore della schermata, viene di nuovo visualizzata la pagina dei dettagli dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="36fe7-112">Clicking on the title or the version of the item, which is displayed at the top of the screen, will bring you back to item detail page.</span></span>