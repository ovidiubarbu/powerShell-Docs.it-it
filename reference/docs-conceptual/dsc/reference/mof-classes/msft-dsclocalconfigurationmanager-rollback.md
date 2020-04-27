---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack
ms.openlocfilehash: 6452bdffd5160d9956576fb59c98e2f9ff7ddbbb
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954938"
---
# <a name="rollback-method"></a>Metodo RollBack

Esegue il rollback della configurazione a una versione precedente.

## <a name="syntax"></a>Sintassi

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

## <a name="parameters"></a>Parametri

*configurationNumber* \[in\] Specifica la configurazione richiesta.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
