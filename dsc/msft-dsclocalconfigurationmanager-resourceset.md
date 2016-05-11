---
DCS.appliesToProduct: 'WindowsServer\_Dev'
Description: 'Eseguire il metodo Set direttamente sul provider.'
MS-HAID: 'cimwin32a.MSFT_DSCLocalConfigurationManager\_resourceset'
MSHAttr: 'PreferredLib:/library'
title: 'Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager'
---

# Metodo ResourceSet della classe MSFT_DSCLocalConfigurationManager

Chiama direttamente il metodo di **Set** di una risorsa DSC.

Sintassi
------

```mof
uint32 ResourceSet(
  [in]  string  ResourceType,
  [in]  string  ModuleName,
  [in]  uint8   resourceProperty[],
  [out] boolean RebootRequired
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

*RebootRequired* \[out\]  
In fase di restituzione, questa proprietà è impostata su **true** se il nodo deve essere riavviato.

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


