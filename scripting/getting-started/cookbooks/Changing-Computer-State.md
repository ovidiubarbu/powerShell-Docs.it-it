---
title:  Modifica dello stato del computer
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  8093268b-27f8-4a49-8871-142c5cc33f01
---

# Modifica dello stato del computer
Per reimpostare un computer in Windows PowerShell, usare uno strumento da riga di comando standard o una classe WMI. Anche se si usa Windows PowerShell solo per eseguire lo strumento, imparare a modificare lo stato di alimentazione del computer in Windows PowerShell illustra alcuni dettagli importanti dell'uso degli strumenti esterni in Windows PowerShell.

### Blocco di un computer
L'unico modo per bloccare un computer direttamente con gli strumenti disponibili standard consiste nel chiamare la funzione **LockWorkstation ()** in **user32. dll**:

```
rundll32.exe user32.dll,LockWorkStation
```

Questo comando blocca immediatamente la workstation. Usa *rundll32.exe*, che esegue DLL di Windows (e salva le librerie corrispondenti per poterle usare più volte) per eseguire user32.dll, una libreria di funzioni di gestione di Windows.

Quando si blocca una workstation mentre è abilitata la funzionalità Cambio rapido utente, ad esempio in Windows XP, il computer visualizza la schermata di accesso utente invece dello screen saver dell'utente corrente.

Per arrestare una sessione specifica in Terminal Server, usare lo strumento da riga di comando **tsshutdn.exe**.

### Disconnessione dalla sessione corrente
È possibile usare alcune tecniche diverse per disconnettersi da una sessione nel sistema locale. Il modo più semplice consiste nell'usare lo strumento da riga di comando di Desktop remoto/Servizi terminal, **logoff.exe**. Per altri dettagli, al prompt di Windows PowerShell digitare **logoff /?**. Per disconnettere la sessione attiva corrente, digitare **logoff** senza argomenti.

È anche possibile usare lo strumento **shutdown.exe** con la relativa opzione di disconnessione:

```
shutdown.exe -l
```

Una terza opzione prevede l'uso di WMI. La classe Win32_OperatingSystem include un metodo Win32Shutdown. È possibile richiamare il metodo con il contrassegno 0 per avviare la disconnessione:

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(0)
```

Per altre informazioni e per individuare altre funzionalità del metodo Win32Shutdown, vedere "Metodo Win32Shutdown della classe Win32_OperatingSystem" in MSDN.

### Arresto o riavvio di un computer
L'arresto e il riavvio dei computer sono in genere gli stessi tipi di attività. Gli strumenti per l'arresto di un computer di solito consentono anche di riavviarlo e viceversa. Sono disponibili due opzioni semplici per riavviare un computer da Windows PowerShell. Usare Tsshutdn.exe o Shutdown.exe con gli argomenti appropriati. È possibile ottenere informazioni dettagliate sull'utilizzo con **tsshutdn.exe /?** o **shutdown.exe /?**.

È possibile eseguire le operazioni di arresto e riavvio anche usando **Win32_OperatingSystem** direttamente da Windows PowerShell.

Per arrestare il computer, usare il metodo Win32Shutdown con il contrassegno **1**.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(1)
```

Per riavviare il sistema operativo, usare il metodo Win32Shutdown con il contrassegno **2**.

```
(Get-WmiObject -Class Win32_OperatingSystem -ComputerName .).Win32Shutdown(2)
```



<!--HONumber=May16_HO2-->


