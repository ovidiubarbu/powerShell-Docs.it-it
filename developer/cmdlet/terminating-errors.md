---
title: Irreversibili | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b804e738-aefa-41bb-9649-f9ed897fd96c
caps.latest.revision: 8
ms.openlocfilehash: c593da1f7bdb6ddf09ba8d5de92af730687dbc8a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859237"
---
# <a name="terminating-errors"></a>Errori irreversibili

In questo argomento illustra il metodo utilizzato per segnalare gli errori di interruzione. Viene inoltre illustrato come chiamare il metodo all'interno di cmdlet e vengono descritte le eccezioni che possono essere restituite dal runtime di Windows PowerShell quando viene chiamato il metodo.

Quando una terminazione errore si verifica, il cmdlet deve segnalare l'errore chiamando il [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (metodo). Questo metodo consente al cmdlet inviare un record di errore che descrive la condizione che ha causato l'errore di terminazione. Per altre informazioni sui record di errore, vedere [record di errore di Windows PowerShell](./windows-powershell-error-records.md).

Quando la [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) viene chiamato il metodo, il runtime di Windows PowerShell arresta l'esecuzione della pipeline in modo permanente e genera un [ System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) eccezione. Eventuali tentativi successivi di chiamare [System.Management.Automation.Cmdlet.Writeobject*](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject), [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError), o diverse altre API fa in modo che tali chiamate generare un [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) eccezione.

Il [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) eccezione può verificarsi anche se un altro cmdlet nella pipeline segnala un errore di terminazione, se l'utente ha richiesto di interrompere la pipeline o se la pipeline è stata interrotta prima del completamento per qualsiasi motivo. Il cmdlet non è necessario intercettare la [System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException) eccezione a meno che non è necessario aprire pulizia delle risorse o il proprio stato interno.

I cmdlet è possono scrivere un numero qualsiasi di oggetti di output o errori non fatali prima che venga segnalato un errore irreversibile. Tuttavia, l'errore di terminazione si arresta in modo permanente la pipeline e alcun output ulteriormente, irreversibili, o possono essere segnalati errori non fatali.

I cmdlet è possono chiamare [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) solo dal thread che ha chiamato la [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [ System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oppure [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) metodo di elaborazione di input. Non tentare di chiamare [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) oppure [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) da un altro thread. Al contrario, gli errori devono essere comunicati al thread principale.

È possibile che un cmdlet per generare un'eccezione durante l'implementazione del [System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing), [System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord), oppure [System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) (metodo). Qualsiasi eccezione generata da questi metodi (ad eccezione di alcune condizioni di errore grave che arrestano l'host di Windows PowerShell) viene interpretata come un errore irreversibile che interrompe la pipeline, ma non Windows PowerShell nel suo complesso. (Si applica solo al thread principale di cmdlet. Le eccezioni non rilevate nel thread generati dal cmdlet, in generale, interrompere l'host di Windows PowerShell.) È consigliabile usare [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) anziché generare un'eccezione perché il record di errore fornisce ulteriori informazioni sulla condizione di errore, che risulta utile per l'utente finale. I cmdlet devono rispettare le linee guida di codice gestito con intercettazione e gestione di tutte le eccezioni (`catch (Exception e)`). Converte solo le eccezioni dei tipi noti e previsto in record degli errori.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.Beginprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing)

[System.Management.Automation.Cmdlet.Endprocessing*](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing)

[System.Management.Automation.Cmdlet.Processrecord*](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord)

[System.Management.Automation.Pipelinestoppedexception](/dotnet/api/System.Management.Automation.PipelineStoppedException)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[Record degli errori di PowerShell di Windows](./windows-powershell-error-records.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
