---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Attivare la configurazione di debug DSC.'
MS-HAID: 'cimwin32a.msft\_dsclocalconfigurationmanager\_enabledebugconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo EnableDebugConfiguration della classe MSFT_DSCLocalConfigurationManager

Abilita il debug delle risorse DSC.

Sintassi
------

```mof
uint32 EnableDebugConfiguration(
  [in] boolean BreakAll
);
```

Parametri
----------

*BreakAll* \[in\]  
Imposta un punto di interruzione su ogni riga nello script della risorsa.

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


