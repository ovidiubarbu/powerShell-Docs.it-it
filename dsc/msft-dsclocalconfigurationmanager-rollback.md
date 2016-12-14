---
title: Metodo RollBack della classe MSFT_DSCLocalConfigurationManager
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: 771a9c7b50aba26f89dbf6b24eb3df67bafeac0a
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="rollback-method-of-the-msftdsclocalconfigurationmanager-class"></a>Metodo RollBack della classe MSFT_DSCLocalConfigurationManager

Esegue il rollback della configurazione a una versione precedente.

<a name="syntax"></a>Sintassi
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

<a name="parameters"></a>Parametri
----------

*configurationNumber* \[in\]  
Specifica la configurazione richiesta. 

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


 

 



