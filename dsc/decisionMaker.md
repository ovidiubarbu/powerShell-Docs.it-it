---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Panoramica di DSC (Desired State Configuration) per decision maker
ms.openlocfilehash: 7c36aa5fadeab8bcb381f316288d102b5ce402e2
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339838"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Panoramica di DSC (Desired State Configuration) per decision maker

Questo documento descrive i vantaggi dell'uso di Windows PowerShell DSC (Desired State Configuration) per le aziende. Non si tratta di una guida tecnica.

## <a name="what-is-desired-state-configuration"></a>Che cos'è DSC (Desired State Configuration)?

PowerShell Desired State Configuration è una piattaforma di gestione delle configurazioni integrata in Windows e basata su standard aperti. DSC è sufficientemente flessibile per funzionare in modo affidabile e coerente in ogni fase del ciclo di distribuzione (sviluppo, test, pre-produzione, produzione), nonché quando viene applicata scalabilità orizzontale.

DSC è incentrato sulle [configurazioni](configurations.md).
Una configurazione è un documento facile da leggere che descrive un ambiente costituito da computer ("nodi") con caratteristiche specifiche.
Queste caratteristiche possono essere semplici, ad esempio per abilitare una funzionalità specifica di Windows, o complesse, ad esempio per la distribuzione di SharePoint.

In DSC sono anche integrate funzionalità di monitoraggio e creazione di report.
Se un sistema non è più conforme, DSC può generare un avviso ed eseguire operazioni per correggere il sistema.

## <a name="benefits-of-using-desired-state-configuration"></a>Vantaggi dell'uso di DSC (Desired State Configuration)

Le configurazioni sono progettate per essere facili da leggere, archiviare e aggiornare.
Le configurazioni dichiarano lo stato desiderato per i dispositivi di destinazione, senza che sia necessario scrivere istruzioni su come impostare tale stato.
In questo modo, DSC semplifica notevolmente l'apprendimento, l'adozione, l'implementazione e la gestione della configurazione.

La creazione di configurazioni comporta l'acquisizione di passaggi di distribuzione complessi come "unica origine di dati reali" in un'unica posizione.
In questo modo, le distribuzioni ripetute di un set specifico di computer sono molto meno soggette a errori.
Migliorare la velocità e l'affidabilità delle distribuzioni consente inoltre di gestire con efficacia distribuzioni complesse.

Le configurazioni possono anche essere condivise tramite [PowerShell Gallery](https://powershellgallery.com) e questo significa che potrebbero essere già disponibili scenari comuni e procedure consigliate per specifiche esigenze.


## <a name="desired-state-configuration-and-devops"></a>DSC (Desired State Configuration) e DevOps

DSC è stato progettato pensando a [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx), una combinazione di persone, processi e strumenti che supportano la distribuzione e l'iterazione rapide focalizzata sull'offerta di valore agli utenti finali, sia interni che esterni.
Con una singola configurazione che definisce un ambiente, gli sviluppatori possono codificare i propri requisiti in una configurazione, archiviare la configurazione nel controllo del codice sorgente e i team operativi possono facilmente distribuire il codice senza dover eseguire processi manuali soggetti a errori.

Le configurazioni sono anche [basate sui dati](configData.md) e consentono ai membri del team operativo di identificare e modificare facilmente gli ambienti, senza l'intervento di uno sviluppatore.

## <a name="desired-state-configuration-on--and-off-premises"></a>DSC (Desired State Configuration) in ambienti locali e non locali

È possibile usare DSC per gestire le distribuzioni sia locali che non locali.
Per le soluzioni locali, DSC ha un [server di pull](pullServer.md) che è possibile usare per centralizzare la gestione dei computer e creare report sul loro stato.
Per le soluzioni cloud, è possibile usare DSC ovunque sia possibile usare Windows.
Ci sono anche offerte specifiche di Azure basate su DSC (Desired State Configuration), ad esempio [Automazione di Azure](https://azure.microsoft.com/en-us/documentation/services/automation/), che consente di centralizzare la creazione di report di DSC.

## <a name="dsc-and-compatibility"></a>DSC e compatibilità

Anche se la soluzione DSC è stata introdotta in Windows Server 2012 R2, è disponibile per sistemi operativi di livello inferiore tramite il pacchetto Windows Management Framework (WMF).
Altre informazioni su WMF sono disponibili nella [home page di PowerShell](/powershell/).

È possibile usare DSC anche per gestire Linux. Per altre informazioni, vedere [Introduzione a DSC per Linux](lnxGettingStarted.md).
