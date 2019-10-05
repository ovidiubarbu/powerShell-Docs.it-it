---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325240"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso di Visual Studio Code per sviluppare PowerShell

Oltre a [PowerShell ISE][ise], PowerShell è supportato correttamente anche in Visual Studio Code (VSCode). L'ambiente ISE non è supportato in PowerShell Core, mentre VSCode è supportato per PowerShell Core in tutte le piattaforme (Windows, macOS e Linux)

È possibile usare VSCode in Windows con la versione 5 di PowerShell con Windows 10 o installando [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) per sistemi operativi Windows inferiori (ad esempio, Windows 8.1 e così via).

Prima di procedere con l'avvio, verificare che PowerShell sia presente nel sistema. Per carichi di lavoro moderni in Windows, macOS e Linux, vedere:

- [Installazione di PowerShell Core in Linux][install-pscore-linux]
- [Installazione di PowerShell Core in macOS][install-pscore-macos]
- [Installazione di PowerShell Core in Windows][install-pscore-windows]

Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Modifica con VSCode

1. [Installazione di VSCode](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in Linux](https://code.visualstudio.com/docs/setup/linux)
   - **macOS**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in macOS](https://code.visualstudio.com/docs/setup/mac)

     > [!IMPORTANT]
     > In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente. Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`. VSCode può ora caricare l'estensione PowerShell.

   - **Windows**: seguire le istruzioni di installazione nella pagina [Esecuzione di VSCode in Windows](https://code.visualstudio.com/docs/setup/windows)

2. Installazione dell'estensione di PowerShell

   - Avviare l'app VSCode come indicato di seguito:
     - **Windows**: digitando `code` nella sessione di PowerShell
     - **Linux**: digitando `code` nel terminale
     - **Linux**: digitando `code` nel terminale
   - Avviare **Quick Open** premendo <kbd>CTRL</kbd>+<kbd>P</kbd> (<kbd>Comando</kbd>+<kbd>P</kbd> in Mac).
   - In Quick Open digitare `ext install powershell` e fare clic su **INVIO**.
   - La vista **Estensioni** si aprirà nella barra laterale. Selezionare l'estensione di PowerShell da Microsoft.
     Dovrebbe essere visualizzato un contenuto simile al seguente:

     ![VSCode](../../images/using-vscode/vscode.png)

   - Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.
   - Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**. Fare clic su **Ricarica**.
   - Dopo il ricaricamento di VSCode, si è pronti per la modifica.

Ad esempio, per creare un nuovo file, fare clic su **File->Nuovo**. Per salvarlo, fare clic su **File->Salva** e quindi specificare un nome per il file, ad esempio `HelloWorld.ps1`. Per chiudere il file, fare clic sulla "x" accanto al nome del file. Per uscire da VSCode, **File-> Esci**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installare l'estensione di PowerShell in sistemi con restrizioni

Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice e pertanto è richiesta l'approvazione manuale dei servizi dell'editor di PowerShell per poterli eseguire nel sistema. Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una causa probabile se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:

```
Language server startup failed.
```

Per approvare manualmente i servizi dell'editor di PowerShell e quindi l'estensione di PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Viene visualizzata la richiesta "Eseguire software di questo autore non attendibile?" Digitare `R` per eseguire il file. Aprire quindi VSCode e verificare che l'estensione di PowerShell funzioni correttamente. Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Scelta di una versione di PowerShell da usare con l'estensione

Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una particolare versione di PowerShell con l'estensione di PowerShell. Usare questa procedura per scegliere la versione:

1. Aprire il riquadro comandi (<kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in Windows e Linux, <kbd>Comando</kbd> + <kbd>Maiuscole</kbd>+<kbd>P</kbd> in macOS).
1. Cercare "Session" (Sessione).
1. Fare clic su "PowerShell: Show Session Menu" (Mostra menu sessione).
1. Scegliere la versione di PowerShell da usare dall'elenco, ad esempio, "PowerShell Core".

> [!IMPORTANT]
> Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell. Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione. È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.

>[!NOTE]
> Esiste un altro modo per accedere al menu della sessione. Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra. Facendo clic su questo numero di versione si passerà al menu della sessione.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Aggiunta di percorsi di PowerShell personalizzati al menu della sessione

È possibile aggiungere altri percorsi per l'eseguibile di PowerShell al menu della sessione tramite un'impostazione di VSCode.

Aggiungere un elemento all'elenco `powershell.powerShellAdditionalExePaths` o creare l'elenco se non esiste nel file `settings.json`:

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

Ogni elemento deve avere:

* `exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.
* `versionName`: testo che verrà visualizzato nel menu della sessione.

È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione (ovvero `versionName` nell'ultima impostazione):

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

Dopo aver specificato questa impostazione, riavviare VSCode o usare l'azione del riquadro comandi "Sviluppatore: Ricarica finestra" per ricaricare la finestra di VSCode corrente.

Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.

> [!NOTE]
> Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.

#### <a name="configuration-settings-for-vscode"></a>Impostazioni di configurazione per VSCode

Seguendo i passaggi descritti nel paragrafo precedente è possibile aggiungere le impostazioni di configurazione in `settings.json`.

È consigliabile usare le impostazioni di configurazione seguenti per VSCode:

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

Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, VS Code consente anche di definire configurazioni diverse in base al linguaggio. Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`. Ad esempio:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Per altre informazioni sulla codifica dei file in VSCode, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Debug con VSCode

### <a name="no-workspace-debugging"></a>Debug senza area di lavoro

A partire dalla versione 1.9 di VSCode, è possibile eseguire il debug degli script di PowerShell senza dover aprire la cartella contenente lo script in questione. Aprire il file di script di PowerShell tramite **File->Apri File**, impostare un punto di interruzione su una riga (premere <kbd>F9</kbd>) e quindi premere <kbd>F5</kbd> per avviare il debug. Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.

### <a name="workspace-debugging"></a>Debug dell'area di lavoro

Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code tramite **Apri cartella...**  dal menu **File**. La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.

Anche con questa modalità, è possibile avviare il debug dello script selezionato di PowerShell premendo <kbd>F5</kbd>. Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto. Ad esempio, è possibile aggiungere una configurazione per:

- avviare test di Pester nel debugger
- avviare un file specifico con gli argomenti nel debugger
- avviare una sessione interattiva nel debugger
- collegare il debugger a un processo host di PowerShell

Seguire questi passaggi per creare il file di configurazione di debug:

  1. Aprire la visualizzazione **Debug** premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd> (<kbd>Comando</kbd>+<kbd>Maiuscole</kbd>+<kbd>D</kbd> in Mac).
  2. Fare clic sull'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.
  3. VSCode richiederà di **selezionare l'ambiente**. Scegliere **PowerShell**.

  Quando si esegue questa operazione, VSCode crea una directory e un file ".vscode\launch.json" nella radice della cartella dell'area di lavoro. Qui è archiviata la configurazione di debug. Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file launch.json. I contenuti del file launch.json sono i seguenti:

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

  Rappresenta gli scenari di debug comuni. Tuttavia quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** . È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell. Una configurazione utile da aggiungere è **PowerShell: avvia script**. Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.

  Una volta stabilita la configurazione di debug, è possibile selezionare la configurazione da usare durante una sessione di debug selezionandone una dal menu a discesa relativo alla configurazione nella visualizzazione della barra degli strumenti **Debug**.

Esistono alcuni blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:

- [Estensione PowerShell][ps-extension]
- [Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]
- [Indicazioni sul debug con Visual Studio Code][vscode-guide]
- [Debug di PowerShell in Visual Studio Code][ps-vscode]
- [Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]
- [Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]
- [Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]

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

## <a name="powershell-extension-for-vscode"></a>Estensione di PowerShell per VSCode

I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).
