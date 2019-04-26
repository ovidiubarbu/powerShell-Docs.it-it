---
title: L'interpretazione di oggetti ErrorRecord | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2a65b964-5bc6-4ade-a66b-b6afa7351ce7
caps.latest.revision: 9
ms.openlocfilehash: 32ebf2531237bfd1042310ccc4155193a58401fd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067638"
---
# <a name="interpreting-errorrecord-objects"></a>Interpretazione degli oggetti ErrorRecord

Nella maggior parte dei casi, un' [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto rappresenta un errore non irreversibile generato da un comando o uno script. Irreversibili inoltre possibile specificare le informazioni aggiuntive in un ErrorRecord tramite il [System.Management.Automation.Icontainserrorrecord](/dotnet/api/System.Management.Automation.IContainsErrorRecord) interfaccia.

Se si desidera scrivere un gestore degli errori in script o un host alla gestione di errori specifici che si verificano durante l'esecuzione del comando o uno script, è necessario interpretare la [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto per determinare se si rappresenta la classe di errore che si desidera gestire.

Quando un cmdlet rileva una chiusura o errore non irreversibile, è necessario creare un record di errore che descrive la condizione di errore. L'applicazione host deve provare a utilizzare questi record di errore ed eseguire qualsiasi azione sarà possibile limitare l'errore. L'applicazione host deve analizzare anche i record di errore per gli errori non fatali che non è riuscito a elaborare un record, ma sono stati in grado di continuare, e debba esaminare i record di errore per gli errori irreversibili che ha causato la pipeline arrestare.

> [!NOTE]
> Per gli errori irreversibili, chiama il cmdlet di [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) (metodo). Per gli errori non fatali, chiama il cmdlet di [System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) (metodo).

## <a name="error-record-design"></a>Progettazione di Record di errore

I record di errore sono progettati per fornire informazioni aggiuntive sull'errore che non è disponibile nelle eccezioni, garantendo che le informazioni combinate in ogni record di errore sono univoche. L'univocità consente all'applicazione host controllare le diverse parti del record error in modo che in grado di identificare la condizione di errore e deve accettare l'azione dell'host.

## <a name="interpreting-error-records"></a>L'interpretazione dei record degli errori

È possibile verificare diverse parti del record di errore per identificare l'errore. Queste parti seguenti:

- La categoria dell'errore

- L'eccezione di errore

- Identificatore dell'errore completo (FQID)

- Altre informazioni

### <a name="the-error-category"></a>La categoria dell'errore

La categoria dell'errore del record error è una delle costanti predefinite fornite dal [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumerazione. Queste informazioni sono disponibili tramite il [System.Management.Automation.ErrorRecord.CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) proprietà delle [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto.

Il cmdlet è possibile specificare le categorie CloseError OpenError, InvalidType, ReadError e WriteError e altre categorie di errore. L'applicazione host è possibile usare la categoria dell'errore per acquisire i gruppi di errori.

### <a name="the-exception"></a>L'eccezione

L'eccezione inclusa nel record di errore viene fornito dal cmdlet e sono accessibili tramite il [System.Management.Automation.ErrorRecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) proprietà del [ System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto.

Le applicazioni host possono utilizzare il `is` (parola chiave) per indicare che l'eccezione di una classe specifica o di una classe derivata. È preferibile al ramo nel tipo di eccezione, come illustrato nell'esempio seguente.

`if (MyNonTerminatingError.Exception is AccessDeniedException)`

In questo modo, vengono rilevate le classi derivate. Tuttavia, esistono problemi se l'eccezione viene deserializzata.

### <a name="the-fqid"></a>Il FQID

Il FQID rappresenta le informazioni più specifiche è possibile usare per identificare l'errore. È una stringa che include un identificatore definito dal cmdlet, il nome della classe del cmdlet e l'origine che ha segnalato l'errore. In generale, un record di errore è analogo a un record dell'evento di un registro eventi di Windows. Il FQID è analoga alla tupla seguente, che identifica la classe di record dell'evento: (*nome registro*, *origine*, *ID evento*).

Il FQID è progettato per essere controllate come un'unica stringa. Tuttavia, esistono casi in cui l'identificatore dell'errore è progettato per essere analizzato dall'applicazione host. Nell'esempio seguente è un identificatore di errore completo in formato corretto.

`CommandNotFoundException,Microsoft.PowerShell.Commands.GetCommandCommand.`

Nell'esempio precedente, il primo token è l'identificatore dell'errore, seguito dal nome della classe del cmdlet. Identificatore dell'errore può essere un singolo token oppure può essere un identificatore delimitato da punti che consente di creare un ramo in ispezione dell'identificatore. Non usare spazi vuoti o punteggiatura nell'identificatore dell'errore. È particolarmente importante non usare una virgola; una virgola viene utilizzata da Windows PowerShell per separare l'identificatore e il nome della classe cmdlet.

### <a name="other-information"></a>Altre informazioni

Il [System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto può fornire anche le informazioni che descrivono l'ambiente in cui si è verificato l'errore. Queste informazioni includono elementi quali i dettagli dell'errore, le informazioni di chiamata e l'oggetto di destinazione che veniva elaborata quando si è verificato l'errore. Anche se queste informazioni potrebbero essere utili per l'applicazione host, non in genere utilizzato per identificare l'errore. Queste informazioni sono disponibili tramite le proprietà seguenti:

[System.Management.Automation.ErrorRecord.ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails)

[System.Management.Automation.ErrorRecord.InvocationInfo](/dotnet/api/System.Management.Automation.ErrorRecord.InvocationInfo)

[System.Management.Automation.ErrorRecord.TargetObject](/dotnet/api/System.Management.Automation.ErrorRecord.TargetObject)

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Cmdlet.WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[Aggiunta di segnalazione errori al Cmdlet di Non fatale](./adding-non-terminating-error-reporting-to-your-cmdlet.md)

[Segnalazione errori di Windows PowerShell](./error-reporting-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
