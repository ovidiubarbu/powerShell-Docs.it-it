---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Specifica delle dipendenze tra nodi
ms.openlocfilehash: c1802d6baa1f2b3449603e0374a83e213abf598e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218621"
---
# <a name="specifying-cross-node-dependencies"></a>Specifica delle dipendenze tra nodi

> Si applica a: Windows PowerShell 5.0

DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi. Il comportamento di queste risorse è il seguente:

* **WaitForAll**: ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.
* **WaitForAny**: ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nella proprietà **NodeName**.
* **WaitForSome**: specifica una proprietà **NodeCount** oltre alla proprietà **NodeName**. La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**.

## <a name="using-waitforxxxx-resources"></a>Uso delle risorse WaitForXXXX

Per usare le risorse **WaitForXXXX**, creare un blocco di risorsa contenente il tipo di risorsa che specifica la risorsa DSC e i nodi da attendere. Quindi usare la proprietà **DependsOn** su eventuali altri blocchi di risorse nella configurazione per attendere che le condizioni specificate nel nodo **WaitForXXXX** abbiano esito positivo.

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

>**Nota**: per impostazione predefinita, le risorse WaitForXXX eseguono un solo tentativo prima dell'esito negativo. Sebbene non sia obbligatorio, è consigliabile specificare un intervallo per i tentativi e il loro numero.

## <a name="see-also"></a>Vedere anche
* [Configurazioni DSC](configurations.md)
* [Risorse DSC](resources.md)
* [Configurazione di Gestione configurazione locale](metaConfig.md)