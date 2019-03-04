---
title: Esempi della Guida basata sui commenti | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 868194a2-17e9-4184-bc36-c04a33f26494
caps.latest.revision: 4
ms.openlocfilehash: dbccaf5b8e48a1c4d924bc0ec4ea09b25e10adf0
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56857967"
---
# <a name="examples-of-comment-based-help"></a><span data-ttu-id="8e8f9-102">Esempi della Guida basata sui commenti</span><span class="sxs-lookup"><span data-stu-id="8e8f9-102">Examples of Comment-Based Help</span></span>

<span data-ttu-id="8e8f9-103">In questo argomento include l'esempio che illustrano come usare la Guida basata su commenti per funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-103">This topic includes example that demonstrate how to use comment-based help for scripts and functions.</span></span>

## <a name="example-1-comment-based-help-for-a-function"></a><span data-ttu-id="8e8f9-104">Esempio 1: Guida basata su commenti per una funzione</span><span class="sxs-lookup"><span data-stu-id="8e8f9-104">Example 1: Comment-Based Help for a Function</span></span>

 <span data-ttu-id="8e8f9-105">La funzione di esempio seguente include la Guida basata sui commenti.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-105">The following sample function includes comment-based Help.</span></span>

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

<span data-ttu-id="8e8f9-106">L'output seguente mostra i risultati di un comando Get-Help che consente di visualizzare la Guida per la funzione Aggiungi estensione.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-106">The following output shows the results of a Get-Help command that displays the help for the Add-Extension function.</span></span>

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

## <a name="example-2-comment-based-help-for-a-script"></a><span data-ttu-id="8e8f9-107">Esempio 2: Guida basata su commenti per uno Script</span><span class="sxs-lookup"><span data-stu-id="8e8f9-107">Example 2: Comment-Based Help for a Script</span></span>

<span data-ttu-id="8e8f9-108">La funzione di esempio seguente include la Guida basata sui commenti.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-108">The following sample function includes comment-based Help.</span></span>

<span data-ttu-id="8e8f9-109">Si noti che le righe vuote tra la chiusura **#>** e il `Param` istruzione.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-109">Notice the blank lines between the closing **#>** and the `Param` statement.</span></span> <span data-ttu-id="8e8f9-110">In uno script che non ha un `Param` istruzione, deve esserci almeno due righe vuote tra il commento finale dell'argomento della Guida e la prima dichiarazione di funzione.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-110">In a script that does not have a `Param` statement, there must be at least two blank lines between the final comment in the Help topic and the first function declaration.</span></span> <span data-ttu-id="8e8f9-111">Senza queste righe vuote, Get-Help associa l'argomento della Guida con la funzione, anziché lo script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-111">Without these blank lines, Get-Help associates the Help topic with the function, instead of the script.</span></span>

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

<span data-ttu-id="8e8f9-112">Il comando seguente ottiene lo script Help.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-112">The following command gets the script Help.</span></span> <span data-ttu-id="8e8f9-113">Poiché lo script non è n una directory in cui è elencata nella variabile di ambiente Path, il comando Get-Help che ottiene lo script Help deve specificare il percorso dello script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-113">Because the script is not n a directory that is listed in the Path environment variable, the Get-Help command that gets the script Help must specify the script path.</span></span>

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

## <a name="example-3-parameter-descriptions-in-a-param-statement"></a><span data-ttu-id="8e8f9-114">Esempio 3: Descrizioni dei parametri in un'istruzione Param</span><span class="sxs-lookup"><span data-stu-id="8e8f9-114">Example 3: Parameter Descriptions in a Param Statement</span></span>

<span data-ttu-id="8e8f9-115">In questo esempio mostra come inserire parameterdescriptions nel `Param` istruzione di una funzione o script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-115">This example show how to insert parameterdescriptions in the `Param` statement of a function or script.</span></span> <span data-ttu-id="8e8f9-116">Questo formato è particolarmente utile quando le descrizioni dei parametri sono brevi.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-116">This format is most useful when the parameter descriptions are brief.</span></span>

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

<span data-ttu-id="8e8f9-117">I risultati sono gli stessi dei risultati, ad esempio 1.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-117">The results are the same as the results for Example 1.</span></span> <span data-ttu-id="8e8f9-118">Get-Help interpreta le descrizioni dei parametri come se si sono accompagnati dal `.Parameter` (parola chiave).</span><span class="sxs-lookup"><span data-stu-id="8e8f9-118">Get-Help interprets the parameter descriptions as though they were accompanied by the `.Parameter` keyword.</span></span>

## <a name="example-4--redirecting-to-an-xml-file"></a><span data-ttu-id="8e8f9-119">Esempio 4:  Il reindirizzamento a un File XML</span><span class="sxs-lookup"><span data-stu-id="8e8f9-119">Example 4:  Redirecting to an XML File</span></span>

<span data-ttu-id="8e8f9-120">È possibile scrivere argomenti della Guida basati su XML per le funzioni e script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-120">You can write XML-based Help topics for functions and scripts.</span></span> <span data-ttu-id="8e8f9-121">Anche se la Guida basata sui commenti è più facile da implementare, Guida basata su XML è necessaria se si desidera maggiore controllo sul contenuto della Guida o se tradurre gli argomenti della Guida in più lingue. Nell'esempio seguente mostra le prime righe dello script di aggiornamento Month.ps1.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-121">Although comment-based Help is easier to implement, XML-based Help is required if you want more precise control over Help content or if you are translating Help topics into multiple languages.The following example shows the first few lines of the Update-Month.ps1 script.</span></span> <span data-ttu-id="8e8f9-122">Lo script Usa i `.ExternalHelp` (parola chiave) per specificare il percorso a un argomento basato su XML per lo script.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-122">The script uses the `.ExternalHelp` keyword to specify the path to an XML-based Help topic for the script.</span></span>

```powershell
#  .ExternalHelp C:\MyScripts\Update-Month-Help.xml

    param ([string]$InputPath, [string]$OutPutPath)

    function Get-Data { }
```

<span data-ttu-id="8e8f9-123">L'esempio seguente illustra l'uso del `.ExternalHelp` parola chiave in una funzione.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-123">The following example shows the use of the `.ExternalHelp` keyword in a function.</span></span>

```powershell
function Add-Extension
{
    param ([string] $name, [string]$extension = "txt")
    $name = $name + "." + $extension
    $name

    # .ExternalHelp C:\ps-test\Add-Extension.xml
}
```

## <a name="example-5--redirecting-to-a-different-help-topic"></a><span data-ttu-id="8e8f9-124">Esempio 5:  Il reindirizzamento a un altro argomento della Guida</span><span class="sxs-lookup"><span data-stu-id="8e8f9-124">Example 5:  Redirecting to a Different Help Topic</span></span>

<span data-ttu-id="8e8f9-125">Il codice seguente è tratto dall'inizio del predefiniti `Help` (funzione) in Windows PowerShell, che visualizza una schermata del testo della Guida alla volta.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-125">The following code is an excerpt from the beginning of the built-in `Help` function in Windows PowerShell, which displays one screen of Help text at a time.</span></span> <span data-ttu-id="8e8f9-126">Poiché l'argomento della Guida per il cmdlet Get-Help viene descritta la funzione di Guida in linea, la funzione Help Usa la `.ForwardHelpTargetName` e `.ForwardHelpCategory` parole chiave per reindirizzare l'utente all'argomento della Guida del cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-126">Because the Help topic for the Get-Help cmdlet describes the Help function, the Help function uses the `.ForwardHelpTargetName` and `.ForwardHelpCategory` keywords to redirect the user to the Get-Help cmdlet Help topic.</span></span>

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

<span data-ttu-id="8e8f9-127">Il comando seguente usa questa funzionalità.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-127">The following command uses this feature.</span></span> <span data-ttu-id="8e8f9-128">Quando un utente digita un comando Get-Help per la funzione Help, Get-Help Visualizza l'argomento della Guida per il cmdlet Get-Help.</span><span class="sxs-lookup"><span data-stu-id="8e8f9-128">When a user types a Get-Help command for the Help function, Get-Help displays the Help topic for the Get-Help cmdlet.</span></span>

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