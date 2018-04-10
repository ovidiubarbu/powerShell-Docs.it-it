---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7eaa4dfb68bc299ad31bce81af96b6a760c4fcc5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="creating-custom-types-using-powershell-classes"></a><span data-ttu-id="a0e37-102">Creazione di tipi personalizzati con le classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e37-102">Creating Custom Types using PowerShell Classes</span></span>

<span data-ttu-id="a0e37-103">È stato migliorato il linguaggio di PowerShell per la definizione di classi e altri tipi definiti dall'utente usando sintassi e semantica formali simili ad altri linguaggi di programmazione orientata agli oggetti.</span><span class="sxs-lookup"><span data-stu-id="a0e37-103">We’ve improved the PowerShell language for defining classes and other user-defined types by using formal syntax and semantics that are similar to other object-oriented programming languages.</span></span> <span data-ttu-id="a0e37-104">L'obiettivo è consentire agli sviluppatori e ai professionisti IT di adottare PowerShell per una vasta gamma di casi d'uso, semplificare lo sviluppo di artefatti di PowerShell (ad esempio risorse DSC) e velocizzare la copertura delle aree di gestione.</span><span class="sxs-lookup"><span data-stu-id="a0e37-104">The goal is to enable developers and IT professionals to embrace PowerShell for a wider range of use cases, simplify development of PowerShell artifacts (such as DSC resources), and accelerate coverage of management surfaces.</span></span>

## <a name="supported-scenarios-in-this-release"></a><span data-ttu-id="a0e37-105">Scenari supportati in questa versione</span><span class="sxs-lookup"><span data-stu-id="a0e37-105">Supported scenarios in this release</span></span>

-   <span data-ttu-id="a0e37-106">Definire risorse DSC e i relativi tipi associati usando il linguaggio di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e37-106">Define DSC resources and their associated types by using the PowerShell language</span></span>
-   <span data-ttu-id="a0e37-107">Definire tipi personalizzati in PowerShell usando costrutti noti della programmazione orientata agli oggetti, come classi, proprietà, metodi e così via.</span><span class="sxs-lookup"><span data-stu-id="a0e37-107">Define custom types in PowerShell by using familiar object-oriented programming constructs, such as classes, properties, methods, etc.</span></span>
-   <span data-ttu-id="a0e37-108">Supporto dell'ereditarietà con le classi in PowerShell e le risorse DSC basate su classi</span><span class="sxs-lookup"><span data-stu-id="a0e37-108">Inheritance support with class in PowerShell and class base DSC resource</span></span>
-   <span data-ttu-id="a0e37-109">Eseguire il debug di tipi con il linguaggio di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a0e37-109">Debug types by using the PowerShell language</span></span>
-   <span data-ttu-id="a0e37-110">Generare e gestire le eccezioni tramite meccanismi formali, al giusto livello</span><span class="sxs-lookup"><span data-stu-id="a0e37-110">Generate and handle exceptions by using formal mechanisms, and at the right level</span></span>