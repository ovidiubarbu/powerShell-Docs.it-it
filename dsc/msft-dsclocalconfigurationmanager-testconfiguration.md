---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Inviare il documento di configurazione al nodo gestito ed eseguirne il test in base alla configurazione corrente.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_testconfiguration'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo TestConfiguration della classe MSFT_DSCLocalConfigurationManager

Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.

Sintassi
------

```mof
uint32 TestConfiguration(
  [in]  uint8                          configurationData[],
  [out] boolean                        InDesiredState,
  [out] MSFT_ResourceInDesiredState    ResourcesInDesiredState[],
  [out] MSFT_ResourceNotInDesiredState ResourcesNotInDesiredState[]
);
```

Parametri
----------

*configurationData* \[in\]  
Dati dell'ambiente per la configurazione.

*InDesiredState* \[out\]  
In fase di restituzione, specifica se il nodo gestito è nello stato specificato dal documento di configurazione.

*ResourcesInDesiredState* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceInDesiredState** che specifica le risorse che si trovano nello stato desiderato.

*ResourcesNotInDesiredState* \[out\]  
In fase di restituzione, contiene un'istanza incorporata della classe **MSFT_ResourceNotInDesiredState** che specifica le risorse che non si trovano nello stato desiderato.

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


