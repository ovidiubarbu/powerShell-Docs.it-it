---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxPackage DSC per Linux
ms.openlocfilehash: 4091cbbd5e34a84b9011870da4bda93281378347
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954818"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>Risorsa nxPackage DSC per Linux

La risorsa **nxPackage** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i pacchetti in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxPackage <string> #ResourceName
{
    Name = <string>
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ FilePath = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Nome del pacchetto per cui si vuole specificare un determinato stato. |
|PackageManager |I valori supportati sono **yum**, **apt** e **zypper**. Specifica lo strumento di gestione dei pacchetti da usare durante l'installazione dei pacchetti. Se si specifica **FilePath**, verrà usato il percorso fornito per installare il pacchetto. In caso contrario, verrà usato uno strumento di gestione dei pacchetti per installare il pacchetto da un repository preconfigurato. Se non si specifica né **PackageManager** né **FilePath**, viene usato il sistema di gestione dei pacchetti predefinito per il sistema. |
|PackageGroup |Se `$true`, **Name** sarà il nome di un gruppo di pacchetti da usare con **PackageManager**. **PackageGroup** non è un valore valido quando si specifica **FilePath**. |
|Arguments |Stringa di argomenti che verrà passata al pacchetto esattamente nel modo specificato. |
|ReturnCode |Codice restituito previsto. Se l'effettivo codice restituito non corrisponde al valore previsto specificato qui, la configurazione restituirà un errore. |
|FilePath |Percorso in cui si trova il pacchetto. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se verificare l'esistenza del pacchetto. Impostare questa proprietà su **Present** per assicurarsi che il pacchetto esista. Impostarla su **Absent** per assicurarsi che il pacchetto non esista. Il valore predefinito è **Present**. |

## <a name="example"></a>Esempio

L'esempio seguente specifica che il pacchetto denominato "httpd" è installato in un computer Linux, usando lo strumento di gestione dei pacchetti "Yum".

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxPackage httpd
    {
        Name = "httpd"
        Ensure = "Present"
        PackageManager = "Yum"
    }
}
```