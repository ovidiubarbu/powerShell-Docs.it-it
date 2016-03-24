# Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra

Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci, come descritto nel blog [qui](http://blogs.msdn.com/b/powershell/archive/2013/12/09/understanding-meta-configuration-in-windows-powershell-desired-state-configuration.aspx). In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente. Nelle tabelle seguenti viene illustrato questo comportamento:

Comportamento nella modalità **PULL**: 

|                                  |**Valore nella metaconfigurazione**|**Valore dopo l'applicazione della metaconfigurazione**|**Frequenza di pull (in minuti)**|**Frequenza di applicazione della configurazione (in minuti)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |                                    |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |40                                  |                                                |

Comportamento nella modalità **PUSH**:

|                                  |**Valore nella metaconfigurazione**|**Valore dopo l'applicazione della metaconfigurazione**|**Frequenza di applicazione della configurazione (in minuti)**|
|----------------------------------|-------------------------------|---------------------------------------------|------------------------------------------------|
|**ConfigurationModeFrequencyMins**|70                             |70                                           |70                                              |
|**RefreshFrequencyMins**          |40                             |40                                           |                                                |
<!--HONumber=Mar16_HO2-->
