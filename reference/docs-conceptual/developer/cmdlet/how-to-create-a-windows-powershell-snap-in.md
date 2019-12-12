---
title: Come creare uno snap-in di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- snap-ins [PowerShell SDK], examples
ms.assetid: 71bd9b2c-5f2e-4aa8-b5fe-08c956540d37
caps.latest.revision: 10
ms.openlocfilehash: 43199544dc02ccae4b61053c30d6ed36576adfcf
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72364430"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="e118e-102">Come creare uno snap-in di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e118e-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="e118e-103">Uno snap-in di Windows PowerShell fornisce un meccanismo per la registrazione di set di cmdlet e un altro provider di Windows PowerShell con la shell, estendendo così la funzionalità della shell.</span><span class="sxs-lookup"><span data-stu-id="e118e-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="e118e-104">Uno snap-in di Windows PowerShell può registrare tutti i cmdlet e i provider in un singolo assembly oppure registrare un elenco specifico di cmdlet e provider.</span><span class="sxs-lookup"><span data-stu-id="e118e-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="e118e-105">Gli assembly snap-in devono essere installati in una directory protetta, così come sarebbero con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="e118e-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="e118e-106">In caso contrario, gli utenti malintenzionati possono sostituire un assembly con codice unsafe.</span><span class="sxs-lookup"><span data-stu-id="e118e-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="e118e-107">Classi di snap-in di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e118e-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="e118e-108">Tutte le classi di snap-in di Windows PowerShell derivano dalle classi [System. Management. Automation. pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) o [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .</span><span class="sxs-lookup"><span data-stu-id="e118e-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="e118e-109">Esempi</span><span class="sxs-lookup"><span data-stu-id="e118e-109">Examples</span></span>

<span data-ttu-id="e118e-110">[Scrittura di uno snap-in di Windows PowerShell](./writing-a-windows-powershell-snap-in.md): in questo esempio viene illustrato come creare uno snap-in utilizzato per registrare tutti i cmdlet e i provider in un assembly.</span><span class="sxs-lookup"><span data-stu-id="e118e-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="e118e-111">[Scrittura di uno snap-in di Windows PowerShell personalizzato](./writing-a-custom-windows-powershell-snap-in.md): in questo esempio viene illustrato come creare uno snap-in personalizzato che consente di registrare un set specifico di cmdlet e provider che possono o meno esistere in un singolo assembly.</span><span class="sxs-lookup"><span data-stu-id="e118e-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="e118e-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e118e-112">See Also</span></span>

[<span data-ttu-id="e118e-113">System. Management. Automation. PSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e118e-113">System.Management.Automation.PSSnapIn</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="e118e-114">System. Management. Automation. CustomPSSnapIn</span><span class="sxs-lookup"><span data-stu-id="e118e-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="e118e-115">Registrazione di cmdlet</span><span class="sxs-lookup"><span data-stu-id="e118e-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="e118e-116">SDK della shell di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e118e-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
