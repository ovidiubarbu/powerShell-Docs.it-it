---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Guida alla scrittura per le configurazioni DSC
ms.openlocfilehash: 498ec0f594ed3229e097903c4ea2ae34d3da03a2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401681"
---
# <a name="writing-help-for-dsc-configurations"></a>Guida alla scrittura per le configurazioni DSC

>Si applica a: Windows PowerShell 5.0

È possibile usare la Guida basata sui commenti nelle configurazioni DSC. Gli utenti possono accedere alla Guida chiamando la **Configuration** con `-?`, oppure utilizzando la [Get-Help](/powershell/module/Microsoft.PowerShell.Core/Get-Help) cmdlet. Posizionare la Guida basata sui commenti direttamente sopra il `Configuration` (parola chiave).
È possibile inserire in linea guida parametro con il blocco di commento, immediatamente sopra la dichiarazione di parametro o entrambi come nell'esempio seguente.

Per altre informazioni sulla Guida basata sui commenti di PowerShell, vedere [about_Comment_Based_Help](/powershell/module/microsoft.powershell.core/about/about_comment_based_help).

> [!NOTE]
> Gli ambienti di sviluppo di PowerShell, come VSCode e ISE, hanno anche frammenti di codice per consentire all'utente di inserire automaticamente i modelli di blocchi di commento.

L'esempio seguente mostra uno script che contiene una configurazione e una Guida basata su commenti per tale configurazione. In questo esempio mostra una configurazione con parametri. Per altre informazioni sull'utilizzo dei parametri nelle configurazioni, vedere [Aggiungi parametri alle configurazioni](add-parameters-to-a-configuration.md).

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

## <a name="viewing-configuration-help"></a>Visualizzazione della Guida di configurazione

Per visualizzare la Guida per una configurazione, usare il `Get-Help` cmdlet con il nome della funzione oppure digitare il nome della funzione seguito da `-?`. Ecco l'output della configurazione precedente passata a `Get-Help`.

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
> Campi di sintassi e gli attributi di parametro vengono generati automaticamente per l'utente mediante PowerShell.

## <a name="see-also"></a>Vedere anche

- [Configurazioni DSC](configurations.md)
- [Scrivere, compilare e applicare una configurazione](write-compile-apply-configuration.md)
- [Aggiungere parametri a una configurazione](add-parameters-to-a-configuration.md)
