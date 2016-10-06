---
title: Miglioramenti della risorsa classe DSC
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: b24e70c1e1aaf71487b00fbccaf6edb0f375b888

---

## Miglioramenti della risorsa classe DSC

In questa versione sono stati risolti i problemi noti di WMF 5.0:
* Get-DscConfiguration può restituire valori vuoti (null) o errori se viene restituito un tipo complesso o una hashtable dalla funzione Get() di una risorsa DSC basata su classe.
* Get-DscConfiguration restituisce un errore se nella configurazione DSC vengono usate le credenziali RunAs.
* La risorsa basata su classe non può essere usata in una configurazione composita.
* Start-DscConfiguration si blocca se la risorsa basata su classe ha una proprietà dello stesso tipo.
* La risorsa basata su classe non può essere usata come risorsa esclusiva.



<!--HONumber=Aug16_HO3-->


