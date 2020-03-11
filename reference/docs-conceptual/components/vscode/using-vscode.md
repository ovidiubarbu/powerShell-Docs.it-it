---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 16ae228c0d169261b783366a730fd2d5d77d32d6
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279070"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso di Visual Studio Code per sviluppare PowerShell

Oltre a [PowerShell ISE][ise], PowerShell è supportato correttamente anche in Visual Studio Code (VSCode). L'ambiente ISE non è supportato in PowerShell Core, mentre VSCode è supportato per PowerShell Core in tutte le piattaforme: Windows, macOS e Linux.

È possibile usare VSCode in Windows con la versione 5 di PowerShell usando Windows 10 o installando Windows Management Framework 5.1 per versioni precedenti dei sistemi operativi Windows, ad esempio Windows 8.1. Per altre informazioni, vedere [Installare e configurare WMF 5.1](/powershell/scripting/wmf/setup/install-configure).

Prima di iniziare, verificare che PowerShell sia presente nel sistema. Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:

- [Installazione di PowerShell Core in Linux][install-pscore-linux]
- [Installazione di PowerShell Core in macOS][install-pscore-macos]
- [Installazione di PowerShell Core in Windows][install-pscore-windows]

Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Modifica con VSCode

1. Installare VSCode. Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).

   Sono disponibili istruzioni per l'installazione per ogni piattaforma:

   - **Linux**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in Linux](https://code.visualstudio.com/docs/setup/linux).
   - **macOS**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in macOS](https://code.visualstudio.com/docs/setup/mac).

     > [!IMPORTANT]
     > In macOS è necessario installare OpenSSL affinché l'estensione di PowerShell funzioni correttamente. Il modo più semplice per eseguire questa operazione consiste nell'installare [Homebrew](https://brew.sh/) e quindi eseguire `brew install openssl`. VSCode può ora caricare l'estensione PowerShell.

   - **Windows**: seguire le istruzioni per l'installazione nella pagina [Esecuzione di VSCode in Windows](https://code.visualstudio.com/docs/setup/windows).

1. Installare l'estensione di PowerShell.

   1. Avviare l'app VSCode come indicato di seguito:
      - **Windows**: digitando `code` nella sessione di PowerShell
      - **Linux**: digitando `code` nel terminale
      - **Linux**: digitando `code` nel terminale
   1. Avviare **Quick Open** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>P</kbd>. In macOS premere <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Aprire Quick Open, digitare `ext install powershell`, quindi premere **INVIO**.
   1. La vista **Estensioni** si aprirà nella barra laterale. Selezionare l'estensione di PowerShell da Microsoft.
      Verrà visualizzata una schermata VSCode simile all'immagine seguente:

      ![VSCode](media/using-vscode/vscode.png)

   1. Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.
   1. Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**. Fare clic su **Ricarica**.
   1. Dopo aver ricaricato VSCode, è possibile apportare le modifiche.

Per creare ad esempio un nuovo file, fare clic su **File > Nuovo**. Per salvarlo, fare clic su **File > Salva**, quindi specificare un nome file, ad esempio `HelloWorld.ps1`. Per chiudere il file, fare clic sulla `X` accanto al nome file. Per uscire da VSCode, **File > Esci**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installare l'estensione di PowerShell in sistemi con restrizioni

Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice ed è richiesta l'approvazione manuale dei servizi dell'editor PowerShell per poterli eseguire nel sistema. Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una possibile causa se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:

```
Language server startup failed.
```

Per approvare manualmente i servizi dell'editor PowerShell e l'estensione di PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?** Digitare `A` per eseguire il file. Aprire quindi VSCode e verificare che l'estensione di PowerShell funzioni correttamente. Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Scelta di una versione di PowerShell da usare con l'estensione

Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una versione particolare di PowerShell con l'estensione di PowerShell. Attenersi alla procedura per scegliere la versione:

1. Aprire il **riquadro comandi** in Windows o Linux con <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>. In macOS usare <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.
1. Cercare **Session** (Sessione).
1. Fare clic su **PowerShell: Show Session Menu** (Mostra menu sessione).
1. Scegliere la versione di PowerShell da usare dall'elenco, ad esempio: **PowerShell Core**.

> [!IMPORTANT]
> Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare i percorsi di installazione di PowerShell. Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione. È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.

>[!NOTE]
> Esiste un altro modo per accedere al menu della sessione. Quando un file di PowerShell è aperto nell'editor, viene visualizzato un numero di versione verde in basso a destra. Facendo clic su questo numero di versione si passerà al menu della sessione.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Aggiunta di percorsi di PowerShell personalizzati al menu della sessione

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

È possibile impostare la versione di PowerShell predefinita da usare con l'impostazione `powershell.powerShellDefaultVersion`, specificando il testo visualizzato nel menu della sessione, vale a dire `versionName` nell'ultima impostazione:

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

Dopo aver configurato questa impostazione, riavviare VSCode oppure per ricaricare la finestra di VSCode corrente dal  **riquadro comandi**, digitare **Sviluppatore: Ricarica finestra**.

Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.

> [!NOTE]
> Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.

### <a name="configuration-settings-for-vscode"></a>Impostazioni di configurazione per VSCode

Seguendo la procedura descritta nel paragrafo precedente, è possibile aggiungere le impostazioni di configurazione in `settings.json`.

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

A partire dalla versione 1.9 di VSCode, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell. Aprire il file di script di PowerShell tramite **File > Apri File**, impostare un punto di interruzione in una riga, premere <kbd>F9</kbd>, quindi premere <kbd>F5</kbd> per avviare il debug. Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.

### <a name="workspace-debugging"></a>Debug dell'area di lavoro

Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code dal menu **File** usando **Apri cartella**. La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.

Anche con questa modalità, è possibile avviare il debug dello script di PowerShell attualmente selezionato premendo <kbd>F5</kbd>. Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto. È ad esempio possibile aggiungere una configurazione per eseguire le operazioni seguenti:

- Avviare test di Pester nel debugger.
- Avviare un file specifico con gli argomenti nel debugger.
- Avviare una sessione interattiva nel debugger.
- Collegare il debugger a un processo host di PowerShell.

Seguire questi passaggi per creare il file di configurazione di debug:

  1. Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>. In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.
  1. Fare clic sull'icona a forma di ingranaggio **Configura** sulla barra degli strumenti.
  1. VSCode richiederà di **selezionare l'ambiente**. Scegliere **PowerShell**.

VSCode creerà una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro. In questa posizione è archiviata la configurazione di debug. Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`. Il contenuto del file `launch.json` è il seguente:

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

Il file rappresenta gli scenari di debug comuni. Quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** . È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell. Una configurazione utile da aggiungere è **PowerShell: avvia script**. Con questa configurazione, è possibile scegliere un file specifico con gli argomenti facoltativi che devono essere avviati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.

Dopo aver definito la configurazione di debug, è possibile selezionare la configurazione che si vuole usare durante una sessione di debug. Selezionare una configurazione dall'elenco a discesa delle configurazioni di debug nella barra degli strumenti della visualizzazione **Debug**.

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
[install-pscore-linux]:  ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../install/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a>Estensione di PowerShell per VSCode

I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).
