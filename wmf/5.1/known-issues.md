---
title: Problemi noti in WMF 5.1 (anteprima)
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: krishna
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 3dde62efa7ba595ed5160cc81b4e2b17a54e52a2
ms.openlocfilehash: d4c9e88ddd6cfaec611527d19d00cbd4db9f5d1d

---

#Problemi noti in WMF 5.1 (anteprima) #

> Nota: queste informazioni sono provvisorie e soggette a modifiche.

##Avvio del collegamento di PowerShell come amministratore
Dopo l'installazione di WMF, se si tenta di avviare PowerShell come amministratore dal collegamento, è possibile che venga visualizzato il messaggio "Errore non specificato".
Riaprire il collegamento non usando l'accesso come amministratore e il collegamento funzionerà ora anche con l'accesso come amministratore.

##Pester
In questa versione vi sono due problemi che è necessario tenere presenti quando si usa Pester o Nano Server:

* L'esecuzione di test su Pester può generare errori a causa delle differenze tra FULL CLR e CORE CLR. In particolare, il metodo di convalida non è disponibile nel tipo XmlDocument. Sei test che tentano di convalidare lo schema dei log di output NUnit hanno esito negativo. 
* Attualmente un test code coverage non riesce perché la risorsa DSC *WindowsFeature* non esiste in Nano Server. Tuttavia, questi errori sono in genere innocui e possono essere ignorati.

##Convalida dell'operazione 

* Update-Help ha esito negativo per il modulo Microsoft.PowerShell.Operation.Validation a causa di un URI della guida non funzionante



<!--HONumber=Sep16_HO4-->


