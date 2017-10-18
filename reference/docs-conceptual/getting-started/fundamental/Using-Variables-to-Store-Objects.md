---
ms.date: 2017-06-05
keywords: powershell,cmdlet
title: Uso di variabili per l'archiviazione di oggetti
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 9a95d421fa2686608a565987c16fecc41c3c6d20
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/13/2017
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="c67ce-103">Uso di variabili per l'archiviazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="c67ce-103">Using Variables to Store Objects</span></span>
<span data-ttu-id="c67ce-104">PowerShell opera sugli oggetti.</span><span class="sxs-lookup"><span data-stu-id="c67ce-104">PowerShell works with objects.</span></span> <span data-ttu-id="c67ce-105">PowerShell consente di creare variabili, fondamentalmente oggetti denominati, per salvare l'output in modo da portelo usare in seguito.</span><span class="sxs-lookup"><span data-stu-id="c67ce-105">PowerShell lets you create variables, essentially named objects, to preserve output for later use.</span></span> <span data-ttu-id="c67ce-106">Se si è abituati a usare le variabili in altre shell, tenere presente che le variabili di PowerShell sono oggetti e non testo.</span><span class="sxs-lookup"><span data-stu-id="c67ce-106">If you are used to working with variables in other shells remember that PowerShell variables are objects, not text.</span></span>

<span data-ttu-id="c67ce-107">Le variabili vengono sempre specificate con il carattere iniziale $ e possono includere qualsiasi carattere alfanumerico o carattere di sottolineatura nei nomi.</span><span class="sxs-lookup"><span data-stu-id="c67ce-107">Variables are always specified with the initial character $, and can include any alphanumeric characters or the underscore in their names.</span></span>

### <a name="creating-a-variable"></a><span data-ttu-id="c67ce-108">Creazione di una variabile</span><span class="sxs-lookup"><span data-stu-id="c67ce-108">Creating a Variable</span></span>
<span data-ttu-id="c67ce-109">È possibile creare una variabile digitando un nome di variabile valido:</span><span class="sxs-lookup"><span data-stu-id="c67ce-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="c67ce-110">Non verrà restituito alcun risultato perché **$loc** non ha un valore.</span><span class="sxs-lookup"><span data-stu-id="c67ce-110">This returns no result because **$loc** does not have a value.</span></span> <span data-ttu-id="c67ce-111">È possibile creare una variabile e assegnarle un valore nello stesso passaggio.</span><span class="sxs-lookup"><span data-stu-id="c67ce-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="c67ce-112">PowerShell crea la variabile solo se non esiste. In caso contrario, assegna il valore specificato alla variabile esistente.</span><span class="sxs-lookup"><span data-stu-id="c67ce-112">PowerShell only creates the variable if it does not exist; otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="c67ce-113">Per archiviare la posizione corrente nella variabile **$loc**, digitare:</span><span class="sxs-lookup"><span data-stu-id="c67ce-113">To store your current location in the variable **$loc**, type:</span></span>

```
$loc = Get-Location
```

<span data-ttu-id="c67ce-114">Non viene visualizzato alcun output quando si digita il comando perché l'output viene inviato a $loc.</span><span class="sxs-lookup"><span data-stu-id="c67ce-114">There is no output displayed when you type this command because the output is sent to $loc.</span></span> <span data-ttu-id="c67ce-115">In PowerShell l'output visualizzato è un effetto collaterale del fatto che i dati non indirizzati diversamente vengono sempre inviati allo schermo.</span><span class="sxs-lookup"><span data-stu-id="c67ce-115">In PowerShell, displayed output is a side effect of the fact that data, which is not otherwise directed, always gets sent to the screen.</span></span> <span data-ttu-id="c67ce-116">Digitando $loc verrà visualizzata la posizione corrente:</span><span class="sxs-lookup"><span data-stu-id="c67ce-116">Typing $loc will show your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="c67ce-117">È possibile usare **Get-Member** per visualizzare informazioni sul contenuto delle variabili.</span><span class="sxs-lookup"><span data-stu-id="c67ce-117">You can use **Get-Member** to display information about the contents of variables.</span></span> <span data-ttu-id="c67ce-118">L'invio attraverso la pipe di $loc a Get-Member indicherà che si tratta di un oggetto **PathInfo**, proprio come l'output da Get-Location:</span><span class="sxs-lookup"><span data-stu-id="c67ce-118">Piping $loc to Get-Member will show you that it is a **PathInfo** object, just like the output from Get-Location:</span></span>

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a><span data-ttu-id="c67ce-119">Manipolazione delle variabili</span><span class="sxs-lookup"><span data-stu-id="c67ce-119">Manipulating Variables</span></span>
<span data-ttu-id="c67ce-120">PowerShell include diversi comandi per la manipolazione delle variabili.</span><span class="sxs-lookup"><span data-stu-id="c67ce-120">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="c67ce-121">È possibile visualizzare un elenco completo in un formato leggibile digitando:</span><span class="sxs-lookup"><span data-stu-id="c67ce-121">You can see a complete listing in a readable form by typing:</span></span>

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="c67ce-122">Oltre alle variabili create nella sessione corrente di PowerShell, esistono diverse variabili definite dal sistema.</span><span class="sxs-lookup"><span data-stu-id="c67ce-122">In addition to the variables you create in your current PowerShell session, there are several system-defined variables.</span></span> <span data-ttu-id="c67ce-123">È possibile usare il cmdlet **Remove-Variable** per cancellare tutte le variabili non controllate da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c67ce-123">You can use the **Remove-Variable** cmdlet to clear out all of the variables which are not controlled by PowerShell.</span></span> <span data-ttu-id="c67ce-124">Digitare il comando seguente per cancellare tutte le variabili:</span><span class="sxs-lookup"><span data-stu-id="c67ce-124">Type the following command to clear all variables:</span></span>

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="c67ce-125">Verrà restituito il prompt di conferma visualizzato di seguito.</span><span class="sxs-lookup"><span data-stu-id="c67ce-125">This will produce the confirmation prompt you see below.</span></span>

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

<span data-ttu-id="c67ce-126">Se si esegue poi il cmdlet **Get-Variable**, verranno visualizzate le variabili di PowerShell rimanenti.</span><span class="sxs-lookup"><span data-stu-id="c67ce-126">If you then run the **Get-Variable** cmdlet, you will see the remaining PowerShell variables.</span></span> <span data-ttu-id="c67ce-127">Dato che esiste anche un'unità di PowerShell per le variabili, è possibile visualizzare tutte le variabili di PowerShell anche digitando:</span><span class="sxs-lookup"><span data-stu-id="c67ce-127">Since there is also a variable PowerShell drive, you can also display all PowerShell variables by typing:</span></span>

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a><span data-ttu-id="c67ce-128">Uso delle variabili di Cmd.exe</span><span class="sxs-lookup"><span data-stu-id="c67ce-128">Using Cmd.exe Variables</span></span>
<span data-ttu-id="c67ce-129">Anche se PowerShell non è Cmd.exe, viene eseguito in un ambiente della shell di comando e può usare le stesse variabili disponibili in qualsiasi ambiente in Windows.</span><span class="sxs-lookup"><span data-stu-id="c67ce-129">Although PowerShell is not Cmd.exe, it runs in a command shell environment and can use the same variables available in any environment in Windows.</span></span> <span data-ttu-id="c67ce-130">Queste variabili vengono esposte tramite un'unità denominata **env:**.</span><span class="sxs-lookup"><span data-stu-id="c67ce-130">These variables are exposed through a drive named **env**:.</span></span> <span data-ttu-id="c67ce-131">È possibile visualizzare queste variabili digitando:</span><span class="sxs-lookup"><span data-stu-id="c67ce-131">You can view these variables by typing:</span></span>

```
Get-ChildItem env:
```

<span data-ttu-id="c67ce-132">Sebbene i cmdlet per le variabili standard non siano progettati per l'utilizzo con le variabili **env:**, è comunque possibile usarle specificando il prefisso **env:**.</span><span class="sxs-lookup"><span data-stu-id="c67ce-132">Although the standard variable cmdlets are not designed to work with **env:** variables, you can still use them by specifying the **env:** prefix.</span></span> <span data-ttu-id="c67ce-133">Per visualizzare la directory radice del sistema operativo, ad esempio, è possibile usare la variabile **%SystemRoot%** della shell dei comandi da PowerShell digitando:</span><span class="sxs-lookup"><span data-stu-id="c67ce-133">For example, to see the operating system root directory, you can use the command-shell **%SystemRoot%** variable from within PowerShell by typing:</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="c67ce-134">È anche possibile creare e modificare le variabili di ambiente da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c67ce-134">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="c67ce-135">Le variabili di ambiente a cui si accede da Windows PowerShell rispettano le normali regole per le variabili di ambiente valide in altre posizioni in Windows.</span><span class="sxs-lookup"><span data-stu-id="c67ce-135">Environment variables accessed from Windows PowerShell conform to the normal rules for environment variables elsewhere in Windows.</span></span>

