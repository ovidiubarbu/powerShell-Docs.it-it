---
ms.date: 06/12/2017
contributor: JKeithB
keywords: gallery,powershell,cmdlet,psgallery
title: Distribuire in Automazione di Azure
ms.openlocfilehash: 5d09a0777c59b642400d683c8cb6f881319fb881
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278737"
---
# <a name="deploy-to-azure-automation"></a>Distribuire in Automazione di Azure

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) nella pagina dei dettagli del pacchetto consente di distribuire il pacchetto da PowerShell Gallery in Automazione di Azure.

![Pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure)](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

Quando si fa clic su questo pulsante, si verrà reindirizzati al portale di gestione di Azure, in cui si accede usando le credenziali del proprio account di Azure.
Se il pacchetto include dipendenze, verranno distribuite anche tutte le dipendenze in Automazione di Azure.

> [!WARNING]
> Se nell'account di Automazione esistono già lo stesso pacchetto e la stessa versione e si esegue nuovamente la distribuzione da PowerShell Gallery, il pacchetto nell'account di Automazione verrà sovrascritto.

Se si distribuisce un modulo, verrà visualizzato nella sezione Moduli di Automazione di Azure.  Se si distribuisce uno script, verrà visualizzato nella sezione Runbook di Automazione di Azure.

Il pulsante Deploy to Azure Automation (Distribuisci in Automazione di Azure) può essere disabilitato aggiungendo il tag AzureAutomationNotSupported ai metadati del pacchetto.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure

Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza. Facendo clic su OK, si accettano le condizioni di licenza.'

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Altre informazioni

- [Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
- [Richiedere l'accettazione della licenza in PowerShell Gallery](packages-that-require-license-acceptance.md)
- [Sito Web di Automazione di Azure](https://azure.microsoft.com/services/automation/)
