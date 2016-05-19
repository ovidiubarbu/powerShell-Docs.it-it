---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Ottenere la cronologia dello stato della configurazione.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_getconfigurationstatus'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo GetConfigurationStatus della classe MSFT_DSCLocalConfigurationManager

Ottenere la cronologia dello stato della configurazione.

Sintassi
------

```mof
uint32 GetConfigurationStatus(
  [in]  boolean                     All,
  [out] MSFT_DSCConfigurationStatus configurationStatus[]
);
```

Parametri
----------

*All* \[in\]  
**true** se questo metodo deve restituire informazioni relative a tutte le esecuzioni di configurazione sulla macchina, tra cui
l'applicazione di configurazione e la verifica di coerenza.

*configurationStatus* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_DSCConfigurationStatus** che definisce le impostazioni.

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


