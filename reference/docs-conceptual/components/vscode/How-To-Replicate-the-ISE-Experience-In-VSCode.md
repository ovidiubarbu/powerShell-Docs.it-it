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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="61ab6-103">Come replicare l'esperienza di ISE in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="61ab6-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="61ab6-104">Mentre l'estensione di PowerShell per Visual Studio code non seek parità di funzionalità completo con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti di ISE.</span><span class="sxs-lookup"><span data-stu-id="61ab6-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="61ab6-105">Questo documento cerca di impostazioni di elenco che è possibile configurare in Visual Studio code per migliorare l'esperienza un po' più familiare rispetto alla finestra di ISE utente.</span><span class="sxs-lookup"><span data-stu-id="61ab6-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="61ab6-106">Tasti di scelta rapida</span><span class="sxs-lookup"><span data-stu-id="61ab6-106">Key bindings</span></span>

| <span data-ttu-id="61ab6-107">Function</span><span class="sxs-lookup"><span data-stu-id="61ab6-107">Function</span></span>                              | <span data-ttu-id="61ab6-108">Associazione di ISE</span><span class="sxs-lookup"><span data-stu-id="61ab6-108">ISE Binding</span></span>                  | <span data-ttu-id="61ab6-109">Associazione di Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="61ab6-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="61ab6-110">Debugger di interruzione e di interruzione</span><span class="sxs-lookup"><span data-stu-id="61ab6-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="61ab6-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="61ab6-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="61ab6-113">Eseguire testo riga/evidenziato corrente</span><span class="sxs-lookup"><span data-stu-id="61ab6-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="61ab6-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="61ab6-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="61ab6-116">Elenco di frammenti disponibili</span><span class="sxs-lookup"><span data-stu-id="61ab6-116">List available snippets</span></span>               | <span data-ttu-id="61ab6-117"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="61ab6-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="61ab6-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="61ab6-119">Associazioni di chiavi personalizzate</span><span class="sxs-lookup"><span data-stu-id="61ab6-119">Custom Key bindings</span></span>

<span data-ttu-id="61ab6-120">È possibile [configurare il proprio esempio tasti di scelta rapida](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="61ab6-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="61ab6-121">Completamento tramite TAB</span><span class="sxs-lookup"><span data-stu-id="61ab6-121">Tab completion</span></span>

<span data-ttu-id="61ab6-122">Per abilitare più simile a ISE completamento tramite TAB, aggiungere questa impostazione:</span><span class="sxs-lookup"><span data-stu-id="61ab6-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="61ab6-123">Questa impostazione è stato aggiunto direttamente in Visual Studio code (piuttosto che nell'estensione).</span><span class="sxs-lookup"><span data-stu-id="61ab6-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="61ab6-124">Il comportamento è determinato da VSCode direttamente e non può essere modificato dall'estensione.</span><span class="sxs-lookup"><span data-stu-id="61ab6-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="61ab6-125">Non lo stato attivo sulla console durante l'esecuzione</span><span class="sxs-lookup"><span data-stu-id="61ab6-125">No focus on console when executing</span></span>

<span data-ttu-id="61ab6-126">Per mantenere lo stato attivo nell'editor, quando si esegue con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="61ab6-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="61ab6-127">Il valore predefinito è `true` per scopi di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="61ab6-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="61ab6-128">Non avviare la console integrata all'avvio</span><span class="sxs-lookup"><span data-stu-id="61ab6-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="61ab6-129">Per interrompere la console integrata all'avvio, impostare:</span><span class="sxs-lookup"><span data-stu-id="61ab6-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="61ab6-130">Il processo di PowerShell in background ancora inizierà dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.</span><span class="sxs-lookup"><span data-stu-id="61ab6-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="61ab6-131">Si supponga che i file siano di PowerShell per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="61ab6-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="61ab6-132">Per rendere i file nuovi o senza titolo, registrare come PowerShell per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="61ab6-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="61ab6-133">Combinazione di colori</span><span class="sxs-lookup"><span data-stu-id="61ab6-133">Color scheme</span></span>

<span data-ttu-id="61ab6-134">Sono disponibili numerosi temi ISE per Visual Studio code rendere l'editor molto più simile di ISE.</span><span class="sxs-lookup"><span data-stu-id="61ab6-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="61ab6-135">Nel [riquadro comandi] tipo `theme` ottenere `Preferences: Color Theme` , quindi premere <kbd>invio</kbd>.</span><span class="sxs-lookup"><span data-stu-id="61ab6-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="61ab6-136">Nell'elenco a discesa, selezionare `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="61ab6-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="61ab6-137">È possibile impostare questo tema nelle impostazioni:</span><span class="sxs-lookup"><span data-stu-id="61ab6-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="61ab6-138">Explorer di comando di PowerShell</span><span class="sxs-lookup"><span data-stu-id="61ab6-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="61ab6-139">Grazie al lavoro di [ @corbob ](https://github.com/corbob), l'estensione di PowerShell è l'inizio di un proprio explorer di comando.</span><span class="sxs-lookup"><span data-stu-id="61ab6-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="61ab6-140">Nel [riquadro comandi], immettere `PowerShell Command Explorer` , quindi premere <kbd>invio</kbd>.</span><span class="sxs-lookup"><span data-stu-id="61ab6-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="61ab6-141">Apri in ISE</span><span class="sxs-lookup"><span data-stu-id="61ab6-141">Open in the ISE</span></span>

<span data-ttu-id="61ab6-142">Se vuole aprire un file in ISE, comunque, è possibile usare <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="61ab6-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="61ab6-143">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="61ab6-143">Other resources</span></span>

- <span data-ttu-id="61ab6-144">ha 4sysops [un ottimo articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di Visual Studio code per essere più simile di ISE.</span><span class="sxs-lookup"><span data-stu-id="61ab6-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="61ab6-145">Ha Mike F Robbins [un ottimo post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="61ab6-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="61ab6-146">Informazioni su PowerShell ha [un'operazione di scrittura eccellente backup](https://www.learnpwsh.com/setup-vs-code-for-powershell/) all'acquisizione di VSCode di installazione per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="61ab6-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="61ab6-147">Altre impostazioni</span><span class="sxs-lookup"><span data-stu-id="61ab6-147">More settings</span></span>

<span data-ttu-id="61ab6-148">Se si conoscono gli altri modi per rendere VSCode più familiare per gli utenti ISE, contribuiscono a questo documento. Se è presente una configurazione di compatibilità si sta cercando, ma non è possibile trovare alcun modo per abilitarlo [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali!</span><span class="sxs-lookup"><span data-stu-id="61ab6-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="61ab6-149">Siamo sempre lieti di accettare le richieste pull e anche i contributi!</span><span class="sxs-lookup"><span data-stu-id="61ab6-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="61ab6-150">Suggerimenti per Visual Studio code</span><span class="sxs-lookup"><span data-stu-id="61ab6-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="61ab6-151">Riquadro comandi</span><span class="sxs-lookup"><span data-stu-id="61ab6-151">Command Palette</span></span>

<span data-ttu-id="61ab6-152"><kbd>F1</kbd> oppure <kbd>Ctrl</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Shift</kbd>+<kbd>P</kbd> in macOS)</span><span class="sxs-lookup"><span data-stu-id="61ab6-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="61ab6-153">Un modo utile l'esecuzione di comandi in Visual Studio code.</span><span class="sxs-lookup"><span data-stu-id="61ab6-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="61ab6-154">Per altre informazioni, vedere [la documentazione di Visual Studio code](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="61ab6-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Riquadro comandi]: #command-palette
[Command Palette]: #command-palette
