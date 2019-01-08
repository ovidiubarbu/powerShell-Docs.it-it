---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Get-Test-Set
ms.openlocfilehash: e46710954679bf20f4536c6efbcbd4dafd9e629e
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401446"
---
# <a name="get-test-set"></a>Get-Test-Set

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

![Ottenere, testare e impostare](/media/get-test-set.png)

PowerShell Desired State Configuration è costruito intorno a un **ottenere**, **Test**, e **impostare** processo. DSC [risorse](resources.md) ognuno contiene metodi per completare ciascuna di queste operazioni. In un [Configuration](../configurations/configurations.md), è definire blocchi risorsa per riempire le chiavi che diventano i parametri per una risorsa **ottenere**, **Test**, e **impostata** metodi.

Si tratta la sintassi per un **servizio** blocco di risorse. Il **servizio** risorse configura i servizi di Windows.

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

Il **ottenere**, **Test**, e **impostare** metodi del **servizio** risorse avranno blocchi dei parametri che accettano questi valori.

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
> Determina la lingua e il metodo utilizzato per definire la risorsa come la **ottenere**, **Test**, e **impostare** verranno definiti i metodi.

Poiché il **servizio** risorsa ha solo una chiave necessaria (`Name`), una **servizio** risorsa di blocco potrebbe essere semplice come questa:

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

Quando applicata, la [Gestione configurazione locale](../managing-nodes/metaConfig.md) leggerà il valore "Spooler" dal file "MOF" e passarlo al `-Name` parametri del **ottenere**, **Test**, e **impostata** metodi per l'istanza "MyService" delle **servizio** risorsa.

## <a name="get"></a>Get

Il **ottenere** metodo di una risorsa, recupera lo stato della risorsa perché è configurata nel nodo di destinazione. Questo stato viene restituito come un [hashtable](/powershell/module/microsoft.powershell.core/about/about_hash_tables). Le chiavi del **hashtable** saranno i valori configurabili, o parametri, accetta la risorsa.

Il **ottenere** metodo esegue il mapping direttamente alle [Get-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/get-dscconfiguration) cmdlet. Quando si chiama `Get-DSCConfiguration`, le esecuzioni di Gestione configurazione locale le **ottenere** (metodo) di ogni risorsa nella configurazione attualmente applicata. Gestione configurazione locale Usa i valori di chiave archiviati nel file "MOF" come parametri per ogni istanza di risorsa corrispondente.

Si tratta di output di esempio da un **servizio** risorse che consente di configurare il servizio "Spooler".

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

L'output mostra le proprietà del valore corrente può essere configurato per il **servizio** risorsa.

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

Il **Test** metodo di una risorsa determina se il nodo di destinazione è attualmente compatibile con la risorsa *stato desiderato*. Il **Test** metodo restituisce `$True` o `$False` solo per indicare se il nodo è conforme.
Quando si chiama [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration), le chiamate di Gestione configurazione locale le **Test** (metodo) di ogni risorsa nella configurazione attualmente applicata. Gestione configurazione locale Usa i valori di chiave archiviati nel file "MOF" come parametri per ogni istanza di risorsa corrispondente.

Se il risultato di qualsiasi risorsa singole **Test** viene `$False`, `Test-DSCConfiguration` restituisce `$False` che indica che il nodo non è conforme. Se tutte le risorse **Test** metodi restituiscono `$True`, `Test-DSCConfiguration` restituisce `$True` per indicare che il nodo è conforme.

```powershell
Test-DSCConfiguration
```

```output
True
```

A partire da PowerShell 5.0, il `-Detailed` è stato aggiunto il parametro. Che specifica `-Detailed` provoca `Test-DSCConfiguration` per restituire un oggetto che contiene le raccolte di risultati per le risorse conformi e non conformi.

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

Il **impostata** metodo di una risorsa tenta di forzare il nodo per diventare conformi con la risorsa *stato desiderato*. Il **impostata** metodo deve essere **idempotente**, che significa che **impostare** potrebbe essere eseguito più volte e otterrà sempre lo stesso risultato senza errori.  Quando si esegue [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Start-DSCConfiguration), i cicli di Gestione configurazione locale tramite ogni risorsa nella configurazione attualmente applicata. Gestione configurazione locale recupera i valori di chiave per l'istanza corrente di risorse dal file "MOF" e li usa come parametri per il **Test** (metodo). Se il **Test** metodo restituisce `$True`, il nodo è conforme con la risorsa corrente e il **impostare** metodo è stato ignorato. Se il **Test** restituisce `$False`, il nodo è non conforme.  Gestione configurazione locale passa la risorsa di valori di chiave dell'istanza come parametri per la risorsa **impostare** metodo, il ripristino del nodo per la conformità.

Specificando il `-Verbose` e `-Wait` i parametri, è possibile controllare lo stato di avanzamento del `Start-DSCConfiguration` cmdlet. In questo esempio, il nodo è già conforme. Il `Verbose` output indica che il **impostare** metodo è stato ignorato.

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

- [Panoramica della piattaforma DSC di Automazione di Azure](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Configurazione di un server di pull SMB](../pull-server/pullServerSMB.md)
- [Configurazione di un client di pull](../pull-server/pullClientConfigID.md)
