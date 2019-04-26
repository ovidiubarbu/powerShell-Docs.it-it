---
title: La modalità aggiornabile Help può essere usato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7674636e-a0f2-4587-bfc5-dd3e6ce5489e
caps.latest.revision: 6
ms.openlocfilehash: 5b6ae54ee6c843996c875189b6ee553be5e4f614
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082261"
---
# <a name="how-updatable-help-works"></a>Come funziona la Guida aggiornabile

Questo argomento viene illustrato come i processi per la Guida aggiornabile del file XML HelpInfo CAB file per ogni modulo e consente di installare l'aggiornamento della Guida per gli utenti.

## <a name="the-update-help-process"></a>Il processo di Update-Help

L'elenco seguente descrive le operazioni dei [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando un utente esegue un comando per aggiornare i file della Guida per un modulo in determinate impostazioni cultura dell'interfaccia utente.

1. `Update-Help` Ottiene il file XML HelpInfo remoto dal percorso specificato dal valore della **HelpInfoURI** chiave nel manifesto del modulo e convalida il file a fronte dello schema. (Per visualizzare lo schema, vedere [dello Schema XML HelpInfo](./helpinfo-xml-schema.md).) Quindi `Update-Help` Cerca un file XML HelpInfo locale per il modulo nella directory del modulo nel computer dell'utente.

2. `Update-Help` Confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo remoti e locali per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non esistono Nessun file XML HelpInfo locale per il modulo, `Update-Help` Prepara per scaricare nuovi file della Guida.

3. `Update-Help` Consente di selezionare il file CAB per il modulo dal percorso specificato per il **HelpContentUri** elemento nel file XML HelpInfo remoto. Usa il nome del modulo, GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Update-Help` Scarica il file CAB, è possibile decomprimere, convalida i file di contenuto della Guida e Salva la Guida in linea i file contenuti nella sottodirectory specifica del linguaggio della directory del modulo nel computer dell'utente.

5. `Update-Help` Crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa gli elementi solo per il file CAB che installato. Quindi Salva il file XML HelpInfo locale nella directory del modulo e l'aggiornamento è terminata.

## <a name="the-save-help-process"></a>Il processo di Save-Help

L'elenco seguente descrive le azioni del [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) e [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) cmdlet quando un utente esegue i comandi per aggiornare i file della Guida in una condivisione file e quindi usare tali file per aggiornare i file della Guida di computer dell'utente.

Il `Save-Help` cmdlet esegue le azioni seguenti in risposta a un comando per salvare i file della Guida per un modulo in una condivisione di file specificato dal **DestinationPath** parametro.

1. `Save-Help` Ottiene il file XML HelpInfo remoto dal percorso specificato dal valore della **HelpInfoURI** chiave nel manifesto del modulo e convalida il file a fronte dello schema. (Per visualizzare lo schema, vedere [dello Schema XML HelpInfo](./helpinfo-xml-schema.md).) Quindi `Save-Help` Cerca un file XML HelpInfo locale nella directory specificata dal **DestinationPath** parametri nel `Save-Help` comando.

2. `Save-Help` Confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo remoti e locali per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non esistono Nessun file XML HelpInfo locale per il modulo nel **DestinationPath** directory `Save-Help` Prepara per scaricare nuovi file della Guida.

3. `Save-Help` Consente di selezionare il file CAB per il modulo dal percorso specificato per il **HelpContentUri** elemento nel file XML HelpInfo remoto. Usa il nome del modulo, GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Save-Help` Scarica il file CAB e lo salva nella **DestinationPath** directory. (Non crea tutte le sottodirectory specifiche del linguaggio.)

5. `Save-Help` Crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa gli elementi solo per il file CAB salvato. Quindi Salva il file XML HelpInfo locale nel **DestinationPath** directory e terminano l'aggiornamento.

   Il `Update-Help` cmdlet esegue le azioni seguenti in risposta a un comando per aggiornare i file della Guida nel computer dell'utente dai file in una condivisione di file specificato dal **SourcePath** parametro.

1. `Update-Help` Ottiene il file XML HelpInfo remoto dal **SourcePath** directory. Quindi cerca un file XML HelpInfo locale nella directory del modulo nel computer dell'utente.

2. `Update-Help` Confronta il numero di versione dei file della Guida per le impostazioni cultura dell'interfaccia utente specificate nei file XML HelpInfo remoti e locali per il modulo. Se il numero di versione nel file remoto è maggiore del numero di versione nel file locale o se non esistono Nessun file XML HelpInfo locale, `Update-Help` prepara l'installazione di nuovi file della Guida.

3. `Update-Help` Consente di selezionare il file CAB per il modulo dalla **SourcePath** directory. Usa il nome del modulo, GUID del modulo e le impostazioni cultura dell'interfaccia utente per identificare il file CAB.

4. `Update-Help` decomprime il file CAB, convalida i file di contenuto della Guida in linea e Salva la Guida in linea i file contenuti nella sottodirectory specifica del linguaggio della directory del modulo nel computer dell'utente.

5. `Update-Help` Crea un file XML HelpInfo locale copiando il file XML HelpInfo remoto. Modifica il file XML HelpInfo locale in modo che includa gli elementi solo per il file CAB che installato. Quindi Salva il file XML HelpInfo locale nella directory del modulo e l'aggiornamento è terminata.