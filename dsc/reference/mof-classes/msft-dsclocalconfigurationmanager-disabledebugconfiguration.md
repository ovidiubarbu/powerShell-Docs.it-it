---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo DisableDebugConfiguration
ms.openlocfilehash: e3eab98c734b3fd1593ceb2b5d4b40fa69a3bf97
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67727167"
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
