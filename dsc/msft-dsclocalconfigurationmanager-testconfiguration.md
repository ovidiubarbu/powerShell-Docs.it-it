---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d746832b01310f43a7aae33dd0fa70c0928bb3e0
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893927"
---
# <a name="testconfiguration-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager

Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.

## <a name="syntax"></a>Sintassi

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
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

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration

## <a name="see-also"></a>Vedere anche

[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)