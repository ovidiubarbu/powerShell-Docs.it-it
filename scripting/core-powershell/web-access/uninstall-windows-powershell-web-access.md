---
title:  disinstallare Accesso Web Windows PowerShell
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
---

#  Disinstallare Accesso Web Windows PowerShell

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

Seguire i passaggi indicati in questo argomento per eliminare l'applicazione e il sito Web di Accesso Web Windows PowerShell dal server gateway che esegue Windows Server 2012 R2 o Windows Server 2012. Prima di iniziare, informare gli utenti della console basata sul Web di cui si intende rimuovere il sito Web.

<a href="" id="BKMK_uninstall"></a>

------------------------------------------------------------------------

Prima di disinstallare Accesso Web Windows PowerShell dal server gateway, eseguire il cmdlet <span class="code">Uninstall-PswaWebApplication</span> per rimuovere il sito Web e le applicazioni Web di Accesso Web Windows PowerShell oppure eseguire la procedura [Per eliminare le applicazioni Web e il sito Web di Accesso Web Windows PowerShell in Gestione IIS](#BKMK_delsite).

La procedura di disinstallazione di Accesso Web Windows PowerShell non disinstalla IIS o le altre funzionalità installate automaticamente, perché sono necessarie per l'esecuzione di Accesso Web Windows PowerShell. La procedura di disinstallazione mantiene installate le funzionalità da cui dipende Accesso Web Windows PowerShell. Se necessario, è possibile disinstallare tali funzionalità separatamente.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disinstallazione consigliata (rapida)</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_1" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell con i cmdlet di Windows PowerShell.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Eliminare l'applicazione Web</span></a>

------------------------------------------------------------------------

Se è stato specificato il nome del sito Web personalizzato, aggiungere il parametro <span class="code">WebsiteName</span> al comando e specificare il nome del sito Web. Se è stata usata un'applicazione Web personalizzata (non l'applicazione predefinita, **pswa**), aggiungere il parametro <span class="code">WebApplicationName</span> al comando e specificare il nome dell'applicazione Web.

#### Per eliminare il sito Web e le applicazioni Web tramite il cmdlet Uninstall-PswaWebApplication

1.  Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.

    -   Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2.  Digitare **Uninstall-PswaWebApplication** e quindi premere **INVIO**.

3.  Se si usa un certificato di prova, aggiungere il parametro <span class="code">DeleteTestCertificate</span> al cmdlet come mostrato nell'esempio seguente.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_28147344-ab2f-49e7-b1c2-6dbe649d4366'); "Copia negli Appunti.")

        Uninstall-PswaWebApplication -DeleteTestCertificate

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Disinstallare Accesso Web Windows PowerShell</span></a>

------------------------------------------------------------------------

#### Per disinstallare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell

1.  Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni. Se è presente una sessione aperta, continuare con il passaggio successivo.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell**, quindi scegliere **Esegui come amministratore**.

2.  Digitare il codice seguente e premere **INVIO**, dove *nome_computer* rappresenta un server remoto da cui si vuole rimuovere Accesso Web Windows PowerShell. Il parametro <span class="code">–Restart</span> riavvia automaticamente i server di destinazione, se richiesto dalla procedura di rimozione.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_7b534520-f292-471f-89e3-a1079c03e369'); "Copia negli Appunti.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Per rimuovere ruoli e funzionalità da un disco rigido virtuale offline, è necessario aggiungere i parametri <span class="code">-ComputerName</span> e <span class="code">-VHD</span>. Il parametro <span class="code">-ComputerName</span> contiene il nome del server in cui montare il disco rigido virtuale e il parametro <span class="code">VHD</span> contiene il percorso del file VHD nel server specificato.

    [Copy](javascript:if%20(window.epx.codeSnippet)window.epx.codeSnippet.copyCode('CodeSnippetContainerCode_5d8f91ee-b91a-4653-b7df-e745187fd72d'); "Copia negli Appunti.")

        Uninstall-WindowsFeature –Name WindowsPowerShellWebAccess –VHD <path> -ComputerName <computer_name> -Restart

3.  Terminata la rimozione verificare che Accesso Web Windows PowerShell sia stato rimosso, aprendo la pagina **Tutti i server** in Server Manager, selezionando un server da cui è stata rimossa la funzionalità e visualizzando il riquadro **Ruoli e funzionalità** nella pagina del server selezionato. È anche possibile eseguire il cmdlet <span class="code">Get-WindowsFeature</span> indicando come destinazione il server selezionato (Get-WindowsFeature -ComputerName &lt;*nome_computer*&gt;) per visualizzare un elenco di ruoli e funzionalità installati nel server.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Disinstallazione personalizzata</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_2" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell usando la Rimozione guidata ruoli e funzionalità in Server Manager e la console Gestione IIS.

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 1: Eliminare l'applicazione Web</span></a>

------------------------------------------------------------------------

#### Per eliminare le applicazioni Web e il sito Web di Accesso Web Windows PowerShell tramite Gestione IIS

1.  Aprire la console Gestione IIS eseguendo una delle operazioni seguenti. Se è già aperta, continuare con il passaggio successivo.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.

    -   Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**. Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

2.  Nel riquadro dell'albero di Gestione IIS selezionare il sito Web che esegue l'applicazione Web Accesso Web Windows PowerShell.

3.  Nel riquadro **Azioni**, in **Gestisci sito Web** fare clic su **Arresta**.

4.  Nel riquadro dell'albero fare clic con il pulsante destro del mouse sull'applicazione Web nel sito Web che esegue l'applicazione Web di Accesso Web Windows PowerShell, quindi fare clic su **Rimuovi**.

5.  Nel riquadro dell'albero selezionare **Pool di applicazioni**, selezionare la cartella del pool di applicazioni di Accesso Web Windows PowerShell, fare clic su **Arresta** nel riquadro **Azioni**, quindi fare clic su **Rimuovi** nel riquadro del contenuto.

6.  Chiudere Gestione Internet Information Services (IIS).

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
    <td><p>Durante la disinstallazione il certificato non viene eliminato. Se è stato creato un certificato autofirmato o si utilizza un certificato di prova e si desidera rimuoverlo, eliminare il certificato in Gestione IIS.</p></td>
    </tr>
    </tbody>
    </table>

###

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Passaggio 2: Disinstallare Accesso Web Windows PowerShell</span></a>

------------------------------------------------------------------------

#### Per disinstallare Accesso Web Windows PowerShell tramite Rimozione guidata ruoli e funzionalità

1.  Se Server Manager è già aperto, andare al passaggio successivo. Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.

    -   Nella schermata **Start** di Windows fare clic su **Server Manager**.

2.  Scegliere **Rimuovi ruoli e funzionalità** dal menu **Gestisci**.

3.  Nella pagina **Selezione server di destinazione** selezionare il server o il disco rigido virtuale offline da cui si vuole rimuovere la funzionalità. Per selezionare un disco rigido virtuale offline, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale. Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.

4.  Fare di nuovo clic su **Avanti** per ignorare la pagina **Rimuovi funzionalità**.

5.  Deselezionare la casella di controllo **Accesso Web Windows PowerShell** e fare clic su **Avanti**.

6.  Nella pagina **Conferma selezioni per la rimozione** fare clic su **Rimuovi**.

<a href="javascript:void(0)" class="LW_CollapsibleArea_TitleAhref" title="Collapse"><span class="cl_CollapsibleArea_expanding LW_CollapsibleArea_Img"></span><span class="LW_CollapsibleArea_Title">Vedere anche</span></a>
<a href="/en-us/library/dn282396(v=ws.11).aspx#Anchor_3" class="LW_CollapsibleArea_Anchor_Img" title="Right-click to copy and share the link for this section"></a>

------------------------------------------------------------------------

[Distribuire Accesso Web Windows PowerShell](https://technet.microsoft.com/en-us/library/hh831611(v=ws.11).aspx)
[Guida di Gestione IIS](https://technet.microsoft.com/library/cc732664.aspx)

<span>Show:</span> Inherited Protected

<span class="stdr-votetitle">Questa pagina è stata utile?</span>
Sì No

Altri suggerimenti?

<span class="stdr-count"><span class="stdr-charcnt">1500</span> caratteri rimanenti</span> Invia Ignora

<span class="stdr-thankyou">Grazie.</span> <span class="stdr-appreciate">I suggerimenti degli utenti sono importanti.</span>

[Gestisci il tuo profilo](https://social.technet.microsoft.com/profile)

|

<a href="javascript:void(0)" id="SiteFeedbackLinkOpener"><span id="FeedbackButton" class="FeedbackButton clip20x21"> <img src="https://i-technet.sec.s-msft.com/Areas/Epx/Content/Images/ImageSprite.png?v=635975720914499532" alt="Site Feedback" id="feedBackImg" class="cl_footer_feedback_icon" /> </span> Commenti e suggerimenti sul sito</a> Commenti e suggerimenti sul sito

<a href="javascript:void(0)" id="SiteFeedbackLinkCloser">x</a>

Raccontaci la tua esperienza

La pagina si è caricata velocemente?

<span> Sì<span> </span></span> <span> No<span> </span></span>

La grafica della pagina è piacevole?

<span> Sì<span> </span></span> <span> No<span> </span></span>

Altre informazioni

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

Il codice e gli script di terze parti, collegati al presente sito o a cui il sito Web fa riferimento, vengono ceduti in licenza all'utente dalle terze parti proprietarie di tale codice, non da Microsoft. Vedere le Condizioni per l'utilizzo di Ajax CDN di ASP.NET – http://www.asp.net/ajaxlibrary/CDN.ashx.
<img src="https://m.webtrends.com/dcsjwb9vb00000c932fd0rjc7_5p3t/njs.gif?dcsuri=/nojavascript&amp;WT.js=No" alt="DCSIMG" id="Img1" width="1" height="1" />



<!--HONumber=May16_HO2-->


