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
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Come creare uno snap-in di Windows PowerShell

Uno snap-in di Windows PowerShell fornisce un meccanismo per la registrazione di set di cmdlet e un altro provider di Windows PowerShell con la shell, estendendo così la funzionalità della shell. Uno snap-in di Windows PowerShell può registrare tutti i cmdlet e i provider in un singolo assembly oppure registrare un elenco specifico di cmdlet e provider.

Gli assembly snap-in devono essere installati in una directory protetta, così come sarebbero con altri sistemi operativi. In caso contrario, gli utenti malintenzionati possono sostituire un assembly con codice unsafe.

## <a name="windows-powershell-snap-in-classes"></a>Classi di snap-in di Windows PowerShell

Tutte le classi di snap-in di Windows PowerShell derivano dalle classi [System. Management. Automation. pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) o [System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn) .

## <a name="examples"></a>Esempi

[Scrittura di uno snap-in di Windows PowerShell](./writing-a-windows-powershell-snap-in.md): in questo esempio viene illustrato come creare uno snap-in utilizzato per registrare tutti i cmdlet e i provider in un assembly.

[Scrittura di uno snap-in di Windows PowerShell personalizzato](./writing-a-custom-windows-powershell-snap-in.md): in questo esempio viene illustrato come creare uno snap-in personalizzato che consente di registrare un set specifico di cmdlet e provider che possono o meno esistere in un singolo assembly.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. PSSnapIn](/dotnet/api/System.Management.Automation.PSSnapIn)

[System. Management. Automation. CustomPSSnapIn](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[Registrazione di cmdlet](./registering-cmdlets.md)

[SDK della shell di Windows PowerShell](../windows-powershell-reference.md)
