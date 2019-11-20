---
ms.date: 06/12/2017
contributor: Farehar
keywords: raccolta,powershell,psgallery
title: Richiedi accettazione della licenza
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328212"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="172f4-103">Richiedi accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="172f4-103">Require license acceptance</span></span>

<span data-ttu-id="172f4-104">Il testo Richiedi accettazione della licenza viene visualizzato nella pagina dei dettagli degli elementi per i moduli che richiedono l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="172f4-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="172f4-105">La licenza per il modulo può essere visualizzata facendo clic sul collegamento 'View License.txt' (Visualizza License.txt).</span><span class="sxs-lookup"><span data-stu-id="172f4-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Richiedi accettazione della licenza](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="172f4-107">Agli utenti verrà richiesto di accettare la licenza durante l'installazione, il salvataggio o l'aggiornamento del modulo tramite PowerShellGet o per la distribuzione in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="172f4-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="172f4-108">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="172f4-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="172f4-109">Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="172f4-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="172f4-110">Facendo clic su OK, si accettano le condizioni di licenza.'</span><span class="sxs-lookup"><span data-stu-id="172f4-110">By clicking OK, you are accepting license terms.'</span></span>

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="172f4-112">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="172f4-112">More details</span></span>

<span data-ttu-id="172f4-113">[Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
[Sito Web Automazione di Azure](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="172f4-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>