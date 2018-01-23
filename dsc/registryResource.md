---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Registry DSC
ms.openlocfilehash: 1e73e4275c0d9db5d8fac7641514ea8190f719ca
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-registry-resource"></a>Risorsa Registry DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.

## <a name="syntax"></a>Sintassi

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## <a name="properties"></a>Proprietà
|  Proprietà  |  Description   | 
|---|---| 
| Key| Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato. Questo percorso deve includere l'hive.| 
| ValueName| Indica il nome del valore del Registro di sistema. Per aggiungere o rimuovere una chiave del Registro di sistema specificare questa proprietà come stringa vuota, senza specificare ValueType o ValueData. Per modificare o rimuovere il valore predefinito di una chiave del Registro di sistema specificare questa proprietà come stringa vuota e specificare ValueType o ValueData.| 
| Ensure| Indica se la chiave e il valore esistono. Impostare questa proprietà su "Present" per specificare che la chiave e il valore esistono. Impostare questa proprietà su "Absent" per specificare che la chiave e il valore non esistono. Il valore predefinito è "Present".| 
| Force| Se la chiave del Registro di sistema è presente, __Force__ la sovrascrive con il nuovo valore. Se si elimina una chiave del Registro di sistema con sottochiavi il valore deve essere __$true__.| 
| Hex| Indica se i dati verranno espressi in formato esadecimale. Se questa proprietà è specificata, i dati con valori DWORD o QWORD vengono presentati in formato esadecimale. La proprietà non è valida per altri tipi. Il valore predefinito è __$false__.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 
| ValueData| Dati per il valore del Registro di sistema.| 
| ValueType| Indica il tipo di valore. I tipi supportati sono: 
<ul><li>Stringa (REG_SZ)</li>


<li>Binario (REG-BINARY)</li>


<li>Dword a 32 bit (REG_DWORD)</li>


<li>Qword a 64 bit (REG_QWORD)</li>


<li>Multistringa (REG_MULTI_SZ)</li>


<li>Stringa espandibile (REG_EXPAND_SZ)</li></ul>

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

>**Nota:** la modifica di un'impostazione del Registro di sistema nell'hive **HKEY\_CURRENT\_USER** richiede l'esecuzione della configurazione con le credenziali dell'utente anziché come il sistema.
>È possibile usare la proprietà **PsDscRunAsCredential** per specificare le credenziali utente per la configurazione. Per un esempio, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md)



