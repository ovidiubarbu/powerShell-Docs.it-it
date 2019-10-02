---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Distribuire in Automazione di Azure
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/27/2019
ms.locfileid: "71327912"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="f2bd9-103">Distribuire in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="f2bd9-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="f2bd9-104">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli del pacchetto consente di distribuire il pacchetto da PowerShell Gallery in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="f2bd9-106">Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="f2bd9-107">Se il pacchetto include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="f2bd9-108">Se nell'account di Automazione esistono già lo stesso pacchetto e la stessa versione e si esegue nuovamente la distribuzione da PowerShell Gallery, il pacchetto nell'account di Automazione verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="f2bd9-109">Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="f2bd9-110">Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="f2bd9-111">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati del pacchetto.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="f2bd9-112">Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="f2bd9-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="f2bd9-113">Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza.</span><span class="sxs-lookup"><span data-stu-id="f2bd9-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="f2bd9-114">Facendo clic su OK, si accettano le condizioni di licenza.'</span><span class="sxs-lookup"><span data-stu-id="f2bd9-114">By clicking OK, you are accepting license terms.'</span></span>

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="f2bd9-116">Altri dettagli</span><span class="sxs-lookup"><span data-stu-id="f2bd9-116">More details</span></span>

- [<span data-ttu-id="f2bd9-117">Richiedere l'accettazione della licenza in PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="f2bd9-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="f2bd9-118">Richiedere l'accettazione della licenza in PowerShell Gallery</span><span class="sxs-lookup"><span data-stu-id="f2bd9-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="f2bd9-119">Sito Web di Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="f2bd9-119">Azure Automation website</span></span>](https://azure.microsoft.com/services/automation/)
