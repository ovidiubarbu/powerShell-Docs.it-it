---
title: Come aggiungere una sezione vedere anche a un argomento della guida del provider | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367840"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a><span data-ttu-id="7bdcd-102">Come aggiungere una sezione Vedere anche a un argomento della Guida dei provider</span><span class="sxs-lookup"><span data-stu-id="7bdcd-102">How to Add a See Also Section to a Provider Help Topic</span></span>

<span data-ttu-id="7bdcd-103">In questa sezione viene illustrato come popolare la sezione **vedere anche** di un argomento della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-103">This section explains how to populate the **SEE ALSO** section of a provider help topic.</span></span>

<span data-ttu-id="7bdcd-104">La sezione **vedere anche** è costituita da un elenco di argomenti correlati al provider o che possono aiutare gli utenti a comprendere e usare il provider.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-104">The **SEE ALSO** section consists of a list of topics that are related to the provider or might help the user better understand and use the provider.</span></span> <span data-ttu-id="7bdcd-105">L'elenco di argomenti può includere la guida per i cmdlet, la guida del provider e gli argomenti della Guida concettuale ("about") in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-105">The topic list can include cmdlet help, provider help and conceptual ("about") help topics in Windows PowerShell.</span></span> <span data-ttu-id="7bdcd-106">Può inoltre includere riferimenti a libri, carta e argomenti online, inclusa una versione online dell'argomento della guida del provider corrente.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-106">It can also include references to books, paper, and online topics, including an online version of the current provider help topic.</span></span>

<span data-ttu-id="7bdcd-107">Quando si fa riferimento agli argomenti online, fornire l'URI o un termine di ricerca in testo normale.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-107">When you refer to online topics, provide the URI or a search term in plain text.</span></span> <span data-ttu-id="7bdcd-108">Il cmdlet `Get-Help` non collega né reindirizza gli argomenti dell'elenco.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-108">The `Get-Help` cmdlet does not link or redirect to any of the topics in the list.</span></span> <span data-ttu-id="7bdcd-109">Inoltre, il parametro `Online` del cmdlet `Get-Help` non funziona con la guida del provider.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-109">Also, the `Online` parameter of the `Get-Help` cmdlet does not work with provider help.</span></span>

<span data-ttu-id="7bdcd-110">La sezione vedere anche viene creata dall'elemento `RelatedLinks` e dai tag in esso contenuti.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-110">The See Also section is created from the `RelatedLinks` element and the tags that it contains.</span></span> <span data-ttu-id="7bdcd-111">Nel codice XML seguente viene illustrato come aggiungere i tag.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-111">The following XML shows how to add the tags.</span></span>

### <a name="to-add-see-also-topics"></a><span data-ttu-id="7bdcd-112">Per aggiungere gli argomenti "vedere anche"</span><span class="sxs-lookup"><span data-stu-id="7bdcd-112">To Add "SEE ALSO" Topics</span></span>

1. <span data-ttu-id="7bdcd-113">Nel file *AssemblyName*. dll-help. XML, all'interno dell'elemento `providerHelp`, aggiungere un elemento `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-113">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `RelatedLinks` element.</span></span> <span data-ttu-id="7bdcd-114">L'elemento `RelatedLinks` deve essere l'ultimo elemento nell'elemento `providerHelp`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-114">The `RelatedLinks` element should be the last element in the `providerHelp` element.</span></span> <span data-ttu-id="7bdcd-115">In ogni argomento della guida del provider è consentito un solo elemento `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-115">Only one `RelatedLinks` element is permitted in each provider help topic.</span></span>

   <span data-ttu-id="7bdcd-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="7bdcd-116">For example:</span></span>

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. <span data-ttu-id="7bdcd-117">Per ogni argomento nella sezione **vedere anche** , all'interno dell'elemento `RelatedLinks`, aggiungere un elemento `navigationLink`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-117">For each topic in the **SEE ALSO** section, within the `RelatedLinks` element, add a `navigationLink` element.</span></span> <span data-ttu-id="7bdcd-118">Quindi, all'interno di ogni elemento `navigationLink`, aggiungere un elemento `linkText` e un elemento `uri`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-118">Then, within each `navigationLink` element, add one `linkText` element and one `uri` element.</span></span> <span data-ttu-id="7bdcd-119">Se non si usa l'elemento `uri`, è possibile aggiungerlo come elemento vuoto (\<uri/>).</span><span class="sxs-lookup"><span data-stu-id="7bdcd-119">If you are not using the `uri` element, you can add it as an empty element (\<uri/>).</span></span>

   <span data-ttu-id="7bdcd-120">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="7bdcd-120">For example:</span></span>

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

3. <span data-ttu-id="7bdcd-121">Digitare il nome dell'argomento tra i tag `linkText`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-121">Type the topic name between the `linkText` tags.</span></span> <span data-ttu-id="7bdcd-122">Se si specifica un URI, digitarlo tra i tag `uri`.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-122">If you are providing a URI, type it between the `uri` tags.</span></span> <span data-ttu-id="7bdcd-123">Per indicare la versione online dell'argomento della guida del provider corrente, tra i tag `linkText`, digitare "versione online:" anziché il nome dell'argomento.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-123">To indicate the online version of the current provider help topic, between the `linkText` tags, type "Online version:" instead of the topic name.</span></span> <span data-ttu-id="7bdcd-124">In genere, il collegamento "versione online:" è il primo argomento nell'elenco vedere anche l'argomento.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-124">Typically, the "Online version:" link is the first topic in the SEE ALSO topic list.</span></span>

   <span data-ttu-id="7bdcd-125">L'esempio seguente include tre argomenti vedere anche.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-125">The following example include three SEE ALSO topics.</span></span> <span data-ttu-id="7bdcd-126">Il primo si riferisce alla versione online dell'argomento corrente.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-126">The first refer to the online version of the current topic.</span></span> <span data-ttu-id="7bdcd-127">Il secondo si riferisce a un argomento della Guida dei cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-127">The second refers to a Windows PowerShell cmdlet help topic.</span></span> <span data-ttu-id="7bdcd-128">Il terzo si riferisce a un altro argomento online.</span><span class="sxs-lookup"><span data-stu-id="7bdcd-128">The third refers to another online topic.</span></span>

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