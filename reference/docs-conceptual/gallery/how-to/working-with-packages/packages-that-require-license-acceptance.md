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
# <a name="require-license-acceptance"></a>Richiedi accettazione della licenza

Il testo Richiedi accettazione della licenza viene visualizzato nella pagina dei dettagli degli elementi per i moduli che richiedono l'accettazione della licenza. La licenza per il modulo può essere visualizzata facendo clic sul collegamento 'View License.txt' (Visualizza License.txt).

![Richiedi accettazione della licenza](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

Agli utenti verrà richiesto di accettare la licenza durante l'installazione, il salvataggio o l'aggiornamento del modulo tramite PowerShellGet o per la distribuzione in Automazione di Azure.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Richiedere l'accettazione della licenza per la distribuzione in Automazione di Azure

Se per il modulo da distribuire in Automazione di Azure è richiesta l'accettazione della licenza, l'interfaccia utente del portale visualizzerà un messaggio di dichiarazione di non responsabilità che indica 'Questo modulo richiede l'accettazione della licenza. Facendo clic su OK, si accettano le condizioni di licenza.'

![Per la distribuzione in Automazione di Azure è richiesta l'accettazione della licenza](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Altre informazioni

[Richiedere l'accettazione della licenza in PowerShellGet](../../concepts/module-license-acceptance.md)
[Sito Web Automazione di Azure](/azure/automation)
