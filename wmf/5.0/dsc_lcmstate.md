---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: db9b48c188b3bfe2e20c06875606a285922f55a6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219862"
---
# <a name="detailed-information-about-lcm-state"></a>Informazioni dettagliate sullo stato di Gestione configurazione locale

Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale. Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.
