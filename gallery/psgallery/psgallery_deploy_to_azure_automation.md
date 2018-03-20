---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: gallery,powershell,cmdlet,psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 223acbcc2f6cd4f15e1ee55d3f2f68df851cd902
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="16185-103">Distribuire in Automazione di Azure</span><span class="sxs-lookup"><span data-stu-id="16185-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="16185-104">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento consente di distribuire l'elemento da PowerShell Gallery in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="16185-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="16185-106">Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.</span><span class="sxs-lookup"><span data-stu-id="16185-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="16185-107">Se l'elemento include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="16185-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="16185-108">AVVISO: se nell'account di Automazione esistono già lo stesso elemento e la stessa versione, se si esegue nuovamente la distribuzione da PowerShell Gallery, l'elemento nell'account di Automazione verrà sovrascritto.</span><span class="sxs-lookup"><span data-stu-id="16185-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="16185-109">Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="16185-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="16185-110">Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.</span><span class="sxs-lookup"><span data-stu-id="16185-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="16185-111">Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="16185-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="16185-112">Per altre informazioni su Automazione di Azure, vedere il [sito Web di Automazione di Azure](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="16185-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>

