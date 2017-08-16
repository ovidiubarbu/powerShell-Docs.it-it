---
ms.date: 2017-06-05T00:00:00.000Z
keywords: powershell,cmdlet
title: "regole di autorizzazione e funzionalità di sicurezza di accesso web windows powershell"
ms.openlocfilehash: 706830f618173879185f5b84570fdc7782434d59
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="authorization-rules-and-security-features-of-windows-powershell-web-access"></a>Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

Accesso Web di Windows PowerShell® in Windows Server® 2012 R2 e Windows Server® 2012 prevede un modello di sicurezza restrittivo. È necessario che agli utenti venga concesso l'accesso in modo esplicito prima che possano accedere al gateway Accesso Web Windows PowerShell e usare la console di Windows PowerShell basata sul Web.

-   [Configurazione delle regole di autorizzazione e della sicurezza del sito](#BKMK_auth)

-   [Gestione delle sessioni](#BKMK_sesmgmt)


Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso. Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente. Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione. Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).

Gli amministratori possono definire da 0 a *n* regole di autenticazione per Accesso Web Windows PowerShell. Poiché la sicurezza predefinita è di tipo restrittivo, l'assenza di regole di autenticazione implica che nessun utente può accedere ad alcun elemento.

I cmdlet Add-PswaAuthorizationRule e Test-PswaAuthorizationRule in Windows Server 2012 R2 includono ora un parametro Credential che consente di aggiungere e testare le regole di autorizzazione di Accesso Web Windows PowerShell da un computer remoto o in una sessione di Accesso Web Windows PowerShell attiva. Come con gli altri cmdlet di Windows PowerShell che includono un parametro Credential, è possibile specificare un oggetto PSCredential come valore del parametro. Per creare un oggetto PSCredential che contiene le credenziali da passare a un computer remoto, eseguire il cmdlet [Get-Credential](https://technet.microsoft.com/library/hh849815.aspx).

Le regole di autenticazione Accesso Web Windows PowerShell sono costituite da elenchi di operazioni consentite. Ogni regola definisce una connessione consentita fra utenti, computer di destinazione e specifiche [configurazioni di sessione](https://technet.microsoft.com/library/dd819508.aspx) di Windows PowerShell, denominate anche endpoint o spazi di esecuzione, nei computer di destinazione specificati.

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Nota sulla sicurezza </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Affinché un utente possa ottenere l'accesso, è sufficiente che una sola regola risulti vera. Se dalla console basata sul Web si consente a un utente di accedere a un computer, con accesso al linguaggio completo o solo ai cmdlet di Windows PowerShell per la gestione remota, tale utente potrà accedere (o passare) ad altri computer connessi al primo computer di destinazione. Il modo più sicuro per configurare Accesso Web Windows PowerShell consiste nel limitare l'accesso degli utenti alle sole configurazioni di sessione vincolate (denominate anche endpoint o spazi di esecuzione) che consentono di eseguire le specifiche attività che devono essere in genere eseguite in modalità remota.</p></td>
</tr>
</tbody>
</table>

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Nome</p></th>
<th><p>Descrizione</p></th>
<th><p>Parametri</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592890.aspx">Add-PswaAuthorizationRule</a></p></td>
<td><p>Aggiunge una nuova regola di autorizzazione al set di regole di autorizzazione di Accesso Web Windows PowerShell.</p></td>
<td><ul>
<li><p>ComputerGroupName</p></li>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserGroupName</p></li>
<li><p>UserName</p></li>
<li><p>Credenziali (Windows Server 2012 R2 e versioni successive)</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592893.aspx">Remove-PswaAuthorizationRule</a></p></td>
<td><p>Rimuove da Accesso Web Windows PowerShell una regola di autorizzazione specificata.</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p><a href="https://technet.microsoft.com/library/jj592891.aspx">Get-PswaAuthorizationRule</a></p></td>
<td><p>Restituisce un set di regole di autorizzazione di Accesso Web Windows PowerShell. Se utilizzato senza parametri, questo cmdlet restituisce tutte le regole.</p></td>
<td><ul>
<li><p>Id</p></li>
<li><p>RuleName</p></li>
</ul></td>
</tr>
<tr class="even">
<td><p><a href="https://technet.microsoft.com/library/jj592892.aspx">Test-PswaAuthorizationRule</a></p></td>
<td><p>Valuta le regole di autorizzazione per determinare se una specifica richiesta di accesso per un utente, un computer o una configurazione di sessione è stata autorizzata. Per impostazione predefinita, se non vengono aggiunti parametri questo cmdlet valuta tutte le regole di autorizzazione. Gli amministratori possono aggiungere parametri per specificare una regola di autorizzazione o un sottoinsieme di regole da testare.</p></td>
<td><ul>
<li><p>ComputerName</p></li>
<li><p>ConfigurationName</p></li>
<li><p>RuleName</p></li>
<li><p>UserName</p></li>
<li><p>Credenziali (Windows Server 2012 R2 e versioni successive)</p></li>
</ul></td>
</tr>
</tbody>
</table>

I cmdlet precedenti creano un set di regole di accesso, che viene usato per autorizzare un utente nel gateway di Accesso Web Windows PowerShell. Le regole sono diverse dagli elenchi di controllo di accesso (ACL) nei computer di destinazione e forniscono un livello di sicurezza aggiuntivo per l'accesso Web. Ulteriori informazioni sulla sicurezza verranno fornite nelle sezioni successive.

Se un utente non supera tali livelli di sicurezza, riceve un messaggio di "accesso negato" nella finestra del browser. Anche se i dettagli relativi alla sicurezza vengono registrati nel server gateway, agli utenti finali non viene comunicato il numero dei livelli di sicurezza superati o il livello a cui si è verificato l'errore di accesso o autenticazione.

Per altre informazioni sulla configurazione delle regole di autorizzazione, vedere la sezione [Configurazione delle regole di autorizzazione](#BKMK_configrules) in questo argomento.

<a href="" id="BKMK_sec"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Sicurezza</span></a>

------------------------------------------------------------------------

Il modello di sicurezza di Accesso Web Windows PowerShell prevede quattro livelli fra l'utente finale della console basata sul Web e un computer di destinazione. Gli amministratori di Accesso Web Windows PowerShell possono aggiungere ulteriori livelli di sicurezza eseguendo alcune operazioni di configurazione nella console Gestione IIS. Per altre informazioni sulla protezione dei siti Web nella console Gestione IIS, vedere [Configurare la sicurezza del server Web (IIS 7)](https://technet.microsoft.com/library/cc731278(v=ws.10).aspx). Per altre informazioni sulle procedure consigliate per IIS e su come prevenire gli attacchi DoS (Denial of Service), vedere le [procedure consigliate per la prevenzione degli attacchi DoS (Denial of Service)](https://technet.microsoft.com/library/cc750213.aspx). L'amministratore può anche acquistare e installare un prodotto di autenticazione commerciale.

I quattro livelli di sicurezza fra l'utente finale e il computer di destinazione sono illustrati nella tabella seguente.

<table>
<colgroup>
<col width="33%" />
<col width="33%" />
<col width="33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Ordine</p></th>
<th><p>Livello</p></th>
<th><p>Descrizione</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>1</p></td>
<td><p>Funzionalità di sicurezza del server Web (IIS), come l'autenticazione tramite certificati client</p></td>
<td><p>Gli utenti di Accesso Web Windows PowerShell devono sempre fornire nome utente e password per autenticare l'account nel gateway. Gli amministratori di Accesso Web Windows PowerShell possono tuttavia decidere di attivare o disattivare l'autenticazione con certificati client (vedere il passaggio 10 della procedura "Per utilizzare Gestione IIS per configurare il gateway in un sito Web esistente" in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installare e usare Accesso Web Windows PowerShell</a>). La funzionalità facoltativa per i certificati client richiede che, oltre al nome utente e alla password, gli utenti forniscano anche un certificato client valido, nell'ambito della configurazione del server Web (IIS). Se il livello relativo al certificato client è abilitato, la pagina di accesso di Accesso Web Windows PowerShell richiede agli utenti di fornire un certificato valido prima di valutare le relative credenziali. L'autenticazione tramite certificati client controlla automaticamente il certificato client.</p>
<p>Se non viene trovato un certificato valido, Accesso Web Windows PowerShell informa l'utente in modo che possa fornirne uno. Se viene trovato un certificato valido, Accesso Web Windows PowerShell apre la pagina di accesso per consentire agli utenti di immettere nome utente e password.</p>
<p>Questo è un esempio delle impostazioni di sicurezza aggiuntive offerte dal server Web (IIS). Per informazioni sulle altre funzionalità di sicurezza di IIS, vedere <a href="https://technet.microsoft.com/library/cc731278(ws.10).aspx">Configurare la sicurezza del server Web (IIS 7)</a>.</p></td>
</tr>
<tr class="even">
<td><p>2</p></td>
<td><p>Autenticazione del gateway basata su moduli di Accesso Web Windows PowerShell</p></td>
<td><p>La pagina di accesso di Accesso Web Windows PowerShell richiede un set di credenziali (nome utente e password) e offre agli utenti la possibilità di specificare credenziali diverse per il computer di destinazione. Se l'utente non fornisce altre credenziali, per la connessione al computer di destinazione vengono utilizzati il nome utente e la password principali specificati per la connessione al gateway.</p>
<p>Le credenziali richieste vengono autenticate nel gateway di Accesso Web Windows PowerShell e devono corrispondere ad account utente validi nel server gateway locale di Accesso Web Windows PowerShell o in Active Directory®.</p>
<p>Dopo l'autenticazione dell'utente nel gateway, Accesso Web Windows PowerShell controlla le regole di autorizzazione per verificare se l'utente ha accesso al computer di destinazione richiesto. Se l'autorizzazione ha esito positivo, le credenziali dell'utente vengono passate al computer di destinazione.</p></td>
</tr>
<tr class="odd">
<td><p>3</p></td>
<td><p>Regole di autorizzazione di Accesso Web Windows PowerShell</p></td>
<td><p>Dopo l'autenticazione dell'utente nel gateway, Accesso Web Windows PowerShell controlla le regole di autorizzazione per verificare se l'utente ha accesso al computer di destinazione richiesto. Se l'autorizzazione ha esito positivo, le credenziali dell'utente vengono passate al computer di destinazione.</p>
<p>Tali regole vengono valutate solo dopo l'autenticazione dell'utente nel gateway e prima dell'autenticazione nel computer di destinazione.</p></td>
</tr>
<tr class="even">
<td><p>4</p></td>
<td><p>Autenticazione e regole di autorizzazione del computer di destinazione</p></td>
<td><p>L'ultimo livello di sicurezza di Accesso Web Windows PowerShell è costituito dalla configurazione di protezione del computer di destinazione. Gli utenti devono avere i diritti di accesso appropriati, configurati sia nel computer di destinazione che nelle regole di autorizzazione di Accesso Web Windows PowerShell, per eseguire una console Windows PowerShell basata sul Web che può operare sul computer di destinazione con Accesso Web Windows PowerShell.</p>
<p>Questo livello offre un meccanismo di sicurezza uguale a quello che valuta i tentativi di connessione quando un utente crea una sessione remota di Windows PowerShell per un computer di destinazione direttamente da Windows PowerShell, eseguendo il cmdlet <strong>Enter-PSSession</strong> o <strong>New-PSSession</strong>.</p>
<p>Per impostazione predefinita, Accesso Web Windows PowerShell usa il nome utente e la password principali per eseguire l'autenticazione sia nel gateway che nel computer di destinazione. La sezione <strong>Impostazioni di connessione facoltative</strong> della pagina Web di accesso offre agli utenti la possibilità di specificare credenziali diverse per il computer di destinazione, se sono necessarie. Se l'utente non fornisce altre credenziali, per la connessione al computer di destinazione vengono utilizzati il nome utente e la password principali specificati per la connessione al gateway.</p>
<p>Le regole di autorizzazione possono essere utilizzate per consentire agli utenti di accedere a una configurazione di sessione specifica. È possibile creare configurazioni di sessione o spazi di esecuzione con restrizioni per Accesso Web Windows PowerShell e consentire a utenti specifici di connettersi solo a configurazioni di sessione specifiche, quando effettuano l'accesso ad Accesso Web Windows PowerShell. È possibile utilizzare gli elenchi di controllo di accesso (ACL) per identificare gli utenti che hanno accesso a endpoint specifici e limitare ulteriormente l'accesso all'endpoint per un gruppo di utenti specifico, utilizzando le regole di autorizzazione descritte in questa sezione. Per altre informazioni sugli spazi di esecuzione con restrizioni, vedere l'articolo relativo agli <a href="https://msdn.microsoft.com/library/windows/desktop/ee706589.aspx">spazi di esecuzione con restrizioni</a> su MSDN.</p></td>
</tr>
</tbody>
</table>

<a href="" id="BKMK_configrules"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurazione delle regole di autorizzazione</span></a>

------------------------------------------------------------------------

In genere gli amministratori vogliono applicare agli utenti di Accesso Web Windows PowerShell le stesse regole di autorizzazione già definite nell'ambiente per la gestione remota di Windows PowerShell. La prima procedura di questa sezione illustra come aggiungere una regola di autorizzazione sicura che consente l'accesso a un singolo utente per la gestione di un singolo computer con una singola configurazione di sessione. La seconda procedura illustra come rimuovere una regola di autorizzazione non più necessaria.

Se si prevede di usare configurazioni di sessione personalizzate per consentire a utenti specifici di lavorare esclusivamente in spazi di esecuzione di Accesso Web Windows PowerShell con restrizioni, creare le configurazioni di sessione personalizzate prima di aggiungere le regole di autorizzazione che vi fanno riferimento. Non è possibile usare i cmdlet di Accesso Web Windows PowerShell per creare configurazioni di sessione personalizzate. Per altre informazioni sulla creazione di configurazioni di sessione personalizzate, vedere [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) su MSDN.

L'unico carattere jolly supportato dai cmdlet di Accesso Web Windows PowerShell è l'asterisco ( \* ). I caratteri jolly all'interno delle stringhe non sono supportati. Utilizzare un singolo asterisco per proprietà (utenti, computer o configurazioni di sessione).

<table>
<colgroup>
<col width="100%" />
</colgroup>
<thead>
<tr class="header">
<th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Per altre modalità di uso della regole di autorizzazione per la concessione dell'accesso agli utenti e la protezione dell'ambiente Accesso Web Windows PowerShell, vedere la sezione <a href="#BKMK_others">Altri scenari di esempio per le regole di autorizzazione</a> in questo argomento.</p></td>
</tr>
</tbody>
</table>

#### <a name="to-add-a-restrictive-authorization-rule"></a>Per aggiungere una regola di autorizzazione restrittiva

1.  Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

2.  <span class="label">Passaggio facoltativo per la limitazione dell'accesso utente con configurazioni di sessione:</span> verificare che le configurazioni di sessione da usare nelle proprie regole esistano già. Se non sono ancora state create, utilizzare le istruzioni per la creazione di configurazioni di sessione disponibili nell'articolo [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) di MSDN.

3.  Digitare il comando seguente e quindi premere **INVIO**.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_1079478f-cd51-4d35-8022-4b532a9d57a4'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente, tramite una specifica configurazione di sessione con ambito limitato alle esigenze tipiche di utilizzo di script e cmdlet dell'utente. Nell'esempio seguente, a un utente di nome <span class="code">JSmith</span> nel dominio <span class="code">Contoso</span> viene consentito l'accesso per la gestione del computer <span class="code">Contoso_214</span>, con una configurazione di sessione denominata <span class="code">NewAdminsOnly</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4e760377-e401-4ef4-988f-7a0aec1b2a90'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;. Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.

#### <a name="to-remove-an-authorization-rule"></a>Per rimuovere una regola di autorizzazione

1.  Se non è ancora stata aperta una sessione di Windows PowerShell, vedere il passaggio 1 della procedura [Per aggiungere una regola di autorizzazione restrittiva](#BKMK_arar) in questa sezione.

2.  Digitare il comando seguente e premere **INVIO**. *ID regola* rappresenta l'ID univoco della regola che si vuole rimuovere.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0daef66d-0ecf-47fb-a8a0-d4dbceb8409d'); "Copia negli Appunti.")

        Remove-PswaAuthorizationRule -ID <rule ID>

    In alternativa, se non si conosce il numero ID ma si conosce il nome descrittivo della regola da rimuovere, è possibile aggiungere tale nome al cmdlet <span class="code">Remove-PswaAuthorizationRule</span> per rimuovere la regola, come nell'esempio seguente: Get-PswaAuthorizationRule -RuleName &lt;*nome regola*&gt; | Remove-PswaAuthorizationRule.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Non viene richiesto se si vuole eliminare la regola di autorizzazione specificata, perché l'eliminazione avviene infatti quando si premere <strong>INVIO</strong>. Verificare con attenzione la regola di autorizzazione da rimuovere prima di eseguire il cmdlet <strong>Remove-PswaAuthorizationRule</strong>.</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_others"></a>
####

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Altri esempi di scenari per le regole di autorizzazione</span></a>

------------------------------------------------------------------------

Per ogni sessione di Windows PowerShell viene usata una configurazione di sessione. Se non è specificata, Windows PowerShell usa la configurazione di sessione predefinita incorporata in Windows PowerShell, denominata Microsoft.PowerShell, che include tutti i cmdlet disponibili in un computer. Gli amministratori possono limitare l'accesso a tutti i computer definendo una configurazione di sessione basata su uno spazio di esecuzione con restrizioni, ovvero un insieme limitato di attività e cmdlet che possono essere eseguiti dagli utenti finali. Se si consente a un utente di accedere a un computer, con accesso al linguaggio completo o solo ai cmdlet di Windows PowerShell per la gestione remota, tale utente potrà connettersi agli altri computer connessi al primo. Definendo uno spazio di esecuzione con restrizioni si impedisce agli utenti di accedere ad altri computer dal relativo spazio di esecuzione di Windows PowerShell consentito, aumentando la sicurezza dell'ambiente Accesso Web Windows PowerShell. La configurazione di sessione può essere distribuita, usando Criteri di gruppo, a tutti i computer che gli amministratori vogliono rendere accessibili con Accesso Web Windows PowerShell. Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx). Di seguito sono riportati alcuni esempi relativi a questo scenario.

-   Un amministratore crea un endpoint, denominato **EndpointPswa** e basato su uno spazio di esecuzione con restrizioni, quindi crea la regola **\*,\*,EndpointPswa**, e distribuisce l'endpoint agli altri computer. La regola consente a tutti gli utenti di accedere a tutti i computer con endpoint **EndpointPswa**. Se questa è l'unica regola di autorizzazione definita nel set di regole, i computer che non dispongono di tale endpoint non sono accessibili.

-   L'amministratore ha creato un endpoint basato su uno spazio di esecuzione con restrizioni denominato **EndpointPswa** e vuole limitare l'accesso a utenti specifici. L'amministratore crea un gruppo di utenti denominato **SupportoLivello1** e definisce la regola **SupportoLivello1,\*,EndpointPswa**. La regola concede agli utenti del gruppo **SupportoLivello1** l'accesso a tutti i computer che dispongono della configurazione **EndpointPswa**. Analogamente, è possibile impostare l'accesso con restrizioni per un insieme di computer specifico.

-   Alcuni amministratori forniscono maggiori diritti di accesso a determinati utenti, ad esempio creando i due gruppi di utenti **Amministratori** e **SupportoBase**. L'amministratore crea anche un endpoint basato su uno spazio di esecuzione con restrizioni denominato **EndpointPswa** e definisce le due regole seguenti: **Amministratori,\*,\*** e **SupportoBase,\*,EndpointPswa**. La prima regola fornisce l'accesso a tutti i computer a tutti gli utenti del gruppo **Amministratori**, mentre la seconda consente a tutti gli utenti del gruppo **SupportoBase** di accedere solo ai computer con **EndpointPswa**.

-   Un amministratore ha configurato un ambiente di test privato e desidera consentire a tutti gli utenti autorizzati della rete di accedere a tutti i computer della rete che utilizzando normalmente, con accesso a tutte le configurazioni di sessione che utilizzando normalmente. Poiché si tratta di un ambiente di test privato, l'amministratore crea una regola di autorizzazione non sicura. L'amministratore esegue il cmdlet <span class="code">Add-PswaAuthorizationRule \* \* \*</span>, che usa il carattere jolly **\*** per rappresentare tutti gli utenti, tutti i computer e tutte le configurazioni. Questa regola è equivalente alla seguente: <span class="code">Add-PswaAuthorizationRule -UserName \* -ComputerName \* -ConfigurationName \*</span>.

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC17938.jpeg" title="System_CAPS_security" alt="System_CAPS_security" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-security" /></span><span class="alertTitle"> Nota sulla sicurezza </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Non è consigliabile usare questa regola in un ambiente sicuro, perché elude il livello di sicurezza fornito da Accesso Web Windows PowerShell.</p></td>
    </tr>
    </tbody>
    </table>

-   Un amministratore deve consentire agli utenti di connettersi ai computer di destinazione di un ambiente che include sia gruppi di lavoro che domini. I computer dei gruppi di lavoro vengono talvolta utilizzati per connettersi ai computer di destinazione nei domini e i computer dei domini vengono talvolta utilizzati per connettersi a computer di destinazione nei gruppi di lavoro. L'amministratore ha incluso il server gateway, *PswaServer*, nel gruppo di lavoro e il computer di destinazione *srv1.contoso.com* in un dominio. *Chris* è un utente locale autorizzato sia nel server gateway del gruppo di lavoro che nel computer di destinazione. Nel server del gruppo di lavoro il suo nome utente è *chrisLocal*, mentre nel computer di destinazione è *contoso\\chris*. Per autorizzare Chris ad accedere a srv1.contoso.com, l'amministratore aggiunge la regola seguente.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_8d183d3d-1c19-44b8-9297-530b0efc7c79'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -userName PswaServer\chrisLocal -computerName srv1.contoso.com -configurationName Microsoft.PowerShell

    Tale regola consente di autenticare Chris nel server gateway e autorizzarne l'accesso a *srv1*. Nella pagina di accesso Chris deve specificare un secondo set di credenziali nell'area **Impostazioni di connessione facoltative** (*contoso\\chris*). Il server gateway usa il set di credenziali aggiuntivo per autenticare l'utente nel computer di destinazione, *srv1.contoso.com*.

    Nello scenario precedente Accesso Web Windows PowerShell può stabilire la connessione al computer di destinazione solo se le operazioni seguenti riescono e sono consentite almeno da una regola di autorizzazione.

    1.  Autenticazione nel server gateway del gruppo di lavoro, con l'aggiunta di un nome utente con formato *nome_server*\\*nome_utente* alla regola di autorizzazione

    2.  Autenticazione nel computer di destinazione con le credenziali alternative specificate nell'area **Impostazioni di connessione facoltative** della pagina di accesso

    <table>
    <colgroup>
    <col width="100%" />
    </colgroup>
    <thead>
    <tr class="header">
    <th><span><img src="https://i-technet.sec.s-msft.com/dynimg/IC101471.jpeg" title="System_CAPS_note" alt="System_CAPS_note" id="s-e6f6a65cf14f462597b64ac058dbe1d0-system-media-system-caps-note" /></span><span class="alertTitle">Nota </span></th>
    </tr>
    </thead>
    <tbody>
    <tr class="odd">
    <td><p>Se il gateway e i computer di destinazione si trovano in gruppi di lavoro o domini diversi, è necessario stabilire una relazione di trust tra i computer nei due gruppi di lavoro, i due domini o tra il gruppo di lavoro e il dominio. Tale relazione non può essere configurata usando i cmdlet di Accesso Web Windows PowerShell per le regole di autorizzazione. Le regole di autorizzazione non definiscono una relazione di trust fra computer, ma si limitano ad autorizzare gli utenti a connettersi a specifici computer di destinazione e configurazioni di sessione. Per altre informazioni su come configurare una relazione di trust fra domini diversi, vedere l'articolo relativo alla <a href="https://technet.microsoft.com/library/cc794775.aspx">creazione di relazioni di trust fra domini e foreste</a>. Per ulteriori informazioni su come aggiungere i computer del gruppo di lavoro a un elenco di host attendibili, vedere l'articolo relativo alla <a href="https://technet.microsoft.com/library/dd759202.aspx">gestione remota con Server Manager</a>.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Uso di un singolo set di regole di autorizzazione per più siti</span></a>

------------------------------------------------------------------------

Le regole di autorizzazione sono archiviate in un file XML, che per impostazione predefinita ha percorso %windir%\\Web\\PowershellWebAccess\\data\\AuthorizationRules.xml.

Il percorso del file XML delle regole di autorizzazione è archiviato nel file **powwa.config**, disponibile in %windir%\\Web\\PowershellWebAccess\\data. L'amministratore ha la possibilità di modificare il riferimento al percorso predefinito in **powwa.config**, per soddisfare preferenze o requisiti specifici. La possibilità di modificare il percorso del file consente di usare le stesse regole di autorizzazione per più gateway di Accesso Web Windows PowerShell, se si vuole creare una configurazione di questo tipo.

<a href="" id="BKMK_sesmgmt"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Gestione delle sessioni</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Fare clic con il pulsante destro del mouse per copiare e condividere il collegamento per questa sezione"></a>

------------------------------------------------------------------------

Per impostazione predefinita, Accesso Web Windows PowerShell consente un massimo di tre sessioni contemporanee per utente. Per modificare il numero di sessioni supportato per ogni utente, è possibile modificare il file **web.config** dell'applicazione Web in Gestione IIS. Il percorso del file **web.config** è $Env:Windir\\Web\\PowerShellWebAccess\\wwwroot\\Web.config.

Per impostazione predefinita, il server Web (IIS) è configurato in modo da riavviare il pool di applicazioni in caso di modifica delle impostazioni. Ad esempio, se si modifica il file **web.config**, il pool di applicazioni viene riavviato. Dal momento che Accesso Web Windows PowerShell usa gli stati di sessione in memoria, gli utenti connessi alle sessioni di Accesso Web Windows PowerShell perdono il proprio stato al riavvio del pool di applicazioni.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Impostazione dei parametri predefiniti nella pagina di accesso</span></a>

------------------------------------------------------------------------

Se il gateway di Accesso Web Windows PowerShell è in esecuzione in Windows Server 2012 R2, è possibile configurare valori predefiniti per le impostazioni visualizzate nella pagina di accesso di Accesso Web Windows PowerShell. I valori devono essere configurati nel file **web.config** descritto nel paragrafo precedente. I valori predefiniti per le impostazioni della pagina di accesso sono disponibili nella sezione **appSettings** del file web.config. Ecco un esempio della sezione **appSettings**. I valori validi per molte di queste impostazioni sono gli stessi di quelli dei parametri corrispondenti del cmdlet [New-PSSession](https://technet.microsoft.com/library/hh849717.aspx) in Windows PowerShell. Ad esempio, la chiave <span class="code">defaultApplicationName</span>, come mostrato nel blocco di codice seguente, corrisponde al valore della variabile di preferenza **$PSSessionApplicationName** nel computer di destinazione.

[Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_6ccfd0a1-485a-4ac5-9636-89ebab501bef'); "Copia negli Appunti.")

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

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Timeout e disconnessioni non pianificate</span></a>

------------------------------------------------------------------------

Per le sessioni di Accesso Web Windows PowerShell è previsto un timeout. In Accesso Web Windows PowerShell in esecuzione in Windows Server 2012, dopo 15 minuti di inattività della sessione viene visualizzato un messaggio di timeout. Se l'utente non risponde entro cinque minuti dalla visualizzazione del messaggio di timeout, la sessione viene chiusa e l'utente viene disconnesso. La durata dei periodi di timeout delle sessioni può essere modificata nelle impostazioni del sito Web in Gestione IIS.

In Accesso Web Windows PowerShell in esecuzione in Windows Server 2012 R2, per impostazione predefinita le sessioni scadono dopo 20 minuti di inattività. Se gli utenti vengono disconnessi da una sessione nella console basata sul Web a causa di un errore di rete, arresti non pianificati o altri errori e non perché la sessione è stata volutamente chiusa, le sessioni di Accesso Web Windows PowerShell rimarranno in esecuzione e connesse al computer di destinazione, finché non sarà trascorso il periodo di timeout sul lato client. La sessione viene disconnessa trascorsi i 20 minuti predefiniti o dopo il periodo di timeout specificato dall'amministratore del gateway, a seconda del valore inferiore.

Se il server gateway esegue Windows Server 2012 R2, Accesso Web Windows PowerShell consente agli utenti di riconnettersi alle sessioni salvate in un secondo momento, ma quando le sessioni vengono disconnesse a causa di errori di rete, arresti non pianificati o altri errori, gli utenti non potranno visualizzare le sessioni salvate o riconnettersi finché non sarà trascorso il periodo di timeout specificato dall'amministratore del gateway.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Comprimi"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/dn282394(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Fare clic con il pulsante destro del mouse per copiare e condividere il collegamento per questa sezione"></a>

------------------------------------------------------------------------

[Installare e usare Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[about_Session_Configurations](https://technet.microsoft.com/library/dd819508.aspx)
[Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx)

<span>Show:</span> Inherited Protected

<span class="stdr-votetitle">Questa pagina è stata utile?</span>
Sì No

Altri suggerimenti?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora

<span class="stdr-thankyou">Grazie</span> <span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span>

[Gestisci il tuo profilo](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

Raccontaci la tua esperienza

La pagina è stata caricata rapidamente?

<span> Sì<span> </span></span> <span> No<span> </span></span>

Ti piace la grafica?

<span> Sì<span> </span></span> <span> No<span> </span></span>

Parla con noi

-   [Newsletter Flash](https://technet.microsoft.com/cc543196.aspx)
-   |
-   [Contattaci](https://technet.microsoft.com/cc512759.aspx)
-   |
-   [Informativa sulla privacy](https://privacy.microsoft.com/privacystatement)
-   |
-   [Condizioni per l'utilizzo](https://technet.microsoft.com/cc300389.aspx)
-   |
-   [Marchi](https://www.microsoft.com/en-us/legal/intellectualproperty/Trademarks/)
-   |

© 2016 Microsoft

© 2016 Microsoft

Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft. Vedere le condizioni d'uso di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />

