---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 0c9c1d33117067d76d61036d5839f0b676eb4a97
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
---
# <a name="resourceset-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Set** di una risorsa DSC.

<a name="syntax"></a>Sintassi
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
);
```

<a name="parameters"></a>Parametri
----------

*ResourceType* \[in\] Nome della risorsa da chiamare.

*ModuleName* \[in\] Nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\] Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.

*RebootRequired* \[out\] Al termine dell'esecuzione, questa proprietà viene impostata su **true** se il nodo deve essere riavviato.

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