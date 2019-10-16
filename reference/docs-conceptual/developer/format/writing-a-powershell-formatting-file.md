---
title: Scrittura di un file di formattazione di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361410"
---
# <a name="writing-a-powershell-formatting-file"></a>Scrittura di un file di formattazione di PowerShell

"La scrittura di un file di formattazione di PowerShell" è per gli sviluppatori di comandi che scrivono cmdlet o funzioni che restituiscono oggetti alla riga di comando. I file di formattazione definiscono il modo in cui PowerShell visualizza tali oggetti dalla riga di comando. In questa documentazione viene fornita una panoramica dei file di formattazione, una spiegazione dei concetti che è necessario comprendere durante la scrittura di questi file, esempi di XML utilizzati in questi file e una sezione di riferimento per gli elementi XML.

## <a name="in-this-section"></a>Contenuto della sezione

[Cenni preliminari sul file di formattazione](./formatting-file-overview.md) Viene descritto il tipo di file di formato e i componenti generali di un file di formattazione, incluse le funzionalità comuni che è possibile definire nel file, i diversi tipi di visualizzazioni di formato che è possibile definire per gli oggetti .NET e un esempio semplificato del codice XML utilizzato per definire una tabella v IEW.

[Concetti relativi ai file di formattazione](./formatting-file-concepts.md) Include informazioni che potrebbero essere necessarie per la creazione di file di formattazione personalizzati, ad esempio i diversi tipi di viste che è possibile definire e i componenti speciali di tali visualizzazioni.

[Esempi di file di formattazione](./examples-of-formatting-files.md) Vengono forniti esempi XML di diversi file di formattazione, inclusi esempi di una vista tabella, una visualizzazione elenco e una visualizzazione estesa, oltre ad esempi che illustrano come definire funzionalità quali set di selezione, condizioni di selezione e controlli comuni.

[Formato riferimento XML](./format-schema-xml-reference.md) Include argomenti di riferimento per gli elementi XML utilizzati in un file di formattazione.
