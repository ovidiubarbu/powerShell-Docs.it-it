---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 73d7d543505a3768a0660084345d3858e055514f
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="resourcetest-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Test** di una risorsa DSC.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*ResourceType* \[in\]  
Il nome della risorsa da chiamare.

*ModuleName* \[in\]  
Il nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\]  
Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare il cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.

*InDesiredState* \[out\]  
In fase di restituzione, questa proprietà è impostata su **true** se il nodo di destinazione è nello stato desiderato.

<a id="return-value" class="xliff"></a>
## Valore restituito
------------

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

<a id="remarks" class="xliff"></a>
## Osservazioni

Si tratta di un metodo statico.

<a id="requirements" class="xliff"></a>
## Requisiti
------------
>**MOF:** DscCore.mof

>**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration


<a id="see-also" class="xliff"></a>
## Vedere anche


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 



