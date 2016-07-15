---
title: WinRMSecurity
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 67ef350559f9b3d17232f3c93d67634b3e939c60
ms.openlocfilehash: b1addddd50368fadcbb2581673d3ebc7cad8e32a

---

# Considerazioni sulla sicurezza della comunicazione remota di PowerShell

La comunicazione remota di PowerShell è il metodo consigliato per gestire i sistemi Windows. La comunicazione remota di PowerShell è abilitata per impostazione predefinita su Windows Server 2012 R2. Questo documento illustra i problemi di sicurezza, i suggerimenti e le procedure consigliate per la comunicazione remota di PowerShell.

## Informazioni sulla comunicazione remota di PowerShell

La comunicazione remota di PowerShell usa la [Gestione remota Windows (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426.aspx), ovvero l'implementazione Microsoft del protocollo [Web Services for Management (WS-Management)](http://www.dmtf.org/sites/default/files/standards/documents/DSP0226_1.2.0.pdf), per consentire agli utenti di eseguire i comandi di PowerShell nei computer remoti. È possibile trovare altre informazioni sull'uso della comunicazione remota di PowerShell in [Esecuzione di comandi remoti](https://technet.microsoft.com/en-us/library/dd819505.aspx).

La comunicazione remota di PowerShell non corrisponde all'uso del parametro **ComputerName** di un cmdlet per l'esecuzione in un computer remoto che usa RPC (Remote Procedure Call) come protocollo sottostante.

##  Impostazioni predefinite della comunicazione remota di PowerShell

La comunicazione remota di PowerShell (e WinRM) esegue l'ascolto delle porte seguenti:

- HTTP: 5985
- HTTPS: 5986

Per impostazione predefinita, la comunicazione remota di PowerShell consente connessioni solo dai membri del gruppo degli amministratori. Le sessioni vengono avviate nel contesto utente, quindi tutti i controlli di accesso del sistema operativo applicati a singoli utenti e gruppi continuano a essere applicati con la comunicazione remota di PowerShell.

Sulle reti private, la regola del firewall di Windows predefinita per la comunicazione remota di PowerShell accetta tutte le connessioni. Sulle reti pubbliche la regola Firewall di Windows predefinita consente le connessioni della comunicazione remota di PowerShell solo dall'interno della stessa subnet. È necessario modificare in modo esplicito tale regola per aprire la comunicazione remota di PowerShell per tutte le connessioni di una rete pubblica.

>**Avviso:** la regola del firewall per le reti pubbliche è progettata per proteggere il computer da tentativi di connessione esterna potenzialmente dannosi. Prestare attenzione quando si rimuove questa regola.

## Isolamento del processo

La comunicazione remota di PowerShell usa [Gestione remota Windows (WinRM)](https://msdn.microsoft.com/en-us/library/windows/desktop/aa384426) per la comunicazione tra computer. WinRM viene eseguito come servizio dell'account del servizio di rete e genera processi isolati eseguiti come account utente per ospitare le istanze di PowerShell. Un'istanza di PowerShell in esecuzione per un solo utente non ha accesso a un processo che esegue un'istanza di PowerShell con un altro account utente.

## Registri eventi generati dalla comunicazione remota di Powershell

FireEye ha fornito un ottimo riepilogo dei registri eventi e di altre prove relative alla protezione generato dalle sessioni di comunicazione remota di PowerShell, disponibile in  
[Investigating PowerShell Attacks](https://www.fireeye.com/content/dam/fireeye-www/global/en/solutions/pdfs/wp-lazanciyan-investigating-powershell-attacks.pdf) (Ricerche sugli attacchi a PowerShell.

## Protocolli di trasporto e crittografia

È utile valutare la sicurezza di una connessione della comunicazione remota di PowerShell da due prospettive: l'autenticazione iniziale e la comunicazione continua. 

Indipendentemente dal protocollo di trasporto usato (HTTP o HTTPS), la comunicazione remota di PowerShell esegue sempre la crittografia su tutte le comunicazioni dopo l'autenticazione iniziale con una chiave simmetrica AES-256 per ogni sessione.
    
### Autenticazione iniziale

L'autenticazione conferma l'identità del client al server e, idealmente, l'identità del server al client.
    
Quando un client si connette a un server di dominio usando il proprio nome di computer, ad esempio server01 o server01. contoso.com, il protocollo di autenticazione predefinito è [Kerberos](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378747.aspx).
Kerberos garantisce l'identità dell'utente e l'identità del server senza inviare credenziali riutilizzabili.

Quando un client si connette a un server di dominio tramite il relativo indirizzo IP o si connette a un server del gruppo di lavoro, l'autenticazione Kerberos non può essere applicata. In questo caso la comunicazione remota di PowerShell si basa sul [protocollo di autenticazione NTLM](https://msdn.microsoft.com/en-us/library/windows/desktop/aa378749.aspx), che garantisce l'identità dell'utente senza che sia necessario inviare credenziali delegabili. Per dimostrare l'identità dell'utente, il protocollo NTLM richiede che sia il client che il server calcolino una chiave di sessione dalla password dell'utente senza mai scambiare la stessa password. Il server in genere non conosce la password dell'utente, quindi comunica con il controller di dominio, che conosce la password e calcola la chiave della sessione per il server. 
      
Il protocollo NTLM, tuttavia, garantisce l'identità del server. Come con tutti i protocolli che usano NTLM per l'autenticazione, un utente malintenzionato con accesso all'account computer di un computer aggiunto al dominio può richiamare il controller di dominio per calcolare una chiave di sessione NTLM e quindi rappresentare il server.

L'autenticazione basata su NTLM è disabilitata per impostazione predefinita, ma è ammessa una configurazione di SSL nel server di destinazione o la configurazione dell'impostazione TrustedHosts di WinRM.
    
#### Uso di certificati SSL per convalidare l'identità del server durante le connessioni basate su NTLM

Poiché il protocollo di autenticazione NTLM non è in grado di garantire l'identità del server di destinazione, a meno che non conosca già la password, è possibile configurare i server di destinazione per l'uso di SSL per la comunicazione remota di PowerShell. L'assegnazione di un certificato SSL al server di destinazione, se emesso da un'autorità di certificazione che anche il client considera attendibile, consente l'autenticazione basata su NTLM, che garantisce l'identità sia dell'utente che del server.
    
#### Ignorare gli errori di identità del server basata su NTLM
      
Se la distribuzione di un certificato SSL a un server per le connessioni NTLM non è applicabile, è possibile eliminare gli errori di identità risultanti aggiungendo il server all'elenco **TrustedHosts** di WinRM. Si noti che l'aggiunta del nome di un server all'elenco TrustedHosts non deve essere considerata una dichiarazione di attendibilità degli stessi host, poiché il protocollo di autenticazione NTLM non è in grado di garantire che venga effettivamente eseguita la connessione all'host a cui si intende connettersi.
In alternativa, considerare l'impostazione di TrustedHosts come elenco degli host per i quali eliminare l'errore generato dall'impossibilità di verificare l'identità del server.
    
    
### Comunicazione continua

Dopo aver completato l'autenticazione iniziale, il [Protocollo di comunicazione remota di PowerShell](https://msdn.microsoft.com/en-us/library/dd357801.aspx) esegue la crittografia di tutte le comunicazioni in corso con una chiave simmetrica AES-256 per ogni sessione.  


## Esecuzione del secondo hop

Per impostazione predefinita, la comunicazione remota di PowerShell usa Kerberos (se disponibile) o NTLM per l'autenticazione. Entrambi questi protocolli eseguono l'autenticazione al computer remoto senza inviare le credenziali.
Si tratta del modo più sicuro per eseguire l'autenticazione. Tuttavia, dal momento che il computer remoto non dispone delle credenziali dell'utente, non può accedere ad altri computer e servizi per conto dell'utente. Questo problema è conosciuto come "Doppio Hop".

Esistono diversi modi per evitare questo problema:

### Delega vincolata Kerberos

Per i server a elevata attendibilità, è possibile abilitare la [delega vincolata Kerberos](https://technet.microsoft.com/en-us/library/cc995228.aspx). In questo modo il server remoto è in grado di rappresentare l'utente autenticato a un elenco specificato di computer e servizi.

### Attendibilità tra computer remoti

Se si considerano attendibili gli utenti connessi in remoto a *Server1* alle risorse di *Server2*, è possibile concedere esplicitamente l'accesso a *Server1* per queste risorse.

### Usare credenziali esplicite per l'accesso alle risorse remote

È possibile passare le credenziali in modo esplicito a una risorsa remota tramite il parametro **Credential** di un cmdlet. Ad esempio:

```powershell
$myCredential = Get-Credential
New-PSDrive -Name Tools \\Server2\Shared\Tools -Credential $myCredential 
```

### CredSSP

È possibile usare il protocollo [CredSSP (Credential Security Support Provider)](https://msdn.microsoft.com/en-us/library/windows/desktop/bb931352.aspx) per l'autenticazione, specificando "CredSSP" come valore del parametro `Authentication` di una chiamata al cmdlet [New-PSSession](https://technet.microsoft.com/en-us/library/hh849717.aspx). CredSSP passa al server le credenziali in testo normale, esponendo l'utente ad attacchi con furto di credenziali. Se il computer remoto viene compromesso, l'utente malintenzionato ha accesso alle credenziali dell'utente. Per impostazione predefinita, CredSSP è disabilitato sia nei computer client che nei computer server. È opportuno abilitare CredSSP solo negli ambienti più attendibili. Ad esempio, quando un amministratore di dominio si connette a un controller di dominio perché il controller di dominio è estremamente attendibile.

Per altre informazioni sui problemi di sicurezza relativi all'uso di CredSSP per la comunicazione remota di PowerShell, vedere [Accidental Sabotage: Beware of CredSSP](http://www.powershellmagazine.com/2014/03/06/accidental-sabotage-beware-of-credssp) (Sabotaggio accidentale: attenzione a CredSSP).

Per altre informazioni sugli attacchi con furto di credenziali, vedere [Mitigating Pass-the-Hash (PtH) Attacks and Other Credential Theft](https://www.microsoft.com/en-us/download/details.aspx?id=36036) (Mitigazione degli attacchi Pass-the-Hash (PtH) e di altre tecniche per il furto delle credenziali).











<!--HONumber=Jul16_HO1-->


