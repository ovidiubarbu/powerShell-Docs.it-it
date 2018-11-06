---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: f5cd9c0cc23fef5891bf02c10b6541ab0f9d418a
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002463"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="11c42-103">Risoluzione dei problemi relativi a cmdlet</span><span class="sxs-lookup"><span data-stu-id="11c42-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="11c42-104">Come risolvere il problema segnalato da un messaggio di tipo "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"</span><span class="sxs-lookup"><span data-stu-id="11c42-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="11c42-105">È stato segnalato che `Install-Module` o `Update-Module` talvolta causa errori in alcuni computer.</span><span class="sxs-lookup"><span data-stu-id="11c42-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span>
<span data-ttu-id="11c42-106">In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.</span><span class="sxs-lookup"><span data-stu-id="11c42-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="11c42-107">Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="11c42-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="11c42-108">È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.</span><span class="sxs-lookup"><span data-stu-id="11c42-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="11c42-109">Nell'esempio viene usato il modulo 'Azure'.</span><span class="sxs-lookup"><span data-stu-id="11c42-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```
