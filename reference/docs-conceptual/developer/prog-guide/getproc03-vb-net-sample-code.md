---
title: Codice di esempio GetProc03 (VB.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: a0a88ca517347a94fc81534caace6efa0f13fdd7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360310"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="5bede-102">Codice di esempio di GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="5bede-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="5bede-103">Nel codice seguente viene illustrata l'implementazione di un cmdlet di `Get-Process` che può accettare input da pipeline.</span><span class="sxs-lookup"><span data-stu-id="5bede-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="5bede-104">Questa implementazione definisce un parametro di `Name` che accetta input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi forniti, quindi usa il metodo [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) come meccanismo di output per l'invio di oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="5bede-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5bede-105">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="5bede-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
