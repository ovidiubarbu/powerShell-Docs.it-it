---
ms.date: 12/05/2019
keywords: powershell,cmdlet
title: Avvio di Windows PowerShell
ms.openlocfilehash: 97b15a4cd79c77a391451ba917f985f9d99db3f5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "74953824"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="a3b4f-103">Avvio di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3b4f-103">Starting Windows PowerShell</span></span>

<span data-ttu-id="a3b4f-104">Windows PowerShell è una `.DLL` del motore di scripting incorporata in più host.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-104">Windows PowerShell is a scripting engine `.DLL` that's embedded into multiple hosts.</span></span> <span data-ttu-id="a3b4f-105">Gli host più comuni che verranno avviati sono la riga di comando interattiva **powershell.exe** e ISE (Interactive Scripting Environment) **powershell_ise.exe**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-105">The most common hosts you'll start are the interactive command-line **powershell.exe** and the Interactive Scripting Environment **powershell_ise.exe**.</span></span>

<span data-ttu-id="a3b4f-106">Per avviare Windows PowerShell® in Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, vedere [Attività di gestione comuni e navigazione in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span><span class="sxs-lookup"><span data-stu-id="a3b4f-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation in Windows](/previous-versions/windows/it-pro/windows-server-2012-R2-and-2012/hh831491(v=ws.11)).</span></span>

## <a name="powershell-core-has-renamed-binary"></a><span data-ttu-id="a3b4f-107">Il file binario di PowerShell Core è stato rinominato</span><span class="sxs-lookup"><span data-stu-id="a3b4f-107">PowerShell Core has renamed binary</span></span>

<span data-ttu-id="a3b4f-108">PowerShell Core, noto come PowerShell, è la versione 6 (e successive) open source e usa .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-108">PowerShell Core, referred to as PowerShell, is version 6 and higher that's open source and uses .NET Core.</span></span> <span data-ttu-id="a3b4f-109">Sono disponibili versioni supportate in Windows, macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-109">Supported versions are available on Windows, macOS, and Linux.</span></span>

<span data-ttu-id="a3b4f-110">A partire da PowerShell 6, il file binario di PowerShell è stato rinominato **pwsh.exe** per Windows e **pwsh** per macOS e Linux.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-110">Beginning in PowerShell 6, the PowerShell binary was renamed **pwsh.exe** for Windows and **pwsh** for macOS and Linux.</span></span> <span data-ttu-id="a3b4f-111">È possibile avviare le versioni di anteprima di PowerShell usando **pwsh-preview**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-111">You can start PowerShell preview versions using **pwsh-preview**.</span></span> <span data-ttu-id="a3b4f-112">Per altre informazioni, vedere [Novità di PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) e [Informazioni su pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span><span class="sxs-lookup"><span data-stu-id="a3b4f-112">For more information, see [What's New in PowerShell Core 6.0](/powershell/scripting/whats-new/what-s-new-in-powershell-core-60#renamed-powershellexe-to-pwshexe) and [About pwsh](/powershell/module/microsoft.powershell.core/about/about_pwsh?view=powershell-7).</span></span>

<span data-ttu-id="a3b4f-113">Per trovare la documentazione di riferimento sui cmdlet e per l'installazione di PowerShell 7, usare i collegamenti seguenti:</span><span class="sxs-lookup"><span data-stu-id="a3b4f-113">To find cmdlet reference and installation documentation for PowerShell 7, use the following links:</span></span>

| <span data-ttu-id="a3b4f-114">Document</span><span class="sxs-lookup"><span data-stu-id="a3b4f-114">Document</span></span> | <span data-ttu-id="a3b4f-115">Collegamento</span><span class="sxs-lookup"><span data-stu-id="a3b4f-115">Link</span></span> |
| ----- | ----- |
| <span data-ttu-id="a3b4f-116">Informazioni di riferimento sui cmdlet</span><span class="sxs-lookup"><span data-stu-id="a3b4f-116">Cmdlet reference</span></span> | [<span data-ttu-id="a3b4f-117">Visualizzatore dei moduli di PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3b4f-117">PowerShell Module Browser</span></span>](/powershell/module/?view=powershell-7) |
| <span data-ttu-id="a3b4f-118">Installazione in Windows</span><span class="sxs-lookup"><span data-stu-id="a3b4f-118">Windows installation</span></span> | [<span data-ttu-id="a3b4f-119">Installazione di PowerShell Core in Windows</span><span class="sxs-lookup"><span data-stu-id="a3b4f-119">Installing PowerShell Core on Windows</span></span>](/powershell/scripting/install/installing-powershell-core-on-windows?view=powershell-7) |
| <span data-ttu-id="a3b4f-120">Installazione in macOS</span><span class="sxs-lookup"><span data-stu-id="a3b4f-120">macOS installation</span></span> | [<span data-ttu-id="a3b4f-121">Installazione di PowerShell Core in macOS</span><span class="sxs-lookup"><span data-stu-id="a3b4f-121">Installing PowerShell Core on macOS</span></span>](/powershell/scripting/install/installing-powershell-core-on-macos?view=powershell-7) |
| <span data-ttu-id="a3b4f-122">Installazione in Linux</span><span class="sxs-lookup"><span data-stu-id="a3b4f-122">Linux installation</span></span> | [<span data-ttu-id="a3b4f-123">Installazione di PowerShell Core in Linux</span><span class="sxs-lookup"><span data-stu-id="a3b4f-123">Installing PowerShell Core on Linux</span></span>](/powershell/scripting/install/installing-powershell-core-on-linux?view=powershell-7) |

<span data-ttu-id="a3b4f-124">Per visualizzare il contenuto per altre versioni di PowerShell, vedere [Come usare la documentazione di PowerShell](../how-to-use-docs.md).</span><span class="sxs-lookup"><span data-stu-id="a3b4f-124">To view content for other PowerShell versions, see [How to use the PowerShell documentation](../how-to-use-docs.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="a3b4f-125">Come avviare Windows PowerShell in versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="a3b4f-125">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="a3b4f-126">Questa sezione illustra come avviare Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) in Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-126">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="a3b4f-127">Descrive anche come abilitare la funzionalità facoltativa per Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-127">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="a3b4f-128">Usare uno dei metodi seguenti per avviare la versione installata di Windows PowerShell 3.0 o Windows PowerShell 4.0, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-128">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="a3b4f-129">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="a3b4f-129">From the Start Menu</span></span>

- <span data-ttu-id="a3b4f-130">Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-130">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="a3b4f-131">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-131">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="a3b4f-132">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="a3b4f-132">At the Command Prompt</span></span>

<span data-ttu-id="a3b4f-133">Per avviare Windows PowerShell in **cmd.exe**, Windows PowerShell o Windows PowerShell ISE, digitare:</span><span class="sxs-lookup"><span data-stu-id="a3b4f-133">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="a3b4f-134">È anche possibile usare i parametri del programma **powershell.exe** per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-134">You can also use the parameters of the **powershell.exe** program to customize the session.</span></span> <span data-ttu-id="a3b4f-135">Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="a3b4f-135">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="a3b4f-136">Con privilegi amministrativi (Esegui come amministratore)</span><span class="sxs-lookup"><span data-stu-id="a3b4f-136">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="a3b4f-137">Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-137">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="a3b4f-138">Come avviare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="a3b4f-138">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="a3b4f-139">Per avviare Windows PowerShell ISE, usare uno dei seguenti metodi.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-139">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="a3b4f-140">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="a3b4f-140">From the Start Menu</span></span>

- <span data-ttu-id="a3b4f-141">Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-141">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="a3b4f-142">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-142">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="a3b4f-143">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="a3b4f-143">At the Command Prompt</span></span>

<span data-ttu-id="a3b4f-144">Per avviare Windows PowerShell in **cmd.exe**, Windows PowerShell o Windows PowerShell ISE, digitare:</span><span class="sxs-lookup"><span data-stu-id="a3b4f-144">In **cmd.exe**, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="a3b4f-145">o</span><span class="sxs-lookup"><span data-stu-id="a3b4f-145">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="a3b4f-146">Con privilegi amministrativi (Esegui come amministratore)</span><span class="sxs-lookup"><span data-stu-id="a3b4f-146">With Administrative privileges (Run as administrator)</span></span>

<span data-ttu-id="a3b4f-147">Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-147">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="a3b4f-148">Come abilitare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="a3b4f-148">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="a3b4f-149">In Windows PowerShell 4.0 e Windows PowerShell 3.0, Windows PowerShell ISE è abilitato per impostazione predefinita in tutte le versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-149">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="a3b4f-150">Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-150">If it isn't already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="a3b4f-151">In Windows PowerShell 2.0, Windows PowerShell ISE è abilitato per impostazione predefinita in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-151">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="a3b4f-152">In Windows Server 2008 R2 e Windows Server 2008, tuttavia, è una funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-152">However, on Windows Server 2008 R2 and Windows Server 2008, it's an optional feature.</span></span>

<span data-ttu-id="a3b4f-153">Per abilitare Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-153">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="a3b4f-154">Per abilitare Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="a3b4f-154">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="a3b4f-155">Avviare Server Manager.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-155">Start Server Manager.</span></span>
2. <span data-ttu-id="a3b4f-156">Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-156">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="a3b4f-157">In Selezionare le funzionalità fare clic su Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="a3b4f-157">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="a3b4f-158">Avvio della versione a 32 bit di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="a3b4f-158">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="a3b4f-159">Quando si installa Windows PowerShell in un computer a 64 bit, oltre alla versione a 64 bit viene installato **Windows PowerShell (x86)** , una versione a 32 bit di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-159">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="a3b4f-160">Quando si esegue Windows PowerShell, viene eseguita la versione a 64 bit per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-160">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="a3b4f-161">Tuttavia, in alcuni casi potrebbe essere necessario eseguire **Windows PowerShell (x86)** , ad esempio quando si usa un modulo che richiede la versione a 32 bit o quando ci si connette in remoto a un computer a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-161">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you're using a module that requires the 32-bit version or when you're connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="a3b4f-162">Per avviare una versione a 32 bit di Windows PowerShell, usare una delle procedure seguenti.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-162">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="a3b4f-163">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="a3b4f-163">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="a3b4f-164">Nella schermata **Start** digitare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-164">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a3b4f-165">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-165">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="a3b4f-166">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-166">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-167">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-167">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-168">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a3b4f-168">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="a3b4f-169">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="a3b4f-169">In Windows Server® 2012</span></span>

- <span data-ttu-id="a3b4f-170">Nella schermata **Start** digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-170">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-171">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-171">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-172">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-172">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-173">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a3b4f-173">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="a3b4f-174">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="a3b4f-174">In Windows® 8.1</span></span>

- <span data-ttu-id="a3b4f-175">Nella schermata **Start** digitare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-175">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="a3b4f-176">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-176">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="a3b4f-177">Se si esegue [Strumenti di amministrazione remota del server](https://go.microsoft.com/fwlink/?LinkID=304145) per Windows 8.1, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-177">If you're running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a3b4f-178">Selezionare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-178">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-179">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-179">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-180">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a3b4f-180">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="a3b4f-181">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="a3b4f-181">In Windows® 8</span></span>

- <span data-ttu-id="a3b4f-182">Nella schermata **Start** spostare il cursore nell'angolo in alto a destra, fare clic su **Impostazioni**, fare clic su **Riquadri** e quindi spostare il dispositivo di scorrimento **Mostra strumenti di amministrazione** su **Sì**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-182">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to **Yes**.</span></span> <span data-ttu-id="a3b4f-183">A questo punto digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-183">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-184">Se si esegue [Strumenti di amministrazione remota del server](https://www.microsoft.com/download/details.aspx?id=28972) per Windows 8, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="a3b4f-184">If you're running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="a3b4f-185">Selezionare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-185">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-186">Nella schermata **Start** o sul desktop digitare **PowerShell(x86)** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="a3b4f-186">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="a3b4f-187">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="a3b4f-187">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
