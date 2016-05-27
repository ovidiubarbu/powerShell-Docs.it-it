---
title:   Panoramica di Windows PowerShell DSC (Desired State Configuration) 
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Panoramica di Windows PowerShell DSC (Desired State Configuration) 

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Questo argomento descrive la funzionalità Windows PowerShell DSC (Desired State Configuration) in Windows PowerShell. L'argomento offre una panoramica di DSC e indicazioni sulle risorse della documentazione utili per comprendere e usare DSC.

## Descrizione delle funzionalità
DSC è una nuova piattaforma di gestione di Windows PowerShell che consente di distribuire e gestire dati di configurazione per i servizi software, nonché di gestire l'ambiente in cui vengono eseguiti questi servizi.

DSC fornisce un set di estensioni del linguaggio di Windows PowerShell, nuovi cmdlet di Windows PowerShell e risorse che è possibile usare per specificare in modo dichiarativo come si vuole configurare l'ambiente software. Consente inoltre di mantenere e gestire le configurazioni esistenti.

## Applicazioni pratiche
Di seguito sono illustrati alcuni scenari di esempio in cui è possibile usare le risorse DSC predefinite per configurare e gestire un insieme di computer (noti anche come nodi di destinazione) in modo automatico:

* Abilitazione o disabilitazione di funzionalità e ruoli del server
* Gestione delle impostazioni del Registro di sistema
* Gestione di file e directory
* Avvio, arresto e gestione di processi e servizi
* Gestione di gruppi e account utente
* Distribuzione di nuovo software
* Gestione di variabili di ambiente
* Esecuzione di script di Windows PowerShell
* Correzione di una configurazione che si discosta rispetto allo stato desiderato
* Individuazione dello stato di configurazione effettivo di un nodo specifico

## Concetti chiave
DSC è una piattaforma dichiarativa usata per la configurazione, la distribuzione e la gestione dei sistemi. È costituita da tre componenti principali:

* Le [configurazioni](configurations.md) sono script di PowerShell dichiarativi che definiscono e configurano le istanze delle risorse. Quando viene eseguita la configurazione, DSC (e le risorse chiamate dalla configurazione) si assicurano semplicemente che il risultato sia quello desiderato, facendo in modo che lo stato del sistema corrisponda a quanto definito dalla configurazione. Le configurazioni DSC sono inoltre idempotenti: Gestione configurazione locale continua a garantire che i computer siano configurati in base a qualsiasi stato dichiarato dalla configurazione.
* Le risorse sono i blocchi predefiniti essenziali di DSC, scritti per modellare i diversi componenti di un sottosistema e implementare il flusso di controllo degli stati che cambiano. Le risorse si trovano all'interno dei moduli di PowerShell e possono essere scritte per modellare un elemento generico, come un file o un processo di Windows, o un elemento specifico, come un server IIS o una VM in esecuzione in Azure.
* Gestione configurazione locale è il motore usato da DSC per semplificare l'interazione tra risorse e configurazioni. Gestione configurazione locale esegue regolarmente il polling del sistema usando il flusso di controllo implementato dalle risorse per garantire che lo stato definito da una configurazione venga mantenuto. Se lo stato del sistema non è quello previsto, Gestione configurazione locale usa più logica all'interno delle risorse per ottenere il risultato desiderato, in base alla dichiarazione di configurazione. 

DSC include anche una serie di nuove parole chiave del linguaggio, nonché nuovi cmdlet e strumenti che consentono la creazione di configurazioni, offrono supporto per la creazione di risorse DSC e consentono di richiamare le configurazioni e gestire la funzione Gestione configurazione locale. Molti di questi cmdlet sono disponibili in Windows 8.1 come parte del modulo PSDesiredStateConfiguration, inclusi `Start-DscConfiguration`, `Set-DscLocalConfigurationManager` e `Get-DscResource`. xDscResourceDesigner (disponibile in [PowerShell Gallery](https://www.powershellgallery.com/packages/xDSCResourceDesigner/)) è una raccolta di cmdlet che semplificano lo sviluppo di risorse DSC.

## Vedere anche
* [Configurazioni DSC](configurations.md)
* [Risorse DSC](resources.md)
* [Configurazione di Gestione configurazione locale](metaConfig.md)



<!--HONumber=May16_HO3-->


