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
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="3a1bc-102">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="3a1bc-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="3a1bc-103">"La scrittura di un file di formattazione di PowerShell" è per gli sviluppatori di comandi che scrivono cmdlet o funzioni che restituiscono oggetti alla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="3a1bc-104">I file di formattazione definiscono il modo in cui PowerShell visualizza tali oggetti dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="3a1bc-105">In questa documentazione viene fornita una panoramica dei file di formattazione, una spiegazione dei concetti che è necessario comprendere durante la scrittura di questi file, esempi di XML utilizzati in questi file e una sezione di riferimento per gli elementi XML.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="3a1bc-106">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="3a1bc-106">In This Section</span></span>

<span data-ttu-id="3a1bc-107">[Cenni preliminari sul file di formattazione](./formatting-file-overview.md) Viene descritto il tipo di file di formato e i componenti generali di un file di formattazione, incluse le funzionalità comuni che è possibile definire nel file, i diversi tipi di visualizzazioni di formato che è possibile definire per gli oggetti .NET e un esempio semplificato del codice XML utilizzato per definire una tabella v IEW.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="3a1bc-108">[Concetti relativi ai file di formattazione](./formatting-file-concepts.md) Include informazioni che potrebbero essere necessarie per la creazione di file di formattazione personalizzati, ad esempio i diversi tipi di viste che è possibile definire e i componenti speciali di tali visualizzazioni.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="3a1bc-109">[Esempi di file di formattazione](./examples-of-formatting-files.md) Vengono forniti esempi XML di diversi file di formattazione, inclusi esempi di una vista tabella, una visualizzazione elenco e una visualizzazione estesa, oltre ad esempi che illustrano come definire funzionalità quali set di selezione, condizioni di selezione e controlli comuni.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="3a1bc-110">[Formato riferimento XML](./format-schema-xml-reference.md) Include argomenti di riferimento per gli elementi XML utilizzati in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="3a1bc-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
