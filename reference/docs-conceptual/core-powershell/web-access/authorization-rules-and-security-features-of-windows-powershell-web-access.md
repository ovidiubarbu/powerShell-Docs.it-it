---
ms.date: 06/27/2017
keywords: powershell,cmdlet
title: Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell
ms.openlocfilehash: 0e765ae90661a054ca9bae71d0f6d449cccb185d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

Accesso Web di Windows PowerShell in Windows Server 2012 R2 e Windows Server 2012 prevede un modello di sicurezza restrittivo.
È necessario che agli utenti venga concesso l'accesso in modo esplicito prima che possano accedere al gateway Accesso Web Windows PowerShell e usare la console di Windows PowerShell basata sul Web.

## <a name="configuring-authorization-rules-and-site-security"></a>Configurazione delle regole di autorizzazione e della sicurezza del sito

Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso.
Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente.
Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione.
Vedere [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlet di Accesso Web Windows PowerShell).

Gli amministratori possono definire da 0 a *n* regole di autenticazione per Accesso Web Windows PowerShell.
Poiché la sicurezza predefinita è di tipo restrittivo, l'assenza di regole di autenticazione implica che nessun utente può accedere ad alcun elemento.

I cmdlet [Add-PswaAuthorizationRule](cmdlets/add-pswaauthorizationrule.md) e [Test-PswaAuthorizationRule](cmdlets/test-pswaauthorizationrule.md) in Windows Server 2012 R2 includono ora un parametro Credential che consente di aggiungere e testare le regole di autorizzazione di Accesso Web Windows PowerShell da un computer remoto o in una sessione di Accesso Web Windows PowerShell attiva.
Come con gli altri cmdlet di Windows PowerShell che includono un parametro Credential, è possibile specificare un oggetto PSCredential come valore del parametro.
Per creare un oggetto PSCredential che contiene le credenziali da passare a un computer remoto, eseguire il cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).

Le regole di autenticazione Accesso Web Windows PowerShell sono costituite da elenchi di operazioni consentite.
Ogni regola definisce una connessione consentita fra utenti, computer di destinazione e specifiche [configurazioni di sessione](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) di Windows PowerShell, denominate anche endpoint o _spazi di esecuzione_, nei computer di destinazione specificati.
Per una spiegazione degli **spazi di esecuzione** vedere [Beginning Use of PowerShell Runspaces](https://blogs.technet.microsoft.com/heyscriptingguy/2015/11/26/beginning-use-of-powershell-runspaces-part-1/) (Uso iniziale degli spazi di esecuzione di PowerShell)

> **Nota sulla sicurezza**
>
> Affinché un utente possa ottenere l'accesso, è sufficiente che una sola regola risulti vera.
Se dalla console basata sul Web si consente a un utente di accedere a un computer, con accesso al linguaggio completo o solo ai cmdlet di Windows PowerShell per la gestione remota, tale utente potrà accedere (o passare) ad altri computer connessi al primo computer di destinazione.
Il modo più sicuro per configurare Accesso Web Windows PowerShell consiste nel limitare l'accesso degli utenti alle sole configurazioni di sessione vincolate che consentono di eseguire specifiche attività che devono essere in genere eseguite in modalità remota.

I cmdlet illustrati in [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlet di Accesso Web Windows PowerShell) consentono di creare un set di regole di accesso, che viene usato per autorizzare un utente nel gateway di Accesso Web Windows PowerShell.
Le regole sono diverse dagli elenchi di controllo di accesso (ACL) nei computer di destinazione e forniscono un livello di sicurezza aggiuntivo per l'accesso Web.
Ulteriori informazioni sulla sicurezza verranno fornite nelle sezioni successive.

Se un utente non supera tali livelli di sicurezza, riceve un messaggio di "accesso negato" nella finestra del browser.
Anche se i dettagli relativi alla sicurezza vengono registrati nel server gateway, agli utenti finali non viene comunicato il numero dei livelli di sicurezza superati o il livello a cui si è verificato l'errore di accesso o autenticazione.

Per altre informazioni sulla configurazione delle regole di autorizzazione, vedere la sezione [Configurazione delle regole di autorizzazione](#configuring-authorization-rules-and-site-security) in questo argomento.

### <a name="security"></a>Sicurezza

Il modello di sicurezza di Accesso Web Windows PowerShell prevede quattro livelli fra l'utente finale della console basata sul Web e un computer di destinazione.
Gli amministratori di Accesso Web Windows PowerShell possono aggiungere ulteriori livelli di sicurezza eseguendo alcune operazioni di configurazione nella console Gestione IIS.
Per altre informazioni sulla protezione dei siti Web nella console Gestione IIS, vedere [Configurare la sicurezza del server Web (IIS 7)](https://technet.microsoft.com/library/cc731278).
Per altre informazioni sulle procedure consigliate per IIS e su come prevenire gli attacchi DoS (Denial of Service), vedere le [procedure consigliate per la prevenzione degli attacchi DoS (Denial of Service)](https://technet.microsoft.com/library/cc750213).
L'amministratore può anche acquistare e installare un prodotto di autenticazione commerciale.

I quattro livelli di sicurezza fra l'utente finale e il computer di destinazione sono illustrati nella tabella seguente.

|Livello|Livello|
|-|-|
|1|[funzionalità per la sicurezza del server Web IIS](#iis-web-server-security-features)|
|2|[autenticazione del gateway basata su moduli di Accesso Web Windows PowerShell](#windows-powershell-web-access-forms-based-gateway-authentication)|
|3|[regole di autorizzazione di Accesso Web Windows PowerShell](#windows-powershell-web-access-authorization-rules)|
|4|[regole di autenticazione e autorizzazione del computer di destinazione](#target-authentication-and-authorization-rules)|

Informazioni dettagliate su ogni livello sono disponibili nelle sezioni seguenti:

#### <a name="iis-web-server-security-features"></a>Funzionalità per la sicurezza del server Web IIS

Gli utenti di Accesso Web Windows PowerShell devono sempre fornire nome utente e password per autenticare l'account nel gateway.
Gli amministratori di Accesso Web Windows PowerShell possono tuttavia decidere di attivare o disattivare l'autenticazione del certificato client (vedere [Installare e usare Accesso Web Windows PowerShell](install-and-use-windows-powershell-web-access.md)) per testare un certificato e, successivamente, configurare un certificato originale.

La funzionalità facoltativa per i certificati client richiede che, oltre al nome utente e alla password, gli utenti forniscano anche un certificato client valido, nell'ambito della configurazione del server Web (IIS).
Se il livello relativo al certificato client è abilitato, la pagina di accesso di Accesso Web Windows PowerShell richiede agli utenti di fornire un certificato valido prima di valutare le relative credenziali.
L'autenticazione tramite certificati client controlla automaticamente il certificato client.
Se non viene trovato un certificato valido, Accesso Web Windows PowerShell informa l'utente in modo che possa fornirne uno.
Se viene trovato un certificato valido, Accesso Web Windows PowerShell apre la pagina di accesso per consentire agli utenti di immettere nome utente e password.

Questo è un esempio delle impostazioni di sicurezza aggiuntive offerte dal server Web IIS.
Per informazioni sulle altre funzionalità di sicurezza di IIS, vedere [Configure Web Server Security (IIS 7)](https://technet.microsoft.com/library/cc731278) (Configurare la sicurezza del server Web (IIS 7)

#### <a name="windows-powershell-web-access-forms-based-gateway-authentication"></a>Autenticazione del gateway basata su moduli di Accesso Web Windows PowerShell

La pagina di accesso di Accesso Web Windows PowerShell richiede un set di credenziali (nome utente e password) e offre agli utenti la possibilità di specificare credenziali diverse per il computer di destinazione.
Se l'utente non fornisce altre credenziali, per la connessione al computer di destinazione vengono utilizzati il nome utente e la password principali specificati per la connessione al gateway.

Le credenziali richieste vengono autenticate nel gateway di Accesso Web Windows PowerShell
e devono corrispondere ad account utente validi nel server gateway locale di Accesso Web Windows PowerShell o in Active Directory®.

#### <a name="windows-powershell-web-access-authorization-rules"></a>Regole di autorizzazione di Accesso Web Windows PowerShell

Dopo l'autenticazione dell'utente nel gateway, Accesso Web Windows PowerShell controlla le regole di autorizzazione per verificare se l'utente ha accesso al computer di destinazione richiesto.
Se l'autorizzazione ha esito positivo, le credenziali dell'utente vengono passate al computer di destinazione.

Tali regole vengono valutate solo dopo l'autenticazione dell'utente nel gateway e prima dell'autenticazione nel computer di destinazione.

#### <a name="target-authentication-and-authorization-rules"></a>Autenticazione e regole di autorizzazione del computer di destinazione

L'ultimo livello di sicurezza di Accesso Web Windows PowerShell è costituito dalla configurazione di protezione del computer di destinazione.
Gli utenti devono avere i diritti di accesso appropriati, configurati sia nel computer di destinazione che nelle regole di autorizzazione di Accesso Web Windows PowerShell, per eseguire una console Windows PowerShell basata sul Web che può operare sul computer di destinazione con Accesso Web Windows PowerShell.

Questo livello offre un meccanismo di sicurezza uguale a quello che valuta i tentativi di connessione quando un utente crea una sessione remota di Windows PowerShell per un computer di destinazione direttamente da Windows PowerShell, eseguendo il cmdlet [Enter-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/Enter-PSSession) o [New-PSSession](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/new-pssession).

Per impostazione predefinita, Accesso Web Windows PowerShell usa il nome utente e la password principali per eseguire l'autenticazione sia nel gateway che nel computer di destinazione.
La sezione **Impostazioni di connessione facoltative** della pagina di accesso basata sul Web offre agli utenti la possibilità di specificare credenziali diverse per il computer di destinazione, se sono necessarie.
Se l'utente non specifica altre credenziali, per la connessione al computer di destinazione vengono usati il nome utente e la password principali specificati per la connessione al gateway.

Le regole di autorizzazione possono essere utilizzate per consentire agli utenti di accedere a una configurazione di sessione specifica.
È possibile creare configurazioni di sessione o _spazi di esecuzione con restrizioni_ per Accesso Web Windows PowerShell e consentire a utenti specifici di connettersi solo a configurazioni di sessione specifiche, quando accedono ad Accesso Web Windows PowerShell.
È possibile usare gli elenchi di controllo di accesso (ACL) per identificare gli utenti che hanno accesso a endpoint specifici e limitare ulteriormente l'accesso all'endpoint per un gruppo di utenti specifico, usando le regole di autorizzazione descritte in questa sezione.
Per altre informazioni sugli spazi di esecuzione con restrizioni, vedere [Creating a constrained runspace](https://msdn.microsoft.com/en-us/library/dn614668) (Creazione di uno spazio di esecuzione con restrizioni).

### <a name="configuring-authorization-rules"></a>Configurazione delle regole di autorizzazione

In genere gli amministratori vogliono applicare agli utenti di Accesso Web Windows PowerShell le stesse regole di autorizzazione già definite nell'ambiente per la gestione remota di Windows PowerShell.
La prima procedura di questa sezione illustra come aggiungere una regola di autorizzazione sicura che consente l'accesso a un singolo utente per la gestione di un unico computer con una singola configurazione di sessione.
La seconda procedura illustra come rimuovere una regola di autorizzazione non più necessaria.

Se si prevede di usare configurazioni di sessione personalizzate per consentire a utenti specifici di lavorare esclusivamente in spazi di esecuzione di Accesso Web Windows PowerShell con restrizioni, creare le configurazioni di sessione personalizzate prima di aggiungere le regole di autorizzazione che vi fanno riferimento.
Non è possibile usare i cmdlet di Accesso Web Windows PowerShell per creare configurazioni di sessione personalizzate.
Per altre informazioni sulla creazione di configurazioni di sessione personalizzate, vedere [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

L'unico carattere jolly supportato dai cmdlet di Accesso Web Windows PowerShell è l'asterisco ( \* ).
I caratteri jolly all'interno delle stringhe non sono supportati. Utilizzare un singolo asterisco per proprietà (utenti, computer o configurazioni di sessione).

> **Nota**
>
> Per altre modalità di uso della regole di autorizzazione per la concessione dell'accesso agli utenti e la protezione dell'ambiente di Accesso Web Windows PowerShell, vedere [Altri scenari di esempio per le regole di autorizzazione](#other-authorization-rule-scenario-examples) in questo argomento.

#### <a name="to-add-a-restrictive-authorization-rule"></a>Per aggiungere una regola di autorizzazione restrittiva

1. Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

    - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    - Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e scegliere **Esegui come amministratore**.

2. **Passaggio facoltativo** Per limitare l'accesso agli utenti tramite le configurazioni di sessione:

    Verificare che le configurazioni di sessione da usare esistano già nelle regole.
Se non sono ancora state create, usare le istruzioni per la creazione di configurazioni di sessione disponibili in [about_Session_Configuration_Files](https://msdn.microsoft.com/en-us/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configuration_files).

3. Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente usando una configurazione di sessione specifica con ambito limitato alle esigenze tipiche dell'utente in termini di script e cmdlet. Digitare il comando seguente e quindi premere **INVIO**.

```powershell
Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>
```

  - Nell'esempio seguente, a un utente di nome _JSmith_ nel dominio _Contoso_ viene consentito l'accesso per la gestione del computer _Contoso_214_, con una configurazione di sessione denominata _NewAdminsOnly_.

```powershell
Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly
```

4. Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;. Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.

#### <a name="to-remove-an-authorization-rule"></a>Per rimuovere una regola di autorizzazione

1. Se non è ancora stata aperta una sessione di Windows PowerShell, vedere il passaggio 1 della procedura [Per aggiungere una regola di autorizzazione restrittiva](#to-add-a-restrictive-authorization-rule) in questa sezione.

2. Digitare il comando seguente e premere **INVIO**. *ID regola* rappresenta l'ID univoco della regola che si vuole rimuovere.

```powershell
Remove-PswaAuthorizationRule -ID <rule ID>
```

In alternativa, se non si conosce l'ID ma si conosce il nome descrittivo della regola da rimuovere, è possibile ottenere il nome della regola e inviarlo tramite pipe al cmdlet `Remove-PswaAuthorizationRule` per rimuovere la regola, come illustrato nell'esempio seguente: `Get-PswaAuthorizationRule -RuleName <rule-name> | Remove-PswaAuthorizationRule`.

>**Nota**:
>
>Non viene richiesto se si vuole eliminare la regola di autorizzazione specificata, perché l'eliminazione avviene infatti quando si premere **INVIO**. Verificare con attenzione la regola di autorizzazione da rimuovere prima di eseguire il cmdlet `Remove-PswaAuthorizationRule`.

#### <a name="other-authorization-rule-scenario-examples"></a>Altri scenari di esempio per le regole di autorizzazione

Per ogni sessione di Windows PowerShell viene usata una configurazione di sessione. Se non è specificata, Windows PowerShell usa la configurazione di sessione predefinita incorporata in Windows PowerShell, denominata Microsoft.PowerShell, che include tutti i cmdlet disponibili in un computer. Gli amministratori possono limitare l'accesso a tutti i computer definendo una configurazione di sessione basata su uno spazio di esecuzione con restrizioni, ovvero un insieme limitato di attività e cmdlet che possono essere eseguiti dagli utenti finali. Se si consente a un utente di accedere a un computer, con accesso al linguaggio completo o solo ai cmdlet di Windows PowerShell per la gestione remota, tale utente potrà connettersi agli altri computer connessi al primo. Definendo uno spazio di esecuzione con restrizioni si impedisce agli utenti di accedere ad altri computer dal relativo spazio di esecuzione di Windows PowerShell consentito, aumentando la sicurezza dell'ambiente Accesso Web Windows PowerShell. La configurazione di sessione può essere distribuita, usando Criteri di gruppo, a tutti i computer che gli amministratori vogliono rendere accessibili con Accesso Web Windows PowerShell. Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx).
Di seguito sono riportati alcuni esempi relativi a questo scenario.

- Un amministratore crea un endpoint, denominato **EndpointPswa** e basato su uno spazio di esecuzione con restrizioni, quindi crea la regola **\*,\*,EndpointPswa**, e distribuisce l'endpoint agli altri computer. La regola consente a tutti gli utenti di accedere a tutti i computer con endpoint **EndpointPswa**. Se questa è l'unica regola di autorizzazione definita nel set di regole, i computer che non dispongono di tale endpoint non sono accessibili.

- L'amministratore ha creato un endpoint basato su uno spazio di esecuzione con restrizioni denominato **EndpointPswa** e vuole limitare l'accesso a utenti specifici. L'amministratore crea un gruppo di utenti denominato **SupportoLivello1** e definisce la regola **SupportoLivello1,\*,EndpointPswa**. La regola concede agli utenti del gruppo **SupportoLivello1** l'accesso a tutti i computer che dispongono della configurazione **EndpointPswa**. Analogamente, è possibile impostare l'accesso con restrizioni per un insieme di computer specifico.

- Alcuni amministratori forniscono maggiori diritti di accesso a determinati utenti, ad esempio creando i due gruppi di utenti **Amministratori** e **SupportoBase**. L'amministratore crea anche un endpoint basato su uno spazio di esecuzione con restrizioni denominato **EndpointPswa** e definisce le due regole seguenti: **Amministratori,\*,\*** e **SupportoBase,\*,EndpointPswa**. La prima regola fornisce l'accesso a tutti i computer a tutti gli utenti del gruppo **Amministratori**, mentre la seconda consente a tutti gli utenti del gruppo **SupportoBase** di accedere solo ai computer con **EndpointPswa**.

- Un amministratore ha configurato un ambiente di test privato e desidera consentire a tutti gli utenti autorizzati della rete di accedere a tutti i computer della rete che utilizzando normalmente, con accesso a tutte le configurazioni di sessione che utilizzando normalmente. Poiché si tratta di un ambiente di test privato, l'amministratore crea una regola di autorizzazione non sicura.
  - L'amministratore esegue il cmdlet `Add-PswaAuthorizationRule * * *`, che utilizza il carattere jolly **\*** per rappresentare tutti gli utenti, tutti i computer e tutte le configurazioni.
  - Tale regola equivale alla seguente: `Add-PswaAuthorizationRule -UserName * -ComputerName * -ConfigurationName *`.

  >**Nota**:
  >
  >Non è consigliabile usare questa regola in un ambiente sicuro, perché elude il livello di sicurezza fornito da Accesso Web Windows PowerShell.

- Un amministratore deve consentire agli utenti di connettersi ai computer di destinazione di un ambiente che include sia gruppi di lavoro che domini. I computer dei gruppi di lavoro vengono talvolta utilizzati per connettersi ai computer di destinazione nei domini e i computer dei domini vengono talvolta utilizzati per connettersi a computer di destinazione nei gruppi di lavoro. L'amministratore ha incluso il server gateway, *PswaServer*, nel gruppo di lavoro e il computer di destinazione *srv1.contoso.com* in un dominio. *Chris* è un utente locale autorizzato sia nel server gateway del gruppo di lavoro che nel computer di destinazione. Nel server del gruppo di lavoro il suo nome utente è *chrisLocal*, mentre nel computer di destinazione è *contoso\\chris*. Per autorizzare Chris ad accedere a srv1.contoso.com, l'amministratore aggiunge la regola seguente.

```powershell
Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell
```

Tale regola consente di autenticare Chris nel server gateway e autorizzarne l'accesso a *srv1*. Nella pagina di accesso Chris deve specificare un secondo set di credenziali nell'area **Impostazioni di connessione facoltative** (*contoso\\chris*). Il server gateway usa il set di credenziali aggiuntivo per autenticare l'utente nel computer di destinazione, *srv1.contoso.com*.

Nello scenario precedente Accesso Web Windows PowerShell può stabilire la connessione al computer di destinazione solo se le operazioni seguenti riescono e sono consentite almeno da una regola di autorizzazione.

1. Autenticazione nel server gateway del gruppo di lavoro, con l'aggiunta di un nome utente con formato *nome_server*\\*nome_utente* alla regola di autorizzazione

2. Autenticazione nel computer di destinazione con le credenziali alternative specificate nell'area **Impostazioni di connessione facoltative** della pagina di accesso

  >**Nota**:
  >
  >Se il gateway e i computer di destinazione si trovano in gruppi di lavoro o domini diversi, è necessario stabilire una relazione di trust tra i computer nei due gruppi di lavoro, i due domini o tra il gruppo di lavoro e il dominio. Tale relazione non può essere configurata usando i cmdlet di Accesso Web Windows PowerShell per le regole di autorizzazione. Le regole di autorizzazione non definiscono una relazione di trust fra computer, ma si limitano ad autorizzare gli utenti a connettersi a specifici computer di destinazione e configurazioni di sessione. Per altre informazioni su come configurare una relazione di trust fra domini diversi, vedere l'articolo relativo alla [creazione di relazioni di trust fra domini e foreste](https://technet.microsoft.com/library/cc794775.aspx"). Per altre informazioni su come aggiungere i computer del gruppo di lavoro a un elenco di host attendibili, vedere [Gestione remota tramite Server Manager](https://technet.microsoft.com/library/dd759202.aspx)

### <a name="using-a-single-set-of-authorization-rules-for-multiple-sites"></a>Utilizzo di un singolo set di regole di autorizzazione per più siti

Le regole di autorizzazione sono archiviate in un file XML, il cui percorso è per impostazione predefinita _%windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml_.

Il percorso del file XML delle regole di autorizzazione è archiviato nel file **powwa.config**, disponibile in _%windir%\\Web\\PowershellWebAccess\\data_. L'amministratore ha la possibilità di modificare il riferimento al percorso predefinito in **powwa.config**, per soddisfare preferenze o requisiti specifici. La possibilità di modificare il percorso del file consente di usare le stesse regole di autorizzazione per più gateway di Accesso Web Windows PowerShell, se si vuole creare una configurazione di questo tipo.

## <a name="session-management"></a>Gestione delle sessioni

Per impostazione predefinita, Accesso Web Windows PowerShell consente un massimo di tre sessioni contemporanee per utente. Per modificare il numero di sessioni supportato per ogni utente, è possibile modificare il file **web.config** dell'applicazione Web in Gestione IIS.
Il percorso del file **web.config** è _$Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config_.

Per impostazione predefinita, il server Web IIS è configurato in modo da riavviare il pool di applicazioni in caso di modifica delle impostazioni. Ad esempio, se si modifica il file **web.config**, il pool di applicazioni viene riavviato.
>Dal momento che **Accesso Web Windows PowerShell** usa gli stati sessione in memoria, gli utenti connessi alle sessioni di **Accesso Web Windows PowerShell** perdono il proprio stato al riavvio del pool di applicazioni.

### <a name="setting-default-parameters-on-the-sign-in-page"></a>Impostazione dei parametri predefiniti nella pagina di accesso

Se il gateway di Accesso Web Windows PowerShell è in esecuzione in Windows Server 2012 R2, è possibile configurare valori predefiniti per le impostazioni visualizzate nella pagina di accesso di Accesso Web Windows PowerShell. I valori devono essere configurati nel file **web.config** descritto nel paragrafo precedente. I valori predefiniti per le impostazioni della pagina di accesso sono disponibili nella sezione **appSettings** del file web.config. Ecco un esempio della sezione **appSettings**. I valori validi per molte di queste impostazioni sono gli stessi di quelli dei parametri corrispondenti del cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) in Windows PowerShell.
Ad esempio, la chiave `defaultApplicationName`, come illustrato nel blocco di codice seguente, corrisponde al valore della variabile di preferenza **$PSSessionApplicationName** nel computer di destinazione.

```xml
    <appSettings>
            <add key="maxSessionsAllowedPerUser" value="3"/>
            <add key="defaultPortNumber" value="5985"/>
            <add key="defaultSSLPortNumber" value="5986"/>
            <add key="defaultApplicationName" value="WSMAN"/>
            <add key="defaultUseSslSelection" value="0"/>
            <add key="defaultAuthenticationType" value="0"/>
            <add key="defaultAllowRedirection" value="0"/>
            <add key="defaultConfigurationName" value="Microsoft.PowerShell"/>
    </appSettings>
```

### <a name="time-outs-and-unplanned-disconnections"></a>Disconnessioni e timeout non pianificati

Per le sessioni di Accesso Web Windows PowerShell è previsto un timeout. In Accesso Web Windows PowerShell in esecuzione in Windows Server 2012, dopo 15 minuti di inattività della sessione viene visualizzato un messaggio di timeout. Se l'utente non risponde entro cinque minuti dalla visualizzazione del messaggio di timeout, la sessione viene chiusa e l'utente viene disconnesso. La durata dei periodi di timeout delle sessioni può essere modificata nelle impostazioni del sito Web in Gestione IIS.

In Accesso Web Windows PowerShell in esecuzione in Windows Server 2012 R2, per impostazione predefinita le sessioni scadono dopo 20 minuti di inattività. Se gli utenti vengono disconnessi da una sessione nella console basata sul Web a causa di un errore di rete, arresti non pianificati o altri errori e non perché la sessione è stata volutamente chiusa, le sessioni di Accesso Web Windows PowerShell rimarranno in esecuzione e connesse al computer di destinazione, finché non sarà trascorso il periodo di timeout sul lato client. La sessione viene disconnessa trascorsi i 20 minuti predefiniti o dopo il periodo di timeout specificato dall'amministratore del gateway, a seconda del valore inferiore.

Se il server gateway esegue Windows Server 2012 R2, Accesso Web Windows PowerShell consente agli utenti di riconnettersi alle sessioni salvate in un secondo momento, ma quando le sessioni vengono disconnesse a causa di errori di rete, arresti non pianificati o altri errori, gli utenti non potranno visualizzare le sessioni salvate o riconnettersi finché non sarà trascorso il periodo di timeout specificato dall'amministratore del gateway.

## <a name="see-also"></a>Vedere anche

- [Installare e usare Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
- [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
- [Windows PowerShell Web Access Cmdlets](cmdlets/web-access-cmdlets.md) (Cmdlet di Accesso Web Windows PowerShell)