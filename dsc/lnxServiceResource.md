---
title: Risorsa nxService DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 8443860628617eb56ce370be62f9618f19f78077
ms.sourcegitcommit: 26f4e52f3dd008b51b7eae7b634f0216eec6200e
translationtype: HT
---
# <a name="dsc-for-linux-nxservice-resource"></a>Risorsa nxService DSC per Linux

La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Proprietà
|  Proprietà |  Descrizione | 
|---|---|
| Name| Nome del servizio/daemon da configurare.| 
| Controller| Tipo di controller del servizio da usare per la configurazione del servizio.| 
| Enabled| Indica se il servizio viene avviato all'avvio del sistema.| 
| State| Indica se il servizio è in esecuzione. Impostare questa proprietà su "Stopped" per specificare che il servizio non è in esecuzione. Impostare la proprietà su "Running" per specificare che il servizio è in esecuzione.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Informazioni aggiuntive

La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste. È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.

## <a name="example"></a>Esempio

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

