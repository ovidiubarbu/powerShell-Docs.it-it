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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 9f3f79a29e0fb7ec5a5111284bb7985548e17749

---

### Considerazioni per la limitazione dei comandi
Questo passaggio richiede una puntualizzazione.
È essenziale che tutte le funzionalità esposte con JEA si trovino in aree con restrizioni di amministratore.
Gli utenti non amministratori non devono essere in grado di modificare gli script usati negli endpoint JEA.

Si noti che è fondamentale non concedere agli utenti di JEA la possibilità di sovrascrivere le configurazioni di JEA e gli script consentiti all'interno delle proprie sessioni di JEA.
Prestare particolare attenzione quando si espongono comandi come `Copy-Item`.




<!--HONumber=Jun16_HO4-->


