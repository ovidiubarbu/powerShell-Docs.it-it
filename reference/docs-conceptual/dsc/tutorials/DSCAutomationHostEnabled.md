---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Chiave del Registro di sistema DSCAutomationHostEnabled
ms.openlocfilehash: 2bccd2738b9f61efd656fdf0f98cf71affdbe781
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954268"
---
>Si applica a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chiave del Registro di sistema DSCAutomationHostEnabled

DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System** per abilitare la configurazione del computer in fase di avvio iniziale.
**DSCAutomationHostEnabled** supporta tre modalità:

|  Valore DSCAutomationHostEnabled  |  Descrizione   |
|---|---|
0 | Disabilitazione della configurazione della macchina al momento dell'avvio. |
1 | Abilitazione della configurazione della macchina al momento dell'avvio. |
2 | Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente. Si tratta del valore predefinito. |

## <a name="see-also"></a>Vedere anche

Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).
