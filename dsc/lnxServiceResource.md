---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxService DSC per Linux
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267780"
---
# <a name="dsc-for-linux-nxservice-resource"></a>Risorsa nxService DSC per Linux

La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Proprietà

| Proprietà | Description |
|---|---|
| Nome| Nome del servizio/daemon da configurare.|
| Controller| Tipo di controller del servizio da usare per la configurazione del servizio.|
| Enabled| Indica se il servizio viene avviato all'avvio del sistema.|
| State| Indica se il servizio è in esecuzione. Impostare questa proprietà su "Stopped" per specificare che il servizio non è in esecuzione. Impostare la proprietà su "Running" per specificare che il servizio è in esecuzione.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informazioni aggiuntive

La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste. È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.

## <a name="example"></a>Esempio

L'esempio seguente mostra la configurazione del servizio 'httpd' (per Apache HTTP Server), registrato con il controller del servizio **SystemD**.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```