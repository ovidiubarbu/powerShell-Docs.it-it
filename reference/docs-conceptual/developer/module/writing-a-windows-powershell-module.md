---
title: Scrittura di un modulo di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360620"
---
# <a name="writing-a-windows-powershell-module"></a><span data-ttu-id="5dd9e-102">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-102">Writing a Windows PowerShell Module</span></span>

<span data-ttu-id="5dd9e-103">Questo documento è stato scritto per gli amministratori, gli sviluppatori di script e gli sviluppatori di cmdlet che devono creare pacchetti e distribuire i cmdlet di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-103">This document is written for administrators, script developers, and cmdlet developers who need to package and distribute their Windows PowerShell cmdlets.</span></span> <span data-ttu-id="5dd9e-104">Usando i moduli di Windows PowerShell, è possibile creare pacchetti e distribuire le soluzioni di Windows PowerShell senza usare un linguaggio compilato.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-104">By using Windows PowerShell modules, you can package and distribute your Windows PowerShell solutions without using a compiled language.</span></span>

<span data-ttu-id="5dd9e-105">I moduli di Windows PowerShell consentono di partizionare, organizzare ed estrarre il codice di Windows PowerShell in unità autosufficienti e riutilizzabili.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-105">Windows PowerShell modules enable you to partition, organize, and abstract your Windows PowerShell code into self-contained, reusable units.</span></span> <span data-ttu-id="5dd9e-106">Con queste unità riutilizzabili, è possibile condividere facilmente i moduli direttamente con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-106">With these reusable units, you can easily share your modules directly with others.</span></span> <span data-ttu-id="5dd9e-107">Gli sviluppatori di script possono anche riassemblare moduli di terze parti per creare applicazioni personalizzate basate su script.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-107">If you are a script developer, you can also repackage third-party modules to create custom script-based applications.</span></span> <span data-ttu-id="5dd9e-108">I moduli, simili ai moduli di altri linguaggi di scripting, ad esempio Perl e Python, abilitano soluzioni di scripting pronte per la produzione che usano componenti riutilizzabili e ridistribuibili, con l'ulteriore vantaggio di consentire di riassemblare ed estrarre più componenti in creare soluzioni personalizzate.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-108">Modules, similar to modules in other scripting languages such as Perl and Python, enable production-ready scripting solutions that use reusable, redistributable components, with the added benefit of enabling you to repackage and abstract multiple components to create custom solutions.</span></span>

<span data-ttu-id="5dd9e-109">Al massimo, Windows PowerShell considererà tutti i codici di script di Windows PowerShell validi salvati in un file con estensione psm1 come modulo.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-109">At their most basic, Windows PowerShell will treat any valid Windows PowerShell script code saved in a .psm1 file as a module.</span></span> <span data-ttu-id="5dd9e-110">PowerShell considererà inoltre automaticamente qualsiasi assembly di cmdlet binario come modulo.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-110">PowerShell will also automatically treat any binary cmdlet assembly as a module.</span></span> <span data-ttu-id="5dd9e-111">Tuttavia, è anche possibile usare un modulo (o più specificamente un manifesto del modulo) per raggruppare un'intera soluzione.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-111">However, you can also use a module (or more specifically, a module manifest) to bundle an entire solution together.</span></span> <span data-ttu-id="5dd9e-112">Negli scenari seguenti vengono descritti gli utilizzi tipici dei moduli di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-112">The following scenarios describe typical uses for Windows PowerShell modules.</span></span>

### <a name="libraries"></a><span data-ttu-id="5dd9e-113">Librerie</span><span class="sxs-lookup"><span data-stu-id="5dd9e-113">Libraries</span></span>

<span data-ttu-id="5dd9e-114">I moduli possono essere usati per creare pacchetti e distribuire librerie coerenti di funzioni che eseguono attività comuni.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-114">Modules can be used to package and distribute cohesive libraries of functions that perform common tasks.</span></span> <span data-ttu-id="5dd9e-115">In genere, i nomi di queste funzioni condividono uno o più sostantivi che riflettono l'attività comune per cui vengono usati.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-115">Typically, the names of these functions share one or more nouns that reflect the common task that they are used for.</span></span> <span data-ttu-id="5dd9e-116">Queste funzioni possono anche essere simili alle classi .NET Framework in quanto possono avere membri pubblici e privati.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-116">These functions can also be similar to .NET Framework classes in that they can have public and private members.</span></span> <span data-ttu-id="5dd9e-117">Una libreria, ad esempio, può contenere un set di funzioni per i trasferimenti di file.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-117">For example, a library can contain a set of functions for file transfers.</span></span> <span data-ttu-id="5dd9e-118">In questo caso, il sostantivo che riflette l'attività comune potrebbe essere "file".</span><span class="sxs-lookup"><span data-stu-id="5dd9e-118">In this case, the noun reflecting the common task might be "file."</span></span>

### <a name="configuration"></a><span data-ttu-id="5dd9e-119">Configurazione</span><span class="sxs-lookup"><span data-stu-id="5dd9e-119">Configuration</span></span>

<span data-ttu-id="5dd9e-120">I moduli possono essere utilizzati per personalizzare l'ambiente mediante l'aggiunta di cmdlet, provider, funzioni e variabili specifici.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-120">Modules can be used to customize your environment by adding specific cmdlets, providers, functions, and variables.</span></span>

### <a name="compiled-code-development-and-distribution"></a><span data-ttu-id="5dd9e-121">Sviluppo e distribuzione di codice compilato</span><span class="sxs-lookup"><span data-stu-id="5dd9e-121">Compiled Code Development and Distribution</span></span>

<span data-ttu-id="5dd9e-122">Gli sviluppatori di cmdlet e provider possono utilizzare moduli per testare e distribuire il codice compilato senza la necessità di creare snap-in. Possono importare l'assembly che contiene il codice compilato come modulo (un modulo binario) senza dover creare e registrare gli snap-in.</span><span class="sxs-lookup"><span data-stu-id="5dd9e-122">Cmdlet and provider developers can use modules to test and distribute their compiled code without needing to create snap-ins. They can import the assembly that contains the compiled code as a module (a binary module) without needing to create and register snap-ins.</span></span>

## <a name="see-also"></a><span data-ttu-id="5dd9e-123">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5dd9e-123">See Also</span></span>

[<span data-ttu-id="5dd9e-124">Informazioni su un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-124">Understanding a Windows PowerShell Module</span></span>](./understanding-a-windows-powershell-module.md)

[<span data-ttu-id="5dd9e-125">Come scrivere un modulo di script di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-125">How to Write a PowerShell Script Module</span></span>](./how-to-write-a-powershell-script-module.md)

[<span data-ttu-id="5dd9e-126">Come scrivere un modulo binario di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-126">How to Write a PowerShell Binary Module</span></span>](./how-to-write-a-powershell-binary-module.md)

[<span data-ttu-id="5dd9e-127">Come scrivere un manifesto del modulo PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-127">How to Write a PowerShell Module Manifest</span></span>](how-to-write-a-powershell-module-manifest.md)

[<span data-ttu-id="5dd9e-128">Modifica del percorso di installazione di PSModulePath</span><span class="sxs-lookup"><span data-stu-id="5dd9e-128">Modifying the PSModulePath Installation Path</span></span>](./modifying-the-psmodulepath-installation-path.md)

[<span data-ttu-id="5dd9e-129">Importazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-129">Importing a PowerShell Module</span></span>](./importing-a-powershell-module.md)

[<span data-ttu-id="5dd9e-130">Installazione di un modulo di PowerShell</span><span class="sxs-lookup"><span data-stu-id="5dd9e-130">Installing a PowerShell Module</span></span>](./installing-a-powershell-module.md)
