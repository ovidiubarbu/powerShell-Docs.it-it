---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Service DSC
ms.openlocfilehash: 0bef6aa6d3526c9d8d92187c1e738d5c46b5665a
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953048"
---
# <a name="dsc-service-resource"></a>Risorsa Service DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Service** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione.

## <a name="syntax"></a>Sintassi

```Syntax
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Path = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Indica il nome del servizio. A volte questo nome è diverso da quello visualizzato. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet `Get-Service`. |
|BuiltInAccount |Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**. |
|Credential |Indica le credenziali per l'account in cui verrà eseguito il servizio. Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme. |
|StartupType |Indica il tipo di avvio per il servizio. I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**. |
|State |Indica lo stato che si vuole specificare per il servizio. I valori sono: **Running** o **Stopped**. |
|Description |Specifica la descrizione del servizio di destinazione. |
|DisplayName |Indica il nome visualizzato del servizio di destinazione. |
|Path |Indica il percorso del file binario per un nuovo servizio. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se il servizio di destinazione è presente nel sistema. Impostare questa proprietà su **Absent** per specificare che il servizio di destinazione non esiste. Impostando il valore su **Present** ci si assicura che il servizio di destinazione esista. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

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