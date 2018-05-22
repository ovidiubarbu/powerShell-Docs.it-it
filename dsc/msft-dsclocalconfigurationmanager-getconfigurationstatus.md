---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 725b1a2a62510a4e9b59aabdec8a7e502c737bfc
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
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