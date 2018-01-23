---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: c58b7a8f2485ff02f09763749a3de8a75f882d19
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
>Si applica a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chiave del Registro di sistema DSCAutomationHostEnabled

DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** per abilitare la configurazione del computer all'avvio iniziale.
DSCAutomationHostEnabled supporta tre modalità:

|  Valore DSCAutomationHostEnabled  |  Description   | 
|---|---| 
0 | Disabilitazione della configurazione della macchina al momento dell'avvio. |
1 | Abilitazione della configurazione della macchina al momento dell'avvio. |
2 | Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente. Questo è il valore predefinito. |

## <a name="see-also"></a>Vedere anche

Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).


