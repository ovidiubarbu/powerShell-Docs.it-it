---
title: Scrittura di un modulo di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 3c6d8e410427d6cfaa1c15db421b3fe935f7d322
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082057"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="24f8f-102">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="24f8f-103">Questo documento è scritto per gli amministratori, sviluppatori di script e gli sviluppatori di cmdlet che hanno bisogno per creare un pacchetto e distribuire i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24f8f-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="24f8f-104">Usando moduli di Windows PowerShell, è possibile creare un pacchetto e distribuire soluzioni di Windows PowerShell senza usare un linguaggio compilato.</span><span class="sxs-lookup"><span data-stu-id="24f8f-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="24f8f-105">I moduli di Windows PowerShell consentono di partizione, organizzare e astraggono del codice di Windows PowerShell in unità indipendente e riutilizzabile.</span><span class="sxs-lookup"><span data-stu-id="24f8f-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="24f8f-106">Con queste unità riutilizzabile, è possibile condividere facilmente i moduli direttamente con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="24f8f-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="24f8f-107">Se sei uno sviluppatore di script, è anche possibile riassemblare i moduli di terze parti per creare applicazioni personalizzate basate su script.</span><span class="sxs-lookup"><span data-stu-id="24f8f-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="24f8f-108">I moduli, simili a moduli in altri linguaggi di script come Perl e Python, abilitare soluzioni di scripting di produzione che usano i componenti ridistribuibili e riutilizzabili, con l'ulteriore vantaggio di poter ricreare il pacchetto e astrarre più componenti creare soluzioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="24f8f-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="24f8f-109">Al loro più elementare, Windows PowerShell considererà qualsiasi codice di script Windows PowerShell validi salvato in un file con estensione psm1 come modulo.</span><span class="sxs-lookup"><span data-stu-id="24f8f-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="24f8f-110">PowerShell considererà automaticamente anche tutti gli assembly binari cmdlet come un modulo.</span><span class="sxs-lookup"><span data-stu-id="24f8f-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="24f8f-111">Tuttavia, è possibile utilizzare anche un modulo o, più specificamente, un manifesto del modulo per raccogliere un'intera soluzione.</span><span class="sxs-lookup"><span data-stu-id="24f8f-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="24f8f-112">Di seguito sono descritti gli utilizzi tipici dei moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="24f8f-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="24f8f-113">Librerie</span><span class="sxs-lookup"><span data-stu-id="24f8f-113">Libraries</span></span>

<span data-ttu-id="24f8f-114">I moduli possono essere usati assemblare e distribuire le librerie coesa di funzioni che eseguono attività comuni.</span><span class="sxs-lookup"><span data-stu-id="24f8f-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="24f8f-115">In genere, i nomi di queste funzioni condividono uno o più sostantivi che riflettono l'attività più comune che vengono utilizzati per.</span><span class="sxs-lookup"><span data-stu-id="24f8f-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="24f8f-116">Queste funzioni possono anche essere simile a classi di .NET Framework in quanto possono avere membri privati e pubblici.</span><span class="sxs-lookup"><span data-stu-id="24f8f-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="24f8f-117">Ad esempio, una libreria può contenere un set di funzioni per i trasferimenti di file.</span><span class="sxs-lookup"><span data-stu-id="24f8f-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="24f8f-118">In questo caso, il sostantivo che riflettono l'attività comune potrebbe essere "file".</span><span class="sxs-lookup"><span data-stu-id="24f8f-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="24f8f-119">Configurazione</span><span class="sxs-lookup"><span data-stu-id="24f8f-119">Configuration</span></span>

<span data-ttu-id="24f8f-120">I moduli possono essere usati per personalizzare l'ambiente mediante l'aggiunta di variabili, i provider, funzioni e cmdlet specifici.</span><span class="sxs-lookup"><span data-stu-id="24f8f-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="24f8f-121">Sviluppo di codice compilato e la distribuzione</span><span class="sxs-lookup"><span data-stu-id="24f8f-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="24f8f-122">Gli sviluppatori di cmdlet e provider possono usare i moduli a testare e distribuire il proprio codice compilato senza dover creare snap-in. È possibile importare l'assembly che contiene il codice compilato come modulo (un modulo binario) senza la necessità di creare e registrare gli snap-in.</span><span class="sxs-lookup"><span data-stu-id="24f8f-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="24f8f-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="24f8f-123">See Also</span></span>

[<span data-ttu-id="24f8f-124">Understanding a PowerShell Module di Windows</span><span class="sxs-lookup"><span data-stu-id="24f8f-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="24f8f-125">Come scrivere un modulo di Script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="24f8f-126">Come scrivere un modulo di file binari di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="24f8f-127">Come scrivere un manifesto del modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-127">How to Write a PowerShell Module Manifest</span></span>](http://msdn.microsoft.com/en-us/abe4c24b-e64e-4a61-81d5-18c4fceba0b6)

[<span data-ttu-id="24f8f-128">Modifica il percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="24f8f-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="24f8f-129">Importazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="24f8f-130">Installazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="24f8f-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
