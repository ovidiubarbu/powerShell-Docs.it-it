---
title: Come aggiungere una descrizione del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862597"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="c976b-102">Come aggiungere una descrizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="c976b-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="c976b-103">Questa sezione descrive come aggiungere il contenuto visualizzato nella sezione Descrizione del cmdlet Help.</span><span class="sxs-lookup"><span data-stu-id="c976b-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="c976b-104">Nel file della Guida, questo contenuto viene aggiunto al nodo del comando per ciascun cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c976b-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="c976b-105">Per una panoramica completa di un file della Guida, aprire un file dll Help.xml che si trova nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c976b-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="c976b-106">Ad esempio, il file Microsoft.PowerShell.Commands.Management.dll Help.xml contiene contenuto per molti dei cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c976b-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="c976b-107">Per aggiungere una descrizione</span><span class="sxs-lookup"><span data-stu-id="c976b-107">To Add a Description</span></span>

- <span data-ttu-id="c976b-108">Inizia illustrando le funzionalità di base del cmdlet in modo più dettagliato.</span><span class="sxs-lookup"><span data-stu-id="c976b-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="c976b-109">In molti casi, è possibile spiegare i termini utilizzati nel nome del cmdlet e illustrare i concetti di familiari con un esempio.</span><span class="sxs-lookup"><span data-stu-id="c976b-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="c976b-110">Ad esempio, se il cmdlet aggiunge i dati in un file, illustrano che aggiunge i dati alla fine di un file esistente.</span><span class="sxs-lookup"><span data-stu-id="c976b-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="c976b-111">Per trovare tutte le funzionalità del cmdlet, esaminare l'elenco di parametri.</span><span class="sxs-lookup"><span data-stu-id="c976b-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="c976b-112">Descrivere la funzione principale del cmdlet e quindi includere altre funzioni e funzionalità.</span><span class="sxs-lookup"><span data-stu-id="c976b-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="c976b-113">Ad esempio, se la funzione principale del cmdlet consiste nel modificare una proprietà, ma il cmdlet può modificare tutte le proprietà, ad esempio, nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="c976b-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="c976b-114">Se i parametri del cmdlet consentono agli utenti di sollecitazione informazioni in modi diversi, trattazione.</span><span class="sxs-lookup"><span data-stu-id="c976b-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="c976b-115">Includere informazioni sui metodi che gli utenti possono usare il cmdlet, oltre all'Usa ovvia.</span><span class="sxs-lookup"><span data-stu-id="c976b-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="c976b-116">Ad esempio, è possibile usare l'oggetto che il `Get-Host` cmdlet recupera per modificare il colore del testo nella finestra di comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c976b-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="c976b-117">Esempio:  "Il `Get-Acl` cmdlet recupera gli oggetti che rappresentano il descrittore di sicurezza di un file o una risorsa.</span><span class="sxs-lookup"><span data-stu-id="c976b-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="c976b-118">Il descrittore di sicurezza contiene gli elenchi di controllo di accesso della risorsa.</span><span class="sxs-lookup"><span data-stu-id="c976b-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="c976b-119">L'elenco ACL consente di specificare le relative autorizzazioni utenti e gruppi di utenti per accedere alla risorsa."</span><span class="sxs-lookup"><span data-stu-id="c976b-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="c976b-120">La descrizione dettagliata deve descrivere il cmdlet, ma non dovrebbe descrivere i concetti che usa il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c976b-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="c976b-121">Posizionare le definizioni di concetto in note aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="c976b-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="c976b-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c976b-122">See Also</span></span>

[<span data-ttu-id="c976b-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c976b-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
