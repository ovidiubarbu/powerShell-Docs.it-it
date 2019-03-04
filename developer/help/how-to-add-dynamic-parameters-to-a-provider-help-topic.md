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
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="eab41-102">Come aggiungere parametri dinamici a un argomento della Guida dei provider</span><span class="sxs-lookup"><span data-stu-id="eab41-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="eab41-103">In questa sezione illustra come popolare la **parametri dinamici** sezione di un argomento della Guida di provider.</span><span class="sxs-lookup"><span data-stu-id="eab41-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="eab41-104">*I parametri dinamici* sono parametri di un cmdlet o funzione che sono disponibili solo in condizioni specificate.</span><span class="sxs-lookup"><span data-stu-id="eab41-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="eab41-105">I parametri dinamici che sono documentati in un argomento della Guida di provider sono i parametri dinamici che aggiunge il provider per il cmdlet o una funzione quando l'unità del provider viene usata il cmdlet o funzione.</span><span class="sxs-lookup"><span data-stu-id="eab41-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="eab41-106">I parametri dinamici possono anche essere documentati nella Guida dei cmdlet personalizzati per un provider.</span><span class="sxs-lookup"><span data-stu-id="eab41-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="eab41-107">Durante la scrittura della Guida di provider sia Guida personalizzata sui cmdlet per un provider, includere la documentazione del parametro dinamico in entrambi i documenti.</span><span class="sxs-lookup"><span data-stu-id="eab41-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="eab41-108">Per altre informazioni sulla Guida personalizzata sui cmdlet, vedere [iscritto Windows PowerShell personalizzate la Guida dei Cmdlet per i provider](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="eab41-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="eab41-109">Se un provider può neimplementuje metodu parametri dinamici, l'argomento della Guida del provider contiene un oggetto vuoto `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="eab41-110">Per aggiungere i parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="eab41-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="eab41-111">Nel *AssemblyName*nel file con estensione dll help.xml, all'interno di `providerHelp` elemento, aggiungere un `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="eab41-112">Il `DynamicParameters` elemento dovrebbe essere visualizzati dopo il `Tasks` elemento e prima di `RelatedLinks` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="eab41-113">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="eab41-113">For example:</span></span>

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

   <span data-ttu-id="eab41-114">Se il provider può neimplementuje metodu parametri dinamici, il `DynamicParameters` elemento può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="eab41-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="eab41-115">All'interno di `DynamicParameters` elemento per ogni parametro dinamico, aggiungere un `DynamicParameter` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="eab41-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="eab41-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="eab41-117">In ognuno `DynamicParameter` elemento, aggiungere un' `Name` e `CmdletSupported` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="eab41-118">Nome dell'elemento</span><span class="sxs-lookup"><span data-stu-id="eab41-118">Element Name</span></span>|<span data-ttu-id="eab41-119">Description</span><span class="sxs-lookup"><span data-stu-id="eab41-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="eab41-120">Nome</span><span class="sxs-lookup"><span data-stu-id="eab41-120">Name</span></span>|<span data-ttu-id="eab41-121">Specifica il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="eab41-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="eab41-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="eab41-122">CmdletSupported</span></span>|<span data-ttu-id="eab41-123">Specifica i cmdlet in cui il parametro è valido.</span><span class="sxs-lookup"><span data-stu-id="eab41-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="eab41-124">Digitare un elenco delimitato da virgole di nomi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eab41-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="eab41-125">Ad esempio, i seguenti documenti XML la `Encoding` parametri dinamici che consente di aggiungere il provider FileSystem di Windows PowerShell per il `Add-Content`, `Get-Content`, `Set-Content` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="eab41-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="eab41-126">In ognuno `DynamicParameter` elemento, aggiungere un `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="eab41-127">Il `Type` elemento è un contenitore per il `Name` elemento che contiene il tipo .NET del valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="eab41-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="eab41-128">Ad esempio, il codice XML seguente mostra che il tipo .NET del `Encoding` parametri dinamici sono il [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumerazione.</span><span class="sxs-lookup"><span data-stu-id="eab41-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="eab41-129">Aggiungere il `Description` elemento che contiene una breve descrizione del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="eab41-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="eab41-130">Quando si crea la descrizione, usare le linee guida prescritte per tutti i parametri del cmdlet in [come aggiungere le informazioni sui parametri](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="eab41-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="eab41-131">Ad esempio, il codice XML seguente include la descrizione del `Encoding` parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="eab41-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="eab41-132">Aggiungere il `PossibleValues` elemento e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="eab41-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="eab41-133">Insieme, questi elementi vengono descritti i valori del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="eab41-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="eab41-134">Questo elemento è progettato per i valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="eab41-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="eab41-135">Se il parametro dinamico non accetta un valore, come avviene con un parametro opzionale, o i valori non possono essere enumerati, aggiungere un oggetto vuoto `PossibleValues` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="eab41-136">Nella tabella seguente elenca e descrive il `PossibleValues` elemento e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="eab41-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="eab41-137">Nome dell'elemento</span><span class="sxs-lookup"><span data-stu-id="eab41-137">Element Name</span></span>|<span data-ttu-id="eab41-138">Description</span><span class="sxs-lookup"><span data-stu-id="eab41-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="eab41-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="eab41-139">PossibleValues</span></span>|<span data-ttu-id="eab41-140">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="eab41-140">This element is a container.</span></span> <span data-ttu-id="eab41-141">Gli elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="eab41-141">Its child elements are described below.</span></span> <span data-ttu-id="eab41-142">Aggiungere uno `PossibleValues` elemento per ogni argomento della Guida di provider.</span><span class="sxs-lookup"><span data-stu-id="eab41-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="eab41-143">L'elemento può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="eab41-143">The element can be empty.</span></span>|
   |<span data-ttu-id="eab41-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="eab41-144">PossibleValue</span></span>|<span data-ttu-id="eab41-145">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="eab41-145">This element is a container.</span></span> <span data-ttu-id="eab41-146">Gli elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="eab41-146">Its child elements are described below.</span></span> <span data-ttu-id="eab41-147">Aggiungere uno `PossibleValue` (elemento) per ogni valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="eab41-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="eab41-148">Value</span><span class="sxs-lookup"><span data-stu-id="eab41-148">Value</span></span>|<span data-ttu-id="eab41-149">Specifica il nome del valore.</span><span class="sxs-lookup"><span data-stu-id="eab41-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="eab41-150">Description</span><span class="sxs-lookup"><span data-stu-id="eab41-150">Description</span></span>|<span data-ttu-id="eab41-151">Questo elemento contiene un `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-151">This element contains a `Para` element.</span></span> <span data-ttu-id="eab41-152">Il testo nel `Para` elemento descrive il valore denominato nel `Value` elemento.</span><span class="sxs-lookup"><span data-stu-id="eab41-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="eab41-153">Ad esempio, il codice XML seguente mostra uno `PossibleValue` elemento di `Encoding` parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="eab41-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="eab41-154">Esempio</span><span class="sxs-lookup"><span data-stu-id="eab41-154">Example</span></span>

<span data-ttu-id="eab41-155">L'esempio seguente mostra le `DynamicParameters` elemento del `Encoding` parametri dinamici.</span><span class="sxs-lookup"><span data-stu-id="eab41-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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