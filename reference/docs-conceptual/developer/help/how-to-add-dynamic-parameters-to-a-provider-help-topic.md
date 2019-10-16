---
title: Come aggiungere parametri dinamici a un argomento della guida del provider | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e20e5ad6-a6e6-4a63-9d42-1ac54214f748
caps.latest.revision: 5
ms.openlocfilehash: 59839e9b8b6f2a56f2f1a9c755f2f1a85deb34aa
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72361260"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a>Come aggiungere parametri dinamici a un argomento della Guida dei provider

In questa sezione viene illustrato come popolare la sezione **parametri dinamici** di un argomento della guida del provider.

I *parametri dinamici* sono parametri di un cmdlet o di una funzione disponibili solo in condizioni specificate.

I parametri dinamici documentati in un argomento della guida del provider sono i parametri dinamici aggiunti dal provider al cmdlet o alla funzione quando si utilizza il cmdlet o la funzione nell'unità del provider.

I parametri dinamici possono anche essere documentati nella Guida personalizzata dei cmdlet per un provider. Quando si scrivono sia la guida del provider che la guida personalizzata sui cmdlet per un provider, includere la documentazione relativa ai parametri dinamici in entrambi i documenti.

Se un provider non implementa parametri dinamici, l'argomento della guida del provider contiene un elemento `DynamicParameters` vuoto.

### <a name="to-add-dynamic-parameters"></a>Per aggiungere parametri dinamici

1. Nel file *AssemblyName*. dll-help. XML, all'interno dell'elemento `providerHelp`, aggiungere un elemento `DynamicParameters`. L'elemento `DynamicParameters` deve essere visualizzato dopo l'elemento `Tasks` e prima dell'elemento `RelatedLinks`.

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

   Se il provider non implementa parametri dinamici, l'elemento `DynamicParameters` può essere vuoto.

2. All'interno dell'elemento `DynamicParameters`, per ogni parametro dinamico, aggiungere un elemento `DynamicParameter`.

   Ad esempio:

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. In ogni elemento `DynamicParameter` aggiungere un elemento `Name` e `CmdletSupported`.

   |Nome elemento|Description|
   |------------------|-----------------|
   |Name|Specifica il nome del parametro.|
   |CmdletSupported|Specifica i cmdlet in cui il parametro è valido. Digitare un elenco delimitato da virgole di nomi di cmdlet.|

   Il codice XML seguente, ad esempio, illustra il parametro dinamico `Encoding` aggiunto dal provider FileSystem di Windows PowerShell ai cmdlet `Add-Content`, `Get-Content`, `Set-Content`.

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. In ogni elemento `DynamicParameter` aggiungere un elemento `Type`. L'elemento `Type` è un contenitore per l'elemento `Name` che contiene il tipo .NET del valore del parametro dinamico.

   Il codice XML seguente, ad esempio, indica che il tipo .NET del parametro dinamico `Encoding` è l'enumerazione [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .

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

5. Aggiungere l'elemento `Description`, che contiene una breve descrizione del parametro dinamico. Quando si compone la descrizione, utilizzare le linee guida previste per tutti i parametri del cmdlet in [come aggiungere informazioni sui parametri](./how-to-add-parameter-information.md).

   Il codice XML seguente, ad esempio, include la descrizione del parametro dinamico `Encoding`.

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

6. Aggiungere l'elemento `PossibleValues` e i relativi elementi figlio. Insieme, questi elementi descrivono i valori del parametro dinamico. Questo elemento è progettato per i valori enumerati. Se il parametro dinamico non accetta un valore, come nel caso di un parametro switch, oppure non è possibile enumerare i valori, aggiungere un elemento `PossibleValues` vuoto.

   La tabella seguente elenca e descrive l'elemento `PossibleValues` e i relativi elementi figlio.

   |Nome elemento|Description|
   |------------------|-----------------|
   |PossibleValues|Questo elemento è un contenitore. I relativi elementi figlio sono descritti di seguito. Aggiungere un elemento `PossibleValues` a ogni argomento della guida del provider. L'elemento può essere vuoto.|
   |PossibleValue|Questo elemento è un contenitore. I relativi elementi figlio sono descritti di seguito. Aggiungere un elemento `PossibleValue` per ogni valore del parametro dinamico.|
   |Value|Specifica il nome del valore.|
   |Description|Questo elemento contiene un elemento `Para`. Il testo nell'elemento `Para` descrive il valore denominato nell'elemento `Value`.|

   Il codice XML seguente, ad esempio, Mostra un elemento `PossibleValue` del parametro dinamico `Encoding`.

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

Nell'esempio seguente viene illustrato l'elemento `DynamicParameters` del parametro dinamico `Encoding`.

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