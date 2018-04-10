---
ms.date: 06/12/2017
contributor: manikb
ms.topic: reference
keywords: raccolta,powershell,cmdlet,psget
title: psget_cmdlets_troubleshooting
ms.openlocfilehash: bc49dc78b8205d1194ddfe4bdca98b3e681860bd
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="9aa28-103">Come risolvere il problema segnalato da un messaggio simile a: "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"</span><span class="sxs-lookup"><span data-stu-id="9aa28-103">How to resolve "WARNING: Package 'your package name' failed to download" issue?</span></span>




<span data-ttu-id="9aa28-104">È stato segnalato che il cmdlet Install-Module o Update-Module a volte genera un errore in alcuni computer.</span><span class="sxs-lookup"><span data-stu-id="9aa28-104">It is reported that Install-Module or Update-Module sometimes fails on some machines.</span></span>
<span data-ttu-id="9aa28-105">In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.</span><span class="sxs-lookup"><span data-stu-id="9aa28-105">Based on our investigation, it is something to do with the networking connection.</span></span>
<span data-ttu-id="9aa28-106">Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="9aa28-106">Recently we updated NuGet provider so that it can reliably download packages.</span></span>
<span data-ttu-id="9aa28-107">È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.</span><span class="sxs-lookup"><span data-stu-id="9aa28-107">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span>
<span data-ttu-id="9aa28-108">Nell'esempio viene usato il modulo 'Azure'.</span><span class="sxs-lookup"><span data-stu-id="9aa28-108">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```