---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b028079cf826719967858f50e357b441ba8f9d79
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047672"
---
# <a name="sendconfigurationapplyasync-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo SendConfigurationApplyAsync della classe MSFT_DSCLocalConfigurationManager

Invia il documento di configurazione in modo asicrono al nodo gestito e usa l'agente di configurazione per applicare la configurazione.

## <a name="syntax"></a>Sintassi

```mof
uint32 SendConfigurationApplyAsync(
  [in] uint8   ConfigurationData[],
  [in] boolean force,
  [in] string  jobId
);
```

## <a name="parameters"></a>Parametri

*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.

*force* \[in\] **true** per forzare l'arresto della configurazione.

*jobId* \[in\] ID del processo per cui inviare la configurazione.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)