---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: risoluzione dei problemi di accesso in accesso web windows powershell
ms.openlocfilehash: c10e19b177110ff62d44f28b6a523380b55b79e0
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
<a id="troubleshooting-access-problems-in-windows-powershell-web-access" class="xliff"></a>
#  Risoluzione dei problemi di accesso in Accesso Web Windows PowerShell

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

<a href="" id="BKMK_trouble"></a>

------------------------------------------------------------------------

La tabella seguente illustra alcuni problemi comuni che possono verificarsi quando gli utenti provano a connettersi a un computer remoto con Accesso Web Windows PowerShell e include alcuni suggerimenti per la risoluzione di tali problemi.

<table>
<colgroup>
<col width="50%" />
<col width="50%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Problema</p></th>
<th><p>Possibile causa e soluzione</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Errore di accesso</p></td>
<td><p>Il problema può essere dovuto a uno dei motivi seguenti.</p>
<ul>
<li><p>Non esiste una regola di autorizzazione che consenta all'utente di accedere al computer o a una configurazione di sessione specifica sul computer remoto. La sicurezza di Accesso Web Windows PowerShell è restrittiva, quindi è necessario consentire esplicitamente agli utenti l'accesso ai computer remoti, usando le regole di autorizzazione. Per altre informazioni sulla creazione delle regole di autorizzazione, vedere la sezione <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a> in questo argomento.</p></li>
<li><p>L'utente non è autorizzato ad accedere al computer di destinazione. Tale autorizzazione è determinata dagli elenchi di controllo di accesso (ACL). Per altre informazioni, vedere la sezione "Connessione ad Accesso Web Windows PowerShell" dell'articolo <a href="https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx">Usare la console di Windows PowerShell basata sul Web</a> o consultare il <a href="https://msdn.microsoft.com/library/windows/desktop/ee706585.aspx">blog del team di Windows PowerShell</a>.</p>
<ul>
<li><p>La gestione remota di Windows PowerShell potrebbe non essere abilitata nel computer di destinazione. Verificare che tale funzione sia abilitata nel computer a cui l'utente sta tentando di connettersi. Per altre informazioni, vedere la sezione "Modalità di configurazione del computer per la comunicazione remota" dell'argomento <a href="https://technet.microsoft.com/library/dd315349.aspx">about_Remote_Requirements</a> negli argomenti della Guida di Windows PowerShell.</p></li>
</ul></li>
</ul></td>
</tr>
<tr class="even">
<td><p>Quando gli utenti provano a connettersi a Accesso Web Windows PowerShell da una finestra di Internet Explorer, viene visualizzata una pagina di <strong>Errore interno del server</strong> oppure Internet Explorer smette di rispondere. Si tratta di un problema specifico di Internet Explorer.</p></td>
<td><p>Questo problema può verificarsi per gli utenti che effettuano l'accesso con un nome di dominio contenente caratteri cinesi, oppure se il nome del server gateway contiene uno o più caratteri cinesi. Per risolvere il problema, l'utente deve <a href="http://ie.microsoft.com/testdrive/info/downloads/Default.html">installare ed eseguire Internet Explorer 10</a>, quindi effettuare la procedura seguente.</p>
<ol>
<li><p>Impostare su <strong>Standard di IE10</strong> la <strong>Modalità documento</strong> di Internet Explorer.</p>
<ol>
<li><p>Premere <strong>F12</strong> per aprire la console degli strumenti di sviluppo.</p></li>
<li><p>In Internet Explorer 10 fare clic su <strong>Modalità browser</strong> e selezionare <strong>Internet Explorer 10</strong>.</p></li>
<li><p>Fare clic su <strong>Modalità documento</strong> e fare clic su <strong>Standard di IE10</strong>.</p></li>
<li><p>Premere di nuovo <strong>F12</strong> per chiudere la console degli strumenti di sviluppo.</p></li>
</ol></li>
<li><p>Disabilitare la configurazione automatica del proxy.</p>
<ol>
<li><p>In Internet Explorer 10 scegliere <strong>Opzioni Internet</strong> dal menu <strong>Strumenti</strong>.</p></li>
<li><p>Nella finestra di dialogo <strong>Opzioni Internet</strong> passare alla scheda <strong>Connessioni</strong> e fare clic su <strong>Impostazioni LAN</strong>.</p></li>
<li><p>Deselezionare la casella di controllo <strong>Rileva automaticamente impostazioni</strong>. Fare clic su <strong>OK</strong>, quindi fare di nuovo clic su <strong>OK</strong> per chiudere la finestra di dialogo <strong>Opzioni Internet</strong>.</p></li>
</ol></li>
</ol></td>
</tr>
<tr class="odd">
<td><p>Non è possibile connettersi a un computer remoto del gruppo di lavoro</p></td>
<td><p>Se il computer di destinazione è membro di un gruppo di lavoro, usare la sintassi seguente per fornire il nome utente e accedere al computer: &lt;<em>nome_gruppo_di_lavoro</em>&gt;\&lt;<em>nome_utente</em>&gt;</p></td>
</tr>
<tr class="even">
<td><p>Non è possibile trovare gli strumenti di gestione del server Web (IIS) anche se il ruolo corrispondente è stato installato</p></td>
<td><p>Se Accesso Web Windows PowerShell viene installato con il cmdlet <span class="code">Install-WindowsFeature</span>, gli strumenti di gestione non vengono installati, a meno che non si aggiunga il parametro <span class="code">IncludeManagementTools</span> al cmdlet. Per un esempio, vedere la sezione relativa all'installazione di Accesso Web Windows PowerShell con i cmdlet di Windows PowerShell in <a href="https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx">Installare e usare Accesso Web Windows PowerShell</a>. Per aggiungere la console Gestione IIS e altri strumenti di gestione di IIS necessari, selezionarli in una sessione di Aggiunta guidata ruoli e funzionalità aperta con il server gateway. L'Aggiunta guidata ruoli e funzionalità viene aperta in Server Manager.</p></td>
</tr>
<tr class="odd">
<td><p>Il sito Web di Accesso Web Windows PowerShell non è accessibile</p></td>
<td><p>Se in Internet Explorer è abilitata la funzione Configurazione sicurezza avanzata, è possibile aggiungere il sito Web di Accesso Web Windows PowerShell all'elenco dei siti attendibili o disabilitare la funzione. È possibile disabilitare Sicurezza avanzata di Internet Explorer nel riquadro <strong>Proprietà</strong> della pagina <strong>Server locale</strong> in Server Manager.</p></td>
</tr>
<tr class="even">
<td><p>Il messaggio di errore seguente viene visualizzato quando si prova a stabilire una connessione e il computer di destinazione è il server gateway ed è anche incluso in un gruppo di lavoro: <strong>Errore di autorizzazione. Verificare di essere autorizzati a connettersi al computer di destinazione.</strong></p></td>
<td><p>Se il server di destinazione è costituito dal server gateway e quest'ultimo è incluso in un gruppo di lavoro, specificare il nome dell'utente, il nome del computer e il nome del gruppo di utenti come mostrato nella tabella seguente, evitando di usare solo un punto (.) per rappresentare il nome del computer.</p>
<div>
<table>
<colgroup>
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
<col width="20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>Scenario</p></th>
<th><p>Parametro UserName</p></th>
<th><p>Parametro UserGroup</p></th>
<th><p>Parametro ComputerName</p></th>
<th><p>Parametro ComputerGroup</p></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><p>Il server gateway è in un dominio</p></td>
<td><p><em>Nome_server</em>\<em>nome_utente</em>, Localhost\<em>nome_utente</em> o .\<em>nome_utente</em></p></td>
<td><p><em>Nome_server</em>\<em>gruppo_utenti</em>, Localhost\<em>gruppo_utenti</em> o .\<em>gruppo_utenti</em></p></td>
<td><p>Nome completo del server gateway o Localhost</p></td>
<td><p><em>Nome_server</em>\<em>gruppo_computer</em>, Localhost\<em>gruppo_computer</em> o .\<em>gruppo_computer</em></p></td>
</tr>
<tr class="even">
<td><p>Il server gateway è in un gruppo di lavoro</p></td>
<td><p><em>Nome_server</em>\<em>nome_utente</em>, Localhost\<em>nome_utente</em> o .\<em>nome_utente</em></p></td>
<td><p><em>Nome_server</em>\<em>gruppo_utenti</em>, Localhost\<em>gruppo_utenti</em> o .\<em>gruppo_utenti</em></p></td>
<td><p>Nome server</p></td>
<td><p><em>Nome_server</em>\<em>gruppo_computer</em>, Localhost\<em>gruppo_computer</em> o .\<em>gruppo_computer</em></p></td>
</tr>
</tbody>
</table>
</div>
<p>Effettuare l'accesso specificando il server gateway come computer di destinazione e utilizzando credenziali formattate in uno dei modi seguenti.</p>
<ul>
<li><p><em>Nome_server</em>\<em>nome_utente</em></p></li>
<li><p>Localhost\<em>nome_utente</em></p></li>
<li><p>.\<em>nome_utente</em></p></li>
</ul></td>
</tr>
<tr class="odd">
<td><p>In una regola di autorizzazione, al posto della sintassi <em>nome_utente</em>/<em>nome_computer</em>  viene visualizzato un ID di sicurezza (SID)</p></td>
<td><p>La regola non è più valida o la query in Servizi di dominio Active Directory non è riuscita. In genere, una regola di autorizzazione non risulta valida nel caso in cui un server gateway che in precedenza apparteneva a un gruppo di lavoro venga aggiunto a un dominio.</p></td>
</tr>
<tr class="even">
<td><p>Non è possibile accedere a un computer di destinazione che nelle regole di autorizzazione è stato specificato sotto forma di indirizzo IPv6 di dominio</p></td>
<td><p>Le regole di autorizzazione non supportano gli indirizzi IPv6 nel formato dei nomi di dominio. Per specificare un computer di destinazione tramite un indirizzo IPv6, nella regola di autorizzazione utilizzare l'indirizzo IPv6 originale, che contiene due punti (:). Sia i nomi di dominio che gli indirizzi IPv6 in formato numerico, ovvero con i due punti (:) sono supportati come nome del computer di destinazione nella pagina di accesso di Accesso Web Windows PowerShell, ma non nelle regole di autorizzazione. Per altre informazioni sugli indirizzi IPv6, vedere l'articolo <a href="https://technet.microsoft.com/library/cc781672.aspx">Funzionamento di IPv6</a>.</p></td>
</tr>
</tbody>
</table>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/dn282395(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx)
[Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx)
[about_Remote_Requirements](https://technet.microsoft.com/library/dd315349.aspx)

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

