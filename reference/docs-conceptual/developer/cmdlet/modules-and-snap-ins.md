---
title: Moduli e snap-in | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365370"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="c0dab-102">Moduli e snap-in</span><span class="sxs-lookup"><span data-stu-id="c0dab-102">Modules and Snap-ins</span></span>

<span data-ttu-id="c0dab-103">I cmdlet possono essere aggiunti a una sessione usando i moduli (introdotti da Windows PowerShell 2,0) o gli snap-in. Una volta aggiunto il cmdlet alla sessione, può essere eseguito a livello di codice da un'applicazione host o in modo interattivo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="c0dab-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="c0dab-104">È consigliabile usare i moduli come metodo di recapito per aggiungere cmdlet a una sessione per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="c0dab-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="c0dab-105">I moduli consentono di aggiungere cmdlet caricando l'assembly in cui è definito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c0dab-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="c0dab-106">Non è necessario implementare una classe snap-in.</span><span class="sxs-lookup"><span data-stu-id="c0dab-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="c0dab-107">I moduli consentono di aggiungere altre risorse, ad esempio variabili, funzioni, script, tipi e file di formattazione e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="c0dab-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="c0dab-108">Gli snap-in possono essere utilizzati solo per aggiungere cmdlet e provider alla sessione.</span><span class="sxs-lookup"><span data-stu-id="c0dab-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="c0dab-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c0dab-109">See Also</span></span>

[<span data-ttu-id="c0dab-110">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0dab-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="c0dab-111">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c0dab-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
