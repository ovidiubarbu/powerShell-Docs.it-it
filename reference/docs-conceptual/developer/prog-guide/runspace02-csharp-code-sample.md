---
title: Esempio diC#codice Runspace02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 59a7b8b9-f72e-43fd-9a10-77404441a3f2
caps.latest.revision: 6
ms.openlocfilehash: 047d14d70853399bc262ac3f1541da38184c3ff8
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/08/2020
ms.locfileid: "80977880"
---
# <a name="runspace02-c-code-sample"></a><span data-ttu-id="b31d2-102">Codice di esempio di Runspace02 (C#)</span><span class="sxs-lookup"><span data-stu-id="b31d2-102">Runspace02 (C#) Code Sample</span></span>

<span data-ttu-id="b31d2-103">Ecco il C# codice sorgente per l'esempio Runspace02.</span><span class="sxs-lookup"><span data-stu-id="b31d2-103">Here is the C# source code for the Runspace02 sample.</span></span> <span data-ttu-id="b31d2-104">Questo esempio usa la classe [System. Management. Automation. Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) per eseguire il cmdlet `Get-Process` in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="b31d2-104">This sample uses the [System.Management.Automation.Runspaceinvoke](/dotnet/api/System.Management.Automation.RunspaceInvoke) class to execute the `Get-Process` cmdlet synchronously.</span></span> <span data-ttu-id="b31d2-105">Windows Forms e data binding vengono quindi utilizzati per visualizzare i risultati in un controllo DataGridView</span><span class="sxs-lookup"><span data-stu-id="b31d2-105">Windows Forms and data binding are then used to display the results in a DataGridView control</span></span>

## <a name="code-sample"></a><span data-ttu-id="b31d2-106">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="b31d2-106">Code Sample</span></span>

:::code language="csharp" source="~/../powershell-sdk-samples/SDK-2.0/csharp/Runspace02/Runspace02.cs" range="11-82":::

## <a name="see-also"></a><span data-ttu-id="b31d2-107">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b31d2-107">See Also</span></span>

[<span data-ttu-id="b31d2-108">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b31d2-108">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
