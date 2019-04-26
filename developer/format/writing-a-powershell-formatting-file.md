---
title: La scrittura di un File di formattazione di PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 39acce45-5144-43ba-894d-a4ce782fa67d
caps.latest.revision: 13
ms.openlocfilehash: f89f0009972d5237d71cb8f0d1c53cd0ae614b67
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083575"
---
# <a name="writing-a-powershell-formatting-file"></a><span data-ttu-id="bc81f-102">Scrittura di un file di formattazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="bc81f-102">Writing a PowerShell Formatting File</span></span>

<span data-ttu-id="bc81f-103">"La scrittura di un File di formattazione di PowerShell" è destinato agli sviluppatori di comandi che scrivono i cmdlet o funzioni che restituiscono oggetti alla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="bc81f-103">"Writing a PowerShell Formatting File" is for command developers who are writing cmdlets or functions that output objects to the command line.</span></span> <span data-ttu-id="bc81f-104">File di formattazione definiscono la modalità di visualizzazione tali oggetti nella riga di comando PowerShell.</span><span class="sxs-lookup"><span data-stu-id="bc81f-104">Formatting files define how PowerShell displays those objects at the command line.</span></span> <span data-ttu-id="bc81f-105">Questa documentazione viene fornita una panoramica di formattare i file, una spiegazione dei concetti che è necessario comprendere quando si scrive questi file, esempi di XML Schema usato in questi file e una sezione di riferimento per gli elementi XML.</span><span class="sxs-lookup"><span data-stu-id="bc81f-105">This documentation provides an overview of formatting files, an explanation of the concepts that you should understand when writing these files, examples of XML used in these files, and a reference section for the XML elements.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="bc81f-106">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="bc81f-106">In This Section</span></span>

<span data-ttu-id="bc81f-107">[Panoramica dei File di formattazione](./formatting-file-overview.md) descrive quale un file di formato e i componenti generali di un file di formattazione, incluse le funzionalità comuni che possono essere definite nel file, i diversi tipi di viste di formato che possono essere definite per gli oggetti .NET e un oggetto un esempio semplificato del codice XML utilizzato per definire una visualizzazione tabella.</span><span class="sxs-lookup"><span data-stu-id="bc81f-107">[Formatting File Overview](./formatting-file-overview.md) Describes what a format file is and the general components of a formatting file, including common features that can be defined in the file, the different types of format views that can be defined for .NET objects, and a simplified example of the XML used to define a table view.</span></span>

<span data-ttu-id="bc81f-108">[Concetti relativi al File di formattazione](./formatting-file-concepts.md) sono incluse informazioni che potrebbe essere necessario conoscere durante la creazione di una formattazione di file, ad esempio componenti speciali le visualizzazioni e i diversi tipi di viste che è possibile definire.</span><span class="sxs-lookup"><span data-stu-id="bc81f-108">[Formatting File Concepts](./formatting-file-concepts.md) Includes information that you might need to know when creating your own formatting files, such as the different types of views that you can define and special components of those views.</span></span>

<span data-ttu-id="bc81f-109">[Esempi di file di formattazione](./examples-of-formatting-files.md) forniti esempi di diversi file di formattazione, inclusi esempi di visualizzazione di una tabella, una visualizzazione elenco e una visualizzazione più ampia, nonché esempi che illustrano come definire le funzionalità, come i set di selezione, condizioni di selezione, fornisce XML e controlli comuni.</span><span class="sxs-lookup"><span data-stu-id="bc81f-109">[Examples of Formatting Files](./examples-of-formatting-files.md) Provides XML examples of several formatting files, including examples of a table view, a list view, and a wide view, as well as examples that show how to define features such as selection sets, selection conditions, and common controls.</span></span>

<span data-ttu-id="bc81f-110">[Riferimenti XML di formato](./format-schema-xml-reference.md) include argomenti di riferimento per gli elementi XML utilizzati in un file di formattazione.</span><span class="sxs-lookup"><span data-stu-id="bc81f-110">[Format XML Reference](./format-schema-xml-reference.md) Includes reference topics for the XML elements used in a formatting file.</span></span>
