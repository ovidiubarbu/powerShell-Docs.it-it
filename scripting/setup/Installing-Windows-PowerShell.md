---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Installazione di Windows PowerShell
ms.assetid: 6fbb0409-5a54-48ec-95e6-7f8b7d8c4969
ms.openlocfilehash: 2b4cdec52dfc98649a81ab2265a204fcdb0bd8d7
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="installing-windows-powershell"></a><span data-ttu-id="c6451-103">Installazione di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6451-103">Installing Windows PowerShell</span></span>
<span data-ttu-id="c6451-104">Windows® 8 e Windows Server® 2012 includono Windows PowerShell 3.0 e tutti i relativi prerequisiti.</span><span class="sxs-lookup"><span data-stu-id="c6451-104">Windows® 8 and Windows Server® 2012 include Windows PowerShell 3.0 and all of its prerequisites.</span></span> <span data-ttu-id="c6451-105">Il sistema include anche il motore di Windows PowerShell 2.0 per la compatibilità con le versioni precedenti dei programmi host che non possono usare Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6451-105">The system also includes the Windows PowerShell 2.0 engine for backward compatibility with host programs that cannot use Windows PowerShell 3.0.</span></span>

<span data-ttu-id="c6451-106">Questo argomento descrive come installare Windows PowerShell 3.0 nei sistemi precedenti, nonché come installare e abilitare le funzionalità necessarie.</span><span class="sxs-lookup"><span data-stu-id="c6451-106">This topic explains how to install Windows PowerShell 3.0 on earlier systems and install and enable the required features.</span></span>

<span data-ttu-id="c6451-107">Questo argomento include le sezioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="c6451-107">This topic includes the following sections:</span></span>

-   [<span data-ttu-id="c6451-108">Installazione di Windows PowerShell in Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c6451-108">Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows8andWindowsServer2012)

-   [<span data-ttu-id="c6451-109">Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c6451-109">Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindows7andWindowsServer2008R2)

-   [<span data-ttu-id="c6451-110">Installazione di Windows PowerShell in Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="c6451-110">Installing Windows PowerShell on Windows Server 2008</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnWindowsServer2008LH)

-   [<span data-ttu-id="c6451-111">Installazione di Windows PowerShell in Server Core</span><span class="sxs-lookup"><span data-stu-id="c6451-111">Installing Windows PowerShell on Server Core</span></span>](Installing-Windows-PowerShell.md#BKMK_InstallingOnServerCore)

-   [<span data-ttu-id="c6451-112">Distribuzione di Accesso Web Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6451-112">Deploying Windows PowerShell Web Access</span></span>](https://technet.microsoft.com/en-us/library/639d0eff-98a3-4124-b52c-26921ebd98b0)

-   [<span data-ttu-id="c6451-113">Installazione del motore di Windows PowerShell 2.0</span><span class="sxs-lookup"><span data-stu-id="c6451-113">Installing the Windows PowerShell 2.0 Engine</span></span>](Installing-the-Windows-PowerShell-2.0-Engine.md)

## <span data-ttu-id="c6451-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installazione di Windows PowerShell in Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="c6451-114"><a name="BKMK_InstallingOnWindows8andWindowsServer2012"></a>Installing Windows PowerShell on Windows 8 and Windows Server 2012</span></span>
<span data-ttu-id="c6451-115">Windows PowerShell 3.0 viene fornito già installato, configurato e pronto per l'uso.</span><span class="sxs-lookup"><span data-stu-id="c6451-115">Windows PowerShell 3.0 arrives installed, configured, and ready to use.</span></span> <span data-ttu-id="c6451-116">Windows PowerShell Integrated Scripting Environment (ISE) viene installato e abilitato.</span><span class="sxs-lookup"><span data-stu-id="c6451-116">Windows PowerShell Integrated Scripting Environment (ISE) is installed and enabled.</span></span> <span data-ttu-id="c6451-117">Per informazioni sull'avvio di Windows PowerShell, vedere [Avvio di Windows PowerShell in Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) e [Avvio di Windows PowerShell in Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span><span class="sxs-lookup"><span data-stu-id="c6451-117">For information about starting Windows PowerShell, see [Starting Windows PowerShell on Windows 8](https://technet.microsoft.com/en-us/library/d7be1668-8617-4890-ad90-dd9765fbd2c3) and [Starting Windows PowerShell on Windows Server 2012](https://technet.microsoft.com/library/hh831491.aspx#BKMK_powershell).</span></span>

## <span data-ttu-id="c6451-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installazione di Windows PowerShell in Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="c6451-118"><a name="BKMK_InstallingOnWindows7andWindowsServer2008R2"></a>Installing Windows PowerShell on Windows 7 and Windows Server 2008 R2</span></span>
<span data-ttu-id="c6451-119">Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono Windows 7 con Service Pack 1 e Windows Server 2008 R2 con Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="c6451-119">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows 7 with Service Pack 1 and Windows Server 2008 R2 with Service Pack 1.</span></span> <span data-ttu-id="c6451-120">Di seguito sono disponibili istruzioni di installazione separate per i computer con l'opzione di installazione Server Core di Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="c6451-120">There are separate installation instructions below for computers running with the Server Core installation option of Windows Server 2008 R2.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="c6451-121">Preparativi per l'installazione</span><span class="sxs-lookup"><span data-stu-id="c6451-121">Getting ready to install</span></span>

-   <span data-ttu-id="c6451-122">Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c6451-122">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="c6451-123">Per installare Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c6451-123">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="c6451-124">Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span><span class="sxs-lookup"><span data-stu-id="c6451-124">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="c6451-125">Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span><span class="sxs-lookup"><span data-stu-id="c6451-125">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

2.  <span data-ttu-id="c6451-126">Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="c6451-126">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

<span data-ttu-id="c6451-127">Per informazioni sull'avvio di Windows PowerShell 3.0, vedere [Avvio di Windows PowerShell in versioni precedenti di Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span><span class="sxs-lookup"><span data-stu-id="c6451-127">For information about starting Windows PowerShell 3.0, see [Starting Windows PowerShell on Earlier Versions of Windows](Starting-Windows-PowerShell-on-Earlier-Versions-of-Windows.md).</span></span>

## <span data-ttu-id="c6451-128"><a name="BKMK_InstallingOnServerCore"></a>Installazione di Windows PowerShell in Server Core</span><span class="sxs-lookup"><span data-stu-id="c6451-128"><a name="BKMK_InstallingOnServerCore"></a>Installing Windows PowerShell on Server Core</span></span>
<span data-ttu-id="c6451-129">Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono l'opzione di installazione Server Core di Windows Server 2008 R2 con Service Pack 1.</span><span class="sxs-lookup"><span data-stu-id="c6451-129">These instructions explain how to install Windows PowerShell 3.0 on computers running the Server Core installation option of Windows Server 2008 R2 with Service Pack 1.</span></span>

<span data-ttu-id="c6451-130">I primi passaggi della procedura usano i comandi Gestione e manutenzione immagini distribuzione per installare Microsoft NET Framework 2.0 per Server Core e Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c6451-130">The first steps in the procedure use Deployment Image Servicing and Management (DISM) commands to install Microsoft .NET Framework 2.0 for Server Core and Windows PowerShell 2.0.</span></span> <span data-ttu-id="c6451-131">Questi programmi sono prerequisiti di Windows Management Framework 3.0, che viene installato in un passaggio successivo.</span><span class="sxs-lookup"><span data-stu-id="c6451-131">These programs are prerequisites for Windows Management Framework 3.0, which is installed in a subsequent step.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="c6451-132">Preparativi per l'installazione</span><span class="sxs-lookup"><span data-stu-id="c6451-132">Getting ready to install</span></span>

-   <span data-ttu-id="c6451-133">Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c6451-133">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="c6451-134">Per installare Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c6451-134">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="c6451-135">Avviare Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="c6451-135">Start Cmd.exe</span></span>

2.  <span data-ttu-id="c6451-136">Eseguire i seguenti comandi Gestione e manutenzione immagini distribuzione.</span><span class="sxs-lookup"><span data-stu-id="c6451-136">Run the following DISM commands.</span></span> <span data-ttu-id="c6451-137">Questi comandi installano .NET Framework 2.0 e Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="c6451-137">These commands install .NET Framework 2.0 and Windows PowerShell 2.0.</span></span>

    ```
    dism /online /enable-feature:NetFx2-ServerCore
    dism /online /enable-feature:MicrosoftWindowsPowerShell
    dism /online /enable-feature:NetFx2-ServerCore-WOW64
    ```

3.  <span data-ttu-id="c6451-138">Eseguire l'installazione completa di Microsoft .NET Framework 4.0 per Server Core dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span><span class="sxs-lookup"><span data-stu-id="c6451-138">Install Microsoft .NET Framework 4.0 full installation for Server Core from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=248450](http://go.microsoft.com/fwlink/?LinkID=248450).</span></span>

4.  <span data-ttu-id="c6451-139">Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="c6451-139">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <span data-ttu-id="c6451-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installazione di Windows PowerShell in Windows Server 2008</span><span class="sxs-lookup"><span data-stu-id="c6451-140"><a name="BKMK_InstallingOnWindowsServer2008LH"></a>Installing Windows PowerShell on Windows Server 2008</span></span>
<span data-ttu-id="c6451-141">Queste istruzioni spiegano come installare Windows PowerShell 3.0 nei computer che eseguono Windows Server 2008 con Service Pack 2.</span><span class="sxs-lookup"><span data-stu-id="c6451-141">These instructions explain how to install Windows PowerShell 3.0 on computers running Windows Server 2008 with Service Pack 2.</span></span>

<span data-ttu-id="c6451-142">Nei sistemi Windows Server 2008, Windows Management Framework (Windows PowerShell 2.0, KB 968930) è un prerequisito per Windows Management Framework 3.0.</span><span class="sxs-lookup"><span data-stu-id="c6451-142">On Windows Server 2008 systems, Windows Management Framework (Windows PowerShell 2.0, KB 968930) is a prerequisite for Windows Management Framework 3.0.</span></span> <span data-ttu-id="c6451-143">La funzionalità di "protezione estesa per l'autenticazione" protegge il computer da attacchi di inoltro dell'autenticazione e consente di usare il parametro **UseSSL** durante la creazione delle sessioni remote.</span><span class="sxs-lookup"><span data-stu-id="c6451-143">The "Extended Protection for Authentication" feature protects the computer from authentication forwarding attacks and allows you to use the **UseSSL** parameter when creating remote sessions.</span></span> <span data-ttu-id="c6451-144">Per installare Windows PowerShell 3.0 e il motore di Windows PowerShell 2.0, usare la procedura seguente.</span><span class="sxs-lookup"><span data-stu-id="c6451-144">To install Windows PowerShell 3.0 and the Windows PowerShell 2.0 Engine, use the following procedure.</span></span>

#### <a name="getting-ready-to-install"></a><span data-ttu-id="c6451-145">Preparativi per l'installazione</span><span class="sxs-lookup"><span data-stu-id="c6451-145">Getting ready to install</span></span>

-   <span data-ttu-id="c6451-146">Prima di installare Windows Management Framework 3.0, disinstallare eventuali versioni precedenti.</span><span class="sxs-lookup"><span data-stu-id="c6451-146">Before installing Windows Management Framework 3.0, uninstall any previous versions of Windows Management Framework 3.0.</span></span>

#### <a name="to-install-windows-powershell-30"></a><span data-ttu-id="c6451-147">Per installare Windows PowerShell 3.0</span><span class="sxs-lookup"><span data-stu-id="c6451-147">To install Windows PowerShell 3.0</span></span>

1.  <span data-ttu-id="c6451-148">Installare Microsoft .NET Framework 3.5 con Service Pack 1 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span><span class="sxs-lookup"><span data-stu-id="c6451-148">Install Microsoft .NET Framework 3.5 with Service Pack 1 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242910](http://go.microsoft.com/fwlink/?LinkID=242910).</span></span>

2.  <span data-ttu-id="c6451-149">Installare Windows Management Framework (Windows PowerShell 2.0, KB 968930) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span><span class="sxs-lookup"><span data-stu-id="c6451-149">Install Windows Management Framework (Windows PowerShell 2.0, KB 968930) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkId=243035](http://go.microsoft.com/fwlink/?LinkId=243035).</span></span>

3.  <span data-ttu-id="c6451-150">Installare la versione completa di Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span><span class="sxs-lookup"><span data-stu-id="c6451-150">Install the full installation of Microsoft .NET Framework 4 (dotNetFx40_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=212547](http://go.microsoft.com/fwlink/?LinkID=212547).</span></span>

    <span data-ttu-id="c6451-151">Oppure installare Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span><span class="sxs-lookup"><span data-stu-id="c6451-151">Or, install Microsoft .NET Framework 4.5 (dotNetFx45_Full_setup.exe) from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=242919](http://go.microsoft.com/fwlink/?LinkID=242919).</span></span>

4.  <span data-ttu-id="c6451-152">Installare la "protezione estesa per l'autenticazione" (KB 968389) da [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span><span class="sxs-lookup"><span data-stu-id="c6451-152">Install "Extended Protection for Authentication" (KB 968389) from [http://go.microsoft.com/fwlink/?LinkID=186398](http://go.microsoft.com/fwlink/?LinkID=186398).</span></span>

5.  <span data-ttu-id="c6451-153">Installare Windows Management Framework 3.0 dall'Area download Microsoft all'indirizzo [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span><span class="sxs-lookup"><span data-stu-id="c6451-153">Install Windows Management Framework 3.0 from the Microsoft Download Center at [http://go.microsoft.com/fwlink/?LinkID=240290](http://go.microsoft.com/fwlink/?LinkID=240290).</span></span>

## <a name="see-also"></a><span data-ttu-id="c6451-154">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c6451-154">See Also</span></span>
- [<span data-ttu-id="c6451-155">Requisiti di sistema di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6451-155">Windows PowerShell System Requirements</span></span>](Windows-PowerShell-System-Requirements.md)
- [<span data-ttu-id="c6451-156">Avvio di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c6451-156">Starting Windows PowerShell</span></span>](https://technet.microsoft.com/en-us/library/8ec8c2d7-8e7c-4722-a3d2-498fe5739a8e)

