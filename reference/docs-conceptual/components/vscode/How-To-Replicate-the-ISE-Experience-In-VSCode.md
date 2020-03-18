---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279256"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Come replicare l'esperienza di ISE in Visual Studio Code

Mentre l'estensione di PowerShell per VSCode non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti ISE.

Questo documento cerca di elencare impostazioni che è possibile configurare in VSCode per rendere l'esperienza utente un po' più semplice rispetto all'ISE.

## <a name="ise-mode"></a>Modalità ISE

> [!NOTE]
> Questa funzionalità è disponibile nell'estensione di anteprima di PowerShell a partire dalla versione 2019.12.0 e nell'estensione di PowerShell a partire dalla versione 2020.3.0.

Il modo più semplice per replicare l'esperienza ISE in Visual Studio Code consiste nell'attivazione della "modalità ISE".
A tale scopo, aprire il riquadro comandi (<kbd>F1</kbd> O <kbd>Ctrl</kbd>+<kbd>Maiusc</kbd>+<kbd>P</kbd> O <kbd>Cmd</kbd>+<kbd>Maiusc</kbd>+<kbd>P</kbd> in macOS) e digitare "ISE Mode" (Modalità ISE).
Selezionare "PowerShell: Enable ISE Mode" (PowerShell: abilita modalità ISE) dall'elenco.

Questo comando applica automaticamente molte delle impostazioni descritte in questo documento.
Il risultato è simile al seguente:

![Modalità ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

Il resto di questo articolo include informazioni più dettagliate sulle impostazioni in modalità ISE e su alcune impostazioni aggiuntive.

## <a name="key-bindings"></a>Associazioni di chiave

| Funzione                              | Associazione ISE                  | Associazione VSCode                              |
| ----------------                      | -----------                  | --------------                              |
| Debugger di Interrupt e di interruzione          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Eseguire riga corrente/testo evidenziato | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Elenco di frammenti di codice disponibili               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Associazioni di chiave personalizzate

È possibile [configurare le proprie associazioni di chiave personalizzate](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche VSCode.

## <a name="simplified-ise-like-ui"></a>Interfaccia utente di tipo ISE semplificata

Se si vuole semplificare l'interfaccia utente di Visual Studio Code e renderla più simile all'interfaccia utente ISE, applicare le due impostazioni seguenti:

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> Queste impostazioni sono incluse nella ["modalità ISE"](#ise-mode).

Verranno nascoste le sezioni sottostanti della barra attività e della barra laterale di debug all'interno della casella rossa:

![la sezione evidenziata include la barra attività e la barra laterale di debug](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Il risultato finale è simile al seguente:

![Visualizzazione semplificata di VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Completamento tramite TAB

Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Questa impostazione è stata aggiunta direttamente in VSCode (piuttosto che nell'estensione). Il comportamento è determinato direttamente da VSCode e non può essere modificato dall'estensione.

> [!NOTE]
> Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).

## <a name="no-focus-on-console-when-executing"></a>Stato non attivo sulla console durante l'esecuzione

Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).

Il valore predefinito è `true` a scopo di accessibilità.

## <a name="dont-start-integrated-console-on-startup"></a>Non avviare la console integrata all'avvio

Per arrestare la console integrata all'avvio, impostare:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Il processo in background di PowerShell inizierà comunque dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.

## <a name="assume-files-are-powershell-by-default"></a>Si supponga che i file siano di PowerShell per impostazione predefinita

Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).

## <a name="color-scheme"></a>Combinazione di colori

Sono disponibili numerosi temi ISE per VSCode per rendere l'aspetto dell'editor molto più simile a quello di ISE.

Nel [riquadro comandi] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.
Nell'elenco a discesa selezionare `PowerShell ISE`.

È possibile impostare questo tema nelle impostazioni con:

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).

## <a name="powershell-command-explorer"></a>PowerShell Command Explorer

Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.

Nel [riquadro comandi] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.

> [!NOTE]
> Questo strumento è visualizzato automaticamente nella ["modalità ISE"](#ise-mode).

## <a name="open-in-the-ise"></a>Aprire l'ISE

Se si desidera comunque aprire un file in ISE, è possibile usare <kbd>MAIUSC</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Altre risorse

- 4sysops presenta [un interessante articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di VSCode per essere più simile all'ISE.
- Mike F Robbins ha pubblicato [un interessante post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare VSCode.
- Learn PowerShell presenta [un interessante recensione ](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sulla configurazione di VSCode per PowerShell.

## <a name="more-settings"></a>Altre impostazioni

Se si conoscono altri modi per rendere VSCode più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali domande.

Siamo sempre lieti di accettare PR e contributi.

## <a name="vscode-tips"></a>Suggerimenti per VSCode

### <a name="command-palette"></a>Riquadro comandi

<kbd>F1</kbd> OPPURE <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS)

Un modo pratico di eseguire comandi in VSCode.
Per altre informazioni, vedere [la documentazione di VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Riquadro comandi]: #command-palette
