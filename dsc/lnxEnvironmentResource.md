---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxEnvironment DSC per Linux
ms.openlocfilehash: 6d1d5e578e9a7ddda0e70063f86867de2e87a52e
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Risorsa nxEnvironment DSC per Linux

La risorsa **nxEnvironment** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema in un nodo Linux.

## <a name="syntax"></a>Sintassi

```
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Path = <bool> }
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Proprietà

|  Proprietà |  Description |
|---|---|
| Name| Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato.|
| Value| Valore da assegnare alla variabile di ambiente.|
| Ensure| Determina se verificare l'esistenza della variabile. Impostare questa proprietà su "Present" per specificare che la variabile esiste. Impostarla su "Absent" per specificare che la variabile non esiste. Il valore predefinito è "Present".|
| Path| Definisce la variabile di ambiente configurata. Impostare questa proprietà su **$true** se la variabile è **Path**; in caso contrario, impostarla su **$false**. Il valore predefinito è **$false**. Se la variabile configurata è **Path**, il valore specificato tramite la proprietà **Value** viene aggiunto al valore esistente.|
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Informazioni aggiuntive

* Se la proprietà **Path** è assente o impostata su **$false**, le variabili di ambiente vengono gestite in `/etc/environment`. I programmi o gli script possono richiedere che la configurazione abbia come origine il file `/etc/environment` per accedere alle variabili di ambiente gestite.
* Se la proprietà **Path** è impostata su **$true**, la variabile di ambiente viene gestita nel file `/etc/profile.d/DSCenvironment.sh`. Se questo file non esiste, viene creato automaticamente. Se la proprietà **Ensure** è impostata su "Absent" e la proprietà **Path** è impostata su **$true**, una variabile di ambiente esistente verrà rimossa solo da `/etc/profile.d/DSCenvironment.sh` e non da altri file.

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa **nxEnvironment** per specificare che **TestEnvironmentVariable** è presente e ha il valore "Test-Value". Se la variabile **TestEnvironmentVariable** non è presente, verrà creata.

```
Import-DSCResource -Module nx


nxEnvironment EnvironmentExample
{
    Ensure = “Present”
    Name = “TestEnvironmentVariable”
    Value = “TestValue”
}
```