---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: a6e54a305fdeb6482321c77da8066d2f991c93e1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2019
ms.locfileid: "74117457"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Come replicare l'esperienza di ISE in Visual Studio Code

Mentre l'estensione di PowerShell per VSCode non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti ISE.

Questo documento cerca di elencare impostazioni che è possibile configurare in VSCode per rendere l'esperienza utente un po' più semplice rispetto all'ISE.

## <a name="key-bindings"></a>Associazioni di chiave

| Function                              | Associazione ISE                  | Associazione VSCode                              |
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

Verranno nascoste le sezioni sottostanti della barra attività e della barra laterale di debug all'interno della casella rossa:

![la sezione evidenziata include la barra attività e la barra laterale di debug](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Il risultato finale è simile al seguente:

![Visualizzazione semplificata di VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Completamento tramite TAB

Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Questa impostazione è stata aggiunta direttamente in VSCode (piuttosto che nell'estensione). Il comportamento è determinato direttamente da VSCode e non può essere modificato dall'estensione.

## <a name="no-focus-on-console-when-executing"></a>Nessuno stato attivo sulla console durante l'esecuzione

Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Il valore predefinito è `true` per scopi di accessibilità.

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

## <a name="color-scheme"></a>Combinazione di colori

Sono disponibili numerosi temi ISE per VSCode per rendere l'aspetto dell'editor molto più simile a quello di ISE.

Nel [riquadro comandi] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.
Nell'elenco a discesa selezionare `PowerShell ISE`.

È possibile impostare questo tema nelle impostazioni con:

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell Command Explorer

Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.

Nel [riquadro comandi] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.

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

<kbd>F1</kbd> OPPURE <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS)

Un modo pratico di eseguire comandi in VSCode.
Per altre informazioni, vedere [la documentazione di VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Riquadro comandi]: #command-palette
