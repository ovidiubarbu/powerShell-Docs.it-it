---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7220c972b3f43b4697cf71df54d2d43881938367
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager

Abilita il debug delle risorse DSC.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*BreakAll* \[in\]  
Imposta un punto di interruzione su ogni riga nello script della risorsa.

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
 

 



