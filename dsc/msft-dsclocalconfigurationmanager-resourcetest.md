---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Eseguire il metodo Test direttamente sul provider.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourcetest'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo ResourceTest della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Test** di una risorsa DSC.

Sintassi
------

```mof
uint32 ResourceTest(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean InDesiredState
);
```

Parametri
----------

*ResourceType* \[in\]  
Il nome della risorsa da chiamare.

*ModuleName* \[in\]  
Il nome del modulo che contiene la risorsa da chiamare.

*resourceProperty* \[in\]  
Specifica il nome della proprietà delle risorse e il relativo valore in una tabella hash rispettivamente come chiave e valore. Usare l'articolo
Cmdlet [Get-DscResource](https://technet.microsoft.com/en-us/library/dn521625.aspx) per individuare le proprietà delle risorse e i relativi tipi.

*InDesiredState* \[out\]  
In fase di restituzione, questa proprietà è impostata su **true** se il nodo di destinazione è nello stato desiderato.

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


