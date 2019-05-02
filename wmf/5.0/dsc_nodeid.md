---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058200"
---
# <a name="separation-of-node-and-configuration-ids"></a>Separazione degli ID per nodi e configurazioni

## <a name="overview"></a>Panoramica

Per garantire un'esperienza più flessibile e semplificata durante l'uso di DSC in modalità Pull, in questa versione sono state aggiunte numerose funzionalità. Queste funzionalità sono progettate in modo da offrire la flessibilità necessaria per configurare e distribuire le configurazioni su più nodi, offrendo allo stesso tempo la possibilità di tenere traccia dello stato e di creare report di informazioni per ogni nodo singolarmente.
Queste funzionalità sono le seguenti:

* Un nome di configurazione che identifica la configurazione per un computer. Questo nome può essere condiviso da più nodi di destinazione
* Un ID di agente che identifica in modo univoco un singolo nodo
* Un passaggio di registrazione che si verifica solo la prima volta che un nodo di destinazione si connette a un server di pull

**Nota:** queste caratteristiche e funzionalità sono state aggiunte e non sostituiscono i concetti e le funzionalità esistenti relativi al pull. È possibile usare queste nuove funzionalità o quelle meno recenti con il nuovo server di pull incluso in questa versione.

Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).
