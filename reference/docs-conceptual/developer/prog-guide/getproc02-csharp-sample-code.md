---
title: Codice diC#esempio GetProc02 () | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e4e1eee3-316b-43a4-8a60-313391619be6
caps.latest.revision: 6
ms.openlocfilehash: 5989b1e7030375b1bacdd9b82c25c1a8288fd637
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360370"
---
# <a name="getproc02-c-sample-code"></a><span data-ttu-id="67951-102">Codice di esempio di GetProc02 (C#)</span><span class="sxs-lookup"><span data-stu-id="67951-102">GetProc02 (C#) Sample Code</span></span>

<span data-ttu-id="67951-103">Nel codice seguente viene illustrata l'implementazione di un cmdlet di `Get-Process` che accetta l'input della riga di comando.</span><span class="sxs-lookup"><span data-stu-id="67951-103">The following code shows the implementation of a `Get-Process` cmdlet that accepts command-line input.</span></span> <span data-ttu-id="67951-104">Si noti che questa implementazione definisce un parametro di `Name` per consentire l'input della riga di comando e usa il metodo [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) come meccanismo di output per l'invio di oggetti di output alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="67951-104">Notice that this implementation defines a `Name` parameter to allow command-line input, and it uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending output objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="67951-105">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="67951-105">Code Sample</span></span>

[!code-csharp[GetProcessSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/GetProcessSample02/GetProcessSample02.cs#L11-L76 "GetProcessSample02.cs")]

## <a name="see-also"></a><span data-ttu-id="67951-106">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="67951-106">See Also</span></span>

[<span data-ttu-id="67951-107">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="67951-107">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
