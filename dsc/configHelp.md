---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Guida alla scrittura per le configurazioni DSC
ms.openlocfilehash: c868fa0565baff833423db090a5d62824ab4cad8
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="94812-103">Guida alla scrittura per le configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="94812-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="94812-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="94812-104">Applies To: Windows Windows PowerShell 5.0</span></span>

<span data-ttu-id="94812-105">È possibile usare la Guida basata sui commenti nelle configurazioni DSC.</span><span class="sxs-lookup"><span data-stu-id="94812-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="94812-106">Gli utenti possono accedere alla Guida chiamando la funzione di configurazione con `-?` oppure usando il cmdlet [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx).</span><span class="sxs-lookup"><span data-stu-id="94812-106">Users can access the help by calling the configuration function with `-?`, or by using the [Get-Help](https://technet.microsoft.com/en-us/library/hh849696.aspx) cmdlet.</span></span> <span data-ttu-id="94812-107">Per altre informazioni sulla Guida basata sui commenti di PowerShell, vedere [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx).</span><span class="sxs-lookup"><span data-stu-id="94812-107">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](https://technet.microsoft.com/en-us/library/hh847834.aspx).</span></span>

<span data-ttu-id="94812-108">L'esempio seguente mostra uno script che contiene una configurazione e una Guida basata su commenti per tale configurazione:</span><span class="sxs-lookup"><span data-stu-id="94812-108">The following example shows a script that contains a configuration and comment-based help for it:</span></span>

```powershell
<#
.SYNOPSIS
A brief description of the function or script. This keyword can be used only once for each configuration.


.DESCRIPTION
A detailed description of the function or script. This keyword can be used only once for each configuration.


.PARAMETER ComputerName
The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword. 
Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description. 
The description can include paragraph breaks.

The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters 
(and their descriptions) appear in help topic. To change the order, change the syntax.

.PARAMETER FilePath
Provide a PARAMETER section for each parameter that your script or function accepts.

.EXAMPLE
A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example. If you have multiple examples,
there is no need to number them. PowerShell will number the examples in help text.

.EXAMPLE
This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>

configuration HelpSample1
{
    param([string]$ComputerName,[string]$FilePath)
    File f
    {
        Contents="Hello World"
        DestinationPath = "c:\Destination.txt"
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="94812-109">Visualizzazione della Guida di configurazione</span><span class="sxs-lookup"><span data-stu-id="94812-109">Viewing configuration help</span></span>

<span data-ttu-id="94812-110">Per visualizzare la Guida per una configurazione, usare il cmdlet **Get-Help** con il nome della funzione oppure digitare il nome della funzione seguito da `-?`.</span><span class="sxs-lookup"><span data-stu-id="94812-110">To view the help for a configuration, use the **Get-Help** cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="94812-111">Di seguito viene riportato l'output della funzione precedente quando viene passato a **Get-Help**:</span><span class="sxs-lookup"><span data-stu-id="94812-111">The following is the output of the previous function when passed to **Get-Help**:</span></span>

```powershell
PS C:\> Get-Help HelpSample1

NAME
    HelpSample1
    
SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.
    
    
SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] 
    <String>] [[-FilePath] <String>] [<CommonParameters>]
    
    
DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.
    

RELATED LINKS

REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

## <a name="see-also"></a><span data-ttu-id="94812-112">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="94812-112">See Also</span></span>
* [<span data-ttu-id="94812-113">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="94812-113">DSC Configurations</span></span>](configurations.md)

