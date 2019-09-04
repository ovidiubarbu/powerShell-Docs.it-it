---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Get-Test-Set
ms.openlocfilehash: 68738107cd4a222a13dd4afa158f0370953158ad
ms.sourcegitcommit: 02eed65c526ef19cf952c2129f280bb5615bf0c8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/03/2019
ms.locfileid: "70215420"
---
# <a name="get-test-set"></a>Get-Test-Set

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Ottenere, testare e impostare](../media/get-test-set.png)

La configurazione dello stato desiderato di PowerShell è costruita su un processo **Get**, **Test** e **Set**. Le [risorse](resources.md) DSC contengono ciascuna i metodi per completare ognuna di queste operazioni. In una [Configurazione](../configurations/configurations.md) vengono definiti blocchi di risorse in cui inserire chiavi che diventano i parametri per i metodi **Get**, **Test** e **Set** di una risorsa.

Questa è la sintassi per un blocco di risorse **Service**. La risorsa **Service** configura i servizi di Windows.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

I metodi **Get**, **Test** end **Set** della risorsa **Service** avranno blocchi di parametri che accettano questi valori.

```powershell
    param
    (
        [parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [System.String]
        $Name,

        [System.String]
        [ValidateSet("Automatic", "Manual", "Disabled")]
        $StartupType,

        [System.String]
        [ValidateSet("LocalSystem", "LocalService", "NetworkService")]
        $BuiltInAccount,

        [System.Management.Automation.PSCredential]
        [ValidateNotNull()]
        $Credential,

        [System.String]
        [ValidateSet("Running", "Stopped")]
        $State="Running",

        [System.String]
        [ValidateNotNullOrEmpty()]
        $DisplayName,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Description,

        [System.String]
        [ValidateNotNullOrEmpty()]
        $Path,

        [System.String[]]
        [ValidateNotNullOrEmpty()]
        $Dependencies,

        [System.String]
        [ValidateSet("Present", "Absent")]
        $Ensure="Present"
    )
```

> [!NOTE]
> Il linguaggio e il metodo usati per definire la risorsa determinano come definire i metodi **Get**, **Test** e **Set**.

Poiché la risorsa **Service** ha solo una chiave necessaria (`Name`), un blocco di risorse **Service** può essere semplice come il seguente:

```powershell
Configuration TestConfig
{
    Import-DSCResource -Name Service
    Node localhost
    {
        Service "MyService"
        {
            Name = "Spooler"
        }
    }
}
```

Quando si compila la configurazione precedente, i valori specificati per una chiave vengono archiviati nel file "MOF" generato. Per altre informazioni, vedere [MOF](/windows/desktop/wmisdk/managed-object-format--mof-).

```
instance of MSFT_ServiceResource as $MSFT_ServiceResource1ref
{
SourceInfo = "::5::1::Service";
 ModuleName = "PsDesiredStateConfiguration";
 ResourceID = "[Service]MyService";
 Name = "Spooler";

ModuleVersion = "1.0";

 ConfigurationName = "Test";

};
```

Quando applicata, [Gestione configurazione locale](../managing-nodes/metaConfig.md) leggerà il valore "Spooler" dal file "MOF" e lo passerà al parametro `-Name` dei metodi **Get**, **Test** e **Set** per l'istanza "MyService" della risorsa **Service**.

## <a name="get"></a>Get

Il metodo **Get** di una risorsa recupera lo stato della risorsa così come è configurata nel nodo di destinazione. Questo stato viene restituito come [TabellaHash](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Le chiavi della **TabellaHash** saranno i valori configurabili, o parametri, accettati dalla risorsa.

Il metodo **Get** esegue il mapping direttamente sul cmdlet [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration). Quando si richiama `Get-DSCConfiguration`, la gestione configurazione locale (LCM) esegue il metodo **Get** di ciascuna risorsa nella configurazione attualmente applicata. Gestione configurazione locale (LCM) usa i valori di chiave archiviati come parametri nel file "MOF" per ogni istanza di risorsa corrispondente.

Questo è l'output di esempio di una risorsa **Service** che configura il servizio "Spooler".

```output
ConfigurationName    : Test
DependsOn            :
ModuleName           : PsDesiredStateConfiguration
ModuleVersion        : 1.1
PsDscRunAsCredential :
ResourceId           : [Service]Spooler
SourceInfo           :
BuiltInAccount       : LocalSystem
Credential           :
Dependencies         : {RPCSS, http}
Description          : This service spools print jobs and handles interaction with the printer.  If you turn off
                       this service, you won’t be able to print or see your printers.
DisplayName          : Print Spooler
Ensure               :
Name                 : Spooler
Path                 : C:\WINDOWS\System32\spoolsv.exe
StartupType          : Automatic
State                : Running
Status               :
PSComputerName       :
CimClassName         : MSFT_ServiceResource
```

L'output mostra le proprietà del valore correnti configurabili dalla risorsa **Service**.

```syntax
Service [String] #ResourceName
{
    Name = [string]
    [BuiltInAccount = [string]{ LocalService | LocalSystem | NetworkService }]
    [Credential = [PSCredential]]
    [Dependencies = [string[]]]
    [DependsOn = [string[]]]
    [Description = [string]]
    [DisplayName = [string]]
    [Ensure = [string]{ Absent | Present }]
    [Path = [string]]
    [PsDscRunAsCredential = [PSCredential]]
    [StartupType = [string]{ Automatic | Disabled | Manual }]
    [State = [string]{ Running | Stopped }]
}
```

## <a name="test"></a>Test

Il metodo **Test** di una risorsa determina se il nodo di destinazione è attualmente conforme con lo *stato desiderato* della risorsa. Il metodo **Test** restituisce `$True` o `$False` solo per indicare se il nodo è conforme.
Quando si richiama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration) la gestione configurazione locale (LCM) richiama il metodo **Test** di tutte le risorse nella configurazione attualmente applicata. Gestione configurazione locale (LCM) usa i valori di chiave archiviati come parametri nel file "MOF" per ogni istanza di risorsa corrispondente.

Se il risultato di qualsiasi **Test** di una singola risorsa è `$False`, `Test-DSCConfiguration` restituisce `$False` che indica che il nodo non è conforme. Se tutte i metodi **Test** della risorsa restituiscono `$True`, `Test-DSCConfiguration` restituisce `$True` per indicare che il nodo è conforme.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partire da PowerShell 5.0, è stato aggiunto il parametro `-Detailed`. Se si specifica `-Detailed`, `Test-DSCConfiguration` restituisce un oggetto che contiene le raccolte dei risultati relativi alle risorse conformi e non conformi.

```powershell
Test-DSCConfiguration -Detailed
```

```output
PSComputerName  ResourcesInDesiredState        ResourcesNotInDesiredState     InDesiredState
--------------  -----------------------        --------------------------     --------------
localhost       {[Service]Spooler}                                            True
```

Per altre informazioni, vedere [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration)

## <a name="set"></a>Imposta

Il metodo **Set** di una risorsa tenta di forzare il nodo affinché diventi conforme con lo *stato desiderato* della risorsa. Il metodo **Set** deve essere **idempotente**, che significa che **Set** potrebbe essere eseguito più volte e otterrà sempre lo stesso risultato senza errori.  Quando si esegue [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration) la gestione configurazione locale (LCM) passa da una risorsa all'altra nella configurazione attualmente applicata. La gestione configurazione locale recupera i valori di chiave per l'istanza corrente delle risorse dal file "MOF" e li usa come parametri per il metodo **Test**. Se il metodo **Test** restituisce `$True`, il nodo è conforme con la risorsa corrente e il metodo **Set** viene ignorato. Se **Test** restituisce `$False`, il nodo non è conforme.  La gestione configurazione locale (LCM) passa i valori di chiave dell'istanza della risorsa come parametri al metodo **Set** ripristinando la conformità del nodo.

Specificando i parametri `-Verbose` e `-Wait`, è possibile controllare lo stato di avanzamento del cmdlet `Start-DSCConfiguration`. In questo esempio, il nodo è già conforme. L'output `Verbose` indica che il metodo **Set** è stato ignorato.

```
PS> Start-DSCConfiguration -Verbose -Wait -UseExisting

VERBOSE: Perform operation 'Invoke CimMethod' with following parameters, ''methodName' =
ApplyConfiguration,'className' = MSFT_DSCLocalConfigurationManager,'namespaceName' =
root/Microsoft/Windows/DesiredStateConfiguration'.
VERBOSE: An LCM method call arrived from computer SERVER01 with user sid
S-1-5-21-124525095-708259637-1543119021-1282804.
VERBOSE: [SERVER01]:                            [] Starting consistency engine.
VERBOSE: [SERVER01]:                            [] Checking consistency for current configuration.
VERBOSE: [SERVER01]:                            [DSCEngine] Importing the module
C:\WINDOWS\system32\WindowsPowerShell\v1.0\Modules\PSDesiredStateConfiguration\DscResources\MSFT_ServiceResource\MSFT
_ServiceResource.psm1 in force mode.
VERBOSE: [SERVER01]: LCM:  [ Start  Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ Start  Test     ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [[Service]Spooler] Importing the module MSFT_ServiceResource in
force mode.
VERBOSE: [SERVER01]: LCM:  [ End    Test     ]  [[Service]Spooler]  in 0.2540 seconds.
VERBOSE: [SERVER01]: LCM:  [ Skip   Set      ]  [[Service]Spooler]
VERBOSE: [SERVER01]: LCM:  [ End    Resource ]  [[Service]Spooler]
VERBOSE: [SERVER01]:                            [] Consistency check completed.
VERBOSE: Operation 'Invoke CimMethod' complete.
VERBOSE: Time taken for configuration job to complete is 1.379 seconds
```

## <a name="see-also"></a>Vedere anche

- [Panoramica della piattaforma DSC di Automazione di Azure](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Configurazione di un server di pull SMB](../pull-server/pullServerSMB.md)
- [Configurazione di un client di pull](../pull-server/pullClientConfigID.md)
