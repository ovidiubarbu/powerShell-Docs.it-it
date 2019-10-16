---
title: Come aggiungere una descrizione del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361280"
---
# <a name="how-to-add-a-cmdlet-description"></a><span data-ttu-id="ce2c4-102">Come aggiungere una descrizione del cmdlet</span><span class="sxs-lookup"><span data-stu-id="ce2c4-102">How to Add a Cmdlet Description</span></span>

<span data-ttu-id="ce2c4-103">In questa sezione viene descritto come aggiungere contenuto che viene visualizzato nella sezione Descrizione della guida del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-103">This section describes how to add content that is displayed in the DESCRIPTION section of the cmdlet Help.</span></span> <span data-ttu-id="ce2c4-104">Nel file della guida, questo contenuto viene aggiunto al nodo del comando per ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-104">In the Help file, this content is added to the Command node for each cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="ce2c4-105">Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="ce2c4-106">Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="to-add-a-description"></a><span data-ttu-id="ce2c4-107">Per aggiungere una descrizione</span><span class="sxs-lookup"><span data-stu-id="ce2c4-107">To Add a Description</span></span>

- <span data-ttu-id="ce2c4-108">Per iniziare, è necessario illustrare in modo più dettagliato le funzionalità di base del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-108">Begin by explaining the basic features of the cmdlet in more detail.</span></span> <span data-ttu-id="ce2c4-109">In molti casi, è possibile spiegare i termini usati nel nome del cmdlet e illustrare concetti non noti con un esempio.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-109">In many cases, you can explain the terms used in the cmdlet name and illustrate unfamiliar concepts with an example.</span></span> <span data-ttu-id="ce2c4-110">Se, ad esempio, il cmdlet aggiunge dati a un file, spiega che aggiunge dati alla fine di un file esistente.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-110">For example, if the cmdlet appends data to a file, explain that it adds data to the end of an existing file.</span></span>

- <span data-ttu-id="ce2c4-111">Per trovare tutte le funzionalità del cmdlet, esaminare l'elenco dei parametri.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-111">To find all of the features of the cmdlet, review the parameter list.</span></span> <span data-ttu-id="ce2c4-112">Descrivere la funzione principale del cmdlet e quindi includere altre funzioni e funzionalità.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-112">Describe the primary function of the cmdlet, and then include other functions and features.</span></span> <span data-ttu-id="ce2c4-113">Se, ad esempio, la funzione principale del cmdlet è la modifica di una proprietà, ma il cmdlet può modificare tutte le proprietà, ad esempio nella descrizione dettagliata.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-113">For example, if the main function of the cmdlet is to change one property, but the cmdlet can change all of the properties, say so in the detailed description.</span></span> <span data-ttu-id="ce2c4-114">Se i parametri del cmdlet consentono agli utenti di richiedere informazioni in modi diversi, spiegarlo.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-114">If the cmdlet parameters let the users solicit information in different ways, explain it.</span></span>

- <span data-ttu-id="ce2c4-115">Includere informazioni sui modi in cui gli utenti possono utilizzare il cmdlet, oltre agli utilizzi più evidenti.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-115">Include information on ways that users can use the cmdlet, in addition to the obvious uses.</span></span> <span data-ttu-id="ce2c4-116">Ad esempio, è possibile usare l'oggetto recuperato dal cmdlet `Get-Host` per modificare il colore del testo nella finestra di comando di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-116">For example, you can use the object that the `Get-Host` cmdlet retrieves to change the color of text in the Windows PowerShell command window.</span></span>

  <span data-ttu-id="ce2c4-117">Esempio: "il cmdlet `Get-Acl` Ottiene gli oggetti che rappresentano il descrittore di sicurezza di un file o di una risorsa.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-117">Example:  "The `Get-Acl` cmdlet gets objects that represent the security descriptor of a file or resource.</span></span> <span data-ttu-id="ce2c4-118">Il descrittore di sicurezza contiene gli elenchi di controllo di accesso della risorsa.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-118">The security descriptor contains the access control lists (ACLs) of the resource.</span></span> <span data-ttu-id="ce2c4-119">L'ACL specifica le autorizzazioni che gli utenti e i gruppi di utenti devono accedere alla risorsa ".</span><span class="sxs-lookup"><span data-stu-id="ce2c4-119">The ACL specifies the permissions that users and user groups have to access the resource."</span></span>

- <span data-ttu-id="ce2c4-120">La descrizione dettagliata dovrebbe descrivere il cmdlet, ma non deve descrivere i concetti usati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-120">The detailed description should describe the cmdlet, but it should not describe concepts that the cmdlet uses.</span></span> <span data-ttu-id="ce2c4-121">Inserire le definizioni dei concetti in note aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="ce2c4-121">Place concept definitions in Additional Notes.</span></span>

## <a name="see-also"></a><span data-ttu-id="ce2c4-122">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ce2c4-122">See Also</span></span>

[<span data-ttu-id="ce2c4-123">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ce2c4-123">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
