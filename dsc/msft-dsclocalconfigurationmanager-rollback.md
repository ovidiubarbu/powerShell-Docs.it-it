---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 4956900ecd2c9cb7f2e2b5bcab94616f9f5d5565
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893019"
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo RollBack della classe MSFT_DSCLocalConfigurationManager

Esegue il rollback della configurazione a una versione precedente.

## <a name="syntax"></a>Sintassi

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
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