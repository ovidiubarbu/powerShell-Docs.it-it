---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Avvio di Windows PowerShell in versioni precedenti di Windows
ms.assetid: 57125436-3d1e-4e7f-b5c4-8f0ecb49d642
ms.openlocfilehash: cb56fded1e67a4f4219d210dd95078314e855b1a
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="starting-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="18cc7-103">Avvio di Windows PowerShell in versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="18cc7-103">Starting Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="18cc7-104">Questa sezione illustra come avviare Windows PowerShell e Windows PowerShell Integrated Scripting Environment (ISE) in Windows® 7, Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="18cc7-104">This section explains how to start Windows PowerShell and Windows PowerShell Integrated Scripting Environment (ISE) on Windows® 7, Windows Server® 2008 R2, and Windows Server® 2008.</span></span> <span data-ttu-id="18cc7-105">Descrive anche come abilitare la funzionalità facoltativa per Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server® 2008.</span><span class="sxs-lookup"><span data-stu-id="18cc7-105">It also explains how to enable the optional feature for Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server® 2008 R2 and Windows Server® 2008.</span></span>

<span data-ttu-id="18cc7-106">Per installare Windows PowerShell 4.0 nei sistemi supportati, scaricare e installare [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span><span class="sxs-lookup"><span data-stu-id="18cc7-106">To install Windows PowerShell 4.0 on supported systems, download and install [Windows Management Framework 4.0](http://go.microsoft.com/fwlink/?LinkID=293881).</span></span> <span data-ttu-id="18cc7-107">Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="18cc7-107">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

<span data-ttu-id="18cc7-108">Per installare Windows PowerShell 3.0 nei sistemi supportati, scaricare e installare [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="18cc7-108">To install Windows PowerShell 3.0 on supported systems, download and install [Windows Management Framework 3.0](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span> <span data-ttu-id="18cc7-109">Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="18cc7-109">For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).</span></span>

## <a name="how-to-start-windows-powershell-on-earlier-versions-of-windows"></a><span data-ttu-id="18cc7-110">Come avviare Windows PowerShell in versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="18cc7-110">How to Start Windows PowerShell on Earlier Versions of Windows</span></span>
<span data-ttu-id="18cc7-111">Usare uno dei metodi seguenti per avviare la versione installata di Windows PowerShell 3.0 o Windows PowerShell 4.0, se applicabile.</span><span class="sxs-lookup"><span data-stu-id="18cc7-111">Use any of the following methods to start the installed version of Windows PowerShell 3.0, or Windows PowerShell 4.0, where applicable.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="18cc7-112">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="18cc7-112">From the Start Menu</span></span>

-   <span data-ttu-id="18cc7-113">Fare clic su **Start**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-113">Click **Start**, type **PowerShell**, and then click **Windows PowerShell**.</span></span>

-   <span data-ttu-id="18cc7-114">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-114">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="18cc7-115">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="18cc7-115">At the Command Prompt</span></span>

-   <span data-ttu-id="18cc7-116">Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:</span><span class="sxs-lookup"><span data-stu-id="18cc7-116">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell
    ```

    <span data-ttu-id="18cc7-117">È anche possibile usare i parametri del programma PowerShell.exe per personalizzare la sessione.</span><span class="sxs-lookup"><span data-stu-id="18cc7-117">You can also use the parameters of the PowerShell.exe program to customize the session.</span></span> <span data-ttu-id="18cc7-118">Per altre informazioni, vedere [Guida della riga di comando PowerShell.exe](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span><span class="sxs-lookup"><span data-stu-id="18cc7-118">For more information, see [PowerShell.exe Command-Line Help](../core-powershell/console/PowerShell.exe-Command-Line-Help.md).</span></span>

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="18cc7-119">Con privilegi amministrativi ("Esegui come amministratore")</span><span class="sxs-lookup"><span data-stu-id="18cc7-119">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="18cc7-120">Fare clic su **Start**, digitare **PowerShell**, fare clic con il pulsante destro del mouse su **Windows PowerShell** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-120">Click **Start**, type **PowerShell**, right-click **Windows PowerShell**, and then click **Run as administrator**.</span></span>

## <a name="how-to-start-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="18cc7-121">Come avviare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="18cc7-121">How to Start Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="18cc7-122">Per avviare Windows PowerShell ISE, usare uno dei seguenti metodi.</span><span class="sxs-lookup"><span data-stu-id="18cc7-122">Use any of the following methods to start Windows PowerShell ISE.</span></span>

#### <a name="from-the-start-menu"></a><span data-ttu-id="18cc7-123">Dal menu Start</span><span class="sxs-lookup"><span data-stu-id="18cc7-123">From the Start Menu</span></span>

-   <span data-ttu-id="18cc7-124">Fare clic su **Start**, digitare **ISE** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-124">Click **Start**, type **ISE**, and then click **Windows PowerShell ISE**.</span></span>

-   <span data-ttu-id="18cc7-125">Dal menu **Start** fare clic su **Start**, **Tutti i programmi**, **Accessori**, fare clic sulla cartella **Windows PowerShell** e quindi fare clic su **Windows PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-125">From the **Start** menu, click **Start**, click **All Programs**, click **Accessories**, click the **Windows PowerShell** folder, and then click **Windows PowerShell ISE**.</span></span>

#### <a name="at-the-command-prompt"></a><span data-ttu-id="18cc7-126">Al prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="18cc7-126">At the Command Prompt</span></span>

-   <span data-ttu-id="18cc7-127">Per avviare Windows PowerShell in Cmd.exe, Windows PowerShell o Windows PowerShell ISE digitare:</span><span class="sxs-lookup"><span data-stu-id="18cc7-127">In Cmd.exe, Windows PowerShell, or Windows PowerShell ISE, to start Windows PowerShell, type:</span></span>

    ```
    PowerShell_ISE
    ```

    <span data-ttu-id="18cc7-128">o</span><span class="sxs-lookup"><span data-stu-id="18cc7-128">or</span></span>

    ```
    ISE
    ```

#### <a name="with-administrative-privileges-run-as-administrator"></a><span data-ttu-id="18cc7-129">Con privilegi amministrativi ("Esegui come amministratore")</span><span class="sxs-lookup"><span data-stu-id="18cc7-129">With Administrative privileges ("Run as administrator")</span></span>

1.  <span data-ttu-id="18cc7-130">Fare clic su **Start**, digitare **ISE**, fare clic con il pulsante destro del mouse su **Windows PowerShell ISE** e quindi fare clic su **Esegui come amministratore**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-130">Click **Start**, type **ISE**, right-click **Windows PowerShell ISE**, and then click **Run as administrator**.</span></span>

## <a name="how-to-enable-windows-powershell-ise-on-earlier-releases-of-windows"></a><span data-ttu-id="18cc7-131">Come abilitare Windows PowerShell ISE nelle versioni precedenti di Windows</span><span class="sxs-lookup"><span data-stu-id="18cc7-131">How to Enable Windows PowerShell ISE on Earlier Releases of Windows</span></span>
<span data-ttu-id="18cc7-132">In Windows PowerShell 4.0 e Windows PowerShell 3.0, Windows PowerShell ISE è abilitato per impostazione predefinita in tutte le versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="18cc7-132">In Windows PowerShell 4.0 and Windows PowerShell 3.0, Windows PowerShell ISE is enabled by default on all versions of Windows.</span></span> <span data-ttu-id="18cc7-133">Se non è già abilitato, viene abilitato da Windows Management Framework 4.0 o Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="18cc7-133">If it is not already enabled, Windows Management Framework 4.0 or Windows Management Framework 3.0 enables it.</span></span>

<span data-ttu-id="18cc7-134">In Windows PowerShell 2.0, Windows PowerShell ISE è abilitato per impostazione predefinita in Windows 7.</span><span class="sxs-lookup"><span data-stu-id="18cc7-134">In Windows PowerShell 2.0, Windows PowerShell ISE is enabled by default on Windows 7.</span></span> <span data-ttu-id="18cc7-135">In Windows Server 2008 R2 e Windows Server 2008, tuttavia, è una funzionalità facoltativa.</span><span class="sxs-lookup"><span data-stu-id="18cc7-135">However, on Windows Server 2008 R2 and Windows Server 2008, it is an optional feature.</span></span>

<span data-ttu-id="18cc7-136">Per abilitare Windows PowerShell ISE in Windows PowerShell 2.0 per Windows Server® 2008 R2 e Windows Server 2008, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="18cc7-136">To enable Windows PowerShell ISE in Windows PowerShell 2.0 on Windows Server 2008 R2 or Windows Server 2008, use the following procedure.</span></span>

#### <a name="to-enable-windows-powershell-integrated-scripting-environment-ise"></a><span data-ttu-id="18cc7-137">Per abilitare Windows PowerShell Integrated Scripting Environment (ISE)</span><span class="sxs-lookup"><span data-stu-id="18cc7-137">To enable Windows PowerShell Integrated Scripting Environment (ISE)</span></span>

1.  <span data-ttu-id="18cc7-138">Avviare Server Manager.</span><span class="sxs-lookup"><span data-stu-id="18cc7-138">Start Server Manager.</span></span>

2.  <span data-ttu-id="18cc7-139">Fare clic su **Funzionalità** e quindi su **Aggiungi funzionalità**.</span><span class="sxs-lookup"><span data-stu-id="18cc7-139">Click **Features** and then click **Add Features**.</span></span>

3.  <span data-ttu-id="18cc7-140">In Selezionare le funzionalità fare clic su Windows PowerShell Integrated Scripting Environment (ISE).</span><span class="sxs-lookup"><span data-stu-id="18cc7-140">In Select Features, click Windows PowerShell Integrated Scripting Environment (ISE).</span></span>
