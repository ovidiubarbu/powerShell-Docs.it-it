---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Glossario di Windows PowerShell
ms.assetid: b0f88cbe-cb83-4912-a301-184534cb35c7
ms.openlocfilehash: 48e5d832ead720c8bc7753c94f757ddb21846fc9
ms.sourcegitcommit: ced46469e064736eeb1f5608abbc792ec69bdc92
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/08/2017
---
# <a name="windows-powershell-glossary"></a>Glossario di Windows PowerShell


|Termine|Definizione|
|--------|--------------|
|modulo binario|Modulo di Windows PowerShell il cui modulo radice è un file di modulo binario (con estensione dll). Un modulo binario può includere o meno un manifesto del modulo.|
|parametro comune|Parametro aggiunto a tutti i cmdlet, le funzioni avanzate e i flussi di lavoro dal motore di Windows PowerShell.|
|dot sourcing|In Windows PowerShell, avviare un comando digitando un punto e uno spazio prima del comando. I comandi con dot sourcing vengono eseguiti nell'ambito corrente anziché in un nuovo ambito. Qualsiasi variabile, alias, funzione o unità creata dal comando viene creato nell'ambito corrente ed è disponibile per gli utenti dopo il completamento del comando.|
|modulo dinamico|Modulo che esiste solo in memoria. I cmdlet New-Module e Import-PSSession creano moduli dinamici.|
|parametro dinamico|Parametro aggiunto a un cmdlet, una funzione o uno script di Windows PowerShell in determinate condizioni. I cmdlet, le funzioni, i provider e gli script possono aggiungere parametri dinamici.|
|file di formattazione|File XML di Windows PowerShell con estensione format.ps1xml che definisce la modalità di visualizzazione di un oggetto in Windows PowerShell in base al relativo tipo .NET Framework.|
|stato della sessione globale|Stato della sessione contenente i dati accessibili all'utente di una sessione di Windows PowerShell.|
|host|Interfaccia usata dal motore di Windows PowerShell per comunicare con l'utente. Ad esempio, l'host specifica la modalità di gestione dei prompt tra Windows PowerShell e l'utente.|
|applicazione host|Programma che carica il motore di Windows PowerShell nel suo processo e lo usa per eseguire operazioni.|
|metodo di elaborazione dell'input|Metodo utilizzabile da un cmdlet per elaborare i record ricevuti come input. I metodi di elaborazione dell'input includono BeginProcessing, ProcessRecord, EndProcessing e StopProcessing.|
|modulo manifesto|Modulo di Windows PowerShell che ha un manifesto e la cui chiave ModulesToProcess è vuota.|
|manifesto del modulo|File di dati di Windows PowerShell (con estensione psd1) che descrive il contenuto di un modulo e che controlla la modalità di elaborazione di un modulo.|
|stato della sessione del modulo|Stato della sessione contenente i dati pubblici e privati di un modulo di Windows PowerShell. I dati privati nello stato della sessione non sono disponibili per l'utente di una sessione di Windows PowerShell.|
|errore non fatale|Errore che non impedisce a Windows PowerShell di continuare a elaborare il comando.|
|sostantivo|Parola che segue il segno meno nel nome di un cmdlet di Windows PowerShell. Il sostantivo descrive le risorse su cui agisce il cmdlet.|
|set di parametri|Gruppo di parametri utilizzabili nello stesso comando per eseguire un'azione specifica.|
|inviare tramite pipe|In Windows PowerShell inviare i risultati del comando precedente come input al comando successivo nella pipeline.|
|pipeline|Serie di comandi connessi con operatori pipeline (&#124;) (ASCII 124). Ogni operatore pipeline invia i risultati del comando precedente come input al comando successivo.|
|PSSession|Tipo di sessione di Windows PowerShell creata, gestita e chiusa dall'utente.|
|modulo radice|Modulo specificato nella chiave ModuleToProcess in un manifesto del modulo.|
|spazio di esecuzione|In Windows PowerShell, l'ambiente operativo in cui viene eseguito ogni comando in una pipeline.|
|blocco di script|Nel linguaggio di programmazione di Windows PowerShell, raccolta di istruzioni o espressioni che possono essere usate come una singola unità. Un blocco di script può accettare argomenti e valori restituiti.|
|modulo di script|Modulo di Windows PowerShell il cui modulo radice è un file di modulo di script (con estensione psm1). Un modulo di script può includere o meno un manifesto del modulo.|
|file di modulo di script|File contenente uno script di Windows PowerShell. Lo script definisce i membri esportati dal modulo di script. Per i nomi dei file di modulo di script viene usata l'estensione psm1.|
|shell|Interprete dei comandi usato per passare i comandi al sistema operativo.|
|parametro opzionale|Parametro che non accetta un argomento.|
|errore fatale|Errore che impedisce a Windows PowerShell di continuare a elaborare il comando.|
|transazione|Unità di lavoro atomica. Il lavoro in una transazione deve essere completato nel suo complesso. Se qualsiasi parte della transazione non riesce, l'intera transazione avrà esito negativo.|
|file dei tipi|File XML di Windows PowerShell con estensione ps1xml che estende le proprietà dei tipi di Microsoft .NET Framework in Windows PowerShell.|
|verbo|Parola che precede il segno meno nel nome di un cmdlet di Windows PowerShell. Il verbo descrive l'azione eseguita dal cmdlet.|
|Windows PowerShell|Shell da riga di comando e tecnologia di scripting basata su attività che consente agli amministratori IT di controllare e automatizzare in modo completo le attività di amministrazione del sistema.|
|comando di Windows PowerShell|Elementi in una pipeline che determinano l'esecuzione di un'azione. I comandi di Windows PowerShell vengono digitati tramite la tastiera o richiamati a livello di codice.|
|file di dati di Windows PowerShell|File di testo con estensione psd1. Windows PowerShell usa i file di dati per vari scopi, ad esempio l'archiviazione dei dati del manifesto del modulo e l'archiviazione delle stringhe tradotte per l'internazionalizzazione degli script.|
|unità di Windows PowerShell|Unità virtuale che consente l'accesso diretto a un archivio dati. Può essere definita da un provider di Windows PowerShell o creata nella riga di comando. Le unità create nella riga di comando sono specifiche della sessione e non sono più disponibili dopo la chiusura della sessione.|
|Windows PowerShell Integrated Scripting Environment (ISE)|Applicazione host di Windows PowerShell che consente di eseguire comandi e di scrivere, testare ed eseguire il debug di script in un ambiente conforme a Unicode, familiare e con sintassi a colori.|
|modulo di Windows PowerShell|Unità autosufficiente e riutilizzabile per il partizionamento, l'organizzazione e l'astrazione del codice di Windows PowerShell. Un modulo può contenere cmdlet, provider, funzioni, variabili e altri tipi di risorse che possono essere importati come singola unità.|
|provider di Windows PowerShell|Programma basato su Microsoft .NET Framework che rende disponibili in Windows PowerShell i dati presenti in archivi dati speciali, consentendo di visualizzarli e gestirli.|
|script di Windows PowerShell|Script scritto nel linguaggio di Windows PowerShell.|
|file di script di Windows PowerShell|File con estensione ps1 che contiene uno script che viene scritto nel linguaggio di Windows PowerShell.|
|Snap-in di Windows PowerShell|Risorsa che definisce un set di cmdlet, provider e tipi di Microsoft .NET Framework che possono essere aggiunti all'ambiente di Windows PowerShell.|
|Flusso di lavoro di Windows PowerShell|Un flusso di lavoro è una sequenza di passaggi programmati e connessi che consentono di eseguire attività di lunga durata o richiedono il coordinamento di più passaggi tra più dispositivi o nodi gestiti. Il flusso di lavoro di Windows PowerShell consente a professionisti IT e sviluppatori di creare sequenze di attività di gestione di più dispositivi o singole attività all'interno di un flusso di lavoro come flussi di lavoro. Il flusso di lavoro di Windows PowerShell consente di adattare ed eseguire sia script di Windows PowerShell che file XAML come flussi di lavoro.|

