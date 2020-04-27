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
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="a2479-103">Come replicare l'esperienza di ISE in Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="a2479-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="a2479-104">Mentre l'estensione di PowerShell per VS Code non ricerca la parità delle funzionalità completa con PowerShell ISE, esistono funzionalità in grado di rendere l'esperienza di VS Code più naturale per gli utenti ISE.</span><span class="sxs-lookup"><span data-stu-id="a2479-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="a2479-105">Questo documento cerca di elencare le impostazioni che è possibile configurare in VS Code per rendere l'esperienza utente un po' più semplice rispetto all'ISE.</span><span class="sxs-lookup"><span data-stu-id="a2479-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="a2479-106">Modalità ISE</span><span class="sxs-lookup"><span data-stu-id="a2479-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="a2479-107">Questa funzionalità è disponibile nell'estensione di anteprima di PowerShell a partire dalla versione 2019.12.0 e nell'estensione di PowerShell a partire dalla versione 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="a2479-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="a2479-108">Il modo più semplice per replicare l'esperienza ISE in Visual Studio Code consiste nell'attivazione della "modalità ISE".</span><span class="sxs-lookup"><span data-stu-id="a2479-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="a2479-109">A tale scopo, aprire il riquadro comandi (<kbd>F1</kbd> O <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> O <kbd>CMD</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS) e digitare "Modalità ISE".</span><span class="sxs-lookup"><span data-stu-id="a2479-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="a2479-110">Selezionare "PowerShell: Enable ISE Mode" (PowerShell: abilita modalità ISE) dall'elenco.</span><span class="sxs-lookup"><span data-stu-id="a2479-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="a2479-111">Questo comando applica automaticamente le impostazioni descritte di seguito. Il risultato è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a2479-111">This command automatically applies the settings described below The result looks like this:</span></span>

![Modalità ISE](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="a2479-113">Impostazioni di configurazione della modalità ISE</span><span class="sxs-lookup"><span data-stu-id="a2479-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="a2479-114">La modalità ISE apporta le modifiche seguenti alle impostazioni di VS Code.</span><span class="sxs-lookup"><span data-stu-id="a2479-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="a2479-115">Associazioni di chiave</span><span class="sxs-lookup"><span data-stu-id="a2479-115">Key bindings</span></span>

  |               <span data-ttu-id="a2479-116">Funzione</span><span class="sxs-lookup"><span data-stu-id="a2479-116">Function</span></span>                |         <span data-ttu-id="a2479-117">Associazione ISE</span><span class="sxs-lookup"><span data-stu-id="a2479-117">ISE Binding</span></span>          |              <span data-ttu-id="a2479-118">Tasti di scelta rapida VS Code</span><span class="sxs-lookup"><span data-stu-id="a2479-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="a2479-119">Debugger di Interrupt e di interruzione</span><span class="sxs-lookup"><span data-stu-id="a2479-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="a2479-120"><kbd>CTRL</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="a2479-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="a2479-122">Eseguire riga corrente/testo evidenziato</span><span class="sxs-lookup"><span data-stu-id="a2479-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="a2479-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="a2479-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="a2479-125">Elenco di frammenti di codice disponibili</span><span class="sxs-lookup"><span data-stu-id="a2479-125">List available snippets</span></span>               | <span data-ttu-id="a2479-126"><kbd>CTRL</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="a2479-127"><kbd>CTRL</kbd>+<kbd>ALT</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="a2479-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="a2479-128">È possibile [configurare i tasti di scelta rapida personalizzati](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) anche in VS Code.</span><span class="sxs-lookup"><span data-stu-id="a2479-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="a2479-129">Interfaccia utente di tipo ISE semplificata</span><span class="sxs-lookup"><span data-stu-id="a2479-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="a2479-130">Se si vuole semplificare l'interfaccia utente di Visual Studio Code e renderla più simile all'interfaccia utente ISE, applicare le due impostazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="a2479-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="a2479-131">Queste impostazioni nascondono le sezioni della barra attività e della barra laterale di debug visualizzate all'interno della casella rossa qui sotto:</span><span class="sxs-lookup"><span data-stu-id="a2479-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![la sezione evidenziata include la barra attività e la barra laterale di debug](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="a2479-133">Il risultato finale è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="a2479-133">The end result looks like this:</span></span>

  ![Visualizzazione semplificata di VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="a2479-135">Completamento tramite TAB</span><span class="sxs-lookup"><span data-stu-id="a2479-135">Tab completion</span></span>

  <span data-ttu-id="a2479-136">Per abilitare più completamento tramite TAB di tipo ISE, aggiungere questa impostazione:</span><span class="sxs-lookup"><span data-stu-id="a2479-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="a2479-137">Stato non attivo sulla console durante l'esecuzione</span><span class="sxs-lookup"><span data-stu-id="a2479-137">No focus on console when executing</span></span>

  <span data-ttu-id="a2479-138">Per mantenere lo stato attivo nell'editor, durante l'esecuzione con <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="a2479-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="a2479-139">Il valore predefinito è `true` a scopo di accessibilità.</span><span class="sxs-lookup"><span data-stu-id="a2479-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="a2479-140">Non avviare la console integrata all'avvio</span><span class="sxs-lookup"><span data-stu-id="a2479-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="a2479-141">Per arrestare la console integrata all'avvio, impostare:</span><span class="sxs-lookup"><span data-stu-id="a2479-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="a2479-142">Il processo in background di PowerShell inizia comunque a offrire IntelliSense, analisi di script, passaggio ai simboli e così via, ma la console non verrà visualizzata.</span><span class="sxs-lookup"><span data-stu-id="a2479-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="a2479-143">Si supponga che i file siano di PowerShell per impostazione predefinita</span><span class="sxs-lookup"><span data-stu-id="a2479-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="a2479-144">Per creare file nuovi/senza titolo, registrarli come PowerShell per impostazione predefinita:</span><span class="sxs-lookup"><span data-stu-id="a2479-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="a2479-145">Combinazione di colori</span><span class="sxs-lookup"><span data-stu-id="a2479-145">Color scheme</span></span>

  <span data-ttu-id="a2479-146">Sono disponibili numerosi temi ISE per VS Code per rendere l'aspetto dell'editor molto più simile a quello di ISE.</span><span class="sxs-lookup"><span data-stu-id="a2479-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="a2479-147">Nel [riquadro comandi][] digitare `theme` per ottenere `Preferences: Color Theme`, quindi premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a2479-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="a2479-148">Nell'elenco a discesa selezionare `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="a2479-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="a2479-149">È possibile impostare questo tema nelle impostazioni con:</span><span class="sxs-lookup"><span data-stu-id="a2479-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="a2479-150">PowerShell Command Explorer</span><span class="sxs-lookup"><span data-stu-id="a2479-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="a2479-151">Grazie al lavoro di [@corbob](https://github.com/corbob), l'estensione di PowerShell presenta uno strumento di esplorazione comandi in fase iniziale.</span><span class="sxs-lookup"><span data-stu-id="a2479-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="a2479-152">Nel [riquadro comandi][] immettere `PowerShell Command Explorer` e premere <kbd>INVIO</kbd>.</span><span class="sxs-lookup"><span data-stu-id="a2479-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="a2479-153">Aprire l'ISE</span><span class="sxs-lookup"><span data-stu-id="a2479-153">Open in the ISE</span></span>

  <span data-ttu-id="a2479-154">Se si vuole comunque aprire un file in Windows PowerShell ISE, aprire il [riquadro comandi][], cercare "open in ise" (Apri in ISE) e quindi selezionare **PowerShell: Open Current File in PowerShell ISE** (PowerShell: Apri file corrente in PowerShell ISE).</span><span class="sxs-lookup"><span data-stu-id="a2479-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="a2479-155">Altre risorse</span><span class="sxs-lookup"><span data-stu-id="a2479-155">Other resources</span></span>

- <span data-ttu-id="a2479-156">4sysops presenta [un interessante articolo][4sysops] sulla configurazione di VS Code per renderlo più simile all'ISE.</span><span class="sxs-lookup"><span data-stu-id="a2479-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="a2479-157">Mike F Robbins ha pubblicato [un interessante post][mikefrobbins] su come configurare VS Code.</span><span class="sxs-lookup"><span data-stu-id="a2479-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
- <span data-ttu-id="a2479-158">Nelle risorse di formazione di PowerShell è disponibile [un interessante documento][learnpwsh] sulla configurazione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2479-158">Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell.</span></span>

## <a name="vs-code-tips"></a><span data-ttu-id="a2479-159">Suggerimenti per VS Code</span><span class="sxs-lookup"><span data-stu-id="a2479-159">VS Code Tips</span></span>

- <span data-ttu-id="a2479-160">Riquadro comandi</span><span class="sxs-lookup"><span data-stu-id="a2479-160">Command Palette</span></span>

  <span data-ttu-id="a2479-161">Il riquadro comandi è un modo pratico per eseguire i comandi in VS Code.</span><span class="sxs-lookup"><span data-stu-id="a2479-161">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="a2479-162">Aprire il riquadro comandi usando <kbd>F1</kbd> O <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> O <kbd>CMD</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> in macOS.</span><span class="sxs-lookup"><span data-stu-id="a2479-162">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="a2479-163">Per altre informazioni, vedere la [documentazione di VS Code][vsc-docs].</span><span class="sxs-lookup"><span data-stu-id="a2479-163">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="a2479-164">Disabilitare la Console di debug</span><span class="sxs-lookup"><span data-stu-id="a2479-164">Disable the Debug Console</span></span>

  <span data-ttu-id="a2479-165">Se si prevede di usare VS Code per gli script di PowerShell, è possibile nascondere la **Console di debug** perché non viene usata dall'estensione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a2479-165">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="a2479-166">A tale scopo, fare clic con il pulsante destro del mouse su **Console di debug** e quindi fare clic sul segno di spunta per nasconderla.</span><span class="sxs-lookup"><span data-stu-id="a2479-166">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="a2479-167">Altre impostazioni</span><span class="sxs-lookup"><span data-stu-id="a2479-167">More settings</span></span>

<span data-ttu-id="a2479-168">Se si conoscono altri modi per rendere VS Code più semplice per gli utenti ISE, contribuire a questo documento. Se si sta ricercando una configurazione di compatibilità, ma non si riesce ad abilitarla, [Segnala un problema][] e porre eventuali domande.</span><span class="sxs-lookup"><span data-stu-id="a2479-168">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="a2479-169">Siamo sempre lieti di accettare PR e contributi.</span><span class="sxs-lookup"><span data-stu-id="a2479-169">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Riquadro comandi]: #vs-code-tips
[Command Palette]: #vs-code-tips
[Segnala un problema]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
