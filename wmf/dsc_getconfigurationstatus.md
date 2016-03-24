# Informazioni dettagliate sullo stato della configurazione

Il cmdlet `Get-DscConfigurationStatus` ottiene le informazioni sullo stato di configurazione da un nodo di destinazione. Viene restituito un oggetto completo che include informazioni dettagliate sull'esito positivo o negativo dell'esecuzione della configurazione. È possibile esaminare l'oggetto per scoprire i dettagli sull'esecuzione della configurazione, ad esempio:

* Tutte le risorse con errori
* Qualsiasi risorsa che ha richiesto un riavvio
* Impostazioni di metaconfigurazione al momento dell'esecuzione della configurazione
* Altro.

Il set di parametri seguente restituisce informazioni sullo stato per l'ultima esecuzione della configurazione:

```powershell
Get-DscConfigurationStatus  [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```
Il set di parametri seguente restituisce informazioni sullo stato per tutte le esecuzioni della configurazione precedenti:

```powershell
Get-DscConfigurationStatus  -All 
                            [-CimSession <CimSession[]>] 
                            [-ThrottleLimit <int>] 
                            [-AsJob] 
                            [<CommonParameters>]
```

## Esempio

```powershell
PS C:\> $Status = Get-DscConfigurationStatus 

PS C:\> $Status

Status      StartDate               Type            Mode    RebootRequested     NumberOfResources
------      ---------               ----            ----    ---------------     -----------------
Failure     11/24/2015  3:44:56     Consistency     Push    True                36

PS C:\> $Status.ResourcesNotInDesiredState

ConfigurationName       :   MyService
DependsOn               :   
ModuleName              :   PSDesiredStateConfiguration
ModuleVersion           :   1.1
PsDscRunAsCredential    :   
ResourceID              :   [File]ServiceDll
SourceInfo              :   c:\git\CustomerService\Configs\MyCustomService.ps1::5::34::File
DurationInSeconds       :   0.19
Error                   :   SourcePath must be accessible for current configuration. The related file/directory is:
                            \\Server93\Shared\contosoApp.dll. The related ResourceID is [File]ServiceDll
FinalState              :   
InDesiredState          :   False
InitialState            :   
InstanceName            :   ServiceDll
RebootRequested         :   False
ReosurceName            :   File
StartDate               :   11/24/2015  3:44:56
PSComputerName          :
```<!--HONumber=Mar16_HO2-->
