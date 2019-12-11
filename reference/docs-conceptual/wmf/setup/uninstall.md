---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Disinstallare WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71147861"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="71415-103">Istruzioni di disinstallazione</span><span class="sxs-lookup"><span data-stu-id="71415-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="71415-104">Dal prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="71415-104">Using Command Prompt</span></span>

1. <span data-ttu-id="71415-105">Aprire **Prompt dei comandi**.</span><span class="sxs-lookup"><span data-stu-id="71415-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="71415-106">Eseguire il [programma di avvio di Windows Update autonomo](https://support.microsoft.com/en-us/kb/934307) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="71415-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="71415-107">In Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="71415-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="71415-108">In Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="71415-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="71415-109">In Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="71415-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="71415-110">Dal Pannello di controllo</span><span class="sxs-lookup"><span data-stu-id="71415-110">Using Control Panel</span></span>

1. <span data-ttu-id="71415-111">Aprire il **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="71415-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="71415-112">Aprire **Programmi** e quindi **Disinstalla un programma**.</span><span class="sxs-lookup"><span data-stu-id="71415-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="71415-113">Fare clic su **Visualizza aggiornamenti installati**.</span><span class="sxs-lookup"><span data-stu-id="71415-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="71415-114">Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati.</span><span class="sxs-lookup"><span data-stu-id="71415-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="71415-115">Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="71415-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="71415-116">Fare clic su **Disinstalla**.</span><span class="sxs-lookup"><span data-stu-id="71415-116">Click **Uninstall.**</span></span>
