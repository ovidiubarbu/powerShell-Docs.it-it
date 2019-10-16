---
title: Interpretazione degli oggetti ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365420"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretazione degli oggetti ErrorRecord

Nella maggior parte dei casi, un oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) rappresenta un errore non fatale generato da un comando o uno script. Gli errori di terminazione possono inoltre specificare le informazioni aggiuntive in un ErrorRecord tramite l'interfaccia [System. Management. Automation. Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) .

Se si vuole scrivere un gestore di errori nello script o in un host per gestire errori specifici che si verificano durante l'esecuzione di comandi o script, è necessario interpretare l'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) per determinare se rappresenta la classe di errore che si desidera gestire.

Quando un cmdlet rileva un errore di terminazione o non fatale, deve creare un record di errore in cui viene descritta la condizione di errore. L'applicazione host deve esaminare i record degli errori ed eseguire qualsiasi azione che ridurrà l'errore. L'applicazione host deve inoltre esaminare i record di errore per gli errori non fatali che non sono riusciti a elaborare un record, ma sono stati in grado di continuare ed esaminare i record degli errori per terminare gli errori che hanno causato l'arresto della pipeline.

> [!NOTE]
> Per gli errori di terminazione, il cmdlet chiama il metodo [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Per gli errori non fatali, il cmdlet chiama il metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) .

## <a name="error-record-design"></a>Progettazione record errori

I record degli errori sono progettati per fornire informazioni aggiuntive sugli errori che non sono disponibili nelle eccezioni garantendo al contempo che le informazioni combinate in ogni record di errore siano univoche. Questa unicità consente all'applicazione host di esaminare le diverse parti del record di errore, in modo che possa identificare la condizione di errore e l'azione che l'host deve eseguire.

## <a name="interpreting-error-records"></a>Interpretazione dei record degli errori

Per identificare l'errore, è possibile esaminare diverse parti del record di errore. Queste parti includono quanto segue:

- Categoria di errore

- Eccezione Error

- Identificatore di errore completo (FQID)

- Altre informazioni

### <a name="the-error-category"></a>Categoria di errore

La categoria di errore del record di errore è una delle costanti predefinite fornite dall'enumerazione [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory) . Queste informazioni sono disponibili tramite la proprietà [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) dell'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Il cmdlet può specificare le categorie CloseError, OpenError, InvalidType, ReadError e WriteError e altre categorie di errore. L'applicazione host può utilizzare la categoria di errore per acquisire gruppi di errori.

### <a name="the-exception"></a>Eccezione

L'eccezione inclusa nel record di errore viene fornita dal cmdlet ed è possibile accedervi tramite la proprietà [System. Management. Automation. ErrorRecord. Exception *](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) dell'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

Le applicazioni host possono utilizzare la parola chiave `is` per indicare che l'eccezione è di una classe specifica o di una classe derivata. È preferibile creare un ramo per il tipo di eccezione, come illustrato nell'esempio seguente.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

In questo modo, è possibile intercettare le classi derivate. Tuttavia, esistono problemi se l'eccezione viene deserializzata.

### <a name="the-fqid"></a>FQID

FQID è l'informazione più specifica che è possibile usare per identificare l'errore. Si tratta di una stringa che include un identificatore definito dal cmdlet, il nome della classe di cmdlet e l'origine che ha segnalato l'errore. In generale, un record di errore è analogo a un record di eventi di un registro eventi di Windows. FQID è analogo alla seguente tupla, che identifica la classe del record dell'evento: (*nome log*, *origine*, *ID evento*).

FQID è progettato per essere esaminato come una singola stringa. Tuttavia, esistono casi in cui l'identificatore di errore è progettato per essere analizzato dall'applicazione host. L'esempio seguente è un identificatore di errore completo formato correttamente.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Nell'esempio precedente, il primo token è l'identificatore dell'errore, seguito dal nome della classe del cmdlet. L'identificatore di errore può essere un singolo token o un identificatore separato da punti che consente la diramazione all'ispezione dell'identificatore. Non usare spazi vuoti o segni di punteggiatura nell'identificatore dell'errore. È particolarmente importante non usare una virgola. una virgola viene utilizzata da Windows PowerShell per separare l'identificatore e il nome della classe del cmdlet.

### <a name="other-information"></a>Altre informazioni

L'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) può inoltre fornire informazioni che descrivono l'ambiente in cui si è verificato l'errore. Queste informazioni includono elementi quali i dettagli dell'errore, le informazioni sulla chiamata e l'oggetto di destinazione che era in fase di elaborazione quando si è verificato l'errore. Sebbene queste informazioni possano essere utili per l'applicazione host, non vengono in genere utilizzate per identificare l'errore. Queste informazioni sono disponibili tramite le proprietà seguenti:

[System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System. Management. Automation. ErrorRecord. InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System. Management. Automation. ErrorRecord. TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Aggiunta della segnalazione errori non fatale al cmdlet](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Segnalazione errori di Windows PowerShell](./error-reporting-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
