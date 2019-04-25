---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Miglioramenti del motore di PowerShell in WMF 5.1
ms.openlocfilehash: 738f72b910de7d44f48309013237d523d0dd40a4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62055565"
---
# <a name="powershell-engine-improvements"></a><span data-ttu-id="42b25-103">Miglioramenti apportati al motore di PowerShell</span><span class="sxs-lookup"><span data-stu-id="42b25-103">PowerShell Engine Improvements</span></span>

<span data-ttu-id="42b25-104">I miglioramenti seguenti apportati al motore di PowerShell principale sono stati implementati in WMF 5.1:</span><span class="sxs-lookup"><span data-stu-id="42b25-104">The following improvements to the core PowerShell engine have been implemented in WMF 5.1:</span></span>

## <a name="performance"></a><span data-ttu-id="42b25-105">Prestazioni</span><span class="sxs-lookup"><span data-stu-id="42b25-105">Performance</span></span>

<span data-ttu-id="42b25-106">Le prestazioni sono migliorate in alcune aree importanti:</span><span class="sxs-lookup"><span data-stu-id="42b25-106">Performance has improved in some important areas:</span></span>

- <span data-ttu-id="42b25-107">Avvio</span><span class="sxs-lookup"><span data-stu-id="42b25-107">Startup</span></span>
- <span data-ttu-id="42b25-108">L'invio tramite pipe ai cmdlet come `ForEach-Object` e `Where-Object` è circa il 50% più veloce</span><span class="sxs-lookup"><span data-stu-id="42b25-108">Pipelining to cmdlets like `ForEach-Object` and `Where-Object` is approximately 50% faster</span></span>

<span data-ttu-id="42b25-109">Alcuni miglioramenti di esempio (i risultati possono variare in base all'hardware):</span><span class="sxs-lookup"><span data-stu-id="42b25-109">Some example improvements (your results may vary depending on your hardware):</span></span>

| <span data-ttu-id="42b25-110">Scenario</span><span class="sxs-lookup"><span data-stu-id="42b25-110">Scenario</span></span> | <span data-ttu-id="42b25-111">5.0 - Tempo (ms)</span><span class="sxs-lookup"><span data-stu-id="42b25-111">5.0 Time (ms)</span></span> | <span data-ttu-id="42b25-112">5.1 - Tempo (ms)</span><span class="sxs-lookup"><span data-stu-id="42b25-112">5.1 Time (ms)</span></span> |
| -------- | :---------------: | :---------------: |
| `powershell -command "echo 1"` | <span data-ttu-id="42b25-113">900</span><span class="sxs-lookup"><span data-stu-id="42b25-113">900</span></span> | <span data-ttu-id="42b25-114">250</span><span class="sxs-lookup"><span data-stu-id="42b25-114">250</span></span> |
| <span data-ttu-id="42b25-115">Prima esecuzione di PowerShell: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="42b25-115">First ever PowerShell run: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="42b25-116">30000</span><span class="sxs-lookup"><span data-stu-id="42b25-116">30000</span></span> | <span data-ttu-id="42b25-117">13000</span><span class="sxs-lookup"><span data-stu-id="42b25-117">13000</span></span> |
| <span data-ttu-id="42b25-118">Cache di analisi del comando integrata: `powershell -command "Unknown-Command"`</span><span class="sxs-lookup"><span data-stu-id="42b25-118">Command analysis cache built: `powershell -command "Unknown-Command"`</span></span> | <span data-ttu-id="42b25-119">7000</span><span class="sxs-lookup"><span data-stu-id="42b25-119">7000</span></span> | <span data-ttu-id="42b25-120">520</span><span class="sxs-lookup"><span data-stu-id="42b25-120">520</span></span> |
| <code>1..1000000 &#124; % { }</code> | <span data-ttu-id="42b25-121">1400</span><span class="sxs-lookup"><span data-stu-id="42b25-121">1400</span></span> | <span data-ttu-id="42b25-122">750</span><span class="sxs-lookup"><span data-stu-id="42b25-122">750</span></span> |

> [!Note]
> <span data-ttu-id="42b25-123">Una modifica correlata all'avvio può avere impatto su alcuni scenari non supportati.</span><span class="sxs-lookup"><span data-stu-id="42b25-123">One change related to startup might impact some unsupported scenarios.</span></span>
> <span data-ttu-id="42b25-124">PowerShell non legge i file `$pshome\*.ps1xml`: questi file sono stati convertiti in C# per evitare il sovraccarico dell'elaborazione di file XML da parte di alcuni file e della CPU.</span><span class="sxs-lookup"><span data-stu-id="42b25-124">PowerShell no longer reads the files `$pshome\*.ps1xml` -- these files have been converted to C# to avoid some file and CPU overhead of processing the XML files.</span></span>
> <span data-ttu-id="42b25-125">I file supportano ancora V2 side-by-side, pertanto se si modifica il contenuto del file, la modifica non avrà alcun impatto su V5, ma solo su V2.</span><span class="sxs-lookup"><span data-stu-id="42b25-125">The files still exist to support V2 side-by-side, so if you change the file contents, it will not have any effect to V5, only V2.</span></span>
> <span data-ttu-id="42b25-126">Si noti che la modifica dei contenuti di questi file non ha mai costituito uno scenario supportato.</span><span class="sxs-lookup"><span data-stu-id="42b25-126">Note that changing the contents of these files was never a supported scenario.</span></span>

<span data-ttu-id="42b25-127">Un'altra modifica evidente riguarda la modalità di memorizzazione nella cache dei comandi esportati e di altre informazioni relative ai moduli installati in un sistema da parte di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="42b25-127">Another visible change is how PowerShell caches the exported commands and other information for modules that are installed on a system.</span></span>
<span data-ttu-id="42b25-128">In precedenza, la cache veniva archiviata nella directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span><span class="sxs-lookup"><span data-stu-id="42b25-128">Previously, this cache was stored in the directory `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\CommandAnalysis`.</span></span>
<span data-ttu-id="42b25-129">In WMF 5.1, la cache è un singolo file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span><span class="sxs-lookup"><span data-stu-id="42b25-129">In WMF 5.1, the cache is a single file `$env:LOCALAPPDATA\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.</span></span>
<span data-ttu-id="42b25-130">Per altre informazioni dettagliate, vedere [Modulo Analysis Cache](scenarios-features.md#module-analysis-cache).</span><span class="sxs-lookup"><span data-stu-id="42b25-130">See [Module Analysis Cache](scenarios-features.md#module-analysis-cache) for more details.</span></span>