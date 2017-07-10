---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa nxFileLine DSC per Linux
ms.openlocfilehash: bde42bbe217fc9acf5a3f2ee0136d30e2b5f2415
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="dsc-for-linux-nxfileline-resource" class="xliff"></a>
# Risorsa nxFileLine DSC per Linux

La risorsa **nxFileLine** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le righe in un file di configurazione in un nodo Linux.

<a id="syntax" class="xliff"></a>
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

<a id="properties" class="xliff"></a>
## Proprietà

|  Proprietà |  Descrizione | 
|---|---|
| FilePath| Percorso completo del file in cui gestire le righe nel nodo di destinazione.| 
| ContainsLine| Riga di cui specificare l'esistenza nel file. Questa riga verrà aggiunta al file, se non è presente. **ContainsLine** è una proprietà obbligatoria, ma può essere impostata su una stringa vuota (`ContainsLine = ‘’``) se non è necessaria.| 
| DoesNotContainPattern| Modello di espressione regolare per le righe che non devono essere presenti nel file. Tutte le righe presenti nel file che corrispondono a questa espressione regolare verranno rimosse.| 
| DependsOn | Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.| 

<a id="example" class="xliff"></a>
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

