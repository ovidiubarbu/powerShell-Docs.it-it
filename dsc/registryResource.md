---
title: Risorsa Registry DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 15e346ecd630a1256477d375bc1373f376e76f64

---

# Risorsa Registry DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **Registry** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire i valori e le chiavi del Registro di sistema in un nodo di destinazione.

## Sintassi

```
Registry [string] #ResourceName
{
    Key = [string]
    ValueName = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Force =  [bool]   ]
    [ Hex = [bool] ]
    [ DependsOn = [string[]] ]
    [ ValueData = [string[]] ]
    [ ValueType = [string] { Binary | Dword | ExpandString | MultiString | Qword | String }  ]
}
```

## Proprietà
|  Proprietà  |  Descrizione   | 
|---|---| 
| Key| Indica il percorso della chiave del Registro di sistema per cui si vuole specificare un determinato stato. Questo percorso deve includere l'hive.| 
| ValueName| Indica il nome del valore del Registro di sistema.| 
| Ensure| Indica se la chiave e il valore esistono. Impostare questa proprietà su "Present" per specificare che la chiave e il valore esistono. Impostare questa proprietà su "Absent" per specificare che la chiave e il valore non esistono. Il valore predefinito è "Present".| 
| Force| Se la chiave del Registro di sistema è presente, __Force__ la sovrascrive con il nuovo valore.| 
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

## Esempio
```powershell
Registry RegistryExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Key = "HKEY_LOCAL_MACHINE\SOFTWARE\ExampleKey"
    ValueName = "TestValue"
    ValueData = "TestData"
}
```




<!--HONumber=Jun16_HO4-->


