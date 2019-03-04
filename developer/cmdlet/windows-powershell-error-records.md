---
title: Errore di Windows PowerShell registra | Microsoft Docs
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
ms.openlocfilehash: bbe04a8fb556f0f6807bc0eae6634e3cf505759e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56861977"
---
# <a name="windows-powershell-error-records"></a>Record degli errori di Windows PowerShell

I cmdlet è necessario passare un [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) che identifica la condizione di errore per gli errori irreversibili e non irreversibili.

Il [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetto contiene le informazioni seguenti:

- Eccezione che descrive l'errore. Spesso, si tratta di un'eccezione che il cmdlet intercettati e convertito in un record di errore. Ogni record di errore deve contenere un'eccezione.

Se il cmdlet non è stata intercettata un'eccezione, è necessario creare una nuova eccezione e scegli la classe di eccezione che meglio descrive la condizione di errore. Tuttavia, non è necessario generare l'eccezione in quanto sono accessibili tramite il [System.Management.Automation.Errorrecord.Exception*](/dotnet/api/System.Management.Automation.ErrorRecord.Exception) proprietà del [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord) oggetti.

- Un identificatore dell'errore che fornisce un identificatore di destinazione che può essere utilizzato per scopi diagnostici e dagli script di Windows PowerShell per gestire le condizioni di errore specifici con i gestori degli errori specifico. Ogni record di errore deve contenere un identificatore di errore (vedere l'identificatore dell'errore).

- Una categoria di errore che fornisce un identificatore di tipo generale che può essere utilizzato per scopi diagnostici. Ogni record error è necessario specificare una categoria di errore (vedere la categoria dell'errore).

- Un messaggio di errore di sostituzione facoltativi e un'azione consigliata (vedere il messaggio di errore di sostituzione).

- Informazioni di chiamata facoltativo sul cmdlet che ha generato l'errore. Queste informazioni vengono specificate da Windows PowerShell (vedere il messaggio di chiamata).

- Oggetto di destinazione che veniva elaborata quando si è verificato l'errore. Ciò potrebbe essere l'oggetto di input oppure potrebbe essere un altro oggetto che stava elaborando i cmdlet. Ad esempio, per il comando `remove-item -recurse c:\somedirectory`, l'errore potrebbe essere un'istanza di un oggetto FileInfo per "c:\somedirectory\lockedfile". Le informazioni sull'oggetto di destinazione è facoltative.

## <a name="error-identifier"></a>Identificatore dell'errore

Quando si crea un record di errore, specificare un identificatore che definisce la condizione di errore all'interno del cmdlet. Windows PowerShell combina l'identificatore di destinazione con il nome del cmdlet per creare un identificatore di errore completo. Identificatore dell'errore completo sono accessibili tramite il [System.Management.Automation.Errorrecord.Fullyqualifiederrorid*](/dotnet/api/System.Management.Automation.ErrorRecord.FullyQualifiedErrorId) proprietà del [System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)oggetto. Identificatore dell'errore non è disponibile da solo. È disponibile solo come parte dell'identificatore di errore completo.

Usare le linee guida seguenti per generare gli identificatori degli errori quando si creano record di errore:

- Creare gli identificatori degli errori specifici di una condizione di errore. Per scopi diagnostici e per gli script che gestiscono le condizioni di errore specifici con i gestori degli errori specifico come destinazione gli identificatori di errore. Un utente deve essere in grado di usare l'identificatore dell'errore per identificare l'errore e la relativa origine. Gli identificatori di errore anche abilitare il reporting per condizioni di errore specifiche dalle eccezioni esistenti in modo che nuova sottoclassi di eccezioni non sono necessarie.

- In generale, è possibile assegnare gli identificatori di errore diverso da percorsi del codice diversi. L'utente finale può beneficiare identificatori specifici. Spesso, ogni percorso di codice che chiama [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oppure [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) ha un proprio identificatore. Di norma, definire un nuovo identificatore quando si definisce una nuova stringa di modello per il messaggio di errore e viceversa. Non usare il messaggio di errore come identificatore.

- Quando si pubblica codice utilizzando un identificatore di un determinato errore, si stabilisce che la semantica degli errori con tale identificatore per il prodotto completo supporto del ciclo di vita. Non riutilizzare, in un contesto che è semanticamente diverso dal contesto originale. Se modifica la semantica di questo errore, creare e usare quindi un nuovo identificatore.

- È in genere deve usare un identificatore di un determinato errore solo per le eccezioni di un determinato tipo CLR. Se il tipo dell'eccezione o il tipo dell'oggetto di destinazione viene modificato, creare e usare quindi un nuovo identificatore.

- Scegliere il testo per l'identificatore dell'errore in modo conciso corrispondente all'errore che si sta segnalando. Usare convenzioni di denominazione e l'uso delle maiuscole .NET Framework standard. Non usare spazi vuoti o punteggiatura. Non deve essere localizzata gli identificatori degli errori.

- Non generare in modo dinamico gli identificatori degli errori in modo non riproducibile. Ad esempio, non la incorporano informazioni sull'errore, ad esempio un ID del processo. Gli identificatori di errore sono utili solo se corrispondono agli identificatori errore visualizzati da altri utenti che hanno riscontrato la stessa condizione di errore.

## <a name="error-category"></a>Categoria dell'errore

Quando si crea un record di errore, specificare la categoria dell'errore usando una delle costanti definite per il [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) enumerazione. Windows PowerShell Usa la categoria dell'errore per visualizzare informazioni sugli errori quando gli utenti di impostare il `$ErrorView` variabile `"CategoryView"`.

Evitare di usare la [System.Management.Automation.Errorcategory.Notspecified](/dotnet/api/System.Management.Automation.ErrorCategory.NotSpecified) costante. Se si dispone di tutte le informazioni sull'errore o sull'operazione che ha causato l'errore, scegliere la categoria che meglio descrive l'errore o l'operazione, anche se la categoria non è perfetta.

Le informazioni visualizzate da Windows PowerShell viene definite come stringa di visualizzazione per categorie e progettate per le proprietà del [System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo) classe. (Questa classe avviene tramite l'errore [System.Management.Automation.Errorrecord.Categoryinfo*](/dotnet/api/System.Management.Automation.ErrorRecord.CategoryInfo) proprietà.)

```
{Category}: ({TargetName}:{TargetType}):[{Activity}], {Reason}
```

L'elenco seguente descrive le informazioni visualizzate:

- Categoria: Windows PowerShell-definite [System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory) costante.

- TargetName: Per impostazione predefinita, il nome dell'oggetto cmdlet stava elaborando quando si è verificato l'errore. In alternativa, un'altra stringa definite cmdlet.

- TargetType: Per impostazione predefinita, il tipo dell'oggetto di destinazione. In alternativa, un'altra stringa definite cmdlet.

- Attività: Per impostazione predefinita, il nome del cmdlet che ha creato il record di errore. In alternativa, un'altra stringa definite cmdlet.

- Motivo: Per impostazione predefinita, il tipo di eccezione. In alternativa, un'altra stringa definite cmdlet.

## <a name="replacement-error-message"></a>Messaggio di errore di sostituzione

Quando si sviluppa un record di errore per un cmdlet, il messaggio di errore predefinito per l'errore proviene il testo del messaggio predefinito nel [System.Exception.Message](/dotnet/api/System.Exception.Message) proprietà. Questa è una proprietà di sola lettura il cui testo del messaggio è destinato solo a scopo di debug (in base alle linee guida di .NET Framework). È consigliabile creare un messaggio di errore che sostituisce o aggiunge il testo del messaggio predefinito. Rendere il messaggio più semplice e più specifico al cmdlet.

Il messaggio di sostituzione viene fornito da un [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) oggetto. Usare uno dei seguenti costruttori di questo oggetto perché forniscono informazioni di localizzazione aggiuntivo che possono essere utilizzate da Windows PowerShell.

- [ErrorDetails.ErrorDetails (Cmdlet, stringa, stringa, oggetto\[System.Management.Automation.Errordetails.%23Ctor%28System.Management.Automation.Cmdlet%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Management.Automation.Cmdlet%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilizzare questo costruttore se la stringa di modello è una stringa di risorsa nello stesso assembly in cui viene implementato il cmdlet o se si desidera caricare la stringa di modello tramite un override del [System.Management.Automation.Cmdlet.Getresourcestring* ](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString) (metodo).

- [ErrorDetails.ErrorDetails (Assembly, stringa, stringa, oggetto\[System.Management.Automation.Errordetails.%23Ctor%28System.Reflection.Assembly%2Csystem.String%2Csystem.String%2Csystem.Object%5B%5D%29? Displayproperty = Fullname](/dotnet/api/System.Management.Automation.ErrorDetails.%23ctor%28System.Reflection.Assembly%2CSystem.String%2CSystem.String%2CSystem.Object%5B%5D%29): Utilizzare questo costruttore se la stringa di modello si trova in un altro assembly e non caricarli tramite un override di [System.Management.Automation.Cmdlet.Getresourcestring*](/dotnet/api/System.Management.Automation.Cmdlet.GetResourceString).

Il messaggio di sostituzione deve essere conformi alle linee guida di progettazione .NET Framework per la scrittura di messaggi di eccezione con una piccola differenza. Lo stato di linee guida che devono essere scritti i messaggi di eccezione per gli sviluppatori. Questi messaggi di sostituzione devono essere scritti per l'utente di cmdlet.

Il messaggio di errore di sostituzione deve essere aggiunto prima la [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oppure [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) metodi vengono chiamati . Per aggiungere un messaggio di sostituzione, impostare il [System.Management.Automation.Errorrecord.Errordetails*](/dotnet/api/System.Management.Automation.ErrorRecord.ErrorDetails) proprietà del record error. Quando questa proprietà è impostata, Windows PowerShell Visualizza il [System.Management.Automation.Errordetails.Message*](/dotnet/api/System.Management.Automation.ErrorDetails.Message) proprietà anziché il testo del messaggio predefinito.

## <a name="recommended-action-information"></a>Informazioni sull'azione consigliata

Il [System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails) oggetto può anche fornire informazioni su quali azioni sono consigliate quando si verifica l'errore.

## <a name="invocation-information"></a>Informazioni di chiamata

Quando un cmdlet viene utilizzato [System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) oppure [System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError) per segnalare un record di errore, Windows PowerShell Aggiunge automaticamente le informazioni che descrivono il comando che è stato richiamato quando si è verificato l'errore. Queste informazioni vengono fornite da un [System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo) oggetto che contiene il nome del cmdlet per cui è stato richiamato con il comando, comando stesso e informazioni sulle pipeline o script. Questa proprietà è di sola lettura.

## <a name="see-also"></a>Vedere anche

[System.Management.Automation.Cmdlet.Writeerror*](/dotnet/api/System.Management.Automation.Cmdlet.WriteError)

[System.Management.Automation.Cmdlet.Throwterminatingerror*](/dotnet/api/System.Management.Automation.Cmdlet.ThrowTerminatingError)

[System.Management.Automation.Errorcategory](/dotnet/api/System.Management.Automation.ErrorCategory)

[System.Management.Automation.Errorcategoryinfo](/dotnet/api/System.Management.Automation.ErrorCategoryInfo)

[System.Management.Automation.Errorrecord](/dotnet/api/System.Management.Automation.ErrorRecord)

[System.Management.Automation.Errordetails](/dotnet/api/System.Management.Automation.ErrorDetails)

[System.Management.Automation.Invocationinfo](/dotnet/api/System.Management.Automation.InvocationInfo)

[Segnalazione errori di Windows PowerShell](./error-reporting-concepts.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
