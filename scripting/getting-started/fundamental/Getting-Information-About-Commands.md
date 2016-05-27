---
title:  Recupero di informazioni sui comandi
ms.date:  2016-05-11
keywords:  powershell,cmdlet
description:  
ms.topic:  article
author:  jpjofre
manager:  dongill
ms.prod:  powershell
ms.assetid:  56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
---

# Recupero di informazioni sui comandi
Il cmdlet **Get-Command** di Windows PowerShell ottiene tutti i comandi disponibili nella sessione corrente. Quando si digita **Get-Command** al prompt di Windows PowerShell, verrà visualizzato un output simile al seguente:

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

Questo output è simile all'output della Guida di Cmd.exe, ossia un riepilogo di comandi interni in formato tabella. Nell'estratto dell'output del comando **Get-Command** illustrato sopra, ogni comando visualizzato ha un cmdlet di tipo CommandType. Un cmdlet è un tipo di comando intrinseco di Windows PowerShell, che corrisponde approssimativamente ai comandi **dir** e **cd** di Cmd.exe e ai comandi predefiniti delle shell UNIX, come BASH.

Nell'output del comando **Get-Command** tutte le definizioni terminano con puntini di sospensione (...) per indicare che PowerShell non può visualizzare tutto il contenuto nello spazio disponibile. Quando Windows PowerShell visualizza l'output, lo formatta come testo e quindi lo dispone in modo che i dati si adattino perfettamente alla finestra. Questo aspetto verrà trattato più avanti nella sezione sui formattatori.

Il cmdlet **Get-Command** ha un parametro **Syntax** che ottiene la sintassi di ogni cmdlet. Per ottenere la sintassi del cmdlet Get-Help, usare il comando seguente:

**Get-Command Get-Help -Syntax**

```
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

### Visualizzazione dei tipi di comando disponibili
Il comando **Get-Command** non elenca tutti i comandi disponibili in Windows PowerShell. Al contrario, il comando **Get-Command** elenca solo i cmdlet della sessione corrente. Windows PowerShell supporta in realtà diversi altri tipi di comandi. Anche alias, funzioni e script sono comandi di Windows PowerShell, sebbene non vengano descritti in dettaglio nel Manuale dell'utente. Anche i file esterni eseguibili o che hanno un gestore dei tipi di file registrati vengono classificati come comandi.

Per ottenere tutti i comandi della sessione, digitare:

```
Get-Command *
```

Poiché questo elenco include file esterni nel percorso di ricerca, potrebbe contenere migliaia di elementi. Risulta più utile esaminare un set ridotto di comandi.

Per ottenere comandi nativi di altri tipi, usare il parametro **CommandType** del cmdlet **Get-Command**.

> [!NOTE]
> L'asterisco (*) viene usato per la corrispondenza con carattere jolly negli argomenti dei comandi di Windows PowerShell. Indica una corrispondenza con uno o più caratteri qualsiasi. È possibile digitare **Get-Command a*** per trovare tutti i comandi che iniziano con la lettera "a". A differenza di quanto avviene con Cmd.exe, il carattere jolly di Windows PowerShell corrisponde anche a un punto.

Per ottenere gli alias di comandi, ovvero i nomi alternativi assegnati, digitare:

```
Get-Command -CommandType Alias
```

Per ottenere le funzioni della sessione corrente, digitare:

```
Get-Command -CommandType Function
```

Per visualizzare gli script nel percorso di ricerca di Windows PowerShell, digitare:

```
Get-Command -CommandType Script
```



<!--HONumber=May16_HO2-->


