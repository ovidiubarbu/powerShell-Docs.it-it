---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 26110b3920104da7343b8d55cf63440c12accbbc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="performrequiredconfigurationchecks-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager

Avvia una verifica di coerenza usando l'Utilità di pianificazione.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*Flags* \[in\]  
Una maschera di bit che specifica il tipo di verifica di coerenza da eseguire. I valori seguenti sono validi e possono essere combinati tramite un'operazione bit per bit **OR**:

|Valore |Descrizione |
|:--- |:---|
|**1** | Una verifica di coerenza normale. |
|**2** | La continuazione di una verifica di coerenza dopo un riavvio. Questo valore non deve essere combinato con altri valori. |
|**4** | La configurazione deve essere recuperata dal server di pull specificato nella metaconfigurazione per il nodo. Questo valore deve essere sempre combinato con **1** per un valore di **5**. |
|**8** | Inviare lo stato al server di report. |

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


 

 



