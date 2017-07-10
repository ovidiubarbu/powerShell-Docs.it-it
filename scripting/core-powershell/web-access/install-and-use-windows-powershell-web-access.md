---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: installare e usare accesso web windows powershell
ms.openlocfilehash: a860f7c22829da46f0458ea729fa0afd1fe4fb6f
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
<a id="install-and-use-windows-powershell-web-access" class="xliff"></a>
#  Installare e usare Accesso Web Windows PowerShell

Ultimo aggiornamento: 5 novembre 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

Introdotta per la prima volta in Windows Server® 2012, la funzionalità Accesso Web Windows PowerShell® funge da gateway di Windows PowerShell, fornendo una console di Windows PowerShell basata sul Web destinata a un computer remoto. Consente ai professionisti IT di eseguire comandi e script di Windows PowerShell da una console di Windows PowerShell in un Web browser, senza installare Windows PowerShell, software di gestione remoto o plug-in del browser nel dispositivo client. Per eseguire la console di Windows PowerShell basata sul Web sono sufficienti un gateway di Accesso Web Windows PowerShell configurato correttamente e un dispositivo client con un browser che supporta JavaScript® e accetta i cookie.

Tali dispositivi client possono essere costituiti ad esempio da computer portatili, PC non utilizzati a scopo professionale, computer in prestito, computer tablet, chioschi Web, computer che non eseguono un sistema operativo Windows e telefoni cellulari dotati di browser. I professionisti IT possono eseguire attività di gestione critiche in server Windows remoti utilizzando dispositivi che hanno accesso a una connessione Internet e a un Web browser.

Dopo avere installato e configurato correttamente il gateway, gli utenti possono accedere a una console di Windows PowerShell usando un Web browser. Aprendo il sito Web protetto di Accesso Web Windows PowerShell ed effettuando l'autenticazione, possono quindi eseguire una console di Windows PowerShell basata sul Web.

Per installare e configurare Accesso Web Windows PowerShell, è necessaria una procedura in tre passaggi:

1.  Installazione di Accesso Web Windows PowerShell

2.  Configurazione del gateway

3.  Configurazione delle regole di autorizzazione che consentono l'accesso utente alla console di Windows PowerShell basata sul Web

Prima di installare e configurare Accesso Web Windows PowerShell, è consigliabile leggere l'intera guida, che include istruzioni su come installare, proteggere e disinstallare Accesso Web Windows PowerShell. L'argomento [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx) illustra il modo in cui l'utente accede alla console basata sul Web e descrive le limitazioni e le differenze tra la console di Windows PowerShell basata sul Web e la console di **powershell.exe**. Gli utenti finali della console basata sul Web devono leggere l'argomento [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx), ma possono evitare di leggere il resto della guida.

Questo articolo non fornisce indicazioni dettagliate sulle operazioni nel server Web (IIS), ma illustra solo le procedure necessarie per configurare il gateway di Accesso Web Windows PowerShell come illustrato nell'argomento. Per altre informazioni sulla configurazione e la protezione dei siti Web in IIS, consultare le risorse della documentazione di IIS indicate nella sezione Vedere anche.

Il diagramma seguente mostra come funziona Accesso Web Windows PowerShell.

<span><img src="https://i-technet.sec.s-msft.com/dynimg/IC564303.jpeg" title="Windows PowerShell Web Access diagram" alt="Windows PowerShell Web Access diagram" id="ee15fa8f-ce13-49e5-933d-514f6d60a2b1" /></span>

In questo argomento

-   [Requisiti per l'esecuzione di Accesso Web Windows PowerShell](#BKMK_reqs)

-   [Browser e dispositivi client supportati](#BKMK_browser)

-   [Distribuzione consigliata (rapida)](#BKMK_recm)

-   [Distribuzione personalizzata](#BKMK_custom)

-   [Configurare un certificato autentico](#BKMK_configcert)

<a href="" id="BKMK_reqs"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisiti per l'esecuzione di Accesso Web Windows PowerShell</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_0" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Accesso Web Windows PowerShell richiede il server Web (IIS), .NET Framework 4.5 e Windows PowerShell 3.0 o 4.0 in esecuzione nel server in cui si vuole eseguire il gateway. È possibile installare Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager o i cmdlet di distribuzione di Windows PowerShell per Server Manager. Se si installa Accesso Web Windows PowerShell con Server Manager o i relativi cmdlet di distribuzione, le funzionalità e ruoli necessari vengono aggiunti automaticamente durante il processo di installazione.

Accesso Web Windows PowerShell consente agli utenti remoti di accedere ai computer dell'organizzazione usando Windows PowerShell in un Web browser. Anche se Accesso Web Windows PowerShell è uno strumento di gestione pratico e potente, l'accesso basato sul Web costituisce un potenziale rischio per la sicurezza e deve essere configurato nel modo più sicuro possibile. Per la configurazione del gateway di Accesso Web Windows PowerShell si consiglia di usare tutti i livelli di sicurezza disponibili, ovvero sia le regole di autorizzazione basate su cmdlet incluse in Accesso Web Windows PowerShell, sia i livelli di sicurezza disponibili nel server Web (IIS) e nelle applicazioni di terze parti. Nel presente documento sono illustrati sia esempi non sicuri, da utilizzare solo negli ambienti di test, sia esempi di configurazione consigliati per le distribuzioni sicure.

<a href="" id="BKMK_browser"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser e dispositivi client supportati</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Accesso Web Windows PowerShell supporta i browser Internet seguenti. Anche se i browser per dispositivi mobili non sono ufficialmente supportati, molti potrebbero essere in grado di eseguire la console di Windows PowerShell basata sul Web. Anche gli altri browser che accettano cookie, eseguono JavaScript e aprono i siti Web HTTPS dovrebbero funzionare, ma non sono stati testati ufficialmente.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Browser per computer desktop supportati</span></a>

------------------------------------------------------------------------

-   Windows® Internet Explorer® per Microsoft Windows® 8.0, 9.0, 10.0 e 11.0

-   Mozilla Firefox® 10.0.2

-   Google Chrome™ 17.0.963.56m per Windows

-   Apple Safari® 5.1.2 per Windows

-   Apple Safari® 5.1.2 per Mac OS®

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Dispositivi mobili e browser sottoposti ai test minimi</span></a>

------------------------------------------------------------------------

-   Windows Phone 7 e 7.5

-   Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)

-   Apple Safari 5.0.1 per sistema operativo iPhone

-   Sistema operativo Apple Safari per iPad 2 5.0.1

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Requisiti del browser</span></a>

------------------------------------------------------------------------

Per usare la console di Accesso Web Windows PowerShell basata sul Web, i browser devono:

-   Consentire i cookie dal sito Web del gateway di Accesso Web Windows PowerShell.

-   Sia in grado di aprire e leggere le pagine HTTPS.

-   Aprire ed eseguire siti Web che usano JavaScript.

<a href="" id="BKMK_recm"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Distribuzione consigliata (rapida)</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando i cmdlet di Windows PowerShell o l'Aggiunta guidata ruoli e funzionalità aperta dall'interno di Server Manager. Per l'installazione e la configurazione rapide, usare i cmdlet di Windows PowerShell, come illustrato in questa sezione.

-   [Passaggio 1: Installare Accesso Web Windows PowerShell](#BKMK_step1)

-   [Passaggio 2: Configurare il gateway](#BKMK_step2)

-   [Passaggio 3: Configurare una regola di autorizzazione restrittiva](#BKMK_step3)

<a href="" id="BKMK_step1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Installare Accesso Web Windows PowerShell</span></a>

------------------------------------------------------------------------

<a id="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets" class="xliff"></a>
#### Per installare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell

1.  Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

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
    <td><p>In Windows PowerShell 3.0 e 4.0 non è necessario importare il modulo dei cmdlet di Server Manager nella sessione di Windows PowerShell prima di eseguire i cmdlet che fanno parte di questo modulo. Un modulo viene importato automaticamente alla prima esecuzione di un cmdlet che fa parte del modulo. Inoltre, per i cmdlet di Windows PowerShell non viene fatta distinzione tra maiuscole e minuscole.</p></td>
    </tr>
    </tbody>
    </table>

2.  Digitare il codice seguente, in cui *nome_computer* rappresenta un computer remoto in cui si vuole installare Accesso Web Windows PowerShell, se applicabile, quindi premere **INVIO**. Il parametro <span class="code">Restart</span> riavvia automaticamente i server di destinazione, se necessario.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_374a9c21-4f6e-471e-b957-bb190a594533'); "Copia negli Appunti.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart

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
    <td><p>Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell, gli strumenti di gestione del server Web (IIS) non vengono installati per impostazione predefinita. Per installare gli strumenti di gestione nello stesso server che ospita il gateway di Accesso Web Windows PowerShell, aggiungere il parametro <span class="code">IncludeManagementTools</span> al comando di installazione, come specificato in questo passaggio. Se il sito Web di Accesso Web Windows PowerShell deve essere gestito da un computer remoto, installare lo snap-in Gestione IIS installando <a href="http://go.microsoft.com/fwlink/?LinkID=304145">Strumenti di amministrazione remota del server per Windows 8.1</a> o <a href="http://go.microsoft.com/fwlink/p/?LinkID=238560">Strumenti di amministrazione remota del server per Windows 8</a> nel computer da cui si vuole gestire il gateway.</p></td>
    </tr>
    </tbody>
    </table>

    Per installare ruoli e funzionalità in un disco rigido virtuale offline, è necessario aggiungere i parametri <span class="code">ComputerName</span> e <span class="code">VHD</span>. Il parametro <span class="code">ComputerName</span> contiene il nome del server in cui montare il disco rigido virtuale e il parametro <span class="code">VHD</span> contiene il percorso del file VHD nel server specificato.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_d841d509-347e-49d0-bf54-8d1f306bece6'); "Copia negli Appunti.")

        Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart

3.  Al termine dell'installazione verificare che Accesso Web Windows PowerShell sia stato installato nei server di destinazione eseguendo il cmdlet **Get-WindowsFeature** in un server di destinazione, all'interno di una console di Windows PowerShell aperta con diritti utente elevati. È anche possibile verificare che Accesso Web Windows PowerShell sia stato installato nella console di Server Manager selezionando un server di destinazione nella pagina **Tutti i server** e quindi visualizzando il riquadro **Ruoli e funzionalità** per il server selezionato. È anche possibile visualizzare il file Leggimi per Accesso Web Windows PowerShell.

4.  Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway. Queste istruzioni sono riportate anche nella sezione successiva, [Passaggio 2: Configurare il gateway](#BKMK_step2). Il percorso del file Leggimi è: <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.

<a href="" id="BKMK_step2"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Configurare il gateway</span></a>

------------------------------------------------------------------------

Il cmdlet **Install-PswaWebApplication** costituisce una soluzione rapida per configurare Accesso Web Windows PowerShell. Anche se è possibile aggiungere il parametro <span class="code">UseTestCertificate</span> al cmdlet <span class="code">Install-PswaWebApplication</span> per installare un certificato SSL autofirmato a scopo di test, questa configurazione non è sicura. Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'autorità di certificazione (CA). Gli amministratori possono sostituire il certificato di test con un certificato firmato a scelta, utilizzando la console Gestione IIS.

Per completare la configurazione dell'applicazione Web Accesso Web Windows PowerShell, è possibile eseguire il cmdlet <span class="code">Install-PswaWebApplication</span> o la procedura di configurazione con interfaccia grafica in Gestione IIS. Per impostazione predefinita, il cmdlet installa l'applicazione Web **pswa** e il relativo pool di applicazioni **pswa_pool**, nel contenitore **Sito Web predefinito** visualizzato in Gestione IIS. Facoltativamente, è possibile indicare al cmdlet di cambiare il contenitore del sito predefinito dell'applicazione Web. In Gestione IIS sono disponibili varie opzioni per la configurazione delle applicazioni Web, ad esempio per cambiare il numero di porta o il certificato SSL (Secure Sockets Layer).

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
<td><p>Si consiglia agli amministratori di configurare il gateway in modo che utilizzi un certificato valido firmato da una CA.</p></td>
</tr>
</tbody>
</table>

-   [Per configurare il gateway di Accesso Web Windows PowerShell con un certificato di test tramite Install-PswaWebApplication](#BKMK_testcert)

-   [Per configurare il gateway di Accesso Web Windows PowerShell con un certificato autentico tramite Install-PswaWebApplication e Gestione IIS](#BKMK_gencert)

<a id="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication" class="xliff"></a>
#### Per configurare il gateway di Accesso Web Windows PowerShell con un certificato di test tramite Install-PswaWebApplication

1.  Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.

    -   Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2.  Digitare il comando seguente e quindi premere **INVIO**.

    **Install-PswaWebApplication -UseTestCertificate**

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
    <td><p>Usare il parametro <span class="code">UseTestCertificate</span> esclusivamente in un ambiente di test privato. Per un ambiente di produzione sicuro è consigliabile utilizzare un certificato valido firmato da una CA.</p></td>
    </tr>
    </tbody>
    </table>

    Eseguendo il cmdlet si installa l'applicazione Web Accesso Web Windows PowerShell nel contenitore di IIS Sito Web predefinito. Il cmdlet crea l'infrastruttura necessaria per eseguire Accesso Web Windows PowerShell nel sito Web predefinito, ovvero https://&lt;nome_server&gt;/pswa. Per installare l'applicazione Web in un altro sito Web, specificare il nome del sito Web aggiungendo il parametro <span class="code">WebSiteName</span>. Per modificare il nome dell'applicazione Web che per impostazione predefinita è <span class="code">pswa</span>, aggiungere il parametro <span class="code">WebApplicationName</span>.

    Durante l'esecuzione del cmdlet vengono configurate le impostazioni seguenti. Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS.

    -   Percorso: /pswa

    -   ApplicationPool: pswa_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

    <span class="label">Esempio:</span> <span class="code">Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate</span>

    In questo esempio l'indirizzo del sito Web di Accesso Web Windows PowerShell risultante è https://&lt; *nome_server*&gt;/myWebApp.

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
    <td><p>Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere <a href="#BKMK_step3">Passaggio 3: Configurare una regola di autorizzazione restrittiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a>.</p></td>
    </tr>
    </tbody>
    </table>

<a id="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager" class="xliff"></a>
#### Per configurare il gateway di Accesso Web Windows PowerShell con un certificato autentico tramite Install-PswaWebApplication e Gestione IIS

1.  Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.

    -   Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2.  Digitare il comando seguente e quindi premere **INVIO**.

    **Install-PswaWebApplication**

    Durante l'esecuzione del cmdlet vengono configurate le seguenti impostazioni del gateway. Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS. È anche possibile specificare i valori per i parametri <span class="code">WebsiteName</span> e <span class="code">WebApplicationName</span> del cmdlet <span class="code">Install-PswaWebApplication</span>.

    -   Percorso: /pswa

    -   ApplicationPool: pswa_pool

    -   EnabledProtocols: http

    -   PhysicalPath: %*windir*%/Web/PowerShellWebAccess/wwwroot

3.  Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.

    -   Nella schermata **Start** di Windows fare clic su **Server Manager**.

4.  Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Espandere la cartella **Siti**.

5.  Selezionare il sito Web in cui è stata installata l'applicazione Web Accesso Web Windows PowerShell. Nel riquadro **Azioni** fare clic su **Binding**.

6.  Nella finestra di dialogo **Binding sito** fare clic su **Aggiungi**.

7.  Nella finestra di dialogo **Aggiungi binding sito** selezionare **https** nel campo **Tipo**.

8.  Nel campo **Certificato SSL** selezionare il certificato firmato dal menu a discesa. Fare clic su **OK**. Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.

    L'applicazione Web Accesso Web Windows PowerShell ora è configurata per usare il certificato SSL firmato. Per accedere a Accesso Web Windows PowerShell è possibile aprire https://&lt;nome_server&gt;/pswa in una finestra del browser.

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
    <td><p>Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere <a href="#BKMK_step3">Passaggio 3: Configurare una regola di autorizzazione restrittiva</a> e <a href="https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx">Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell</a>.</p></td>
    </tr>
    </tbody>
    </table>

<a href="" id="BKMK_step3"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 3: Configurare una regola di autorizzazione restrittiva</span></a>

------------------------------------------------------------------------

Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso. Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente. Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione. Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).

Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).

<a id="to-add-a-restrictive-authorization-rule" class="xliff"></a>
#### Per aggiungere una regola di autorizzazione restrittiva

1.  Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

2.  <span class="label">Passaggio facoltativo per la limitazione dell'accesso utente con configurazioni di sessione:</span> verificare che le configurazioni di sessione da usare nelle proprie regole esistano già. Se non sono ancora state create, utilizzare le istruzioni per la creazione di configurazioni di sessione disponibili nell'articolo [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) di MSDN.

3.  Digitare il comando seguente e quindi premere **INVIO**.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_f9e7959b-75d0-4d63-8f8e-02334a8dd09d'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente, tramite una specifica configurazione di sessione con ambito limitato alle esigenze tipiche di utilizzo di script e cmdlet dell'utente. Nell'esempio seguente, a un utente di nome <span class="code">JSmith</span> nel dominio <span class="code">Contoso</span> viene consentito l'accesso per la gestione del computer <span class="code">Contoso_214</span>, con una configurazione di sessione denominata <span class="code">NewAdminsOnly</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ebd5bc5e-ec5d-4955-a86a-63843e480e37'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;. Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.

Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.

<a href="" id="BKMK_custom"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Distribuzione personalizzata</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager. Dopo l'installazione di Accesso Web Windows PowerShell, è possibile personalizzare la configurazione del gateway in Gestione IIS.

<a href="" id="BKMK_custom1"></a>
###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Installare Accesso Web Windows PowerShell</span></a>

------------------------------------------------------------------------

<a id="to-install-windows-powershell-web-access-by-using-the-add-roles-and-features-wizard" class="xliff"></a>
#### Per installare Accesso Web Windows PowerShell tramite Aggiunta guidata ruoli e funzionalità

1.  Se Server Manager è già aperto, andare al passaggio successivo. Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.

    -   Nella schermata **Start** di Windows fare clic su **Server Manager**.

2.  Scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

3.  Nella pagina **Selezione tipo di installazione** selezionare **Installazione basata su ruoli o basata su funzionalità**. Fare clic su **Avanti**.

4.  Nella pagina **Selezione server di destinazione** scegliere un server dal pool di server oppure selezionare un disco rigido virtuale offline. Per selezionare un disco rigido virtuale offline come server di destinazione, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale. Per informazioni su come aggiungere server al pool di server, vedere la Guida di Server Manager. Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.

5.  Nella pagina **Selezione funzionalità** della procedura guidata espandere **Windows PowerShell**e selezionare **Accesso Web Windows PowerShell**.

6.  Viene richiesto di aggiungere le funzionalità necessarie, quali .NET Framework 4.5 e i servizi ruolo del server Web (IIS). Aggiungere le funzionalità necessarie e continuare.

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
    <td><p>Se si installa Accesso Web Windows PowerShell usando l'Aggiunta guidata ruoli e funzionalità, viene installato anche il server Web (IIS), che include lo snap-in Gestione IIS. Se si usa l'Aggiunta guidata ruoli e funzionalità, lo snap-in e gli altri strumenti di gestione di IIS vengono installati per impostazione predefinita. Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell come illustrato nella procedura seguente, gli strumenti di gestione non vengono aggiunti per impostazione predefinita.</p></td>
    </tr>
    </tbody>
    </table>

7.  Se i file delle funzionalità di Accesso Web Windows PowerShell non sono archiviati nel server di destinazione selezionato nel passaggio 4, nella pagina **Conferma selezioni per l'installazione** fare clic su **Specificare un percorso di origine alternativo** e immettere il percorso dei file delle funzionalità. In caso contrario, fare clic su **Installa**.

8.  Dopo aver fatto clic su **Installa**, la pagina **Stato dell'installazione** visualizza lo stato dell'installazione, i risultati e messaggi quali avvisi, errori o procedure di configurazione successive all'installazione necessarie per Accesso Web Windows PowerShell. Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway. Le istruzioni sono incluse anche in questo argomento. Il percorso del file Leggimi è: <span class="computerOutputInline">C:\\Windows\\Web\\PowerShellWebAccess\\wwwroot\\README.txt</span>.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Configurare il gateway</span></a>

------------------------------------------------------------------------

Le istruzioni in questa sezione mostrano come installare l'applicazione Web Accesso Web Windows PowerShell in una sottodirectory del sito Web, anziché nella directory radice. Viene usata una procedura con interfaccia grafica equivalente alle operazioni eseguite dal cmdlet <span class="code">Install-PswaWebApplication</span>. Questa sezione include anche le istruzioni su come usare Gestione IIS per configurare il gateway di Accesso Web Windows PowerShell come sito Web radice.

-   [Per usare Gestione IIS per configurare il gateway in un sito Web esistente](#BKMK_configman)

-   [Per usare Gestione IIS per configurare il gateway come sito Web radice con un certificato di test](#BKMK_configroot)

-   

<a id="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website" class="xliff"></a>
#### Per utilizzare Gestione IIS per configurare il gateway in un sito Web esistente

1.  Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.

    -   Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**. Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

2.  Creare un nuovo pool di applicazioni per Accesso Web Windows PowerShell. Espandere il nodo del server gateway nel riquadro dell'albero di Gestione IIS, selezionare **Pool di applicazioni** e fare clic su **Aggiungi pool di applicazioni** nel riquadro **Azioni**.

3.  Aggiungere un nuovo pool di applicazioni con il nome **pswa_pool**o specificare un altro nome. Fare clic su **OK**.

4.  Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Selezionare la cartella **Siti**.

5.  Fare clic con il pulsante destro del mouse sul sito Web, ad esempio **Sito Web predefinito**, a cui si vuole aggiungere il sito Web di Accesso Web Windows PowerShell e quindi fare clic su **Aggiungi applicazione**.

6.  Nel campo **Alias** digitare pswa o specificare un altro alias. L'alias determina il nome della directory virtuale. Ad esempio, nell'URL seguente **pswa** corrisponde all'alias specificato in questo passaggio: https://&lt;nome_server&gt;/pswa.

7.  Nel campo **Pool di applicazioni** selezionare il pool di applicazioni creato nel passaggio 3.

8.  Nel campo **Percorso fisico** cercare e selezionare il percorso dell'applicazione. È possibile utilizzare il percorso predefinito, ovvero %windir%/Web/PowerShellWebAccess/wwwroot. Fare clic su **OK**.

9.  Eseguire i passaggi illustrati nella procedura [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.

10. <span class="label">Passaggio di sicurezza facoltativo:</span> Con il sito Web selezionato nel riquadro dell'albero, fare doppio clic su **Impostazioni SSL** nel riquadro del contenuto. Selezionare **Richiedi SSL**, quindi fare clic su **Applica** nel riquadro **Azioni**. Facoltativamente, nel riquadro **Impostazioni SSL** è possibile richiedere l'uso di certificati client da parte degli utenti che si connettono al sito Web di Accesso Web Windows PowerShell. Un certificato client consente di verificare l'identità dell'utente di un dispositivo client. Per altre informazioni su come aumentare la sicurezza di Accesso Web Windows PowerShell richiedendo i certificati client, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx) in questa guida.

11. Aprire una sessione del browser in un dispositivo client. Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#BKMK_browser) in questo argomento.

12. Aprire il nuovo sito Web di Accesso Web Windows PowerShell, https://&lt;*nome_server_gateway*&gt;/pswa.

    Il browser dovrebbe visualizzare la pagina di accesso della console di Accesso Web Windows PowerShell.

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
    <td><p>Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</p></td>
    </tr>
    </tbody>
    </table>

13. In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui *nome_pool_applicazioni* rappresenta il nome del pool di applicazioni creato nel passaggio 3, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_c1a80a93-8fcf-4beb-a025-5f81bfb8bdae'); "Copia negli Appunti.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_ac2179c2-9548-4a17-8663-267fdd105380'); "Copia negli Appunti.")

        c:\windows\system32\icacls.exe $authorizationFile

<a id="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate" class="xliff"></a>
#### Per usare Gestione IIS per configurare il gateway come sito Web radice con un certificato di test

1.  Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.

    -   Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**. Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

2.  Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Selezionare la cartella **Siti**.

3.  Nel riquadro **Azioni** fare clic su **Aggiungi sito Web**.

4.  Digitare il nome del sito Web, ad esempio **Accesso Web Windows PowerShell**.

5.  Per il nuovo sito Web viene automaticamente creato un pool di applicazioni. Per utilizzare un pool di applicazioni diverso, fare clic su **Seleziona** per selezionare il pool di applicazioni da associare al nuovo sito Web. Selezionare il pool di applicazioni alternativo nella finestra di dialogo **Seleziona pool di applicazioni** , quindi fare clic su **OK**.

6.  Nella casella di testo **Percorso fisico** accedere a %*windir*%/Web/PowerShellWebAccess/wwwroot.

7.  Nel campo **Tipo** dell'area **Binding** selezionare **https**.

8.  Assegnare al sito Web un numero di porta che non sia già in uso da un altro sito o applicazione. Per individuare le porte aperte, è possibile eseguire il comando **netstat** in una finestra del prompt dei comandi. Il numero di porta predefinito è 443.

    Cambiare la porta predefinita se un altro sito Web sta già utilizzando la porta 443 o esistono altri motivi di sicurezza per cambiare il numero di porta. Se la porta selezionata viene usata da un altro sito Web in esecuzione nel server gateway, quando si fa clic su **OK** nella finestra di dialogo **Aggiungi sito Web** viene visualizzato un avviso. Per eseguire Accesso Web Windows PowerShell è necessaria una porta inutilizzata.

9.  Facoltativamente, se è necessario per l'organizzazione, specificare un nome host significativo per l'organizzazione e gli utenti, ad esempio **www.contoso.com**. Fare clic su **OK**.

10. Per un ambiente di produzione più sicuro, è consigliabile specificare un certificato valido firmato da una CA. È necessario fornire un certificato SSL perché gli utenti possono connettersi a Accesso Web Windows PowerShell solo con un sito Web HTTPS. Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#BKMK_cert) in questo argomento.

11. Fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi sito Web**.

12. In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui *nome_pool_applicazioni* rappresenta il nome del pool di applicazioni creato nel passaggio 4, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_35ae9944-ca44-4af7-9c96-616083b3e3db'); "Copia negli Appunti.")

        $applicationPoolName = "<application_pool_name>"
        $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
        c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null

    Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_0eb6d70a-2807-498b-b088-fa5233ed68d5'); "Copia negli Appunti.")

        c:\windows\system32\icacls.exe $authorizationFile

13. Con il nuovo sito Web selezionato nel riquadro dell'albero di Gestione IIS, fare clic su **Avvia** nel riquadro **Azioni** per avviare il sito Web.

14. Aprire una sessione del browser in un dispositivo client. Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#BKMK_browser) in questo documento.

15. Aprire il nuovo sito Web di Accesso Web Windows PowerShell.

    Il sito Web radice punta alla cartella Accesso Web Windows PowerShell, quindi il browser dovrebbe visualizzare la pagina di accesso di Accesso Web Windows PowerShell quando si apre https://&lt;*nome_server_gateway*&gt;. Non è necessario aggiungere **/pswa** all'URL.

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
    <td><p>Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 3: Configurare una regola di autorizzazione restrittiva</span></a>

------------------------------------------------------------------------

Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso. Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente. Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione. Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](https://technet.microsoft.com/library/hh918342.aspx).

Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/dn282394(v=ws.11).aspx).

<a id="to-add-a-restrictive-authorization-rule" class="xliff"></a>
#### Per aggiungere una regola di autorizzazione restrittiva

1.  Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

2.  <span class="label">Passaggio facoltativo per la limitazione dell'accesso utente con configurazioni di sessione:</span> verificare che le configurazioni di sessione da usare nelle proprie regole esistano già. Se non sono ancora state create, utilizzare le istruzioni per la creazione di configurazioni di sessione disponibili nell'articolo [about_Session_Configuration_Files](https://msdn.microsoft.com/library/windows/desktop/hh847838.aspx) di MSDN.

3.  Digitare il comando seguente e quindi premere **INVIO**.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_4df22c91-f56f-4bb5-91e7-99f9b365ed5d'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>

    Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente, tramite una specifica configurazione di sessione con ambito limitato alle esigenze tipiche di utilizzo di script e cmdlet dell'utente. Nell'esempio seguente, a un utente di nome <span class="code">JSmith</span> nel dominio <span class="code">Contoso</span> viene consentito l'accesso per la gestione del computer <span class="code">Contoso_214</span>, con una configurazione di sessione denominata <span class="code">NewAdminsOnly</span>.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_efc3999a-2905-453f-86cd-014b41658ffc'); "Copia negli Appunti.")

        Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly

4.  Per verificare che la regola sia stata creata, eseguire il cmdlet **Get-PswaAuthorizationRule** o **Test-PswaAuthorizationRule -UserName &lt;dominio\\utente | computer\\utente&gt; -ComputerName** &lt;nome_computer&gt;. Ad esempio, **Test-PswaAuthorizationRule -UserName Contoso\\JSmith -ComputerName Contoso_214**.

Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.

<a href="" id="BKMK_configcert"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Configurare un certificato autentico</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_4" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'Autorità di certificazione (CA). La procedura descritta in questa sezione illustra come ottenere e applicare un certificato SSL valido da un'Autorità di certificazione.

<a id="to-configure-an-ssl-certificate-in-iis-manager" class="xliff"></a>
### Per configurare un certificato SSL in Gestione IIS

1.  Nel riquadro dell'albero di Gestione IIS selezionare il server in cui è installato Accesso Web Windows PowerShell.

2.  Nel riquadro del contenuto fare doppio clic su **Certificati server**.

3.  Nel riquadro **Azioni** eseguire una delle operazioni seguenti. Per altre informazioni sulla configurazione di certificati server in IIS, vedere [Configurazione dei certificati del server in IIS 7](https://technet.microsoft.com/library/cc732230.aspx).

    -   Fare clic su **Importa** per importare un certificato valido esistente da un percorso della rete aziendale.

    -   Fare clic su **Crea richiesta di certificato** per richiedere un certificato a una CA quale VeriSign™, Thawte o GeoTrust®. Il nome comune del certificato deve corrispondere all'intestazione host nella richiesta. Se ad esempio il browser client richiede http://www.contoso.com/, anche il nome comune deve essere http://www.contoso.com/. Questa è l'opzione più sicura, e quindi consigliata, per fornire un certificato al gateway di Accesso Web Windows PowerShell.

    -   Fare clic su **Crea un certificato autofirmato** per creare un certificato da usare immediatamente e, se necessario, far firmare a una CA in un secondo momento. Specificare un nome descrittivo per il certificato autofirmato, ad esempio **Accesso Web Windows PowerShell**. Questa opzione non è considerata sicura ed è consigliabile utilizzarla solo per un ambiente di test privato.

4.  Dopo avere ottenuto o creato un certificato, selezionare il sito Web a cui è applicato (ad esempio **Sito Web predefinito**) nel riquadro dell'albero di Gestione IIS, quindi fare clic su **Binding** nel riquadro **Azioni** .

5.  Nella finestra di dialogo **Aggiungi binding sito** aggiungere un binding **https** al sito, se non è già visualizzato. Se non si utilizza un certificato autofirmato, specificare il nome host del passaggio 3 di questa procedura. Se si utilizza un certificato autofirmato, questo passaggio non è necessario.

6.  Selezionare il certificato ottenuto o creato nel passaggio 3 di questa procedura e quindi fare clic su **OK**.

<a href="" id="BKMK_using"></a>

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Uso della console di Windows PowerShell basata sul Web</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_5" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Dopo avere installato Accesso Web Windows PowerShell e completato la configurazione del gateway come illustrato in questo argomento, la console di Windows PowerShell basata sul Web è pronta all'uso. Per altre informazioni su come iniziare a usare la console basata sul Web, vedere [Usare la console di Windows PowerShell basata sul Web](https://technet.microsoft.com/en-us/library/hh831417(v=ws.11).aspx).

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/hh831611(v=ws.11).aspx#Anchor_6" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Internet Information Services (IIS) 7.0 Documentation (Documentazione di Internet Information Services (IIS) 7.0)](https://technet.microsoft.com/library/cc753433.aspx)
[IIS Manager 7.0 Help (Guida di Gestione IIS 7.0)](https://technet.microsoft.com/library/cc732664.aspx)
[Configure Web Server Security (IIS 7) (Configurare la sicurezza del server Web (IIS 7))](https://technet.microsoft.com/library/cc731278.aspx)
[IPsec Deployment Resources (Risorse sulla distribuzione di IPsec)](https://technet.microsoft.com/network/bb531150)

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

