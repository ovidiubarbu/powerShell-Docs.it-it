---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: d8ddc9d99f0d74ad907a6e39ae0e8ac14159be16
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
<a id="sendmetaconfigurationapply-method-of-the-msftdsclocalconfigurationmanager-class" class="xliff"></a>
# Metodo SendMetaConfigurationApply della classe MSFT_DSCLocalConfigurationManager

Consente di configurare le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.

<a id="syntax" class="xliff"></a>
Sintassi
------

```mof
uint32 SendMetaConfigurationApply(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

<a id="parameters" class="xliff"></a>
Parametri
----------

*ConfigurationData* \[in\]  
I dati dell'ambiente per la configurazione.

*force* \[in\]  
**true** per forzare l'arresto della configurazione.

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


 

 



