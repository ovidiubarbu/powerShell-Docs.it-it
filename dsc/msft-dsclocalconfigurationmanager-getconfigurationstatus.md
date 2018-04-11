---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: dde4ac003b346018561481e05ca7374475f9ff1d
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager

Ottenere la cronologia dello stato della configurazione.

<a name="syntax"></a>Sintassi
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametri
----------

*All* \[in\] **true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione nel computer, compresa l'applicazione di configurazione e la verifica di coerenza.

*configurationStatus* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.

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