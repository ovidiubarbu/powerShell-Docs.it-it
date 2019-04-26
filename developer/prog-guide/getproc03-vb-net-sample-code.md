---
title: GetProc03 codice di esempio (Visual Basic.NET) | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff94c452-d4ec-4492-ac20-61ad52f8ae8c
caps.latest.revision: 7
ms.openlocfilehash: 0cfb5c203c97a4d20e7fadf8183e608e9e31b881
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62081649"
---
# <a name="getproc03-vbnet-sample-code"></a><span data-ttu-id="67257-102">Codice di esempio di GetProc03 (VB.NET)</span><span class="sxs-lookup"><span data-stu-id="67257-102">GetProc03 (VB.NET) Sample Code</span></span>

<span data-ttu-id="67257-103">Il codice seguente viene illustrata l'implementazione di un `Get-Process` cmdlet in grado di accettare le pipeline di input.</span><span class="sxs-lookup"><span data-stu-id="67257-103">The following code shows the implementation of a `Get-Process` cmdlet that can accept pipelined input.</span></span> <span data-ttu-id="67257-104">Questa implementazione definisce una `Name` parametro che accetta l'input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi specificati e Usa quindi il [System.Management.Automation.Cmdlet.WriteObject% 28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) metodo come meccanismo di output per l'invio di oggetti alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="67257-104">This implementation defines a `Name` parameter that accepts pipeline input, retrieves process information from the local computer based on the supplied names, and then uses the [System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject%28System.Object%2CSystem.Boolean%29) method as the output mechanism for sending objects to the pipeline.</span></span>

## <a name="code-sample"></a><span data-ttu-id="67257-105">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="67257-105">Code Sample</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->