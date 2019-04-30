---
ms.date: 12/12/2018
keywords: dsc,powershell,risorsa,raccolta,configurazione
title: Aggiungere parametri a una configurazione
ms.openlocfilehash: 15213404f0cdd6416baf1f83af91b8f5279cc97f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080257"
---
# <a name="add-parameters-to-a-configuration"></a>Aggiungere parametri a una configurazione

Così come le Funzioni, le [Configurazioni](configurations.md) possono essere parametrizzate per consentire configurazioni più dinamiche basate sull'input dell'utente. I passaggi sono simili a quelli descritti nelle [funzioni con parametri](/powershell/module/microsoft.powershell.core/about/about_functions).

Questo esempio inizia con una configurazione di base che configura il servizio "Spooler" in "Esecuzione".

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

Diversamente da una funzione, tuttavia, l'attributo [CmdletBinding](/powershell/module/microsoft.powershell.core/about/about_functions_cmdletbindingattribute) non aggiunge alcuna funzionalità. Oltre ai [parametri comuni](/powershell/module/microsoft.powershell.core/about/about_commonparameters), le configurazioni possono anche usare i seguenti parametri predefiniti, senza che sia necessario definirli.

|Parametro  |Description  |
|---------|---------|
|`-InstanceName`|Usato nella definizione delle [configurazioni composite](compositeconfigs.md)|
|`-DependsOn`|Usato nella definizione delle [configurazioni composite](compositeconfigs.md)|
|`-PSDSCRunAsCredential`|Usato nella definizione delle [configurazioni composite](compositeconfigs.md)|
|`-ConfigurationData`|Usato per passare i [ dati di configurazione](configData.md) strutturati per l'uso nella configurazione.|
|`-OutputPath`|Usato per specificare dove verrà compilato il file "\<computername\>.mof"|

## <a name="adding-your-own-parameters-to-configurations"></a>Aggiungere parametri definiti dall'utente alle configurazioni

Oltre ai parametri predefiniti, è anche possibile aggiungere alle configurazioni parametri definiti dall'utente. Il blocco dei parametri viene indirizzato direttamente alla dichiarazione di configurazione, proprio come una funzione. Un blocco di parametri di configurazione deve trovarsi all'esterno delle dichiarazioni di **nodo** e al di sopra delle istruzioni di *importazione*. Aggiungendo i parametri, è possibile rendere le configurazioni maggiormente solide e dinamiche.

```powershell
Configuration TestConfig
{
    param
    (

    )
```

### <a name="add-a-computername-parameter"></a>Aggiungere un parametro ComputerName

Il primo parametro che è possibile aggiungere è un parametro `-Computername` per compilare dinamicamente un file "MOF" per qualsiasi parametro `-Computername` passato alla configurazione. Come per le funzioni, è anche possibile definire un valore predefinito, nel caso in cui l'utente non passi un valore per `-ComputerName`

```powershell
param
(
    [String]
    $ComputerName="localhost"
)
```

All'interno della configurazione, è quindi possibile specificare il parametro `-ComputerName` quando si definisce il blocco Node.

```powershell
Node $ComputerName
{

}
```

### <a name="calling-your-configuration-with-parameters"></a>Chiamare la configurazione con i parametri

Dopo aver aggiunto i parametri alla configurazione, è possibile usarli così come si farebbe con un cmdlet.

```powershell
TestConfig -ComputerName "server01"
```

### <a name="compiling-multiple-mof-files"></a>Compilazione di più file MOF

Il blocco Node può anche accettare un elenco delimitato da virgole di nomi computer e genererà file "MOF" per ciascuno di essi. È possibile eseguire l'esempio seguente per generare i file "MOF" per tutti i computer passati al parametro `-ComputerName`.

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

Oltre a un parametro `-ComputerName`, è possibile aggiungere parametri per il nome e lo stato del servizio. L'esempio seguente aggiunge un blocco di parametri con un parametro `-ServiceName` e lo usa per definire in modo dinamico il blocco di risorse **Service**. Aggiunge anche un parametro `-State` per definire in modo dinamico **State** nel blocco di risorse **Service**.

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
> In scenari più avanzati, potrebbe essere più utile spostare i dati dinamici in [dati di configurazione](configData.md) strutturati.

La configurazione di esempio usa qui un valore dinamico `$ServiceName`, ma se non ne è specificato uno la compilazione genera un errore. È possibile aggiungere un valore predefinito simile a questo esempio.

```powershell
[String]
$ServiceName="Spooler"
```

In questa istanza, tuttavia, è più opportuno forzare semplicemente l'utente a specificare un valore per il parametro `$ServiceName`. L'attributo `parameter` consente di aggiungere ulteriore supporto di convalida e pipeline ai parametri di configurazione.

Di sopra di qualsiasi dichiarazione di parametro, aggiungere il blocco di attributi `parameter` come nell'esempio seguente.

```powershell
[parameter()]
[String]
$ServiceName
```

È possibile specificare argomenti per ogni attributo `parameter` per controllare gli aspetti del parametro definito. L'esempio seguente rende `$ServiceName` un parametro **obbligatorio**.

```powershell
[parameter(Mandatory)]
[String]
$ServiceName
```

Per il parametro `$State`, sarebbe opportuno impedire all'utente di specificare valori di fuori di un set predefinito (come Running, Stopped). L'attributo `ValidationSet*`impedisce all'utente di specificare valori di fuori di un set predefinito (come Running, Stopped). L'esempio seguente aggiunge l'attributo `ValidationSet` al parametro `$State`. Poiché non si desidera rendere il parametro `$State` **obbligatorio**, è necessario aggiungere per esso un valore predefinito.

```powershell
[ValidateSet("Running", "Stopped")]
[String]
$State="Running"
```

> [!NOTE]
> Non è necessario specificare un attributo `parameter` quando si usa un attributo `validation`.

Sono disponibili altre informazioni su `parameter` e sugli attributi di convalida nelle [informazioni sui parametri delle funzioni avanzate](/powershell/module/microsoft.powershell.core/about/about_Functions_Advanced_Parameters.md).

## <a name="fully-parameterized-configuration"></a>Configurazione completa con parametri

È ora disponibile una configurazione con parametri che forza l'utente a specificare `-InstanceName`, `-ServiceName` e che convalida il parametro `-State`.

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
- [Istruzioni condizionali e cicli nelle configurazioni](flow-control-in-configurations.md)
- [Uso dei dati di configurazione in DSC](configData.md)
- [Separazione dei dati di configurazione e dell'ambiente](separatingEnvData.md)
