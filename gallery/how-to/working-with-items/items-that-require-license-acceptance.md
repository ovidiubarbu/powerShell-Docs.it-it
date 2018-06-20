---
ms.date: 06/12/2017
contributor: Farehar
keywords: raccolta,powershell,psgallery
title: Richiedi accettazione della licenza
ms.openlocfilehash: 69787cdb12aa47223072551c9b68fc046573f022
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218400"
---
# <a name="require-license-acceptance"></a>Richiedi accettazione della licenza

Il testo Richiedi accettazione della licenza viene visualizzato nella pagina dei dettagli degli elementi per i moduli che richiedono l'accettazione della licenza. La licenza per il modulo può essere visualizzata facendo clic sul collegamento 'View License.txt' (Visualizza License.txt).

![Richiedi accettazione della licenza](../../Images/RequireLicenseAcceptance.png)

Agli utenti verrà richiesto di accettare la licenza durante l'installazione, il salvataggio o l'aggiornamento del modulo tramite PowerShellGet o per la distribuzione in Automazione di Azure.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure

Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza. Facendo clic su OK, si accettano le condizioni di licenza.'

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Altri dettagli

[Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
[Sito Web Automazione di Azure](/azure/automation)