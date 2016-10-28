
DSC usa la chiave del Registro di sistema <b>DSCAutomationHostEnabled </b> in <b>HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Policies\System</b> per configurare automaticamente il computer al momento dell'avvio iniziale.
DSCAutomationHostEnabled supporta tre modalità:

|  Valore DSCAutomationHostEnabled  |  Descrizione   | 
|---|---| 
0 | Disabilitazione della configurazione della macchina al momento dell'avvio. |
1 | Abilitazione della configurazione della macchina al momento dell'avvio. |
2 | Abilitazione della configurazione della macchina solo se DSC ha stato in sospeso o corrente. Questo è il valore predefinito. |




<!--HONumber=Oct16_HO2-->


