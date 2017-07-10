---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 09862fd3c19e1e517c9bf5df878113ba3f10d8a6
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager

Recupera l'output dell'agente di configurazione associato a un processo specifico.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*jobId* \[in\]  
L'ID del processo di cui ottenere i dati di output.

*resumeOutputBookmark* \[in\]  
Specifica che l'output deve essere la continuazione di un segnalibro precedente.

*output* \[out\]  
L'output per il processo specificato.

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

 

 



