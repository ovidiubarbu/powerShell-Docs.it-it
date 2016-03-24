# Valore aggiunto per la proprietà RefreshMode

Questa versione introduce un nuovo valore per `RefreshMode`: **Disabled**. Quando viene impostata questa modalità, Gestione configurazione locale non esegue la gestione dei documenti. Questa modalità può essere usata quando viene usato uno strumento di gestione della configurazione di terze parti invece di DSC, pur continuando a usare le risorse DSC con il cmdlet `Invoke-DscResource` oppure se è semplicemente necessario interrompere l'elaborazione DSC per qualsiasi motivo.

```powershell
Configuration LCMSettings
{
    Node localhost
    {
        LocalConfigurationManager
        {
           RefreshMode = 'Disabled'
        }
    }
}

LCMSettings -OutputPath .\LCMSettings
Set-DscLocalConfigurationManager -Path .\LCMSettings -Verbose -ComputerName localhost
```
<!--HONumber=Mar16_HO2-->
