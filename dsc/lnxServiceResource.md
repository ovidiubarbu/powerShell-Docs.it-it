---
title: Risorsa nxService DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 3835495705297616a41329bcfdaad42b464115d8

---

# Risorsa nxService DSC per Linux

La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.

## Sintassi

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | system }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## Proprietà
|  Proprietà |  Descrizione | 
|---|---|
| Name| Nome del servizio/daemon da configurare.| 
| Controller| Tipo di controller del servizio da usare per la configurazione del servizio.| 
| Enabled| Indica se il servizio viene avviato all'avvio del sistema.| 
| State| Indica se il servizio è in esecuzione. Impostare questa proprietà su "Stopped" per specificare che il servizio non è in esecuzione. Impostare la proprietà su "Running" per specificare che il servizio è in esecuzione.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 


## Informazioni aggiuntive

La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste. È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.

## Esempio

L'esempio seguente mostra la configurazione del servizio "httpd" (per Apache HTTP Server), registrato con il controller del servizio **SystemD**.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```




<!--HONumber=Aug16_HO3-->


