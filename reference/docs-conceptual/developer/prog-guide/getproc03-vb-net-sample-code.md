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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72360310"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="c2330-102">Codice di esempio di GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="c2330-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="c2330-103">Il codice seguente illustra l'implementazione di un cmdlet `Get-Process` che può accettare input da pipeline.</span><span class="sxs-lookup"><span data-stu-id="c2330-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="c2330-104">Questa implementazione definisce un parametro `Name` che accetta input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi forniti, quindi usa il metodo [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) come output meccanismo per l'invio di oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="c2330-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [WriteObject(System.Object,System.Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c2330-105">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="c2330-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
