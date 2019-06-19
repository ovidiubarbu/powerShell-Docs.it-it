---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Avvio di Windows PowerShell
ms.openlocfilehash: d2cb77027f404c5b008a902c5147d018dd741a67
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030448"
---
# <a name="starting-windows-powershell"></a><span data-ttu-id="2183d-103">Avvio di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2183d-103">Starting Windows PowerShell</span></span>
<span data-ttu-id="2183d-104">PowerShell è una libreria di collegamento dinamico del motore di script incorporata in più host.</span><span class="sxs-lookup"><span data-stu-id="2183d-104">PowerShell is a scripting engine dll which is embedded into multiple hosts.</span></span>  <span data-ttu-id="2183d-105">Gli host più comuni che verranno avviati sono PowerShell.exe e Interactive Scripting Environment PowerShell_ISE.exe dalla riga di comando interattiva.</span><span class="sxs-lookup"><span data-stu-id="2183d-105">The most common host you will start are the interactive command line PowerShell.exe and the Interactive Scripting Environment PowerShell_ISE.exe.</span></span>

<span data-ttu-id="2183d-106">Per avviare Windows PowerShell® in Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012 e Windows 8, vedere [Attività di gestione comuni e navigazione](https://technet.microsoft.com/library/hh831491.aspx).</span><span class="sxs-lookup"><span data-stu-id="2183d-106">To start Windows PowerShell® on Windows Server® 2012 R2, Windows® 8.1, Windows Server 2012, and Windows 8, see [Common Management Tasks and Navigation](https://technet.microsoft.com/library/hh831491.aspx).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="2183d-107">Come avviare Windows PowerShell in versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="2183d-107">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>

<span data-ttu-id="2183d-108">Questa sezione illustra come avviare Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) in Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="2183d-108">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="2183d-109">Descrive anche come abilitare la funzionalità facoltativa per Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="2183d-109">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="2183d-110">Usare uno dei metodi seguenti per avviare la versione installata di Windows PowerShell 3.0 o Windows PowerShell 4.0, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="2183d-110">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="2183d-111">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="2183d-111">From the Start Menu</span></span>

- <span data-ttu-id="2183d-112">Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2183d-112">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>
- <span data-ttu-id="2183d-113">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="2183d-113">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="2183d-114">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="2183d-114">At the Command Prompt</span></span>

<span data-ttu-id="2183d-115">Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:</span><span class="sxs-lookup"><span data-stu-id="2183d-115">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell
```

<span data-ttu-id="2183d-116">È anche possibile usare i parametri del programma PowerShell.exe per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="2183d-116">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="2183d-117">Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="2183d-117">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="2183d-118">Con privilegi amministrativi ("Esegui come amministratore")</span><span class="sxs-lookup"><span data-stu-id="2183d-118">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="2183d-119">Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="2183d-119">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="2183d-120">Come avviare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="2183d-120">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="2183d-121">Per avviare Windows PowerShell ISE, usare uno dei seguenti metodi.</span><span class="sxs-lookup"><span data-stu-id="2183d-121">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="2183d-122">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="2183d-122">From the Start Menu</span></span>

- <span data-ttu-id="2183d-123">Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="2183d-123">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>
- <span data-ttu-id="2183d-124">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="2183d-124">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="2183d-125">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="2183d-125">At the Command Prompt</span></span>

<span data-ttu-id="2183d-126">Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:</span><span class="sxs-lookup"><span data-stu-id="2183d-126">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

```
PowerShell_ISE
```

<span data-ttu-id="2183d-127">o</span><span class="sxs-lookup"><span data-stu-id="2183d-127">or</span></span>

```
ISE
```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="2183d-128">Con privilegi amministrativi ("Esegui come amministratore")</span><span class="sxs-lookup"><span data-stu-id="2183d-128">With Administrative privileges ("Run as administrator")</span></span>

<span data-ttu-id="2183d-129">Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="2183d-129">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="2183d-130">Come abilitare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="2183d-130">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>

<span data-ttu-id="2183d-131">In Windows PowerShell 4.0 e Windows PowerShell 3.0, Windows PowerShell ISE è abilitato per impostazione predefinita in tutte le versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="2183d-131">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="2183d-132">Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="2183d-132">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="2183d-133">In Windows PowerShell 2.0, Windows PowerShell ISE è abilitato per impostazione predefinita in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="2183d-133">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="2183d-134">In Windows Server 2008 R2 e Windows Server 2008, tuttavia, è una funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="2183d-134">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="2183d-135">Per abilitare Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="2183d-135">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="2183d-136">Per abilitare Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="2183d-136">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1. <span data-ttu-id="2183d-137">Avviare Server Manager.</span><span class="sxs-lookup"><span data-stu-id="2183d-137">Start Server Manager.</span></span>
2. <span data-ttu-id="2183d-138">Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="2183d-138">Click **Features** and then click **Add Features**.</span></span>
3. <span data-ttu-id="2183d-139">In Selezionare le funzionalità fare clic su Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="2183d-139">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>

## <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="2183d-140">Avvio della versione a 32 bit di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2183d-140">Starting the 32-Bit Version of Windows PowerShell</span></span>

<span data-ttu-id="2183d-141">Quando si installa Windows PowerShell in un computer a 64 bit, oltre alla versione a 64 bit viene installato **Windows PowerShell (x86)** , una versione a 32 bit di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="2183d-141">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="2183d-142">Quando si esegue Windows PowerShell, viene eseguita la versione a 64 bit per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="2183d-142">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="2183d-143">Tuttavia, in alcuni casi potrebbe essere necessario eseguire **Windows PowerShell (x86)** , ad esempio quando si usa un modulo che richiede la versione a 32 bit o quando ci si connette in remoto a un computer a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="2183d-143">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="2183d-144">Per avviare una versione a 32 bit di Windows PowerShell, usare una delle procedure seguenti.</span><span class="sxs-lookup"><span data-stu-id="2183d-144">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="2183d-145">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="2183d-145">In Windows Server® 2012 R2</span></span>

- <span data-ttu-id="2183d-146">Nella schermata **Start** digitare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-146">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="2183d-147">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="2183d-147">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="2183d-148">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="2183d-148">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-149">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-149">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-150">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2183d-150">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="2183d-151">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="2183d-151">In Windows Server® 2012</span></span>

- <span data-ttu-id="2183d-152">Nella schermata **Start** digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-152">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-153">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="2183d-153">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-154">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-154">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-155">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2183d-155">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="2183d-156">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="2183d-156">In Windows® 8.1</span></span>

- <span data-ttu-id="2183d-157">Nella schermata **Start** digitare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-157">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="2183d-158">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="2183d-158">Click the **Windows PowerShell x86** tile.</span></span>
- <span data-ttu-id="2183d-159">Se si esegue [Strumenti di amministrazione remota del server](https://go.microsoft.com/fwlink/?LinkID=304145) per Windows 8.1, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="2183d-159">If you are running [Remote Server Administration Tools](https://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span>
  <span data-ttu-id="2183d-160">Selezionare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-160">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-161">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-161">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-162">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2183d-162">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="2183d-163">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="2183d-163">In Windows® 8</span></span>

- <span data-ttu-id="2183d-164">Nella schermata **Start** spostare il cursore nell'angolo in alto a destra, fare clic su **Impostazioni**, fare clic su **Riquadri** e quindi spostare il dispositivo di scorrimento **Mostra strumenti di amministrazione** su Sì.</span><span class="sxs-lookup"><span data-stu-id="2183d-164">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="2183d-165">A questo punto digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-165">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-166">Se si esegue [Strumenti di amministrazione remota del server](https://www.microsoft.com/download/details.aspx?id=28972) per Windows 8, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="2183d-166">If you are running [Remote Server Administration Tools](https://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="2183d-167">Selezionare **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-167">Select **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-168">Nella schermata **Start** o sul desktop digitare **PowerShell(x86)** e quindi fare clic su **Windows PowerShell (x86)** .</span><span class="sxs-lookup"><span data-stu-id="2183d-168">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>
- <span data-ttu-id="2183d-169">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="2183d-169">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>
