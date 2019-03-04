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
# <a name="how-to-create-a-windows-powershell-snap-in"></a>Come creare uno snap-in di Windows PowerShell

Uno snap-in Windows PowerShell fornisce un meccanismo per la registrazione dei set di cmdlet e un altro provider di Windows PowerShell con la shell, estendere le funzionalità della shell. Uno snap-in Windows PowerShell può registrare tutti i cmdlet e provider in un unico assembly o possibile registrare un elenco specifico di cmdlet e provider.

Snap-in di assembly devono essere installati in una directory protetta, esattamente come verrebbero usati con altri sistemi operativi. In caso contrario, gli utenti malintenzionati possono sostituire un assembly con codice unsafe.

## <a name="windows-powershell-snap-in-classes"></a>Classi di PowerShell Snap-in Windows

Tutte le classi di snap-in di Windows PowerShell derivano dal [System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn) oppure [System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn) classi.

## <a name="examples"></a>Esempi

[La scrittura di uno Snap-in PowerShell di Windows](./writing-a-windows-powershell-snap-in.md): In questo esempio viene illustrato come creare uno snap-in che consente di registrare tutti i cmdlet e provider in un assembly.

[La scrittura di uno Snap-in PowerShell di Windows personalizzate](./writing-a-custom-windows-powershell-snap-in.md): In questo esempio viene illustrato come creare un snap-in personalizzato che viene usato per registrare un set specifico di cmdlet e provider che potrebbe o non esistere in un singolo assembly.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Pssnapin](/dotnet/api/System.Management.Automation.PSSnapIn)

[System.Management.Automation.Custompssnapin](/dotnet/api/System.Management.Automation.CustomPSSnapIn)

[La registrazione di cmdlet](./registering-cmdlets.md)

[Windows PowerShell Shell SDK](../windows-powershell-reference.md)
