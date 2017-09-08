---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: 1b480b68c7ce2064f42281d8c5d76156a39e0222
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="test-pswaauthorizationrule"></a><span data-ttu-id="e6488-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6488-103">Test-PswaAuthorizationRule</span></span>

##  <a name="synopsis"></a><span data-ttu-id="e6488-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="e6488-104">SYNOPSIS</span></span>

<span data-ttu-id="e6488-105">Verifica se esiste una regola per un utente, un computer o un endpoint specificato.</span><span class="sxs-lookup"><span data-stu-id="e6488-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="e6488-106">SINTASSI</span><span class="sxs-lookup"><span data-stu-id="e6488-106">SYNTAX</span></span>

###  <a name="computername"></a><span data-ttu-id="e6488-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="e6488-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

###  <a name="connectionuri"></a><span data-ttu-id="e6488-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="e6488-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="e6488-109">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="e6488-109">DESCRIPTION</span></span>

<span data-ttu-id="e6488-110">Il cmdlet **Test-PswaAuthorizationRule** verifica se esiste una regola per un utente, un computer o un endpoint specificato.</span><span class="sxs-lookup"><span data-stu-id="e6488-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="e6488-111">Può essere usato anche per testare le regole di autorizzazione per verificare se la richiesta di accesso a un determinato utente, computer o endpoint è autorizzata.</span><span class="sxs-lookup"><span data-stu-id="e6488-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="e6488-112">Per impostazione predefinita, questo cmdlet valuta tutte le regole nel file di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="e6488-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="e6488-113">Tuttavia, è possibile specificare un sottoinsieme di regole da testare.</span><span class="sxs-lookup"><span data-stu-id="e6488-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="e6488-114">È possibile usare questo cmdlet per la risoluzione degli errori di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="e6488-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="e6488-115">I parametri per questo cmdlet corrispondono ai campi della pagina di accesso di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="e6488-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="e6488-116">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="e6488-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="e6488-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="e6488-118">Specifica il nome del computer da testare.</span><span class="sxs-lookup"><span data-stu-id="e6488-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-119">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-119">Aliases</span></span>                              | <span data-ttu-id="e6488-120">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-120">none</span></span>                                 |
| <span data-ttu-id="e6488-121">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-121">Required?</span></span>                            | <span data-ttu-id="e6488-122">True</span><span class="sxs-lookup"><span data-stu-id="e6488-122">true</span></span>                                 |
| <span data-ttu-id="e6488-123">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-123">Position?</span></span>                            | <span data-ttu-id="e6488-124">2</span><span class="sxs-lookup"><span data-stu-id="e6488-124">2</span></span>                                    |
| <span data-ttu-id="e6488-125">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-125">Default Value</span></span>                        | <span data-ttu-id="e6488-126">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-126">none</span></span>                                 |
| <span data-ttu-id="e6488-127">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-128">False</span><span class="sxs-lookup"><span data-stu-id="e6488-128">false</span></span>                                |
| <span data-ttu-id="e6488-129">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-130">False</span><span class="sxs-lookup"><span data-stu-id="e6488-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="e6488-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="e6488-132">Specifica il nome della configurazione di sessione di Windows PowerShell, nota anche come endpoint o spazio di esecuzione, per eseguire il test.</span><span class="sxs-lookup"><span data-stu-id="e6488-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-133">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-133">Aliases</span></span>                              | <span data-ttu-id="e6488-134">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-134">none</span></span>                                 |
| <span data-ttu-id="e6488-135">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-135">Required?</span></span>                            | <span data-ttu-id="e6488-136">False</span><span class="sxs-lookup"><span data-stu-id="e6488-136">false</span></span>                                |
| <span data-ttu-id="e6488-137">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-137">Position?</span></span>                            | <span data-ttu-id="e6488-138">3</span><span class="sxs-lookup"><span data-stu-id="e6488-138">3</span></span>                                    |
| <span data-ttu-id="e6488-139">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-139">Default Value</span></span>                        | <span data-ttu-id="e6488-140">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-140">none</span></span>                                 |
| <span data-ttu-id="e6488-141">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-142">False</span><span class="sxs-lookup"><span data-stu-id="e6488-142">false</span></span>                                |
| <span data-ttu-id="e6488-143">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-144">False</span><span class="sxs-lookup"><span data-stu-id="e6488-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="e6488-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="e6488-146">Specifica l'URI della connessione da testare.</span><span class="sxs-lookup"><span data-stu-id="e6488-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-147">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-147">Aliases</span></span>                              | <span data-ttu-id="e6488-148">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-148">none</span></span>                                 |
| <span data-ttu-id="e6488-149">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-149">Required?</span></span>                            | <span data-ttu-id="e6488-150">True</span><span class="sxs-lookup"><span data-stu-id="e6488-150">true</span></span>                                 |
| <span data-ttu-id="e6488-151">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-151">Position?</span></span>                            | <span data-ttu-id="e6488-152">2</span><span class="sxs-lookup"><span data-stu-id="e6488-152">2</span></span>                                    |
| <span data-ttu-id="e6488-153">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-153">Default Value</span></span>                        | <span data-ttu-id="e6488-154">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-154">none</span></span>                                 |
| <span data-ttu-id="e6488-155">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-156">False</span><span class="sxs-lookup"><span data-stu-id="e6488-156">false</span></span>                                |
| <span data-ttu-id="e6488-157">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-158">False</span><span class="sxs-lookup"><span data-stu-id="e6488-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="e6488-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="e6488-160">Specifica un oggetto **PSCredential** per un account utente che verrà usato per testare le regole di autorizzazione di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e6488-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="e6488-161">Se non si aggiunge questo parametro, il cmdlet usa l'account utente attualmente connesso.</span><span class="sxs-lookup"><span data-stu-id="e6488-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="e6488-162">Per ottenere un oggetto **PSCredential**, necessario per testare le regole di autorizzazione in modalità remota, eseguire il cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="e6488-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-163">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-163">Aliases</span></span>                              | <span data-ttu-id="e6488-164">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-164">none</span></span>                                 |
| <span data-ttu-id="e6488-165">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-165">Required?</span></span>                            | <span data-ttu-id="e6488-166">False</span><span class="sxs-lookup"><span data-stu-id="e6488-166">false</span></span>                                |
| <span data-ttu-id="e6488-167">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-167">Position?</span></span>                            | <span data-ttu-id="e6488-168">denominato</span><span class="sxs-lookup"><span data-stu-id="e6488-168">named</span></span>                                |
| <span data-ttu-id="e6488-169">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-169">Default Value</span></span>                        | <span data-ttu-id="e6488-170">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-170">none</span></span>                                 |
| <span data-ttu-id="e6488-171">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-172">False</span><span class="sxs-lookup"><span data-stu-id="e6488-172">false</span></span>                                |
| <span data-ttu-id="e6488-173">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-174">False</span><span class="sxs-lookup"><span data-stu-id="e6488-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="e6488-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="e6488-176">Specifica un sottoinsieme di regole da testare.</span><span class="sxs-lookup"><span data-stu-id="e6488-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="e6488-177">Se questo parametro non viene specificato, il cmdlet esegue i test su tutte le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="e6488-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-178">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-178">Aliases</span></span>                              | <span data-ttu-id="e6488-179">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-179">none</span></span>                                 |
| <span data-ttu-id="e6488-180">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-180">Required?</span></span>                            | <span data-ttu-id="e6488-181">False</span><span class="sxs-lookup"><span data-stu-id="e6488-181">false</span></span>                                |
| <span data-ttu-id="e6488-182">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-182">Position?</span></span>                            | <span data-ttu-id="e6488-183">denominato</span><span class="sxs-lookup"><span data-stu-id="e6488-183">named</span></span>                                |
| <span data-ttu-id="e6488-184">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-184">Default Value</span></span>                        | <span data-ttu-id="e6488-185">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-185">none</span></span>                                 |
| <span data-ttu-id="e6488-186">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="e6488-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="e6488-188">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-189">False</span><span class="sxs-lookup"><span data-stu-id="e6488-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="e6488-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="e6488-191">Specifica il nome dell'utente da testare.</span><span class="sxs-lookup"><span data-stu-id="e6488-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="e6488-192">Alias</span><span class="sxs-lookup"><span data-stu-id="e6488-192">Aliases</span></span>                              | <span data-ttu-id="e6488-193">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-193">none</span></span>                                 |
| <span data-ttu-id="e6488-194">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="e6488-194">Required?</span></span>                            | <span data-ttu-id="e6488-195">True</span><span class="sxs-lookup"><span data-stu-id="e6488-195">true</span></span>                                 |
| <span data-ttu-id="e6488-196">Posizione?</span><span class="sxs-lookup"><span data-stu-id="e6488-196">Position?</span></span>                            | <span data-ttu-id="e6488-197">1</span><span class="sxs-lookup"><span data-stu-id="e6488-197">1</span></span>                                    |
| <span data-ttu-id="e6488-198">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="e6488-198">Default Value</span></span>                        | <span data-ttu-id="e6488-199">Nessuno</span><span class="sxs-lookup"><span data-stu-id="e6488-199">none</span></span>                                 |
| <span data-ttu-id="e6488-200">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="e6488-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="e6488-201">False</span><span class="sxs-lookup"><span data-stu-id="e6488-201">false</span></span>                                |
| <span data-ttu-id="e6488-202">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="e6488-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="e6488-203">False</span><span class="sxs-lookup"><span data-stu-id="e6488-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="e6488-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="e6488-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="e6488-205">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="e6488-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="e6488-206">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="e6488-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="e6488-207">INPUT</span><span class="sxs-lookup"><span data-stu-id="e6488-207">INPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="e6488-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="e6488-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="e6488-209">Questo cmdlet accetta una matrice di oggetti PswaAuthorizationRule come input.</span><span class="sxs-lookup"><span data-stu-id="e6488-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

##  <a name="outputs"></a><span data-ttu-id="e6488-210">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="e6488-210">OUTPUTS</span></span>

###  <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="e6488-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="e6488-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="e6488-212">Questo cmdlet genera una matrice di oggetti PswaAuthorizationRule come output.</span><span class="sxs-lookup"><span data-stu-id="e6488-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="e6488-213">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="e6488-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="e6488-214">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="e6488-214">EXAMPLE 1</span></span>

<span data-ttu-id="e6488-215">Questo esempio verifica tutte le regole di autorizzazione per visualizzare quelle che consentono all'utente *contoso\\mhanson* di connettersi al computer *srv2* e usare una configurazione di sessione di Windows PowerShell denominata *test*.</span><span class="sxs-lookup"><span data-stu-id="e6488-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="e6488-216">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="e6488-216">EXAMPLE 2</span></span>

<span data-ttu-id="e6488-217">In questo esempio viene eseguito un test di tutte le regole di autorizzazione per verificare quali regole si applicano all'utente *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="e6488-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

##  <a name="related-topics"></a><span data-ttu-id="e6488-218">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="e6488-218">Related topics</span></span>

-  [<span data-ttu-id="e6488-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6488-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="e6488-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6488-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="e6488-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="e6488-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="e6488-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="e6488-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
