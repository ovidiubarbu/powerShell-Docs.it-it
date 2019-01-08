---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 559ff1793a18e28dad2f176bdb20eb53bc08630d
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047508"
---
# <a name="applyconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo ApplyConfiguration della classe MSFT_DSCLocalConfigurationManager

Usa l'agente di configurazione per applicare la configurazione in sospeso.

Se non sono presenti configurazioni in sospeso, questo metodo applica nuovamente la configurazione corrente.

## <a name="syntax"></a>Sintassi

```mof
uint32 ApplyConfiguration(
  [in] boolean force
);
```

## <a name="parameters"></a>Parametri

*force* \[in\] Se il valore è **true**, la configurazione corrente viene applicata nuovamente, anche se è presente una configurazione in sospeso.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)