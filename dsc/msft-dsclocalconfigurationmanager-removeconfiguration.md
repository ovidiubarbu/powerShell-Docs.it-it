---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: c68d17d38336dec08e078366ea5f2071fcf7c5a8
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
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