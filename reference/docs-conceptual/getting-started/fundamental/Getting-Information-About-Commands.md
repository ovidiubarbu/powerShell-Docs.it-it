---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Recupero di informazioni sui comandi
ms.assetid: 56f8e5b4-d97c-4e59-abbe-bf13e464eb0d
ms.openlocfilehash: 98e449110860ea81939d6ec0b7b1a8534a2da2aa
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/03/2017
---
# <a name="getting-information-about-commands"></a><span data-ttu-id="97f39-103">Recupero di informazioni sui comandi</span><span class="sxs-lookup"><span data-stu-id="97f39-103">Getting Information About Commands</span></span>
<span data-ttu-id="97f39-104">Il cmdlet **Get-Command** di Windows PowerShell ottiene tutti i comandi disponibili nella sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="97f39-104">The Windows PowerShell **Get-Command** cmdlet gets all commands that are available in your current session.</span></span> <span data-ttu-id="97f39-105">Quando si digita **Get-Command** al prompt di Windows PowerShell, verrà visualizzato un output simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="97f39-105">When you type **Get-Command** at a Windows PowerShell prompt, you will see output similar to the following:</span></span>

```
PS> Get-Command
CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Add-Content                     Add-Content [-Path] <String[...
Cmdlet          Add-History                     Add-History [[-InputObject] ...
Cmdlet          Add-Member                      Add-Member [-MemberType] <PS...
...
```

<span data-ttu-id="97f39-106">Questo output è simile all'output della Guida di Cmd.exe, ossia un riepilogo di comandi interni in formato tabella.</span><span class="sxs-lookup"><span data-stu-id="97f39-106">This output looks a lot like the Help output of Cmd.exe: a tabular summary of internal commands.</span></span> <span data-ttu-id="97f39-107">Nell'estratto dell'output del comando **Get-Command** illustrato sopra, ogni comando visualizzato ha un cmdlet di tipo CommandType.</span><span class="sxs-lookup"><span data-stu-id="97f39-107">In the excerpt of the **Get-Command** command output shown above, every command shown has a CommandType of Cmdlet.</span></span> <span data-ttu-id="97f39-108">Un cmdlet è un tipo di comando intrinseco di Windows PowerShell, che corrisponde approssimativamente ai comandi **dir** e **cd** di Cmd.exe e ai comandi predefiniti delle shell UNIX, ad esempio BASH.</span><span class="sxs-lookup"><span data-stu-id="97f39-108">A cmdlet is Windows PowerShell's intrinsic command type - a type that corresponds roughly to the **dir** and **cd** commands of Cmd.exe and to built-ins in UNIX shells such as BASH.</span></span>

<span data-ttu-id="97f39-109">Nell'output del comando **Get-Command** tutte le definizioni terminano con puntini di sospensione (...) per indicare che PowerShell non può visualizzare tutto il contenuto nello spazio disponibile.</span><span class="sxs-lookup"><span data-stu-id="97f39-109">In the output of the **Get-Command** command, all the definitions end with ellipses (...) to indicate that PowerShell cannot display all the content in the available space.</span></span> <span data-ttu-id="97f39-110">Quando Windows PowerShell visualizza l'output, lo formatta come testo e quindi lo dispone in modo che i dati si adattino perfettamente alla finestra.</span><span class="sxs-lookup"><span data-stu-id="97f39-110">When Windows PowerShell displays output, it formats the output as text and then arranges it to make the data fit cleanly into the window.</span></span> <span data-ttu-id="97f39-111">Questo aspetto verrà trattato più avanti nella sezione sui formattatori.</span><span class="sxs-lookup"><span data-stu-id="97f39-111">We will talk about this later in the section on formatters.</span></span>

<span data-ttu-id="97f39-112">Il cmdlet **Get-Command** ha un parametro **Syntax** che ottiene la sintassi di ogni cmdlet.</span><span class="sxs-lookup"><span data-stu-id="97f39-112">The **Get-Command** cmdlet has a **Syntax** parameter that gets the syntax of each cmdlet.</span></span> <span data-ttu-id="97f39-113">Per ottenere la sintassi del cmdlet Get-Help, usare il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="97f39-113">To get the syntax of the Get-Help cmdlet, use the following command:</span></span>

<span data-ttu-id="97f39-114">**Get-Command Get-Help -Syntax**</span><span class="sxs-lookup"><span data-stu-id="97f39-114">**Get-Command Get-Help -Syntax**</span></span>

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

### <a name="displaying-available-command-types"></a><span data-ttu-id="97f39-115">Visualizzazione dei tipi di comando disponibili</span><span class="sxs-lookup"><span data-stu-id="97f39-115">Displaying Available Command Types</span></span>
<span data-ttu-id="97f39-116">Il comando **Get-Command** non elenca tutti i comandi disponibili in Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97f39-116">The **Get-Command** command does not list every command that is available in Windows PowerShell.</span></span> <span data-ttu-id="97f39-117">Al contrario, il comando **Get-Command** elenca solo i cmdlet della sessione corrente.</span><span class="sxs-lookup"><span data-stu-id="97f39-117">Instead, the **Get-Command** command lists only the cmdlets in the current session.</span></span> <span data-ttu-id="97f39-118">Windows PowerShell supporta in realtà diversi altri tipi di comandi.</span><span class="sxs-lookup"><span data-stu-id="97f39-118">Windows PowerShell actually supports several other types of commands.</span></span> <span data-ttu-id="97f39-119">Anche alias, funzioni e script sono comandi di Windows PowerShell, sebbene non vengano descritti in dettaglio nel Manuale dell'utente.</span><span class="sxs-lookup"><span data-stu-id="97f39-119">Aliases, functions, and scripts are also Windows PowerShell commands, although they are not discussed in detail in the Windows PowerShell User's Guide.</span></span> <span data-ttu-id="97f39-120">Anche i file esterni eseguibili o che hanno un gestore dei tipi di file registrati vengono classificati come comandi.</span><span class="sxs-lookup"><span data-stu-id="97f39-120">External files that are executable, or have a registered file type handler, are also classified as commands.</span></span>

<span data-ttu-id="97f39-121">Per ottenere tutti i comandi della sessione, digitare:</span><span class="sxs-lookup"><span data-stu-id="97f39-121">To get all commands in the session, type:</span></span>

```
Get-Command *
```

<span data-ttu-id="97f39-122">Poiché questo elenco include file esterni nel percorso di ricerca, potrebbe contenere migliaia di elementi.</span><span class="sxs-lookup"><span data-stu-id="97f39-122">Because this list includes external files in your search path, it may contain thousands of items.</span></span> <span data-ttu-id="97f39-123">Risulta più utile esaminare un set ridotto di comandi.</span><span class="sxs-lookup"><span data-stu-id="97f39-123">It is more useful to look at a reduced set of commands.</span></span>

<span data-ttu-id="97f39-124">Per ottenere comandi nativi di altri tipi, usare il parametro **CommandType** del cmdlet **Get-Command**.</span><span class="sxs-lookup"><span data-stu-id="97f39-124">To get native commands of other types, use the **CommandType** parameter of the **Get-Command** cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="97f39-125">L'asterisco (\*) viene usato per la corrispondenza con caratteri jolly negli argomenti dei comandi di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="97f39-125">The asterisk (\*) is used for wildcard matching in Windows PowerShell command arguments.</span></span> <span data-ttu-id="97f39-126">Il carattere \* indica una corrispondenza con uno o più caratteri qualsiasi.</span><span class="sxs-lookup"><span data-stu-id="97f39-126">The \* means "match one or more of any characters".</span></span> <span data-ttu-id="97f39-127">È possibile digitare **Get-Command a\&#42;** per trovare tutti i comandi che iniziano con la lettera "a".</span><span class="sxs-lookup"><span data-stu-id="97f39-127">You can type **Get-Command a\&#42;** to find all commands that begin with the letter "a".</span></span> <span data-ttu-id="97f39-128">A differenza di quanto avviene con Cmd.exe, il carattere jolly di Windows PowerShell corrisponde anche a un punto.</span><span class="sxs-lookup"><span data-stu-id="97f39-128">Unlike wildcard matching in Cmd.exe, Windows PowerShell's wildcard will also match a period.</span></span>

<span data-ttu-id="97f39-129">Per ottenere gli alias di comandi, ovvero i nomi alternativi assegnati, digitare:</span><span class="sxs-lookup"><span data-stu-id="97f39-129">To get command aliases, which are the assigned nicknames of commands, type:</span></span>

```
Get-Command -CommandType Alias
```

<span data-ttu-id="97f39-130">Per ottenere le funzioni della sessione corrente, digitare:</span><span class="sxs-lookup"><span data-stu-id="97f39-130">To get the functions in the current session, type:</span></span>

```
Get-Command -CommandType Function
```

<span data-ttu-id="97f39-131">Per visualizzare gli script nel percorso di ricerca di Windows PowerShell, digitare:</span><span class="sxs-lookup"><span data-stu-id="97f39-131">To display scripts in Windows PowerShell's search path, type:</span></span>

```
Get-Command -CommandType Script
```

