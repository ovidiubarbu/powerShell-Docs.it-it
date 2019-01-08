---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/04/2019
ms.locfileid: "54047583"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager

Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.

## <a name="syntax"></a>Sintassi

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

## <a name="parameters"></a>Parametri

*configurationData* \[in\] Dati dell'ambiente per la configurazione.

*InDesiredState* \[out\] Al termine dell'esecuzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.

*ResourcesInDesiredState* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.

*ResourcesNotInDesiredState* \[out\] Al termine dell'esecuzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.

## <a name="return-value"></a>Valore restituito

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## <a name="remarks"></a>Osservazioni

Si tratta di un metodo statico.

## <a name="requirements"></a>Requisiti

MOF** DscCore.mof

spazio dei nomi {0} Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)