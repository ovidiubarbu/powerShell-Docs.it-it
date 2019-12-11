---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Considerazioni sulla sicurezza in JEA
ms.openlocfilehash: befc24fec368c4f6d60477daf63bf17e9431133e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "70017772"
---
# <a name="jea-security-considerations"></a>Considerazioni sulla sicurezza in JEA

JEA consente di migliorare le condizioni di sicurezza, riducendo il numero di amministratori permanenti nei computer. JEA usa una configurazione di sessione di PowerShell per creare un nuovo punto di ingresso che consente agli utenti di gestire il sistema. Agli utenti che richiedono un livello di accesso al computer elevato ma non illimitato per eseguire attività amministrative è possibile concedere l'accesso all'endpoint JEA. Poiché JEA consente di eseguire i comandi di amministratore anche senza avere l'accesso amministratore, è possibile rimuovere questi utenti dai gruppi di sicurezza con privilegi elevati.

## <a name="run-as-account"></a>Account Esegui come

Ogni endpoint JEA ha un account **Esegui come**. Questo è l'account con cui vengono eseguite le azioni dell'utente connesso. Questo account è configurabile nel [file di configurazione sessione](session-configurations.md), e l'account scelto ha un impatto significativo sulla sicurezza dell'endpoint.

Gli **account virtuali** sono il metodo consigliato per configurare l'account **Esegui come**. Gli account virtuali sono account locali temporanei creati per l'utente che si connette e possono essere usati solo per la durata della sessione JEA. Al termine della sessione l'account virtuale viene eliminato e non può più essere usato. L'utente che si connette non conosce le credenziali dell'account virtuale. L'account virtuale non può essere usato per accedere al sistema con altri mezzi, come Desktop remoto o un endpoint di PowerShell non vincolato.

Per impostazione predefinita gli account virtuali appartengono al gruppo **Administrators** locale del computer. Per questo motivo, hanno diritti completi per gestire qualsiasi elemento nel sistema, ma non possono gestire le risorse della rete.
Durante l'autenticazione con altri computer, il contesto utente è l'account del computer locale, non l'account virtuale.

I controller di dominio rappresentano un caso speciale, perché non è presente un gruppo **Administrators**. Gli account virtuali appartengono invece al gruppo **Domain Admins** e possono gestire i servizi directory nel controller di dominio. L'uso dell'identità del dominio resta limitato al controller di dominio in cui è stata creata la sessione JEA. Qualsiasi accesso alla rete sembra provenire dall'oggetto computer controller di dominio.

In entrambi i casi, è possibile definire in modo esplicito a quale gruppo di sicurezza appartiene l'account virtuale. Questa è una procedura efficace se l'attività può essere eseguita senza privilegi di amministratore locale o di dominio. Se è già disponibile un gruppo di sicurezza definito per gli amministratori, concedere all'account virtuale l'appartenenza a tale gruppo. L'appartenenza a gruppi dell'account virtuale è limitato ai gruppi di sicurezza locali nella workstation e nei server membri. Nei controller di dominio gli account virtuali devono essere membri di gruppi di sicurezza del dominio.
Dopo che l'account virtuale è stato aggiunto a uno o più gruppi di sicurezza, non appartiene più ai gruppi predefiniti (amministratore locale o di dominio).

La tabella seguente illustra le opzioni di configurazione possibili e le autorizzazioni risultanti per gli account virtuali:

|        Tipo di computer         | Configurazione del gruppo di account virtuali |                   Contesto dell'utente locale                    | Contesto dell'utente di rete |
| ---------------------------- | ----------------------------------- | ------------------------------------------------------- | -------------------- |
| Controller di dominio            | Default                             | Utente di dominio, membro di "*DOMAIN*\Domain Admins"         | Account del computer     |
| Controller di dominio            | Gruppi di dominio A e B               | Utente di dominio, membro di "*DOMAIN*\A", "*DOMAIN*\B"       | Account del computer     |
| Workstation o server membro | Default                             | Utente locale, membro di "*BUILTIN*\Administrators"        | Account del computer     |
| Workstation o server membro | Gruppi locali C e D                | Utente locale, membro di "*COMPUTER*\C" e "*COMPUTER*\D" | Account del computer     |

Quando si esaminano gli eventi del controllo di sicurezza e i log eventi dell'applicazione, si noterà che ogni sessione utente JEA ha un account virtuale univoco. Questo account univoco consente di far risalire le azioni dell'utente in un endpoint JEA all'utente originale che ha eseguito il comando. I nomi degli account virtuali hanno il formato `WinRM Virtual Users\WinRM_VA_<ACCOUNTNUMBER>_<DOMAIN>_<sAMAccountName>`. Se ad esempio l'utente **Alice** del dominio **Contoso** riavvia un servizio in un endpoint JEA, il nome utente associato a eventi di gestione del controllo del servizio sarà `WinRM Virtual Users\WinRM_VA_1_contoso_alice`.

Gli **account del servizio gestito del gruppo (gMSA)** sono utili quando un server membro deve accedere alle risorse di rete nella sessione JEA. Un esempio è il caso in cui l'endpoint JEA viene usato per controllare l'accesso a un'API REST ospitata in un altro computer. È facile scrivere funzioni per chiamare le API REST, ma per l'autenticazione nell'API è necessaria un'identità di rete. L'uso di un account del servizio gestito del gruppo rende possibile il secondo hop, consentendo di mantenere il controllo sui computer che possono usare l'account. Le autorizzazioni valide dei gMSA sono definite dai gruppi di sicurezza (locale o di dominio) a cui appartiene l'account gMSA.

Quando un endpoint JEA è configurato per usare un account gMSA, le azioni di tutti gli utenti JEA vengono registrate come se provenissero dallo stesso account del servizio gestito. L'unico modo per far risalire determinate azioni a un utente specifico è l'identificazione del set di comandi eseguiti in una trascrizione della sessione di PowerShell.

Le **credenziali pass-through** vengono usate quando non si specifica un account **Esegui come**. PowerShell usa le credenziali dell'utente connesso per eseguire comandi nel server remoto. Pertanto è necessario concedere all'utente connesso l'accesso diretto ai gruppi di gestione con privilegi. Questa configurazione **non** è consigliata per JEA. Se l'utente che si connette ha già privilegi di amministratore, può evitare del tutto JEA e gestire il sistema con altri mezzi non vincolati. Per altre informazioni, vedere nella sezione seguente come [JEA non offre protezione dagli amministratori](#jea-doesnt-protect-against-admins).

Gli **account Esegui come standard** consentono di specificare qualsiasi account utente in cui verrà eseguita l'intera sessione di PowerShell. Le configurazioni di sessione che usano account **Esegui come** fissi (con il parametro `-RunAsCredential`) non supportano JEA. Le definizioni del ruolo smettono di funzionare come previsto. Viene assegnato lo stesso ruolo a tutti gli utenti autorizzati ad accedere all'endpoint.

È consigliabile non usare **RunAsCredential** su un endpoint JEA perché rende difficile attribuire azioni a utenti specifici e per la mancanza di supporto per il mapping degli utenti ai ruoli.

## <a name="winrm-endpoint-acl"></a>ACL endpoint di WinRM

Come per i normali endpoint di comunicazione remota di PowerShell, ogni endpoint JEA ha un elenco di controllo di accesso (ACL) separato che controlla gli utenti che possono eseguire l'autenticazione con l'endpoint JEA. Se la configurazione non è corretta, gli utenti attendibili potrebbero non essere in grado di accedere all'endpoint JEA e/o gli utenti non attendibili potrebbero invece ottenere l'accesso. L'ACL WinRM non influisce sul mapping degli utenti ai ruoli JEA. Questo mapping è controllato dal campo **RoleDefinitions** nel file di configurazione sessione usato per registrare l'endpoint.

Per impostazione predefinita, quando un endpoint JEA ha più funzionalità di ruolo, l'elenco di controllo di accesso WinRM è configurato per consentire l'accesso a tutti gli utenti con mapping. Ad esempio, una sessione JEA configurata usando i comandi seguenti concede l'accesso completo a `CONTOSO\JEA_Lev1` e `CONTOSO\JEA_Lev2`.

```powershell
$roles = @{ 'CONTOSO\JEA_Lev1' = 'Lev1Role'; 'CONTOSO\JEA_Lev2' = 'Lev2Role' }
New-PSSessionConfigurationFile -Path '.\jea.pssc' -SessionType RestrictedRemoteServer -RoleDefinitions $roles -RunAsVirtualAccount
Register-PSSessionConfiguration -Path '.\jea.pssc' -Name 'MyJEAEndpoint'
```

È possibile controllare le autorizzazioni utente con il cmdlet [Get-PSSessionConfiguration](/powershell/module/microsoft.powershell.core/get-pssessionconfiguration).

```powershell
Get-PSSessionConfiguration -Name 'MyJEAEndpoint' | Select-Object Permission
```

```Output
Permission
----------
CONTOSO\JEA_Lev1 AccessAllowed
CONTOSO\JEA_Lev2 AccessAllowed
```

Per modificare l'accesso degli utenti, eseguire `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -ShowSecurityDescriptorUI` per un prompt interattivo o `Set-PSSessionConfiguration -Name 'MyJEAEndpoint' -SecurityDescriptorSddl <SDDL string>` per aggiornare le autorizzazioni. Gli utenti devono avere almeno i diritti di *chiamata* per accedere all'endpoint JEA.

È possibile creare un endpoint JEA che non esegue il mapping di un ruolo definito a ogni utente che esegue l'accesso. Questi utenti possono avviare una sessione JEA, ma dispongono solo dell'accesso ai cmdlet predefiniti. È possibile controllare le autorizzazioni degli utenti in un endpoint JEA eseguendo `Get-PSSessionCapability`. Per altre informazioni, vedere [Controllo e creazione di report in JEA](audit-and-report.md).

## <a name="least-privilege-roles"></a>Ruoli con privilegi minimi

Quando si progettano ruoli JEA è importante ricordare che gli account virtuale e del servizio gestito del gruppo eseguiti in background possono avere accesso illimitato alla gestione del computer locale. Le funzionalità di ruolo JEA consentono di limitare i comandi e le applicazioni eseguibili in tale contesto con privilegi.
I ruoli progettati in modo non corretto possono consentire l'esecuzione di comandi pericolosi, che potrebbero permettere a un utente di oltrepassare i limiti JEA o di ottenere l'accesso a informazioni riservate.

Ad esempio, prendere in considerazione la voce relativa alla funzionalità di ruolo seguente:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\*-Process'
}
```

Questa funzionalità di ruolo consente agli utenti di eseguire qualsiasi cmdlet di PowerShell con il termine **Process** dal modulo **Microsoft.PowerShell.Management**. Gli utenti possono avere l'esigenza di accedere a cmdlet specifici, ad esempio `Get-Process` per identificare le applicazioni in esecuzione nel sistema e `Stop-Process` per terminare le applicazioni che non rispondono. Questa voce consente anche il cmdlet `Start-Process`, che può essere usato per avviare un programma arbitrario con autorizzazioni complete di amministratore. Non è necessario che il programma sia installato localmente nel sistema. Un utente connesso può avviare da una condivisione di file un programma che garantisce privilegi di amministratore locale, esegue malware e altro ancora.

Di seguito viene illustrata una versione più sicura della stessa funzionalità di ruolo:

```powershell
@{
    VisibleCmdlets = 'Microsoft.PowerShell.Management\Get-Process', 'Microsoft.PowerShell.Management\Stop-Process'
}
```

Evitare di usare i caratteri jolly nelle funzionalità di ruolo. Assicurarsi di [controllare le autorizzazioni utente effettive](audit-and-report.md#check-effective-rights-for-a-specific-user) con cadenza periodica, per determinare quali comandi sono accessibili all'utente.

## <a name="jea-doesnt-protect-against-admins"></a>JEA non offre protezione dagli amministratori

Uno dei principi fondamentali di JEA è che consente a utenti non amministratori di eseguire alcune attività di amministrazione. JEA non offre protezione dagli utenti che hanno già privilegi di amministratore. Gli utenti che appartengono a **Domain Admins**, al gruppo **Administrators** locale o ad altri gruppi con privilegi elevati possono aggirare le protezioni di JEA con altri mezzi. Ad esempio un utente può accedere con RDP, usare console MMC remote o connettersi agli endpoint di PowerShell non vincolati. Gli amministratori locali del sistema possono anche modificare le configurazioni JEA per consentire l'accesso ad altri utenti o modificare una funzionalità di ruolo per estendere l'ambito delle operazioni eseguibili da un utente nella sessione JEA. È importante valutare le autorizzazioni estese degli utenti JEA, per verificare se esistono altri modi per ottenere l'accesso con privilegi al sistema.

Una pratica comune è usare JEA per una regolare manutenzione quotidiana e avere una soluzione di gestione dell'accesso just-in-time con privilegi, che consente agli utenti di diventare temporaneamente amministratori locali in situazioni di emergenza. In questo modo gli utenti non sono amministratori permanenti del sistema, ma possono ottenere tali diritti se e solo se portano a termine un flusso di lavoro che documenta l'uso di tali autorizzazioni.
