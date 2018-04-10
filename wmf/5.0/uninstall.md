---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 78ae7ecd40b4d8ad0a6750f43002986483ab18a7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="6a9e8-102">Istruzioni di disinstallazione</span><span class="sxs-lookup"><span data-stu-id="6a9e8-102">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="6a9e8-103">Dal prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="6a9e8-103">Using Command Prompt</span></span>
1.  <span data-ttu-id="6a9e8-104">Aprire **Prompt dei comandi**.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-104">Open **Command Prompt.**</span></span>
2.  <span data-ttu-id="6a9e8-105">Eseguire il [programma di avvio di Windows Update autonomo](https://support.microsoft.com/en-us/kb/934307) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="6a9e8-105">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="6a9e8-106">In Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="6a9e8-106">On Windows Server 2012 R2 and Windows 8.1:</span></span>
```powershell
wusa /uninstall /kb:3134758
```
<span data-ttu-id="6a9e8-107">In Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="6a9e8-107">On Windows Server 2012:</span></span>
```powershell
wusa /uninstall /kb:3134759
```
<span data-ttu-id="6a9e8-108">In Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="6a9e8-108">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="6a9e8-109">Dal Pannello di controllo</span><span class="sxs-lookup"><span data-stu-id="6a9e8-109">Using Control Panel</span></span>
1.  <span data-ttu-id="6a9e8-110">Aprire il **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-110">Open **Control Panel.**</span></span>
2.  <span data-ttu-id="6a9e8-111">Aprire **Programmi** e quindi **Disinstalla un programma**.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-111">Open **Programs**, then open **Uninstall a program.**</span></span>
3.  <span data-ttu-id="6a9e8-112">Fare clic su **Visualizza aggiornamenti installati**.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-112">Click **View installed updates.**</span></span>
4.  <span data-ttu-id="6a9e8-113">Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-113">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="6a9e8-114">Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-114">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="6a9e8-115">Fare clic su **Disinstalla**.</span><span class="sxs-lookup"><span data-stu-id="6a9e8-115">Click **Uninstall.**</span></span>