---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceGet
ms.openlocfilehash: dbe610dfcef5ef6c79783801ecb6fdb7408bdfa5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954998"
---
# <a name="resourceget-method"></a>Metodo ResourceGet

Chiama direttamente il metodo di **Get** di una risorsa DSC.

## <a name="syntax"></a>Sintassi

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

## <a name="parameters"></a>Parametri

*ResourceType* \[in\] Nome della risorsa da chiamare.

*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.

*configurations* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata delle configurazioni.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
