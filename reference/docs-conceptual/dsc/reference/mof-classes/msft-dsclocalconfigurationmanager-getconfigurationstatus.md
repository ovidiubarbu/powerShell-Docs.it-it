---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus
ms.openlocfilehash: 83b30ba2612d962fcf2fa658d07d18fb2d91ccc7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71955018"
---
# <a name="getconfigurationstatus-method"></a>Metodo GetConfigurationStatus

Ottenere la cronologia dello stato della configurazione.

## <a name="syntax"></a>Sintassi

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

## <a name="parameters"></a>Parametri

*All* \[in\] **true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, compresa l'applicazione di configurazione e la verifica coerenza.

*configurationStatus* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
