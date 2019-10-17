---
ms.date: 10/11/2019
keywords: dsc,powershell,configurazione,installazione
title: Panoramica di DSC (Desired State Configuration) per decision maker
ms.openlocfilehash: 271ec04035feb17e932acd0ac80f32213a4e018b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352129"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Panoramica di DSC (Desired State Configuration) per decision maker

Questo documento descrive i vantaggi dell'uso di PowerShell Desired State Configuration (DSC) per le aziende, non è una guida tecnica.

## <a name="what-is-dsc"></a>Che cos'è DSC?

PowerShell DSC è una piattaforma di gestione delle configurazioni integrata in Windows e basata su standard aperti. DSC è sufficientemente flessibile per funzionare in modo affidabile e coerente in ogni fase del ciclo di distribuzione (sviluppo, test, pre-produzione, produzione), nonché quando viene applicata scalabilità orizzontale.

DSC è incentrato sulle [configurazioni](../configurations/configurations.md). Una configurazione è uno script PowerShell che descrive un ambiente costituito da computer o nodi con caratteristiche specifiche. Queste caratteristiche possono essere semplici, ad esempio per abilitare una funzionalità specifica di Windows, o complesse, ad esempio per la distribuzione di SharePoint.

In DSC sono integrate funzionalità di monitoraggio e creazione di report. Se un sistema non è più conforme, DSC può generare un avviso ed eseguire operazioni per correggere il sistema.

## <a name="benefits-of-using-dsc"></a>Vantaggi dell'uso di DSC

La progettazione delle configurazioni ne semplifica la lettura, l'archiviazione e l'aggiornamento. Le configurazioni dichiarano lo stato dei dispositivi di destinazione, senza che sia necessario scrivere istruzioni su come impostare lo stato ai dispositivi. Questi fattori riducono i costi per l'apprendimento, l'adozione, l'implementazione e la gestione della configurazione tramite DSC.

La creazione di configurazioni comporta l'acquisizione di passaggi di distribuzione complessi come **unica origine di riferimento** in un'unica posizione. Le configurazioni rendono le distribuzioni ripetute di un set specifico di computer meno soggette a errori. Le distribuzioni sono anche più veloci e affidabili, il che significa gestire rapidamente distribuzioni complesse.

Le configurazioni sono condivisibili tramite [PowerShell Gallery](https://powershellgallery.com). È possibile che siano già presenti scenari comuni e procedure consigliate per il lavoro che si deve eseguire.

## <a name="dsc-and-devops"></a>DSC e DevOps

La soluzione DSC è stata progettata tenendo in considerazione [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx). Si tratta di una combinazione di persone, processi e strumenti che supportano la distribuzione e l'iterazione rapide, incentrate sull'offrire valore agli utenti finali, sia interni che esterni. Un'unica configurazione che definisce un ambiente significa che gli sviluppatori possono codificare i requisiti in una configurazione e verificare tale configurazione nel controllo del codice sorgente. I team operativi possono quindi distribuire il codice senza dover eseguire processi manuali soggetti a errori.

Le configurazioni sono [basate sui dati](../configurations/configData.md). I dati definiti consentono ai membri del team operativo di identificare e modificare facilmente gli ambienti, senza l'intervento di uno sviluppatore.

## <a name="dsc-on-premises-and-off-premises"></a>DSC locale e non locale

Con DSC è possibile gestire distribuzioni sia locali sia non locali. Per le soluzioni locali, DSC usa un [server di pull](../pull-server/pullServer.md) per centralizzare la gestione dei computer e creare report sul loro stato. Per le soluzioni cloud non locali, è possibile usare DSC in qualsiasi ambiente in cui Windows è utilizzabile.
Sono disponibili offerte specifiche di Azure basate su DSC, ad esempio [Automazione di Azure](https://azure.microsoft.com/en-us/documentation/services/automation/) che centralizza la creazione di report DSC.

## <a name="dsc-and-compatibility"></a>DSC e compatibilità

La soluzione DSC è stata introdotta in Windows Server 2012 R2, ma è disponibile per i sistemi operativi di versione precedente tramite Windows Management Framework. Per altre informazioni su Windows Management Framework, vedere [Windows Management Framework](/powershell/scripting/wmf/overview).

È possibile usare DSC per gestire Linux. Per altre informazioni, vedere [Introduzione a DSC per Linux](../getting-started/lnxGettingStarted.md).
