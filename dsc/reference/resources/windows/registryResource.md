---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: e0ae1a4a27edc08c4e6ccd47786426917eb1ccb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682259"
---
# <a name="dsc-registry-resource"></a>Risorsa Registry DSC

_Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0_

La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Present | Absent }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Proprietà

| Proprietà | Description |
| --- | --- |
| Key| Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato. Questo percorso deve includere l'hive.|
| ValueName| Indica il nome del valore del Registro di sistema. Per aggiungere o rimuovere una chiave del Registro di sistema specificare questa proprietà come stringa vuota, senza specificare ValueType o ValueData. Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema specificare questa proprietà come stringa vuota e specificare ValueType o ValueData.|
| Ensure| Indica se la chiave e il valore esistono. Impostare questa proprietà su "Present" per specificare che la chiave e il valore esistono. Impostare questa proprietà su "Absent" per specificare che la chiave e il valore non esistono. Il valore predefinito è "Present".|
| Force| Se la chiave del Registro di sistema è presente, **Force** la sovrascrive con il nuovo valore. Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere **$true**. |
| Hex| Indica se i dati verranno espressi in formato esadecimale. Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale. La proprietà non è valida per altri tipi. Il valore predefinito è **$false**.|
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.|
| ValueData| Dati per il valore del Registro di sistema.|
| ValueType| Indica il tipo di valore. I tipi supportati sono: Stringa (REG_SZ), file binario (REG-BINARY), Dword 32 bit (REG_DWORD), Qword 64-bit (REG_QWORD), multistringa (REG_MULTI_SZ), stringa espandibile (REG_EXPAND_SZ) |

## <a name="example"></a>Esempio

Questo esempio garantisce che sia presente una chiave denominata "ExampleKey" nell'hive **HKEY\_LOCAL\_MACHINE**.

```powershell
Configuration RegistryTest
{
    Registry RegistryExample
    {
        Ensure      = "Present"  # You can also set Ensure to "Absent"
        Key         = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
        ValueName   = "TestValue"
        ValueData   = "TestData"
    }
}
```

> [!NOTE]
> La modifica di un'impostazione del Registro di sistema nell'hive `HKEY\CURRENT\USER` richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema. È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione. Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](../../../configurations/runAsUser.md).
