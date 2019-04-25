---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: 57152e9f62c34600df63a2db8e9683928e825d93
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085797"
---
# <a name="detailed-information-about-lcm-state"></a>Informazioni dettagliate sullo stato di Gestione configurazione locale

Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale. Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.
