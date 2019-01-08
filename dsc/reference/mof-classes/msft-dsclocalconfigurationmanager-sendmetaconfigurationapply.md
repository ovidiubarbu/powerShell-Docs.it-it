---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b372a6c0ab9d4561dcf67026275e7d3ca6aa2584
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047850"
---
# <a name="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager

Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.

## <a name="syntax"></a>Sintassi

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

## <a name="parameters"></a>Parametri

*ConfigurationData* \[in\] Dati dell'ambiente per la configurazione.

*force* \[in\] **true** per forzare l'arresto della configurazione.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)