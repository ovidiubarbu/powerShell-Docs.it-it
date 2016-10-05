# Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra

Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci. In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente. 

Per altre informazioni, vedere [Configurazione di Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig).

<!--HONumber=Aug16_HO3-->


