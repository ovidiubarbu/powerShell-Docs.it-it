---
title: Errori non fatali | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 468dabd6-bfeb-448d-8e09-0996db516edd
caps.latest.revision: 8
ms.openlocfilehash: 5f804756e0e3e867832f15f50967fd6987f160a5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369600"
---
# <a name="non-terminating-errors"></a>Errori non irreversibili

In questo argomento viene illustrato il metodo utilizzato per segnalare errori non fatali. Viene inoltre illustrato come chiamare il metodo dall'interno del cmdlet.

Quando si verifica un errore non fatale, il cmdlet deve segnalare l'errore chiamando il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) . Quando il cmdlet segnala un errore non fatale, il cmdlet può continuare a operare su questo oggetto di input e su altri oggetti pipeline in ingresso. Se il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) , il cmdlet può scrivere un record di errore che descrive la condizione che ha causato l'errore non fatale. Per ulteriori informazioni sui record degli errori, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).

I cmdlet possono chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) in base alle esigenze all'interno dei metodi di elaborazione dell'input. Tuttavia, i cmdlet possono chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) solo dal thread che ha chiamato il [Metodo System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) input. Non chiamare [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread. Comunicare invece gli errori al thread principale.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
