---
title: Esempi di guida basata su Commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: 30e98bfcf06b1720005a73ee8294aeba7e1ae066
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72367820"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="3d9df-102">Esempi della Guida basata sui commenti</span><span class="sxs-lookup"><span data-stu-id="3d9df-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="3d9df-103">Questo argomento include esempi che illustrano come usare la guida basata su commenti per gli script e le funzioni.</span><span class="sxs-lookup"><span data-stu-id="3d9df-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="3d9df-104">Esempio 1: Guida basata su commenti per una funzione</span><span class="sxs-lookup"><span data-stu-id="3d9df-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="3d9df-105">La funzione di esempio seguente include la guida basata su commenti.</span><span class="sxs-lookup"><span data-stu-id="3d9df-105">The following sample function includes comment-based Help.</span></span>

```powershell
function Add-Extension
{
    param ([string]$Name,[string]$Extension = "txt")
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.

        .DESCRIPTION
        Adds a file name extension to a supplied name.
        Takes any strings for the file name or extension.

        .PARAMETER Name
        Specifies the file name.

        .PARAMETER Extension
        Specifies the extension. "Txt" is the default.

        .INPUTS
        None. You cannot pipe objects to Add-Extension.

        .OUTPUTS
        System.String. Add-Extension returns a string with the extension or file name.

        .EXAMPLE
        C:\PS> extension -name "File"
        File.txt

        .EXAMPLE
        C:\PS> extension -name "File" -extension "doc"
        File.doc

        .EXAMPLE
        C:\PS> extension "File" "doc"
        File.doc

        .LINK
        Online version: http://www.fabrikam.com/extension.html

        .LINK
        Set-Item
    #>
}
```

<span data-ttu-id="3d9df-106">L'output seguente mostra i risultati di un comando Get-Help che visualizza la guida per la funzione Add-Extension.</span><span class="sxs-lookup"><span data-stu-id="3d9df-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

```powershell
C:\PS> get-help add-extension -full
```

```output
        NAME
            Add-Extension

        SYNOPSIS
            Adds a file name extension to a supplied name.

        SYNTAX
            Add-Extension [[-Name] <String>] [[-Extension] <String>] [<CommonParameters>]

        DESCRIPTION
            Adds a file name extension to a supplied name. Takes any strings for the file name or extension.

        PARAMETERS
           -Name
               Specifies the file name.

               Required?                    false
               Position?                    0
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

           -Extension
               Specifies the extension. "Txt" is the default.

               Required?                    false
               Position?                    1
               Default value
               Accept pipeline input?       false
               Accept wildcard characters?

            <CommonParameters>
               This cmdlet supports the common parameters: -Verbose, -Debug,
               -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
               -OutBuffer and -OutVariable. For more information, type
               "get-help about_commonparameters".

        INPUTS
            None. You cannot pipe objects to Add-Extension.

        OUTPUTS
            System.String. Add-Extension returns a string with the extension or file name.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> extension -name "File"
            File.txt

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> extension -name "File" -extension "doc"
            File.doc

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> extension "File" "doc"
            File.doc

        RELATED LINKS
            Online version: http://www.fabrikam.com/extension.html
            Set-Item
```

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="3d9df-107">Esempio 2: Guida basata su commenti per uno script</span><span class="sxs-lookup"><span data-stu-id="3d9df-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="3d9df-108">La funzione di esempio seguente include la guida basata su commenti.</span><span class="sxs-lookup"><span data-stu-id="3d9df-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="3d9df-109">Si notino le righe vuote tra il **#>** di chiusura e l'istruzione `Param`.</span><span class="sxs-lookup"><span data-stu-id="3d9df-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="3d9df-110">In uno script che non include un'istruzione `Param`, è necessario che esistano almeno due righe vuote tra il commento finale nell'argomento della guida e la prima dichiarazione di funzione.</span><span class="sxs-lookup"><span data-stu-id="3d9df-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="3d9df-111">Senza queste righe vuote, Get-Help associa l'argomento della Guida alla funzione, invece dello script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

```powershell
<#
  .SYNOPSIS
  Performs monthly data updates.

  .DESCRIPTION
  The Update-Month.ps1 script updates the registry with new data generated
  during the past month and generates a report.

  .PARAMETER InputPath
  Specifies the path to the CSV-based input file.

  .PARAMETER OutputPath
  Specifies the name and path for the CSV-based output file. By default,
  MonthlyUpdates.ps1 generates a name from the date and time it runs, and
  saves the output in the local directory.

  .INPUTS
  None. You cannot pipe objects to Update-Month.ps1.

  .OUTPUTS
  None. Update-Month.ps1 does not generate any output.

  .EXAMPLE
  C:\PS> .\Update-Month.ps1

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

  .EXAMPLE
  C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath C:\Reports\2009\January.csv
#>

param ([string]$InputPath, [string]$OutPutPath)

function Get-Data { }
```

<span data-ttu-id="3d9df-112">Il comando seguente ottiene la guida per gli script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-112">The following command gets the script Help.</span></span> <span data-ttu-id="3d9df-113">Poiché lo script non è una directory elencata nella variabile di ambiente PATH, il comando Get-Help che ottiene la guida per lo script deve specificare il percorso dello script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

```powershell
C:\PS> get-help c:\ps-test\update-month.ps1 -full
```

```output
            NAME
                C:\ps-test\Update-Month.ps1

            SYNOPSIS
                Performs monthly data updates.

            SYNTAX
                C:\ps-test\Update-Month.ps1 [-InputPath] <String> [[-OutputPath]
                <String>] [<CommonParameters>]

            DESCRIPTION
                The Update-Month.ps1 script updates the registry with new data
                generated during the past month and generates a report.

            PARAMETERS
               -InputPath
                   Specifies the path to the CSV-based input file.

                   Required?                    true
                   Position?                    0
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               -OutputPath
                   Specifies the name and path for the CSV-based output file. By
                   default, MonthlyUpdates.ps1 generates a name from the date
                   and time it runs, and saves the output in the local directory.

                   Required?                    false
                   Position?                    1
                   Default value
                   Accept pipeline input?       false
                   Accept wildcard characters?

               <CommonParameters>
                   This cmdlet supports the common parameters: -Verbose, -Debug,
                   -ErrorAction, -ErrorVariable, -WarningAction, -WarningVariable,
                   -OutBuffer and -OutVariable. For more information, type,
                   "get-help about_commonparameters".

            INPUTS
                   None. You cannot pipe objects to Update-Month.ps1.

            OUTPUTS
                   None. Update-Month.ps1 does not generate any output.

            -------------------------- EXAMPLE 1 --------------------------

            C:\PS> .\Update-Month.ps1

            -------------------------- EXAMPLE 2 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv

            -------------------------- EXAMPLE 3 --------------------------

            C:\PS> .\Update-Month.ps1 -inputpath C:\Data\January.csv -outputPath
            C:\Reports\2009\January.csv

            RELATED LINKS
```

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="3d9df-114">Esempio 3: descrizioni dei parametri in un'istruzione param</span><span class="sxs-lookup"><span data-stu-id="3d9df-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="3d9df-115">Questo esempio illustra come inserire ParameterDescriptions nell'istruzione `Param` di una funzione o di uno script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="3d9df-116">Questo formato è particolarmente utile quando le descrizioni dei parametri sono brevi.</span><span class="sxs-lookup"><span data-stu-id="3d9df-116">This format is most useful when the parameter descriptions are brief.</span></span>

```powershell
function Add-Extension
{
    param
    (
        [string]
        # Specifies the file name.
        $name,

        [string]
        # Specifies the file name extension. "Txt" is the default.
        $extension = "txt"
    )
    $name = $name + "." + $extension
    $name

    <#
        .SYNOPSIS
        Adds a file name extension to a supplied name.
...
    #>
```

<span data-ttu-id="3d9df-117">I risultati corrispondono ai risultati dell'esempio 1.</span><span class="sxs-lookup"><span data-stu-id="3d9df-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="3d9df-118">Get-Help interpreta le descrizioni dei parametri come se fossero accompagnati dalla parola chiave `.Parameter`.</span><span class="sxs-lookup"><span data-stu-id="3d9df-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="3d9df-119">Esempio 4: Reindirizzamento a un file XML</span><span class="sxs-lookup"><span data-stu-id="3d9df-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="3d9df-120">È possibile scrivere argomenti della Guida basati su XML per funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="3d9df-121">Sebbene la guida basata su commenti sia più semplice da implementare, la guida basata su XML è necessaria se si desidera un controllo più preciso sul contenuto della guida o se si stanno traducendo argomenti della Guida in più lingue. Nell'esempio seguente vengono illustrate le prime righe dello script Update-Month. ps1.</span><span class="sxs-lookup"><span data-stu-id="3d9df-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="3d9df-122">Lo script utilizza la parola chiave `.ExternalHelp` per specificare il percorso di un argomento della guida basato su XML per lo script.</span><span class="sxs-lookup"><span data-stu-id="3d9df-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="3d9df-123">Nell'esempio seguente viene illustrato l'utilizzo della parola chiave `.ExternalHelp` in una funzione.</span><span class="sxs-lookup"><span data-stu-id="3d9df-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="3d9df-124">Esempio 5: Reindirizzamento a un argomento della Guida diverso</span><span class="sxs-lookup"><span data-stu-id="3d9df-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="3d9df-125">Il codice seguente è un estratto dall'inizio della funzione `Help` incorporata in Windows PowerShell, che visualizza una schermata del testo della Guida alla volta.</span><span class="sxs-lookup"><span data-stu-id="3d9df-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="3d9df-126">Poiché l'argomento della Guida per il cmdlet Get-Help descrive la funzione Help, la funzione Help usa le parole chiave `.ForwardHelpTargetName` e `.ForwardHelpCategory` per reindirizzare l'utente all'argomento della guida del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="3d9df-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

```powershell
function help
{

    <#
      .FORWARDHELPTARGETNAME Get-Help
      .FORWARDHELPCATEGORY Cmdlet
    #>
    [CmdletBinding(DefaultParameterSetName='AllUsersView')]
    param(
            [Parameter(Position=0, ValueFromPipelineByPropertyName=$true)]
            [System.String]
            ${Name},
    ...
```

<span data-ttu-id="3d9df-127">Il comando seguente usa questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="3d9df-127">The following command uses this feature.</span></span> <span data-ttu-id="3d9df-128">Quando un utente digita un comando Get-Help per la funzione Help, Get-Help Visualizza l'argomento della Guida per il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="3d9df-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

```powershell
C:\PS> get-help help
```

```output
            NAME
                Get-Help

            SYNOPSIS
                Displays information about Windows PowerShell cmdlets and concepts.
            ...
```