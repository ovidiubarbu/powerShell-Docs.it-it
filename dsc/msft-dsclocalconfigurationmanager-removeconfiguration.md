---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: e0ae8a50212b70841d210d7b2d666a2855218d1a
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager

Rimuove i file di configurazione.

<a name="syntax"></a>Sintassi
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

<a name="parameters"></a>Parametri
----------

*Stage* \[in\] Specifica il documento di configurazione da rimuovere. I valori validi sono i seguenti:

|Value |Description |
|:--- |:---|
|**1** | Il documento di configurazione **corrente** (current.mof). |
|**2** | Il documento di configurazione **in sospeso** (pending.mof).  |
|**4** | Il documento di configurazione **precedente** (previous.mof). |

*Force* \[in\] **true** per forzare la rimozione della configurazione.

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