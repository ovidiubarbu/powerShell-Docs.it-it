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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366960"
---
# <a name="updatable-help-overview"></a>Panoramica della Guida aggiornabile

Questo documento fornisce un'introduzione di base alla progettazione e al funzionamento della funzionalità della Guida aggiornabile di Windows PowerShell. È progettato per gli autori di moduli e altri che forniscono agli utenti argomenti della Guida di Windows PowerShell.

## <a name="introduction"></a>Introduzione

Gli argomenti della Guida di Windows PowerShell sono parte integrante dell'esperienza di Windows PowerShell. Come i moduli di Windows PowerShell, gli argomenti della guida vengono aggiornati e migliorati continuamente dagli autori e dai contributi della community degli utenti di Windows PowerShell.

La funzionalità della *Guida aggiornabile* , introdotta in Windows PowerShell 3,0, garantisce agli utenti le versioni più recenti degli argomenti della Guida al prompt dei comandi, anche per i comandi incorporati di Windows PowerShell, senza scaricare nuovi moduli o eseguire Windows Update . La guida aggiornabile semplifica l'aggiornamento fornendo cmdlet che scaricano le versioni più recenti degli argomenti della guida da Internet e le installano nelle sottodirectory corrette del computer locale dell'utente. Anche gli utenti protetti da firewall possono usare i nuovi cmdlet per ottenere la guida aggiornata da una condivisione file interna.

La guida aggiornabile è completamente supportata da tutti i moduli di Windows PowerShell in Windows® 8 e Windows Server® 2012 e le sue funzionalità sono disponibili per tutti gli autori dei moduli di Windows PowerShell. La guida aggiornabile supporta solo file della Guida basati su XML. Non supporta la guida basata su commenti.

La guida aggiornabile include le funzionalità seguenti.

- Il cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) , che determina se gli utenti hanno i file della guida più recenti per un modulo e, in caso contrario, Scarica i file della guida più recenti da Internet, li decomprime e li installa nelle sottodirectory dei moduli corretti nel computer dell'utente.
  Gli utenti possono usare il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) per visualizzare immediatamente gli argomenti della guida appena installati.
  Non è necessario riavviare PowerShell.

- Il cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) , che Scarica i file della guida più recenti da Internet e li salva in una directory file System. Gli utenti possono usare il cmdlet `Update-Help` per ottenere i file della guida dalla directory file system e decomprimerli e installarli nelle sottodirectory dei moduli nel computer dell'utente. Il cmdlet `Save-Help` è progettato per gli utenti che hanno accesso a Internet limitato o senza accesso a Internet e per le aziende che preferiscono limitare l'accesso a Internet.

- **Guida per un modulo**. I file della Guida per un modulo vengono gestiti e recapitati come unità, in modo che gli utenti possano ottenere tutti i file della Guida per i moduli utilizzati. La guida aggiornabile è supportata solo per i moduli, non per gli snap-in di Windows PowerShell.

- **Supporto della versione**. La guida aggiornabile usa le quattro posizioni standard (N1. N2. N3. N4) numeri di versione. La guida aggiornabile Scarica i file della guida quando il numero di versione dei file della guida nel computer dell'utente (o nella directory `Save-Help`) è inferiore al numero di versione dei file della guida nella posizione Internet.

- **Supporto multilingue**. La guida aggiornabile supporta file della guida del modulo in più impostazioni cultura dell'interfaccia utente. I nomi file della Guida aggiornabili includono codici di lingua standard, ad esempio "en-US" e "ja-JP", e i cmdlet `Update-Help` e `Save-Help` posizionano i file della Guida in sottodirectory specifiche della lingua della directory del modulo.

- **Guida generata automaticamente**. Il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) Visualizza la Guida di base per i comandi che non contengono file della guida. La guida generata automaticamente include la sintassi dei comandi e gli alias e le istruzioni per l'uso della guida e della Guida aggiornabile.

- **Guida online migliorata**. Un accesso semplice alla guida online non richiede più file della guida. Il parametro **online** del cmdlet `Get-Help` ora ottiene l'URL di un argomento della Guida in linea dal valore della proprietà **HelpUri** di qualsiasi comando, se non riesce a trovare l'URL della Guida in linea in un file della guida. Per popolare la proprietà **HelpUri** , è possibile aggiungere un attributo **HelpUri** al codice di cmdlet, funzioni e comandi CIM oppure utilizzare **. Collegare** la direttiva della Guida basata su commenti in flussi di lavoro e script.

  Per rendere aggiornabili i file della guida, i moduli di Windows PowerShell in Windows 8 e Windows Server vNext non sono disponibili con i file della guida. Gli utenti possono utilizzare la guida aggiornabile per installare i file della guida e aggiornarli. Gli autori di altri moduli possono includere file della guida nei moduli o ometterli. Il supporto per la guida aggiornabile è facoltativo, ma consigliato.
