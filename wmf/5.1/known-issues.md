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
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 387ebc0467b9f154444292f391af0f4b77123639

---

#Problemi noti in WMF 5.1 (anteprima) #

> Nota: queste informazioni sono provvisorie e soggette a modifiche.

##Problemi relativi a Pester
In questa versione vi sono due problemi che è necessario tenere presenti quando si usa Pester o Nano Server:

* L'esecuzione di test su Pester può generare errori a causa delle differenze tra FULL CLR e CORE CLR. In particolare, il metodo di convalida non è disponibile nel tipo XmlDocument. Sei test che tentano di convalidare lo schema dei log di output NUnit hanno esito negativo. 
* Attualmente un test code coverage non riesce perché la risorsa DSC *WindowsFeature* non esiste in Nano Server. Tuttavia, questi errori sono in genere innocui e possono essere ignorati.


<!--HONumber=Jul16_HO3-->


