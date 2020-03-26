---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 86739970b58460bef9686a75bf0604d0605d4888
ms.sourcegitcommit: d36db3a1bc44aee6bc97422b557041c3aece4c67
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/21/2020
ms.locfileid: "80082417"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso di Visual Studio Code per sviluppare PowerShell

[Visual Studio Code](https://code.visualstudio.com/) è un editor di script multipiattaforma (Windows, macOS e Linux) fornito da Microsoft. Insieme all'[estensione PowerShell](https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell), offre un'esperienza di modifica degli script avanzata e interattiva, che semplifica la scrittura di script PowerShell affidabili.

Visual Studio Code con l'estensione PowerShell è l'editor consigliato per la scrittura di script PowerShell.
Supporta le versioni di PowerShell seguenti:

- PowerShell 7 e versioni successive
- PowerShell Core 6
- Windows PowerShell 5.1

Prima di iniziare, verificare che PowerShell sia presente nel sistema. Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:

- [Installazione di PowerShell Core in Linux][install-pscore-linux]
- [Installazione di PowerShell Core in macOS][install-pscore-macos]
- [Installazione di PowerShell Core in Windows][install-pscore-windows]

Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].

> [!NOTE]
> Visual Studio Code non è [Visual Studio](https://visualstudio.microsoft.com/).

> [!IMPORTANT]
> [Windows PowerShell ISE][ise] è ancora disponibile per Windows, ma non è più incluso nello sviluppo delle funzionalità attive e non funziona con PowerShell 7 e versioni successive o con PowerShell Core 6.
> Questo componente distribuito con Windows continua a essere supportato per la sicurezza e per le correzioni a priorità elevata. Attualmente non è prevista la rimozione di ISE da Windows.

## <a name="editing-with-visual-studio-code"></a>Modifiche con Visual Studio Code

1. Installare Visual Studio Code. Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).

    Sono disponibili istruzioni per l'installazione per ogni piattaforma:

    - **Windows**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Windows](https://code.visualstudio.com/docs/setup/windows).
    - **macOS**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in macOS](https://code.visualstudio.com/docs/setup/mac).
    - **Linux**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Linux](https://code.visualstudio.com/docs/setup/linux).

1. Installare l'estensione di PowerShell.

   1. Avviare l'app Visual Studio Code digitando `code` in una console o `code-insiders` se è stato installato Visual Studio Code Insider.
   1. Avviare **Quick Open** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>P</kbd>. In macOS premere <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Aprire Quick Open, digitare `ext install powershell`, quindi premere **INVIO**.
   1. La vista **Estensioni** si aprirà nella barra laterale. Selezionare l'estensione di PowerShell da Microsoft.
      Verrà visualizzata una schermata Visual Studio Code simile all'immagine seguente:

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Da Microsoft, fare clic sul pulsante **Installa** sull'estensione di PowerShell.
   1. Dopo l'installazione, il pulsante **Ricarica** verrà visualizzato al posto del pulsante **Installa**. Fare clic su **Ricarica**.
   1. Dopo aver ricaricato Visual Studio Code, è possibile procedere con le operazioni di modifica.

Per creare ad esempio un nuovo file, fare clic su **File > Nuovo**. Per salvarlo, fare clic su **File > Salva**, quindi specificare un nome file, ad esempio `HelloWorld.ps1`. Per chiudere il file, fare clic sulla `X` accanto al nome file. Per uscire da Visual Studio Code, **File > Esci**.

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installare l'estensione di PowerShell in sistemi con restrizioni

Alcuni sistemi vengono configurati in modo da richiedere il controllo di tutte le firme di codice ed è richiesta l'approvazione manuale dei servizi dell'editor PowerShell per poterli eseguire nel sistema. Un aggiornamento di Criteri di gruppo che modifica i criteri di esecuzione è una possibile causa se è stata installata l'estensione di PowerShell, ma viene generato un errore simile al seguente:

```
Language server startup failed.
```

Per approvare manualmente i servizi dell'editor PowerShell e l'estensione PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?**
Digitare `A` per eseguire il file. Aprire quindi Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente. Se i problemi persistono, segnalarlo su [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

> [!NOTE]
> L'estensione PowerShell per Visual Studio Code non supporta l'esecuzione in modalità di linguaggio vincolato. Per altre informazioni, vedere la [gestione dei problemi GitHub supportati](https://github.com/PowerShell/vscode-powershell/issues/606).

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Uso di una versione precedente dell'estensione PowerShell per Windows PowerShell V3 e V4

Anche se l'estensione PowerShell corrente [non supporta più le versioni 3 e 4](https://github.com/PowerShell/vscode-powershell/issues/1310), è comunque possibile usare la versione più recente dell'estensione che supportava queste versioni.

> [!NOTE]
> Non verranno apportate correzioni aggiuntive a questa precedente versione dell'estensione. È disponibile nella configurazione attuale e solo se si usano ancora Windows PowerShell V3 e Windows PowerShell V4.

In primo luogo aprire il riquadro Extension (Estensione) e cercare `PowerShell`. Fare quindi clic sull'ingranaggio e selezionare **Install another version...** (Installa un'altra versione...).

![Installa un'altra versione...](media/using-vscode/install-another-version.png)

Selezionare quindi la versione **`2020.1.0`** . Questa è l'ultima versione dell'estensione che supporta V3 e V4.

Aggiungere anche l'impostazione seguente in modo che la versione dell'estensione non venga aggiornata automaticamente:

```json
{
    "extensions.autoUpdate": false
}
```

Sebbene funzionerà in un prossimo futuro, Visual Studio Code potrebbe implementare una modifica che interrompe questa versione dell'estensione.
Per questo motivo e per la mancanza di supporto, è consigliabile eseguire le operazioni seguenti:

- Scaricare PowerShell 7, vale a dire un'installazione affiancata di Windows PowerShell che funziona perfettamente con l'estensione PowerShell
- Aggiornare Windows PowerShell 5.1

La sezione [Modifiche con Visual Studio Code](#editing-with-visual-studio-code) in questo articolo contiene i collegamenti per le installazioni.

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

È possibile aggiungere altri percorsi dell'eseguibile PowerShell al menu della sessione tramite l'[impostazione di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.

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

- `exePath`: percorso per l'eseguibile di `pwsh` o `powershell`.
- `versionName`: testo che verrà visualizzato nel menu della sessione.

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

Dopo aver configurato questa impostazione, riavviare Visual Studio Code oppure per ricaricare la finestra di Visual Studio Code corrente dal  **riquadro comandi**, digitare **Sviluppatore: Ricarica finestra**.

Se si apre il menu della sessione, sono ora visibili le versioni di PowerShell aggiunte.

> [!NOTE]
> Se si compila PowerShell dall'origine, questo è un ottimo modo per testare la compilazione locale di PowerShell.

### <a name="configuration-settings-for-visual-studio-code"></a>Impostazioni di configurazione per Visual Studio Code

Se non si ha familiarità con le modalità di modifica delle impostazioni in Visual Studio Code, è consigliabile prima di tutto esaminare [la documentazione sulle impostazioni di Visual Studio Code](https://code.visualstudio.com/docs/getstarted/settings).

Seguendo la procedura descritta nel paragrafo precedente, è possibile aggiungere le impostazioni di configurazione in `settings.json`.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Se si vuole evitare che queste impostazioni influiscano su tutti i tipi di file, Visual Studio Code consente anche di definire configurazioni diverse per linguaggio. Per creare un'impostazione specifica del linguaggio, inserire le impostazioni in un campo `[<language-name>]`. Ad esempio:

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Per altre informazioni sulla codifica dei file in Visual Studio Code, vedere [Informazioni sulla codifica di file](understanding-file-encoding.md).
>
> Per altri suggerimenti su come configurare Visual Studio Code per la modifica di PowerShell, vedere anche [Come replicare l'esperienza di ISE in Visual Studio Code](How-To-Replicate-the-ISE-Experience-In-VSCode.md).

## <a name="debugging-with-visual-studio-code"></a>Debug con Visual Studio Code

### <a name="no-workspace-debugging"></a>Debug senza area di lavoro

A partire dalla versione 1.9 di Visual Studio Code, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell. Aprire il file di script di PowerShell tramite **File > Apri File**, impostare un punto di interruzione in una riga, premere <kbd>F9</kbd>, quindi premere <kbd>F5</kbd> per avviare il debug. Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.

### <a name="workspace-debugging"></a>Debug dell'area di lavoro

Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta in Visual Studio Code dal menu **File** usando **Apri cartella**. La cartella che è stata aperta si trova in genere nella cartella del progetto PowerShell e/o nella radice del repository Git.

Anche con questa modalità, è possibile avviare il debug dello script di PowerShell attualmente selezionato premendo <kbd>F5</kbd>. Tuttavia, il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto. Verranno analizzate più avanti.

Seguire questi passaggi per creare il file di configurazione di debug:

  1. Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>. In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.
  1. Fare clic sul collegamento per creare un file launch.json.
  1. Visual Studio Code richiederà di **selezionare l'ambiente**. Scegliere **PowerShell**.
  1. Infine, scegliere il tipo di debug che si vuole usare:

- **Avviare il file corrente**: avviare ed eseguire il debug del file nella finestra dell'editor attualmente attiva
- **Avviare lo script**: avviare ed eseguire il debug del file o del comando specificato
- **Sessione interattiva**: eseguire il debug dei comandi eseguiti dalla console integrata
- **Collegare**: collegare il debugger a un processo host di PowerShell in esecuzione

Visual Studio Code creerà una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro. In questa posizione è archiviata la configurazione di debug. Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`. Il contenuto del file `launch.json` è il seguente:

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

## <a name="powershell-extension-for-visual-studio-code"></a>Estensione di PowerShell per Visual Studio Code

I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub](https://github.com/PowerShell/vscode-powershell).

Per contribuire, le richieste pull sono molto apprezzate. Per iniziare, seguire la [documentazione per gli sviluppatori su GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md).

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Risoluzione dei problemi dell'estensione PowerShell per Visual Studio Code

Se si verificano problemi con Visual Studio Code durante lo sviluppo di script di PowerShell, vedere la [guida alla risoluzione dei problemi su GitHub](https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md)
