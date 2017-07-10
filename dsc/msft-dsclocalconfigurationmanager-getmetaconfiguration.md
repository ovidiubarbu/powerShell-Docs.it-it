---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4f209014e9fde5841a9bce743f5364e6677d1e41
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="getmetaconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo GetMetaConfiguration della classe MSFT_DSCLocalConfigurationManager

Consente di ottenere le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 GetMetaConfiguration(
  [out] MSFT_DSCMetaConfiguration MetaConfiguration
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*MetaConfiguration* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCMetaConfiguration** che definisce le impostazioni.

<a id="return-value" class="xliff"></a>
## Valore restituito
------------

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

<a id="remarks" class="xliff"></a>
## Osservazioni

Si tratta di un metodo statico.

<a id="requirements" class="xliff"></a>
## Requisiti
------------
>**MOF:** DscCore.mof

>**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Vedere anche


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



