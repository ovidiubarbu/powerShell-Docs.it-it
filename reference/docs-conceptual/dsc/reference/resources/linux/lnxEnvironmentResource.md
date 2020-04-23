---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxEnvironment DSC per Linux
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953228"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>Risorsa nxEnvironment DSC per Linux

La risorsa **nxEnvironment** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le variabili di ambiente di sistema in un nodo Linux.

## <a name="syntax"></a>Sintassi

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Proprietà

|Proprietà |Descrizione |
|---|---|
|Nome |Indica il nome della variabile di ambiente per cui si vuole specificare un determinato stato. |
|valore |Valore da assegnare alla variabile di ambiente. |
|Path |Definisce la variabile di ambiente configurata. Impostare questa proprietà su `$true` se la variabile è **Path**. In caso contrario, impostarla su `$false`. Il valore predefinito è `$false`. Se la variabile configurata è **Path**, il valore specificato tramite la proprietà **Value** viene aggiunto al valore esistente. |

## <a name="common-properties"></a>Proprietà comuni

|Proprietà |Descrizione |
|---|---|
|DependsOn |Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`. |
|Ensure |Determina se verificare l'esistenza della variabile. Impostare questa proprietà su **Present** per assicurarsi che la variabile esista. Impostarla su **Absent** per assicurarsi che la variabile non esista. Il valore predefinito è **Present**. |

## <a name="additional-information"></a>Informazioni aggiuntive

- Se la proprietà **Path** è assente o impostata su `$false`, le variabili di ambiente vengono gestite in `/etc/environment`.
  I programmi o gli script possono richiedere che la configurazione abbia come origine il file `/etc/environment` per accedere alle variabili di ambiente gestite.
- Se la proprietà **Path** è impostata su `$true`, la variabile di ambiente viene gestita nel file `/etc/profile.d/DSCenvironment.sh`. Se questo file non esiste, viene creato automaticamente. Se la proprietà **Ensure** è impostata su **Absent** e la proprietà **Path** è impostata su `$true`, una variabile di ambiente esistente verrà rimossa solo da `/etc/profile.d/DSCenvironment.sh` e non da altri file.

## <a name="example"></a>Esempio

L'esempio seguente mostra come usare la risorsa **nxEnvironment** per specificare che **TestEnvironmentVariable** è presente e ha il valore "Test-Value". Se la variabile **TestEnvironmentVariable** non è presente, verrà creata.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```