---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxGroup DSC per Linux
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953208"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>Risorsa nxGroup DSC per Linux

La risorsa **nxGroup** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i gruppi locali in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|GroupName |Indica il nome del gruppo per cui si vuole specificare un determinato stato. |
|Members |Specifica i membri che formano il gruppo. |
|MembersToInclude |Indica gli utenti da specificare come membri del gruppo. |
|MembersToExclude |Indica gli utenti da specificare come non membri del gruppo. |
|PreferredGroupID |Imposta l'ID gruppo sul valore specificato, se possibile. Se l'ID gruppo è attualmente in uso, viene usato il successivo ID gruppo disponibile. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se verificare l'esistenza del gruppo. Impostare questa proprietà su **Present** per assicurarsi che il gruppo esista. Impostarla su **Absent** per assicurarsi che il gruppo non esista. Il valore predefinito è **Present**. |

## <a name="example"></a>Esempio

L'esempio seguente specifica che l'utente 'monuser' esiste ed è un membro del gruppo 'DBusers'.

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```