---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Avvio della versione a 32 bit di Windows PowerShell
ms.assetid: 12b31890-2609-4a76-8c24-0ebe78084f50
ms.openlocfilehash: 927b4028fcab68cb26d92bf292df2f0270837457
ms.sourcegitcommit: 598b7835046577841aea2211d613bb8513271a8b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/08/2017
---
# <a name="starting-the-32-bit-version-of-windows-powershell"></a><span data-ttu-id="4cd9e-103">Avvio della versione a 32 bit di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4cd9e-103">Starting the 32-Bit Version of Windows PowerShell</span></span>
<span data-ttu-id="4cd9e-104">Quando si installa Windows PowerShell in un computer a 64 bit, oltre alla versione a 64 bit viene installato **Windows PowerShell (x86)**, una versione a 32 bit di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-104">When you install Windows PowerShell on a 64-bit computer, **Windows PowerShell (x86)**, a 32-bit version of Windows PowerShell is installed in addition to the 64-bit version.</span></span> <span data-ttu-id="4cd9e-105">Quando si esegue Windows PowerShell, viene eseguita la versione a 64 bit per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-105">When you run Windows PowerShell, the 64-bit version runs by default.</span></span>

<span data-ttu-id="4cd9e-106">Tuttavia, in alcuni casi potrebbe essere necessario eseguire **Windows PowerShell (x86)**, ad esempio quando si usa un modulo che richiede la versione a 32 bit o quando ci si connette in remoto a un computer a 32 bit.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-106">However, you might occasionally need to run **Windows PowerShell (x86)**, such as when you are using a module that requires the 32-bit version or when you are connecting remotely to a 32-bit computer.</span></span>

<span data-ttu-id="4cd9e-107">Per avviare una versione a 32 bit di Windows PowerShell, usare una delle procedure seguenti.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-107">To start a 32-bit version of Windows PowerShell, use any of the following procedures.</span></span>

#### <a name="in-windows-server-2012-r2"></a><span data-ttu-id="4cd9e-108">In Windows Server® 2012 R2</span><span class="sxs-lookup"><span data-stu-id="4cd9e-108">In Windows Server® 2012 R2</span></span>

-   <span data-ttu-id="4cd9e-109">Nella schermata **Start** digitare **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-109">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="4cd9e-110">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-110">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="4cd9e-111">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-111">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-112">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-112">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-113">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4cd9e-113">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-server-2012"></a><span data-ttu-id="4cd9e-114">In Windows Server® 2012</span><span class="sxs-lookup"><span data-stu-id="4cd9e-114">In Windows Server® 2012</span></span>

-   <span data-ttu-id="4cd9e-115">Nella schermata **Start** digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-115">On the **Start** screen, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-116">In **Server Manager** scegliere **Windows PowerShell (x86)** dal menu **Strumenti**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-116">In **Server Manager**, from the **Tools** menu, select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-117">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-117">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-118">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4cd9e-118">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-81"></a><span data-ttu-id="4cd9e-119">In Windows® 8.1</span><span class="sxs-lookup"><span data-stu-id="4cd9e-119">In Windows® 8.1</span></span>

-   <span data-ttu-id="4cd9e-120">Nella schermata **Start** digitare **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-120">On the **Start** screen, type **Windows PowerShell (x86)**.</span></span> <span data-ttu-id="4cd9e-121">Fare clic sul riquadro **Windows PowerShell x86**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-121">Click the **Windows PowerShell x86** tile.</span></span>

-   <span data-ttu-id="4cd9e-122">Se si esegue [Strumenti di amministrazione remota del server](http://go.microsoft.com/fwlink/?LinkID=304145) per Windows 8.1, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-122">If you are running [Remote Server Administration Tools](http://go.microsoft.com/fwlink/?LinkID=304145) for Windows 8.1, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="4cd9e-123">Selezionare **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-123">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-124">Sul desktop, spostare il cursore nell'angolo in alto a destra, fare clic su **Cerca**, digitare **PowerShell x86** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-124">On the desktop, move the cursor to the upper right corner, click **Search**, type **PowerShell x86** and then click **Windows PowerShell (x86)**.</span></span>
   
-   <span data-ttu-id="4cd9e-125">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4cd9e-125">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

#### <a name="in-windows-8"></a><span data-ttu-id="4cd9e-126">In Windows® 8</span><span class="sxs-lookup"><span data-stu-id="4cd9e-126">In Windows® 8</span></span>

-   <span data-ttu-id="4cd9e-127">Nella schermata **Start** spostare il cursore nell'angolo in alto a destra, fare clic su **Impostazioni**, fare clic su **Riquadri** e quindi spostare il dispositivo di scorrimento **Mostra strumenti di amministrazione** su Sì.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-127">On the **Start** screen, move the cursor to the upper right corner, click **Settings**, click **Tiles**, and then move the **Show Administrative Tools** slider to Yes.</span></span> <span data-ttu-id="4cd9e-128">A questo punto digitare **PowerShell** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-128">Then, type **PowerShell** and click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-129">Se si esegue [Strumenti di amministrazione remota del server](http://www.microsoft.com/download/details.aspx?id=28972) per Windows 8, è anche possibile aprire Windows PowerShell x86 dal menu **Strumenti di Server Manager**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-129">If you are running [Remote Server Administration Tools](http://www.microsoft.com/download/details.aspx?id=28972) for Windows 8, you can also open Windows PowerShell x86 from the **Server ManagerTools** menu.</span></span> <span data-ttu-id="4cd9e-130">Selezionare **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-130">Select **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-131">Nella schermata **Start** o sul desktop digitare **PowerShell(x86)** e quindi fare clic su **Windows PowerShell (x86)**.</span><span class="sxs-lookup"><span data-stu-id="4cd9e-131">On the **Start** screen or the desktop, type **PowerShell (x86)** and then click **Windows PowerShell (x86)**.</span></span>

-   <span data-ttu-id="4cd9e-132">Dalla riga di comando, immettere: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span><span class="sxs-lookup"><span data-stu-id="4cd9e-132">Via command line, enter: `%SystemRoot%\SysWOW64\WindowsPowerShell\v1.0\powershell.exe`</span></span>

