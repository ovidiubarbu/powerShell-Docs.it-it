---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: 04543351df19160a2da05ccea96e5d392d8c55bf
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37892526"
---
# <a name="dsc-user-resource"></a>Risorsa User DSC

Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **User** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| UserName| Indica il nome dell'account per cui si vuole specificare un determinato stato.|
| Description| Indica la descrizione che si vuole usare per l'account utente.|
| Disabled| Indica se l'account è abilitato. Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato.|
| Ensure| Indica se l'account esiste. Impostare questa proprietà su "Present" per specificare che l'account esiste e su "Absent" per specificare che non esiste.|
| FullName| Rappresenta una stringa che contiene il nome completo da usare per l'account utente.|
| Password| Indica la password da usare per l'account. |
| PasswordChangeNotAllowed| Indica se l'utente può modificare la password. Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password. Il valore predefinito è `$false`.|
| PasswordChangeRequired| Indica se l'utente dovrà cambiare la password all'accesso successivo. Impostare questa proprietà su `$true` se l'utente deve cambiare la password. Il valore predefinito è `$true`.|
| PasswordNeverExpires| Indica se la password scadrà. Impostare questa proprietà su `$true` per assicurarsi che la password per questo utente non scada mai e su `$false` se la password scade. Il valore predefinito è `$false`.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Esempio

```powershell
User UserExample
{
    Ensure = "Present"  # To ensure the user account does not exist, set Ensure to "Absent"
    UserName = "SomeName"
    Password = $passwordCred # This needs to be a credential object
    DependsOn = "[Group]GroupExample" # Configures GroupExample first
}
```