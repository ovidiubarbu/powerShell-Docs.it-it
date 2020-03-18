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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="f6675-103">Come replicare l'esperienza di ISE in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="f6675-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="f6675-104">Mentre l'estensione di PowerShell per VSCode non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VSCode più naturale per gli utenti ISE.</span><span class="sxs-lookup"><span data-stu-id="f6675-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="f6675-105">Questo documento cerca di elencare impostazioni che è possibile configurare in VSCode per rendere l'esperienza utente un po' più semplice rispetto all'ISE.</span><span class="sxs-lookup"><span data-stu-id="f6675-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="f6675-106">Modalità ISE</span><span class="sxs-lookup"><span data-stu-id="f6675-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="f6675-107">Questa funzionalità è disponibile nell'estensione di anteprima di PowerShell a partire dalla versione 2019.12.0 e nell'estensione di PowerShell a partire dalla versione 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="f6675-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="f6675-108">Il modo più semplice per replicare l'esperienza ISE in Visual Studio Code consiste nell'attivazione della "modalità ISE".</span><span class="sxs-lookup"><span data-stu-id="f6675-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="f6675-109">A tale scopo, aprire il riquadro comandi (<kbd>F1</kbd> O <kbd>Ctrl</kbd>+<kbd>Maiusc</kbd>+<kbd>P</kbd> O <kbd>Cmd</kbd>+<kbd>Maiusc</kbd>+<kbd>P</kbd> in macOS) e digitare "ISE Mode" (Modalità ISE).</span><span class="sxs-lookup"><span data-stu-id="f6675-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="f6675-110">Selezionare "PowerShell: Enable ISE Mode" (PowerShell: abilita modalità ISE) dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="f6675-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="f6675-111">Questo comando applica automaticamente molte delle impostazioni descritte in questo documento.</span><span class="sxs-lookup"><span data-stu-id="f6675-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="f6675-112">Il risultato è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f6675-112">The result looks like this:</span></span>

![Modalità ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="f6675-114">Il resto di questo articolo include informazioni più dettagliate sulle impostazioni in modalità ISE e su alcune impostazioni aggiuntive.</span><span class="sxs-lookup"><span data-stu-id="f6675-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="f6675-115">Associazioni di chiave</span><span class="sxs-lookup"><span data-stu-id="f6675-115">Key bindings</span></span>

| <span data-ttu-id="f6675-116">Funzione</span><span class="sxs-lookup"><span data-stu-id="f6675-116">Function</span></span>                              | <span data-ttu-id="f6675-117">Associazione ISE</span><span class="sxs-lookup"><span data-stu-id="f6675-117">ISE Binding</span></span>                  | <span data-ttu-id="f6675-118">Associazione VSCode</span><span class="sxs-lookup"><span data-stu-id="f6675-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="f6675-119">Debugger di Interrupt e di interruzione</span><span class="sxs-lookup"><span data-stu-id="f6675-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="f6675-120"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="f6675-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="f6675-122">Eseguire riga corrente/testo evidenziato</span><span class="sxs-lookup"><span data-stu-id="f6675-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="f6675-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="f6675-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="f6675-125">Elenco di frammenti di codice disponibili</span><span class="sxs-lookup"><span data-stu-id="f6675-125">List available snippets</span></span>               | <span data-ttu-id="f6675-126"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="f6675-127"><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="f6675-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="f6675-128">Associazioni di chiave personalizzate</span><span class="sxs-lookup"><span data-stu-id="f6675-128">Custom Key bindings</span></span>

<span data-ttu-id="f6675-129">È possibile [configurare le proprie associazioni di chiave personalizzate](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in anche VSCode.</span><span class="sxs-lookup"><span data-stu-id="f6675-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="f6675-130">Interfaccia utente di tipo ISE semplificata</span><span class="sxs-lookup"><span data-stu-id="f6675-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="f6675-131">Se si vuole semplificare l'interfaccia utente di Visual Studio Code e renderla più simile all'interfaccia utente ISE, applicare le due impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="f6675-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="f6675-132">Queste impostazioni sono incluse nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="f6675-133">Verranno nascoste le sezioni sottostanti della barra attività e della barra laterale di debug all'interno della casella rossa:</span><span class="sxs-lookup"><span data-stu-id="f6675-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![la sezione evidenziata include la barra attività e la barra laterale di debug](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="f6675-135">Il risultato finale è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="f6675-135">The end result looks like this:</span></span>

![Visualizzazione semplificata di VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="f6675-137">Completamento tramite TAB</span><span class="sxs-lookup"><span data-stu-id="f6675-137">Tab completion</span></span>

<span data-ttu-id="f6675-138">Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:</span><span class="sxs-lookup"><span data-stu-id="f6675-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="f6675-139">Questa impostazione è stata aggiunta direttamente in VSCode (piuttosto che nell'estensione).</span><span class="sxs-lookup"><span data-stu-id="f6675-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="f6675-140">Il comportamento è determinato direttamente da VSCode e non può essere modificato dall'estensione.</span><span class="sxs-lookup"><span data-stu-id="f6675-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="f6675-141">Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="f6675-142">Stato non attivo sulla console durante l'esecuzione</span><span class="sxs-lookup"><span data-stu-id="f6675-142">No focus on console when executing</span></span>

<span data-ttu-id="f6675-143">Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="f6675-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="f6675-144">Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="f6675-145">Il valore predefinito è `true` a scopo di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="f6675-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="f6675-146">Non avviare la console integrata all'avvio</span><span class="sxs-lookup"><span data-stu-id="f6675-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="f6675-147">Per arrestare la console integrata all'avvio, impostare:</span><span class="sxs-lookup"><span data-stu-id="f6675-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="f6675-148">Il processo in background di PowerShell inizierà comunque dal momento che offre IntelliSense, analisi di script, passaggio ai simboli e così via. Ma non verrà visualizzata la console.</span><span class="sxs-lookup"><span data-stu-id="f6675-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="f6675-149">Si supponga che i file siano di PowerShell per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="f6675-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="f6675-150">Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="f6675-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="f6675-151">Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="f6675-152">Combinazione di colori</span><span class="sxs-lookup"><span data-stu-id="f6675-152">Color scheme</span></span>

<span data-ttu-id="f6675-153">Sono disponibili numerosi temi ISE per VSCode per rendere l'aspetto dell'editor molto più simile a quello di ISE.</span><span class="sxs-lookup"><span data-stu-id="f6675-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="f6675-154">Nel [riquadro comandi] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f6675-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="f6675-155">Nell'elenco a discesa selezionare `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="f6675-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="f6675-156">È possibile impostare questo tema nelle impostazioni con:</span><span class="sxs-lookup"><span data-stu-id="f6675-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="f6675-157">Questa impostazione è inclusa nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="f6675-158">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="f6675-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="f6675-159">Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.</span><span class="sxs-lookup"><span data-stu-id="f6675-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="f6675-160">Nel [riquadro comandi] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f6675-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="f6675-161">Questo strumento è visualizzato automaticamente nella ["modalità ISE"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="f6675-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="f6675-162">Aprire l'ISE</span><span class="sxs-lookup"><span data-stu-id="f6675-162">Open in the ISE</span></span>

<span data-ttu-id="f6675-163">Se si desidera comunque aprire un file in ISE, è possibile usare <kbd>MAIUSC</kbd>+<kbd>ALT</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f6675-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="f6675-164">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="f6675-164">Other resources</span></span>

- <span data-ttu-id="f6675-165">4sysops presenta [un interessante articolo](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) sulla configurazione di VSCode per essere più simile all'ISE.</span><span class="sxs-lookup"><span data-stu-id="f6675-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="f6675-166">Mike F Robbins ha pubblicato [un interessante post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) su come configurare VSCode.</span><span class="sxs-lookup"><span data-stu-id="f6675-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="f6675-167">Learn PowerShell presenta [un interessante recensione ](https://www.learnpwsh.com/setup-vs-code-for-powershell/) sulla configurazione di VSCode per PowerShell.</span><span class="sxs-lookup"><span data-stu-id="f6675-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="f6675-168">Altre impostazioni</span><span class="sxs-lookup"><span data-stu-id="f6675-168">More settings</span></span>

<span data-ttu-id="f6675-169">Se si conoscono altri modi per rendere VSCode più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [segnalare un problema](https://github.com/PowerShell/vscode-powershell/issues/new/choose) e porre eventuali domande.</span><span class="sxs-lookup"><span data-stu-id="f6675-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="f6675-170">Siamo sempre lieti di accettare PR e contributi.</span><span class="sxs-lookup"><span data-stu-id="f6675-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="f6675-171">Suggerimenti per VSCode</span><span class="sxs-lookup"><span data-stu-id="f6675-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="f6675-172">Riquadro comandi</span><span class="sxs-lookup"><span data-stu-id="f6675-172">Command Palette</span></span>

<span data-ttu-id="f6675-173"><kbd>F1</kbd> OPPURE <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS)</span><span class="sxs-lookup"><span data-stu-id="f6675-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="f6675-174">Un modo pratico di eseguire comandi in VSCode.</span><span class="sxs-lookup"><span data-stu-id="f6675-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="f6675-175">Per altre informazioni, vedere [la documentazione di VSCode](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="f6675-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Riquadro comandi]: #command-palette
[Command Palette]: #command-palette
