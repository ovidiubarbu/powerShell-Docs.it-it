---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Arresto della configurazione in corso.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_stopconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo StopConfiguration della classe MSFT_DSCLocalConfigurationManager

Arresta la modifica della configurazione in corso.

Sintassi
------

```mof
uint32 StopConfiguration(
  [in] boolean force
);
```

Parametri
----------

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


