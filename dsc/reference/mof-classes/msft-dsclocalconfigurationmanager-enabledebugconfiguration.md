---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b2eaebfa901cb5d93fd0183287073e6b31f975d1
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047592"
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager

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

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)