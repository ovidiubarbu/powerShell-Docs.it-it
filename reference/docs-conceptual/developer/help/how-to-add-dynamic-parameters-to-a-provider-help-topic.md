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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361260"
---
# <a name="how-to-add-dynamic-parameters-to-a-provider-help-topic"></a><span data-ttu-id="3cdac-102">Come aggiungere parametri dinamici a un argomento della Guida dei provider</span><span class="sxs-lookup"><span data-stu-id="3cdac-102">How to Add Dynamic Parameters to a Provider Help Topic</span></span>

<span data-ttu-id="3cdac-103">In questa sezione viene illustrato come popolare la sezione **parametri dinamici** di un argomento della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="3cdac-103">This section explains how to populate the **DYNAMIC PARAMETERS** section of a provider help topic.</span></span>

<span data-ttu-id="3cdac-104">I *parametri dinamici* sono parametri di un cmdlet o di una funzione disponibili solo in condizioni specificate.</span><span class="sxs-lookup"><span data-stu-id="3cdac-104">*Dynamic parameters* are parameters of a cmdlet or function that are available only under specified conditions.</span></span>

<span data-ttu-id="3cdac-105">I parametri dinamici documentati in un argomento della guida del provider sono i parametri dinamici aggiunti dal provider al cmdlet o alla funzione quando si utilizza il cmdlet o la funzione nell'unità del provider.</span><span class="sxs-lookup"><span data-stu-id="3cdac-105">The dynamic parameters that are documented in a provider help topic are the dynamic parameters that the provider adds to the cmdlet or function when the cmdlet or function is used in the provider drive.</span></span>

<span data-ttu-id="3cdac-106">I parametri dinamici possono anche essere documentati nella Guida personalizzata dei cmdlet per un provider.</span><span class="sxs-lookup"><span data-stu-id="3cdac-106">Dynamic parameters can also be documented in custom cmdlet help for a provider.</span></span> <span data-ttu-id="3cdac-107">Quando si scrivono sia la guida del provider che la guida personalizzata sui cmdlet per un provider, includere la documentazione relativa ai parametri dinamici in entrambi i documenti.</span><span class="sxs-lookup"><span data-stu-id="3cdac-107">When writing both provider help and custom cmdlet help for a provider, include the dynamic parameter documentation in both documents.</span></span>

<span data-ttu-id="3cdac-108">Se un provider non implementa parametri dinamici, l'argomento della guida del provider contiene un elemento `DynamicParameters` vuoto.</span><span class="sxs-lookup"><span data-stu-id="3cdac-108">If a provider does not implement any dynamic parameters, the provider help topic contains an empty `DynamicParameters` element.</span></span>

### <a name="to-add-dynamic-parameters"></a><span data-ttu-id="3cdac-109">Per aggiungere parametri dinamici</span><span class="sxs-lookup"><span data-stu-id="3cdac-109">To Add Dynamic Parameters</span></span>

1. <span data-ttu-id="3cdac-110">Nel file *AssemblyName*. dll-help. XML, all'interno dell'elemento `providerHelp`, aggiungere un elemento `DynamicParameters`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-110">In the *AssemblyName*.dll-help.xml file, within the `providerHelp` element, add a `DynamicParameters` element.</span></span> <span data-ttu-id="3cdac-111">L'elemento `DynamicParameters` dovrebbe comparire dopo l'elemento `Tasks` e prima dell'elemento `RelatedLinks`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-111">The `DynamicParameters` element should appear after the `Tasks` element and before the `RelatedLinks` element.</span></span>

   <span data-ttu-id="3cdac-112">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3cdac-112">For example:</span></span>

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

   <span data-ttu-id="3cdac-113">Se il provider non implementa parametri dinamici, l'elemento `DynamicParameters` può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="3cdac-113">If the provider does not implement any dynamic parameters, the `DynamicParameters` element can be empty.</span></span>

2. <span data-ttu-id="3cdac-114">All'interno dell'elemento `DynamicParameters`, per ogni parametro dinamico aggiungere un elemento `DynamicParameter`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-114">Within the `DynamicParameters` element, for each dynamic parameter, add a `DynamicParameter` element.</span></span>

   <span data-ttu-id="3cdac-115">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="3cdac-115">For example:</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
        </DynamicParameter>
    </DynamicParameters>
    ```

3. <span data-ttu-id="3cdac-116">In ogni elemento `DynamicParameter` aggiungere un `Name` e `CmdletSupported` elemento.</span><span class="sxs-lookup"><span data-stu-id="3cdac-116">In each `DynamicParameter` element, add a `Name` and `CmdletSupported` element.</span></span>

   |<span data-ttu-id="3cdac-117">Nome elemento</span><span class="sxs-lookup"><span data-stu-id="3cdac-117">Element Name</span></span>|<span data-ttu-id="3cdac-118">Description</span><span class="sxs-lookup"><span data-stu-id="3cdac-118">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3cdac-119">Name</span><span class="sxs-lookup"><span data-stu-id="3cdac-119">Name</span></span>|<span data-ttu-id="3cdac-120">Specifica il nome del parametro.</span><span class="sxs-lookup"><span data-stu-id="3cdac-120">Specifies the parameter name.</span></span>|
   |<span data-ttu-id="3cdac-121">CmdletSupported</span><span class="sxs-lookup"><span data-stu-id="3cdac-121">CmdletSupported</span></span>|<span data-ttu-id="3cdac-122">Specifica i cmdlet in cui il parametro è valido.</span><span class="sxs-lookup"><span data-stu-id="3cdac-122">Specifies the cmdlets in which the parameter is valid.</span></span> <span data-ttu-id="3cdac-123">Digitare un elenco delimitato da virgole di nomi di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3cdac-123">Type a comma-separated list of cmdlet names.</span></span>|

   <span data-ttu-id="3cdac-124">Il codice XML seguente, ad esempio, documenta il `Encoding` parametro dinamico aggiunto dal provider FileSystem di Windows PowerShell ai cmdlet `Add-Content`, `Get-Content``Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-124">For example, the following XML documents the `Encoding` dynamic parameter that the Windows PowerShell FileSystem provider adds to the `Add-Content`, `Get-Content`, `Set-Content` cmdlets.</span></span>

    ```xml
    <DynamicParameters/>
        <DynamicParameter>
            <Name> Encoding </Name>
            <CmdletSupported> Add-Content, Get-Content, Set-Content </CmdletSupported>
    </DynamicParameters>

    ```

4. <span data-ttu-id="3cdac-125">Aggiungere un elemento `Type` in ogni elemento `DynamicParameter`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-125">In each `DynamicParameter` element, add a `Type` element.</span></span> <span data-ttu-id="3cdac-126">L'elemento `Type` è un contenitore per l'elemento `Name` che contiene il tipo .NET del valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="3cdac-126">The `Type` element is a container for the `Name` element which contains the .NET type of the value of the dynamic parameter.</span></span>

   <span data-ttu-id="3cdac-127">Il codice XML seguente, ad esempio, indica che il tipo .NET del `Encoding` parametro dinamico è l'enumerazione [Microsoft. PowerShell. Commands. FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) .</span><span class="sxs-lookup"><span data-stu-id="3cdac-127">For example, the following XML shows that the .NET type of the `Encoding` dynamic parameter is the [Microsoft.PowerShell.Commands.FileSystemCmdletProviderEncoding](/dotnet/api/microsoft.powershell.commands.filesystemcmdletproviderencoding) enumeration.</span></span>

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

5. <span data-ttu-id="3cdac-128">Aggiungere l'elemento `Description`, che contiene una breve descrizione del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="3cdac-128">Add the `Description` element, which contains a brief description of the dynamic parameter.</span></span> <span data-ttu-id="3cdac-129">Quando si compone la descrizione, utilizzare le linee guida previste per tutti i parametri del cmdlet in [come aggiungere informazioni sui parametri](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="3cdac-129">When composing the description, use the guidelines prescribed for all cmdlet parameters in [How to Add Parameter Information](./how-to-add-parameter-information.md).</span></span>

   <span data-ttu-id="3cdac-130">Il codice XML seguente, ad esempio, include la descrizione del `Encoding` parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="3cdac-130">For example, the following XML includes the description of the `Encoding` dynamic parameter.</span></span>

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

6. <span data-ttu-id="3cdac-131">Aggiungere l'elemento `PossibleValues` e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="3cdac-131">Add the `PossibleValues` element and its child elements.</span></span> <span data-ttu-id="3cdac-132">Insieme, questi elementi descrivono i valori del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="3cdac-132">Together, these elements describe the values of the dynamic parameter.</span></span> <span data-ttu-id="3cdac-133">Questo elemento è progettato per i valori enumerati.</span><span class="sxs-lookup"><span data-stu-id="3cdac-133">This element is designed for enumerated values.</span></span> <span data-ttu-id="3cdac-134">Se il parametro dinamico non accetta un valore, come nel caso di un parametro switch, oppure non è possibile enumerare i valori, aggiungere un elemento `PossibleValues` vuoto.</span><span class="sxs-lookup"><span data-stu-id="3cdac-134">If the dynamic parameter does not take a value, such as is the case with a switch parameter, or the values cannot be enumerated, add an empty `PossibleValues` element.</span></span>

   <span data-ttu-id="3cdac-135">La tabella seguente elenca e descrive l'elemento `PossibleValues` e i relativi elementi figlio.</span><span class="sxs-lookup"><span data-stu-id="3cdac-135">The following table lists and describes the `PossibleValues` element and its child elements.</span></span>

   |<span data-ttu-id="3cdac-136">Nome elemento</span><span class="sxs-lookup"><span data-stu-id="3cdac-136">Element Name</span></span>|<span data-ttu-id="3cdac-137">Description</span><span class="sxs-lookup"><span data-stu-id="3cdac-137">Description</span></span>|
   |------------------|-----------------|
   |<span data-ttu-id="3cdac-138">PossibleValues</span><span class="sxs-lookup"><span data-stu-id="3cdac-138">PossibleValues</span></span>|<span data-ttu-id="3cdac-139">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="3cdac-139">This element is a container.</span></span> <span data-ttu-id="3cdac-140">I relativi elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="3cdac-140">Its child elements are described below.</span></span> <span data-ttu-id="3cdac-141">Aggiungere un elemento `PossibleValues` a ogni argomento della guida del provider.</span><span class="sxs-lookup"><span data-stu-id="3cdac-141">Add one `PossibleValues` element to each provider help topic.</span></span> <span data-ttu-id="3cdac-142">L'elemento può essere vuoto.</span><span class="sxs-lookup"><span data-stu-id="3cdac-142">The element can be empty.</span></span>|
   |<span data-ttu-id="3cdac-143">PossibleValue</span><span class="sxs-lookup"><span data-stu-id="3cdac-143">PossibleValue</span></span>|<span data-ttu-id="3cdac-144">Questo elemento è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="3cdac-144">This element is a container.</span></span> <span data-ttu-id="3cdac-145">I relativi elementi figlio sono descritti di seguito.</span><span class="sxs-lookup"><span data-stu-id="3cdac-145">Its child elements are described below.</span></span> <span data-ttu-id="3cdac-146">Aggiungere un elemento `PossibleValue` per ogni valore del parametro dinamico.</span><span class="sxs-lookup"><span data-stu-id="3cdac-146">Add one `PossibleValue` element for each value of the dynamic parameter.</span></span>|
   |<span data-ttu-id="3cdac-147">Value</span><span class="sxs-lookup"><span data-stu-id="3cdac-147">Value</span></span>|<span data-ttu-id="3cdac-148">Specifica il nome del valore.</span><span class="sxs-lookup"><span data-stu-id="3cdac-148">Specifies the value name.</span></span>|
   |<span data-ttu-id="3cdac-149">Description</span><span class="sxs-lookup"><span data-stu-id="3cdac-149">Description</span></span>|<span data-ttu-id="3cdac-150">Questo elemento contiene un elemento `Para`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-150">This element contains a `Para` element.</span></span> <span data-ttu-id="3cdac-151">Il testo nell'elemento `Para` descrive il valore denominato nell'elemento `Value`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-151">The text in the `Para` element describes the value that is named in the `Value` element.</span></span>|

   <span data-ttu-id="3cdac-152">Il codice XML seguente, ad esempio, Mostra un elemento `PossibleValue` del parametro dinamico `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-152">For example, the following XML shows one `PossibleValue` element of the `Encoding` dynamic parameter.</span></span>

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

## <a name="example"></a><span data-ttu-id="3cdac-153">Esempio</span><span class="sxs-lookup"><span data-stu-id="3cdac-153">Example</span></span>

<span data-ttu-id="3cdac-154">Nell'esempio seguente viene illustrato l'elemento `DynamicParameters` del parametro dinamico `Encoding`.</span><span class="sxs-lookup"><span data-stu-id="3cdac-154">The following example shows the `DynamicParameters` element of the `Encoding` dynamic parameter.</span></span>

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