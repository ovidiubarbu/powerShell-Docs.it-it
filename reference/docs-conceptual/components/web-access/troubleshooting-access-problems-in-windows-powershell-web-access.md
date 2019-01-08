---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: risoluzione dei problemi di accesso in accesso web windows powershell
ms.openlocfilehash: c9b98c7a1685679eb88b718de0351154cb84e92e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401411"
---
# <a name="troubleshooting-access-problems-in-windows-powershell-web-access"></a>Risoluzione dei problemi di accesso in Accesso Web Windows PowerShell

Aggiornamento: 24 giugno 2013 (revisione 23 agosto 2017)

Si applica a: Windows Server 2012 R2, Windows Server 2012

Le sezioni seguenti illustrano alcuni problemi comuni che possono verificarsi quando si prova a connettersi a un computer remoto con Accesso Web Windows PowerShell e includono alcuni suggerimenti per la risoluzione di tali problemi.

## <a name="sign-in-failure"></a>Errore di accesso

Il problema può essere dovuto a uno dei motivi seguenti.

- Non esiste una regola di autorizzazione che consenta all'utente di accedere al computer o a una configurazione di sessione specifica sul computer remoto.

  La sicurezza di Accesso Web Windows PowerShell è restrittiva, quindi è necessario consentire esplicitamente agli utenti l'accesso ai computer remoti, usando le regole di autorizzazione.

  Per altre informazioni sulla creazione delle regole di autorizzazione, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

- L'utente non è autorizzato ad accedere al computer di destinazione. Tale autorizzazione è determinata dagli elenchi di controllo di accesso (ACL).

  Per altre informazioni, vedere [Connessione ad Accesso Web Windows PowerShell](use-the-web-based-windows-powershell-console.md#signing-in-to-windows-powershell-web-access) o il blog del team di Windows PowerShell.

- La gestione remota di Windows PowerShell potrebbe non essere abilitata nel computer di destinazione.

  Verificare che tale funzione sia abilitata nel computer a cui l'utente sta tentando di connettersi.

  Per altre informazioni, vedere [How to Configure Your Computer for Remoting](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote_requirements#how-to-configure-your-computer-for-remoting) (Come configurare il computer per la comunicazione remota).

## <a name="internal-server-error"></a>Errore interno del server

Quando gli utenti provano a connettersi ad Accesso Web Windows PowerShell da una finestra di Internet Explorer, viene visualizzata una pagina di **Errore interno del server** oppure *Internet Explorer* smette di rispondere.

Si tratta di un problema specifico di Internet Explorer.

### <a name="possible-cause"></a>Possibile causa

Questo problema può verificarsi per gli utenti che effettuano l'accesso con un nome di dominio contenente caratteri cinesi, oppure se il nome del server gateway contiene uno o più caratteri cinesi.

#### <a name="workaround"></a>Soluzione alternativa

1. [Installare ed eseguire Internet Explorer 10](https://ie.microsoft.com/testdrive/info/downloads/Default.html)
1. Modificare la **modalità documento** di Internet Explorer impostando gli standard *IE10*.
   1. Premere **F12** per aprire la console di Strumenti di sviluppo
   1. In Internet Explorer 10 fare clic su **Modalità browser** e selezionare *Internet Explorer 10*.
   1. Fare clic su **Modalità documento** e selezionare gli standard *IE10*.
   1. Premere di nuovo **F12** per chiudere la console degli strumenti di sviluppo.
1. Disabilitare la configurazione automatica in Internet Explorer 10.
   1. Scegliere **Opzioni Internet**dal menu **Strumenti**.
   1. Nella finestra di dialogo **Opzioni Internet** passare alla scheda **Connessioni** e fare clic su **Impostazioni LAN**.
   1. Deselezionare la casella di controllo **Rileva automaticamente impostazioni**. Fare clic su **OK**, quindi fare di nuovo clic su **OK** per chiudere la finestra di dialogo *Opzioni Internet*.

## <a name="cannot-connect-to-a-remote-workgroup-computer"></a>Non è possibile connettersi a un computer remoto del gruppo di lavoro

Se il computer di destinazione fa parte di un gruppo di lavoro, usare la sintassi seguente per specificare il nome utente e accedere al computer: `<workgroup_name>\<user_name>`

## <a name="cannot-find-web-server-iis-management-tools-even-though-the-role-was-installed"></a>Non è possibile trovare gli strumenti di gestione del server Web (IIS) anche se il ruolo corrispondente è stato installato

Se Accesso Web Windows PowerShell viene installato tramite il cmdlet `Install-WindowsFeature`, gli strumenti di gestione non vengono installati, a meno che non si aggiunga il parametro `-IncludeManagementTools` al cmdlet.

Per un esempio, vedere [Per installare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell](install-and-use-windows-powershell-web-access.md#to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets).

Per aggiungere la console Gestione IIS e altri strumenti di gestione di IIS necessari, selezionarli in una sessione di **Aggiunta guidata ruoli e funzionalità** che ha come destinazione il server gateway.
L'Aggiunta guidata ruoli e funzionalità viene aperta in Server Manager.

## <a name="windows-powershell-web-access-website-is-not-accessible"></a>Il sito Web di Accesso Web Windows PowerShell non è accessibile

Se in Internet Explorer è abilitata la Sicurezza avanzata, è possibile aggiungere il sito Web di Accesso Web Windows PowerShell all'elenco dei siti attendibili.

Oppure è possibile disabilitare la Sicurezza avanzata di Internet Explorer, anche se, visti i rischi di sicurezza, non è un approccio molto consigliato.
È possibile disabilitare la Sicurezza avanzata di Internet Explorer nel riquadro Proprietà della pagina Server locale in Server Manager.

## <a name="an-authorization-failure-occurred-verify-that-you-are-authorized-to-connect-to-the-destination-computer"></a>Errore di autorizzazione. Verificare di essere autorizzati a connettersi al computer di destinazione.

Il messaggio di errore precedente viene visualizzato quando si prova a stabilire una connessione e il server gateway è il computer di destinazione ed è anche incluso in un gruppo di lavoro.

Se il server gateway è anche il server di destinazione, ed è incluso in un gruppo di lavoro, specificare il nome dell'utente, il nome del computer e il nome del gruppo di utenti,
evitando di usare solo un punto (.) per rappresentare il nome del computer.

### <a name="scenarios-and-proper-values"></a>Scenari e i valori validi

#### <a name="all-cases"></a>Tutti i casi

Parametro | Value
-- | --
UserName | Server\_name\\user\_name<br/>Localhost\\user\_name<br/>.\\user\_name
UserGroup | Server\_name\\user\_group<br/>Localhost\\user\_group<br/>.\\user\_group
ComputerGroup | Server\_name\\computer\_group<br/>Localhost\\computer\_group<br/>.\\computer\_group

#### <a name="gateway-server-is-in-a-domain"></a>Il server gateway è in un dominio

Parametro | Value
-- | --
ComputerName | Nome completo del server gateway o Localhost

#### <a name="gateway-server-is-in-a-workgroup"></a>Il server gateway è in un gruppo di lavoro

Parametro | Value
-- | --
ComputerName | Nome server

### <a name="gateway-credentials"></a>Credenziali del gateway

Effettuare l'accesso specificando il server gateway come computer di destinazione e utilizzando credenziali formattate in uno dei modi seguenti.

- Server\_name\\user\_name
- Localhost\\user\_name
- .\\user\_name

## <a name="a-security-identifier-sid-is-displayed-in-an-authorization-rule"></a>In una regola di autorizzazione viene visualizzato un ID di sicurezza (SID)

In una regola di autorizzazione, al posto della sintassi user\_name/computer\_name viene visualizzato un ID di sicurezza (SID).

La regola non è più valida o la query in Servizi di dominio Active Directory non è riuscita.
In genere, una regola di autorizzazione non risulta valida nel caso in cui il server gateway che in precedenza apparteneva a un gruppo di lavoro venga poi aggiunto a un dominio

## <a name="cannot-sign-in-with-rule-as-an-ipv6-address-with-a-domain"></a>Impossibile accedere usando la regola con indirizzo IPv6 di dominio

Non è possibile accedere a un computer di destinazione che nelle regole di autorizzazione è stato specificato sotto forma di indirizzo IPv6 di dominio

Le regole di autorizzazione non supportano gli indirizzi IPv6 nel formato dei nomi di dominio.

Per specificare un computer di destinazione tramite un indirizzo IPv6, nella regola di autorizzazione utilizzare l'indirizzo IPv6 originale, che contiene due punti (:).
Sia i nomi di dominio che gli indirizzi IPv6 in formato numerico, ovvero con i due punti (:) sono supportati come nome del computer di destinazione nella pagina di accesso di Accesso Web Windows PowerShell, ma non nelle regole di autorizzazione.

Per altre informazioni sugli indirizzi IPv6, vedere l'articolo [Funzionamento di IPv6](https://technet.microsoft.com/library/cc781672(v=ws.10).aspx).

## <a name="see-also"></a>Vedere anche

- [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
- [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
- [about_Remote_Requirements](https://docs.microsoft.com/en-us/powershell/module/microsoft.powershell.core/about/about_remote_requirements)