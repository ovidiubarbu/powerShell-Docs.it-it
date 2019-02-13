---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa ServiceSet DSC
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680722"
---
# <a name="dsc-serviceset-resource"></a>Risorsa ServiceSet DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **ServiceSet** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i servizi nel nodo di destinazione. Questa risorsa è una [risorsa composta](../../../resources/authoringResourceComposite.md) che chiama la [risorsa Service](serviceResource.md) per ogni servizio specificato nella proprietà `Name`.

Usare questa risorsa quando si vogliono configurare diversi servizi nello stesso stato.

## <a name="syntax"></a>Sintassi

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica i nomi del servizio. A volte questo nome è diverso da quelli visualizzati. È possibile ottenere un elenco dei servizi e del rispettivo stato corrente usando il cmdlet [Get-Service](https://technet.microsoft.com/library/hh849804.aspx).|
| StartupType| Indica il tipo di avvio per il servizio. I valori consentiti per questa proprietà sono: **Automatic**, **disabilitato**, e **manuale**|
| BuiltInAccount| Indica l'account di accesso da usare per il servizio. I valori consentiti per questa proprietà sono: **LocalService**, **LocalSystem**, e **NetworkService**.|
| State| Indica lo stato che si vuole specificare per il servizio. **Arrestata** oppure **esecuzione**.|
| Ensure| Indica se i servizi sono presenti nel sistema. Impostare questa proprietà su **Absent** per specificare che i servizi non esistono. Se la proprietà è impostata su **Present** (valore predefinito), specifica che i servizio di destinazione esistono.|
| Credential| Indica le credenziali per l'account in cui verrà eseguita la risorsa del servizio. Questa proprietà e la proprietà **BuiltinAccount** non possono essere usate insieme.|
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è *ResourceName* e il tipo è *ResourceType*, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|



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
