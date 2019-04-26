---
title: Output del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1362f4cd-4e05-4ace-ade6-7128da8ad86c
caps.latest.revision: 10
ms.openlocfilehash: 4c6aacd49b0a87bca6806ba5f08a1b4d48a90959
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068556"
---
# <a name="cmdlet-output"></a><span data-ttu-id="2c52f-102">Output dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="2c52f-102">Cmdlet Output</span></span>

<span data-ttu-id="2c52f-103">In questa sezione vengono descritti i tipi di output del cmdlet e i metodi che è possono chiamare i cmdlet per generare l'output, ad esempio i messaggi di errore e gli oggetti.</span><span class="sxs-lookup"><span data-stu-id="2c52f-103">This section discusses the types of cmdlet output and the methods that cmdlets can call to generate output such as error messages and objects.</span></span> <span data-ttu-id="2c52f-104">Questa sezione descrive inoltre come definire i tipi di .NET Framework che vengono restituiti tramite i cmdlet e modo in cui tali oggetti vengono visualizzati.</span><span class="sxs-lookup"><span data-stu-id="2c52f-104">This section also describes how to define the .NET Framework types that are returned by your cmdlets and how those objects are displayed.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2c52f-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="2c52f-105">In This Section</span></span>

<span data-ttu-id="2c52f-106">[Tipi di Output del Cmdlet](./types-of-cmdlet-output.md) descrive i tipi e i cmdlet possono generare l'output e i metodi che chiamano i cmdlet per generare l'output.</span><span class="sxs-lookup"><span data-stu-id="2c52f-106">[Types of Cmdlet Output](./types-of-cmdlet-output.md) Describes the types and output that cmdlets can generate and the methods that cmdlets call to generate the output.</span></span>

<span data-ttu-id="2c52f-107">[Segnalazione errori cmdlet](./cmdlet-error-reporting.md) illustra i cmdlet di segnalazione, un subset dell'output del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2c52f-107">[Cmdlet Error Reporting](./cmdlet-error-reporting.md) Discusses cmdlet error reporting, a subset of cmdlet output.</span></span>

<span data-ttu-id="2c52f-108">[Estensione di oggetti di Output](./extending-output-objects.md) viene illustrato come utilizzare i file di tipi (con estensione PS1XML) per estendere gli oggetti di .NET Framework che vengono restituiti dal cmdlet, funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="2c52f-108">[Extending Output Objects](./extending-output-objects.md) Discusses how to use the types files (.ps1xml) to extend the .NET Framework objects that are returned by cmdlets, functions, and scripts.</span></span>

<span data-ttu-id="2c52f-109">[File di formattazione PowerShell](../format/powershell-formatting-files.md) descrive i file di formattazione (. format.ps1xml) verranno visualizzati i file che definiscono il valore predefinito per un set specifico di oggetti di .NET Framework in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2c52f-109">[PowerShell Formatting Files](../format/powershell-formatting-files.md) Describes the formatting files (.format.ps1xml) files that define the default display for a specific set of .NET Framework objects in Windows PowerShell.</span></span>

<span data-ttu-id="2c52f-110">[I file di formattazione personalizzata](./custom-formatting-files.md) viene descritto come creare una formattazione personalizzata formati di visualizzazione file per sovrascrivere il valore predefinito o per definire la visualizzazione degli oggetti restituiti dai propri comandi.</span><span class="sxs-lookup"><span data-stu-id="2c52f-110">[Custom Formatting Files](./custom-formatting-files.md) Describes how to create your own custom formatting files to overwrite the default display formats or to define the display of objects returned by your own commands.</span></span>

## <a name="see-also"></a><span data-ttu-id="2c52f-111">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2c52f-111">See Also</span></span>

[<span data-ttu-id="2c52f-112">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2c52f-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
