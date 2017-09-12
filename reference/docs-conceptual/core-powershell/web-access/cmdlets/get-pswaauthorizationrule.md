---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: get pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: eb9f42ab4d9cec111e03a096b2f00740e97ee1b7
ms.sourcegitcommit: d6ab9ab5909ed59cce4ce30e29457e0e75c7ac12
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 09/08/2017
---
# <a name="get-pswaauthorizationrule"></a><span data-ttu-id="821ee-103">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="821ee-103">Get-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="821ee-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="821ee-104">SYNOPSIS</span></span>

<span data-ttu-id="821ee-105">Restituisce un set di regole di autorizzazione di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="821ee-105">Returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>

## <a name="syntax"></a><span data-ttu-id="821ee-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="821ee-106">Syntax</span></span>

### <a name="id"></a><span data-ttu-id="821ee-107">ID</span><span class="sxs-lookup"><span data-stu-id="821ee-107">ID</span></span>
```
Get-PswaAuthorizationRule [[-Id] <Int32[]> ] [ <CommonParameters>]
```

### <a name="name"></a><span data-ttu-id="821ee-108">Nome</span><span class="sxs-lookup"><span data-stu-id="821ee-108">Name</span></span>
```
Get-PswaAuthorizationRule [-RuleName] <String[]> [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="821ee-109">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="821ee-109">DESCRIPTION</span></span>

<span data-ttu-id="821ee-110">Il cmdlet **Get-PswaAuthorizationRule** restituisce un set di regole di autorizzazione di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="821ee-110">The **Get-PswaAuthorizationRule** cmdlet returns a set of the Windows PowerShell® Web Access authorization rules.</span></span>
<span data-ttu-id="821ee-111">Se non si specifica né il parametro **Id** né il parametro **RuleName**, questo cmdlet elenca tutte le regole.</span><span class="sxs-lookup"><span data-stu-id="821ee-111">If neither the **Id** parameter nor the **RuleName** parameter is specified, then this cmdlet lists all rules.</span></span> <span data-ttu-id="821ee-112">Il parametro **Id** può essere usato per filtrare i risultati.</span><span class="sxs-lookup"><span data-stu-id="821ee-112">The **Id** parameter can be used to filter the results.</span></span>

## <a name="parameters"></a><span data-ttu-id="821ee-113">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="821ee-113">PARAMETERS</span></span>

### <a name="-idltint32gt"></a><span data-ttu-id="821ee-114">-Id&lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="821ee-114">-Id&lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="821ee-115">Specifica gli identificatori (ID) delle regole che il cmdlet deve restituire.</span><span class="sxs-lookup"><span data-stu-id="821ee-115">Specifies the identifiers (IDs) of the rules that this cmdlet should get.</span></span> <span data-ttu-id="821ee-116">Se non è stato specificato alcun ID, il cmdlet restituisce tutte le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="821ee-116">If no IDs are specified, then this cmdlet returns all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="821ee-117">Alias</span><span class="sxs-lookup"><span data-stu-id="821ee-117">Aliases</span></span>                              | <span data-ttu-id="821ee-118">Nessuno</span><span class="sxs-lookup"><span data-stu-id="821ee-118">none</span></span>                                 |
| <span data-ttu-id="821ee-119">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="821ee-119">Required?</span></span>                            | <span data-ttu-id="821ee-120">False</span><span class="sxs-lookup"><span data-stu-id="821ee-120">false</span></span>                                |
| <span data-ttu-id="821ee-121">Posizione?</span><span class="sxs-lookup"><span data-stu-id="821ee-121">Position?</span></span>                            | <span data-ttu-id="821ee-122">2</span><span class="sxs-lookup"><span data-stu-id="821ee-122">2</span></span>                                    |
| <span data-ttu-id="821ee-123">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="821ee-123">Default Value</span></span>                        | <span data-ttu-id="821ee-124">Nessuno</span><span class="sxs-lookup"><span data-stu-id="821ee-124">none</span></span>                                 |
| <span data-ttu-id="821ee-125">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="821ee-125">Accept Pipeline Input?</span></span>               | <span data-ttu-id="821ee-126">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="821ee-126">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="821ee-127">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="821ee-127">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="821ee-128">False</span><span class="sxs-lookup"><span data-stu-id="821ee-128">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="821ee-129">-RuleName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="821ee-129">-RuleName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="821ee-130">Specifica i nomi delle regole di autorizzazione da recuperare.</span><span class="sxs-lookup"><span data-stu-id="821ee-130">Specifies the names of authorization rules to retrieve.</span></span> <span data-ttu-id="821ee-131">Questo parametro restituisce tutte le regole che corrispondono esattamente ai nomi delle regole delle stringhe in questa matrice.</span><span class="sxs-lookup"><span data-stu-id="821ee-131">This parameter returns any rules that exactly match the rule names of the strings in this array.</span></span>

|||  
|-|-|
| <span data-ttu-id="821ee-132">Alias</span><span class="sxs-lookup"><span data-stu-id="821ee-132">Aliases</span></span>                              | <span data-ttu-id="821ee-133">Nessuno</span><span class="sxs-lookup"><span data-stu-id="821ee-133">none</span></span>                                 |
| <span data-ttu-id="821ee-134">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="821ee-134">Required?</span></span>                            | <span data-ttu-id="821ee-135">True</span><span class="sxs-lookup"><span data-stu-id="821ee-135">true</span></span>                                 |
| <span data-ttu-id="821ee-136">Posizione?</span><span class="sxs-lookup"><span data-stu-id="821ee-136">Position?</span></span>                            | <span data-ttu-id="821ee-137">2</span><span class="sxs-lookup"><span data-stu-id="821ee-137">2</span></span>                                    |
| <span data-ttu-id="821ee-138">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="821ee-138">Default Value</span></span>                        | <span data-ttu-id="821ee-139">Nessuno</span><span class="sxs-lookup"><span data-stu-id="821ee-139">none</span></span>                                 |
| <span data-ttu-id="821ee-140">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="821ee-140">Accept Pipeline Input?</span></span>               | <span data-ttu-id="821ee-141">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="821ee-141">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="821ee-142">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="821ee-142">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="821ee-143">False</span><span class="sxs-lookup"><span data-stu-id="821ee-143">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="821ee-144">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="821ee-144">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="821ee-145">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="821ee-145">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="821ee-146">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="821ee-146">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="821ee-147">INPUT</span><span class="sxs-lookup"><span data-stu-id="821ee-147">INPUTS</span></span>

### <a name="int"></a><span data-ttu-id="821ee-148">int\[\]</span><span class="sxs-lookup"><span data-stu-id="821ee-148">int\[\]</span></span>

<span data-ttu-id="821ee-149">Questo cmdlet accetta una matrice di numeri interi o una matrice di valori di stringa come input.</span><span class="sxs-lookup"><span data-stu-id="821ee-149">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

### <a name="string"></a><span data-ttu-id="821ee-150">String\[\]</span><span class="sxs-lookup"><span data-stu-id="821ee-150">String\[\]</span></span>

<span data-ttu-id="821ee-151">Questo cmdlet accetta una matrice di numeri interi o una matrice di valori di stringa come input.</span><span class="sxs-lookup"><span data-stu-id="821ee-151">This cmdlet accepts an array of integers or an array of string values as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="821ee-152">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="821ee-152">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="821ee-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="821ee-153">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="821ee-154">Questo cmdlet genera un oggetto PswaAuthorizationRule come output.</span><span class="sxs-lookup"><span data-stu-id="821ee-154">This cmdlet produces a PswaAuthorizationRule object as output.</span></span>


## <a name="examples"></a><span data-ttu-id="821ee-155">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="821ee-155">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="821ee-156">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="821ee-156">EXAMPLE 1</span></span>

<span data-ttu-id="821ee-157">In questo esempio vengono ottenute tutte le regole.</span><span class="sxs-lookup"><span data-stu-id="821ee-157">This example gets all of the rules.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule
```

### <a name="example-2"></a><span data-ttu-id="821ee-158">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="821ee-158">EXAMPLE 2</span></span>

<span data-ttu-id="821ee-159">In questo esempio si ottiene una regola con ID *2*.</span><span class="sxs-lookup"><span data-stu-id="821ee-159">This example gets a rule with an ID of *2*.</span></span>

```PowerShell
    PS C:\> Get-PswaAuthorizationRule –Id 2
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="821ee-160">ESEMPIO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="821ee-160">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="821ee-161">Questo esempio illustra come il cmdlet accetta un valore dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="821ee-161">This example illustrates how the cmdlet accepts a value from pipeline.</span></span>
<span data-ttu-id="821ee-162">In questo cmdlet vengono passati un ID e un nome di regola.</span><span class="sxs-lookup"><span data-stu-id="821ee-162">A rule id and a rule name are passed in this cmdlet.</span></span>

```PowerShell
    PS C:\> "rule1",0 | Get-PswaAuthorizationRule
```

## <a name="related-topics"></a><span data-ttu-id="821ee-163">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="821ee-163">Related topics</span></span>

- [<span data-ttu-id="821ee-164">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="821ee-164">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="821ee-165">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="821ee-165">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="821ee-166">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="821ee-166">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
- [<span data-ttu-id="821ee-167">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="821ee-167">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
