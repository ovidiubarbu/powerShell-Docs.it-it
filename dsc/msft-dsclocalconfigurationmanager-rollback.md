---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Eseguire il rollback alla configurazione precedente.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_rollback'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo RollBack della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo RollBack della classe MSFT_DSCLocalConfigurationManager

Esegue il rollback della configurazione a una versione precedente.

Sintassi
------

```mof
uint32 RollBack(
  [in] uint8 configurationNumber
);
```

Parametri
----------

*configurationNumber* \[in\]  
Specifica la configurazione richiesta. 

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


