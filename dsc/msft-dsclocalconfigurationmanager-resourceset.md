---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 3486ef559102929f8d05994a4bf6e45d49a0c140
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/15/2018
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

*ResourceType* \[in\]  
Il nome della risorsa da chiamare.

*ModuleName* \[in\]  
Il nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\]  
Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.

*RebootRequired* \[out\]  
In fase di restituzione, questa proprietà è impostata su **true** se il nodo deve essere riavviato.

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

 

 



