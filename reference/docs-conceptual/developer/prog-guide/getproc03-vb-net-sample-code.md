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
# <a name="getproc03-vbnet-sample-code"></a>Codice di esempio di GetProc03 (VB.NET)

Nel codice seguente viene illustrata l'implementazione di un cmdlet di `Get-Process` che può accettare input da pipeline. Questa implementazione definisce un parametro di `Name` che accetta input della pipeline, recupera le informazioni sul processo dal computer locale in base ai nomi forniti, quindi usa il metodo [WriteObject (System. Object, System. Boolean)](/dotnet/api/system.management.automation.cmdlet.writeobject?view=pscore-6.2.0#System_Management_Automation_Cmdlet_WriteObject_System_Object_System_Boolean_) come meccanismo di output per l'invio di oggetti alla pipeline.

## <a name="code-sample"></a>Codice di esempio

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplesgetproc03#getproc03vbAll](Msh_samplesgetproc03#getproc03vbAll)]  -->
