---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: aaed29cb81e2079c4673b621b81c52e109aa7b48
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="stopconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager

Arresta la modifica della configurazione in corso.

<a name="syntax"></a>Sintassi
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

<a name="parameters"></a>Parametri
----------

*force* \[in\] **true** per forzare l'arresto della configurazione.

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