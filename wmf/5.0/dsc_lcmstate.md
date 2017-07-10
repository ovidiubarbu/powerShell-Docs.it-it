---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 4fc146f84588d368ac3eb819e3acb4cb8c5d8793
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="detailed-information-about-lcm-state" class="xliff"></a>
# Informazioni dettagliate sullo stato di Gestione configurazione locale

Sono stati introdotti miglioramenti per l'esposizione dei dettagli sullo stato di Gestione configurazione locale. Le informazioni LCMState restituite da Get-DscLocalConfigurationManager possono ora contenere i valori seguenti:

* **Idle**
* **Busy**
* **PendingReboot**
* **PendingConfiguration**

È stata anche aggiunta una proprietà LCMStateDetail che contiene ulteriori informazioni sullo stato.

