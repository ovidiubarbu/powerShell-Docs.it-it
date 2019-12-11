---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117457"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="63c26-103">Come replicare l'esperienza di ISE in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="63c26-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="63c26-104">Mentre l'estensione di PowerShell per VSCode non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti ISE.</span><span class="sxs-lookup"><span data-stu-id="63c26-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="63c26-105">Questo documento cerca di elencare impostazioni che è possibile configurare in VSCode per rendere l'esperienza utente un po' più semplice rispetto all'ISE.</span><span class="sxs-lookup"><span data-stu-id="63c26-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="63c26-106">Associazioni di chiave</span><span class="sxs-lookup"><span data-stu-id="63c26-106">Key bindings</span></span>

| <span data-ttu-id="63c26-107">Function</span><span class="sxs-lookup"><span data-stu-id="63c26-107">Function</span></span>                              | <span data-ttu-id="63c26-108">Associazione ISE</span><span class="sxs-lookup"><span data-stu-id="63c26-108">ISE Binding</span></span>                  | <span data-ttu-id="63c26-109">Associazione VSCode</span><span class="sxs-lookup"><span data-stu-id="63c26-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="63c26-110">Debugger di Interrupt e di interruzione</span><span class="sxs-lookup"><span data-stu-id="63c26-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="63c26-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="63c26-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="63c26-113">Eseguire riga corrente/testo evidenziato</span><span class="sxs-lookup"><span data-stu-id="63c26-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="63c26-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="63c26-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="63c26-116">Elenco di frammenti di codice disponibili</span><span class="sxs-lookup"><span data-stu-id="63c26-116">List available snippets</span></span>               | <span data-ttu-id="63c26-117"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="63c26-118"><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="63c26-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="63c26-119">Associazioni di chiave personalizzate</span><span class="sxs-lookup"><span data-stu-id="63c26-119">Custom Key bindings</span></span>

<span data-ttu-id="63c26-120">È possibile [configurare le proprie associazioni di chiave personalizzate](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche VSCode.</span><span class="sxs-lookup"><span data-stu-id="63c26-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="63c26-121">Interfaccia utente di tipo ISE semplificata</span><span class="sxs-lookup"><span data-stu-id="63c26-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="63c26-122">Se si vuole semplificare l'interfaccia utente di Visual Studio Code e renderla più simile all'interfaccia utente ISE, applicare le due impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="63c26-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="63c26-123">Verranno nascoste le sezioni sottostanti della barra attività e della barra laterale di debug all'interno della casella rossa:</span><span class="sxs-lookup"><span data-stu-id="63c26-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![la sezione evidenziata include la barra attività e la barra laterale di debug](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="63c26-125">Il risultato finale è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="63c26-125">The end result looks like this:</span></span>

![Visualizzazione semplificata di VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="63c26-127">Completamento tramite TAB</span><span class="sxs-lookup"><span data-stu-id="63c26-127">Tab completion</span></span>

<span data-ttu-id="63c26-128">Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:</span><span class="sxs-lookup"><span data-stu-id="63c26-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="63c26-129">Questa impostazione è stata aggiunta direttamente in VSCode (piuttosto che nell'estensione).</span><span class="sxs-lookup"><span data-stu-id="63c26-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="63c26-130">Il comportamento è determinato direttamente da VSCode e non può essere modificato dall'estensione.</span><span class="sxs-lookup"><span data-stu-id="63c26-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="63c26-131">Nessuno stato attivo sulla console durante l'esecuzione</span><span class="sxs-lookup"><span data-stu-id="63c26-131">No focus on console when executing</span></span>

<span data-ttu-id="63c26-132">Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="63c26-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="63c26-133">Il valore predefinito è `true` per scopi di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="63c26-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="63c26-134">Non avviare la console integrata all'avvio</span><span class="sxs-lookup"><span data-stu-id="63c26-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="63c26-135">Per arrestare la console integrata all'avvio, impostare:</span><span class="sxs-lookup"><span data-stu-id="63c26-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="63c26-136">Il processo in background di PowerShell inizierà comunque dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.</span><span class="sxs-lookup"><span data-stu-id="63c26-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="63c26-137">Si supponga che i file siano di PowerShell per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="63c26-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="63c26-138">Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="63c26-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="63c26-139">Combinazione di colori</span><span class="sxs-lookup"><span data-stu-id="63c26-139">Color scheme</span></span>

<span data-ttu-id="63c26-140">Sono disponibili numerosi temi ISE per VSCode per rendere l'aspetto dell'editor molto più simile a quello di ISE.</span><span class="sxs-lookup"><span data-stu-id="63c26-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="63c26-141">Nel [riquadro comandi] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="63c26-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="63c26-142">Nell'elenco a discesa selezionare `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="63c26-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="63c26-143">È possibile impostare questo tema nelle impostazioni con:</span><span class="sxs-lookup"><span data-stu-id="63c26-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="63c26-144">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="63c26-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="63c26-145">Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.</span><span class="sxs-lookup"><span data-stu-id="63c26-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="63c26-146">Nel [riquadro comandi] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="63c26-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="63c26-147">Aprire l'ISE</span><span class="sxs-lookup"><span data-stu-id="63c26-147">Open in the ISE</span></span>

<span data-ttu-id="63c26-148">Se si desidera comunque aprire un file in ISE, è possibile usare <kbd>MAIUSC</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="63c26-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="63c26-149">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="63c26-149">Other resources</span></span>

- <span data-ttu-id="63c26-150">4sysops presenta [un interessante articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di VSCode per essere più simile all'ISE.</span><span class="sxs-lookup"><span data-stu-id="63c26-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="63c26-151">Mike F Robbins ha pubblicato [un interessante post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare VSCode.</span><span class="sxs-lookup"><span data-stu-id="63c26-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="63c26-152">Learn PowerShell presenta [un interessante recensione ](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sulla configurazione di VSCode per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="63c26-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="63c26-153">Altre impostazioni</span><span class="sxs-lookup"><span data-stu-id="63c26-153">More settings</span></span>

<span data-ttu-id="63c26-154">Se si conoscono altri modi per rendere VSCode più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali domande.</span><span class="sxs-lookup"><span data-stu-id="63c26-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="63c26-155">Siamo sempre lieti di accettare PR e contributi.</span><span class="sxs-lookup"><span data-stu-id="63c26-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="63c26-156">Suggerimenti per VSCode</span><span class="sxs-lookup"><span data-stu-id="63c26-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="63c26-157">Riquadro comandi</span><span class="sxs-lookup"><span data-stu-id="63c26-157">Command Palette</span></span>

<span data-ttu-id="63c26-158"><kbd>F1</kbd> OPPURE <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS)</span><span class="sxs-lookup"><span data-stu-id="63c26-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="63c26-159">Un modo pratico di eseguire comandi in VSCode.</span><span class="sxs-lookup"><span data-stu-id="63c26-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="63c26-160">Per altre informazioni, vedere [la documentazione di VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="63c26-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Riquadro comandi]: #command-palette
[Command Palette]: #command-palette
