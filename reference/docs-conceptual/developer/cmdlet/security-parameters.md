---
title: Parametri di sicurezza | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: 9b4d83aeaf45eab1365dec5fbf48c3c796ed5bde
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369500"
---
# <a name="security-parameters"></a>Parametri di sicurezza

Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri utilizzati per fornire informazioni di sicurezza per un'operazione, ad esempio i parametri che specificano le informazioni sulla chiave del certificato e sui privilegi.

|Parametro|Funzionalità|
|---|---|
|**ACL**<br>Tipo di dati: stringa|Implementare questo parametro per specificare il livello di controllo di accesso di protezione per un catalogo o per un Uniform Resource Identifier (URI).|
|**CertFile**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il nome di un file che contiene uno dei seguenti elementi:<br>-Un certificato x. 509 codificato Base64 o Distinguished Encoding Rules (DER)<br>-Un file di #12 PKCS (Public Key Cryptography Standards) che contiene almeno un certificato e una chiave|
|**CertIssuerName**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il nome dell'emittente di un certificato o in modo che l'utente possa specificare una sottostringa.|
|**CertRequestFile**<br>Tipo di dati: stringa|Implementare questo parametro per specificare il nome di un file che contiene una richiesta di certificato PKCS con codifica Base64 o DER #10.|
|**CertSerialNumber**<br>Tipo di dati: stringa|Implementare questo parametro per specificare il numero di serie emesso dall'autorità di certificazione.|
|**CertStoreLocation**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il percorso dell'archivio certificati. Il percorso è in genere un percorso di file.|
|**CertSubjectName**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare l'emittente di un certificato o in modo che l'utente possa specificare una sottostringa.|
|**CertUsage**<br>Tipo di dati: stringa|Implementare questo parametro per specificare l'utilizzo della chiave o l'utilizzo chiavi avanzato. La chiave può essere rappresentata come una maschera di bit, un bit, un identificatore di oggetto (OID) o una stringa.|
|**Credenziali**<br>Tipo di dati: [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementare questo parametro in modo che il cmdlet chieda automaticamente all'utente un nome utente o una password. Se una credenziale completa non viene fornita direttamente, viene visualizzato un messaggio di richiesta per entrambi.|
|**NomeCSP**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il nome del provider di Servizi certificati (CSP).|
|**CSPType**<br>Tipo di dati: Integer|Implementare questo parametro in modo che l'utente possa specificare il tipo di CSP.|
|**Gruppo**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare una raccolta di entità per l'accesso. Per ulteriori informazioni, vedere la descrizione del parametro **Principal** .|
|**KeyAlgorithm**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare l'algoritmo di generazione delle chiavi da usare per la sicurezza.|
|**KeyContainerName**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il nome del contenitore di chiavi.|
|**KeyLength**<br>Tipo di dati: Integer|Implementare questo parametro in modo che l'utente possa specificare la lunghezza della chiave in bit.|
|**Operazione**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare un'azione che può essere eseguita su un oggetto protetto.|
|**Server principale**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare un'entità identificabile univoca per l'accesso.|
|**Privilegio**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il diritto a cui un cmdlet deve eseguire un'operazione per una determinata entità.|
|**Privilegi**<br>Tipo di dati: matrice di privilegi|Implementare questo parametro in modo che l'utente possa specificare i diritti necessari a un cmdlet per eseguire la relativa operazione per una voce specifica.|
|**Role**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare un set di operazioni che possono essere eseguite da un'entità.|
|**SaveCred**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le credenziali salvate in precedenza dall'utente vengano utilizzate quando si specifica il parametro.|
|**Ambito**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare il gruppo di oggetti protetti per il cmdlet.|
|**SID**<br>Tipo di dati: stringa|Implementare questo parametro in modo che l'utente possa specificare un identificatore univoco che rappresenta un'entità.|
|**Attendibile**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i livelli di attendibilità siano supportati quando si specifica il parametro.|
|**TrustLevel**<br>Tipo di dati: parola chiave|Implementare questo parametro in modo che l'utente possa specificare il livello di attendibilità supportato. Ad esempio, i valori possibili sono Internet, Intranet e FullTrust.|

## <a name="see-also"></a>Vedere anche

[Parametri dei cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
