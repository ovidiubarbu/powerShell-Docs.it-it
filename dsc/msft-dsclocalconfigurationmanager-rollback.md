---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b8597e3eb7872d9894863fb02d927c9f475da44c
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="rollback-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo RollBack della classe MSFT_DSCLocalConfigurationManager

Esegue il rollback della configurazione a una versione precedente.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*configurationNumber* \[in\]  
Specifica la configurazione richiesta. 

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


 

 



