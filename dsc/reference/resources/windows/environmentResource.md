---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Environment DSC
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55680952"
---
# <a name="dsc-environment-resource"></a>Risorsa Environment DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa __Environment__ in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema.

## <a name="syntax"></a>Sintassi
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Proprietà

|  Proprietà  |  Description   |
|---|---|
| Nome| Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.|
| Ensure| Indica se una variabile esiste. Impostare questa proprietà su __Present__ per creare una variabile di ambiente se non esiste o per specificare che il suo valore corrisponde a quello fornito tramite la proprietà __Value__ se la variabile esiste già. Impostarla su __Absent__ per eliminare la variabile, se esiste.|
| Path| Definisce la variabile di ambiente configurata. Impostare questa proprietà su __$true__ se la variabile è __Path__; in caso contrario, impostarla su __$false__. Il valore predefinito è __$false__. Se la variabile configurata è __Path__, il valore specificato tramite la proprietà __Value__ viene aggiunto al valore esistente.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| Value| Valore da assegnare alla variabile di ambiente.|

## <a name="example"></a>Esempio

L'esempio seguente specifica che __TestEnvironmentVariable__ è presente e ha il valore __TestValue__. Se la variabile non è presente, viene creata.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```