---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 2712b7ff0a19e643c1f343d436c084f8970c9dd4
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047664"
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Set** di una risorsa DSC.

## <a name="syntax"></a>Sintassi

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

## <a name="parameters"></a>Parametri

*ResourceType* \[in\] Nome della risorsa da chiamare.

*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per individuare le proprietà delle risorse e i relativi tipi.

*RebootRequired* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo deve essere riavviato.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)