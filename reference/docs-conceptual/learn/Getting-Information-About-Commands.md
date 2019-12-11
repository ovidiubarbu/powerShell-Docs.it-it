---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Recupero di informazioni sui comandi
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030950"
---
# <a name="getting-information-about-commands"></a>Recupero di informazioni sui comandi

Il cmdlet `Get-Command` di PowerShell visualizza i comandi disponibili nella sessione corrente.
Quando si esegue il cmdlet `Get-Command`, viene visualizzato un output simile al seguente:

```output
CommandType     Name                    Version    Source
-----------     ----                    -------    ------
Cmdlet          Add-Computer            3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-Content             3.1.0.0    Microsoft.PowerShell.Management
Cmdlet          Add-History             3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-JobTrigger          1.1.0.0    PSScheduledJob
Cmdlet          Add-LocalGroupMember    1.0.0.0    Microsoft.PowerShell.LocalAccounts
Cmdlet          Add-Member              3.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Add-PSSnapin            3.0.0.0    Microsoft.PowerShell.Core
Cmdlet          Add-Type                3.1.0.0    Microsoft.PowerShell.Utility
...
```

Questo output è molto simile all'output della Guida di **cmd.exe**, ovvero un riepilogo di comandi interni in formato tabella. Nell'estratto dell'output del comando `Get-Command` mostrato sopra ogni comando visualizzato ha Cmdlet come CommandType. Un cmdlet è il tipo di comando intrinseco di PowerShell. Questo tipo corrisponde all'incirca a `dir` e `cd` in **cmd.exe** o ai comandi predefiniti di shell UNIX come bash.

Il cmdlet `Get-Command` include un parametro **Syntax** che restituisce la sintassi di ogni cmdlet. L'esempio seguente mostra come ottenere la sintassi del cmdlet `Get-Help`:

```powershell
Get-Command Get-Help -Syntax
```

```output
Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Full] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Detailed] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Examples] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]

Get-Help [[-Name] <String>] [-Path <String>] [-Category <String[]>] [-Component <String[]>] [-Functionality <String[]>]
 [-Role <String[]>] [-Parameter <String>] [-Online] [-Verbose] [-Debug] [-ErrorAction <ActionPreference>] [-WarningAction <ActionPreference>] [-ErrorVariable <String>] [-WarningVariable <String>] [-OutVariable <String>] [-OutBuffer <Int32>]
```

## <a name="displaying-available-command-by-type"></a>Visualizzazione dei comandi disponibili in base al tipo

Il comando `Get-Command` elenca solo i cmdlet della sessione corrente. PowerShell supporta in realtà diversi altri tipi di comandi:

- Alias
- Funzioni
- Script

Anche i file eseguibili esterni o che hanno un gestore dei tipi di file registrati vengono classificati come comandi.

Per ottenere tutti i comandi della sessione, digitare:

```powershell
Get-Command *
```

Poiché questo elenco include comandi esterni nel percorso di ricerca, potrebbe contenere migliaia di elementi.
Risulta più utile esaminare un set ridotto di comandi.

> [!NOTE]
> L'asterisco (\*) viene usato per la corrispondenza con caratteri jolly negli argomenti dei comandi di PowerShell. Il carattere \* indica una corrispondenza con uno o più caratteri qualsiasi. È possibile digitare `Get-Command a*` per trovare tutti i comandi che iniziano con la lettera "a". A differenza di quanto avviene in **cmd.exe**, il carattere jolly di PowerShell corrisponde anche a un punto.

Per ottenere comandi nativi di altri tipi, usare il parametro **CommandType** di `Get-Command`.
.

Per ottenere gli alias di comandi, ovvero i nomi alternativi assegnati, digitare:

```powershell
Get-Command -CommandType Alias
```

Per ottenere le funzioni della sessione corrente, digitare:

```powershell
Get-Command -CommandType Function
```

Per visualizzare gli script nel percorso di ricerca di PowerShell, digitare:

```powershell
Get-Command -CommandType Script
```
