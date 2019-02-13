---
ms.date: 08/23/2017
keywords: powershell,cmdlet
title: disinstallare accesso web windows powershell
ms.openlocfilehash: 22c874d766445dccedd8494097daf16c30fa66ff
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682509"
---
# <a name="uninstall-windows-powershell-web-access"></a>Disinstallare Accesso Web Windows PowerShell

Ultimo aggiornamento: 24 giugno 2013

Si applica a: Windows Server 2012 R2, Windows Server 2012

I passaggi descritti in questo argomento consentono di rimuovere il sito Web di Accesso Web Windows PowerShell e l'applicazione corrispondente dal server gateway in cui sono installati.

## <a name="notify-users"></a>Informare gli utenti

Prima di iniziare, informare gli utenti della console basata sul Web di cui si intende rimuovere il sito Web.

La procedura di disinstallazione di Accesso Web Windows PowerShell non disinstalla IIS o le altre funzionalità installate automaticamente, perché sono necessarie per l'esecuzione di Accesso Web Windows PowerShell.
La procedura di disinstallazione mantiene installate le funzionalità da cui dipende Accesso Web Windows PowerShell. Se necessario, è possibile disinstallare tali funzionalità separatamente.

## <a name="recommended-quick-uninstallation"></a>Disinstallazione consigliata (rapida)

Le procedure in questa sezione consentono di installare sia:

- l'applicazione Web Accesso Web Windows PowerShell, sia
- la funzionalità Accesso Web Windows PowerShell

usando i cmdlet di Windows PowerShell.

### <a name="step-1-delete-the-web-application-using-cmdlets"></a>Passaggio 1: Eliminare l'applicazione web usando i cmdlet

1. Per aprire una sessione di Windows PowerShell, eseguire una di queste operazioni.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni.

    -   Nella schermata **Start** di Windows fare clic su **Windows PowerShell**.

2. Digitare `Uninstall-PswaWebApplication` e quindi premere **INVIO**.
   1. Se è stato specificato il nome del sito Web personalizzato, aggiungere il parametro `-WebsiteName` al comando e specificare il nome del sito Web.

        `Uninstall-PswaWebApplication -WebsiteName <web-site-name>`
   1. Se è stata usata un'applicazione Web personalizzata e non l'applicazione predefinita, **pswa**, aggiungere il parametro `-WebApplicationName` al comando e specificare il nome dell'applicazione Web.

        `Uninstall-PswaWebApplication -WebApplicationName <web-application-name>`
   1. Se si utilizza un certificato di prova, aggiungere il parametro `DeleteTestCertificate` al cmdlet come mostrato nell'esempio seguente.

        `Uninstall-PswaWebApplication -DeleteTestCertificate`

### <a name="step-2-uninstall-windows-powershell-web-access-using-cmdlets"></a>Passaggio 2: Disinstallare accesso Web di Windows PowerShell usando i cmdlet

1. Per aprire una sessione di Windows PowerShell con diritti utente elevati, eseguire una di queste operazioni. Se è presente una sessione aperta, continuare con il passaggio successivo.

    -   Nel desktop di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** nella barra delle applicazioni e scegliere **Esegui come amministratore**.

    -   Nella schermata **Start** di Windows fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi scegliere **Esegui come amministratore**.

1. Digitare il codice seguente e premere **INVIO**, dove *nome_computer* rappresenta un server remoto da cui si vuole rimuovere Accesso Web Windows PowerShell. Il parametro `-Restart` riavvia automaticamente i server di destinazione, se richiesto dalla procedura di rimozione.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -ComputerName <computer_name> -Restart

    Per rimuovere ruoli e funzionalità da un disco rigido virtuale offline, è necessario aggiungere i parametri `-ComputerName` e `-VHD` . Il parametro `-ComputerName` contiene il nome del server in cui montare il disco rigido virtuale e il parametro `-VHD` contiene il percorso del file VHD nel server specificato.

        Uninstall-WindowsFeature -Name WindowsPowerShellWebAccess -VHD <path> -ComputerName <computer_name> -Restart

1. Terminata la rimozione verificare che Accesso Web Windows PowerShell sia stato rimosso, aprendo la pagina **Tutti i server** in Server Manager, selezionando un server da cui è stata rimossa la funzionalità e visualizzando il riquadro **Ruoli e funzionalità** nella pagina del server selezionato.

    È anche possibile eseguire il cmdlet `Get-WindowsFeature` indicando come destinazione il server selezionato (Get-WindowsFeature -ComputerName &lt;*nome_computer*&gt;) per visualizzare un elenco di ruoli e funzionalità installati nel server.

## <a name="custom-uninstallation"></a>Disinstallazione personalizzata

Le procedure in questa sezione consentono di disinstallare l'applicazione Web Accesso Web Windows PowerShell e la funzionalità Accesso Web Windows PowerShell usando la Rimozione guidata ruoli e funzionalità in Server Manager e la console Gestione IIS.

### <a name="step-1-delete-the-web-application-using-iis-manager"></a>Passaggio 1: Eliminare l'applicazione web tramite Gestione IIS


1. Aprire la console Gestione IIS eseguendo una delle operazioni seguenti. Se è già aperta, continuare con il passaggio successivo.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows. Nel menu **Strumenti** di Server Manager fare clic su **Gestione Internet Information Services (IIS)**.

    -   Nella schermata **Start** di Windows digitare una parte qualsiasi del nome **Gestione Internet Information Services (IIS)**. Fare clic sul collegamento quando viene visualizzato nell'elenco dei risultati **App**.

1. Nel riquadro dell'albero di Gestione IIS selezionare il sito Web che esegue l'applicazione Web Accesso Web Windows PowerShell.

1. Nel riquadro **Azioni**, in **Gestisci sito Web** fare clic su **Arresta**.

1. Nel riquadro dell'albero fare clic con il pulsante destro del mouse sull'applicazione Web nel sito Web che esegue l'applicazione Web di Accesso Web Windows PowerShell, quindi fare clic su **Rimuovi**.

1. Nel riquadro dell'albero selezionare **Pool di applicazioni**, selezionare la cartella del pool di applicazioni di Accesso Web Windows PowerShell, fare clic su **Arresta** nel riquadro **Azioni**, quindi fare clic su **Rimuovi** nel riquadro del contenuto.

1. Chiudere Gestione Internet Information Services (IIS).

> ![Nota di avviso](images/SecurityNote.jpeg)**Nota**:
>
> Durante la disinstallazione il certificato non viene eliminato.
>
> Se è stato creato un certificato autofirmato o si utilizza un certificato di prova e si desidera rimuoverlo, eliminare il certificato in Gestione IIS.

### <a name="step-2-uninstall-windows-powershell-web-access-using-the-remove-roles-and-features-wizard"></a>Passaggio 2: Disinstallare accesso Web di Windows PowerShell tramite la rimozione guidata ruoli e funzionalità

1. Se Server Manager è già aperto, andare al passaggio successivo. Se Server Manager non è aperto, aprirlo in uno dei modi seguenti.

    -   Nel desktop di Windows avviare Server Manager facendo clic su **Server Manager** nella barra delle applicazioni di Windows.

    -   Nella schermata **Start** di Windows fare clic su **Server Manager**.

1. Scegliere **Rimuovi ruoli e funzionalità** dal menu **Gestisci**.

1. Nella pagina **Selezione server di destinazione** selezionare il server o il disco rigido virtuale offline da cui si vuole rimuovere la funzionalità. Per selezionare un disco rigido virtuale offline, selezionare innanzitutto il server in cui montare il disco rigido virtuale, quindi selezionare il file del disco rigido virtuale. Dopo aver selezionato il server di destinazione, fare clic su **Avanti**.

1. Fare di nuovo clic su **Avanti** per ignorare la pagina **Rimuovi funzionalità**.

1. Deselezionare la casella di controllo **Accesso Web Windows PowerShell** e fare clic su **Avanti**.

1. Nella pagina **Conferma selezioni per la rimozione** fare clic su **Rimuovi**.

## <a name="see-also"></a>Vedere anche

- [Installare e usare Accesso Web Windows PowerShell](install-and-use-windows-powershell-web-access.md)
- [Guida di Gestione IIS 7.0](https://technet.microsoft.com/library/cc732664.aspx)