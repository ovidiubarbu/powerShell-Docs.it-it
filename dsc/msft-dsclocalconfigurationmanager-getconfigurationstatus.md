---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: a41e7a15fc935c2cd5fd4cb66d0ab13509d5d4e0
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="getconfigurationstatus-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager

Ottenere la cronologia dello stato della configurazione.

<a name="syntax"></a>Sintassi
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

<a name="parameters"></a>Parametri
----------

*All* \[in\]  
**true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, compresa l'applicazione di configurazione e la verifica coerenza.

*configurationStatus* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.

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


 

 



