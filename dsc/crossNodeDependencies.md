---
title: Specifica delle dipendenze tra nodi
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 04aa6292dee991060669e1ac770cf98cbba41bfc
ms.openlocfilehash: f4c64d3603fd01f29a63f8b180057714bf3d1197

---

# Specifica delle dipendenze tra nodi

> Si applica a: Windows PowerShell 5.0

DSC fornisce risorse speciali quali **WaitForAll**, **WaitForAny** e **WaitForSome** che possono essere usate nelle configurazioni per specificare le dipendenze nelle configurazioni di altri nodi. Il comportamento di queste risorse è il seguente:

* **WaitForAll**: ha esito positivo se la risorsa specificata è nello stato desiderato in tutti i nodi di destinazione definiti nella proprietà **NodeName**.
* **WaitForAny**: ha esito positivo se la risorsa specificata è nello stato desiderato in almeno uno dei nodi di destinazione definiti nella proprietà **NodeName**.
* **WaitForSome**: specifica una proprietà **NodeCount** oltre alla proprietà **NodeName**. La risorsa ha esito positivo se si trova nello stato desiderato in un numero minimo di nodi, specificato in **NodeCount**, definito dalla proprietà **NodeName**. 

## Uso delle risorse WaitForXXXX

Per usare le risorse **WaitForXXXX**, creare un blocco di risorsa contenente il tipo di risorsa che specifica la risorsa DSC e i nodi da attendere. Quindi usare la proprietà **DependsOn** su eventuali altri blocchi di risorse nella configurazione per attendere che le condizioni specificate nel nodo **WaitForXXXX** abbiano esito positivo.

Nella configurazione seguente, ad esempio, il nodo di destinazione è in attesa del completamento della risorsa **xADDomain** nel nodo **MyDC** con un numero massimo di 30 tentativi, a intervalli di 15 secondi, prima che il nodo di destinazione possa essere aggiunto al dominio.

```PowerShell
Configuration JoinDomain

{
    Import-DscResource -Module xComputerManagement

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
            Name             = 'MyPC'
            DomainName       = 'Contoso.com'
            Credential       = (Get-Credential)
            DependsOn        ='[WaitForAll]DC'
        }
    }
}
```

>**Nota**: per impostazione predefinita, le risorse WaitForXXX eseguono un solo tentativo prima dell'esito negativo. Sebbene non sia obbligatorio, è consigliabile specificare un intervallo per i tentativi e il loro numero.

## Vedere anche
* [Configurazioni DSC](configurations.md)
* [Risorse DSC](resources.md)
* [Configurazione di Gestione configurazione locale](metaConfig.md)




<!--HONumber=Jun16_HO4-->


