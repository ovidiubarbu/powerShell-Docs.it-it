---
title: Panoramica di DSC (Desired State Configuration) per decision maker
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: 6477ae8575c83fc24150f9502515ff5b82bc8198
ms.openlocfilehash: 2d2b142dc862f7655f28aa34e1fd91f63bd6286e

---

# Panoramica di DSC (Desired State Configuration) per decision maker #

Questo documento descrive i vantaggi dell'uso di PowerShell DSC (Desired State Configuration) per le aziende. Non si tratta di una guida tecnica.

## Che cos'è DSC (Desired State Configuration)? ##

Windows PowerShell DSC (Desired State Configuration) è una piattaforma di gestione delle configurazioni integrata in Windows e basata su standard aperti. DSC è sufficientemente flessibile per funzionare in modo affidabile e coerente in ogni fase del ciclo di distribuzione (sviluppo, test, pre-produzione, produzione), nonché quando viene applicata scalabilità orizzontale. 

DSC ha come concetto centrale l'idea di "[configurazioni](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)", ovvero documenti facili da leggere che descrivono un ambiente costituito da computer ("nodi") con caratteristiche specifiche. Queste caratteristiche possono essere semplici, ad esempio per abilitare una funzionalità specifica di Windows, o complesse, ad esempio per la distribuzione di SharePoint. 

In DSC sono anche integrate funzionalità di monitoraggio e creazione di report. Se un sistema non è più conforme, DSC può generare un avviso ed eseguire operazioni per correggere il sistema. 

## Vantaggi dell'uso di DSC (Desired State Configuration) ##

Le configurazioni sono progettate per essere facili da leggere, archiviare e aggiornare. Le configurazioni dichiarano semplicemente lo stato desiderato per i dispositivi di destinazione, senza che sia necessario scrivere istruzioni su come impostare tale stato. In questo modo, DSC semplifica notevolmente l'apprendimento, l'adozione, l'implementazione e la gestione della configurazione. 

La creazione di configurazioni comporta l'acquisizione di passaggi di distribuzione complessi come "unica origine di dati reali" in un'unica posizione. In questo modo, le distribuzioni ripetute di un set specifico di computer sono molto meno soggette a errori. Ciò rende le distribuzioni più veloci e affidabili. È quindi possibile eseguire distribuzioni complesse in tempi brevi.

Le configurazioni possono anche essere condivise tramite [PowerShell Gallery](https://powershellgallery.com). Ciò significa che potrebbero essere già disponibili scenari comuni e procedure consigliate per il lavoro da svolgere.


## DSC (Desired State Configuration) e DevOps ##

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) è una combinazione di persone, tecnologie e cultura che consente rapidità di distribuzione e iterazione. La soluzione DSC è stata progettata tenendo in considerazione DevOps. La disponibilità di una singola configurazione che definisce un ambiente significa che gli sviluppatori possono codificare i requisiti in una configurazione e verificare la configurazione nel controllo del codice sorgente, mentre i team operativi possono distribuire facilmente il codice senza dover eseguire processi manuali soggetti a errori. 

Le configurazioni sono anche [guidate dai dati](https://msdn.microsoft.com/en-us/powershell/dsc/configdata) e quindi i team operativi possono identificare e modificare gli ambienti in modo più semplice, senza l'intervento di uno sviluppatore. 

## DSC (Desired State Configuration) in ambienti locali e non locali ##

È possibile usare DSC per gestire le distribuzioni sia locali che non locali. Per le soluzioni locali, DSC (Desired State Configuration) ha un [server di pull](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) che è possibile usare per centralizzare la gestione dei computer e creare report sul loro stato. Per le soluzioni cloud, è possibile usare DSC (Desired State Configuration) ovunque sia possibile usare Windows. Ci sono anche offerte specifiche di Azure basate su DSC, ad esempio [Automazione di Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), che consente di centralizzare la creazione di report di DSC. 

## DSC e compatibilità ##

Anche se la soluzione DSC è stata introdotta in Windows Server 2012 R2, è disponibile per sistemi operativi di livello inferiore attraverso il pacchetto Windows Management Framework (WMF). Altre informazioni su WMF sono disponibili nella [home page di PowerShell](https://msdn.microsoft.com/en-us/powershell/). 

È possibile usare DSC anche per gestire Linux. Per altre informazioni, vedere [Introduzione a DSC per Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).




<!--HONumber=Jun16_HO4-->


