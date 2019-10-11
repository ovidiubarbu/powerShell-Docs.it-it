---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ServiceSet DSC
ms.openlocfilehash: 97c25f46940d69ed6c696e2692e29131e9a997b0
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71953028"
---
# <a name="dsc-serviceset-resource"></a>Risorsa ServiceSet DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **ServiceSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione. Questa risorsa è una [risorsa composita](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Service](serviceResource.md) per ogni servizio specificato nella proprietà **Name**.

Usare questa risorsa quando si vogliono configurare diversi servizi nello stesso stato.

## <a name="syntax"></a>Sintassi

```Syntax
ServiceSet [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Description |
|---|---|
|Nome |Indica i nomi del servizio. A volte questo nome è diverso da quelli visualizzati. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet `Get-Service`. |
|StartupType |Indica il tipo di avvio per i servizi. I valori consentiti per questa proprietà sono: **Automatic**, **Disabled** e **Manual**. |
|BuiltInAccount |Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem** e **NetworkService**. |
|State |Indica lo stato che si vuole specificare per i servizi: **Stopped** o **Running**. |
|Credential |Indica le credenziali per l'account in cui verrà eseguita la risorsa del servizio. Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Description |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Indica se i servizi sono presenti nel sistema. Impostare questa proprietà su **Absent** per specificare che i servizi non esistono. Impostando il valore su **Present** ci si assicura che i servizi di destinazione esistano. Il valore predefinito è **Present**. |
|PsDscRunAsCredential |Imposta le credenziali per l'esecuzione dell'intera risorsa. |

> [!NOTE]
> La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali. Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).

## <a name="example"></a>Esempio

La configurazione seguente avvia i servizi "Servizi Desktop remoto" e "Audio di Windows".

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```