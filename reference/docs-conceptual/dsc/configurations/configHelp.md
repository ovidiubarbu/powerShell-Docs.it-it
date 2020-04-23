---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Guida alla scrittura per le configurazioni DSC
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954138"
---
# <a name="writing-help-for-dsc-configurations"></a><span data-ttu-id="b5954-103">Guida alla scrittura per le configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="b5954-103">Writing help for DSC configurations</span></span>

><span data-ttu-id="b5954-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b5954-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="b5954-105">È possibile usare la Guida basata sui commenti nelle configurazioni DSC.</span><span class="sxs-lookup"><span data-stu-id="b5954-105">You can use comment-based help in DSC configurations.</span></span> <span data-ttu-id="b5954-106">Gli utenti possono accedere alla Guida chiamando **Configuration** con `-?` oppure usando il cmdlet [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help).</span><span class="sxs-lookup"><span data-stu-id="b5954-106">Users can access the help by calling the **Configuration** with `-?`, or by using the [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet.</span></span> <span data-ttu-id="b5954-107">Posizionare la Guida basata sui commenti direttamente sopra la parola chiave `Configuration`.</span><span class="sxs-lookup"><span data-stu-id="b5954-107">Place your Comment-based help directly above the `Configuration` keyword.</span></span>
<span data-ttu-id="b5954-108">È possibile inserire la Guida per i parametri in linea con il blocco di commento, subito sopra la dichiarazione del parametro o entrambi come nell'esempio seguente.</span><span class="sxs-lookup"><span data-stu-id="b5954-108">You can place parameter help in-line with your comment block, directly above the parameter declaration, or both as in the example below.</span></span>

<span data-ttu-id="b5954-109">Per altre informazioni sulla Guida basata sui commenti di PowerShell, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span><span class="sxs-lookup"><span data-stu-id="b5954-109">For more information about PowerShell comment-based help, see [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).</span></span>

> [!NOTE]
> <span data-ttu-id="b5954-110">Gli ambienti di sviluppo di PowerShell, come VSCode e ISE, includono anche frammenti di codice che consentono di inserire automaticamente modelli di blocchi di commento.</span><span class="sxs-lookup"><span data-stu-id="b5954-110">PowerShell development environments, like VSCode and the ISE, also have snippets to allow you to automatically insert comment block templates.</span></span>

<span data-ttu-id="b5954-111">L'esempio seguente mostra uno script che contiene una configurazione e una Guida basata su commenti per tale configurazione.</span><span class="sxs-lookup"><span data-stu-id="b5954-111">The following example shows a script that contains a configuration and comment-based help for it.</span></span> <span data-ttu-id="b5954-112">Questo esempio mostra una configurazione con parametri.</span><span class="sxs-lookup"><span data-stu-id="b5954-112">This example shows a Configuration with parameters.</span></span> <span data-ttu-id="b5954-113">Per altre informazioni sull'uso dei parametri nelle configurazioni, vedere [Aggiungere parametri a una configurazione](add-parameters-to-a-configuration.md).</span><span class="sxs-lookup"><span data-stu-id="b5954-113">To learn more about using parameters in your Configurations, see [Add Parameters to your Configurations](add-parameters-to-a-configuration.md).</span></span>

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

.EXAMPLE
HelpSample -ComputerName localhost

A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.
.EXAMPLE
HelpSample -FilePath "C:\output.txt"

This example will be labeled "EXAMPLE 2" when help is displayed to the user.
#>
configuration HelpSample1
{
    param
    (
        [string]$ComputerName = 'localhost',
        # Provide a PARAMETER section for each parameter that your script or function accepts.
        [string]$FilePath = 'C:\Destination.txt'
    )

    Node $ComputerName
    {
        File HelloWorld
        {
            Contents="Hello World"
            DestinationPath = $FilePath
        }
    }
}
```

## <a name="viewing-configuration-help"></a><span data-ttu-id="b5954-114">Visualizzazione della Guida di configurazione</span><span class="sxs-lookup"><span data-stu-id="b5954-114">Viewing configuration help</span></span>

<span data-ttu-id="b5954-115">Per visualizzare la Guida per una configurazione, usare il cmdlet `Get-Help` con il nome della funzione oppure digitare il nome della funzione seguito da `-?`.</span><span class="sxs-lookup"><span data-stu-id="b5954-115">To view the help for a configuration, use the `Get-Help` cmdlet with the name of the function, or type the name of the function followed by `-?`.</span></span> <span data-ttu-id="b5954-116">Di seguito viene riportato l'output della configurazione precedente passata a `Get-Help`.</span><span class="sxs-lookup"><span data-stu-id="b5954-116">The following is the output of the previous Configuration passed to `Get-Help`.</span></span>

```powershell
Get-Help HelpSample1 -Detailed
```

```output
NAME
    HelpSample1

SYNOPSIS
    A brief description of the function or script. This keyword can be used only once for each configuration.


SYNTAX
    HelpSample1 [[-InstanceName] <String>] [[-DependsOn] <String[]>] [[-PsDscRunAsCredential] <PSCredential>] [[-OutputPath] <String>] [[-ConfigurationData] <Hashtable>] [[-ComputerName] <String>] [[-FilePath] <String>] [<CommonParameters>]


DESCRIPTION
    A detailed description of the function or script. This keyword can be used only once for each configuration.


PARAMETERS
    -InstanceName <String>

    -DependsOn <String[]>

    -PsDscRunAsCredential <PSCredential>

    -OutputPath <String>

    -ConfigurationData <Hashtable>

    -ComputerName <String>
        The description of a parameter. Add a .PARAMETER keyword for each parameter in the function or script syntax.

        Type the parameter name on the same line as the .PARAMETER keyword. Type the parameter description on the lines following the .PARAMETER keyword.
        Windows PowerShell interprets all text between the .PARAMETER line and the next keyword or the end of the comment block as part of the parameter description.
        The description can include paragraph breaks.

        The Parameter keywords can appear in any order in the comment block, but the function or script syntax determines the order in which the parameters
        (and their descriptions) appear in help topic. To change the order, change the syntax.

    -FilePath <String>
        Provide a PARAMETER section for each parameter that your script or function accepts.

    <CommonParameters>
        This cmdlet supports the common parameters: Verbose, Debug,
        ErrorAction, ErrorVariable, WarningAction, WarningVariable,
        OutBuffer, PipelineVariable, and OutVariable. For more information, see
        about_CommonParameters (https:/go.microsoft.com/fwlink/?LinkID=113216).

    -------------------------- EXAMPLE 1 --------------------------

    PS C:\>HelpSample -ComputerName localhost

    A sample command that uses the function or script, optionally followed by sample output and a description. Repeat this keyword for each example.
    PowerShell automatically prefaces the first line with a PowerShell prompt. Additional lines are treated as output and description. The example can contain spaces, newlines and PowerShell code.

    If you have multiple examples, there is no need to number them. PowerShell will number the examples in help text.




    -------------------------- EXAMPLE 2 --------------------------

    PS C:\>HelpSample -FilePath "C:\output.txt"

    This example will be labeled "EXAMPLE 2" when help is displayed to the user.




REMARKS
    To see the examples, type: "get-help HelpSample1 -examples".
    For more information, type: "get-help HelpSample1 -detailed".
    For technical information, type: "get-help HelpSample1 -full".
```

> [!NOTE]
> <span data-ttu-id="b5954-117">Gli attributi per i campi e i parametri della sintassi vengono generati automaticamente da PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b5954-117">Syntax fields and parameter attributes are automatically generated for you by PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="b5954-118">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b5954-118">See Also</span></span>

- [<span data-ttu-id="b5954-119">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="b5954-119">DSC Configurations</span></span>](configurations.md)
- [<span data-ttu-id="b5954-120">Scrivere, compilare e applicare una configurazione</span><span class="sxs-lookup"><span data-stu-id="b5954-120">Write, Compile, and Apply a Configuration</span></span>](write-compile-apply-configuration.md)
- [<span data-ttu-id="b5954-121">Aggiungere parametri a una configurazione</span><span class="sxs-lookup"><span data-stu-id="b5954-121">Add Parameters to a Configuration</span></span>](add-parameters-to-a-configuration.md)
