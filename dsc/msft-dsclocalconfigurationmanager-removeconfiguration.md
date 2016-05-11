---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Rimozione dei file di configurazione.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_removeconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo RemoveConfiguration della classe MSFT_DSCLocalConfigurationManager

Rimuove i file di configurazione.

Sintassi
------

```mof
uint32 RemoveConfiguration(
  [in] uint32  Stage,
  [in] boolean Force
);
```

Parametri
----------

*Stage* \[in\]  
Specifica il documento di configurazione da rimuovere. I valori validi sono i seguenti:

|Valore |Descrizione |
|:--- |:---|
|**1** | Il documento di configurazione **corrente** (current.mof). |
|**2** | Il documento di configurazione **in sospeso** (pending.mof).  |
|**4** | Il documento di configurazione **precedente** (previous.mof). |

*Force* \[in\]  
**true** per forzare la rimozione della configurazione.

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


