---
title: Uso di Visual Studio Code per sviluppare PowerShell
description: Uso di Visual Studio Code per sviluppare PowerShell
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "80978696"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Uso di Visual Studio Code per sviluppare PowerShell

[Visual Studio Code][vscode] è un editor di script multipiattaforma di Microsoft. Insieme all'[estensione PowerShell][psext], offre un'esperienza di modifica degli script avanzata e interattiva, che semplifica la scrittura di script PowerShell affidabili. Visual Studio Code con l'estensione PowerShell è l'editor consigliato per la scrittura di script PowerShell.

Supporta le versioni di PowerShell seguenti:

- PowerShell 7 e versioni successive (Windows, macOS e Linux)
- PowerShell Core 6 (Windows, macOS e Linux)
- Windows PowerShell 5.1 (solo Windows)

> [!NOTE]
> Visual Studio Code non è [Visual Studio][].

## <a name="getting-started"></a>Introduzione

Prima di iniziare, verificare che PowerShell sia presente nel sistema. Per carichi di lavoro moderni in Windows, macOS e Linux, vedere i collegamenti seguenti:

- [Installazione di PowerShell in Linux][install-pscore-linux]
- [Installazione di PowerShell in macOS][install-pscore-macos]
- [Installazione di PowerShell in Windows][install-pscore-windows]

Per carichi di lavoro di Windows PowerShell tradizionali, vedere [Installazione di Windows PowerShell][install-winps].

> [!IMPORTANT]
> [Windows PowerShell ISE][ise] continua a essere disponibile per Windows. Tuttavia, non viene più sviluppato in modo attivo. ISE non funziona con PowerShell 6 e versioni successive. Poiché è un componente di Windows, continua a essere supportato per la sicurezza e per le correzioni a priorità elevata.
> Non è prevista la rimozione di ISE da Windows.

## <a name="editing-with-visual-studio-code"></a>Modifiche con Visual Studio Code

1. Installare Visual Studio Code. Per altre informazioni, vedere la panoramica [onfigurazione di Visual Studio Code][vsc-setup].

   Sono disponibili istruzioni per l'installazione per ogni piattaforma:

   - **Windows**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Windows][vsc-setup-win].
   - **macOS**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in macOS][vsc-setup-macOS].
   - **Linux**: seguire le istruzioni di installazione nella pagina di [esecuzione di Visual Studio Code in Linux][vsc-setup-linux].

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

Alcuni sistemi sono configurati in modo da richiedere la convalida di tutte le firme del codice. È possibile che venga visualizzato l'errore seguente:

```
Language server startup failed.
```

Questo problema può verificarsi quando i criteri di esecuzione di PowerShell vengono impostati da Criteri di gruppo di Windows. Per approvare manualmente i servizi dell'editor PowerShell e l'estensione PowerShell per Visual Studio Code, aprire un prompt di PowerShell ed eseguire il comando seguente:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Viene visualizzata la richiesta **Eseguire software di questo autore non attendibile?** Digitare `A` per eseguire il file. Aprire quindi Visual Studio Code e verificare che l'estensione di PowerShell funzioni correttamente. Se i problemi persistono, segnalarlo su [Problemi di GitHub][].

> [!NOTE]
> L'estensione PowerShell per Visual Studio Code non supporta l'esecuzione in modalità di linguaggio vincolato. Per altre informazioni, vedere il [problema 606 su GitHub][i606].

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Scelta di una versione di PowerShell da usare con l'estensione

Con PowerShell Core installato side-by-side con Windows PowerShell è ora possibile usare una versione specifica di PowerShell con l'estensione di PowerShell. Questa funzionalità esegue la ricerca in alcuni percorsi noti nei diversi sistemi operativi per individuare le installazioni di PowerShell.

Attenersi alla procedura per scegliere la versione:

1. Aprire il **riquadro comandi** in Windows o Linux con <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>. In macOS usare <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd>.
1. Cercare **Session** (Sessione).
1. Fare clic su **PowerShell: Show Session Menu** (Mostra menu sessione).
1. Scegliere la versione di PowerShell da usare dall'elenco, ad esempio: **PowerShell Core**.

Se PowerShell è installato in un percorso non tipico, potrebbe non comparire inizialmente nel menu della sessione. È possibile estendere il menu della sessione [aggiungendo percorsi personalizzati](#adding-your-own-powershell-paths-to-the-session-menu) come descritto di seguito.

> [!NOTE]
> È anche possibile accedere al menu della sessione di PowerShell dal numero di versione verde nell'angolo inferiore destro della barra di stato. Facendo clic su questo numero di versione si apre il menu della sessione.

## <a name="configuration-settings-for-visual-studio-code"></a>Impostazioni di configurazione per Visual Studio Code

Se non si ha familiarità con le modalità di modifica delle impostazioni in Visual Studio Code, è consigliabile prima di tutto leggere [la documentazione sulle impostazioni di Visual Studio Code][vsc-settings].

Dopo aver letto la documentazione, è possibile aggiungere le impostazioni di configurazione in `settings.json`.

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
> Per altre informazioni sulla codifica dei file in Visual Studio Code, vedere [Informazioni sulla codifica di file][file-encoding].
>
> Per altri suggerimenti su come configurare Visual Studio Code per la modifica di PowerShell, vedere anche [Come replicare l'esperienza di ISE in Visual Studio Code][vsc-ise].

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

Per impostare la versione predefinita di PowerShell, impostare il valore `powershell.powerShellDefaultVersion` sul testo visualizzato nel menu della sessione (detto anche `versionName`):

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

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Uso di una versione precedente dell'estensione PowerShell per Windows PowerShell V3 e V4

L'estensione PowerShell corrente non supporta [PowerShell V3 e V4][i1310]. Tuttavia, è possibile usare la versione più recente dell'estensione che supporta PowerShell V3 e V4.

> [!CAUTION]
> Non verranno apportate correzioni aggiuntive a questa precedente versione dell'estensione. È disponibile nella configurazione attuale e solo se si usano ancora Windows PowerShell V3 e Windows PowerShell V4.

In primo luogo aprire il riquadro Extension (Estensione) e cercare `PowerShell`. Fare quindi clic sull'ingranaggio e selezionare **Install another version...** (Installa un'altra versione...).

![Installa un'altra versione...](media/using-vscode/install-another-version.png)

Selezionare quindi la versione **2020.1.0**. Questa è l'ultima versione dell'estensione che supporta V3 e V4. Assicurarsi di aggiungere l'impostazione seguente in modo che la versione dell'estensione non venga aggiornata automaticamente:

```json
{
    "extensions.autoUpdate": false
}
```

La versione **2020.1.0** funzionerà nel prossimo futuro, tuttavia, Visual Studio Code potrebbe implementare una modifica che interrompe questa versione dell'estensione. Per questo motivo e per la mancanza di supporto, è consigliabile:

- Aggiornare Windows PowerShell 5.1
- Installare PowerShell 7, vale a dire un'installazione affiancata di Windows PowerShell che funziona perfettamente con l'estensione PowerShell

## <a name="debugging-with-visual-studio-code"></a>Debug con Visual Studio Code

### <a name="no-workspace-debugging"></a>Debug senza area di lavoro

In Visual Studio Code 1.9 o versione successiva, è possibile eseguire il debug degli script di PowerShell senza aprire la cartella contenente lo script di PowerShell.

1. Aprire il file di script di PowerShell con **File > Apri file...**
1. Impostare un punto di interruzione, selezionare una riga, quindi premere <kbd>F9</kbd>
1. Premere <kbd>F5</kbd> per avviare il debug

Verrà visualizzato il riquadro delle azioni di debug che consente di interrompere il debugger, eseguire le istruzioni, riprendere e arrestare il debug.

### <a name="workspace-debugging"></a>Debug dell'area di lavoro

Il debug dell'area di lavoro fa riferimento al debug nel contesto di una cartella che è stata aperta dal menu **File** usando **Apri cartella**. La cartella che si apre si trova in genere nella cartella del progetto PowerShell o nella radice del repository Git. Il debug dell'area di lavoro consente di definire più configurazioni di debug diverse dal semplice debug del file attualmente aperto.

Seguire questi passaggi per creare un file di configurazione di debug:

1. Aprire la visualizzazione **Debug** in Windows o Linux premendo <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>. In macOS premere <kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>D</kbd>.
1. Fare clic sul collegamento per **creare un file launch.json**.
1. In **Seleziona ambiente** scegliere **PowerShell**.
1. Scegliere il tipo di debug che si vuole usare:

   - **Avviare il file corrente**: avviare ed eseguire il debug del file nella finestra dell'editor attualmente attiva
   - **Avviare lo script**: avviare ed eseguire il debug del file o del comando specificato
   - **Sessione interattiva**: eseguire il debug dei comandi eseguiti dalla console integrata
   - **Attach** (Associa): collegare il debugger a un processo host di PowerShell in esecuzione

Visual Studio Code crea una directory e un file `.vscode\launch.json` nella radice della cartella dell'area di lavoro per archiviare la configurazione di debug. Se i file si trovano in un repository Git, in genere si vuole eseguire il commit del file `launch.json`. Il contenuto del file `launch.json` è il seguente:

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

Il file rappresenta gli scenari di debug comuni. Quando si apre il file nell'editor, viene visualizzato il pulsante **Aggiungi configurazione...** . È possibile fare clic su questo pulsante per aggiungere altre configurazioni di debug per PowerShell. Una configurazione utile da aggiungere è **PowerShell: avvia script**. Con questa configurazione, è possibile specificare un file contenente gli argomenti facoltativi che vengono usati ogni volta che si preme <kbd>F5</kbd>, a prescindere dal file attivo nell'editor.

Dopo aver definito la configurazione di debug, è possibile selezionare la configurazione che si vuole usare durante una sessione di debug. Selezionare una configurazione dall'elenco a discesa delle configurazioni di debug nella barra degli strumenti della visualizzazione **Debug**.

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Risoluzione dei problemi dell'estensione PowerShell per Visual Studio Code

Se si verificano problemi con Visual Studio Code durante lo sviluppo di script di PowerShell, vedere la [guida alla risoluzione dei problemi][troubleshooting] su GitHub.

## <a name="useful-resources"></a>Risorse utili

Sono disponibili video e blog che possono risultare utili per iniziare subito con l'estensione di PowerShell per Visual Studio Code:

### <a name="videos"></a>Video

- [Usare Visual Studio Code come editor di PowerShell predefinito](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code: approfondimenti sul debug degli script di PowerShell](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>Post di BLOG

- [Estensione PowerShell][pscdn]
- [Scrivere ed eseguire il debug degli script di PowerShell in Visual Studio Code][debug]
- [Indicazioni sul debug con Visual Studio Code][psdbgblog]
- [Debug di PowerShell in Visual Studio Code][psdbg-gh]
- [Introduzione allo sviluppo di PowerShell in Visual Studio Code][getting-started]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 1 ][editing-part1]
- [Funzionalità di modifica di Visual Studio Code per lo sviluppo di PowerShell - Parte 2 ][editing-part2]
- [Debug di script di PowerShell in Visual Studio Code - Parte 1][debugging-part1]
- [Debug di script di PowerShell in Visual Studio Code - Parte 2][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>Codice sorgente del progetto di estensione di PowerShell

I codici sorgente dell'estensione di PowerShell sono disponibili in [GitHub][psext-src].

Per contribuire, è necessario usare le richieste pull. Per iniziare, seguire la [documentazione per gli sviluppatori][dev-docs] su GitHub.

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[Problemi di GitHub]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
