---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
title: Disinstallare WMF 5.0
ms.openlocfilehash: f562a4a4506bfdede6b23bd186b80f40cc9e45ca
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147861"
---
# <a name="uninstallation-instructions"></a><span data-ttu-id="65f44-103">Istruzioni di disinstallazione</span><span class="sxs-lookup"><span data-stu-id="65f44-103">Uninstallation Instructions</span></span>

## <a name="using-command-prompt"></a><span data-ttu-id="65f44-104">Dal prompt dei comandi</span><span class="sxs-lookup"><span data-stu-id="65f44-104">Using Command Prompt</span></span>

1. <span data-ttu-id="65f44-105">Aprire **Prompt dei comandi**.</span><span class="sxs-lookup"><span data-stu-id="65f44-105">Open **Command Prompt.**</span></span>
2. <span data-ttu-id="65f44-106">Eseguire il [programma di avvio di Windows Update autonomo](https://support.microsoft.com/en-us/kb/934307) come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="65f44-106">Run the [Windows Update Standalone Launcher](https://support.microsoft.com/en-us/kb/934307) as shown below:</span></span>

<span data-ttu-id="65f44-107">In Windows Server 2012 R2 e Windows 8.1:</span><span class="sxs-lookup"><span data-stu-id="65f44-107">On Windows Server 2012 R2 and Windows 8.1:</span></span>

```powershell
wusa /uninstall /kb:3134758
```

<span data-ttu-id="65f44-108">In Windows Server 2012:</span><span class="sxs-lookup"><span data-stu-id="65f44-108">On Windows Server 2012:</span></span>

```powershell
wusa /uninstall /kb:3134759
```

<span data-ttu-id="65f44-109">In Windows Server 2008 R2 SP1 e Windows 7 SP1:</span><span class="sxs-lookup"><span data-stu-id="65f44-109">On Windows Server 2008 R2 SP1 and Windows 7 SP1:</span></span>

```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a><span data-ttu-id="65f44-110">Dal Pannello di controllo</span><span class="sxs-lookup"><span data-stu-id="65f44-110">Using Control Panel</span></span>

1. <span data-ttu-id="65f44-111">Aprire il **Pannello di controllo**.</span><span class="sxs-lookup"><span data-stu-id="65f44-111">Open **Control Panel.**</span></span>
2. <span data-ttu-id="65f44-112">Aprire **Programmi** e quindi **Disinstalla un programma**.</span><span class="sxs-lookup"><span data-stu-id="65f44-112">Open **Programs**, then open **Uninstall a program.**</span></span>
3. <span data-ttu-id="65f44-113">Fare clic su **Visualizza aggiornamenti installati**.</span><span class="sxs-lookup"><span data-stu-id="65f44-113">Click **View installed updates.**</span></span>
4. <span data-ttu-id="65f44-114">Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati.</span><span class="sxs-lookup"><span data-stu-id="65f44-114">Select **Windows Management Framework 5.0** from the list of installed updates.</span></span> <span data-ttu-id="65f44-115">Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*.</span><span class="sxs-lookup"><span data-stu-id="65f44-115">This corresponds to *KB3134758*, *KB3134759*, or *KB3134760*.</span></span> <span data-ttu-id="65f44-116">Fare clic su **Disinstalla**.</span><span class="sxs-lookup"><span data-stu-id="65f44-116">Click **Uninstall.**</span></span>
