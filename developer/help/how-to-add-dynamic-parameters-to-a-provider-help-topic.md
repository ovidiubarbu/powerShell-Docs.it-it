---
title: Come aggiungere parametri dinamici a un argomento della Guida di Provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56859877"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Come aggiungere parametri dinamici a un argomento della Guida dei provider

In questa sezione illustra come popolare la **parametri dinamici** sezione di un argomento della Guida di provider.

*I parametri dinamici* sono parametri di un cmdlet o funzione che sono disponibili solo in condizioni specificate.

I parametri dinamici che sono documentati in un argomento della Guida di provider sono i parametri dinamici che aggiunge il provider per il cmdlet o una funzione quando l'unità del provider viene usata il cmdlet o funzione.

I parametri dinamici possono anche essere documentati nella Guida dei cmdlet personalizzati per un provider. Durante la scrittura della Guida di provider sia Guida personalizzata sui cmdlet per un provider, includere la documentazione del parametro dinamico in entrambi i documenti. Per altre informazioni sulla Guida personalizzata sui cmdlet, vedere [iscritto Windows PowerShell personalizzate la Guida dei Cmdlet per i provider](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).

Se un provider può neimplementuje metodu parametri dinamici, l'argomento della Guida del provider contiene un oggetto vuoto `DynamicParameters` elemento.

### <a name="to-add-dynamic-parameters"></a>Per aggiungere i parametri dinamici

1. Nel *AssemblyName*nel file con estensione dll help.xml, all'interno di `providerHelp` elemento, aggiungere un `DynamicParameters` elemento. Il `DynamicParameters` elemento dovrebbe essere visualizzati dopo il `Tasks` elemento e prima di `RelatedLinks` elemento.

   Ad esempio:

    ```xml
    <providerHelp>
        <Tasks>
        </Tasks>
        <DynamicParameters>
        </DynamicParameters>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

   Se il provider può neimplementuje metodu parametri dinamici, il `DynamicParameters` elemento può essere vuoto.

2. All'interno di `DynamicParameters` elemento per ogni parametro dinamico, aggiungere un `DynamicParameter` elemento.

   Ad esempio:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. In ognuno `DynamicParameter` elemento, aggiungere un' `Name` e `CmdletSupported` elemento.

   |Nome dell'elemento|Description|
   |------------------|-----------------|
   |Nome|Specifica il nome del parametro.|
   |CmdletSupported|Specifica i cmdlet in cui il parametro è valido. Digitare un elenco delimitato da virgole di nomi di cmdlet.|

   Ad esempio, i seguenti documenti XML la `Encoding` parametri dinamici che consente di aggiungere il provider FileSystem di Windows PowerShell per il `Add-Content`, `Get-Content`, `Set-Content` cmdlet.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. In ognuno `DynamicParameter` elemento, aggiungere un `Type` elemento. Il `Type` elemento è un contenitore per il `Name` elemento che contiene il tipo .NET del valore del parametro dinamico.

   Ad esempio, il codice XML seguente mostra che il tipo .NET del `Encoding` parametri dinamici sono il [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumerazione.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
    ...
    </DynamicParameters>
    ```

5. Aggiungere il `Description` elemento che contiene una breve descrizione del parametro dinamico. Quando si crea la descrizione, usare le linee guida prescritte per tutti i parametri del cmdlet in [come aggiungere le informazioni sui parametri](./how-to-add-parameter-information.md).

   Ad esempio, il codice XML seguente include la descrizione del `Encoding` parametri dinamici.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
            <Type>
                <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
            <Type>
            <Description> Specifies the encoding of the output file that contains the content. </Description>
    ...
    </DynamicParameters>
    ```

6. Aggiungere il `PossibleValues` elemento e i relativi elementi figlio. Insieme, questi elementi vengono descritti i valori del parametro dinamico. Questo elemento è progettato per i valori enumerati. Se il parametro dinamico non accetta un valore, come avviene con un parametro opzionale, o i valori non possono essere enumerati, aggiungere un oggetto vuoto `PossibleValues` elemento.

   Nella tabella seguente elenca e descrive il `PossibleValues` elemento e i relativi elementi figlio.

   |Nome dell'elemento|Description|
   |------------------|-----------------|
   |PossibleValues|Questo elemento è un contenitore. Gli elementi figlio sono descritti di seguito. Aggiungere uno `PossibleValues` elemento per ogni argomento della Guida di provider. L'elemento può essere vuoto.|
   |PossibleValue|Questo elemento è un contenitore. Gli elementi figlio sono descritti di seguito. Aggiungere uno `PossibleValue` (elemento) per ogni valore del parametro dinamico.|
   |Value|Specifica il nome del valore.|
   |Description|Questo elemento contiene un `Para` elemento. Il testo nel `Para` elemento descrive il valore denominato nel `Value` elemento.|

   Ad esempio, il codice XML seguente mostra uno `PossibleValue` elemento di `Encoding` parametri dinamici.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
    ...
            <Description> Specifies the encoding of the output file that contains the content. </Description>
            <PossibleValues>
                <PossibleValue>
                    <Value> ASCII </Value>
                    <Description>
                        <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                    </Description>
                </PossibleValue>
    ...
            </PossibleValues>
    </DynamicParameters>
    ```

## <a name="example"></a>Esempio

L'esempio seguente mostra le `DynamicParameters` elemento del `Encoding` parametri dinamici.

```xml
<DynamicParameters/>
    <DynamicParameter>
        <Name> Encoding </Name>
        <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
        <Type>
            <Name> Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding </Name>
        <Type>
        <Description> Specifies the encoding of the output file that contains the content. </Description>
        <PossibleValues>
            <PossibleValue>
                <Value> ASCII </Value>
                <Description>
                    <para> Uses the encoding for the ASCII (7-bit) character set. </para>
                </Description>
            </PossibleValue>
            <PossibleValue>
                <Value> Unicode </Value>
                <Description>
                    <para> Encodes in UTF-16 format using the little-endian byte order. </para>
                </Description>
            </PossibleValue>
        </PossibleValues>
</DynamicParameters>
```