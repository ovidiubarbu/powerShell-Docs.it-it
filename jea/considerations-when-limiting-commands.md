---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: considerazioni per la limitazione dei comandi
ms.technology: powershell
ms.openlocfilehash: 0b4396ee130d99c42f613c1b79193c236ad472e7
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="considerations-when-limiting-commands"></a>Considerazioni per la limitazione dei comandi
Questo passaggio richiede una puntualizzazione.
È essenziale che tutte le funzionalità esposte con JEA si trovino in aree con restrizioni di amministratore.
Gli utenti non amministratori non devono essere in grado di modificare gli script usati negli endpoint JEA.

Si noti che è fondamentale non concedere agli utenti di JEA la possibilità di sovrascrivere le configurazioni di JEA e gli script consentiti all'interno delle proprie sessioni di JEA.
Prestare particolare attenzione quando si espongono comandi come `Copy-Item`.

