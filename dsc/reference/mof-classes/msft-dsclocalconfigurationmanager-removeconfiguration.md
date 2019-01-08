---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 03555cc73da1272bdebebc3d93b26aaf8fabc18e
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047680"
---
# <a name="removeconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager

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

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)