---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 04f0f3146473dc71f492086449d9dce5467c55db
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager

Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.

<a name="syntax"></a>Sintassi
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

<a name="parameters"></a>Parametri
----------

*configurationData* \[in\]  
Dati dell'ambiente per la configurazione.

*InDesiredState* \[out\]  
In fase di restituzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.

*ResourcesInDesiredState* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.

*ResourcesNotInDesiredState* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.

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


 

 



