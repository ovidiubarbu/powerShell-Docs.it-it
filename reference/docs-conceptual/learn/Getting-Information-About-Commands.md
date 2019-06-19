---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Recupero di informazioni sui comandi
ms.openlocfilehash: eb918c6f89d8369db775258263a8f7a7902a6cc7
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030950"
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="49d83-103">Recupero di informazioni sui comandi</span><span class="sxs-lookup"><span data-stu-id="49d83-103">Getting information about commands</span></span>

<span data-ttu-id="49d83-104">Il cmdlet `Get-Command` di PowerShell visualizza i comandi disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="49d83-104">The PowerShell `Get-Command` displays commands that are available in your current session.</span></span>
<span data-ttu-id="49d83-105">Quando si esegue il cmdlet `Get-Command`, viene visualizzato un output simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="49d83-105">When you run the `Get-Command` cmdlet, you see something similar to the following output:</span></span>

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

<span data-ttu-id="49d83-106">Questo output è molto simile all'output della Guida di **cmd.exe**, ovvero un riepilogo di comandi interni in formato tabella.</span><span class="sxs-lookup"><span data-stu-id="49d83-106">This output looks a lot like the Help output of **cmd.exe**: a tabular summary of internal commands.</span></span> <span data-ttu-id="49d83-107">Nell'estratto dell'output del comando `Get-Command` mostrato sopra ogni comando visualizzato ha Cmdlet come CommandType.</span><span class="sxs-lookup"><span data-stu-id="49d83-107">In the excerpt of the `Get-Command` command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="49d83-108">Un cmdlet è il tipo di comando intrinseco di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49d83-108">A cmdlet is PowerShell's intrinsic command type.</span></span> <span data-ttu-id="49d83-109">Questo tipo corrisponde all'incirca a `dir` e `cd` in **cmd.exe** o ai comandi predefiniti di shell UNIX come bash.</span><span class="sxs-lookup"><span data-stu-id="49d83-109">This type corresponds roughly to commands like `dir` and `cd` in **cmd.exe** or the built-in commands of Unix shells like bash.</span></span>

<span data-ttu-id="49d83-110">Il cmdlet `Get-Command` include un parametro **Syntax** che restituisce la sintassi di ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="49d83-110">The `Get-Command` cmdlet has a **Syntax** parameter that returns syntax of each cmdlet.</span></span> <span data-ttu-id="49d83-111">L'esempio seguente mostra come ottenere la sintassi del cmdlet `Get-Help`:</span><span class="sxs-lookup"><span data-stu-id="49d83-111">The following example shows how to get the syntax of the `Get-Help` cmdlet:</span></span>

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

## <a name="displaying-available-command-by-type"></a><span data-ttu-id="49d83-112">Visualizzazione dei comandi disponibili in base al tipo</span><span class="sxs-lookup"><span data-stu-id="49d83-112">Displaying available command by type</span></span>

<span data-ttu-id="49d83-113">Il comando `Get-Command` elenca solo i cmdlet della sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="49d83-113">The `Get-Command` command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="49d83-114">PowerShell supporta in realtà diversi altri tipi di comandi:</span><span class="sxs-lookup"><span data-stu-id="49d83-114">PowerShell actually supports several other types of commands:</span></span>

- <span data-ttu-id="49d83-115">Alias</span><span class="sxs-lookup"><span data-stu-id="49d83-115">Aliases</span></span>
- <span data-ttu-id="49d83-116">Funzioni</span><span class="sxs-lookup"><span data-stu-id="49d83-116">Functions</span></span>
- <span data-ttu-id="49d83-117">Script</span><span class="sxs-lookup"><span data-stu-id="49d83-117">Scripts</span></span>

<span data-ttu-id="49d83-118">Anche i file eseguibili esterni o che hanno un gestore dei tipi di file registrati vengono classificati come comandi.</span><span class="sxs-lookup"><span data-stu-id="49d83-118">External executable files, or files that have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="49d83-119">Per ottenere tutti i comandi della sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="49d83-119">To get all commands in the session, type:</span></span>

```powershell
Get-Command *
```

<span data-ttu-id="49d83-120">Poiché questo elenco include comandi esterni nel percorso di ricerca, potrebbe contenere migliaia di elementi.</span><span class="sxs-lookup"><span data-stu-id="49d83-120">This list includes external commands in your search path so it can contain thousands of items.</span></span>
<span data-ttu-id="49d83-121">Risulta più utile esaminare un set ridotto di comandi.</span><span class="sxs-lookup"><span data-stu-id="49d83-121">It is more useful to look at a reduced set of commands.</span></span>

> [!NOTE]
> <span data-ttu-id="49d83-122">L'asterisco (\*) viene usato per la corrispondenza con caratteri jolly negli argomenti dei comandi di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49d83-122">The asterisk (\*) is used for wildcard matching in PowerShell command arguments.</span></span> <span data-ttu-id="49d83-123">Il carattere \* indica una corrispondenza con uno o più caratteri qualsiasi.</span><span class="sxs-lookup"><span data-stu-id="49d83-123">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="49d83-124">È possibile digitare `Get-Command a*` per trovare tutti i comandi che iniziano con la lettera "a".</span><span class="sxs-lookup"><span data-stu-id="49d83-124">You can type `Get-Command a*` to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="49d83-125">A differenza di quanto avviene in **cmd.exe**, il carattere jolly di PowerShell corrisponde anche a un punto.</span><span class="sxs-lookup"><span data-stu-id="49d83-125">Unlike wildcard matching in **cmd.exe**, PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="49d83-126">Per ottenere comandi nativi di altri tipi, usare il parametro **CommandType** di `Get-Command`.</span><span class="sxs-lookup"><span data-stu-id="49d83-126">Use the **CommandType** parameter of `Get-Command` to get native commands of other types.</span></span>
<span data-ttu-id="49d83-127">.</span><span class="sxs-lookup"><span data-stu-id="49d83-127">cmdlet.</span></span>

<span data-ttu-id="49d83-128">Per ottenere gli alias di comandi, ovvero i nomi alternativi assegnati, digitare:</span><span class="sxs-lookup"><span data-stu-id="49d83-128">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```powershell
Get-Command -CommandType Alias
```

<span data-ttu-id="49d83-129">Per ottenere le funzioni della sessione corrente, digitare:</span><span class="sxs-lookup"><span data-stu-id="49d83-129">To get the functions in the current session, type:</span></span>

```powershell
Get-Command -CommandType Function
```

<span data-ttu-id="49d83-130">Per visualizzare gli script nel percorso di ricerca di PowerShell, digitare:</span><span class="sxs-lookup"><span data-stu-id="49d83-130">To display scripts in PowerShell's search path, type:</span></span>

```powershell
Get-Command -CommandType Script
```
