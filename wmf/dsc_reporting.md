# Invio di report sullo stato della configurazione in una posizione centrale

È possibile inviare informazioni dettagliate sullo stato di configurazione di DSC a un server che esegue il servizio DSC. Al servizio DSC vengono inviate le stesse informazioni restituite dal cmdlet Get-DscConfigurationStatus Definendo il server di report in una metaconfigurazione, queste informazioni sullo stato vengono inviate al server quando si verifica un errore o la configurazione viene completata correttamente. Queste informazioni vengono inviate quando un nodo è configurato in modalità pull o push. Le informazioni sullo stato vengono archiviate nel database del servizio DSC.

## Metaconfigurazione di esempio per i report sullo stato
```PowerShell
[DscLocalConfigurationManager()]
Configuration ReportingClientMetaConfig
{
    Settings
        {
            RefreshFrequencyMins = 30
            RefreshMode = "PUSH"
            ConfigurationModeFrequencyMins = 15
            AllowModuleOverwrite = $true
        }

        ReportServerWeb ReportManager
        {
            ServerUrL = "http://localhost:8080/PSDSCPullServer/PSDSCPullserver.svc"
            AllowUnsecureConnection  = $true
        }           
}
```
Viene creato un nuovo endpoint OData con il servizio DSC che espone queste informazioni sullo stato. Passando un ID di configurazione o un ID di agente {$guid} all'endpoint, è possibile raccogliere e analizzare tutte le informazioni sullo stato per un nodo.

## Esempio di richiesta Web per raccogliere lo stato della configurazione 
```PowerShell
$statusReports = Invoke-WebRequest -Uri "[http://localhost:8080/PSDSCPullserver/PSDSCPullserver.svc/Node(ConfigurationId='$guid')/StatusReport](http://localhost:8080/PSDSCPullserver/psdscpullserver.svc/Node(ConfigurationId='$guid')/StatusReport)s" -UseBasicParsing -UseDefaultCredentials -ContentType "application/json;odata=minimalmetadata;streaming=true;charset=utf-8" -Headers @{Accept = "application/json"; ProtocolVersion = “1.1”}
```<!--HONumber=Mar16_HO2-->
