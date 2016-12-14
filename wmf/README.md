---
title: Windows Management Framework (WMF)
ms.date: 2016-05-16
keywords: PowerShell, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
ms.openlocfilehash: eacd33d2a0a92977a3990132e23eef9871a7f0dc
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) è un meccanismo di distribuzione che offre un'interfaccia di gestione coerente delle varie caratteristiche di Windows e Windows Server.
Con l'installazione di WMF, i clienti ottengono un modo semplice per l'interazione tra diversi sistemi operativi nel proprio ambiente.
WMF rende disponibili gli aggiornamenti alle funzionalità di gestione, in una determinata versione di Windows e Windows Server, disponibile per l'installazione nelle versioni precedenti (in genere 2 versioni precedenti) di Windows e Windows Server.

L'installazione di WMF aggiunge e/o aggiorna le funzionalità seguenti:

- Windows PowerShell
- Windows PowerShell Desired State Configuration (DSC)
- Windows PowerShell Integrated Script Environment (ISE)
- Gestione remota Windows (WinRM)
- Strumentazione gestione Windows (WMI)
- Servizi Web di Windows PowerShell (estensione IIS OData di gestione)
- Registrazione inventario software (SIL)
- Provider CIM di gestione del server

## <a name="wmf-release-notes"></a>Note sulla versione di WMF
Per informazioni sui vari miglioramenti in PowerShell e altri componenti di una determinata versione di WMF, consultare i collegamenti seguenti per rivedere le note sulla versione:


- [WMF 5.1 (Preview)](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)


## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilità di WMF tra i sistemi operativi Windows

>TODO: Aggiungere collegamenti a WMF DLC nell'intestazione di colonna

| Versione del sistema operativo | [WMF 5.1 Preview*]() | [WMF 5.0]() | [WMF 4.0]() |  [WMF 3.0]() | [WMF (2.0)]() |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Incluso* | Incluso* |  |  |  |
| Windows 10 | Incluso* | Incluso*  | | | |  
| Windows Server 2012 R2| ?? | Sì | Incluso |  |  |
| Windows 8.1 | ?? | Sì |  Incluso |  |  |
| Windows Server 2012 | ?? | Sì | Sì |  Incluso | |
| Windows 8 |  |  |  | Incluso | |
| Windows Server 2008 R2 SP1 | ?? | Sì | Sì |  Sì| Incluso |
| Windows 7 SP1  | ?? | Sì | Sì | Sì | Incluso |
| Windows Server 2008 SP2 | | | | Sì | Sì |
| Windows Vista | | | | | Sì |
| Windows Server 2003| | | |  | Sì |
| Windows XP | | | |  | Sì |

>TODO: Spiegare * nella tabella precedente
