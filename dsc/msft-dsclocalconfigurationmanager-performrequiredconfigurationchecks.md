---
title: Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---


# Metodo PerformRequiredConfigurationChecks della classe MSFT_DSCLocalConfigurationManager

Avvia una verifica di coerenza usando l'Utilità di pianificazione.

Sintassi
------

```mof
uint32 PerformRequiredConfigurationChecks(
  [in] uint32 Flags
);
```

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

## Valore restituito
------------

In caso di esito positivo, il valore restituisce zero, altrimenti, restituisce un codice di errore.

## Osservazioni

Si tratta di un metodo statico.

## Requisiti
------------
>**MOF:** DscCore.mof

>**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration


## Vedere anche


[**MSFT_DSCLocalConfigurationManager**](msft-dsclocalconfigurationmanager.md)


 

 





<!--HONumber=May16_HO3-->


