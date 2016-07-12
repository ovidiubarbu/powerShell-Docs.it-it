---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: creazione di report per JEA
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: d867a6462e9fa8b6e16c8c2103899c72b380116c

---

# Creazione di report per JEA
Poiché JEA consente agli utenti senza privilegi l'esecuzione in un contesto con privilegi, la registrazione e il controllo sono estremamente importanti.
In questa sezione vengono illustrati gli strumenti che agevolano le procedure di registrazione e creazione di report.

## Creazione di report per azioni JEA
### Trascrizione over-the-shoulder
Uno dei modi più rapidi per ottenere un riepilogo delle operazioni eseguite in una sessione di PowerShell è osservare da vicino l'attività dell'utente.
Vengono visualizzati i comandi in uso, l'output di tali comandi e tutto appare in ordine.
Oppure no, ma almeno si viene a sapere.
Le trascrizioni di PowerShell sono progettate in modo da offrire una visualizzazione simile al termine dell'attività.

Quando si usa il campo "TranscriptDirectory" nella configurazione di sessione, PowerShell registra automaticamente una trascrizione di tutte le azioni intraprese in una determinata sessione.
Le trascrizioni dalle sessioni sono contenute in questo documento: "$env: ProgramData\JEAConfiguration\Transcripts"

Come si può vedere, la trascrizione registra informazioni sull'utente "connesso", l'utente "RunAs", i comandi eseguiti nella sessione e altro ancora.
Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).

### Registri eventi di PowerShell
Dopo aver attivato la registrazione dei moduli, anche tutte le azioni di PowerShell vengono registrate nei normali registri eventi di Windows.
Questa attività è leggermente più complessa da gestire rispetto alle trascrizioni, ma può essere utile il livello di dettaglio che offre.

Nel registro operativo "PowerShell", l'ID evento 4104 registrerà ogni comando richiamato se è stata abilitata la registrazione dei moduli.

### Altri registri eventi
A differenza dei registri e delle trascrizioni di PowerShell, altri meccanismi di registrazione non acquisiscono l'utente "connesso".
È necessario stabilire una certa correlazione tra gli altri registri e i registri di PowerShell per la corrispondenza tra le azioni intraprese.

Nel registro operativo di "Gestione remota Windows", l'ID evento 193 registrerà il SID e il nome dell'utente connesso, nonché il SID dell'account virtuale RunAs per agevolare questa correlazione.
Come forse si è notato, il nome dell'account virtuale RunAs include alla fine il dominio e il nome utente dell'utente connesso.

## Creazione di report per la configurazione JEA
### Get-PSSessionConfiguration
Per segnalare con precisione lo stato dell'ambiente, è importante sapere quanti endpoint JEA sono impostati sul computer.
`Get-PSSessionConfiguration` esegue questa operazione.

### Get-PSSessionCapability
Creare manualmente report sulle capacità di ogni utente usando un endpoint JEA può essere molto complesso.
Potenzialmente occorre controllare diverse capacità del ruolo.
Fortunatamente il cmdlet "Get-PSSessionCapability" esegue questa operazione.

Per testarlo, eseguire il comando seguente dal prompt dei comandi di PowerShell come amministratore:
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```




<!--HONumber=Jul16_HO1-->


