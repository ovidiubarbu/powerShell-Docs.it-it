---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationResultOutput della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d10a8b44e5056e3fce1598518630a84aff6ceb
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
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

*jobId* \[in\] ID del processo per cui ottenere i dati di output.

*resumeOutputBookmark* \[in\] Specifica che l'output deve essere la continuazione di un segnalibro precedente.

*output* \[out\] Output per il processo specificato.

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