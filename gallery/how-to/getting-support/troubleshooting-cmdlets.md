---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: 6295a5b99aa19db933569638d84e490ad81eedc7
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/10/2018
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="db3cf-103">Risoluzione dei problemi relativi a cmdlet</span><span class="sxs-lookup"><span data-stu-id="db3cf-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="db3cf-104">Come risolvere il problema segnalato da un messaggio simile a: "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"</span><span class="sxs-lookup"><span data-stu-id="db3cf-104">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>

<span data-ttu-id="db3cf-105">È stato segnalato che il cmdlet Install-Module o Update-Module a volte genera un errore in alcuni computer.</span><span class="sxs-lookup"><span data-stu-id="db3cf-105">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="db3cf-106">In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.</span><span class="sxs-lookup"><span data-stu-id="db3cf-106">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="db3cf-107">Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="db3cf-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="db3cf-108">È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.</span><span class="sxs-lookup"><span data-stu-id="db3cf-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="db3cf-109">Nell'esempio viene usato il modulo 'Azure'.</span><span class="sxs-lookup"><span data-stu-id="db3cf-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```