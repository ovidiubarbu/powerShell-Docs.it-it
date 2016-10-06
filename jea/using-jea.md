---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: uso di jea
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: 88ce340c09efdbb3d81a72fe6113c1187a9152f2
ms.openlocfilehash: 9db7a5a91d25d459313117da34af63016f03c241

---

# Uso di JEA
Questa sezione è incentrata sull'esperienza dell'utente finale *con JEA*.
Nella sezione dei prerequisiti è stato creato un endpoint JEA dimostrativo,
che verrà usato di seguito per illustrare il funzionamento di JEA.
Nelle sezioni successive della guida si procederà a ritroso, presentando le azioni e i file che hanno reso possibile l'esperienza utente descritta.

## Uso di JEA come utente non amministratore
Per visualizzare JEA in azione, è necessario usare la comunicazione remota di PowerShell come utente non amministratore.
Eseguire il comando seguente in una nuova finestra di PowerShell:   

```PowerShell
$NonAdminCred = Get-Credential
```

Immettere le credenziali per l'account non amministratore quando richiesto.
Se è stata seguita la sezione [Configurare utenti e gruppi](creating-a-domain-controller.md#set-up-users-and-groups), saranno:
-   Nome utente = "OperatorUser"
-   Password = "pa$$w0rd"

Quindi, eseguire il comando seguente per connettersi all'endpoint dimostrativo usando le credenziali specificate:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Viene avviata una sessione interattiva di PowerShell remota nel computer locale.
Specificando il parametro "Credential", la connessione viene eseguita *come se l'utente fosse* OperatorUser (o qualsiasi account usato).
La modifica nella richiesta a `[localhost]: PS>` indica che si sta lavorando in una sessione remota.  

Per visualizzare i comandi disponibili, nel prompt dei comandi remoto eseguire:

```PowerShell
Get-Command
```

Come si può vedere, si tratta di un subset molto limitato dei comandi disponibili in una normale finestra di PowerShell, che spesso può includere diverse migliaia di comandi.
In particolare, visualizza solo gli 8 comandi JEA predefiniti (Clear-Host, Exit-PSSession, Get-Command, Get-FormatData, Get-Help, Measure-Object, Out-Default, Select-Object) e i due comandi inclusi in modo esplicito nel file di capacità del ruolo per la manutenzione.

Osservare quindi il contesto utente in cui opera questa sessione richiamando la funzione personalizzata inclusa nel file di capacità del ruolo per la manutenzione:

```PowerShell
Get-UserInfo
```

L'output di questa funzione indica un valore sia per "ConnectedUser" che per "RunAsUser".
L'utente connesso è l'account connesso alla sessione remota, ad esempio il proprio account.
Non è necessario che l'utente connesso abbia privilegi di amministratore.
L'account "RunAs" è l'account che effettivamente esegue le azioni con privilegi.
La possibilità di connettersi come utente normale e di eseguire operazioni come utente con privilegi consente agli utenti senza privilegi di eseguire specifiche attività amministrative senza avere diritti amministrativi.

Per vedere come funziona in pratica questo concetto, eseguire il comando seguente:

```PowerShell
Restart-Service -Name Spooler -Verbose
```

In genere, Restart-Service richiede privilegi di amministratore per essere eseguito.
Con l'account virtuale JEA, tuttavia, può essere eseguito usando credenziali senza privilegi.

Pertanto, JEA consente di svolgere il proprio lavoro usando i comandi già in uso.
Come vengono gestiti i comandi che *non si devono* usare?
Provare a eseguire un comando diverso nella sessione JEA, ad esempio `Restart-Computer`, e si noterà che JEA ne impedisce l'esecuzione.

```PowerShell
[localhost]: PS> Restart-Computer
The term 'Restart-Computer' is not recognized as the name of a cmdlet, function, script file, or
operable program. Check the spelling of the name, or if a path was included, verify that the path
is correct and try again.
    + CategoryInfo          : ObjectNotFound: (Restart-Computer:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException
```

Per lasciare l'endpoint JEA vincolato, eseguire il comando seguente:

```PowerShell
Exit-PSSession
```

In questo modo l'utente viene disconnesso dalla sessione di PowerShell remota.




<!--HONumber=Aug16_HO3-->


