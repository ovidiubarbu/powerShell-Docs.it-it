---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 9cc4384088fcc39b09979b8ae4d023fc46307b13
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager

Avvia una verifica di coerenza usando l'Utilità di pianificazione.

<a name="syntax"></a>Sintassi
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a name="parameters"></a>Parametri
----------

*Flags* \[in\] Maschera di bit che specifica il tipo di verifica di coerenza da eseguire. I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:

|Value |Description |
|:--- |:---|
|**1** | Una verifica di coerenza normale. |
|**2** | La continuazione di una verifica di coerenza dopo un riavvio. Questo valore non deve essere combinato con altri valori. |
|**4** | La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo. Questo valore deve essere sempre combinato con **1** per un valore di **5**. |
|**8** | Inviare lo stato al server di report. |

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