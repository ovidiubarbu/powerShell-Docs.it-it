---
title: Gli errori non è definitiva | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067655"
---
# <a name="non-terminating-errors"></a>Errori non irreversibili

In questo argomento illustra il metodo utilizzato per segnalare errori non fatali. Inoltre illustrato come chiamare il metodo dal cmdlet.

Quando si verifica un errore non irreversibile, il cmdlet deve segnalare l'errore chiamando il [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo). Quando il cmdlet segnala un errore non irreversibile, il cmdlet può continuare a funzionare su questo oggetto di input e in entrata ulteriormente gli oggetti di pipeline. Se viene chiamato il cmdlet di [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) metodo, il cmdlet può scrivere un record di errore che descrive la condizione che ha causato l'errore non fatale. Per altre informazioni sui record di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).

I cmdlet è possono chiamare [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) esigenze da entro i metodi di elaborazione dell'input. Tuttavia, è possono chiamare i cmdlet [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo dal thread che ha chiamato la [System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oppure [System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo di elaborazione di input. Non chiamare [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread. Al contrario, comunicare gli errori nel thread principale.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Cmdlet.EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Record degli errori di PowerShell di Windows](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
