---
ms.date: 06/12/2017
contributor: Farehar
keywords: raccolta,powershell,psgallery
title: Richiedi accettazione della licenza
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278653"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="0bc5f-103">Richiedi accettazione della licenza</span><span class="sxs-lookup"><span data-stu-id="0bc5f-103">Require license acceptance</span></span>

<span data-ttu-id="0bc5f-104">Il testo Richiedi accettazione della licenza viene visualizzato nella pagina dei dettagli degli elementi per i moduli che richiedono l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="0bc5f-105">La licenza per il modulo può essere visualizzata facendo clic sul collegamento 'View License.txt' (Visualizza License.txt).</span><span class="sxs-lookup"><span data-stu-id="0bc5f-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Richiedi accettazione della licenza](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="0bc5f-107">Agli utenti verrà richiesto di accettare la licenza durante l'installazione, il salvataggio o l'aggiornamento del modulo tramite PowerShellGet o per la distribuzione in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="0bc5f-108">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="0bc5f-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="0bc5f-109">Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="0bc5f-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="0bc5f-110">Facendo clic su OK, si accettano le condizioni di licenza.'</span><span class="sxs-lookup"><span data-stu-id="0bc5f-110">By clicking OK, you are accepting license terms.'</span></span>

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="0bc5f-112">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="0bc5f-112">More details</span></span>

<span data-ttu-id="0bc5f-113">[Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
[Sito Web Automazione di Azure](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="0bc5f-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
