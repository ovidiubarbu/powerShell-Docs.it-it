---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9e2a978f9d16abaed959be022229db4da5fd65bd
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="enabledebugconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager

Abilita il debug delle risorse DSC.

<a name="syntax"></a>Sintassi
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

<a name="parameters"></a>Parametri
----------

*BreakAll* \[in\] Imposta un punto di interruzione su ogni riga nello script della risorsa.

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