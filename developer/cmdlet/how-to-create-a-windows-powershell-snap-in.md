---
title: Come creare uno Snap-in PowerShell di Windows | Microsoft Docs
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
ms.openlocfilehash: 73834cea1d90943cf954728d6295d8eb33e14f57
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859757"
---
# <a name="how-to-create-a-windows-powershell-snap-in"></a><span data-ttu-id="f2a0b-102">Come creare uno snap-in di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f2a0b-102">How to Create a Windows PowerShell Snap-in</span></span>

<span data-ttu-id="f2a0b-103">Uno snap-in Windows PowerShell fornisce un meccanismo per la registrazione dei set di cmdlet e un altro provider di Windows PowerShell con la shell, estendere le funzionalità della shell.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-103">A Windows PowerShell snap-in provides a mechanism for registering sets of cmdlets and another Windows PowerShell provider with the shell, thus extending the functionality of the shell.</span></span> <span data-ttu-id="f2a0b-104">Uno snap-in Windows PowerShell può registrare tutti i cmdlet e provider in un unico assembly o possibile registrare un elenco specifico di cmdlet e provider.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-104">A Windows PowerShell snap-in can register all the cmdlets and providers in a single assembly, or it can register a specific list of cmdlets and providers.</span></span>

<span data-ttu-id="f2a0b-105">Snap-in di assembly devono essere installati in una directory protetta, esattamente come verrebbero usati con altri sistemi operativi.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-105">Snap-in assemblies should be installed in a protected directory, just as they would be with other operating systems.</span></span> <span data-ttu-id="f2a0b-106">In caso contrario, gli utenti malintenzionati possono sostituire un assembly con codice unsafe.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-106">Otherwise, malicious users can replace an assembly with unsafe code.</span></span>

## <a name="windows-powershell-snap-in-classes"></a><span data-ttu-id="f2a0b-107">Classi di PowerShell Snap-in Windows</span><span class="sxs-lookup"><span data-stu-id="f2a0b-107">Windows PowerShell Snap-in Classes</span></span>

<span data-ttu-id="f2a0b-108">Tutte le classi di snap-in di Windows PowerShell derivano dal [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) oppure [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classi.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-108">All Windows PowerShell snap-in classes derive from the [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) or [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classes.</span></span>

## <a name="examples"></a><span data-ttu-id="f2a0b-109">Esempi</span><span class="sxs-lookup"><span data-stu-id="f2a0b-109">Examples</span></span>

<span data-ttu-id="f2a0b-110">[La scrittura di uno Snap-in PowerShell di Windows](./writing-a-windows-powershell-snap-in.md): In questo esempio viene illustrato come creare uno snap-in che consente di registrare tutti i cmdlet e provider in un assembly.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-110">[Writing a Windows PowerShell Snap-in](./writing-a-windows-powershell-snap-in.md): This example shows how to create a snap-in that is used to register all the cmdlets and providers in an assembly.</span></span>

<span data-ttu-id="f2a0b-111">[La scrittura di uno Snap-in PowerShell di Windows personalizzate](./writing-a-custom-windows-powershell-snap-in.md): In questo esempio viene illustrato come creare un snap-in personalizzato che viene usato per registrare un set specifico di cmdlet e provider che potrebbe o non esistere in un singolo assembly.</span><span class="sxs-lookup"><span data-stu-id="f2a0b-111">[Writing a Custom Windows PowerShell Snap-in](./writing-a-custom-windows-powershell-snap-in.md): This example shows how to create a custom snap-in that is used to register a specific set of cmdlets and providers that might or might not exist in a single assembly.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2a0b-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="f2a0b-112">See Also</span></span>

[<span data-ttu-id="f2a0b-113">System.Management.Automation.Pssnapin</span><span class="sxs-lookup"><span data-stu-id="f2a0b-113">System.Management.Automation.Pssnapin</span></span>](/dotnet/api/System.Management.Automation.PSSnapIn)

[<span data-ttu-id="f2a0b-114">System.Management.Automation.Custompssnapin</span><span class="sxs-lookup"><span data-stu-id="f2a0b-114">System.Management.Automation.Custompssnapin</span></span>](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[<span data-ttu-id="f2a0b-115">La registrazione di cmdlet</span><span class="sxs-lookup"><span data-stu-id="f2a0b-115">Registering Cmdlets</span></span>](./registering-cmdlets.md)

[<span data-ttu-id="f2a0b-116">Windows PowerShell Shell SDK</span><span class="sxs-lookup"><span data-stu-id="f2a0b-116">Windows PowerShell Shell SDK</span></span>](../windows-powershell-reference.md)
