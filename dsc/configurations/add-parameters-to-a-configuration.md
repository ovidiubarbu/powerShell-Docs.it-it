---
ms.date: 12/12/2018
keywords: DSC, powershell, resource, raccolta, il programma di installazione
title: Aggiungere parametri a una configurazione
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401429"
---
# <a name="add-parameters-to-a-configuration"></a>Aggiungere parametri a una configurazione

Ad esempio le funzioni [configurazioni](configurations.md) può essere parametrizzata per consentire più dinamiche configurazioni basate sull'input dell'utente. I passaggi sono simili a quelle descritte nel [le funzioni con parametri](/powershell/module/microsoft.powershell.core/about/about_functions).

In questo esempio inizia con una configurazione di base che consente di configurare il servizio "Spooler" in "Esecuzione".

```powershell
Configuration TestConfig
{
    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}
```

## <a name="built-in-configuration-parameters"></a>Parametri di configurazione predefiniti

A differenza di una funzione, tuttavia, il [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) attributo non aggiunge alcuna funzionalità. Oltre a [parametri comuni](/powershell/module/microsoft.powershell.core/about/about_commonparameters), configurazioni anche possono usare quanto segue compilata nei parametri, senza che sia necessario definirli.

|Parametro  |Description  |
|---------|---------|
|`-InstanceName`|Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)|
|`-DependsOn`|Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Utilizzato nella definizione [configurazioni composito](compositeconfigs.md)|
|`-ConfigurationData`|Consente di passare in strutturato [i dati di configurazione](configData.md) per l'uso nella configurazione.|
|`-OutputPath`|Consente di specificare dove il "\<computername\>MOF" file verrà compilate|

## <a name="adding-your-own-parameters-to-configurations"></a>Aggiungere i propri parametri alle configurazioni

Oltre ai parametri predefiniti, è anche possibile aggiungere i propri parametri alle configurazioni. Il blocco dei parametri viene indirizzato direttamente all'interno della dichiarazione di configurazione, proprio come una funzione. Un blocco del parametro di configurazione deve essere di fuori di qualsiasi **nodo** dichiarazioni e versioni successive qualsiasi *importare* istruzioni. Quando si aggiungono parametri, è possibile apportare le configurazioni più affidabile e dinamica.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Aggiungere un parametro ComputerName

Il primo parametro è possibile aggiungere è un `-Computername` parametro affinché sia possibile compilare dinamicamente un file "con estensione MOF" per qualsiasi `-Computername` si passa alla propria configurazione. Ad esempio funzioni, è inoltre possibile definire un valore predefinito, nel caso in cui l'utente non supera un valore per `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

All'interno della configurazione, è quindi possibile specificare il `-ComputerName` parametro quando si definisce il blocco del nodo.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Chiamare la configurazione con parametri

Dopo aver aggiunto i parametri per la configurazione, è possibile usarli come si farebbe con un cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>La compilazione di più file con estensione MOF

Il blocco del nodo può anche accettare un elenco delimitato da virgole di nomi di computer e genererà file "MOF" per ciascuno. È possibile eseguire l'esempio seguente per generare i file "MOF" per tutti i computer passati al `-ComputerName` parametro.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service 'Spooler'
        {
            Name = 'Spooler'
            State = 'Running'
        }
    }
}

TestConfig -ComputerName "server01", "server02", "server03"
```

## <a name="advanced-parameters-in-configurations"></a>Parametri avanzati nelle configurazioni

Oltre a un `-ComputerName` parametro, è possibile aggiungere parametri per il nome del servizio e lo stato. L'esempio seguente aggiunge un blocco di parametri con un `-ServiceName` parametro e lo usa per definire in modo dinamico il **servizio** blocco di risorse. Aggiunge anche un `-State` parametro per definire in modo dinamico il **stato** nel **servizio** blocco di risorse.

```powershell
Configuration TestConfig
{
    param
    (
        [String]
        $ServiceName,

        [String]
        $State,

        [String]
        $ComputerName="localhost"
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node $ComputerName
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

> [!NOTE]
> In più scenari advacned, potrebbe essere più utile per spostare i dati dinamici in un structured [i dati di configurazione](configData.md).

Nell'esempio di configurazione ora accetta una dinamica `$ServiceName`, ma se non è specificato, la compilazione genera un errore. È possibile aggiungere valore predefinito è simile all'esempio.

```powershell
[String]
$ServiceName="Spooler"
```

In questo caso, tuttavia, è più opportuno forzare semplicemente all'utente di specificare un valore per il `$ServiceName` parametro. Il `parameter` attributo consente di aggiungere ulteriore convalida e la pipeline supportano ai parametri di configurazione.

Di sopra di qualsiasi dichiarazione di parametro, aggiungere il `parameter` blocco di attributi come nell'esempio seguente.

```powershell
[parameter()]
[String]
$ServiceName
```

È possibile specificare argomenti a ogni `parameter` attributo, per controllare gli aspetti del parametro definito. Nell'esempio seguente viene eseguita la `$ServiceName` una **obbligatorio** parametro.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Per il `$State` parametro, siamo lieti di impedire all'utente di specificare i valori di fuori di un set predefinito (come in esecuzione, arrestato) il `ValidationSet*`attributo impedirebbe l'utente che specifica i valori di fuori di un set predefinito (ad esempio, in esecuzione, Arrestato). L'esempio seguente aggiunge il `ValidationSet` dell'attributo di `$State` parametro. Poiché non vogliamo rendere la `$State` parametro **obbligatorio**, è necessario aggiungere un valore predefinito per tale.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Non è necessario specificare una `parameter` attributo quando si usa un `validation` attributo.

Altre informazioni, vedere la `parameter` e gli attributi di convalida nel [about_Functions_Advanced_Parameters](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configurazione completa con parametri

È ora disponibile una configurazione con parametri che impone all'utente di specificare una `-InstanceName`, `-ServiceName`e convalida il `-State` parametro.

```powershell
Configuration TestConfig
{
    param
    (
        [parameter(Mandatory)]
        [String]
        $ServiceName,

        [ValidateSet("Running","Stopped")]
        [String]
        $State="Running",

        [String]
        $ComputerName="localhost",
    )

    # It is best practice to implicitly import any required resources or modules.
    Import-DSCResource -Module PSDesiredStateConfiguration

    Node localhost
    {
        Service $ServiceName
        {
            Name = $ServiceName
            State = $State
        }
    }
}
```

## <a name="see-also"></a>Vedere anche

- [Scrivere informazioni della Guida per le configurazioni DSC](configHelp.md)
- [Configurazione dinamica](flow-control-in-configurations.md)
- [Usare i dati di configurazione nelle configurazioni](configData.md)
- [Dati di configurazione e dell'ambiente separato](separatingEnvData.md)
