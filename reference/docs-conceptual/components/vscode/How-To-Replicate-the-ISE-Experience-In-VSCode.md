---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681949"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Come replicare l'esperienza di ISE in Visual Studio Code

Mentre l'estensione di PowerShell per Visual Studio code non seek parità di funzionalità completo con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti di ISE.

Questo documento cerca di impostazioni di elenco che è possibile configurare in Visual Studio code per migliorare l'esperienza un po' più familiare rispetto alla finestra di ISE utente.

## <a name="key-bindings"></a>Tasti di scelta rapida

| Function                              | Associazione di ISE                  | Associazione di Visual Studio code                              |
| ----------------                      | -----------                  | --------------                              |
| Debugger di interruzione e di interruzione          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Eseguire testo riga/evidenziato corrente | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Elenco di frammenti disponibili               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Associazioni di chiavi personalizzate

È possibile [configurare il proprio esempio tasti di scelta rapida](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche Visual Studio code.

## <a name="tab-completion"></a>Completamento tramite TAB

Per abilitare più simile a ISE completamento tramite TAB, aggiungere questa impostazione:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Questa impostazione è stato aggiunto direttamente in Visual Studio code (piuttosto che nell'estensione). Il comportamento è determinato da VSCode direttamente e non può essere modificato dall'estensione.

## <a name="no-focus-on-console-when-executing"></a>Non lo stato attivo sulla console durante l'esecuzione

Per mantenere lo stato attivo nell'editor, quando si esegue con <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Il valore predefinito è `true` per scopi di accessibilità.

## <a name="dont-start-integrated-console-on-startup"></a>Non avviare la console integrata all'avvio

Per interrompere la console integrata all'avvio, impostare:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Il processo di PowerShell in background ancora inizierà dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.

## <a name="assume-files-are-powershell-by-default"></a>Si supponga che i file siano di PowerShell per impostazione predefinita

Per rendere i file nuovi o senza titolo, registrare come PowerShell per impostazione predefinita:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Combinazione di colori

Sono disponibili numerosi temi ISE per Visual Studio code rendere l'editor molto più simile di ISE.

Nel [riquadro comandi] tipo `theme` ottenere `Preferences: Color Theme` , quindi premere <kbd>invio</kbd>.
Nell'elenco a discesa, selezionare `PowerShell ISE`.

È possibile impostare questo tema nelle impostazioni:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>Explorer di comando di PowerShell

Grazie al lavoro di [ @corbob ](https://github.com/corbob), l'estensione di PowerShell è l'inizio di un proprio explorer di comando.

Nel [riquadro comandi], immettere `PowerShell Command Explorer` , quindi premere <kbd>invio</kbd>.

## <a name="open-in-the-ise"></a>Apri in ISE

Se vuole aprire un file in ISE, comunque, è possibile usare <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Altre risorse

- ha 4sysops [un ottimo articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di Visual Studio code per essere più simile di ISE.
- Ha Mike F Robbins [un ottimo post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare Visual Studio code.
- Informazioni su PowerShell ha [un'operazione di scrittura eccellente backup](https://www.learnpwsh.com/setup-vs-code-for-powershell/) all'acquisizione di VSCode di installazione per PowerShell.

## <a name="more-settings"></a>Altre impostazioni

Se si conoscono gli altri modi per rendere VSCode più familiare per gli utenti ISE, contribuiscono a questo documento. Se è presente una configurazione di compatibilità si sta cercando, ma non è possibile trovare alcun modo per abilitarlo [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali!

Siamo sempre lieti di accettare le richieste pull e anche i contributi!

## <a name="vscode-tips"></a>Suggerimenti per Visual Studio code

### <a name="command-palette"></a>Riquadro comandi

<kbd>F1</kbd> oppure <kbd>Ctrl</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> in macOS)

Un modo utile l'esecuzione di comandi in Visual Studio code.
Per altre informazioni, vedere [la documentazione di Visual Studio code](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Riquadro comandi]: #command-palette
