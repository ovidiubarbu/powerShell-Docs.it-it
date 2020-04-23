---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Uso di variabili per l'archiviazione di oggetti
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030364"
---
# <a name="using-variables-to-store-objects"></a><span data-ttu-id="44a3b-103">Uso di variabili per l'archiviazione di oggetti</span><span class="sxs-lookup"><span data-stu-id="44a3b-103">Using variables to store objects</span></span>

<span data-ttu-id="44a3b-104">PowerShell opera sugli oggetti.</span><span class="sxs-lookup"><span data-stu-id="44a3b-104">PowerShell works with objects.</span></span> <span data-ttu-id="44a3b-105">PowerShell permette di creare oggetti denominati noti come variabili.</span><span class="sxs-lookup"><span data-stu-id="44a3b-105">PowerShell lets you create named objects known as variables.</span></span>
<span data-ttu-id="44a3b-106">I nomi delle variabili possono includere il carattere di sottolineatura e qualsiasi carattere alfanumerico.</span><span class="sxs-lookup"><span data-stu-id="44a3b-106">Variable names can include the underscore character and any alphanumeric characters.</span></span> <span data-ttu-id="44a3b-107">Se usata in PowerShell, una variabile viene sempre specificata tramite il carattere \$ seguito dal nome della variabile.</span><span class="sxs-lookup"><span data-stu-id="44a3b-107">When used in PowerShell, a variable is always specified using the \$ character followed by variable name.</span></span>

## <a name="creating-a-variable"></a><span data-ttu-id="44a3b-108">Creazione di una variabile</span><span class="sxs-lookup"><span data-stu-id="44a3b-108">Creating a variable</span></span>

<span data-ttu-id="44a3b-109">È possibile creare una variabile digitando un nome di variabile valido:</span><span class="sxs-lookup"><span data-stu-id="44a3b-109">You can create a variable by typing a valid variable name:</span></span>

```
PS> $loc
PS>
```

<span data-ttu-id="44a3b-110">Questo esempio non restituisce alcun risultato, perché `$loc` non ha un valore.</span><span class="sxs-lookup"><span data-stu-id="44a3b-110">This example returns no result because `$loc` doesn't have a value.</span></span> <span data-ttu-id="44a3b-111">È possibile creare una variabile e assegnarle un valore nello stesso passaggio.</span><span class="sxs-lookup"><span data-stu-id="44a3b-111">You can create a variable and assign it a value in the same step.</span></span> <span data-ttu-id="44a3b-112">PowerShell crea la variabile solo se non esiste.</span><span class="sxs-lookup"><span data-stu-id="44a3b-112">PowerShell only creates the variable if it doesn't exist.</span></span>
<span data-ttu-id="44a3b-113">In caso contrario, assegna il valore specificato alla variabile esistente.</span><span class="sxs-lookup"><span data-stu-id="44a3b-113">Otherwise, it assigns the specified value to the existing variable.</span></span> <span data-ttu-id="44a3b-114">L'esempio seguente archivia il percorso corrente nella variabile `$loc`:</span><span class="sxs-lookup"><span data-stu-id="44a3b-114">The following example stores the current location in the variable `$loc`:</span></span>

```powershell
$loc = Get-Location
```

<span data-ttu-id="44a3b-115">Quando si digita questo comando, PowerShell non visualizza alcun output.</span><span class="sxs-lookup"><span data-stu-id="44a3b-115">PowerShell displays no output when you type this command.</span></span> <span data-ttu-id="44a3b-116">PowerShell invia l'output di "Get-Location" a `$loc`.</span><span class="sxs-lookup"><span data-stu-id="44a3b-116">PowerShell sends the output of 'Get-Location' to `$loc`.</span></span> <span data-ttu-id="44a3b-117">In PowerShell i dati che non vengono assegnati o reindirizzati vengono inviati allo schermo.</span><span class="sxs-lookup"><span data-stu-id="44a3b-117">In PowerShell, data that isn't assigned or redirected is sent to the screen.</span></span> <span data-ttu-id="44a3b-118">Se si digita `$loc`, viene visualizzato il percorso corrente:</span><span class="sxs-lookup"><span data-stu-id="44a3b-118">Typing `$loc` shows your current location:</span></span>

```
PS> $loc

Path
----
C:\temp
```

<span data-ttu-id="44a3b-119">È possibile usare `Get-Member` per visualizzare informazioni sul contenuto delle variabili.</span><span class="sxs-lookup"><span data-stu-id="44a3b-119">You can use `Get-Member` to display information about the contents of variables.</span></span> <span data-ttu-id="44a3b-120">`Get-Member` mostra che `$loc` è un oggetto **PathInfo**, proprio come l'output di `Get-Location`:</span><span class="sxs-lookup"><span data-stu-id="44a3b-120">`Get-Member` shows you that `$loc` is a **PathInfo** object, just like the output from `Get-Location`:</span></span>

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a><span data-ttu-id="44a3b-121">Modifica delle variabili</span><span class="sxs-lookup"><span data-stu-id="44a3b-121">Manipulating variables</span></span>

<span data-ttu-id="44a3b-122">PowerShell include diversi comandi per la manipolazione delle variabili.</span><span class="sxs-lookup"><span data-stu-id="44a3b-122">PowerShell provides several commands to manipulate variables.</span></span> <span data-ttu-id="44a3b-123">È possibile visualizzare un elenco completo in un formato leggibile digitando:</span><span class="sxs-lookup"><span data-stu-id="44a3b-123">You can see a complete listing in a readable form by typing:</span></span>

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

<span data-ttu-id="44a3b-124">PowerShell crea anche diverse variabili definite dal sistema.</span><span class="sxs-lookup"><span data-stu-id="44a3b-124">PowerShell also creates several system-defined variables.</span></span> <span data-ttu-id="44a3b-125">È possibile usare il cmdlet `Remove-Variable` per rimuovere dalla sessione corrente le variabili che non sono controllate da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44a3b-125">You can use the `Remove-Variable` cmdlet to remove variables, which are not controlled by PowerShell, from the current session.</span></span> <span data-ttu-id="44a3b-126">Digitare il comando seguente per cancellare tutte le variabili:</span><span class="sxs-lookup"><span data-stu-id="44a3b-126">Type the following command to clear all variables:</span></span>

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

<span data-ttu-id="44a3b-127">Dopo aver eseguito il comando precedente, il cmdlet `Get-Variable` mostra le variabili di sistema di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44a3b-127">After running the previous command, the `Get-Variable` cmdlet shows the PowerShell system variables.</span></span>

<span data-ttu-id="44a3b-128">PowerShell crea anche un'unità di variabili.</span><span class="sxs-lookup"><span data-stu-id="44a3b-128">PowerShell also creates a variable drive.</span></span> <span data-ttu-id="44a3b-129">Usare l'esempio seguente per visualizzare tutte le variabili di PowerShell usando l'unità delle variabili:</span><span class="sxs-lookup"><span data-stu-id="44a3b-129">Use the following example to display all PowerShell variables using the variable drive:</span></span>

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a><span data-ttu-id="44a3b-130">Uso di variabili di cmd.exe</span><span class="sxs-lookup"><span data-stu-id="44a3b-130">Using cmd.exe variables</span></span>

<span data-ttu-id="44a3b-131">PowerShell può usare le stesse variabili di ambiente disponibili per qualsiasi processo Windows, incluso **cmd.exe**.</span><span class="sxs-lookup"><span data-stu-id="44a3b-131">PowerShell can use the same environment variables available to any Windows process, including **cmd.exe**.</span></span> <span data-ttu-id="44a3b-132">Queste variabili vengono esposte tramite un'unità denominata `env:`.</span><span class="sxs-lookup"><span data-stu-id="44a3b-132">These variables are exposed through a drive named `env:`.</span></span> <span data-ttu-id="44a3b-133">È possibile visualizzare queste variabili digitando il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="44a3b-133">You can view these variables by typing the following command:</span></span>

```powershell
Get-ChildItem env:
```

<span data-ttu-id="44a3b-134">I cmdlet `*-Variable` standard non sono progettati per funzionare con variabili di ambiente.</span><span class="sxs-lookup"><span data-stu-id="44a3b-134">The standard `*-Variable` cmdlets aren't designed to work with environment variables.</span></span> <span data-ttu-id="44a3b-135">È possibile accedere alle variabili di ambiente usando il prefisso di unità `env:`.</span><span class="sxs-lookup"><span data-stu-id="44a3b-135">Environment variables are accessed using the `env:` drive prefix.</span></span> <span data-ttu-id="44a3b-136">Ad esempio, la variabile **%SystemRoot%** in **cmd.exe** contiene il nome della directory radice del sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="44a3b-136">For example, the **%SystemRoot%** variable in **cmd.exe** contains the operating system's root directory name.</span></span> <span data-ttu-id="44a3b-137">In PowerShell è possibile usare `$env:SystemRoot` per accedere allo stesso valore.</span><span class="sxs-lookup"><span data-stu-id="44a3b-137">In PowerShell, you use `$env:SystemRoot` to access the same value.</span></span>

```
PS> $env:SystemRoot
C:\WINDOWS
```

<span data-ttu-id="44a3b-138">È anche possibile creare e modificare le variabili di ambiente da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="44a3b-138">You can also create and modify environment variables from within PowerShell.</span></span> <span data-ttu-id="44a3b-139">Le variabili di ambiente in PowerShell seguono le stesse regole per le variabili di ambiente usate altrove nel sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="44a3b-139">Environment variables in PowerShell follow the same rules for environment variables used elsewhere in the operating system.</span></span> <span data-ttu-id="44a3b-140">L'esempio seguente crea una nuova variabile di ambiente:</span><span class="sxs-lookup"><span data-stu-id="44a3b-140">The following example creates a new environment variable:</span></span>

```powershell
$env:LIB_PATH='/usr/local/lib'
```

<span data-ttu-id="44a3b-141">Benché non sia necessario, spesso i nomi delle variabili di ambiente usano tutte lettere maiuscole.</span><span class="sxs-lookup"><span data-stu-id="44a3b-141">Though not required, it's common for environment variable names to use all uppercase letters.</span></span>
