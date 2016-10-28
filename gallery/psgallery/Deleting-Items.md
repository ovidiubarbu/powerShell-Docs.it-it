---
description: 
manager: carolz
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,gallery
ms.date: 2016-10-14
contributor: manikb
title: Eliminazione di elementi
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: e6c526d1074f61154d03b92b6bf6f599976f5936
ms.openlocfilehash: 4e0258ccf05ef5ab0dc799a5113b05becc3dbb05

---


# Eliminazione di elementi

PowerShell Gallery non supporta l'eliminazione permanente di elementi perché questo impedirebbe la disponibilità di altri elementi dipendenti da quelli eliminati.

PowerShell Gallery supporta invece un modo per "escludere dall'elenco" un elemento, operazione che può essere eseguita nella pagina di gestione dell'elemento sul sito Web. Quando un elemento viene escluso dall'elenco, non viene più individuato dalle ricerche e non viene visualizzato in nessun elenco di elementi, né in PowerShell Gallery né usando i comandi PowerShellGet. È tuttavia possibile scaricarlo specificandone la versione esatta. Questo consente agli script automatizzati di continuare a funzionare.

Se si verifica una situazione eccezionale che richiede l'eliminazione di un elemento, tale operazione può essere eseguita manualmente dal team di PowerShell Gallery. Una violazione di copyright o la presenza di contenuto potenzialmente dannoso è una ragione valida per procedere all'eliminazione. In questo caso, è necessario inviare una richiesta di supporto tramite [PowerShell Gallery] (http://www.PowerShellGallery.com).




<!--HONumber=Oct16_HO2-->


