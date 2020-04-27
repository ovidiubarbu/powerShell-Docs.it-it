---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005602"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Come replicare l'esperienza di ISE in Visual Studio Code

Mentre l'estensione di PowerShell per VS Code non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VS Code più naturale per gli utenti ISE.

Questo documento cerca di elencare le impostazioni che è possibile configurare in VS Code per rendere l'esperienza utente un po' più semplice rispetto all'ISE.

## <a name="ise-mode"></a>Modalità ISE

> [!NOTE]
> Questa funzionalità è disponibile nell'estensione di anteprima di PowerShell a partire dalla versione 2019.12.0 e nell'estensione di PowerShell a partire dalla versione 2020.3.0.

Il modo più semplice per replicare l'esperienza ISE in Visual Studio Code consiste nell'attivazione della "modalità ISE".
A tale scopo, aprire il riquadro comandi (<kbd>F1</kbd> O <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> O <kbd>CMD</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS) e digitare "Modalità ISE". Selezionare "PowerShell: Enable ISE Mode" (PowerShell: abilita modalità ISE) dall'elenco.

Questo comando applica automaticamente le impostazioni descritte di seguito. Il risultato è simile al seguente:

![Modalità ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>Impostazioni di configurazione della modalità ISE

La modalità ISE apporta le modifiche seguenti alle impostazioni di VS Code.

- Associazioni di chiave

  |               Funzione                |         Associazione ISE          |              Tasti di scelta rapida VS Code                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | Debugger di Interrupt e di interruzione          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | Eseguire riga corrente/testo evidenziato | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | Elenco di frammenti di codice disponibili               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd> |

  > [!NOTE]
  > È possibile [configurare i tasti di scelta rapida personalizzati](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) anche in VS Code.

- Interfaccia utente di tipo ISE semplificata

  Se si vuole semplificare l'interfaccia utente di Visual Studio Code e renderla più simile all'interfaccia utente ISE, applicare le due impostazioni seguenti:

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  Queste impostazioni nascondono le sezioni della barra attività e della barra laterale di debug visualizzate all'interno della casella rossa qui sotto:

  ![la sezione evidenziata include la barra attività e la barra laterale di debug](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  Il risultato finale è simile al seguente:

  ![Visualizzazione semplificata di VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Completamento tramite TAB

  Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:

  ```json
  "editor.tabCompletion": "on",
  ```

- Stato non attivo sulla console durante l'esecuzione

  Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  Il valore predefinito è `true` a scopo di accessibilità.

- Non avviare la console integrata all'avvio

  Per arrestare la console integrata all'avvio, impostare:

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > Il processo in background di PowerShell inizia comunque a offrire IntelliSense, analisi di script, passaggio ai simboli e così via, ma la console non verrà visualizzata.

- Si supponga che i file siano di PowerShell per impostazione predefinita

  Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:

  ```json
  "files.defaultLanguage": "powershell",
  ```

- Combinazione di colori

  Sono disponibili numerosi temi ISE per VS Code per rendere l'aspetto dell'editor molto più simile a quello di ISE.

  Nel [riquadro comandi][] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>. Nell'elenco a discesa selezionare `PowerShell ISE`.

  È possibile impostare questo tema nelle impostazioni con:

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- PowerShell Command Explorer

  Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.

  Nel [riquadro comandi][] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.

- Aprire l'ISE

  Se si vuole comunque aprire un file in Windows PowerShell ISE, aprire il [riquadro comandi][], cercare "open in ise" (Apri in ISE) e quindi selezionare **PowerShell: Open Current File in PowerShell ISE** (PowerShell: Apri file corrente in PowerShell ISE).

## <a name="other-resources"></a>Altre risorse

- 4sysops presenta [un interessante articolo][4sysops] sulla configurazione di VS Code per renderlo più simile all'ISE.
- Mike F Robbins ha pubblicato [un interessante post][mikefrobbins] su come configurare VS Code.
- Nelle risorse di formazione di PowerShell è disponibile [un interessante documento][learnpwsh] sulla configurazione di PowerShell.

## <a name="vs-code-tips"></a>Suggerimenti per VS Code

- Riquadro comandi

  Il riquadro comandi è un modo pratico per eseguire i comandi in VS Code. Aprire il riquadro comandi usando <kbd>F1</kbd> O <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> O <kbd>CMD</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS.

  Per altre informazioni, vedere la [documentazione di VS Code][vsc-docs].

- Disabilitare la Console di debug

  Se si prevede di usare VS Code per gli script di PowerShell, è possibile nascondere la **Console di debug** perché non viene usata dall'estensione di PowerShell. A tale scopo, fare clic con il pulsante destro del mouse su **Console di debug** e quindi fare clic sul segno di spunta per nasconderla.

## <a name="more-settings"></a>Altre impostazioni

Se si conoscono altri modi per rendere VS Code più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [Segnala un problema][] e porre eventuali domande.

Siamo sempre lieti di accettare PR e contributi.

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Riquadro comandi]: #vs-code-tips
[Segnala un problema]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
