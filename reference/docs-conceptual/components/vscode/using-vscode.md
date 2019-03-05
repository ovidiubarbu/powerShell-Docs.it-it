---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 1e9b9d811a39656327af2810bd6dc8aaf3fde3a4
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251388"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso di Visual Studio Code per sviluppare PowerShell

Oltre a [PowerShell ISE][ise], PowerShell è ben supportata anche in Visual Studio Code.
ISE non è supportata in PowerShell Core, mentre Visual Studio Core è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)

È possibile usare Visual Studio Code con la versione 5 di PowerShell in Windows con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).

Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema.
Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:

- [Installazione di PowerShell Core in Linux][install-pscore-linux]
- [Installazione di PowerShell Core in macOS][install-pscore-macos]
- [Installazione di PowerShell Core in Windows][install-pscore-windows]

Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Modifiche con Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Installazione di Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Linux](https://code.visualstudio.com/docs/setup/linux)

- **macOS**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su macOS](https://code.visualstudio.com/docs/setup/mac)

  > [!IMPORTANT]
  > In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente.
  > Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`.
  > VS Code può ora caricare l'estensione PowerShell.

- **Windows**: seguire le istruzioni di installazione nella pagina per l'[Esecuzione di Visual Studio Core su Windows](https://code.visualstudio.com/docs/setup/windows)

### <a name="2-installing-powershell-extension"></a>2. Installazione dell'estensione di PowerShell

- Avviare l'app di Visual Studio Code per:
  - **Windows**: digitando `code` nella sessione di PowerShell
  - **Linux**: digitando `code` nel terminale
  - **Linux**: digitando `code` nel terminale

- Avviare **Quick Open** premendo **CTRL+P** (**CMD+P** su Mac).
- In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.
- La vista **Estensioni** si aprirà nella barra laterale. Selezionare l'estensione di PowerShell da Microsoft.
  Dovrebbe essere visualizzato un contenuto simile al seguente:

  ![VSCode](../../images/vscode.png)

- Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.
- Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**.
  Fare clic su **Ricarica**.
- Dopo aver ricaricato Visual Studio Code, è possibile procedere con la modifica.

Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**.
Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`.
Per chiudere il file, fare clic sulla "x" accanto al nome del file.
Per uscire da Visual Studio Code, **File->Esci**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installare l'estensione di PowerShell in sistemi con restrizioni

Alcuni sistemi vengono configurati in modo che richiede tutte le firme di codice da controllare e quindi richiede servizi Editor PowerShell manualmente da approvare per l'esecuzione nel sistema.
Un aggiornamento di criteri di gruppo che modifica i criteri di esecuzione è una causa probabile se è stata installata l'estensione di PowerShell, ma raggiungono un errore, ad esempio:

```
Language server startup failed.
```

Per approvare manualmente i servizi Editor PowerShell e quindi l'estensione di PowerShell per Visual Studio code aprire un messaggio di richiesta e l'esecuzione di PowerShell:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Viene richiesto con "Si vuole eseguire il software server di pubblicazione non attendibili?"
Tipo `R` per eseguire il file. Quindi, aprire Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente. Se continuano a verificarsi problemi di Guida introduttiva, segnalarlo sul [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="using-a-specific-installed-version-of-powershell"></a>Uso di una versione specifica di PowerShell

Se si vuole usare un'installazione specifica di PowerShell con Visual Studio Code, è necessario aggiungere una nuova variabile al file delle impostazioni utente.

1. Fare clic su **File -> Preferenze -> Impostazioni**
1. Nell'editor verranno visualizzati due riquadri.
   Nel riquadro di destra (`settings.json`) inserire la seguente impostazione, appropriata per il sistema operativo in uso, tra parentesi graffe (`{` e `}`) e sostituire **\<version\>** con la versione di PowerShell installata:

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. Sostituire l'impostazione con il percorso PowerShell desiderato eseguibile
1. Salvare il file di impostazioni e riavviare Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Impostazioni di configurazione per Visual Studio Code

Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.

Per Visual Studio Code, è consigliabile usare le impostazioni di configurazione seguenti:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Se non si vuole queste impostazioni interessano tutti i tipi di file, Visual Studio code consente inoltre alle configurazioni per ogni lingua. Creare un'impostazione specifica del linguaggio inserendo le impostazioni in un `[<language-name>]` campo. Ad esempio:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Per altre informazioni sul file codifica in Visual Studio Code, vedere [informazioni sulla codifica file](understanding-file-encoding.md).

## <a name="debugging-with-visual-studio-code"></a>Debug con Visual Studio Code

### <a name="no-workspace-debugging"></a>Debug senza area di lavoro

A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione. Aprire il file di script di PowerShell con **File -> Apri File...** , impostare un punto di interruzione su una riga (premere F9) e quindi premere F5 per avviare il debug. Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.

### <a name="workspace-debugging"></a>Debug dell'area di lavoro

Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**.
La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.

Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo F5.
Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.
Ad esempio, è possibile aggiungere una configurazione per:

- avviare test di Pester nel debugger
- avviare un file specifico con gli argomenti nel debugger
- avviare una sessione interattiva nel debugger
- collegare il debugger a un processo host di PowerShell

Seguire questi passaggi per creare il file di configurazione di debug:

  1. Aprire la vista **Debug** premendo **CTRL+MAIUSC+D** (**CMD+MAIUSC+D** su Mac).
  2. Premere l'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.
  3. Visual Studio Code richiederà di **selezionare l'ambiente**. Scegliere **PowerShell**.

  Quando si esegue questa operazione, Visual Studio Code crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro.
  Qui è archiviata la configurazione di debug. Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file launch.json.
  I contenuti del file launch.json sono i seguenti:

  ```json
  {
    "version": "0.2.0",
    "configurations": [
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Launch (current file)",
            "script": "${file}",
            "args": [],
            "cwd": "${file}"
        },
        {
            "type": "PowerShell",
            "request": "attach",
            "name": "PowerShell Attach to Host Process",
            "processId": "${command.PickPSHostProcess}",
            "runspaceId": 1
        },
        {
            "type": "PowerShell",
            "request": "launch",
            "name": "PowerShell Interactive Session",
            "cwd": "${workspaceRoot}"
        }
    ]
  }
  ```

  Rappresenta gli scenari di debug comuni.
  Tuttavia quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...**.
  Premere questo pulsante per aggiungere altre configurazioni di debug per PowerShell. Una configurazione utile da aggiungere è **PowerShell: avvia Script**.
  Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme F5, a prescindere dal file attivo nell'editor.

  Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.

Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:

- [Estensione PowerShell][ps-extension]
- [Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]
- [Indicazioni sul debug con Visual Studio Code][vscode-guide]
- [Debug di PowerShell in Visual Studio Code][ps-vscode]
- [Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]
- [Debug di script di PowerShell in Visual Studio Code – Parte 1][debugging-part1]
- [Debug di script di PowerShell in Visual Studio Code – Parte 2][debugging-part2]

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a>Estensione di PowerShell per Visual Studio Code

I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).
