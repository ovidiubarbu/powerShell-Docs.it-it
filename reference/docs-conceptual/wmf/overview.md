---
ms.date: 04/19/2019
keywords: wmf,powershell,installazione
title: Windows Management Framework (WMF)
ms.openlocfilehash: d581370fd602e03c86aa549eb8b273ff4d01b4e5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/19/2019
ms.locfileid: "71147911"
---
# <a name="windows-management-framework"></a>Windows Management Framework

Windows Management Framework (WMF) offre un'interfaccia di gestione coerente per Windows. WMF offre un modo semplice per gestire diverse versioni di client Windows e Windows Server. I pacchetti di installazione WMF contengono aggiornamenti alla funzionalità di gestione e sono disponibili per le versioni precedenti di Windows.

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

- [WMF 5.1](whats-new/release-notes.md#wmf-51-changes)
- [WMF 5.0](whats-new/release-notes.md#wmf-50-changes)
- [WMF 4.0](https://download.microsoft.com/download/3/D/6/3D61D262-8549-4769-A660-230B67E15B25/Windows%20Management%20Framework%204%200%20Release%20Notes.docx)
- [WMF 3.0](https://download.microsoft.com/download/E/7/6/E76850B8-DA6E-4FF5-8CCE-A24FC513FD16/WMF%203%20Release%20Notes.docx)

## <a name="wmf-availability-across-windows-operating-systems"></a>Disponibilità di WMF tra i sistemi operativi Windows

|        Versione del sistema operativo         | [WMF 5.1][]  | WMF 5.0<br>*Supporto scaduto* | [WMF 4.0][]  | [WMF 3.0][]  | [WMF 2.0][]  |
| --------------------------------------- | ------------ | --------------------------- | ------------ | ------------ | ------------ |
| Windows Server 2019                     | Incluso |                             |              |              |              |
| Windows Server 2016                     | Incluso |                             |              |              |              |
| Windows 10                              | Incluso | Incluso                |              |              |              |
| Windows Server 2012 R2                  | Sì          | Sì                         | Incluso |              |              |
| Windows 8.1                             | Sì          | Sì                         | Incluso |              |              |
| Windows Server 2012                     | Sì          | Sì                         | Sì          | Incluso |              |
| Windows 8<br>*Supporto scaduto*           |              |                             |              | Incluso |              |
| Windows Server 2008 R2 SP1              | Sì          | Sì                         | Sì          | Sì          | Incluso |
| Windows 7 SP1                           | Sì          | Sì                         | Sì          | Sì          | Incluso |
| Windows Server 2008 SP2                 |              |                             |              | Sì          | Sì          |
| Windows Vista<br>*Supporto scaduto*       |              |                             |              |              | Sì          |
| Windows Server 2003<br>*Supporto scaduto* |              |                             |              |              | Sì          |
| Windows XP<br>*Supporto scaduto*          |              |                             |              | Sì          | Sì          |

- **Incluso**: le funzionalità della versione specificata di WMF sono state rilasciate nella versione indicata di Windows Client o di Windows Server.
- **Supporto scaduto**: questi prodotti non sono più supportati da Microsoft. È necessario eseguire l'aggiornamento a una nuova versione supportata. Per altre informazioni, vedere la pagina [Criteri relativi al ciclo di vita Microsoft][].

> [!NOTE]
> Il programma di installazione di WMF 5.0 non è più disponibile o supportato. È stato sostituito da WMF 5.1.

[Criteri relativi al ciclo di vita Microsoft]: https://support.microsoft.com/lifecycle
[WMF 5.1]: https://aka.ms/wmf51download
[WMF 4.0]: https://aka.ms/wmf4download
[WMF 3.0]: https://aka.ms/wmf3download
[WMF 2.0]: https://aka.ms/wmf2download
