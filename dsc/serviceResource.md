---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Service DSC
ms.openlocfilehash: 3e2db8999ab1db2964f88e1ee14c6ad6e641c5e3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222435"
---
# <a name="dsc-service-resource"></a>Risorsa Service DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0


La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica il nome del servizio. A volte questo nome è diverso da quello visualizzato. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet Get-Service.|
| BuiltInAccount| Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**.|
| Credential| Indica le credenziali per l'account in cui verrà eseguito il servizio. Questa proprietà e la proprietà __BuiltinAccount__ non possono essere usate insieme.|
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Indica il tipo di avvio per il servizio. I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**|
| State| Indica lo stato che si vuole specificare per il servizio.|
| Description | Specifica la descrizione del servizio di destinazione.|
| DisplayName | Indica il nome visualizzato del servizio di destinazione.|
| Ensure | Indica se il servizio di destinazione è presente nel sistema. Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste. Se la proprietà è impostata su **Present** (valore predefinito), specifica che il servizio di destinazione esiste.|
| Path | Indica il percorso del file binario per un nuovo servizio.|

## <a name="example"></a>Esempio

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```