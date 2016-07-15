---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: FILE LEGGIMI
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d4e46653ff31ea7cda71f1c92b12ce5f2811b8a7
ms.openlocfilehash: e24757029fd3ac9a70f710a7a755c35f440f087c

---

# Just Enough Administration
Just Enough Administration (JEA) è una tecnologia di protezione che consente l'amministrazione delegata per qualsiasi elemento che possa essere gestito con PowerShell.
Con JEA, è possibile:
- **Ridurre il numero di amministratori dei computer** sfruttando gli account virtuali che eseguono azioni con privilegi per conto degli utenti normali.
- **Limitare le operazioni consentite agli utenti** specificando quali cmdlet, funzioni e comandi esterni possono eseguire.
- **Seguire da vicino le attività degli utenti** e capirle meglio grazie a trascrizioni "over-the-shoulder" che indicano esattamente quali comandi eseguono gli utenti durante una sessione.

**Perché tutto questo è importante?**  
Si consideri uno scenario comune in cui i server DNS condividono il percorso con i controller di dominio Active Directory.
Gli amministratori DNS devono avere privilegi di amministratore locale per risolvere i problemi del server DNS, ma per farlo è necessario che siano membri del gruppo di sicurezza con privilegi elevati "Domain Admins".
Con questo approccio gli amministratori DNS saranno in grado di controllare l'intero dominio e di accedere a tutte le risorse del computer.

Se JEA è installato, è possibile configurare un ruolo per gli amministratori DNS che consenta l'accesso a tutti i comandi necessari per svolgere il proprio lavoro, ma niente di più.
Ciò significa che è possibile specificare l'accesso appropriato per ripristinare una cache DNS danneggiata senza concedere inavvertitamente diritti per usare Active Directory, sfogliare il file system o eseguire script potenzialmente pericolosi.
In più, quando la sessione JEA è configurata per l'uso di account virtuali monouso con privilegi, gli amministratori DNS possono connettersi al server usando credenziali *non privilegiate* ed eseguire comunque comandi con privilegi.

## Disponibilità
La soluzione JEA è stata sviluppata in parallelo a Windows Server 2016 ed è disponibile nelle versioni precedenti di Windows con gli aggiornamenti di Windows Management Framework.
La versione corrente di JEA è disponibile nelle piattaforme seguenti:

**Windows Server**
- Windows Server 2016 Technical Preview 4 e versioni successive
- Windows Server 2012 R2, 2012 e 2008 R2\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato

**Client Windows**
- Windows 10 con l'aggiornamento di novembre (1511) installato
- Windows 8.1, 8 e 7\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato

\* Il supporto per gli account virtuali nelle sessioni JEA attualmente non è disponibile in Windows Server 2008 R2 o Windows 7.


## Esplorare la guida all'esperienza
A questo punto si può iniziare a imparare come creare, distribuire e usare il proprio endpoint JEA.

Questa guida consente di iniziare rapidamente con un endpoint JEA predefinito per avere un'idea di come sarà l'esperienza per l'utente finale, quindi spiega come ricreare l'endpoint da zero illustrando concetti come le configurazioni di sessione e le capacità del ruolo.

1.  [Introduzione](introduction.md)   
Brevi considerazioni sul perché è opportuno prendere in considerazione JEA

2.  [Prerequisiti](prerequisites.md)  
Viene illustrato come configurare l'ambiente

3.  [Uso di JEA](using-jea.md)  
Informazioni preliminari sull'esperienza dell'operatore con JEA

4.  [Ricreare la demo](remake-the-demo-endpoint.md)  
Creare una configurazione di sessione JEA da zero

5.  [Capacità del ruolo](role-capabilities.md)  
Informazioni su come personalizzare le funzionalità JEA con i file di capacità del ruolo

6.  [End-to-end - Active Directory](end-to-end---active-directory.md)  
Creare un endpoint completamente nuovo per la gestione di Active Directory

7.  [Distribuzione e manutenzione con più computer](multi-machine-deployment-and-maintenance.md)  
Scoprire in che modo le modalità di distribuzione e creazione cambiano con le dimensioni

8.  [Creazione di report per JEA](reporting-on-jea.md)  
Informazioni su come controllare tutte le azioni e l'infrastruttura di JEA e creare i relativi report

9.  Appendici
  - [Concetti principali usati in questa guida](key-concepts-used-throughout-this-guide.md)  
  -  [Creazione di un controller di dominio](creating-a-domain-controller.md)  
  -  [Blacklist](on-blacklisting.md)  
  -  [Considerazioni per la limitazione dei comandi](considerations-when-limiting-commands.md)  
  -  [Problemi comuni delle capacità del ruolo](common-role-capability-pitfalls.md)

## Iniziare a creare i propri endpoint JEA
È facile creare un endpoint JEA: è sufficiente un sistema abilitato per JEA e un editor di testo, ad esempio PowerShell ISE.
Un suggerimento utile per iniziare è creare i file scheletro usando `New-PSRoleCapabilityFile -Path <path>` e `New-PSSessionCapabilityFile -Path <Path>` senza altri argomenti.
I file scheletro contengono tutti i campi di configurazione applicabili oltre a commenti utili che spiegano per cosa può essere usato ogni campo.

Per semplificare ulteriormente la creazione degli endpoint JEA, vedere il [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) che offre un'interfaccia utente grafica con cui è possibile creare file di configurazione di sessione e file di capacità del ruolo.
È supportata anche la generazione di capacità del ruolo in base ai registri di PowerShell per iniziare a gestire i comandi eseguiti regolarmente dagli utenti per svolgere le proprie attività.




<!--HONumber=Jul16_HO1-->


