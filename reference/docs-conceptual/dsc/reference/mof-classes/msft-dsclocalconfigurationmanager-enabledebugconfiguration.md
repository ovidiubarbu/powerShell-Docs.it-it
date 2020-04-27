---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration
ms.openlocfilehash: f1290e4d898332361850ffc85aa0a8d79863c8f7
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953438"
---
# <a name="enabledebugconfiguration-method"></a>Metodo EnableDebugConfiguration

Abilita il debug delle risorse DSC.

## <a name="syntax"></a>Sintassi

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

## <a name="parameters"></a>Parametri

*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
