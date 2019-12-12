---
title: Record degli errori di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- error category [PowerShell SDK]
- error identifier [PowerShell SDK]
- error records [PowerShell SDK]
- error category string [PowerShell SDK]
ms.assetid: bdd66fea-eb63-4bb6-9cbe-9a799e5e0db5
caps.latest.revision: 9
ms.openlocfilehash: 5412d88b690a1f5f1ef387416e3bf9da3a32c95d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369110"
---
# <a name="windows-powershell-error-records"></a>Record degli errori di Windows PowerShell

I cmdlet devono passare un oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) che identifica la condizione di errore per gli errori di terminazione e non fatale.

L'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) contiene le informazioni seguenti:

- Eccezione che descrive l'errore. Spesso si tratta di un'eccezione che il cmdlet ha rilevato e convertito in un record di errore. Ogni record di errore deve contenere un'eccezione.

Se il cmdlet non ha intercettato un'eccezione, deve creare una nuova eccezione e scegliere la classe di eccezione che meglio descrive la condizione di errore. Tuttavia, non è necessario generare l'eccezione perché è possibile accedervi tramite la proprietà [System. Management. Automation. ErrorRecord. Exception](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) dell'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) .

- Identificatore di errore che fornisce un indicatore di destinazione che può essere utilizzato per scopi diagnostici e per gli script di Windows PowerShell per gestire condizioni di errore specifiche con gestori di errori specifici. Ogni record di errore deve contenere un identificatore di errore (vedere l'identificatore di errore).

- Categoria di errori che fornisce un indicatore generale che può essere utilizzato per scopi diagnostici. Ogni record di errore deve specificare una categoria di errori (vedere la categoria di errore).

- Un messaggio di errore di sostituzione facoltativo e un'azione consigliata (vedere il messaggio di errore di sostituzione).

- Informazioni di chiamata facoltative sul cmdlet che ha generato l'errore. Queste informazioni vengono specificate da Windows PowerShell (vedere il messaggio di chiamata).

- Oggetto di destinazione che era in fase di elaborazione quando si è verificato l'errore. Questo potrebbe essere l'oggetto di input o un altro oggetto che è stato elaborato dal cmdlet. Per il comando `remove-item -recurse c:\somedirectory`, ad esempio, l'errore potrebbe essere un'istanza di un oggetto FileInfo per "c:\somedirectory\lockedfile". Le informazioni sull'oggetto di destinazione sono facoltative.

## <a name="error-identifier"></a>Identificatore errore

Quando si crea un record di errore, specificare un identificatore che definisce la condizione di errore all'interno del cmdlet. Windows PowerShell combina l'identificatore di destinazione con il nome del cmdlet per creare un identificatore di errore completo. È possibile accedere all'identificatore di errore completo tramite la proprietà [System. Management. Automation. ErrorRecord. FullyQualifiedErrorId](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) dell'oggetto [System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord) . L'identificatore di errore non è disponibile da solo. È disponibile solo come parte dell'identificatore di errore completo.

Usare le linee guida seguenti per generare identificatori di errore quando si creano i record degli errori:

- Consente di creare identificatori di errore specifici di una condizione di errore. Individuare gli identificatori di errore per scopi diagnostici e per gli script che gestiscono condizioni di errore specifiche con gestori di errori specifici. Un utente dovrebbe essere in grado di utilizzare l'identificatore di errore per identificare l'errore e la relativa origine. Gli identificatori di errore consentono inoltre la creazione di report per condizioni di errore specifiche da eccezioni esistenti, in modo che le nuove sottoclassi di eccezione non siano necessarie.

- In generale, assegnare identificatori di errore diversi a percorsi di codice diversi. L'utente finale trae vantaggio da identificatori specifici. Spesso ogni percorso di codice che chiama [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ha un proprio identificatore. Come regola, definire un nuovo identificatore quando si definisce una nuova stringa di modello per il messaggio di errore e viceversa. Non utilizzare il messaggio di errore come identificatore.

- Quando si pubblica il codice usando un identificatore di errore specifico, viene stabilita la semantica degli errori con tale identificatore per il ciclo di vita del supporto completo del prodotto. Non riutilizzarlo in un contesto semanticamente diverso dal contesto originale. Se la semantica di questo errore viene modificata, creare e quindi utilizzare un nuovo identificatore.

- È in genere consigliabile usare un identificatore di errore specifico solo per le eccezioni di un particolare tipo CLR. Se il tipo dell'eccezione o il tipo dell'oggetto di destinazione viene modificato, creare e quindi utilizzare un nuovo identificatore.

- Scegliere il testo per l'identificatore di errore che corrisponde in modo conciso all'errore che si sta segnalando. Utilizzare le convenzioni di denominazione e delle maiuscole .NET Framework standard. Non usare spazi vuoti o segni di punteggiatura. Non localizzare gli identificatori degli errori.

- Non generare in modo dinamico gli identificatori di errore in modo non riproducibile. Ad esempio, non inserire informazioni sugli errori, ad esempio un ID processo. Gli identificatori di errore sono utili solo se corrispondono agli identificatori di errore visualizzati da altri utenti che riscontrano la stessa condizione di errore.

## <a name="error-category"></a>Categoria errore

Quando si crea un record di errore, specificare la categoria dell'errore usando una delle costanti definite dall'enumerazione [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) . Windows PowerShell usa la categoria Error per visualizzare le informazioni sugli errori quando gli utenti impostano la variabile `$ErrorView` su `"CategoryView"`.

Evitare di usare la costante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) **NotSpecified** . Se si dispone di informazioni sull'errore o sull'operazione che ha causato l'errore, scegliere la categoria che meglio descrive l'errore o l'operazione, anche se la categoria non corrisponde a una corrispondenza perfetta.

Le informazioni visualizzate da Windows PowerShell sono definite stringa di visualizzazione delle categorie e vengono compilate in base alle proprietà della classe [System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) . Questa classe è accessibile tramite la proprietà Error [System. Management. Automation. ErrorRecord. CategoryInfo](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) .

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

Nell'elenco seguente vengono descritte le informazioni visualizzate:

- Category: costante [System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0) definita da Windows PowerShell.

- TargetName: per impostazione predefinita, il nome dell'oggetto che è stato elaborato dal cmdlet quando si è verificato l'errore. O, un'altra stringa definita dal cmdlet.

- TargetType: per impostazione predefinita, il tipo dell'oggetto di destinazione. O, un'altra stringa definita dal cmdlet.

- Activity: per impostazione predefinita, il nome del cmdlet che ha creato il record di errore. Oppure, altre stringhe definite dal cmdlet.

- Motivo: per impostazione predefinita, il tipo di eccezione. O, un'altra stringa definita dal cmdlet.

## <a name="replacement-error-message"></a>Messaggio di errore di sostituzione

Quando si sviluppa un record di errore per un cmdlet, il messaggio di errore predefinito per l'errore deriva dal testo del messaggio predefinito nella proprietà [System. Exception. Message](/dotnet/api/System.Exception.Message) . Si tratta di una proprietà di sola lettura il cui testo del messaggio è destinato solo a scopi di debug, in base alle linee guida .NET Framework. Si consiglia di creare un messaggio di errore che sostituisce o aumenta il testo del messaggio predefinito. Rendere il messaggio più semplice e più specifico per il cmdlet.

Il messaggio di sostituzione viene fornito da un oggetto [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) . Usare uno dei costruttori seguenti di questo oggetto perché forniscono informazioni di localizzazione aggiuntive che possono essere usate da Windows PowerShell.

- [ErrorDetails (cmdlet, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Management_Automation_Cmdlet_System_String_System_String_System_Object___): usare questo costruttore se la stringa del modello è una stringa di risorsa nello stesso assembly in cui è implementato il cmdlet o se si vuole caricare la stringa del modello tramite un override del metodo [System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) .

- [ErrorDetails (assembly, String, String, Object [])](/dotnet/api/system.management.automation.errordetails.-ctor?view=pscore-6.2.0#System_Management_Automation_ErrorDetails__ctor_System_Reflection_Assembly_System_String_System_String_System_Object___): usare questo costruttore se la stringa del modello si trova in un altro assembly e non viene caricata tramite un override di [System. Management. Automation. cmdlet. GetResourceString](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Il messaggio di sostituzione deve essere conforme alle linee guida di progettazione .NET Framework per la scrittura di messaggi di eccezione con una piccola differenza. Lo stato delle linee guida indica che i messaggi di eccezione devono essere scritti per gli sviluppatori. Questi messaggi di sostituzione devono essere scritti per l'utente del cmdlet.

È necessario aggiungere il messaggio di errore di sostituzione prima di chiamare i metodi [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) . Per aggiungere un messaggio di sostituzione, impostare la proprietà [System. Management. Automation. ErrorRecord. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) del record di errore. Quando questa proprietà è impostata, Windows PowerShell Visualizza la proprietà [System. Management. Automation. ErrorDetails. Message *](/dotnet/api/System.Management.Automation.ErrorDetails.Message) anziché il testo del messaggio predefinito.

## <a name="recommended-action-information"></a>Informazioni sulle azioni consigliate

L'oggetto [System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails) può inoltre fornire informazioni sulle azioni consigliate quando si verifica l'errore.

## <a name="invocation-information"></a>Informazioni sulla chiamata

Quando un cmdlet USA [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) o [System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) per segnalare un record di errore, Windows PowerShell aggiunge automaticamente informazioni che descrivono il comando che è stato richiamato quando si è verificato l'errore. Queste informazioni vengono fornite da un oggetto [System. Management. Automation. invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) contenente il nome del cmdlet richiamato dal comando, il comando stesso e le informazioni sulla pipeline o lo script. Questa proprietà è di sola lettura.

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System. Management. Automation. cmdlet. ThrowTerminatingError *](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System. Management. Automation. ErrorCategory](/dotnet/api/System.Management.Automation.ErrorCategory?view=pscore-6.2.0)

[System. Management. Automation. Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System. Management. Automation. ErrorRecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System. Management. Automation. ErrorDetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System. Management. Automation. invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Segnalazione errori di Windows PowerShell](./error-reporting-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
