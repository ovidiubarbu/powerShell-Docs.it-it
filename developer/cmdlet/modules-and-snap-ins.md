---
title: I moduli e Snap-in | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2d342f91-23e0-467f-8de2-f9657d820693
caps.latest.revision: 6
ms.openlocfilehash: 157cd64e286392f3fd770e1e34542682b1e63625
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860497"
---
# <a name="modules-and-snap-ins"></a><span data-ttu-id="ede63-102">Moduli e snap-in</span><span class="sxs-lookup"><span data-stu-id="ede63-102">Modules and Snap-ins</span></span>

<span data-ttu-id="ede63-103">I cmdlet possono essere aggiunti tramite moduli (introdotti da Windows PowerShell 2.0) o gli snap-in a una sessione. Dopo aver aggiunto il cmdlet alla sessione che può essere eseguita a livello di codice da un'applicazione host o in modo interattivo dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="ede63-103">Cmdlets can be added to a session using modules (introduced by Windows PowerShell 2.0) or snap-ins. Once the cmdlet is added to the session it can be run programmatically by a host application or interactively at the command line.</span></span>

<span data-ttu-id="ede63-104">È consigliabile usare i moduli come il metodo di recapito per l'aggiunta di cmdlet per una sessione per i motivi seguenti:</span><span class="sxs-lookup"><span data-stu-id="ede63-104">We recommend that you use modules as the delivery method for adding cmdlets to a session for the following reasons:</span></span>

- <span data-ttu-id="ede63-105">I moduli consentono di aggiungere i cmdlet per il caricamento dell'assembly in cui è definito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ede63-105">Modules allow you to add cmdlets by loading the assembly where the cmdlet is defined.</span></span> <span data-ttu-id="ede63-106">Non è necessario implementare una classe di snap-in.</span><span class="sxs-lookup"><span data-stu-id="ede63-106">There is no need to implement a snap-in class.</span></span>

- <span data-ttu-id="ede63-107">I moduli consentono di aggiungere altre risorse, ad esempio variabili, funzioni, script, i tipi e formattazione file e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="ede63-107">Modules allow you to add other resources, such as variables, functions, scripts, types and formatting files, and more.</span></span>

- <span data-ttu-id="ede63-108">Gli snap-in è utilizzabile solo per aggiungere i cmdlet e provider alla sessione.</span><span class="sxs-lookup"><span data-stu-id="ede63-108">Snap-ins can be used only to add cmdlets and providers to the session.</span></span>

## <a name="see-also"></a><span data-ttu-id="ede63-109">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ede63-109">See Also</span></span>

[<span data-ttu-id="ede63-110">Scrittura di un modulo di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ede63-110">Writing a Windows PowerShell Module</span></span>](../module/writing-a-windows-powershell-module.md)

[<span data-ttu-id="ede63-111">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ede63-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
