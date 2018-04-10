---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: baa35e9acd24d6f6155acf617a0d2c2210742af7
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="detailed-information-about-lcm-state"></a>Informazioni dettagliate sullo stato di Gestione configurazione locale

Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale. Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.