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
<a name="deploy-to-azure-automation"></a>Distribuire in Automazione di Azure
===========================

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento consente di distribuire l'elemento da PowerShell Gallery in Automazione di Azure.

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](Images/DeployToAzureAutomationButton.png)

Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.
Se l'elemento include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.

AVVISO: se nell'account di Automazione esistono già lo stesso elemento e la stessa versione, se si esegue nuovamente la distribuzione da PowerShell Gallery, l'elemento nell'account di Automazione verrà sovrascritto.

Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.  Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati dell'elemento.

Per altre informazioni su Automazione di Azure, vedere il [sito Web di Automazione di Azure](http://azure.microsoft.com/services/automation/).