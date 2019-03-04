---
title: Come aggiungere un vedere anche sezione a un argomento della Guida di Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858347"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="3fe4e-102">Come aggiungere una sezione Vedere anche a un argomento della Guida dei provider</span><span class="sxs-lookup"><span data-stu-id="3fe4e-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="3fe4e-103">In questa sezione illustra come popolare la **vedere anche** sezione di un argomento della Guida di provider.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="3fe4e-104">Il **vedere anche** sezione è costituita da un elenco di argomenti che sono correlati al provider o può consentire all'utente di comprendere meglio e usare il provider.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="3fe4e-105">Nell'elenco di argomenti può includere cmdlet help, Guida del provider e concettuale ("about"), gli argomenti della Guida in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="3fe4e-106">Anche possibile includere riferimenti a libri, documento e gli argomenti online, tra cui una versione online dell'argomento della Guida di provider corrente.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="3fe4e-107">Quando si fa riferimento ad argomenti in linea, fornire l'URI o un termine di ricerca in testo normale.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="3fe4e-108">Il `Get-Help` cmdlet non collegare o reindirizzare a uno degli argomenti nell'elenco.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="3fe4e-109">Inoltre, il `Online` parametro del `Get-Help` cmdlet non funziona con l'aiuto di provider.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="3fe4e-110">La sezione Vedere anche viene creata dal `RelatedLinks` elemento e i tag in esso contenuti.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="3fe4e-111">Il codice XML seguente viene illustrato come aggiungere i tag.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="3fe4e-112">Per aggiungere gli argomenti "Vedere anche"</span><span class="sxs-lookup"><span data-stu-id="3fe4e-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="3fe4e-113">Nel *AssemblyName*nel file con estensione dll help.xml, all'interno di `providerHelp` elemento, aggiungere un `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="3fe4e-114">Il `RelatedLinks` elemento deve essere l'ultimo elemento di `providerHelp` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="3fe4e-115">Un solo `RelatedLinks` elemento è consentito in ogni argomento della Guida di provider.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="3fe4e-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fe4e-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="3fe4e-117">Per ogni argomento nel **vedere anche** sezione, all'interno di `RelatedLinks` elemento, aggiungere un `navigationLink` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="3fe4e-118">Quindi, all'interno di ciascun `navigationLink` elemento, aggiungerne uno `linkText` elemento e l'altra `uri` elemento.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="3fe4e-119">Se non si usa la `uri` elemento, è possibile aggiungerlo come elemento vuoto (\<uri / >).</span><span class="sxs-lookup"><span data-stu-id="3fe4e-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="3fe4e-120">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3fe4e-120">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

3. <span data-ttu-id="3fe4e-121">Digitare il nome dell'argomento tra il `linkText` tag.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="3fe4e-122">Se si specifica un URI, digitarla tra il `uri` tag.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="3fe4e-123">Per indicare la versione online dell'argomento della Guida del provider corrente, tra il `linkText` tag, digitare "versione Online:" anziché il nome dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="3fe4e-124">In genere, la "versione Online:" collegamento è il primo argomento dell'elenco di argomento vedere anche.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="3fe4e-125">Nell'esempio seguente include tre argomenti Vedere anche.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="3fe4e-126">Il primo fare riferimento alla versione online dell'argomento corrente.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="3fe4e-127">Il secondo fa riferimento a un argomento della Guida cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="3fe4e-128">Il terzo fa riferimento a un altro argomento online.</span><span class="sxs-lookup"><span data-stu-id="3fe4e-128">The third refers to another online topic.</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```