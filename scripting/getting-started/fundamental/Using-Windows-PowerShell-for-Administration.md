---
title: Uso di Windows PowerShell per l'amministrazione
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
translationtype: Human Translation
ms.sourcegitcommit: 03ac4b90d299b316194f1fa932e7dbf62d4b1c8e
ms.openlocfilehash: f6d5477c32f8f254ab7280945847509588002e83

---

# Uso di Windows PowerShell per l'amministrazione
L'obiettivo fondamentale di Windows PowerShell è offrire un controllo amministrativo migliore e più semplice sui sistemi, sia in modo interattivo che tramite script. Questo capitolo illustra come risolvere molti problemi specifici di amministrazione dei sistemi Windows con Windows PowerShell. Anche se gli script o le funzioni non sono stati trattati nel Manuale dell'utente di Windows PowerShell, le soluzioni possono essere usate da script o come funzioni in un secondo momento. Verranno illustrati alcuni esempi che includono le funzioni come parte della soluzione dei problemi.

In tutte le descrizioni delle soluzioni si potrà notare l'uso di soluzioni miste con cmdlet specifici, il cmdlet generale Get\-WmiObject e anche strumenti esterni che fanno parte delle infrastrutture Windows e .NET Framework. L'uso di strumenti esterni fa parte delle finalità di progettazione a lungo termine di Windows PowerShell. Anche in caso di espansione del sistema, gli utenti si troveranno ad affrontare situazioni in cui i set di strumenti disponibili non offrono tutte le funzionalità necessarie. Anziché incoraggiare la dipendenza dalle implementazioni basate esclusivamente su cmdlet, Windows PowerShell tenta di supportare soluzioni di integrazione da tutti gli scenari alternativi possibili.




<!--HONumber=Jun16_HO4-->


