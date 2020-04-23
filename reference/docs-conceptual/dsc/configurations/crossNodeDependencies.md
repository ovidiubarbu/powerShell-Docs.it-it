---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: 62e553d894897ae1908745c2788b7b7b9cbe50ff
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954108"
---
# <a name="specifying-cross-node-dependencies"></a>Specifica delle dipendenze tra nodi

> Si applica a: Windows PowerShell 5.0

DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi. Il comportamento di queste risorse è il seguente:

- **WaitForAll**: ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.
- **WaitForAny**: ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nella proprietà **NodeName**.
- **WaitForSome**: specifica una proprietà **NodeCount** oltre alla proprietà **NodeName**. La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.

## <a name="syntax"></a>Sintassi

Le risorse **WaitForAll** e **WaitForAny** condividono la stessa sintassi. Sostituire \<ResourceType\> nell'esempio seguente con **WaitForAny** oppure **WaitForAll**.
Come per la parola chiave **DependsOn**, sarà necessario formattare il nome come "[ResourceType]ResourceName". Se la risorsa appartiene a un oggetto [Configuration](configurations.md) separato, includere **ConfigurationName** nella stringa formattata "[ResourceType]ResourceName::[ConfigurationName]::[ConfigurationName]". **NodeName** è il computer o il nodo su cui deve restare in attesa la risorsa corrente.

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

La risorsa **WaitForSome** ha una sintassi simile all'esempio precedente, ma aggiunge la chiave **NodeCount**. **NodeCount** indica il numero di nodi su cui deve restare in attesa la risorsa corrente.

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

Tutte le risorse **WaitForXXXX** condividono le chiavi di sintassi seguenti.

|Proprietà|  Descrizione   |
|---------|---------------------|
| RetryIntervalSec| Il numero di secondi prima di riprovare. Il valore minimo è 1.|
| RetryCount| Il numero massimo di tentativi.|
| ThrottleLimit| Numero di computer da connettere contemporaneamente. Il valore predefinito è `New-CimSession`.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Per altre informazioni, vedere [DependsOn](resource-depends-on.md)|
| PsDscRunAsCredential | Vedere [Esecuzione di DSC con le credenziali dell'utente](./runAsUser.md) |

## <a name="using-waitforxxxx-resources"></a>Uso delle risorse WaitForXXXX

Ogni risorsa **WaitForXXXX** attende il completamento delle risorse specificate sul nodo specificato.
Altre risorse nella stessa configurazione possono quindi *dipendere* dalla risorsa **WaitForXXXX** tramite la chiave **DependsOn**.

Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.

Per impostazione predefinita, le risorse **WaitForXXX** eseguono un solo tentativo prima dell'esito negativo. Sebbene non sia obbligatorio, è consigliabile specificare **RetryCount** e **RetryIntervalSec**.

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

Quando si compila la configurazione vengono generati due file "MOF". Applicare entrambi i file "MOF" ai nodi di destinazione usando il cmdlet [Start-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration)

> [!NOTE]
> Le risorse **WaitForXXX** usano Gestione remota Windows per controllare lo stato degli altri nodi.
> Per altre informazioni sulla porta e sui requisiti di sicurezza per Gestione remota Windows, vedere [Considerazioni sulla sicurezza della comunicazione remota di PowerShell](/powershell/scripting/learn/remoting/winrmsecurity?view=powershell-6).

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Usare le dipendenze delle risorse](resource-depends-on.md)
- [Risorse DSC](../resources/resources.md)
- [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)
