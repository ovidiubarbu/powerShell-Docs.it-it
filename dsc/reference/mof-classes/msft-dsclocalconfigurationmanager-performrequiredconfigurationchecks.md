---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: b92eefb7fbea6d96afa31f6b802ba10fe20d4103
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55682032"
---
# <a name="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager

Avvia una verifica di coerenza usando l'Utilità di pianificazione.

## <a name="syntax"></a>Sintassi

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

## <a name="parameters"></a>Parametri

*Flags* \[in\] Maschera di bit che specifica il tipo di verifica di coerenza da eseguire. I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:

|Value |Description |
|:--- |:---|
|**1** | Una verifica di coerenza normale. |
|**2** | La continuazione di una verifica di coerenza dopo un riavvio. Questo valore non deve essere combinato con altri valori. |
|**4** | La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo. Questo valore deve essere sempre combinato con **1** per un valore di **5**. |
|**8** | Inviare lo stato al server di report. |

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)