---
ms.openlocfilehash: 84b29953f09eb62eb30f52d84b087eb4f1f90eed
ms.sourcegitcommit: bc42c9166857147a1ecf9924b718d4a48eb901e3
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/03/2019
ms.locfileid: "66470652"
---
# <a name="microsoft-open-source-code-of-conduct"></a><span data-ttu-id="1ba75-101">Codice di condotta Microsoft Open Source</span><span class="sxs-lookup"><span data-stu-id="1ba75-101">Microsoft Open Source Code of Conduct</span></span>

<span data-ttu-id="1ba75-102">Per questo progetto è stato adottato [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) (Codice di condotta Microsoft Open Source).</span><span class="sxs-lookup"><span data-stu-id="1ba75-102">This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/).</span></span>
<span data-ttu-id="1ba75-103">Per altre informazioni, vedere [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) (Domande frequenti sul codice di condotta) oppure contattare [opencode@microsoft.com](mailto:opencode@microsoft.com) per eventuali domande o commenti.</span><span class="sxs-lookup"><span data-stu-id="1ba75-103">For more information see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/) or contact [opencode@microsoft.com](mailto:opencode@microsoft.com) with any additional questions or comments.</span></span>

[live-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=live
[staging-badge]: https://powershell.visualstudio.com/PowerShell-Docs/_apis/build/status/PowerShell-Docs-CI?branchName=staging

## <a name="build-status"></a><span data-ttu-id="1ba75-106">Stato della compilazione</span><span class="sxs-lookup"><span data-stu-id="1ba75-106">Build Status</span></span>

| <span data-ttu-id="1ba75-107">Ramo attivo</span><span class="sxs-lookup"><span data-stu-id="1ba75-107">Live Branch</span></span> | <span data-ttu-id="1ba75-108">Ramo di staging</span><span class="sxs-lookup"><span data-stu-id="1ba75-108">Staging Branch</span></span> |
|:------------|:---------------|
| <span data-ttu-id="1ba75-109">[![live-badge][]][live-badge]</span><span class="sxs-lookup"><span data-stu-id="1ba75-109">[![live-badge][]][live-badge]</span></span> | <span data-ttu-id="1ba75-110">[![staging-badge][]][staging-badge]</span><span class="sxs-lookup"><span data-stu-id="1ba75-110">[![staging-badge][]][staging-badge]</span></span>

## <a name="powershell-documentation"></a><span data-ttu-id="1ba75-111">Documentazione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="1ba75-111">PowerShell Documentation</span></span>

<span data-ttu-id="1ba75-112">Questo è il repository PowerShell-Docs, che contiene la documentazione ufficiale di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1ba75-112">Welcome to the PowerShell-Docs repository, housing the official PowerShell documentation.</span></span>

## <a name="repository-structure"></a><span data-ttu-id="1ba75-113">Struttura del repository</span><span class="sxs-lookup"><span data-stu-id="1ba75-113">Repository Structure</span></span>

<span data-ttu-id="1ba75-114">Ognuna delle cartelle di primo livello seguenti in questo repository contiene un set di documenti pubblicato in [Microsoft Docs](https://docs.microsoft.com/powershell).</span><span class="sxs-lookup"><span data-stu-id="1ba75-114">Each of the following top-level folders in this repo contain a DocSet that is published to [Microsoft Docs](https://docs.microsoft.com/powershell).</span></span>

- <span data-ttu-id="1ba75-115">[/developer/](https://docs.microsoft.com/powershell/developer/) è la posizione futura della documentazione di PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="1ba75-115">[/developer/](https://docs.microsoft.com/powershell/developer/) is the future home of the PowerShell SDK documentation</span></span>
  - <span data-ttu-id="1ba75-116">È in corso la migrazione di questo contenuto da MSDN</span><span class="sxs-lookup"><span data-stu-id="1ba75-116">We are in the process of migrating this content from MSDN</span></span>
- <span data-ttu-id="1ba75-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) per la funzionalità DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="1ba75-117">[/dsc/](https://docs.microsoft.com/powershell/dsc/) is for the Desired State Configuration feature</span></span>
- <span data-ttu-id="1ba75-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) per [PowerShell Gallery](https://www.powershellgallery.com/)</span><span class="sxs-lookup"><span data-stu-id="1ba75-118">[/gallery/](https://docs.microsoft.com/powershell/gallery) is for the [PowerShell Gallery](https://www.powershellgallery.com/)</span></span>
- <span data-ttu-id="1ba75-119">[/jea/](https://docs.microsoft.com/powershell/jea/) per la funzionalità JEA (Just Enough Administration)</span><span class="sxs-lookup"><span data-stu-id="1ba75-119">[/jea/](https://docs.microsoft.com/powershell/jea/) is for the Just Enough Administration feature</span></span>
- <span data-ttu-id="1ba75-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) per gli argomenti concettuali relativi a PowerShell e per le informazioni di riferimento sui moduli per le versioni 3.0, 4.0, 5.0, 5.1 e 6.0</span><span class="sxs-lookup"><span data-stu-id="1ba75-120">[/reference/](https://docs.microsoft.com/powershell/scripting/) is for PowerShell conceptual topics and module reference across versions 3.0, 4.0, 5.0, 5.1, and 6.0</span></span>
  - <span data-ttu-id="1ba75-121">Questo contenuto è anche l'origine del contenuto della Guida recuperato tramite il cmdlet `Get-Help`</span><span class="sxs-lookup"><span data-stu-id="1ba75-121">This content is also the source of help content retrieved by the `Get-Help` cmdlet</span></span>
- <span data-ttu-id="1ba75-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contiene le note sulla versione per Windows Management Framework, il pacchetto usato per distribuire le nuove versioni di PowerShell nelle versioni precedenti di Windows.</span><span class="sxs-lookup"><span data-stu-id="1ba75-122">[/wmf](https://docs.microsoft.com/powershell/wmf/readme) contains release notes for the Windows Management Framework, the package used to distribute new versions of PowerShell to previous versions of Windows.</span></span>

## <a name="contributing"></a><span data-ttu-id="1ba75-123">Contributi</span><span class="sxs-lookup"><span data-stu-id="1ba75-123">Contributing</span></span>

<span data-ttu-id="1ba75-124">I contributi vengono aggiunti attivamente a questo repository tramite [richiesta pull](https://help.github.com/articles/using-pull-requests/) nel ramo di *staging*.</span><span class="sxs-lookup"><span data-stu-id="1ba75-124">We actively merge contributions into this repository via [pull request](https://help.github.com/articles/using-pull-requests/) into the *staging* branch.</span></span>
<span data-ttu-id="1ba75-125">Si noti che prima di inviare una richiesta pull è necessario [firmare un contratto di licenza per i contributi](https://cla.microsoft.com/) in modo che la community possa liberamente usare i contributi inviati.</span><span class="sxs-lookup"><span data-stu-id="1ba75-125">Please note that before you submit a pull request you must [sign a Contribution License Agreement](https://cla.microsoft.com/) to ensure that the community is free to use your submissions.</span></span>

<span data-ttu-id="1ba75-126">Per altre informazioni sui contributi, leggere la [guida per i collaboratori](CONTRIBUTING.md).</span><span class="sxs-lookup"><span data-stu-id="1ba75-126">For more information on contributing, read our [contributor's guide](CONTRIBUTING.md).</span></span>
<span data-ttu-id="1ba75-127">La guida per i collaboratori contiene informazioni dettagliate su come contribuire alla documentazione, sugli strumenti suggeriti, nonché sui requisiti di stile e di formattazione.</span><span class="sxs-lookup"><span data-stu-id="1ba75-127">The contributor's guide contains detail information about how to contribute documentation, suggested tools, and style and formatting requirements.</span></span>
<span data-ttu-id="1ba75-128">Usare i modelli per i problemi e le richieste di pull per garantire la coerenza della documentazione tra le varie versioni.</span><span class="sxs-lookup"><span data-stu-id="1ba75-128">Please use the Issue and Pull Request templates to help keep documentation consistent across versions.</span></span>

## <a name="licenses"></a><span data-ttu-id="1ba75-129">Licenze</span><span class="sxs-lookup"><span data-stu-id="1ba75-129">Licenses</span></span>

<span data-ttu-id="1ba75-130">Sono disponibili due file di licenza per questo progetto.</span><span class="sxs-lookup"><span data-stu-id="1ba75-130">There are two license files for this project.</span></span>
<span data-ttu-id="1ba75-131">La licenza MIT si applica al codice contenuto in questo repository.</span><span class="sxs-lookup"><span data-stu-id="1ba75-131">The MIT License applies to the code contained in this repo.</span></span>
<span data-ttu-id="1ba75-132">La licenza Creative Commons si applica alla documentazione.</span><span class="sxs-lookup"><span data-stu-id="1ba75-132">The Creative Commons license applies to the documentation.</span></span>