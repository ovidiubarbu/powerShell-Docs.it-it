
---
titolo: Chiave del Registro di sistema DSCAutomationHostEnabled ms.date:  2016-05-16 parole chiave:  powershell,descrizione DSC:  
ms.topic: autore articolo: eslesar manager: dongill ms.prod: powershell
---

>Si applica a: Windows PowerShell 5.0

# <a name="dscautomationhostenabled-registry-key"></a>Chiave del Registro di sistema DSCAutomationHostEnabled

DSC usa la chiave del Registro di sistema **DSCAutomationHostEnabled** in **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies** per configurare automaticamente il computer all'avvio iniziale.
DSCAutomationHostEnabled supporta tre modalità:

|  Valore DSCAutomationHostEnabled  |  Descrizione   | 
|---|---| 
0 | Disabilitazione della configurazione della macchina al momento dell'avvio. |
1 | Abilitazione della configurazione della macchina al momento dell'avvio. |
2 | Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente. Questo è il valore predefinito. |

## <a name="see-also"></a>Vedere anche

Per un esempio di come usare questa funzionalità per eseguire configurazione all'avvio iniziale, vedere [Configurare una macchina virtuale all'avvio iniziale tramite DSC](bootstrapDsc.md).


