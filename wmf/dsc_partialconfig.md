# Configurare un nodo con più frammenti di configurazione (configurazioni parziali)

WMF 5.0 consente di recapitare i documenti di configurazione a un nodo in frammenti. Affinché un nodo possa ricevere più frammenti di un documento di configurazione, l'istanza di Gestione configurazione locale nel nodo deve essere impostata in modo da specificare i frammenti previsti, come illustrato in questo esempio.

```powershell
[DSCLocalConfigurationManager()]
configuration SQLServerDSCSettings
{
    Node localhost
    {
        Settings
        {
            ConfigurationModeFrequencyMins = 30
        }

        ConfigurationRepositoryWeb OSConfigServer
        {
            ServerURL = "https://corp.contoso.com/OSConfigServer/PSDSCPullServer.svc"
        }

        ConfigurationRepositoryWeb SQLConfigServer
        {
            ServerURL = "https://corp.contoso.com/SQLConfigServer/PSDSCPullServer.svc"
        }

        PartialConfiguration OSConfig
        {
            Description = 'Configuration for the Base OS'
            ExclusiveResources = 'PSDesiredStateConfiguration\*'
            ConfigurationSource = '[ConfigurationRepositoryWeb]OSConfigServer'
        }

        PartialConfiguration SQLConfig
        {
            Description = 'Configuration for the SQL Server'
            ConfigurationSource = '[ConfigurationRepositoryWeb]SQLConfigServer'
            DependsOn = '[PartialConfiguration]OSConfig'
        }
    }
}
```

In una configurazione parziale, il nome della configurazione deve corrispondere alla definizione in Gestione configurazione locale. Nell'esempio precedente, le configurazioni devono essere denominate `OSConfig` e `SQLConfig`.

L'impostazione di Gestione configurazione locale per le configurazioni parziali consente il coordinamento delle configurazioni, ma NON offre funzionalità di sicurezza.<!--HONumber=Mar16_HO2-->
