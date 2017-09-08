---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: remove pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: d316cb98efc730ed3e99f6a5dac2b969e3437129
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="remove-pswaauthorizationrule"></a><span data-ttu-id="19c2a-103">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="19c2a-103">Remove-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="19c2a-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="19c2a-104">SYNOPSIS</span></span>

<span data-ttu-id="19c2a-105">Rimuove da Accesso Web Windows PowerShell® una regola di autorizzazione specificata.</span><span class="sxs-lookup"><span data-stu-id="19c2a-105">Removes a specified authorization rule from Windows PowerShell® Web Access.</span></span>

## <a name="syntax"></a><span data-ttu-id="19c2a-106">SINTASSI</span><span class="sxs-lookup"><span data-stu-id="19c2a-106">SYNTAX</span></span>

###  <a name="id"></a><span data-ttu-id="19c2a-107">Id</span><span class="sxs-lookup"><span data-stu-id="19c2a-107">Id</span></span>
```
Remove-PswaAuthorizationRule [-Id] <Int32[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

### <a name="rule"></a><span data-ttu-id="19c2a-108">Regola</span><span class="sxs-lookup"><span data-stu-id="19c2a-108">Rule</span></span>
```
Remove-PswaAuthorizationRule [-Rule] <PswaAuthorizationRule[]> [-Force] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="19c2a-109">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="19c2a-109">DESCRIPTION</span></span>

<span data-ttu-id="19c2a-110">Rimuove da Accesso Web Windows PowerShell una regola di autorizzazione specificata.</span><span class="sxs-lookup"><span data-stu-id="19c2a-110">Removes a specified authorization rule from Windows PowerShell Web Access.</span></span>

## <a name="parameters"></a><span data-ttu-id="19c2a-111">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="19c2a-111">PARAMETERS</span></span>

### <a name="-force"></a><span data-ttu-id="19c2a-112">-Force</span><span class="sxs-lookup"><span data-stu-id="19c2a-112">-Force</span></span>

<span data-ttu-id="19c2a-113">Esegue il cmdlet senza chiedere conferma.</span><span class="sxs-lookup"><span data-stu-id="19c2a-113">Runs the cmdlet without prompting for confirmation.</span></span> <span data-ttu-id="19c2a-114">Per impostazione predefinita il cmdlet chiede conferma prima di procedere.</span><span class="sxs-lookup"><span data-stu-id="19c2a-114">By default the cmdlet asks for confirmation before proceeding.</span></span>

|||  
|-|-|
| <span data-ttu-id="19c2a-115">Alias</span><span class="sxs-lookup"><span data-stu-id="19c2a-115">Aliases</span></span>                              | <span data-ttu-id="19c2a-116">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-116">none</span></span>                                 |
| <span data-ttu-id="19c2a-117">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="19c2a-117">Required?</span></span>                            | <span data-ttu-id="19c2a-118">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-118">false</span></span>                                |
| <span data-ttu-id="19c2a-119">Posizione?</span><span class="sxs-lookup"><span data-stu-id="19c2a-119">Position?</span></span>                            | <span data-ttu-id="19c2a-120">denominato</span><span class="sxs-lookup"><span data-stu-id="19c2a-120">named</span></span>                                |
| <span data-ttu-id="19c2a-121">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="19c2a-121">Default Value</span></span>                        | <span data-ttu-id="19c2a-122">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-122">none</span></span>                                 |
| <span data-ttu-id="19c2a-123">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="19c2a-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="19c2a-124">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-124">false</span></span>                                |
| <span data-ttu-id="19c2a-125">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="19c2a-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="19c2a-126">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-126">false</span></span>                                |

### <a name="-id-ltint32gt"></a><span data-ttu-id="19c2a-127">-Id &lt;Int32\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="19c2a-127">-Id &lt;Int32\[\]&gt;</span></span>

<span data-ttu-id="19c2a-128">Specifica gli identificatori (ID) di una o più regole da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="19c2a-128">Specifies the identifiers (IDs) of one or more rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="19c2a-129">Alias</span><span class="sxs-lookup"><span data-stu-id="19c2a-129">Aliases</span></span>                              | <span data-ttu-id="19c2a-130">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-130">none</span></span>                                 |
| <span data-ttu-id="19c2a-131">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="19c2a-131">Required?</span></span>                            | <span data-ttu-id="19c2a-132">True</span><span class="sxs-lookup"><span data-stu-id="19c2a-132">true</span></span>                                 |
| <span data-ttu-id="19c2a-133">Posizione?</span><span class="sxs-lookup"><span data-stu-id="19c2a-133">Position?</span></span>                            | <span data-ttu-id="19c2a-134">2</span><span class="sxs-lookup"><span data-stu-id="19c2a-134">2</span></span>                                    |
| <span data-ttu-id="19c2a-135">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="19c2a-135">Default Value</span></span>                        | <span data-ttu-id="19c2a-136">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-136">none</span></span>                                 |
| <span data-ttu-id="19c2a-137">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="19c2a-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="19c2a-138">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="19c2a-138">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="19c2a-139">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="19c2a-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="19c2a-140">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-140">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="19c2a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="19c2a-141">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="19c2a-142">Specifica le regole da rimuovere.</span><span class="sxs-lookup"><span data-stu-id="19c2a-142">Specifies the rules to remove.</span></span>

|||  
|-|-|
| <span data-ttu-id="19c2a-143">Alias</span><span class="sxs-lookup"><span data-stu-id="19c2a-143">Aliases</span></span>                              | <span data-ttu-id="19c2a-144">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-144">none</span></span>                                 |
| <span data-ttu-id="19c2a-145">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="19c2a-145">Required?</span></span>                            | <span data-ttu-id="19c2a-146">True</span><span class="sxs-lookup"><span data-stu-id="19c2a-146">true</span></span>                                 |
| <span data-ttu-id="19c2a-147">Posizione?</span><span class="sxs-lookup"><span data-stu-id="19c2a-147">Position?</span></span>                            | <span data-ttu-id="19c2a-148">2</span><span class="sxs-lookup"><span data-stu-id="19c2a-148">2</span></span>                                    |
| <span data-ttu-id="19c2a-149">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="19c2a-149">Default Value</span></span>                        | <span data-ttu-id="19c2a-150">Nessuno</span><span class="sxs-lookup"><span data-stu-id="19c2a-150">none</span></span>                                 |
| <span data-ttu-id="19c2a-151">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="19c2a-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="19c2a-152">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="19c2a-152">True (ByValue)</span></span>                       |
| <span data-ttu-id="19c2a-153">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="19c2a-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="19c2a-154">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="19c2a-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="19c2a-155">-Confirm</span></span>

<span data-ttu-id="19c2a-156">Richiede conferma prima di eseguire il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19c2a-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="19c2a-157">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="19c2a-157">Required?</span></span>                            | <span data-ttu-id="19c2a-158">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-158">false</span></span>                                |
| <span data-ttu-id="19c2a-159">Posizione?</span><span class="sxs-lookup"><span data-stu-id="19c2a-159">Position?</span></span>                            | <span data-ttu-id="19c2a-160">denominato</span><span class="sxs-lookup"><span data-stu-id="19c2a-160">named</span></span>                                |
| <span data-ttu-id="19c2a-161">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="19c2a-161">Default Value</span></span>                        | <span data-ttu-id="19c2a-162">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-162">false</span></span>                                |
| <span data-ttu-id="19c2a-163">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="19c2a-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="19c2a-164">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-164">false</span></span>                                |
| <span data-ttu-id="19c2a-165">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="19c2a-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="19c2a-166">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="19c2a-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="19c2a-167">-WhatIf</span></span>

<span data-ttu-id="19c2a-168">Mostra gli effetti dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19c2a-168">Shows what would happen if the cmdlet runs.</span></span> <span data-ttu-id="19c2a-169">Il cmdlet non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="19c2a-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="19c2a-170">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="19c2a-170">Required?</span></span>                            | <span data-ttu-id="19c2a-171">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-171">false</span></span>                                |
| <span data-ttu-id="19c2a-172">Posizione?</span><span class="sxs-lookup"><span data-stu-id="19c2a-172">Position?</span></span>                            | <span data-ttu-id="19c2a-173">denominato</span><span class="sxs-lookup"><span data-stu-id="19c2a-173">named</span></span>                                |
| <span data-ttu-id="19c2a-174">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="19c2a-174">Default Value</span></span>                        | <span data-ttu-id="19c2a-175">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-175">false</span></span>                                |
| <span data-ttu-id="19c2a-176">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="19c2a-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="19c2a-177">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-177">false</span></span>                                |
| <span data-ttu-id="19c2a-178">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="19c2a-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="19c2a-179">False</span><span class="sxs-lookup"><span data-stu-id="19c2a-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="19c2a-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="19c2a-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="19c2a-181">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="19c2a-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="19c2a-182">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="19c2a-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="19c2a-183">INPUT</span><span class="sxs-lookup"><span data-stu-id="19c2a-183">INPUTS</span></span>

###  <a name="int"></a><span data-ttu-id="19c2a-184">int\[\]</span><span class="sxs-lookup"><span data-stu-id="19c2a-184">int\[\]</span></span>

<span data-ttu-id="19c2a-185">Questo cmdlet accetta una matrice di numeri interi o una matrice di oggetti PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="19c2a-185">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

###  <a name="pswaauthorizationrule"></a><span data-ttu-id="19c2a-186">PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="19c2a-186">PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="19c2a-187">Questo cmdlet accetta una matrice di numeri interi o una matrice di oggetti PswaAuthorizationRule.</span><span class="sxs-lookup"><span data-stu-id="19c2a-187">This cmdlet accepts either an array of integers or an array of PswaAuthorizationRule objects.</span></span>

##  <a name="outputs"></a><span data-ttu-id="19c2a-188">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="19c2a-188">OUTPUTS</span></span>

<span data-ttu-id="19c2a-189">Questo cmdlet non genera alcun output.</span><span class="sxs-lookup"><span data-stu-id="19c2a-189">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="19c2a-190">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="19c2a-190">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="19c2a-191">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="19c2a-191">EXAMPLE 1</span></span>

<span data-ttu-id="19c2a-192">Questo esempio rimuove la regola di autorizzazione con ID di *2*.</span><span class="sxs-lookup"><span data-stu-id="19c2a-192">This example removes the authorization rule with an ID of *2*.</span></span>

```
Remove-PswaAuthorizationRule –Id 2
```

### <a name="example-2-example-2-subheading"></a><span data-ttu-id="19c2a-193">ESEMPIO 2 {#example-2 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="19c2a-193">EXAMPLE 2 {#example-2 .subHeading}</span></span>

<span data-ttu-id="19c2a-194">In questo esempio vengono rimosse tutte le regole di autorizzazione e viene richiesta la conferma da parte dell'utente.</span><span class="sxs-lookup"><span data-stu-id="19c2a-194">This example removes all authorization rules and also requires confirmation by the user.</span></span>

```
Get-PswaAuthorizationRule | Remove-PswaAuthorizationRule -Confirm
```

##  <a name="related-topics"></a><span data-ttu-id="19c2a-195">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="19c2a-195">Related topics</span></span>

-  [<span data-ttu-id="19c2a-196">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="19c2a-196">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="19c2a-197">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="19c2a-197">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="19c2a-198">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="19c2a-198">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="19c2a-199">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="19c2a-199">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
