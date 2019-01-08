---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxPackage DSC per Linux
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047600"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>Risorsa nxPackage DSC per Linux

La risorsa **nxPackage** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i pacchetti in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà |  Description |
|---|---|
| Nome| Nome del pacchetto per cui si vuole specificare un determinato stato.|
| Ensure| Determina se verificare l'esistenza del pacchetto. Impostare questa proprietà su "Present" per specificare che il pacchetto esiste. Impostarla su "Absent" per specificare che il pacchetto non esiste. Il valore predefinito è "Present".|
| PackageManager| I valori supportati sono "yum", "apt" e "zypper". Specifica lo strumento di gestione dei pacchetti da usare durante l'installazione dei pacchetti. Se si specifica **FilePath**, verrà usato il percorso fornito per installare il pacchetto. In caso contrario, verrà usato uno strumento di gestione dei pacchetti per installare il pacchetto da un repository preconfigurato. Se non si specifica né **PackageManager** né **FilePath**, viene usato il sistema di gestione dei pacchetti predefinito per il sistema.|
| FilePath| Percorso in cui si trova il pacchetto|
| PackageGroup| Se **$true**, **Name** sarà il nome di un gruppo di pacchetti da usare con **PackageManager**. **PacakgeGroup** non è un valore valido quando si specifica **FilePath**.|
| Arguments| Stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato.|
| ReturnCode| Codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Esempio

L'esempio seguente specifica che il pacchetto denominato "httpd" è installato in un computer Linux, usando lo strumento di gestione dei pacchetti "Yum".

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```