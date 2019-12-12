---
title: Funzionamento della Guida aggiornabile | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367080"
---
# <a name="how-updatable-help-works"></a>Come funziona la Guida aggiornabile

In questo argomento viene illustrato il modo in cui la guida aggiornabile elabora il file XML e i file CAB HelpInfo per ogni modulo e installa la guida aggiornata per gli utenti.

## <a name="the-update-help-process"></a>Il processo Update-Help

Nell'elenco seguente vengono descritte le azioni del cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) quando un utente esegue un comando per aggiornare i file della Guida per un modulo in una particolare lingua dell'interfaccia utente.

1. `Update-Help` ottiene il file XML HelpInfo remoto dal percorso specificato dal valore della chiave **HelpInfoURI** nel manifesto del modulo e convalida il file rispetto allo schema. Per visualizzare lo schema, vedere [HELPINFO XML Schema](./helpinfo-xml-schema.md). Quindi `Update-Help` Cerca un file XML HelpInfo locale per il modulo nella directory del modulo nel computer dell'utente.

2. `Update-Help` confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo locali e remoti per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non è presente un file XML HelpInfo locale per il modulo, `Update-Help` prepara il download dei nuovi file della guida.

3. `Update-Help` seleziona il file CAB per il modulo dal percorso specificato dall'elemento **HelpContentUri** nel file XML HELPINFO remoto. Usa il nome del modulo, il GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Update-Help` Scarica il file CAB, lo decomprime, convalida i file di contenuto della guida e salva i file di contenuto della guida nella sottodirectory specifica del linguaggio della directory dei moduli nel computer dell'utente.

5. `Update-Help` crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa solo gli elementi per il file CAB installato. Quindi Salva il file XML HelpInfo locale nella directory del modulo e conclude l'aggiornamento.

## <a name="the-save-help-process"></a>Il processo Save-Help

Nell'elenco seguente vengono descritte le azioni dei cmdlet [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) quando un utente esegue i comandi per aggiornare i file della Guida in una condivisione file e quindi utilizza tali file per aggiornare i file della guida nel computer dell'utente.

Il cmdlet `Save-Help` esegue le azioni seguenti in risposta a un comando per salvare i file della Guida per un modulo in una condivisione file specificata dal parametro **DestinationPath** .

1. `Save-Help` ottiene il file XML HelpInfo remoto dal percorso specificato dal valore della chiave **HelpInfoURI** nel manifesto del modulo e convalida il file rispetto allo schema. Per visualizzare lo schema, vedere [HELPINFO XML Schema](./helpinfo-xml-schema.md). Quindi `Save-Help` Cerca un file XML HelpInfo locale nella directory specificata dal parametro **DestinationPath** nel comando `Save-Help`.

2. `Save-Help` confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo locali e remoti per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non è presente un file XML HelpInfo locale per il modulo nella directory **DestinationPath** , `Save-Help` prepara il download dei nuovi file della guida.

3. `Save-Help` seleziona il file CAB per il modulo dal percorso specificato dall'elemento **HelpContentUri** nel file XML HELPINFO remoto. Usa il nome del modulo, il GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Save-Help` Scarica il file CAB e lo salva nella directory **DestinationPath** Non viene creata alcuna sottodirectory specifica del linguaggio.

5. `Save-Help` crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa solo elementi per il file CAB salvato. Salva quindi il file XML HelpInfo locale nella directory **DestinationPath** e conclude l'aggiornamento.

   Il cmdlet `Update-Help` esegue le azioni seguenti in risposta a un comando per aggiornare i file della guida nel computer di un utente dai file in una condivisione file specificata dal parametro **SourcePath** .

1. `Update-Help` ottiene il file XML HelpInfo remoto dalla directory **SourcePath** Quindi Cerca un file XML HelpInfo locale nella directory del modulo sul computer dell'utente.

2. `Update-Help` confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo locali e remoti per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non è presente un file XML HelpInfo locale, `Update-Help` prepara l'installazione di nuovi file della guida.

3. `Update-Help` seleziona il file CAB per il modulo dalla directory **SourcePath** . Usa il nome del modulo, il GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Update-Help` decomprime il file CAB, convalida i file di contenuto della guida e salva i file di contenuto della guida nella sottodirectory specifica del linguaggio della directory dei moduli nel computer dell'utente.

5. `Update-Help` crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa solo gli elementi per il file CAB installato. Quindi Salva il file XML HelpInfo locale nella directory del modulo e conclude l'aggiornamento.