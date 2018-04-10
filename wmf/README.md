---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
title: Windows Management Framework (WMF)
ms.openlocfilehash: 715ac6fe5df47066415a65d91a0982fd7070a426
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
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

- [WMF 5.1](5.1/release-notes.md)
- [WMF 5.0](5.0/releasenotes.md)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilità di WMF tra i sistemi operativi Windows

| Versione del sistema operativo | [WMF 5.1](https://aka.ms/wmf51download) | [WMF 5.0](https://aka.ms/wmf5download) | [WMF 4.0](https://aka.ms/wmf4download) |  [WMF 3.0](https://aka.ms/wmf3download) | [WMF 2.0](https://aka.ms/wmf2download) |
| ------------------------ | ----------- | ----------- | ----------- | ------------ |  ------------- |
| Windows Server 2016 | Incluso |  |  |  |  |
| Windows 10 | Incluso | Incluso  | | | |
| Windows Server 2012 R2| Sì | Sì | Incluso |  |  |
| Windows 8.1 | Sì | Sì |  Incluso |  |  |
| Windows Server 2012 | Sì | Sì | Sì |  Incluso | |
| Windows 8 |  |  |  | Incluso | |
| Windows Server 2008 R2 SP1 | Sì | Sì | Sì |  Sì| Incluso |
| Windows 7 SP1  | Sì | Sì | Sì | Sì | Incluso |
| Windows Server 2008 SP2 | | | | Sì | Sì |
| Windows Vista | | | | | Sì |
| Windows Server 2003| | | |  | Sì |
| Windows XP | | | |  | Sì |

**"Incluso"**: le funzionalità di `specified WMF` sono state rilasciate nella versione indicata di Windows e Windows Server.
Di conseguenza, `specified WMF` non deve essere installato nelle versioni indicate del sistema operativo.