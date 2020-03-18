---
title: Uso di PowerShell in Docker
description: Come usare PowerShell preinstallato in un'immagine Docker.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279658"
---
# <a name="using-powershell-in-docker"></a><span data-ttu-id="97fa2-103">Uso di PowerShell in Docker</span><span class="sxs-lookup"><span data-stu-id="97fa2-103">Using PowerShell in Docker</span></span>

<span data-ttu-id="97fa2-104">Le immagini Docker vengono pubblicate con PowerShell preinstallato.</span><span class="sxs-lookup"><span data-stu-id="97fa2-104">We publish Docker images with PowerShell preinstalled.</span></span> <span data-ttu-id="97fa2-105">Questo articolo illustra come iniziare a usare PowerShell nel contenitore Docker.</span><span class="sxs-lookup"><span data-stu-id="97fa2-105">This article shows you how to get started using PowerShell in the Docker container.</span></span>

## <a name="finding-available-images"></a><span data-ttu-id="97fa2-106">Individuazione delle immagini disponibili</span><span class="sxs-lookup"><span data-stu-id="97fa2-106">Finding available images</span></span>

<span data-ttu-id="97fa2-107">Le immagini rilasciate richiedono Docker 17.05 o versione successiva.</span><span class="sxs-lookup"><span data-stu-id="97fa2-107">The released images require Docker 17.05 or newer.</span></span> <span data-ttu-id="97fa2-108">Si presume anche che l'utente sia in grado di eseguire Docker senza `sudo` o diritti amministrativi locali.</span><span class="sxs-lookup"><span data-stu-id="97fa2-108">It is also expected that you are able to run Docker without `sudo` or local administrative rights.</span></span> <span data-ttu-id="97fa2-109">Seguire le [istruzioni][install] ufficiali di Docker per installare `docker` correttamente.</span><span class="sxs-lookup"><span data-stu-id="97fa2-109">Please follow Docker's official [instructions][install] to install `docker` correctly.</span></span>

<span data-ttu-id="97fa2-110">I contenitori di versione derivano dall'immagine di distribuzione ufficiale, ad esempio `centos:7`, quindi installano le dipendenze e infine installano il pacchetto di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97fa2-110">The release containers derive from the official distribution image, such as `centos:7`, then install dependencies, and finally install the PowerShell package.</span></span>

<span data-ttu-id="97fa2-111">Questi contenitori sono disponibili in [hub.docker.com/r/microsoft/powershell][docker-release].</span><span class="sxs-lookup"><span data-stu-id="97fa2-111">These containers live at [hub.docker.com/r/microsoft/powershell][docker-release].</span></span>

<span data-ttu-id="97fa2-112">Per altre informazioni su queste immagini Docker, visitare il repository [PowerShell-Docker][PowerShell-Docker] in GitHub.</span><span class="sxs-lookup"><span data-stu-id="97fa2-112">For more information about these Docker images, visit the [PowerShell-Docker][PowerShell-Docker] repository on GitHub.</span></span>

## <a name="using-powershell-in-a-container"></a><span data-ttu-id="97fa2-113">Uso di PowerShell in un contenitore</span><span class="sxs-lookup"><span data-stu-id="97fa2-113">Using PowerShell in a container</span></span>

<span data-ttu-id="97fa2-114">I passaggi seguenti descrivono i comandi Docker necessari per scaricare l'immagine e avviare una sessione interattiva di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97fa2-114">The following steps show the Docker commands required to download the image and start an interactive PowerShell session.</span></span>

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a><span data-ttu-id="97fa2-115">Rimuovere l'immagine quando non è più necessaria</span><span class="sxs-lookup"><span data-stu-id="97fa2-115">Remove the image when no longer needed</span></span>

<span data-ttu-id="97fa2-116">Il comando seguente viene usato per eliminare il contenitore Docker quando non è più necessario.</span><span class="sxs-lookup"><span data-stu-id="97fa2-116">The following command is used to delete the Docker container when you no longer need it.</span></span>

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a><span data-ttu-id="97fa2-117">Informazioni legali e concessione in licenza</span><span class="sxs-lookup"><span data-stu-id="97fa2-117">Legal and Licensing</span></span>

<span data-ttu-id="97fa2-118">PowerShell viene concesso in licenza in base alla [licenza MIT][].</span><span class="sxs-lookup"><span data-stu-id="97fa2-118">PowerShell is licensed under the [MIT license][].</span></span>

### <a name="windows-docker-file-and-image-licenses"></a><span data-ttu-id="97fa2-119">Licenze per file e immagini Docker per Windows</span><span class="sxs-lookup"><span data-stu-id="97fa2-119">Windows Docker File and Image Licenses</span></span>

<span data-ttu-id="97fa2-120">Richiedendo e usando l'immagine del sistema operativo per i contenitori Windows, l'utente conferma di aver compreso e di accettare le condizioni di licenza supplementari disponibili in Docker Hub:</span><span class="sxs-lookup"><span data-stu-id="97fa2-120">By requesting and using the Container OS Image for Windows containers, you acknowledge, understand, and consent to the Supplemental License Terms available on Docker hub:</span></span>

- <span data-ttu-id="97fa2-121">[Window Server Core][Window Server Core]</span><span class="sxs-lookup"><span data-stu-id="97fa2-121">[Window Server Core][Window Server Core]</span></span>
- <span data-ttu-id="97fa2-122">[Nano Server][Nano Server]</span><span class="sxs-lookup"><span data-stu-id="97fa2-122">[Nano Server][Nano Server]</span></span>

### <a name="telemetry"></a><span data-ttu-id="97fa2-123">Telemetria</span><span class="sxs-lookup"><span data-stu-id="97fa2-123">Telemetry</span></span>

<span data-ttu-id="97fa2-124">Per impostazione predefinita, PowerShell raccoglie dati di telemetria limitati senza informazioni personali per facilitare lo sviluppo di versioni future di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97fa2-124">By default, PowerShell collects limited telemetry without personally identifiable information to help aid development of future versions of PowerShell.</span></span> <span data-ttu-id="97fa2-125">Per rifiutare esplicitamente l'invio di dati di telemetria, creare una variabile di ambiente denominata `POWERSHELL_TELEMETRY_OPTOUT` impostata sul valore `1` prima di avviare PowerShell dal percorso di installazione.</span><span class="sxs-lookup"><span data-stu-id="97fa2-125">To opt-out of sending telemetry, create an environment variable called `POWERSHELL_TELEMETRY_OPTOUT` set to a value of `1` before starting PowerShell from the installed location.</span></span> <span data-ttu-id="97fa2-126">I dati di telemetria raccolti rientrano nell'[informativa sulla privacy di Microsoft][privacy].</span><span class="sxs-lookup"><span data-stu-id="97fa2-126">The telemetry we collect falls under the [Microsoft Privacy Statement][privacy].</span></span>

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[licenza MIT]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[MIT license]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
