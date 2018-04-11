---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: WinRMSecurity
ms.openlocfilehash: e390a84b6f7a1932afdad84c7b09ce7da2ec5370
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="powershell-remoting-security-considerations"></a>Considerazioni sulla sicurezza della comunicazione remota di PowerShell

La comunicazione remota di PowerShell è il metodo consigliato per gestire i sistemi Windows. La comunicazione remota di PowerShell è abilitata per impostazione predefinita su Windows Server 2012 R2. Questo documento illustra i problemi di sicurezza, i suggerimenti e le procedure consigliate per la comunicazione remota di PowerShell.

## <a name="what-is-powershell-remoting"></a>Informazioni sulla comunicazione remota di PowerShell

La comunicazione remota di PowerShell usa la [Gestione remota Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426.aspx), ovvero l'implementazione Microsoft del protocollo [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf), per consentire agli utenti di eseguire i comandi di PowerShell nei computer remoti. È possibile trovare altre informazioni sull'uso della comunicazione remota di PowerShell in [Esecuzione di comandi remoti](https://technet.microsoft.com/library/dd819505.aspx).

La comunicazione remota di PowerShell non corrisponde all'uso del parametro **ComputerName** di un cmdlet per l'esecuzione in un computer remoto che usa RPC (Remote Procedure Call) come protocollo sottostante.

## <a name="powershell-remoting-default-settings"></a>Impostazioni predefinite della comunicazione remota di PowerShell

La comunicazione remota di PowerShell (e WinRM) esegue l'ascolto delle porte seguenti:

- HTTP: 5985
- HTTPS: 5986

Per impostazione predefinita, la comunicazione remota di PowerShell consente connessioni solo dai membri del gruppo degli amministratori. Le sessioni vengono avviate nel contesto utente, quindi tutti i controlli di accesso del sistema operativo applicati a singoli utenti e gruppi continuano a essere applicati con la comunicazione remota di PowerShell.

Sulle reti private, la regola del firewall di Windows predefinita per la comunicazione remota di PowerShell accetta tutte le connessioni. Sulle reti pubbliche la regola Firewall di Windows predefinita consente le connessioni della comunicazione remota di PowerShell solo dall'interno della stessa subnet. È necessario modificare in modo esplicito tale regola per aprire la comunicazione remota di PowerShell per tutte le connessioni di una rete pubblica.

>**Avviso:** la regola del firewall per le reti pubbliche è progettata per proteggere il computer da tentativi di connessione esterna potenzialmente dannosi. Prestare attenzione quando si rimuove questa regola.

## <a name="process-isolation"></a>Isolamento del processo

La comunicazione remota di PowerShell usa [Gestione remota Windows (WinRM)](https://msdn.microsoft.com/library/windows/desktop/aa384426) per la comunicazione tra computer.
WinRM viene eseguito come servizio dell'account del servizio di rete e genera processi isolati eseguiti come account utente per ospitare le istanze di PowerShell. Un'istanza di PowerShell in esecuzione per un solo utente non ha accesso a un processo che esegue un'istanza di PowerShell con un altro account utente.

## <a name="event-logs-generated-by-powershell-remoting"></a>Registri eventi generati dalla comunicazione remota di Powershell

FireEye ha fornito un ottimo riepilogo dei registri eventi e di altre prove relative alla sicurezza generato dalle sessioni di comunicazione remota di PowerShell, disponibile in [Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf) (Ricerche sugli attacchi a PowerShell).

## <a name="encryption-and-transport-protocols"></a>Protocolli di trasporto e crittografia

È utile valutare la sicurezza di una connessione della comunicazione remota di PowerShell da due prospettive: l'autenticazione iniziale e la comunicazione continua.

Indipendentemente dal protocollo di trasporto usato (HTTP o HTTPS), la comunicazione remota di PowerShell esegue sempre la crittografia su tutte le comunicazioni dopo l'autenticazione iniziale con una chiave simmetrica AES-256 per ogni sessione.

### <a name="initial-authentication"></a>Autenticazione iniziale

L'autenticazione conferma l'identità del client al server e, idealmente, l'identità del server al client.

Quando un client si connette a un server di dominio usando il proprio nome di computer, ad esempio server01 o server01. contoso.com, il protocollo di autenticazione predefinito è [Kerberos](https://msdn.microsoft.com/library/windows/desktop/aa378747.aspx).
Kerberos garantisce l'identità dell'utente e l'identità del server senza inviare credenziali riutilizzabili.

Quando un client si connette a un server di dominio tramite il relativo indirizzo IP o si connette a un server del gruppo di lavoro, l'autenticazione Kerberos non può essere applicata. In questo caso la comunicazione remota di PowerShell si basa sul [protocollo di autenticazione NTLM](https://msdn.microsoft.com/library/windows/desktop/aa378749.aspx), che garantisce l'identità dell'utente senza che sia necessario inviare credenziali delegabili. Per dimostrare l'identità dell'utente, il protocollo NTLM richiede che sia il client che il server calcolino una chiave di sessione dalla password dell'utente senza mai scambiare la stessa password. Il server in genere non conosce la password dell'utente, quindi comunica con il controller di dominio, che conosce la password e calcola la chiave della sessione per il server.

Il protocollo NTLM, tuttavia, garantisce l'identità del server. Come con tutti i protocolli che usano NTLM per l'autenticazione, un utente malintenzionato con accesso all'account computer di un computer aggiunto al dominio può richiamare il controller di dominio per calcolare una chiave di sessione NTLM e quindi rappresentare il server.

L'autenticazione basata su NTLM è disabilitata per impostazione predefinita, ma è ammessa una configurazione di SSL nel server di destinazione o la configurazione dell'impostazione TrustedHosts di WinRM.

#### <a name="using-ssl-certificates-to-validate-server-identity-during-ntlm-based-connections"></a>Uso di certificati SSL per convalidare l'identità del server durante le connessioni basate su NTLM

Poiché il protocollo di autenticazione NTLM non è in grado di garantire l'identità del server di destinazione, a meno che non conosca già la password, è possibile configurare i server di destinazione per l'uso di SSL per la comunicazione remota di PowerShell. L'assegnazione di un certificato SSL al server di destinazione, se emesso da un'autorità di certificazione che anche il client considera attendibile, consente l'autenticazione basata su NTLM, che garantisce l'identità sia dell'utente che del server.

#### <a name="ignoring-ntlm-based-server-identity-errors"></a>Ignorare gli errori di identità del server basata su NTLM

Se la distribuzione di un certificato SSL a un server per le connessioni NTLM non è applicabile, è possibile eliminare gli errori di identità risultanti aggiungendo il server all'elenco **TrustedHosts** di WinRM. Si noti che l'aggiunta del nome di un server all'elenco TrustedHosts non deve essere considerata una dichiarazione di attendibilità degli stessi host, poiché il protocollo di autenticazione NTLM non è in grado di garantire che venga effettivamente eseguita la connessione all'host a cui si intende connettersi.
In alternativa, considerare l'impostazione di TrustedHosts come elenco degli host per i quali eliminare l'errore generato dall'impossibilità di verificare l'identità del server.


### <a name="ongoing-communication"></a>Comunicazione continua

Dopo aver completato l'autenticazione iniziale, il [Protocollo di comunicazione remota di PowerShell](https://msdn.microsoft.com/en-us/library/dd357801.aspx) esegue la crittografia di tutte le comunicazioni in corso con una chiave simmetrica AES-256 per ogni sessione.


## <a name="making-the-second-hop"></a>Esecuzione del secondo hop

Per impostazione predefinita, la comunicazione remota di PowerShell usa Kerberos (se disponibile) o NTLM per l'autenticazione. Entrambi questi protocolli eseguono l'autenticazione al computer remoto senza inviare le credenziali.
Si tratta del modo più sicuro per eseguire l'autenticazione. Tuttavia, dal momento che il computer remoto non dispone delle credenziali dell'utente, non può accedere ad altri computer e servizi per conto dell'utente.
Ciò è noto come "problema del secondo hop".

Ci sono diversi modi per evitare questo problema. Per le descrizioni di questi metodi e dei vantaggi e svantaggi di ogni metodo, vedere [Creazione del secondo hop nella comunicazione remota di PowerShell](PS-remoting-second-hop.md).