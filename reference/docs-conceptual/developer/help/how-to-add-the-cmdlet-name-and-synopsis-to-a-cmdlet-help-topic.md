---
title: Come aggiungere il nome del cmdlet e la sinossia a un argomento della guida del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1d0e1eb1-a962-4406-9625-175cfa3364ad
caps.latest.revision: 10
ms.openlocfilehash: f142548be473da15e702f4fa01835609d75b9d51
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361190"
---
# <a name="how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic"></a><span data-ttu-id="de192-102">Come aggiungere il nome dei cmdlet e il riepilogo a un argomento della Guida sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="de192-102">How to Add the Cmdlet Name and Synopsis to a Cmdlet Help Topic</span></span>

<span data-ttu-id="de192-103">In questa sezione viene descritto come aggiungere contenuti che vengono visualizzati nelle sezioni nome e riepilogo della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de192-103">This section describes how to add content that is displayed in the NAME and SYNOPSIS sections of the cmdlet help.</span></span> <span data-ttu-id="de192-104">Nel file della guida, questo contenuto viene aggiunto al nodo del comando per ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de192-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="de192-105">Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de192-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="de192-106">Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="de192-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-the-cmdlet-name-and-a-synopsis"></a><span data-ttu-id="de192-107">Per aggiungere il nome del cmdlet e un riepilogo</span><span class="sxs-lookup"><span data-stu-id="de192-107">To Add the Cmdlet Name and a Synopsis</span></span>

- <span data-ttu-id="de192-108">La guida del cmdlet può visualizzare due descrizioni per il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de192-108">The cmdlet Help can display two descriptions for the cmdlet.</span></span> <span data-ttu-id="de192-109">La prima descrizione è una breve descrizione indicata come sinossia.</span><span class="sxs-lookup"><span data-stu-id="de192-109">The first description is a short description that is referred to as the synopsis.</span></span> <span data-ttu-id="de192-110">La seconda descrizione è una descrizione più dettagliata descritta in [aggiunta della descrizione dettagliata a un argomento della guida del cmdlet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="de192-110">The second description is a more detailed description that is discussed in [Adding the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span> <span data-ttu-id="de192-111">Entrambe queste descrizioni devono essere scritte come un solo paragrafo.</span><span class="sxs-lookup"><span data-stu-id="de192-111">Both these descriptions should be written as a single paragraph.</span></span>

- <span data-ttu-id="de192-112">In sinossia non ripetere il nome del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="de192-112">In the synopsis do not repeat the cmdlet name.</span></span> <span data-ttu-id="de192-113">Informare l'utente che il cmdlet Get-server ottiene un server è Brief, ma non informativo.</span><span class="sxs-lookup"><span data-stu-id="de192-113">Informing the user that the Get-Server cmdlet gets a server is brief, but not informative.</span></span> <span data-ttu-id="de192-114">Usare invece i sinonimi e aggiungere i dettagli alla descrizione.</span><span class="sxs-lookup"><span data-stu-id="de192-114">Instead, use synonyms and add details to the description.</span></span>

  <span data-ttu-id="de192-115">Esempio: "ottiene un oggetto che rappresenta un computer locale o remoto".</span><span class="sxs-lookup"><span data-stu-id="de192-115">Example: "Gets an object that represents a local or remote computer."</span></span>

- <span data-ttu-id="de192-116">Usare verbi semplici come "Get", "create" e "Change" nella sintassi.</span><span class="sxs-lookup"><span data-stu-id="de192-116">Use simple verbs like "get", "create", and "change" in the synopsis.</span></span> <span data-ttu-id="de192-117">Evitare di usare "set" perché è vago e parole fantasiose come "modifica".</span><span class="sxs-lookup"><span data-stu-id="de192-117">Avoid using "set" because it is vague, and fancy words such as "modify."</span></span>

  <span data-ttu-id="de192-118">Esempio: "ottiene informazioni sulla firma Authenticode in un file".</span><span class="sxs-lookup"><span data-stu-id="de192-118">Example: "Gets information about the Authenticode signature in a file."</span></span>

- <span data-ttu-id="de192-119">Scrivi nella voce attiva.</span><span class="sxs-lookup"><span data-stu-id="de192-119">Write in active voice.</span></span> <span data-ttu-id="de192-120">Ad esempio, "usare l'oggetto TimeSpan..." è molto più chiaro di "l'oggetto TimeSpan può essere usato per..."</span><span class="sxs-lookup"><span data-stu-id="de192-120">For example, "Use the TimeSpan object..." is much clearer than "the TimeSpan object can be used to..."</span></span>

- <span data-ttu-id="de192-121">Evitare il verbo "display" quando si descrivono i cmdlet che ottengono oggetti.</span><span class="sxs-lookup"><span data-stu-id="de192-121">Avoid the verb "display" when describing cmdlets that get objects.</span></span> <span data-ttu-id="de192-122">Anche se Windows PowerShell Visualizza i dati dei cmdlet, è importante introdurre gli utenti al concetto che il cmdlet restituisce .NET Framework oggetti i cui dati potrebbero non essere visualizzati.</span><span class="sxs-lookup"><span data-stu-id="de192-122">Although Windows PowerShell displays cmdlet data, it is important to introduce users to the concept that the cmdlet returns .NET Framework objects whose data may not be displayed.</span></span> <span data-ttu-id="de192-123">Se si enfatizza la visualizzazione, è possibile che l'utente non renda conto che il cmdlet potrebbe avere restituito molte altre proprietà e metodi utili che non vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="de192-123">If you emphasize the display, the user might not realize that the cmdlet may have returned many other useful properties and methods that are not displayed.</span></span>

## <a name="see-also"></a><span data-ttu-id="de192-124">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="de192-124">See Also</span></span>

 [<span data-ttu-id="de192-125">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="de192-125">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)