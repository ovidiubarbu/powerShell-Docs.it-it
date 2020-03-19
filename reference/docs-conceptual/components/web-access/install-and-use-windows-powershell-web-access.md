---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: installare e usare accesso web windows powershell
ms.openlocfilehash: a3207c859c4b93b07d4c1b41d7df5269daa39a7d
ms.sourcegitcommit: c97dcf1e00ef540e7464c36c88f841474060044c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2020
ms.locfileid: "79402618"
---
# <a name="install-and-use-windows-powershell-web-access"></a>Installare e usare Accesso Web Windows PowerShell

Aggiornamento: 5 novembre 2013 (Data di modifica: 23 agosto 2017)

Si applica a: Windows Server 2012 R2, Windows Server 2012

## <a name="introduction"></a>Introduzione

La funzionalità Accesso Web Windows PowerShell, introdotta per la prima volta in Windows Server 2012, funge da gateway di Windows PowerShell e offre una console di Windows PowerShell basata sul Web destinata a un computer remoto. Consente ai professionisti IT di eseguire comandi e script di Windows PowerShell da una console di Windows PowerShell in un Web browser, senza installare Windows PowerShell, software di gestione remoto o plug-in del browser nel dispositivo client. Per eseguire la console di Windows PowerShell basata sul Web sono sufficienti un gateway di Accesso Web Windows PowerShell configurato correttamente e un dispositivo client con un browser che supporta JavaScript e accetta i cookie.

Tali dispositivi client possono essere costituiti ad esempio da computer portatili, PC non utilizzati a scopo professionale, computer in prestito, computer tablet, chioschi Web, computer che non eseguono un sistema operativo Windows e telefoni cellulari dotati di browser. I professionisti IT possono eseguire attività di gestione critiche in server Windows remoti utilizzando dispositivi che hanno accesso a una connessione Internet e a un Web browser.

Dopo avere installato e configurato correttamente il gateway, gli utenti possono accedere a una console di Windows PowerShell usando un Web browser. Aprendo il sito Web protetto di Accesso Web Windows PowerShell ed effettuando l'autenticazione, possono quindi eseguire una console di Windows PowerShell basata sul Web.

Per installare e configurare Accesso Web Windows PowerShell, è necessaria una procedura in tre passaggi:

1. [Installare Accesso Web Windows PowerShell](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurare il gateway](#configure-the-gateway)
1. [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule)

Prima di installare e configurare Accesso Web Windows PowerShell, è consigliabile leggere l'intera guida, che include istruzioni su come installare, proteggere e disinstallare Accesso Web Windows PowerShell. L'argomento [Usare la console di Windows PowerShell basata sul Web](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831417(v=ws.11)) illustra il modo in cui l'utente accede alla console basata sul Web e descrive le limitazioni e le differenze tra la console di Windows PowerShell basata sul Web e la console di **powershell.exe**. Gli utenti finali della console basata sul Web devono leggere l'argomento [Usare la console di Windows PowerShell basata sul Web](use-the-web-based-windows-powershell-console.md), ma possono evitare di leggere il resto della guida.

Questo argomento non offre informazioni dettagliate sulle operazioni eseguite nel server Web IIS, ma illustra solo le procedure necessarie per configurare il gateway di Accesso Web Windows PowerShell come indicato nell'argomento. Per altre informazioni sulla configurazione e la protezione dei siti Web in IIS, consultare le risorse della documentazione di IIS indicate nella sezione Vedere anche.

Il diagramma seguente mostra come funziona Accesso Web Windows PowerShell.

![Diagramma di Accesso Web Windows PowerShell](media/install-and-use-windows-powershell-web-access/Windows-PowerShell-Web-Access-diagram.jpg)

## <a name="requirements-for-running-windows-powershell-web-access"></a>Requisiti per l'esecuzione di Accesso Web Windows PowerShell

Accesso Web Windows PowerShell richiede il server Web (IIS), .NET Framework 4.5 e Windows PowerShell 3.0 o 4.0 in esecuzione nel server in cui si vuole eseguire il gateway. È possibile installare Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager o i cmdlet di distribuzione di Windows PowerShell per Server Manager. Se si installa Accesso Web Windows PowerShell con Server Manager o i relativi cmdlet di distribuzione, le funzionalità e ruoli necessari vengono aggiunti automaticamente durante il processo di installazione.

Accesso Web Windows PowerShell consente agli utenti remoti di accedere ai computer dell'organizzazione usando Windows PowerShell in un Web browser. Anche se Accesso Web Windows PowerShell è uno strumento di gestione pratico e potente, l'accesso basato sul Web costituisce un potenziale rischio per la sicurezza e deve essere configurato nel modo più sicuro possibile. Per la configurazione del gateway di Accesso Web Windows PowerShell si consiglia di usare tutti i livelli di sicurezza disponibili, ovvero sia le regole di autorizzazione basate su cmdlet incluse in Accesso Web Windows PowerShell, sia i livelli di sicurezza disponibili nel server Web (IIS) e nelle applicazioni di terze parti. Nel presente documento sono illustrati sia esempi non sicuri, da utilizzare solo negli ambienti di test, sia esempi di configurazione consigliati per le distribuzioni sicure.

## <a name="browser-and-client-device-support"></a>Browser e dispositivi client supportati

Accesso Web Windows PowerShell supporta i browser Internet seguenti. Anche se i browser per dispositivi mobili non sono ufficialmente supportati, molti potrebbero essere in grado di eseguire la console di Windows PowerShell basata sul Web.
Anche gli altri browser che accettano cookie, eseguono JavaScript e aprono i siti Web HTTPS dovrebbero funzionare, ma non sono stati testati ufficialmente.

### <a name="supported-desktop-computer-browsers"></a>Browser per computer desktop supportati

- Windows Internet Explorer per Microsoft Windows 8.0, 9.0, 10.0 e 11.0
- Mozilla Firefox 10.0.2
- Google Chrome 17.0.963.56m per Windows
- Apple Safari 5.1.2 per Windows
- Apple Safari 5.1.2 per Mac OS

### <a name="minimally-tested-mobile-devices-or-browsers"></a>Dispositivi mobili e browser sottoposti ai test minimi

- Windows Phone 7 e 7.5
- Google Android WebKit 3.1 Browser Android 2.2.1 (Kernel 2.6)
- Apple Safari 5.0.1 per sistema operativo iPhone
- Apple Safari 5.0.1 per sistema operativo iPad 2

### <a name="browser-requirements"></a>Requisiti del browser

Per usare la console di Accesso Web Windows PowerShell basata sul Web, i browser devono:

- Consentire i cookie dal sito Web del gateway di Accesso Web Windows PowerShell.
- Sia in grado di aprire e leggere le pagine HTTPS.
- Aprire ed eseguire siti Web che usano JavaScript.

## <a name="recommended-quick-deployment"></a>Distribuzione rapida consigliata

È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando i cmdlet di Windows PowerShell o l'Aggiunta guidata ruoli e funzionalità aperta dall'interno di Server Manager. Per l'installazione e la configurazione rapide, usare i cmdlet di Windows PowerShell, come illustrato in questa sezione.

1. [Installare Accesso Web Windows PowerShell](#install-windows-powershell-web-access-using-powershell-cmdlets)
1. [Configurare il gateway](#configure-the-gateway)
1. [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule)

### <a name="install-windows-powershell-web-access-using-powershell-cmdlets"></a>Installare Accesso Web Windows PowerShell usando cmdlet di PowerShell

#### <a name="to-install-windows-powershell-web-access-by-using-windows-powershell-cmdlets"></a>Per installare Accesso Web Windows PowerShell tramite i cmdlet di Windows PowerShell

1. Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

   - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.
   - Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

   > [!NOTE]
   > In Windows PowerShell 3.0 e 4.0 non è necessario importare il modulo dei cmdlet di Server Manager nella sessione di Windows PowerShell prima di eseguire i cmdlet che fanno parte di questo modulo. Un modulo viene importato automaticamente alla prima esecuzione di un cmdlet che fa parte del modulo.
   > Inoltre, per i cmdlet di Windows PowerShell non viene fatta distinzione tra maiuscole e minuscole.

1. Digitare il codice seguente, in cui *nome_computer* rappresenta un computer remoto in cui si vuole installare Accesso Web Windows PowerShell, se applicabile, quindi premere **INVIO**. Il parametro `-Restart` consente di riavviare automaticamente i server di destinazione se necessario.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -IncludeManagementTools -Restart`

   > [!NOTE]
   > Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell, gli strumenti di gestione del server Web (IIS) non vengono installati per impostazione predefinita. Per installare gli strumenti di gestione nello stesso server che ospita il gateway di Accesso Web Windows PowerShell, aggiungere il parametro `-IncludeManagementTools` al comando di installazione, come specificato in questo passaggio. Se il sito Web di Accesso Web Windows PowerShell deve essere gestito da un computer remoto, installare lo snap-in Gestione IIS installando [Strumenti di amministrazione remota del server per Windows 8.1](https://www.microsoft.com/en-us/download/details.aspx?id=39296) o [Strumenti di amministrazione remota del server per Windows 8](https://www.microsoft.com/en-us/download/details.aspx?id=28972) nel computer da cui si vuole gestire il gateway.

   Per installare ruoli e funzionalità in un disco rigido virtuale offline, è necessario aggiungere i parametri `-ComputerName` e `-VHD`. Il parametro `-ComputerName` contiene il nome del server in cui montare il disco rigido virtuale e il parametro `-VHD` contiene il percorso del file VHD nel server specificato.

   `Install-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -IncludeManagementTools -Restart`

1. Al termine dell'installazione verificare che Accesso Web Windows PowerShell sia stato installato nei server di destinazione eseguendo il cmdlet `Get-WindowsFeature` in un server di destinazione, all'interno di una console di Windows PowerShell aperta con diritti utente elevati. È anche possibile verificare che Accesso Web Windows PowerShell sia stato installato nella console di Server Manager selezionando un server di destinazione nella pagina **Tutti i server** e quindi visualizzando il riquadro **Ruoli e funzionalità** per il server selezionato. È anche possibile visualizzare il file Leggimi per Accesso Web Windows PowerShell.

1. Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway. Queste istruzioni sono riportate anche nella sezione successiva, [Configurare il gateway](#configure-the-gateway). Il percorso del file Leggimi è `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurare il gateway

Il cmdlet **Install-PswaWebApplication** costituisce una soluzione rapida per configurare Accesso Web Windows PowerShell. Anche se è possibile aggiungere il parametro `UseTestCertificate` al cmdlet `Install-PswaWebApplication` per installare un certificato SSL autofirmato a scopo di test, questa configurazione non è sicura. Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'autorità di certificazione (CA). Gli amministratori possono sostituire il certificato di test con un certificato firmato a scelta, utilizzando la console Gestione IIS.

Per completare la configurazione dell'applicazione Web Accesso Web Windows PowerShell, è possibile eseguire il cmdlet `Install-PswaWebApplication` o la procedura di configurazione con interfaccia grafica in Gestione IIS.
Per impostazione predefinita, il cmdlet installa l'applicazione Web **pswa** e il relativo pool di applicazioni **pswa_pool**, nel contenitore **Sito Web predefinito** visualizzato in Gestione IIS. Facoltativamente, è possibile indicare al cmdlet di cambiare il contenitore del sito predefinito dell'applicazione Web. In Gestione IIS sono disponibili varie opzioni per la configurazione delle applicazioni Web, ad esempio per cambiare il numero di porta o il certificato SSL (Secure Sockets Layer).

> [!IMPORTANT]
> Si consiglia agli amministratori di configurare il gateway in modo che utilizzi un certificato valido firmato da una CA.

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-test-certificate-by-using-install-pswawebapplication"></a>Per configurare il gateway di Accesso Web Windows PowerShell con un certificato di test tramite Install-PswaWebApplication

1. Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

   - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.
   - Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2. Digitare il comando seguente e quindi premere **INVIO**.

   `Install-PswaWebApplication -UseTestCertificate`

   > [!IMPORTANT]
   > Usare il parametro `UseTestCertificate` solo in un ambiente di test privato. Per un ambiente di produzione sicuro è consigliabile utilizzare un certificato valido firmato da una CA.

   Eseguendo il cmdlet si installa l'applicazione Web Accesso Web Windows PowerShell nel contenitore di IIS Sito Web predefinito. Il cmdlet crea l'infrastruttura necessaria per eseguire Accesso Web Windows PowerShell nel sito Web predefinito, `https://<server_name>/pswa`. Per installare l'applicazione Web in un altro sito Web, specificare il nome del sito Web aggiungendo il parametro `WebSiteName`. Per modificare il nome dell'applicazione Web (che per impostazione predefinita è `pswa`), aggiungere il parametro `WebApplicationName`.

   Durante l'esecuzione del cmdlet vengono configurate le impostazioni seguenti. Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS.

   - Percorso: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

   **Esempio**: `Install-PswaWebApplication -webApplicationName myWebApp -useTestCertificate`

   In questo esempio l'indirizzo del sito Web di Accesso Web Windows PowerShell risultante è `https://<server_name>/myWebApp`.

   > [!NOTE]
   > Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule) e [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-configure-the-windows-powershell-web-access-gateway-with-a-genuine-certificate-by-using-install-pswawebapplication-and-iis-manager"></a>Per configurare il gateway di Accesso Web Windows PowerShell con un certificato autentico tramite Install-PswaWebApplication e Gestione IIS

1. Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

   - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.
   - Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2. Digitare il comando seguente e quindi premere **INVIO**.

   `Install-PswaWebApplication`

   Durante l'esecuzione del cmdlet vengono configurate le seguenti impostazioni del gateway. Se si desidera, è possibile modificare tali impostazioni manualmente nella console Gestione IIS. È anche possibile specificare i valori per i parametri `WebsiteName` e `WebApplicationName` del cmdlet `Install-PswaWebApplication`.

   - Percorso: /pswa
   - ApplicationPool: pswa_pool
   - EnabledProtocols: http
   - PhysicalPath: %windir%/Web/PowerShellWebAccess/wwwroot

3. Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

   - Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)** .
   - Nella schermata **Start** di Windows fare clic su **Server Manager**.

4. Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Espandere la cartella **Siti**.

5. Selezionare il sito Web in cui è stata installata l'applicazione Web Accesso Web Windows PowerShell.
   Nel riquadro **Azioni** fare clic su **Binding**.

6. Nella finestra di dialogo **Binding sito** fare clic su **Aggiungi**.

7. Nella finestra di dialogo **Aggiungi binding sito** selezionare **https** nel campo **Tipo**.

8. Nel campo **Certificato SSL** selezionare il certificato firmato dal menu a discesa.
   Fare clic su **OK**. Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#to-configure-an-ssl-certificate-in-iis-manager) in questo argomento.

   L'applicazione Web Accesso Web Windows PowerShell ora è configurata per usare il certificato SSL firmato.

   Per accedere ad Accesso Web Windows PowerShell, è possibile aprire `https://<server_name>/pswa` in una finestra del browser.

   > [!NOTE]
   > Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule) e [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configure-a-restrictive-authorization-rule"></a>Configurare una regola di autorizzazione restrittiva

Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso. Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente. Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione. Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="to-add-a-restrictive-authorization-rule"></a>Per aggiungere una regola di autorizzazione restrittiva

1. Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

   - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.
   - Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

2. Passaggio facoltativo per limitare l'accesso agli utenti tramite le configurazioni di sessione: Verificare che le configurazioni di sessione da usare nelle regole esistano già. Se non sono ancora state create, usare le istruzioni per la creazione di configurazioni di sessione disponibili in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

3. Digitare il comando seguente e quindi premere **INVIO**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente usando una configurazione di sessione specifica con ambito limitato alle esigenze tipiche dell'utente in termini di script e cmdlet.

   Nell'esempio seguente, a un utente con nome `JSmith` nel dominio `Contoso` viene consentito l'accesso per la gestione del computer `Contoso_214`, tramite una configurazione di sessione denominata `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName Contoso\JSmith -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

4. Eseguire il cmdlet `Get-PswaAuthorizationRule` o `Test-PswaAuthorizationRule -UserName <domain\user> -ComputerName <computer-name>` per verificare che la regola sia stata creata.

   Ad esempio: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.

## <a name="custom-deployment"></a>Distribuzione personalizzata

È possibile installare il gateway di Accesso Web Windows PowerShell in un server che esegue Windows Server 2012 R2 o Windows Server 2012 usando l'Aggiunta guidata ruoli e funzionalità in Server Manager.
Dopo l'installazione di Accesso Web Windows PowerShell, è possibile personalizzare la configurazione del gateway in Gestione IIS.

### <a name="install-windows-powershell-web-access-using-the-add-roles-and-features-wizard"></a>Installare Accesso Web Windows PowerShell tramite Aggiunta guidata ruoli e funzionalità

1. Se Server Manager è già aperto, andare al passaggio successivo. Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.

   - Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.
   - Nella schermata **Start** di Windows fare clic su **Server Manager**.

2. Scegliere **Aggiungi ruoli e funzionalità** dal menu **Gestione**.

3. Nella pagina **Selezione tipo di installazione** fare clic su **Installazione basata su ruoli o basata su funzionalità**.
   Fare clic su **Avanti**.

4. Nella pagina **Selezione server di destinazione** scegliere un server dal pool di server oppure selezionare un disco rigido virtuale offline. Per selezionare un disco rigido virtuale offline come server di destinazione, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale. Per informazioni su come aggiungere server al pool di server, vedere la Guida di Server Manager. Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.

5. Nella pagina **Selezione funzionalità** della procedura guidata espandere **Windows PowerShell**e selezionare **Accesso Web Windows PowerShell**.

6. Viene richiesto di aggiungere le funzionalità necessarie, quali .NET Framework 4.5 e i servizi ruolo del server Web (IIS). Aggiungere le funzionalità necessarie e continuare.

   > [!NOTE]
   > Se si installa Accesso Web Windows PowerShell usando l'Aggiunta guidata ruoli e funzionalità, viene installato anche il server Web (IIS), che include lo snap-in Gestione IIS. Se si usa l'Aggiunta guidata ruoli e funzionalità, lo snap-in e gli altri strumenti di gestione di IIS vengono installati per impostazione predefinita. Se si installa Accesso Web Windows PowerShell usando i cmdlet di Windows PowerShell come illustrato nella procedura seguente, gli strumenti di gestione non vengono aggiunti per impostazione predefinita.

7. Se i file delle funzionalità di Accesso Web Windows PowerShell non sono archiviati nel server di destinazione selezionato nel passaggio 4, nella pagina **Conferma selezioni per l'installazione** fare clic su **Specificare un percorso di origine alternativo** e immettere il percorso dei file delle funzionalità. In caso contrario, fare clic su **Installa**.

8. Dopo aver fatto clic su **Installa**, la pagina **Stato dell'installazione** visualizza lo stato dell'installazione, i risultati e messaggi quali avvisi, errori o procedure di configurazione successive all'installazione necessarie per Accesso Web Windows PowerShell. Dopo l'installazione di Accesso Web Windows PowerShell viene richiesto di esaminare il file Leggimi, che contiene istruzioni sulle operazioni di configurazione di base necessarie per il gateway. Le istruzioni sono incluse anche in questo argomento. Il percorso del file Leggimi è `C:\Windows\Web\PowerShellWebAccess\wwwroot\README.txt`.

### <a name="configure-the-gateway"></a>Configurare il gateway

Le istruzioni in questa sezione riguardano l'installazione dell'applicazione Web Accesso Web Windows PowerShell in una sottodirectory del sito Web, anziché nella directory radice. Questa procedura con interfaccia grafica è equivalente alle operazioni eseguite dal cmdlet `Install-PswaWebApplication`. Questa sezione include anche le istruzioni su come usare Gestione IIS per configurare il gateway di Accesso Web Windows PowerShell come sito Web radice.

#### <a name="to-use-iis-manager-to-configure-the-gateway-in-an-existing-website"></a>Per utilizzare Gestione IIS per configurare il gateway in un sito Web esistente

1. Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

   - Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)** .
   - Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)** . Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

2. Creare un nuovo pool di applicazioni per Accesso Web Windows PowerShell. Espandere il nodo del server gateway nel riquadro dell'albero di Gestione IIS, selezionare **Pool di applicazioni** e fare clic su **Aggiungi pool di applicazioni** nel riquadro **Azioni**.

3. Aggiungere un nuovo pool di applicazioni con il nome **pswa_pool**o specificare un altro nome. Fare clic su **OK**.

4. Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Selezionare la cartella **Siti**.

5. Fare clic con il pulsante destro del mouse sul sito Web, ad esempio **Sito Web predefinito**, a cui si vuole aggiungere il sito Web di Accesso Web Windows PowerShell e quindi fare clic su **Aggiungi applicazione**.

6. Nel campo **Alias** digitare pswa o specificare un altro alias. L'alias determina il nome della directory virtuale. Ad esempio, nell'URL seguente **pswa** corrisponde all'alias specificato in questo passaggio: `https://<server-name>/pswa`.

7. Nel campo **Pool di applicazioni** selezionare il pool di applicazioni creato nel passaggio 3.

8. Nel campo **Percorso fisico** cercare e selezionare il percorso dell'applicazione. È possibile usare il percorso predefinito, `$env:windir/Web/PowerShellWebAccess/wwwroot`. Fare clic su **OK**.

9. Eseguire i passaggi illustrati nella procedura [Per configurare un certificato SSL in Gestione IIS](#to-configure-an-ssl-certificate-in-iis-manager) in questo argomento.

10. Passaggio di sicurezza facoltativo:

    Con il sito Web selezionato nel riquadro dell'albero, fare doppio clic su **Impostazioni SSL** nel riquadro del contenuto.
    Selezionare **Richiedi SSL**, quindi fare clic su **Applica** nel riquadro **Azioni**. Facoltativamente, nel riquadro **Impostazioni SSL** è possibile richiedere l'uso di certificati client da parte degli utenti che si connettono al sito Web di Accesso Web Windows PowerShell. Un certificato client consente di verificare l'identità dell'utente di un dispositivo client. Per altre informazioni su come aumentare la sicurezza di Accesso Web Windows PowerShell richiedendo i certificati client, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md) in questa guida.

11. Aprire una sessione del browser in un dispositivo client. Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#browser-and-client-device-support) in questo argomento.

12. Aprire il nuovo sito Web di Accesso Web Windows PowerShell, **https://\<*nome_server_gateway*\>/pswa**.

    Il browser dovrebbe visualizzare la pagina di accesso della console di Accesso Web Windows PowerShell.

    > [!NOTE]
    > Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule) e [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

13. In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui *nome_pool_applicazioni* rappresenta il nome del pool di applicazioni creato nel passaggio 3, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.

    ```powershell
    $applicationPoolName = "<application_pool_name>"
    $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
    c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
    ```

    Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:

    ```powershell
    c:\windows\system32\icacls.exe $authorizationFile
    ```

#### <a name="to-use-iis-manager-to-configure-the-gateway-as-a-root-website-with-a-test-certificate"></a>Per usare Gestione IIS per configurare il gateway come sito Web radice con un certificato di test

1. Aprire la console Gestione IIS eseguendo una delle operazioni seguenti.

   - Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)** .
   - Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)** . Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

1. Nel riquadro dell'albero di Gestione IIS espandere il nodo del server in cui è installato Accesso Web Windows PowerShell finché non viene visualizzata la cartella **Siti**. Selezionare la cartella **Siti**.

1. Nel riquadro **Azioni** fare clic su **Aggiungi sito Web**.

1. Digitare il nome del sito Web, ad esempio **Accesso Web Windows PowerShell**.

1. Per il nuovo sito Web viene automaticamente creato un pool di applicazioni. Per utilizzare un pool di applicazioni diverso, fare clic su **Seleziona** per selezionare il pool di applicazioni da associare al nuovo sito Web. Selezionare il pool di applicazioni alternativo nella finestra di dialogo **Seleziona pool di applicazioni** , quindi fare clic su **OK**.

1. Nella casella di testo **Percorso fisico** accedere a %windir%/Web/PowerShellWebAccess/wwwroot.

1. Nel campo **Tipo** dell'area **Binding** selezionare **https**.

1. Assegnare al sito Web un numero di porta che non sia già in uso da un altro sito o applicazione.
   Per individuare le porte aperte, è possibile eseguire il comando **netstat** in una finestra del prompt dei comandi. Il numero di porta predefinito è 443.

   Cambiare la porta predefinita se un altro sito Web sta già utilizzando la porta 443 o esistono altri motivi di sicurezza per cambiare il numero di porta. Se la porta selezionata viene usata da un altro sito Web in esecuzione nel server gateway, quando si fa clic su **OK** nella finestra di dialogo **Aggiungi sito Web** viene visualizzato un avviso. Per eseguire Accesso Web Windows PowerShell è necessaria una porta inutilizzata.

1. Facoltativamente, se è necessario per l'organizzazione, specificare un nome host significativo per l'organizzazione e gli utenti, ad esempio **`www.contoso.com`** . Fare clic su **OK**.

1. Per un ambiente di produzione più sicuro, è consigliabile specificare un certificato valido firmato da una CA. È necessario fornire un certificato SSL perché gli utenti possono connettersi a Accesso Web Windows PowerShell solo con un sito Web HTTPS. Per altre informazioni su come ottenere un certificato, vedere [Per configurare un certificato SSL in Gestione IIS](#to-configure-an-ssl-certificate-in-iis-manager) in questo argomento.

1. Fare clic su **OK** per chiudere la finestra di dialogo **Aggiungi sito Web**.

1. In una sessione di Windows PowerShell aperta con diritti utente elevati (Esegui come amministratore) eseguire lo script seguente, in cui _nome_pool_applicazioni_ rappresenta il nome del pool di applicazioni creato nel passaggio 4, per concedere al pool di applicazioni i diritti di accesso al file di autorizzazione.

   ```powershell
   $applicationPoolName = "<application_pool_name>"
   $authorizationFile = "C:\windows\web\powershellwebaccess\data\AuthorizationRules.xml"
   c:\windows\system32\icacls.exe $authorizationFile /grant ('"' + "IIS AppPool\$applicationPoolName" + '":R') > $null
   ```

   Per visualizzare i diritti di accesso esistenti per il file di autorizzazione, eseguire il comando seguente:

   ```powershell
   c:\windows\system32\icacls.exe $authorizationFile
   ```

1. Con il nuovo sito Web selezionato nel riquadro dell'albero di Gestione IIS, fare clic su **Avvia** nel riquadro **Azioni** per avviare il sito Web.

1. Aprire una sessione del browser in un dispositivo client. Per altre informazioni sui browser e i dispositivi supportati, vedere la sezione [Browser e dispositivi client supportati](#browser-and-client-device-support) in questo documento.

1. Aprire il nuovo sito Web di Accesso Web Windows PowerShell.

   Il sito Web radice punta alla cartella Accesso Web Windows PowerShell, quindi il browser dovrebbe visualizzare la pagina di accesso di Accesso Web Windows PowerShell quando si apre `https://<gateway_server_name>`. Non è necessario aggiungere **/pswa** all'URL.

   > [!NOTE]
   > Non è possibile accedere al sito Web finché non si consente l'accesso agli utenti aggiungendo le regole di autorizzazione appropriate. Per altre informazioni, vedere [Configurare una regola di autorizzazione restrittiva](#configure-a-restrictive-authorization-rule) e [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

### <a name="configuring-a-restrictive-authorization-rule"></a>Configurazione di una regola di autorizzazione restrittiva

Dopo che Accesso Web Windows PowerShell è stato installato e il gateway è stato configurato, gli utenti possono aprire la pagina di accesso in un browser, ma non possono accedere finché l'amministratore di Accesso Web Windows PowerShell non concede esplicitamente l'accesso. Il controllo di accesso di Accesso Web Windows PowerShell viene gestito con il set di cmdlet di Windows PowerShell descritto nella tabella seguente. Non esiste un'interfaccia grafica paragonabile per aggiungere o gestire le regole di autorizzazione. Per informazioni dettagliate sui cmdlet di Accesso Web Windows PowerShell, vedere gli argomenti di riferimento sui cmdlet in [Cmdlet di Accesso Web Windows PowerShell](/powershell/module/powershellwebaccess/?view=winserver2012r2-ps).

Per altre informazioni sulla sicurezza e sulle regole di autorizzazione di Accesso Web Windows PowerShell, vedere [Regole di autorizzazione e funzionalità di sicurezza di Accesso Web Windows PowerShell](authorization-rules-and-security-features-of-windows-powershell-web-access.md).

#### <a name="adding-a-restrictive-authorization-rule"></a>Aggiunta di una regola di autorizzazione restrittiva

1. Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni.

   - Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.
   - Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

1. Passaggio facoltativo per limitare l'accesso agli utenti tramite le configurazioni di sessione:

   Verificare che le configurazioni di sessione da usare nelle regole esistano già. Se non sono ancora state create, usare le istruzioni per la creazione di configurazioni di sessione disponibili in [about_Session_Configuration_Files](/powershell/module/microsoft.powershell.core/about/about_session_configurations).

1. Digitare il comando seguente e quindi premere **INVIO**.

   `Add-PswaAuthorizationRule -UserName <domain\user | computer\user> -ComputerName <computer_name> -ConfigurationName <session_configuration_name>`

   Questa regola di autorizzazione consente a un utente specifico di accedere a un computer della rete a cui ha accesso normalmente usando una configurazione di sessione specifica con ambito limitato alle esigenze tipiche dell'utente in termini di script e cmdlet.

   Nell'esempio seguente, a un utente con nome `JSmith` nel dominio `Contoso` viene consentito l'accesso per la gestione del computer `Contoso_214`, tramite una configurazione di sessione denominata `NewAdminsOnly`.

   `Add-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214 -ConfigurationName NewAdminsOnly`

1. Eseguire il cmdlet `Get-PswaAuthorizationRule` o `Test-PswaAuthorizationRule -UserName '<domain\user>' -ComputerName <computer-name>` per verificare che la regola sia stata creata.

   Ad esempio: `Test-PswaAuthorizationRule -UserName 'Contoso\JSmith' -ComputerName Contoso_214`.

   Dopo la configurazione di una regola di autorizzazione, gli utenti autorizzati possono accedere alla console basata sul Web e iniziare a usare Accesso Web Windows PowerShell.

## <a name="configure-a-genuine-certificate"></a>Configurare un certificato autentico

Per un ambiente di produzione sicuro, usare sempre un certificato SSL valido firmato da un'Autorità di certificazione (CA). La procedura descritta in questa sezione illustra come ottenere e applicare un certificato SSL valido da un'Autorità di certificazione.

### <a name="to-configure-an-ssl-certificate-in-iis-manager"></a>Per configurare un certificato SSL in Gestione IIS

1. Nel riquadro dell'albero di Gestione IIS selezionare il server in cui è installato Accesso Web Windows PowerShell.

1. Nel riquadro del contenuto fare doppio clic su **Certificati server**.

1. Nel riquadro **Azioni** eseguire una delle operazioni seguenti. Per altre informazioni sulla configurazione di certificati server in IIS, vedere [Configurazione dei certificati del server in IIS 7](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).

   - Fare clic su **Importa** per importare un certificato valido esistente da un percorso della rete aziendale.
   - Fare clic su **Crea richiesta di certificato** per richiedere un certificato a una CA, ad esempio [VeriSign](https://www.verisign.com/), [Thawte](https://www.thawte.com/) o [GeoTrust](https://www.geotrust.com/). Il nome comune del certificato deve corrispondere all'intestazione host nella richiesta.

     Se ad esempio il browser client richiede `http://www.contoso.com/`, anche il nome comune deve essere `http://www.contoso.com/`. Questa è l'opzione più sicura, e quindi consigliata, per fornire un certificato al gateway di Accesso Web Windows PowerShell.

   - Fare clic su **Crea un certificato autofirmato** per creare un certificato da usare immediatamente e, se necessario, far firmare a una CA in un secondo momento. Specificare un nome descrittivo per il certificato autofirmato, ad esempio **Accesso Web Windows PowerShell**. Questa opzione non è considerata sicura ed è consigliabile utilizzarla solo per un ambiente di test privato.

1. Dopo avere ottenuto o creato un certificato, selezionare il sito Web a cui è applicato (ad esempio **Sito Web predefinito**) nel riquadro dell'albero di Gestione IIS, quindi fare clic su **Binding** nel riquadro **Azioni** .

1. Nella finestra di dialogo **Aggiungi binding sito** aggiungere un binding **https** al sito, se non è già visualizzato. Se non si utilizza un certificato autofirmato, specificare il nome host del passaggio 3 di questa procedura. Se si utilizza un certificato autofirmato, questo passaggio non è necessario.

1. Selezionare il certificato ottenuto o creato nel passaggio 3 di questa procedura e quindi fare clic su **OK**.

## <a name="using-the-web-based-windows-powershell-console"></a>Utilizzo della console di Windows PowerShell basata sul Web

Dopo avere installato Accesso Web Windows PowerShell e completato la configurazione del gateway come illustrato in questo argomento, la console di Windows PowerShell basata sul Web è pronta all'uso. Per altre informazioni su come iniziare a usare la console basata sul Web, vedere [Usare la console di Windows PowerShell basata sul Web](use-the-web-based-windows-powershell-console.md).

## <a name="see-also"></a>Vedere anche

[Documentazione di Internet Information Services (IIS) 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753433(v=ws.10))

[Guida di Gestione IIS 7.0](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732664(v=ws.11))

[Configure Web Server Security (IIS 7)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731278(v=ws.10)) (Configurare la sicurezza del server Web)

[Risorse sulla distribuzione di IPsec](/previous-versions/windows/it-pro/windows-server-2003/cc776369(v=ws.10))
