---
title: I parametri di sicurezza | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e199bba3-90d3-41ca-9d78-cb502e58508d
caps.latest.revision: 6
ms.openlocfilehash: c8b3f907a80d1f6125a5ac04236245503db76ed0
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251303"
---
# <a name="security-parameters"></a>Parametri di sicurezza

La tabella seguente elenca i nomi consigliati e funzionalità per i parametri utilizzati per fornire informazioni di sicurezza per un'operazione, ad esempio i parametri che specificano le informazioni chiave e il privilegio di certificato.

|Parametro|Funzionalità|
|---|---|
|**ACL**<br>Tipo di dati: String|Implementare questo parametro per specificare il livello di controllo di accesso di protezione per un catalogo o per un identificatore URI (Uniform Resource).|
|**CertFile**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome di un file che contiene uno dei seguenti:<br>-Un certificato x.509 con codifica Base64 o Distinguished Encoding Rules (DER)<br>-Un file Public Key Cryptography Standards (PKCS) #12 che contiene almeno un certificato e la chiave|
|**CertIssuerName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome dell'autorità emittente di un certificato o in modo che l'utente può specificare una sottostringa.|
|**CertRequestFile**<br>Tipo di dati: String|Implementare questo parametro per specificare il nome di un file che contiene una richiesta di certificato con codifica DER PKCS #10 o Base64.|
|**CertSerialNumber**<br>Tipo di dati: String|Implementare questo parametro per specificare il numero di serie che è stato rilasciato dall'autorità di certificazione.|
|**CertStoreLocation**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il percorso dell'archivio certificati. Il percorso è in genere un percorso di file.|
|**CertSubjectName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare l'autorità emittente di un certificato o in modo che l'utente può specificare una sottostringa.|
|**CertUsage**<br>Tipo di dati: String|Implementare questo parametro per specificare l'utilizzo della chiave o l'utilizzo chiavi avanzato. La chiave può essere rappresentata come una maschera di bit, un po', un identificatore di oggetto (OID), o una stringa.|
|**Credenziali**<br>Tipo di dati: [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential)|Implementare questo parametro in modo che il cmdlet chiederà automaticamente all'utente per un nome utente o password. Se una credenziale completa non viene fornita direttamente, viene visualizzato un prompt dei comandi per entrambi.|
|**CSPName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome del provider di servizi certificati (CSP).|
|**CSPType**<br>Tipo di dati: Intero|Implementare questo parametro in modo che l'utente può specificare il tipo di CSP.|
|**Gruppo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare una raccolta di entità per l'accesso. Per altre informazioni, vedere la descrizione del **Principal** parametro.|
|**KeyAlgorithm**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare l'algoritmo di generazione della chiave da usare per la sicurezza.|
|**KeyContainerName**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il nome del contenitore di chiavi.|
|**KeyLength**<br>Tipo di dati: Intero|Implementare questo parametro in modo che l'utente può specificare la lunghezza della chiave in bit.|
|**Operazione**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un'azione che può essere eseguita su un oggetto protetto.|
|**Entità**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un'entità di identificazione univoca per l'accesso.|
|**con privilegi**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il diritto di che un cmdlet deve eseguire un'operazione per una particolare entità.|
|**Privilegi**<br>Tipo di dati: Matrice dei privilegi|Implementare questo parametro in modo che l'utente può specificare i diritti di un cmdlet necessari per eseguire l'operazione per una particolare voce.|
|**Ruolo**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un set di operazioni che possono essere eseguite da un'entità.|
|**SaveCred**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che le credenziali che sono state salvate in precedenza dall'utente da utilizzare quando viene specificato il parametro.|
|**Ambito**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare il gruppo di oggetti protetti per il cmdlet.|
|**SID**<br>Tipo di dati: String|Implementare questo parametro in modo che l'utente può specificare un identificatore univoco che rappresenta un'entità.|
|**attendibile**<br>Tipo di dati: SwitchParameter|Implementare questo parametro in modo che i livelli di attendibilità sono supportati quando il parametro è specificato.|
|**TrustLevel**<br>Tipo di dati: Parola chiave|Implementare questo parametro in modo che l'utente può specificare il livello di attendibilità è supportato. Ad esempio, i valori possibili includono internet, intranet e fulltrust.|

## <a name="see-also"></a>Vedere anche

[Parametri del cmdlet](./cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Windows PowerShell SDK](../windows-powershell-reference.md)
