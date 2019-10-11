---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo DisableDebugConfiguration
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71955058"
---
# <a name="disabledebugconfiguration-method"></a>Metodo DisableDebugConfiguration

Disabilita il debug delle risorse DSC.

## <a name="syntax"></a>Sintassi

```mof
uint32 DisableDebugConfiguration();
```

## <a name="parameters"></a>Parametri

Questo metodo non presenta parametri.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
