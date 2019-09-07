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
ms.openlocfilehash: cc4877242a16a9caa99564aeaae985f85e38791e
ms.sourcegitcommit: ffcc1c55f5b3adc063353cb75f2a2183acc2234a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 09/06/2019
ms.locfileid: "70737592"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="98911-102">Come aggiungere parametri dinamici a un argomento della Guida dei provider</span><span class="sxs-lookup"><span data-stu-id="98911-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="98911-103">In questa sezione viene illustrato come popolare la sezione **parametri dinamici** di un argomento della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="98911-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="98911-104">I *parametri dinamici* sono parametri di un cmdlet o di una funzione disponibili solo in condizioni specificate.</span><span class="sxs-lookup"><span data-stu-id="98911-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="98911-105">I parametri dinamici documentati in un argomento della guida del provider sono i parametri dinamici aggiunti dal provider al cmdlet o alla funzione quando si utilizza il cmdlet o la funzione nell'unità del provider.</span><span class="sxs-lookup"><span data-stu-id="98911-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="98911-106">I parametri dinamici possono anche essere documentati nella Guida personalizzata dei cmdlet per un provider.</span><span class="sxs-lookup"><span data-stu-id="98911-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="98911-107">Quando si scrivono sia la guida del provider che la guida personalizzata sui cmdlet per un provider, includere la documentazione relativa ai parametri dinamici in entrambi i documenti.</span><span class="sxs-lookup"><span data-stu-id="98911-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span> <span data-ttu-id="98911-108">Per ulteriori informazioni sulla guida personalizzata dei cmdlet, vedere la pagina relativa alla [scrittura della Guida dei cmdlet personalizzati di Windows PowerShell per i provider](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span><span class="sxs-lookup"><span data-stu-id="98911-108">For more information about custom cmdlet help, see [Writing Windows PowerShell Custom Cmdlet Help for Providers](./writing-custom-cmdlet-help-for-windows-powershell-providers.md).</span></span>

<span data-ttu-id="98911-109">Se un provider non implementa parametri dinamici, l'argomento della guida del provider contiene un elemento `DynamicParameters` vuoto.</span><span class="sxs-lookup"><span data-stu-id="98911-109">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="98911-110">Per aggiungere parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="98911-110">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="98911-111">Nel file *AssemblyName*. dll-help. XML all'interno dell' `providerHelp` elemento aggiungere un `DynamicParameters` elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-111">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="98911-112">L' `DynamicParameters` elemento deve essere visualizzato dopo `Tasks` l'elemento e prima `RelatedLinks` dell'elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-112">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="98911-113">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="98911-113">For example:</span></span>

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

   <span data-ttu-id="98911-114">Se il provider non implementa parametri dinamici, l' `DynamicParameters` elemento può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="98911-114">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="98911-115">All'interno `DynamicParameters` dell'elemento, per ogni parametro dinamico, aggiungere `DynamicParameter` un elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-115">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="98911-116">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="98911-116">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="98911-117">In ogni `DynamicParameter` elemento aggiungere un `Name` elemento e `CmdletSupported` .</span><span class="sxs-lookup"><span data-stu-id="98911-117">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="98911-118">Nome dell'elemento</span><span class="sxs-lookup"><span data-stu-id="98911-118">Element Name</span></span>|<span data-ttu-id="98911-119">Description</span><span class="sxs-lookup"><span data-stu-id="98911-119">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="98911-120">Name</span><span class="sxs-lookup"><span data-stu-id="98911-120">Name</span></span>|<span data-ttu-id="98911-121">Specifica il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="98911-121">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="98911-122">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="98911-122">CmdletSupported</span></span>|<span data-ttu-id="98911-123">Specifica i cmdlet in cui il parametro è valido.</span><span class="sxs-lookup"><span data-stu-id="98911-123">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="98911-124">Digitare un elenco delimitato da virgole di nomi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98911-124">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="98911-125">Il codice XML seguente, ad esempio, `Encoding` documenta il parametro dinamico aggiunto dal provider FileSystem `Add-Content`di Windows PowerShell ai `Get-Content`cmdlet `Set-Content` ,,.</span><span class="sxs-lookup"><span data-stu-id="98911-125">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="98911-126">In ogni `DynamicParameter` elemento aggiungere un `Type` elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-126">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="98911-127">L' `Type` elemento è un contenitore per l' `Name` elemento che contiene il tipo .NET del valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-127">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="98911-128">Il codice XML seguente, ad esempio, indica che il tipo .NET `Encoding` del parametro dinamico è l'enumerazione [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="98911-128">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="98911-129">Aggiungere l' `Description` elemento, che contiene una breve descrizione del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-129">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="98911-130">Quando si compone la descrizione, utilizzare le linee guida previste per tutti i parametri del cmdlet in [come aggiungere informazioni sui parametri](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="98911-130">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="98911-131">Il codice XML seguente, ad esempio, include la descrizione `Encoding` del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-131">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="98911-132">Aggiungere l' `PossibleValues` elemento e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="98911-132">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="98911-133">Insieme, questi elementi descrivono i valori del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-133">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="98911-134">Questo elemento è progettato per i valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="98911-134">This element is designed for enumerated values.</span></span> <span data-ttu-id="98911-135">Se il parametro dinamico non accetta un valore, come nel caso di un parametro switch, oppure non è possibile enumerare i valori, aggiungere un elemento vuoto `PossibleValues` .</span><span class="sxs-lookup"><span data-stu-id="98911-135">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="98911-136">La tabella seguente elenca e descrive l' `PossibleValues` elemento e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="98911-136">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="98911-137">Nome dell'elemento</span><span class="sxs-lookup"><span data-stu-id="98911-137">Element Name</span></span>|<span data-ttu-id="98911-138">Descrizione</span><span class="sxs-lookup"><span data-stu-id="98911-138">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="98911-139">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="98911-139">PossibleValues</span></span>|<span data-ttu-id="98911-140">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="98911-140">This element is a container.</span></span> <span data-ttu-id="98911-141">I relativi elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="98911-141">Its child elements are described below.</span></span> <span data-ttu-id="98911-142">Aggiungere un `PossibleValues` elemento a ogni argomento della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="98911-142">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="98911-143">L'elemento può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="98911-143">The element can be empty.</span></span>|
   |<span data-ttu-id="98911-144">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="98911-144">PossibleValue</span></span>|<span data-ttu-id="98911-145">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="98911-145">This element is a container.</span></span> <span data-ttu-id="98911-146">I relativi elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="98911-146">Its child elements are described below.</span></span> <span data-ttu-id="98911-147">Aggiungere un `PossibleValue` elemento per ogni valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-147">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="98911-148">Valore</span><span class="sxs-lookup"><span data-stu-id="98911-148">Value</span></span>|<span data-ttu-id="98911-149">Specifica il nome del valore.</span><span class="sxs-lookup"><span data-stu-id="98911-149">Specifies the value name.</span></span>|
   |<span data-ttu-id="98911-150">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="98911-150">Description</span></span>|<span data-ttu-id="98911-151">Questo elemento contiene un `Para` elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-151">This element contains a `Para` element.</span></span> <span data-ttu-id="98911-152">Il testo nell' `Para` elemento descrive il valore denominato `Value` nell'elemento.</span><span class="sxs-lookup"><span data-stu-id="98911-152">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="98911-153">Il codice XML seguente, ad esempio, `PossibleValue` Mostra un elemento `Encoding` del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-153">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="98911-154">Esempio</span><span class="sxs-lookup"><span data-stu-id="98911-154">Example</span></span>

<span data-ttu-id="98911-155">Nell'esempio seguente viene illustrato `DynamicParameters` l'elemento `Encoding` del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="98911-155">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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