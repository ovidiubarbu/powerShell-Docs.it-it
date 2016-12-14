---
title: Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 1666b85402f17230090f7290c8cb400dd9fbf0a6
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="resourceget-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo ResourceGet della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Get** di una risorsa DSC.

<a name="syntax"></a>Sintassi
------

```mof
uint32 ResourceGet(
  [in]  string           ResourceType,
  [in]  string           ModuleName,
  [in]  uint8            resourceProperty[],
  [out] OMI_BaseResource configurations
);
```

<a name="parameters"></a>Parametri
----------

*ResourceType* \[in\]  
Il nome della risorsa da chiamare.

*ModuleName* \[in\]  
Il nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\]  
Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.

*configurations* \[out\]  
In fase di restituzione, contiene un'istanza incorporata delle configurazioni.

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


 

 



