---
title: Risorsa nxFileLine DSC per Linux
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 9196129e79272d8bee717ef8a5d42fb590760a0f

---

# Risorsa nxFileLine DSC per Linux

La risorsa **nxFileLine** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le righe in un file di configurazione in un nodo Linux.

## Sintassi

```
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]

}
```

## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| FilePath| Percorso completo del file in cui gestire le righe nel nodo di destinazione.| 
| ContainsLine| Riga di cui specificare l'esistenza nel file. Questa riga verrà aggiunta al file, se non è presente. **ContainsLine** è una proprietà obbligatoria, ma può essere impostata su una stringa vuota (`ContainsLine = ‘’``) se non è necessaria.| 
| DoesNotContainPattern| Modello di espressione regolare per le righe che non devono essere presenti nel file. Tutte le righe presenti nel file che corrispondono a questa espressione regolare verranno rimosse.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

## Esempio

Questo esempio illustra l'uso della risorsa **nxFileLine** per configurare il file `/etc/sudoers`, specificando che l'utente: monuser è configurato per non richiedere TTY.

```
Import-DSCResource -Module nx 

nxFileLine DoNotRequireTTY
{
   FilePath = “/etc/sudoers”
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
} 
```




<!--HONumber=Jun16_HO4-->


