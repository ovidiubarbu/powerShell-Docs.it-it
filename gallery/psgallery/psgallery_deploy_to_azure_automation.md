---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="3c527-103">Distribuire in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="3c527-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="3c527-104">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento consente di distribuire l'elemento da PowerShell Gallery in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="3c527-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="3c527-106">Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.</span><span class="sxs-lookup"><span data-stu-id="3c527-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="3c527-107">Se l'elemento include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="3c527-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="3c527-108">AVVISO: se nell'account di Automazione esistono già lo stesso elemento e la stessa versione, se si esegue nuovamente la distribuzione da PowerShell Gallery, l'elemento nell'account di Automazione verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="3c527-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="3c527-109">Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="3c527-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="3c527-110">Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="3c527-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="3c527-111">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="3c527-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="3c527-112">Per altre informazioni su Automazione di Azure, vedere il [sito Web di Automazione di Azure](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="3c527-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>