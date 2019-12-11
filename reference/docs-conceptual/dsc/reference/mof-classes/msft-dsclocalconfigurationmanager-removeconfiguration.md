---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration
ms.openlocfilehash: aacbed96beb960d7e0d449423a4de9a27f0a287e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71953398"
---
# <a name="removeconfiguration-method"></a>Metodo RemoveConfiguration

Rimuove i file di configurazione.

## <a name="syntax"></a>Sintassi

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

## <a name="parameters"></a>Parametri

*Stage* \[in\] Specifica il documento di configurazione da rimuovere. I valori validi sono i seguenti:

|Value |Description |
|:--- |:---|
|**1** | Il documento di configurazione **corrente** (current.mof). |
|**2** | Il documento di configurazione **in sospeso** (pending.mof).  |
|**4** | Il documento di configurazione **precedente** (previous.mof). |

*Force* \[in\] **true** per forzare la rimozione della configurazione.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)
