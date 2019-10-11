---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa User DSC
ms.openlocfilehash: dec432c2ff1b4e4408165fef391e77cbf1d85ac4
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953008"
---
# <a name="dsc-user-resource"></a>Risorsa User DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **User** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire gli account utente locali nel nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
User [string] #ResourceName
{
    UserName = [string]
    [ Description = [string] ]
    [ Disabled = [bool] ]
    [ FullName = [string] ]
    [ Password = [PSCredential] ]
    [ PasswordChangeNotAllowed = [bool] ]
    [ PasswordChangeRequired = [bool] ]
    [ PasswordNeverExpires = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|UserName |Indica il nome dell'account per cui si vuole specificare un determinato stato. |
|Description |Indica la descrizione che si vuole usare per l'account utente. |
|Disabled |Indica se l'account è abilitato. Impostare questa proprietà su `$true` per assicurarsi che l'account sia disabilitato e su `$false` per assicurarsi che sia abilitato. |
|FullName |Rappresenta una stringa che contiene il nome completo da usare per l'account utente. |
|Password |Indica la password da usare per l'account. |
|PasswordChangeNotAllowed |Indica se l'utente può modificare la password. Impostare questa proprietà su `$true` per assicurarsi che l'utente non possa modificare la password e su `$false` per consentire all'utente di modificare la password. Il valore predefinito è `$false`. |
|PasswordChangeRequired |Indica se l'utente dovrà cambiare la password all'accesso successivo. Impostare questa proprietà su `$true` se l'utente deve cambiare la password. Il valore predefinito è `$true`. |
|PasswordNeverExpires |Indica se la password scadrà. Per assicurarsi che la password per questo account non scada mai, impostare questa proprietà su `$true`. Impostarla su `$false` se la password scadrà. Il valore predefinito è `$false`. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se l'account esiste. Impostare questa proprietà su **Present** per assicurarsi che l'account esista e su **Absent** per specificare che non esiste. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

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