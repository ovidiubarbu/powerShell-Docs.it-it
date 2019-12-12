---
ms.date: 06/12/2017
contributor: manikb
keywords: raccolta,powershell,cmdlet,psget
title: Risoluzione dei problemi relativi a cmdlet
ms.openlocfilehash: d87c680472c2588efbfe8b3c4d6f2dbee6883a0c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72352118"
---
# <a name="troubleshooting-cmdlets"></a><span data-ttu-id="4d726-103">Risoluzione dei problemi relativi a cmdlet</span><span class="sxs-lookup"><span data-stu-id="4d726-103">Troubleshooting cmdlets</span></span>

## <a name="how-to-resolve-warning-package-your-package-name-failed-to-download-issue"></a><span data-ttu-id="4d726-104">Come risolvere il problema "AVVISO: Impossibile scaricare il pacchetto 'nome pacchetto'"</span><span class="sxs-lookup"><span data-stu-id="4d726-104">How to resolve "WARNING: Package 'your package name' failed to download" issue</span></span>

<span data-ttu-id="4d726-105">È stato segnalato che `Install-Module` o `Update-Module` talvolta causa errori in alcuni computer.</span><span class="sxs-lookup"><span data-stu-id="4d726-105">It is reported that `Install-Module` or `Update-Module` sometimes fails on some machines.</span></span> <span data-ttu-id="4d726-106">In base alle ricerche effettuate, il problema ha probabilmente a che fare con la connessione di rete.</span><span class="sxs-lookup"><span data-stu-id="4d726-106">Based on our investigation, it is something to do with the networking connection.</span></span> <span data-ttu-id="4d726-107">Di recente è stato aggiornato il provider NuGet per assicurare il download affidabile dei pacchetti.</span><span class="sxs-lookup"><span data-stu-id="4d726-107">Recently we updated NuGet provider so that it can reliably download packages.</span></span> <span data-ttu-id="4d726-108">È possibile usare le istruzioni riportate di seguito per installare la build più recente del provider NuGet e quindi installare o aggiornare il proprio modulo.</span><span class="sxs-lookup"><span data-stu-id="4d726-108">You can follow the instructions below to install the latest build of NuGet provider and then install or update your module.</span></span> <span data-ttu-id="4d726-109">Nell'esempio viene usato il modulo 'Azure'.</span><span class="sxs-lookup"><span data-stu-id="4d726-109">Let's use 'Azure' module as an example below.</span></span>

```powershell
Install-PackageProvider NuGet -MinimumVersion 2.8.5.206 -Force
Launch new PowerShell Console
Update-Module Azure -Verbose
```

### <a name="required-network-endpoints"></a><span data-ttu-id="4d726-110">Endpoint di rete richiesti</span><span class="sxs-lookup"><span data-stu-id="4d726-110">Required network endpoints</span></span>

<span data-ttu-id="4d726-111">I cmdlet di installazione e aggiornamento richiedono l'accesso a Internet per connettersi agli endpoint di rete usati da PowerShell Gallery.</span><span class="sxs-lookup"><span data-stu-id="4d726-111">The Install and Update cmdlets require internet access to connect to the network endpoints used by by the PowerShell Gallery.</span></span> <span data-ttu-id="4d726-112">Assicurarsi che i criteri di accesso alla rete consentano di connettersi agli endpoint seguenti.</span><span class="sxs-lookup"><span data-stu-id="4d726-112">Ensure that your network access policies allow you to connect to the following endpoints.</span></span>

- <span data-ttu-id="4d726-113">oneget.org</span><span class="sxs-lookup"><span data-stu-id="4d726-113">oneget.org</span></span>
- <span data-ttu-id="4d726-114">go.microsoft.com</span><span class="sxs-lookup"><span data-stu-id="4d726-114">go.microsoft.com</span></span>
- <span data-ttu-id="4d726-115">az818661.vo.msecnd.net</span><span class="sxs-lookup"><span data-stu-id="4d726-115">az818661.vo.msecnd.net</span></span>
- <span data-ttu-id="4d726-116">[www.powershellgallery.com](www.powershellgallery.com)</span><span class="sxs-lookup"><span data-stu-id="4d726-116">www.powershellgallery.com</span></span>
- <span data-ttu-id="4d726-117">devopsgallerystorage.blob.core.windows.net</span><span class="sxs-lookup"><span data-stu-id="4d726-117">devopsgallerystorage.blob.core.windows.net</span></span>
