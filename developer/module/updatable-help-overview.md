---
title: Panoramica della Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 03/22/2012
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
applies_to:
- Windows PowerShell 3.0
ms.assetid: 3f7388a9-9fa8-42bc-b294-538c9a01e30a
caps.latest.revision: 12
ms.openlocfilehash: f2dfb9642ba2dde38124142b659b425bbbb00f37
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057604"
---
# <a name="updatable-help-overview"></a>Panoramica della Guida aggiornabile

Questo documento fornisce un'introduzione di base per la progettazione e il funzionamento della funzionalità Guida aggiornabile di Windows PowerShell. È progettato per gli autori di moduli e altri utenti che agli utenti di inviare argomenti della Guida di Windows PowerShell.

## <a name="introduction"></a>Introduzione

Gli argomenti della Guida di Windows PowerShell sono parte integrante dell'esperienza di Windows PowerShell. Ad esempio moduli di Windows PowerShell, gli argomenti della Guida vengono continuamente aggiornati e migliorati per gli autori e per i contributi della community di utenti di Windows PowerShell.

Il *la Guida aggiornabile* funzionalità introdotta in Windows PowerShell 3.0, assicura che gli utenti abbiano le versioni più recenti degli argomenti della Guida al prompt dei comandi, anche per i comandi incorporati di Windows PowerShell, senza scaricare nuovi moduli o esegue l'aggiornamento di Windows. La Guida aggiornabile semplifica l'aggiornamento, fornendo cmdlet che scaricare le versioni più recenti degli argomenti della Guida da Internet e installarli nelle sottodirectory corretta nel computer locale dell'utente. Anche gli utenti che sono protetti da firewall possono usare i nuovi cmdlet per ottenere della Guida aggiornati da una condivisione file interna.

La Guida aggiornabile è completamente supportata da tutti i moduli di Windows PowerShell in Windows® 8 e Windows Server® 2012 e le relative funzionalità sono disponibili per tutti gli autori di moduli di Windows PowerShell. La Guida aggiornabile supporta solo i file della Guida basata su XML. Non supporta la Guida basata sui commenti.

La Guida aggiornabile comprende le funzionalità seguenti.

- Il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet, che determina se gli utenti hanno la Guida più recente nei file per un modulo e, in caso contrario, scarica i file della Guida più recenti da Internet, li decomprime e li installa nella sottodirectory del modulo corretto di computer dell'utente.
  Gli utenti possono usare la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet per visualizzare gli argomenti della Guida appena installato immediatamente.
  Essi non è necessario riavviare PowerShell.

- Il [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet, che scarica la Guida più recente di file da Internet e li salva nella directory del file system. Gli utenti possono usare il `Update-Help` cmdlet per ottenere i file della Guida dalla directory del file system e decomprimere e installarle nella sottodirectory del modulo nel computer dell'utente. Il `Save-Help` cmdlet è progettato per gli utenti con o senza accesso a Internet e per le aziende che preferiscono limitare l'accesso a Internet.

- **Argomenti della Guida per un modulo**. I file della Guida per un modulo sono gestiti e distribuiti come un'unità, in modo che gli utenti possono ottenere tutti i file della Guida per i moduli che usano. La Guida aggiornabile è supportata solo per i moduli, non per snap-in Windows PowerShell.

- **Supporto della versione**. La Guida aggiornabile utilizza standard quattro posizioni (N1. N2. N3. Numeri di versione n4). La Guida aggiornabile Scarica file della Guida quando il numero di versione della Guida del file nel computer dell'utente (o nel `Save-Help` directory) è inferiore al numero di versione dei file della Guida in corrispondenza della posizione di Internet.

- **Supporto per più linguaggi**. La Guida aggiornabile supporta i file della Guida del modulo in più impostazioni cultura dell'interfaccia utente. La Guida aggiornabile nomi file includono codici standard del linguaggio, ad esempio "en-US" e "ja-JP" e il `Update-Help` e `Save-Help` i cmdlet di inserire i file della Guida nella sottodirectory specifica del linguaggio della directory del modulo.

- **La Guida generata automaticamente**. Il [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet Visualizza le informazioni di base per i comandi che non sono disponibili file della Guida. La Guida generata automaticamente include la sintassi del comando e gli alias e le istruzioni per l'uso della Guida in linea e la Guida aggiornabile.

- **Migliorata la Guida in linea**. Accedere facilmente alla Guida in linea non richiede più i file della Guida. Il **Online** parametro delle `Get-Help` cmdlet ora Ottiene l'URL dell'argomento della Guida online dal valore della **HelpUri** proprietà di qualsiasi comando, se non viene trovata l'URL della Guida online di un file della Guida. È possibile popolare la **HelpUri** proprietà mediante l'aggiunta di un **HelpUri** attributo per il codice del cmdlet, funzioni e i comandi CIM, o tramite il **. Collegamento** direttiva della Guida basata sui commenti negli script e flussi di lavoro.

  Per rendere i file della Guida aggiornabile, i moduli di Windows PowerShell in Windows 8 e Windows Server vNext non vengono forniti con i file della Guida. Gli utenti possono usare la Guida aggiornabile per installare i file della Guida e aggiornarli. Gli autori di altri moduli possono includono file della Guida nei moduli o omesse. Supporto per la Guida aggiornabile è facoltativo ma consigliato.
