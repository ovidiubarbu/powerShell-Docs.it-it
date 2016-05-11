---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Inviare il documento di configurazione al nodo gestito e usare l'agente di configurazione per applicare la configurazione tramite il metodo Get.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo GetConfiguration della classe MSFT_DSCLocalConfigurationManager

Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.

Sintassi
------

```mof
uint32 GetConfiguration(
  [in]  uint8            configurationData[],
  [out] OMI_BaseResource configurations[]
);
```

Parametri
----------

*configurationData* \[in\]  
Specifica i dati di configurazione da inviare.

*configurations* \[out\]  
In fase di restituzione, contiene un'istanza incorporata delle configurazioni.

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
 

 





<!--HONumber=Apr16_HO2-->


