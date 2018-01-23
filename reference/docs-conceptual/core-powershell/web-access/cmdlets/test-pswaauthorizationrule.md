---
description: 
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: test pswaauthorizationrule
ms.technology: powershell
ms.openlocfilehash: fb2937397616160c70b056e412e42fb8ff4c2f27
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="test-pswaauthorizationrule"></a><span data-ttu-id="6fda3-103">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fda3-103">Test-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="6fda3-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="6fda3-104">SYNOPSIS</span></span>

<span data-ttu-id="6fda3-105">Verifica se esiste una regola per un utente, un computer o un endpoint specificato.</span><span class="sxs-lookup"><span data-stu-id="6fda3-105">Verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>

## <a name="syntax"></a><span data-ttu-id="6fda3-106">SINTASSI</span><span class="sxs-lookup"><span data-stu-id="6fda3-106">SYNTAX</span></span>

### <a name="computername"></a><span data-ttu-id="6fda3-107">ComputerName</span><span class="sxs-lookup"><span data-stu-id="6fda3-107">ComputerName</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ComputerName] <String> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

### <a name="connectionuri"></a><span data-ttu-id="6fda3-108">ConnectionUri</span><span class="sxs-lookup"><span data-stu-id="6fda3-108">ConnectionUri</span></span>
```
Test-PswaAuthorizationRule [-UserName] <String> [-ConnectionUri] <Uri> [[-ConfigurationName] <String> ] [-Credential <PSCredential> ] [-Rule <PswaAuthorizationRule[]> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="6fda3-109">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="6fda3-109">DESCRIPTION</span></span>

<span data-ttu-id="6fda3-110">Il cmdlet **Test-PswaAuthorizationRule** verifica se esiste una regola per un utente, un computer o un endpoint specificato.</span><span class="sxs-lookup"><span data-stu-id="6fda3-110">The **Test-PswaAuthorizationRule** cmdlet verifies whether a rule exists for a specified user, computer, or endpoint.</span></span>
<span data-ttu-id="6fda3-111">Può essere usato anche per testare le regole di autorizzazione per verificare se la richiesta di accesso a un determinato utente, computer o endpoint è autorizzata.</span><span class="sxs-lookup"><span data-stu-id="6fda3-111">This cmdlet can also be used to test authorization rules, to validate that a particular user, computer or endpoint access request is authorized.</span></span>
<span data-ttu-id="6fda3-112">Per impostazione predefinita, questo cmdlet valuta tutte le regole nel file di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="6fda3-112">By default, this cmdlet evaluates all rules in the authorization file.</span></span>
<span data-ttu-id="6fda3-113">Tuttavia, è possibile specificare un sottoinsieme di regole da testare.</span><span class="sxs-lookup"><span data-stu-id="6fda3-113">However, you can specify a subset of rules to test.</span></span>

<span data-ttu-id="6fda3-114">È possibile usare questo cmdlet per la risoluzione degli errori di autenticazione.</span><span class="sxs-lookup"><span data-stu-id="6fda3-114">You can use this cmdlet to help troubleshoot authentication failures.</span></span>

<span data-ttu-id="6fda3-115">I parametri per questo cmdlet corrispondono ai campi della pagina di accesso di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="6fda3-115">The parameters for this cmdlet correspond to fields on the Windows PowerShell® Web Access sign-on page.</span></span>

## <a name="parameters"></a><span data-ttu-id="6fda3-116">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="6fda3-116">PARAMETERS</span></span>

### <a name="-computername-ltstringgt"></a><span data-ttu-id="6fda3-117">-ComputerName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-117">-ComputerName &lt;String&gt;</span></span>

<span data-ttu-id="6fda3-118">Specifica il nome del computer da testare.</span><span class="sxs-lookup"><span data-stu-id="6fda3-118">Specifies the name of the computer to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-119">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-119">Aliases</span></span>                              | <span data-ttu-id="6fda3-120">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-120">none</span></span>                                 |
| <span data-ttu-id="6fda3-121">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-121">Required?</span></span>                            | <span data-ttu-id="6fda3-122">True</span><span class="sxs-lookup"><span data-stu-id="6fda3-122">true</span></span>                                 |
| <span data-ttu-id="6fda3-123">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-123">Position?</span></span>                            | <span data-ttu-id="6fda3-124">2</span><span class="sxs-lookup"><span data-stu-id="6fda3-124">2</span></span>                                    |
| <span data-ttu-id="6fda3-125">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-125">Default Value</span></span>                        | <span data-ttu-id="6fda3-126">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-126">none</span></span>                                 |
| <span data-ttu-id="6fda3-127">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-127">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-128">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-128">false</span></span>                                |
| <span data-ttu-id="6fda3-129">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-129">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-130">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-130">false</span></span>                                |

### <a name="-configurationname-ltstringgt"></a><span data-ttu-id="6fda3-131">-ConfigurationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-131">-ConfigurationName &lt;String&gt;</span></span>

<span data-ttu-id="6fda3-132">Specifica il nome della configurazione di sessione di Windows PowerShell, nota anche come endpoint o spazio di esecuzione, per eseguire il test.</span><span class="sxs-lookup"><span data-stu-id="6fda3-132">Specifies the name of the Windows PowerShell session configuration, also known as endpoint or runspace, to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-133">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-133">Aliases</span></span>                              | <span data-ttu-id="6fda3-134">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-134">none</span></span>                                 |
| <span data-ttu-id="6fda3-135">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-135">Required?</span></span>                            | <span data-ttu-id="6fda3-136">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-136">false</span></span>                                |
| <span data-ttu-id="6fda3-137">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-137">Position?</span></span>                            | <span data-ttu-id="6fda3-138">3</span><span class="sxs-lookup"><span data-stu-id="6fda3-138">3</span></span>                                    |
| <span data-ttu-id="6fda3-139">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-139">Default Value</span></span>                        | <span data-ttu-id="6fda3-140">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-140">none</span></span>                                 |
| <span data-ttu-id="6fda3-141">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-142">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-142">false</span></span>                                |
| <span data-ttu-id="6fda3-143">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-144">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-144">false</span></span>                                |

### <a name="-connectionuri-lturigt"></a><span data-ttu-id="6fda3-145">-ConnectionUri &lt;Uri&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-145">-ConnectionUri &lt;Uri&gt;</span></span>

<span data-ttu-id="6fda3-146">Specifica l'URI della connessione da testare.</span><span class="sxs-lookup"><span data-stu-id="6fda3-146">Specifies the connection URI to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-147">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-147">Aliases</span></span>                              | <span data-ttu-id="6fda3-148">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-148">none</span></span>                                 |
| <span data-ttu-id="6fda3-149">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-149">Required?</span></span>                            | <span data-ttu-id="6fda3-150">True</span><span class="sxs-lookup"><span data-stu-id="6fda3-150">true</span></span>                                 |
| <span data-ttu-id="6fda3-151">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-151">Position?</span></span>                            | <span data-ttu-id="6fda3-152">2</span><span class="sxs-lookup"><span data-stu-id="6fda3-152">2</span></span>                                    |
| <span data-ttu-id="6fda3-153">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-153">Default Value</span></span>                        | <span data-ttu-id="6fda3-154">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-154">none</span></span>                                 |
| <span data-ttu-id="6fda3-155">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-156">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-156">false</span></span>                                |
| <span data-ttu-id="6fda3-157">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-158">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-158">false</span></span>                                |

### <a name="-credential-ltpscredentialgt"></a><span data-ttu-id="6fda3-159">-Credential &lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-159">-Credential &lt;PSCredential&gt;</span></span>

<span data-ttu-id="6fda3-160">Specifica un oggetto **PSCredential** per un account utente che verrà usato per testare le regole di autorizzazione di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="6fda3-160">Specifies a **PSCredential** object for a user account that you want to use to test Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="6fda3-161">Se non si aggiunge questo parametro, il cmdlet usa l'account utente attualmente connesso.</span><span class="sxs-lookup"><span data-stu-id="6fda3-161">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="6fda3-162">Per ottenere un oggetto **PSCredential**, necessario per testare le regole di autorizzazione in modalità remota, eseguire il cmdlet [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936).</span><span class="sxs-lookup"><span data-stu-id="6fda3-162">To get a **PSCredential** object, which is required to test authorization rules remotely, run the [Get-Credential](http://go.microsoft.com/fwlink/?LinkID=293936) cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-163">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-163">Aliases</span></span>                              | <span data-ttu-id="6fda3-164">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-164">none</span></span>                                 |
| <span data-ttu-id="6fda3-165">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-165">Required?</span></span>                            | <span data-ttu-id="6fda3-166">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-166">false</span></span>                                |
| <span data-ttu-id="6fda3-167">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-167">Position?</span></span>                            | <span data-ttu-id="6fda3-168">denominato</span><span class="sxs-lookup"><span data-stu-id="6fda3-168">named</span></span>                                |
| <span data-ttu-id="6fda3-169">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-169">Default Value</span></span>                        | <span data-ttu-id="6fda3-170">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-170">none</span></span>                                 |
| <span data-ttu-id="6fda3-171">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-171">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-172">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-172">false</span></span>                                |
| <span data-ttu-id="6fda3-173">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-173">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-174">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-174">false</span></span>                                |

### <a name="-rule-ltpswaauthorizationrulegt"></a><span data-ttu-id="6fda3-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-175">-Rule &lt;PswaAuthorizationRule\[\]&gt;</span></span>

<span data-ttu-id="6fda3-176">Specifica un sottoinsieme di regole da testare.</span><span class="sxs-lookup"><span data-stu-id="6fda3-176">Specifies a subset of rules to test.</span></span> <span data-ttu-id="6fda3-177">Se questo parametro non viene specificato, il cmdlet esegue i test su tutte le regole di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="6fda3-177">If this parameter is not specified, then this cmdlet tests against all authorization rules.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-178">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-178">Aliases</span></span>                              | <span data-ttu-id="6fda3-179">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-179">none</span></span>                                 |
| <span data-ttu-id="6fda3-180">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-180">Required?</span></span>                            | <span data-ttu-id="6fda3-181">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-181">false</span></span>                                |
| <span data-ttu-id="6fda3-182">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-182">Position?</span></span>                            | <span data-ttu-id="6fda3-183">denominato</span><span class="sxs-lookup"><span data-stu-id="6fda3-183">named</span></span>                                |
| <span data-ttu-id="6fda3-184">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-184">Default Value</span></span>                        | <span data-ttu-id="6fda3-185">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-185">none</span></span>                                 |
| <span data-ttu-id="6fda3-186">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-186">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-187">True (ByValue)</span><span class="sxs-lookup"><span data-stu-id="6fda3-187">True (ByValue)</span></span>                       |
| <span data-ttu-id="6fda3-188">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-188">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-189">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-189">false</span></span>                                |

### <a name="-username-ltstringgt"></a><span data-ttu-id="6fda3-190">-UserName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-190">-UserName &lt;String&gt;</span></span>

<span data-ttu-id="6fda3-191">Specifica il nome dell'utente da testare.</span><span class="sxs-lookup"><span data-stu-id="6fda3-191">Specifies the name of the user to test.</span></span>

|||  
|-|-|
| <span data-ttu-id="6fda3-192">Alias</span><span class="sxs-lookup"><span data-stu-id="6fda3-192">Aliases</span></span>                              | <span data-ttu-id="6fda3-193">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-193">none</span></span>                                 |
| <span data-ttu-id="6fda3-194">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="6fda3-194">Required?</span></span>                            | <span data-ttu-id="6fda3-195">True</span><span class="sxs-lookup"><span data-stu-id="6fda3-195">true</span></span>                                 |
| <span data-ttu-id="6fda3-196">Posizione?</span><span class="sxs-lookup"><span data-stu-id="6fda3-196">Position?</span></span>                            | <span data-ttu-id="6fda3-197">1</span><span class="sxs-lookup"><span data-stu-id="6fda3-197">1</span></span>                                    |
| <span data-ttu-id="6fda3-198">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="6fda3-198">Default Value</span></span>                        | <span data-ttu-id="6fda3-199">Nessuno</span><span class="sxs-lookup"><span data-stu-id="6fda3-199">none</span></span>                                 |
| <span data-ttu-id="6fda3-200">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="6fda3-200">Accept Pipeline Input?</span></span>               | <span data-ttu-id="6fda3-201">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-201">false</span></span>                                |
| <span data-ttu-id="6fda3-202">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="6fda3-202">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="6fda3-203">False</span><span class="sxs-lookup"><span data-stu-id="6fda3-203">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="6fda3-204">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="6fda3-204">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="6fda3-205">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="6fda3-205">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="6fda3-206">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="6fda3-206">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="6fda3-207">INPUT</span><span class="sxs-lookup"><span data-stu-id="6fda3-207">INPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="6fda3-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="6fda3-208">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="6fda3-209">Questo cmdlet accetta una matrice di oggetti PswaAuthorizationRule come input.</span><span class="sxs-lookup"><span data-stu-id="6fda3-209">This cmdlet accepts an array of PswaAuthorizationRule objects as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="6fda3-210">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="6fda3-210">OUTPUTS</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="6fda3-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span><span class="sxs-lookup"><span data-stu-id="6fda3-211">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule\[\]</span></span>

<span data-ttu-id="6fda3-212">Questo cmdlet genera una matrice di oggetti PswaAuthorizationRule come output.</span><span class="sxs-lookup"><span data-stu-id="6fda3-212">This cmdlet produces an array of PswaAuthorizationRule objects as output.</span></span>

## <a name="examples"></a><span data-ttu-id="6fda3-213">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="6fda3-213">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="6fda3-214">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="6fda3-214">EXAMPLE 1</span></span>

<span data-ttu-id="6fda3-215">Questo esempio verifica tutte le regole di autorizzazione per visualizzare quelle che consentono all'utente *contoso\\mhanson* di connettersi al computer *srv2* e usare una configurazione di sessione di Windows PowerShell denominata *test*.</span><span class="sxs-lookup"><span data-stu-id="6fda3-215">This example tests all authorization rules in order to display all the rules that allow the user *contoso\\mhanson* to connect to the computer *srv2* and use a Windows PowerShell session configuration named *test*.</span></span>

```
Test-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserName contoso\mhanson -ConfigurationName test
```

### <a name="example-2"></a><span data-ttu-id="6fda3-216">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="6fda3-216">EXAMPLE 2</span></span>

<span data-ttu-id="6fda3-217">In questo esempio viene eseguito un test di tutte le regole di autorizzazione per verificare quali regole si applicano all'utente *contoso\\mhanson*.</span><span class="sxs-lookup"><span data-stu-id="6fda3-217">This example tests all authorization rules to check which authorization rules apply to the user *contoso\\mhanson*.</span></span>

```
Test-PswaAuthorizationRule -UserName contoso\mhanson -ComputerName *
```

## <a name="related-topics"></a><span data-ttu-id="6fda3-218">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="6fda3-218">Related topics</span></span>

- [<span data-ttu-id="6fda3-219">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fda3-219">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="6fda3-220">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fda3-220">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="6fda3-221">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="6fda3-221">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
- [<span data-ttu-id="6fda3-222">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="6fda3-222">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
