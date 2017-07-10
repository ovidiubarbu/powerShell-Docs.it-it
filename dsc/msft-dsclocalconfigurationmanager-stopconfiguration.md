---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: f0b550615b20f07f99c8ed7009805c45794bfe22
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager

Arresta la modifica della configurazione in corso.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*force* \[in\]  
**true** per forzare l'arresto della configurazione.

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


 

 



