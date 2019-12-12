---
title: Errori di terminazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: d1967fe7996f75ec5229920f7ec49aa5ff6bdbfd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369330"
---
# <a name="terminating-errors"></a>Errori irreversibili

In questo argomento viene illustrato il metodo utilizzato per segnalare gli errori di terminazione. Viene inoltre illustrato come chiamare il metodo dall'interno del cmdlet e vengono illustrate le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.

Quando si verifica un errore di terminazione, il cmdlet deve segnalare l'errore chiamando il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Questo metodo consente al cmdlet di inviare un record di errore che descrive la condizione che ha causato l'errore di terminazione. Per ulteriori informazioni sui record degli errori, vedere la pagina relativa ai [record degli errori di Windows PowerShell](./windows-powershell-error-records.md).

Quando viene chiamato il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) , il runtime di Windows PowerShell interrompe in modo permanente l'esecuzione della pipeline e genera un'eccezione [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) . Eventuali tentativi successivi di chiamare [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)o diverse altre API causano la generazione di un'eccezione [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) da tali chiamate.

L'eccezione [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) può verificarsi anche se un altro cmdlet della pipeline segnala un errore irreversibile, se l'utente ha richiesto di arrestare la pipeline o se la pipeline è stata interrotta prima del completamento per qualsiasi motivo. Non è necessario che il cmdlet intercettare l'eccezione [System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) a meno che non sia necessario pulire le risorse aperte o il relativo stato interno.

I cmdlet possono scrivere un numero qualsiasi di oggetti di output o errori non fatali prima di segnalare un errore di terminazione. Tuttavia, l'errore di terminazione interrompe in modo permanente la pipeline e non è possibile segnalare ulteriori output, errori di terminazione o errori non fatali.

I cmdlet possono chiamare [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) solo dal thread che ha chiamato il [Metodo System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Non tentare di chiamare [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) o [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread. Al contrario, gli errori devono essere comunicati nuovamente al thread principale.

Un cmdlet può generare un'eccezione nell'implementazione del metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)o [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Qualsiasi eccezione generata da questi metodi (ad eccezione di alcune condizioni di errore gravi che arrestano l'host di Windows PowerShell) viene interpretata come un errore irreversibile che interrompe la pipeline, ma non Windows PowerShell nel suo complesso. (Si applica solo al thread del cmdlet principale). Le eccezioni non rilevate nei thread generati dal cmdlet, in generale, interrompono l'host di Windows PowerShell. Si consiglia di usare [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) anziché generare un'eccezione perché il record di errore fornisce informazioni aggiuntive sulla condizione di errore, che risulta utile per l'utente finale. I cmdlet devono rispettare le linee guida per il codice gestito rispetto a intercettare e gestire tutte le eccezioni (`catch (Exception e)`). Converte solo le eccezioni dei tipi noti e previsti nei record degli errori.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System. Management. Automation. Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Record degli errori di Windows PowerShell](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
