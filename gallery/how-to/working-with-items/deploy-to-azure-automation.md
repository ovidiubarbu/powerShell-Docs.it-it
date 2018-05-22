---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Distribuire in Automazione di Azure
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a>Distribuire in Automazione di Azure

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli dell'elemento consente di distribuire l'elemento da PowerShell Gallery in Automazione di Azure.

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](../../Images/DeployToAzureAutomationButton.png)

Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.
Se l'elemento include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.

> [!WARNING]
> Se nell'account di Automazione esistono già lo stesso elemento e la stessa versione e si esegue nuovamente la distribuzione da PowerShell Gallery, l'elemento nell'account di Automazione verrà sovrascritto.

Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.  Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati dell'elemento.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure

Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza. Facendo clic su OK, si accettano le condizioni di licenza.'

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Altri dettagli

- [Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Richiedere l'accettazione della licenza in PowerShell Gallery](items-that-require-license-acceptance.md)
- [Sito Web di Automazione di Azure](http://azure.microsoft.com/services/automation/)
