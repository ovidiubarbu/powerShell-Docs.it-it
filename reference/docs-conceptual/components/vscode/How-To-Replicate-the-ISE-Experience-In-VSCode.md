---
title: Come replicare l'esperienza di ISE in Visual Studio Code
description: Come replicare l'esperienza di ISE in Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058523"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="58a56-103">Come replicare l'esperienza di ISE in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="58a56-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="58a56-104">Mentre l'estensione di PowerShell per VSCode non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti ISE.</span><span class="sxs-lookup"><span data-stu-id="58a56-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="58a56-105">Questo documento cerca di elencare impostazioni che è possibile configurare in VSCode per rendere l'esperienza utente un po' più semplice rispetto all'ISE.</span><span class="sxs-lookup"><span data-stu-id="58a56-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="58a56-106">Associazioni di chiave</span><span class="sxs-lookup"><span data-stu-id="58a56-106">Key bindings</span></span>

| <span data-ttu-id="58a56-107">Function</span><span class="sxs-lookup"><span data-stu-id="58a56-107">Function</span></span>                              | <span data-ttu-id="58a56-108">Associazione ISE</span><span class="sxs-lookup"><span data-stu-id="58a56-108">ISE Binding</span></span>                  | <span data-ttu-id="58a56-109">Associazione VSCode</span><span class="sxs-lookup"><span data-stu-id="58a56-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="58a56-110">Debugger di Interrupt e di interruzione</span><span class="sxs-lookup"><span data-stu-id="58a56-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="58a56-111"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="58a56-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="58a56-113">Eseguire riga corrente/testo evidenziato</span><span class="sxs-lookup"><span data-stu-id="58a56-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="58a56-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="58a56-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="58a56-116">Elenco di frammenti di codice disponibili</span><span class="sxs-lookup"><span data-stu-id="58a56-116">List available snippets</span></span>               | <span data-ttu-id="58a56-117"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="58a56-118"><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="58a56-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="58a56-119">Associazioni di chiave personalizzate</span><span class="sxs-lookup"><span data-stu-id="58a56-119">Custom Key bindings</span></span>

<span data-ttu-id="58a56-120">È possibile [configurare le proprie associazioni di chiave personalizzate](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche VSCode.</span><span class="sxs-lookup"><span data-stu-id="58a56-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="58a56-121">Completamento tramite TAB</span><span class="sxs-lookup"><span data-stu-id="58a56-121">Tab completion</span></span>

<span data-ttu-id="58a56-122">Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:</span><span class="sxs-lookup"><span data-stu-id="58a56-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="58a56-123">Questa impostazione è stata aggiunta direttamente in VSCode (piuttosto che nell'estensione).</span><span class="sxs-lookup"><span data-stu-id="58a56-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="58a56-124">Il comportamento è determinato direttamente da VSCode e non può essere modificato dall'estensione.</span><span class="sxs-lookup"><span data-stu-id="58a56-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="58a56-125">Nessuno stato attivo sulla console durante l'esecuzione</span><span class="sxs-lookup"><span data-stu-id="58a56-125">No focus on console when executing</span></span>

<span data-ttu-id="58a56-126">Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="58a56-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="58a56-127">Il valore predefinito è `true` per scopi di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="58a56-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="58a56-128">Non avviare la console integrata all'avvio</span><span class="sxs-lookup"><span data-stu-id="58a56-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="58a56-129">Per arrestare la console integrata all'avvio, impostare:</span><span class="sxs-lookup"><span data-stu-id="58a56-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="58a56-130">Il processo in background di PowerShell inizierà comunque dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.</span><span class="sxs-lookup"><span data-stu-id="58a56-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="58a56-131">Si supponga che i file siano di PowerShell per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="58a56-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="58a56-132">Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="58a56-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="58a56-133">Combinazione di colori</span><span class="sxs-lookup"><span data-stu-id="58a56-133">Color scheme</span></span>

<span data-ttu-id="58a56-134">Sono disponibili numerosi temi ISE per VSCode per rendere l'aspetto dell'editor molto più simile a quello di ISE.</span><span class="sxs-lookup"><span data-stu-id="58a56-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="58a56-135">Nel [riquadro comandi] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="58a56-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="58a56-136">Nell'elenco a discesa selezionare `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="58a56-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="58a56-137">È possibile impostare questo tema nelle impostazioni con:</span><span class="sxs-lookup"><span data-stu-id="58a56-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="58a56-138">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="58a56-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="58a56-139">Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.</span><span class="sxs-lookup"><span data-stu-id="58a56-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="58a56-140">Nel [riquadro comandi] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="58a56-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="58a56-141">Aprire l'ISE</span><span class="sxs-lookup"><span data-stu-id="58a56-141">Open in the ISE</span></span>

<span data-ttu-id="58a56-142">Se si desidera comunque aprire un file in ISE, è possibile usare <kbd>MAIUSC</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="58a56-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="58a56-143">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="58a56-143">Other resources</span></span>

- <span data-ttu-id="58a56-144">4sysops presenta [un interessante articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di VSCode per essere più simile all'ISE.</span><span class="sxs-lookup"><span data-stu-id="58a56-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="58a56-145">Mike F Robbins ha pubblicato [un interessante post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare VSCode.</span><span class="sxs-lookup"><span data-stu-id="58a56-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="58a56-146">Learn PowerShell presenta [un interessante recensione ](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sulla configurazione di VSCode per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="58a56-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="58a56-147">Altre impostazioni</span><span class="sxs-lookup"><span data-stu-id="58a56-147">More settings</span></span>

<span data-ttu-id="58a56-148">Se si conoscono altri modi per rendere VSCode più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali domande.</span><span class="sxs-lookup"><span data-stu-id="58a56-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="58a56-149">Siamo sempre lieti di accettare PR e contributi.</span><span class="sxs-lookup"><span data-stu-id="58a56-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="58a56-150">Suggerimenti per VSCode</span><span class="sxs-lookup"><span data-stu-id="58a56-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="58a56-151">Riquadro comandi</span><span class="sxs-lookup"><span data-stu-id="58a56-151">Command Palette</span></span>

<span data-ttu-id="58a56-152"><kbd>F1</kbd> OPPURE <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS)</span><span class="sxs-lookup"><span data-stu-id="58a56-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="58a56-153">Un modo pratico di eseguire comandi in VSCode.</span><span class="sxs-lookup"><span data-stu-id="58a56-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="58a56-154">Per altre informazioni, vedere [la documentazione di VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="58a56-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Riquadro comandi]: #command-palette
[Command Palette]: #command-palette
