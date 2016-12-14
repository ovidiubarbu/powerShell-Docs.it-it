---
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 8f13964dfbbe1cd827c58232a35d1cbacddeed1b
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="getconfigurationresultoutput-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager

Recupera l'output dell'agente di configurazione associato a un processo specifico.

<a name="syntax"></a>Sintassi
------

```mof
uint32 GetConfigurationResultOutput(
  [in]  string                      jobId,
  [in]  uint8                       resumeOutputBookmark[],
  [out] MSFT_DSCConfigurationOutput output[]
);
```

<a name="parameters"></a>Parametri
----------

*jobId* \[in\]  
L'ID del processo di cui ottenere i dati di output.

*resumeOutputBookmark* \[in\]  
Specifica che l'output deve essere la continuazione di un segnalibro precedente.

*output* \[out\]  
L'output per il processo specificato.

## <a name="return-value"></a>Valore restituito
------------

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti
------------
>**MOF:** DscCore.mof

>**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration


## <a name="see-also"></a>Vedere anche


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)

 

 



