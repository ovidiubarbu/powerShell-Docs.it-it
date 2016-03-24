# Configurare Gestione configurazione locale DSC con il nuovo attributo per la metaconfigurazione

L'attributo `DscLocalConfigurationManager` definisce un blocco di configurazione come metaconfigurazione, usata per configurare Gestione configurazione locale DSC. Questo attributo limita una configurazione ai soli elementi per configurare Gestione configurazione locale DSC. Durante l'elaborazione, questa configurazione genera un file `*.meta.mof` che viene poi inviato ai nodi di destinazione appropriati tramite il cmdlet `Set-DscLocalConfigurationManager`.

```powershell
[DscLocalConfigurationManager()]
configuration meta
{
    Node localhost
    {
        Settings
        {
            ConfigurationMode = "ApplyAndAutocorrect"
            ConfigurationID = "5603f952-d6c6-4971-88c4-948636bf5c3f"
            RefreshMode = "Pull"
        }
        ConfigurationRepositoryWeb PullServer
        {
            ServerURL = "https://corp.contoso.com/PSDSCPullServer/PSDSCPullServer.svc"
        }
    }
}
```

Nell'esempio precedente la modalità di aggiornamento per Gestione configurazione locale viene configurata per l'uso della modalità pull, viene impostata la modalità di configurazione ApplyAndAutocorrect e vengono definiti il tipo e il percorso del server di pull.

Il nuovo attributo di configurazione sostituisce ed estende le funzionalità della risorsa LocalConfigurationManager da PowerShell 4.0. Questa risorsa LocalConfigurationManager è ancora supportata in configurazioni senza questo attributo per garantire la compatibilità con le versioni precedenti.

Metarisorse:

| **Nome risorsa**            | **Descrizione**                                |
|------------------------------|------------------------------------------------|
| LocalConfigurationManager    | Varie impostazioni per l'esecuzione del motore DSC      |
| PartialConfiguration         | Impostazioni per configurazioni parziali                 |
| ConfigurationRepositoryWeb   | Repository di configurazioni basato sul Web             |
| ConfigurationRepositoryShare | Repository di configurazioni basato su condivisione file      |
| ResourceRepositoryWeb        | Repository di risorse basato sul Web                  |
| ResourceRepositoryShare      | Repository di risorse basato su file                 |
| ReportServerWeb              | Endpoint di creazione report basato sul Web per uno scenario di pull |
<!--HONumber=Mar16_HO2-->
