---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Inviare il documento di configurazione al nodo gestito e salvarlo come in sospeso.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_sendconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo SendConfiguration della classe MSFT_DSCLocalConfigurationManager

Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.

Sintassi
------

```mof
uint32 SendConfiguration(
  [in] uint8   ConfigurationData[],
  [in] boolean force
);
```

Parametri
----------

*ConfigurationData* \[in\]  
I dati dell'ambiente per la configurazione.

*force* \[in\]  
**true** per forzare l'arresto della configurazione.

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


