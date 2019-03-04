---
title: Come aggiungere il nome di Cmdlet e il riepilogo per un argomento della Guida Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861827"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="0af49-102">Come aggiungere il nome dei cmdlet e il riepilogo a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="0af49-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="0af49-103">Questa sezione descrive come aggiungere contenuto che viene visualizzato nelle sezioni nome e il riepilogo della Guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0af49-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="0af49-104">Nel file della Guida, questo contenuto viene aggiunto al nodo del comando per ciascun cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0af49-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="0af49-105">Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0af49-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="0af49-106">Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0af49-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="0af49-107">Per aggiungere il nome del Cmdlet e un riepilogo</span><span class="sxs-lookup"><span data-stu-id="0af49-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="0af49-108">La Guida dei cmdlet è possibile visualizzare due descrizioni del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0af49-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="0af49-109">La descrizione prima è una breve descrizione che viene definita il riepilogo.</span><span class="sxs-lookup"><span data-stu-id="0af49-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="0af49-110">La seconda descrizione è una descrizione più dettagliata che verrà discusso [aggiunta la descrizione dettagliata per un argomento della Guida Cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="0af49-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="0af49-111">Entrambe queste descrizioni devono essere scritti come un paragrafo unico.</span><span class="sxs-lookup"><span data-stu-id="0af49-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="0af49-112">Il riepilogo non si ripetono il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="0af49-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="0af49-113">Per informare l'utente che il cmdlet Get-Server Ottiene un server è breve, ma non informativi.</span><span class="sxs-lookup"><span data-stu-id="0af49-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="0af49-114">Al contrario, uso dei sinonimi e aggiungere i dettagli per la descrizione.</span><span class="sxs-lookup"><span data-stu-id="0af49-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="0af49-115">Esempio: "Ottiene un oggetto che rappresenta un computer locale o remoto."</span><span class="sxs-lookup"><span data-stu-id="0af49-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="0af49-116">Usare verbi semplici, ad esempio "get", "Crea" e "Modifica" il riepilogo.</span><span class="sxs-lookup"><span data-stu-id="0af49-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="0af49-117">Evitare di usare "set" perché è vaga e fantasiosi parole come "la modifica."</span><span class="sxs-lookup"><span data-stu-id="0af49-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="0af49-118">Esempio: "Ottiene informazioni sulla firma Authenticode in un file".</span><span class="sxs-lookup"><span data-stu-id="0af49-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="0af49-119">Scrivere in forma attiva.</span><span class="sxs-lookup"><span data-stu-id="0af49-119">Write in active voice.</span></span> <span data-ttu-id="0af49-120">Ad esempio, "Usa l'oggetto TimeSpan..." è molto più chiaro rispetto a "l'oggetto TimeSpan utilizzabile per..."</span><span class="sxs-lookup"><span data-stu-id="0af49-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="0af49-121">Evitare il verbo "display" quando si descrivono i cmdlet che ottiene gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="0af49-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="0af49-122">Anche se Windows PowerShell consente di visualizzare i dati di cmdlet, è importante per introdurre gli utenti per il concetto che il cmdlet restituisce gli oggetti di .NET Framework i cui dati potrebbero non essere visualizzati.</span><span class="sxs-lookup"><span data-stu-id="0af49-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="0af49-123">Se si evidenziazione la visualizzazione, l'utente potrebbe non essere consapevoli che il cmdlet potrebbe avere restituito molte altre proprietà e metodi utili che non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="0af49-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="0af49-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0af49-124">See Also</span></span>

 [<span data-ttu-id="0af49-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="0af49-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)