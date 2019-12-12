---
title: Linee guida per lo sviluppo consultivo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 79c9bcbc-a2eb-4253-a4b8-65ba54ce8d01
caps.latest.revision: 9
ms.openlocfilehash: 980b488800587e31286e2ca2ece924e07f8af3f3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370040"
---
# <a name="advisory-development-guidelines"></a>Linee guida sullo sviluppo consigliate

In questa sezione vengono descritte le linee guida da considerare per garantire un ambiente di sviluppo e un'esperienza utente soddisfacenti. In alcuni casi potrebbero non essere applicabili.

## <a name="design-guidelines"></a>Linee guida per la progettazione

Quando si progettano i cmdlet, è necessario considerare le linee guida seguenti. Quando si individuano le linee guida per la progettazione applicabili alla propria situazione, assicurarsi di esaminare le linee guida del codice per le linee guida simili.

### <a name="support-an-inputobject-parameter-ad01"></a>Supporto di un parametro InputObject (AD01)

Poiché Windows PowerShell funziona direttamente con gli oggetti di Microsoft .NET Framework, un oggetto .NET Framework è spesso disponibile che corrisponde esattamente al tipo richiesto dall'utente per eseguire una determinata operazione. `InputObject` è il nome standard di un parametro che accetta come input un oggetto di questo tipo. Ad esempio, il cmdlet di esempio **Stop-proc** nell' [esercitazione StopProc](./stopproc-tutorial.md) definisce un parametro `InputObject` di tipo process che supporta l'input dalla pipeline. L'utente può ottenere un set di oggetti processo, manipolarli per selezionare gli oggetti esatti da arrestare, quindi passarli direttamente al cmdlet **Stop-proc** .

### <a name="support-the-force-parameter-ad02"></a>Supporto del parametro Force (AD02)

Occasionalmente, un cmdlet deve proteggere l'utente dall'esecuzione di un'operazione richiesta. Questo cmdlet deve supportare un parametro `Force` per consentire all'utente di eseguire l'override della protezione se l'utente dispone delle autorizzazioni per eseguire l'operazione.

Il cmdlet [Remove-Item](/powershell/module/microsoft.powershell.management/remove-item) , ad esempio, in genere non rimuove un file di sola lettura. Tuttavia, questo cmdlet supporta un `Force` parametro in modo che un utente possa forzare la rimozione di un file di sola lettura. Se l'utente dispone già dell'autorizzazione per modificare l'attributo di sola lettura e l'utente rimuove il file, l'utilizzo del `Force` parametro semplifica l'operazione. Tuttavia, se l'utente non dispone dell'autorizzazione per rimuovere il file, il `Force` parametro non ha alcun effetto.

### <a name="handle-credentials-through-windows-powershell-ad03"></a>Gestire le credenziali tramite Windows PowerShell (AD03)

Un cmdlet deve definire un parametro di `Credential` per rappresentare le credenziali. Questo parametro deve essere di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) e deve essere definito utilizzando una dichiarazione dell'attributo Credential. Questo supporto richiede automaticamente l'utente per il nome utente, la password o per entrambi quando una credenziale completa non viene direttamente fornita. Per altre informazioni sull'attributo Credential, vedere [dichiarazione dell'attributo Credential](./credential-attribute-declaration.md).

### <a name="support-encoding-parameters-ad04"></a>Supporto dei parametri di codifica (AD04)

Se il cmdlet legge o scrive testo in o da un formato binario, ad esempio scrivendo o leggendo da un file in un file System, il cmdlet deve disporre di un parametro Encoding che specifichi la modalità di codifica del testo nel formato binario.

### <a name="test-cmdlets-should-return-a-boolean-ad05"></a>I cmdlet di test devono restituire un valore booleano (AD05)

I cmdlet che eseguono test sulle risorse devono restituire un tipo [System. Boolean](/dotnet/api/System.Boolean) alla pipeline in modo che possano essere usati nelle espressioni condizionali.

## <a name="code-guidelines"></a>Linee guida del codice

Le linee guida seguenti devono essere prese in considerazione durante la scrittura del codice del cmdlet. Quando si individuano le linee guida applicabili alla propria situazione, assicurarsi di esaminare le linee guida per la progettazione di linee guida simili.

### <a name="follow-cmdlet-class-naming-conventions-ac01"></a>Seguire le convenzioni di denominazione della classe cmdlet (AC01)

Seguendo le convenzioni di denominazione standard, è possibile rendere i cmdlet più individuabili e aiutare l'utente a capire esattamente quali sono i cmdlet. Questa procedura è particolarmente importante per altri sviluppatori che usano Windows PowerShell perché i cmdlet sono tipi pubblici.

#### <a name="define-a-cmdlet-in-the-correct-namespace"></a>Definire un cmdlet nello spazio dei nomi corretto

Normalmente si definisce la classe per un cmdlet in uno spazio dei nomi .NET Framework che accoda ". Comandi "allo spazio dei nomi che rappresenta il prodotto in cui viene eseguito il cmdlet. I cmdlet inclusi in Windows PowerShell, ad esempio, sono definiti nello spazio dei nomi `Microsoft.PowerShell.Commands`.

#### <a name="name-the-cmdlet-class-to-match-the-cmdlet-name"></a>Denominare la classe cmdlet in modo che corrisponda al nome del cmdlet

Quando si rinomina la classe .NET Framework che implementa un cmdlet, denominare la classe " *\<verbo > **\<sostantivo*** \<comando >", in cui si sostituisce il *verbo\<* > e\<i segnaposto > *sostantivo* con il verbo e il sostantivo utilizzati per il nome del cmdlet. Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) , ad esempio, viene implementato da una classe denominata `GetProcessCommand`.

### <a name="if-no-pipeline-input-override-the-beginprocessing-method-ac02"></a>Se nessun input della pipeline esegue l'override del metodo BeginProcessing (AC02)

Se il cmdlet non accetta input dalla pipeline, l'elaborazione deve essere implementata nel metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) . L'uso di questo metodo consente a Windows PowerShell di mantenere l'ordinamento tra i cmdlet. Il primo cmdlet della pipeline restituisce sempre i relativi oggetti prima che i cmdlet rimanenti nella pipeline ottengano la possibilità di avviare l'elaborazione.

### <a name="to-handle-stop-requests-override-the-stopprocessing-method-ac03"></a>Per gestire le richieste di arresto, eseguire l'override del metodo StopProcessing (AC03)

Eseguire l'override del metodo [System. Management. Automation. cmdlet. StopProcessing](/dotnet/api/System.Management.Automation.Cmdlet.StopProcessing) in modo che il cmdlet possa gestire il segnale di arresto. Per alcuni cmdlet è necessario molto tempo per completare l'operazione e consentire un lungo periodo di tempo tra le chiamate al runtime di Windows PowerShell, ad esempio quando il cmdlet blocca il thread nelle chiamate RPC con esecuzione prolungata. Sono inclusi i cmdlet che effettuano chiamate al metodo [System. Management. Automation. cmdlet. WriteObject](/dotnet/api/System.Management.Automation.Cmdlet.WriteObject) , al metodo [System. Management. Automation. cmdlet. WriteError](/dotnet/api/System.Management.Automation.Cmdlet.WriteError) e ad altri meccanismi di feedback che possono richiedere molto tempo per il completamento. In questi casi, l'utente potrebbe dover inviare un segnale di arresto a questi cmdlet.

### <a name="implement-the-idisposable-interface-ac04"></a>Implementare l'interfaccia IDisposable (AC04)

Se il cmdlet dispone di oggetti che non sono stati eliminati (scritti nella pipeline) dal metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , il cmdlet potrebbe richiedere l'eliminazione di oggetti aggiuntivi. Se, ad esempio, il cmdlet apre un handle di file nel metodo [System. Management. Automation. cmdlet. BeginProcessing](/dotnet/api/System.Management.Automation.Cmdlet.BeginProcessing) e mantiene aperto l'handle per l'uso da parte del metodo [System. Management. Automation. cmdlet. ProcessRecord](/dotnet/api/System.Management.Automation.Cmdlet.ProcessRecord) , questo handle deve essere chiuso al termine dell'elaborazione.

Il runtime di Windows PowerShell non chiama sempre il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) . Ad esempio, il metodo [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) potrebbe non essere chiamato se il cmdlet viene annullato a metà durante l'operazione o se si verifica un errore di terminazione in qualsiasi parte del cmdlet. Pertanto, la classe .NET Framework per un cmdlet che richiede la pulizia degli oggetti deve implementare il modello di interfaccia [System. IDisposable](/dotnet/api/System.IDisposable) completo, incluso il finalizzatore, in modo che il runtime di Windows PowerShell possa chiamare entrambi i metodi [System. Management. Automation. cmdlet. EndProcessing](/dotnet/api/System.Management.Automation.Cmdlet.EndProcessing) e [System. IDisposable. Dispose *](/dotnet/api/System.IDisposable.Dispose) al termine dell'elaborazione.

### <a name="use-serialization-friendly-parameter-types-ac05"></a>Usare tipi di parametro descrittivi per la serializzazione (AC05)

Per supportare l'esecuzione del cmdlet su computer remoti, usare i tipi che possono essere facilmente serializzati nel computer client e quindi riattivati nel computer server. I tipi seguenti sono semplici da serializzare.

Tipi primitivi:

- Byte, SByte, Decimal, Single, Double, Int16, Int32, Int64, UInt16, UInt32 e UInt64.

- Boolean, Guid, byte [], TimeSpan, DateTime, Uri e Version.

- Char, String, XmlDocument.

Tipi di rehydratable predefiniti:

- PSPrimitiveDictionary

- SwitchParameter

- PSListModifier

- PSCredential

- IPAddress, MailAddress

- CultureInfo

- X509Certificate2, X500DistinguishedName

- DirectorySecurity, FileSecurity, RegistrySecurity

Altri tipi:

- StringaSicura

- Contenitori (elenchi e dizionari del tipo precedente)

### <a name="use-securestring-for-sensitive-data-ac06"></a>Usare SecureString per i dati sensibili (AC06)

Quando si gestiscono dati sensibili, utilizzare sempre il tipo di dati [System. Security. SecureString](/dotnet/api/System.Security.SecureString) . Ciò può includere l'input della pipeline ai parametri, oltre a restituire dati sensibili alla pipeline.

## <a name="see-also"></a>Vedere anche

[Linee guida per lo sviluppo richieste](./required-development-guidelines.md)

[Linee guida per lo sviluppo fortemente consigliate](./strongly-encouraged-development-guidelines.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
