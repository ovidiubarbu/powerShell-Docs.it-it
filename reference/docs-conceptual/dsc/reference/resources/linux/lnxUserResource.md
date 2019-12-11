---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxUser DSC per Linux
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954798"
---
# <a name="dsc-for-linux-nxuser-resource"></a>Risorsa nxUser DSC per Linux

La risorsa **nxUser** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli utenti locali in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Indica il nome dell'account per cui si vuole specificare un determinato stato. |
|---|---|
|UserName |Indica il percorso in cui si vuole specificare lo stato di un file o una directory. |
|FullName |Stringa che contiene il nome completo da usare per l'account utente. |
|Description |Descrizione dell'account utente. |
|Password |Hash della password dell'utente nel formato appropriato per il computer Linux. In genere, è un hash salt SHA-256 o SHA-512. In Debian e Ubuntu Linux, questo valore può essere generato con il comando `mkpasswd`. Per altre distribuzioni Linux, è possibile usare il metodo di crittografia della libreria Crypt di Python per generare l'hash. |
|Disabilitata |Indica se l'account è abilitato. Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato. |
|PasswordChangeRequired |Indica se l'utente può modificare la password. Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password. Il valore predefinito è `$false`. Questa proprietà viene valutata solo se l'account utente non esisteva in precedenza e viene creato ora. |
|HomeDirectory |Home directory per l'utente. |
|GroupID |ID gruppo primario per l'utente. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Specifica se l'account esiste. Impostare questa proprietà su **Present** per assicurarsi che l'account esista e su **Absent** per specificare che non esiste. |

## <a name="example"></a>Esempio

L'esempio seguente specifica che l'utente "monuser" esiste ed è un membro del gruppo "DBusers".

```powershell
Import-DSCResource -Module nx

Node $node
{
   nxUser UserExample{
      UserName = "monuser"
      Description = "Monitoring user"
      Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
      Ensure = "Present"
      HomeDirectory = "/home/monuser"
   }

   nxGroup GroupExample{
      GroupName = "DBusers"
      Ensure = "Present"
      MembersToInclude = "monuser"
      DependsOn = "[nxUser]UserExample"
   }
}
```