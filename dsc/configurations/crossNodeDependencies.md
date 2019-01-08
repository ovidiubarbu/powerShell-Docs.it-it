---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: 1bdfbd9f8a94809d6bf410eff525e1c877fb6aad
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401164"
---
# <a name="specifying-cross-node-dependencies"></a>Specifica delle dipendenze tra nodi

> Si applica a: Windows PowerShell 5.0

DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi. Il comportamento di queste risorse è il seguente:

- **WaitForAll**: Ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definito nel **NodeName** proprietà.
- **WaitForAny**: Ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nel **NodeName** proprietà.
- **WaitForSome**: Specifica un **NodeCount** oltre alla proprietà un **NodeName** proprietà. La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.

## <a name="syntax"></a>Sintassi

Il **WaitForAll** e **WaitForAny** risorse che condividono la stessa sintassi. Sostituire \<ResourceType\> nell'esempio seguente con uno **WaitForAny** oppure **WaitForAll**.
Ad esempio la **DependsOn** (parola chiave), è necessario formattare il nome come "[ResourceType] ResourceName". Se la risorsa appartiene a un oggetto separato [Configuration](configurations.md), includono il **ConfigurationName** nella stringa di formato "[ResourceType] ResourceName:: [ConfigurationName]:: [ConfigurationName]". Il **NodeName** è il computer o un nodo, in cui deve attendere la risorsa corrente.

```
<ResourceType> [string] #ResourceName
{
    ResourceName = [string]
    NodeName = [string]
    [ DependsOn = [string[]] ]
    [ PsDscRunAsCredential = [PSCredential]]
    [ RetryCount = [Uint32] ]
    [ RetryIntervalSec = [Uint64] ]
    [ ThrottleLimit = [Uint32]]
}
```

Il **WaitForSome** risorsa presenta una sintassi simile all'esempio precedente, ma aggiunge le **NodeCount** chiave. Il **NodeCount** indica il numero di nodi dovrebbe attendere la risorsa corrente.

```
WaitForSome [String] #ResourceName
{
    NodeCount = [UInt32]
    NodeName = [string[]]
    ResourceName = [string]
    [DependsOn = [string[]]]
    [PsDscRunAsCredential = [PSCredential]]
    [RetryCount = [UInt32]]
    [RetryIntervalSec = [UInt64]]
    [ThrottleLimit = [UInt32]]
}
```

Tutti i **WaitForXXXX** condividere le chiavi di sintassi seguenti.

|  Proprietà |  Descrizione | | RetryIntervalSec | Il numero di secondi prima di riprovare. Valore minimo è 1. | | RetryCount | Il numero massimo di tentativi. | | ThrottleLimit | Numero di computer da connettere contemporaneamente. Il valore predefinito è `New-CimSession` predefinito. | | DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Per altre informazioni, vedere [DependsOn](resource-depends-on.md)| | PsDscRunAsCredential | Vedere [uso di DSC con le credenziali dell'utente](./runAsUser.md) |


## <a name="using-waitforxxxx-resources"></a>Uso delle risorse WaitForXXXX

Ciascuna **WaitForXXXX** attese risorse per le risorse specificate per il completamento nel nodo specificato. Altre risorse nella stessa configurazione possono quindi *dipendono* le **WaitForXXXX** risorse usando il **DependsOn** chiave.

Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.

```powershell
Configuration JoinDomain
{
    Import-DscResource -Module xComputerManagement, xActiveDirectory

    Node myDC
    {
        WindowsFeature InstallAD
        {
            Ensure = 'Present'
            Name = 'AD-Domain-Services'
        }

        xADDomain NewDomain
        {
            DomainName = 'Contoso.com'
            DomainAdministratorCredential = (Get-Credential)
            SafemodeAdministratorPassword = (Get-Credential)
            DatabasePath = "C:\Windows\NTDS"
            LogPath = "C:\Windows\NTDS"
            SysvolPath = "C:\Windows\Sysvol"
        }
    }

    Node myDomainJoinedServer
    {
        WaitForAll DC
        {
            ResourceName      = '[xADDomain]NewDomain'
            NodeName          = 'MyDC'
            RetryIntervalSec  = 15
            RetryCount        = 30
        }

        xComputer JoinDomain
        {
            Name             = 'myPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

Quando si compila la configurazione, vengono generati due file di "MOF". Applicare entrambi i file "MOF" ai nodi di destinazione usando il [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet

>**Nota:** Per impostazione predefinita il WaitForXXX risorse prova una sola volta e quindi esito negativo. Sebbene non sia obbligatorio, si sarà in genere consigliabile specificare una **RetryCount** e **RetryIntervalSec**.

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Usare le dipendenze delle risorse](resource-depends-on.md)
- [Risorse DSC](../resources/resources.md)
- [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)
