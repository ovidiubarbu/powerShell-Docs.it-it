---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso di Windows PowerShell per l'amministrazione
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="using-windows-powershell-for-administration"></a>Uso di Windows PowerShell per l'amministrazione
L'obiettivo fondamentale di Windows PowerShell è offrire un controllo amministrativo migliore e più semplice sui sistemi, sia in modo interattivo che tramite script. Questo capitolo illustra come risolvere molti problemi specifici di amministrazione dei sistemi Windows con Windows PowerShell. Anche se gli script o le funzioni non sono stati trattati nel Manuale dell'utente di Windows PowerShell, le soluzioni possono essere usate da script o come funzioni in un secondo momento. Verranno illustrati alcuni esempi che includono le funzioni come parte della soluzione dei problemi.

In tutte le descrizioni delle soluzioni si potrà notare l'uso di soluzioni miste con cmdlet specifici, il cmdlet generale Get-WmiObject e anche strumenti esterni che fanno parte delle infrastrutture Windows e .NET Framework. L'uso di strumenti esterni fa parte delle finalità di progettazione a lungo termine di Windows PowerShell. Anche in caso di espansione del sistema, gli utenti si troveranno ad affrontare situazioni in cui i set di strumenti disponibili non offrono tutte le funzionalità necessarie. Anziché incoraggiare la dipendenza dalle implementazioni basate esclusivamente su cmdlet, Windows PowerShell tenta di supportare soluzioni di integrazione da tutti gli scenari alternativi possibili.