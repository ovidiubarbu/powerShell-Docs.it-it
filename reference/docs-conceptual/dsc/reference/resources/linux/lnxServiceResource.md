---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxService DSC per Linux
ms.openlocfilehash: 6bb58796c4deff1153f932f61c328d84f8c4d2ca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954838"
---
# <a name="dsc-for-linux-nxservice-resource"></a>Risorsa nxService DSC per Linux

La risorsa **nxService** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
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

|Proprietà |Description |
|---|---|
|Nome |Nome del servizio/daemon da configurare. |
|Controller |Tipo di controller del servizio da usare per la configurazione del servizio. |
|Enabled |Indica se il servizio viene avviato all'avvio del sistema. |
|State |Indica se il servizio è in esecuzione. Impostare questa proprietà su **Stopped** per assicurarsi che il servizio non sia in esecuzione. Impostare la proprietà su **Running** per assicurarsi che il servizio sia in esecuzione. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |

## <a name="additional-information"></a>Informazioni aggiuntive

La risorsa **nxService** non crea uno script o una definizione del servizio se il servizio non esiste. È possibile usare la risorsa **nxFile** di PowerShell DSC (Desired State Configuration) per gestire l'esistenza o il contenuto dello script o del file di definizione del servizio.

## <a name="example"></a>Esempio

L'esempio seguente mostra la configurazione del servizio 'httpd' (per Apache HTTP Server), registrato con il controller del servizio **SystemD**.

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```