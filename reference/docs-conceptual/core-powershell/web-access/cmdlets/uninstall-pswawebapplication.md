---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: uninstall pswawebapplication
ms.technology: powershell
ms.openlocfilehash: 64d546427e44d7bd284da8f682a7218afbadd0ad
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2017
---
#  <a name="uninstall-pswawebapplication"></a><span data-ttu-id="28a90-103">Uninstall-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="28a90-103">Uninstall-PswaWebApplication</span></span>

##  <a name="synopsis"></a><span data-ttu-id="28a90-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="28a90-104">SYNOPSIS</span></span>

<span data-ttu-id="28a90-105">Disinstalla l'applicazione Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28a90-105">Uninstalls the Windows PowerShell® web application.</span></span>

## <a name="syntax"></a><span data-ttu-id="28a90-106">SINTASSI</span><span class="sxs-lookup"><span data-stu-id="28a90-106">SYNTAX</span></span>

###  <a name="default"></a><span data-ttu-id="28a90-107">Default</span><span class="sxs-lookup"><span data-stu-id="28a90-107">Default</span></span>
```
Uninstall-PswaWebApplication [[-WebApplicationName] <String> ] [-DeleteTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="28a90-108">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="28a90-108">DESCRIPTION</span></span>

<span data-ttu-id="28a90-109">Il cmdlet **Uninstall-PswaWebApplication** disinstalla l'applicazione Web Windows PowerShell e rimuove il sito Web da IIS.</span><span class="sxs-lookup"><span data-stu-id="28a90-109">The **Uninstall-PswaWebApplication** cmdlet uninstalls the Windows PowerShell web application and removes the website from IIS.</span></span> <span data-ttu-id="28a90-110">Il cmdlet non disinstalla IIS o altre funzionalità installate perché sono necessarie per l'esecuzione di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28a90-110">The cmdlet does not uninstall IIS, or any other features installed because they were required for Windows PowerShell to run.</span></span>

## <a name="parameters"></a><span data-ttu-id="28a90-111">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="28a90-111">PARAMETERS</span></span>

### <a name="-deletetestcertificate"></a><span data-ttu-id="28a90-112">-DeleteTestCertificate</span><span class="sxs-lookup"><span data-stu-id="28a90-112">-DeleteTestCertificate</span></span>

<span data-ttu-id="28a90-113">Indica che il certificato di test creato dal cmdlet **Install\_PswaWebApplication**, con il parametro **UseTestCertificate**, viene eliminato.</span><span class="sxs-lookup"><span data-stu-id="28a90-113">Indicates that the test certificates created by the **Install\_PswaWebApplication** cmdlet (with the **UseTestCertificate** parameter) is deleted.</span></span>
<span data-ttu-id="28a90-114">Viene rimosso solo il certificato di test con lo stesso nome di quello creato dal cmdlet **Install-PswaWebApplication**.</span><span class="sxs-lookup"><span data-stu-id="28a90-114">Only the test certificate with the same name as the one created by the **Install-PswaWebApplication** cmdlet is removed.</span></span>

|||  
|-|-|
| <span data-ttu-id="28a90-115">Alias</span><span class="sxs-lookup"><span data-stu-id="28a90-115">Aliases</span></span>                              | <span data-ttu-id="28a90-116">Nessuno</span><span class="sxs-lookup"><span data-stu-id="28a90-116">none</span></span>                                 |
| <span data-ttu-id="28a90-117">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="28a90-117">Required?</span></span>                            | <span data-ttu-id="28a90-118">False</span><span class="sxs-lookup"><span data-stu-id="28a90-118">false</span></span>                                |
| <span data-ttu-id="28a90-119">Posizione?</span><span class="sxs-lookup"><span data-stu-id="28a90-119">Position?</span></span>                            | <span data-ttu-id="28a90-120">denominato</span><span class="sxs-lookup"><span data-stu-id="28a90-120">named</span></span>                                |
| <span data-ttu-id="28a90-121">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-121">Default Value</span></span>                        | <span data-ttu-id="28a90-122">True</span><span class="sxs-lookup"><span data-stu-id="28a90-122">true</span></span>                                 |
| <span data-ttu-id="28a90-123">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="28a90-123">Accept Pipeline Input?</span></span>               | <span data-ttu-id="28a90-124">False</span><span class="sxs-lookup"><span data-stu-id="28a90-124">false</span></span>                                |
| <span data-ttu-id="28a90-125">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="28a90-125">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="28a90-126">False</span><span class="sxs-lookup"><span data-stu-id="28a90-126">false</span></span>                                |

### <a name="-webapplicationname-ltstringgt"></a><span data-ttu-id="28a90-127">-WebApplicationName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="28a90-127">-WebApplicationName &lt;String&gt;</span></span>

<span data-ttu-id="28a90-128">Specifica il nome dell'applicazione Web da disinstallare.</span><span class="sxs-lookup"><span data-stu-id="28a90-128">Specifies the name of the web application to uninstall.</span></span>

|||  
|-|-|
| <span data-ttu-id="28a90-129">Alias</span><span class="sxs-lookup"><span data-stu-id="28a90-129">Aliases</span></span>                              | <span data-ttu-id="28a90-130">Nessuno</span><span class="sxs-lookup"><span data-stu-id="28a90-130">none</span></span>                                 |
| <span data-ttu-id="28a90-131">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="28a90-131">Required?</span></span>                            | <span data-ttu-id="28a90-132">False</span><span class="sxs-lookup"><span data-stu-id="28a90-132">false</span></span>                                |
| <span data-ttu-id="28a90-133">Posizione?</span><span class="sxs-lookup"><span data-stu-id="28a90-133">Position?</span></span>                            | <span data-ttu-id="28a90-134">1</span><span class="sxs-lookup"><span data-stu-id="28a90-134">1</span></span>                                    |
| <span data-ttu-id="28a90-135">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-135">Default Value</span></span>                        | <span data-ttu-id="28a90-136">pswa</span><span class="sxs-lookup"><span data-stu-id="28a90-136">pswa</span></span>                                 |
| <span data-ttu-id="28a90-137">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="28a90-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="28a90-138">False</span><span class="sxs-lookup"><span data-stu-id="28a90-138">false</span></span>                                |
| <span data-ttu-id="28a90-139">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="28a90-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="28a90-140">False</span><span class="sxs-lookup"><span data-stu-id="28a90-140">false</span></span>                                |

### <a name="-websitename-ltstringgt"></a><span data-ttu-id="28a90-141">-WebSiteName &lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="28a90-141">-WebSiteName &lt;String&gt;</span></span>

<span data-ttu-id="28a90-142">Specifica il nome del sito Web in cui è installata l'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="28a90-142">Specifies the name of the web site where the web application is installed.</span></span>

|||  
|-|-|
| <span data-ttu-id="28a90-143">Alias</span><span class="sxs-lookup"><span data-stu-id="28a90-143">Aliases</span></span>                              | <span data-ttu-id="28a90-144">Nessuno</span><span class="sxs-lookup"><span data-stu-id="28a90-144">none</span></span>                                 |
| <span data-ttu-id="28a90-145">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="28a90-145">Required?</span></span>                            | <span data-ttu-id="28a90-146">False</span><span class="sxs-lookup"><span data-stu-id="28a90-146">false</span></span>                                |
| <span data-ttu-id="28a90-147">Posizione?</span><span class="sxs-lookup"><span data-stu-id="28a90-147">Position?</span></span>                            | <span data-ttu-id="28a90-148">denominato</span><span class="sxs-lookup"><span data-stu-id="28a90-148">named</span></span>                                |
| <span data-ttu-id="28a90-149">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-149">Default Value</span></span>                        | <span data-ttu-id="28a90-150">Sito Web predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-150">Default Web Site</span></span>                     |
| <span data-ttu-id="28a90-151">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="28a90-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="28a90-152">False</span><span class="sxs-lookup"><span data-stu-id="28a90-152">false</span></span>                                |
| <span data-ttu-id="28a90-153">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="28a90-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="28a90-154">False</span><span class="sxs-lookup"><span data-stu-id="28a90-154">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="28a90-155">-Confirm</span><span class="sxs-lookup"><span data-stu-id="28a90-155">-Confirm</span></span>

<span data-ttu-id="28a90-156">Richiede conferma prima di eseguire il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28a90-156">Prompts you for confirmation before running the cmdlet.</span></span>

|||  
|-|-|
| <span data-ttu-id="28a90-157">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="28a90-157">Required?</span></span>                            | <span data-ttu-id="28a90-158">False</span><span class="sxs-lookup"><span data-stu-id="28a90-158">false</span></span>                                |
| <span data-ttu-id="28a90-159">Posizione?</span><span class="sxs-lookup"><span data-stu-id="28a90-159">Position?</span></span>                            | <span data-ttu-id="28a90-160">denominato</span><span class="sxs-lookup"><span data-stu-id="28a90-160">named</span></span>                                |
| <span data-ttu-id="28a90-161">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-161">Default Value</span></span>                        | <span data-ttu-id="28a90-162">False</span><span class="sxs-lookup"><span data-stu-id="28a90-162">false</span></span>                                |
| <span data-ttu-id="28a90-163">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="28a90-163">Accept Pipeline Input?</span></span>               | <span data-ttu-id="28a90-164">False</span><span class="sxs-lookup"><span data-stu-id="28a90-164">false</span></span>                                |
| <span data-ttu-id="28a90-165">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="28a90-165">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="28a90-166">False</span><span class="sxs-lookup"><span data-stu-id="28a90-166">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="28a90-167">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="28a90-167">-WhatIf</span></span>

<span data-ttu-id="28a90-168">Mostra gli effetti dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="28a90-168">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="28a90-169">Il cmdlet non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="28a90-169">The cmdlet is not run.</span></span>

|||  
|-|-|
| <span data-ttu-id="28a90-170">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="28a90-170">Required?</span></span>                            | <span data-ttu-id="28a90-171">False</span><span class="sxs-lookup"><span data-stu-id="28a90-171">false</span></span>                                |
| <span data-ttu-id="28a90-172">Posizione?</span><span class="sxs-lookup"><span data-stu-id="28a90-172">Position?</span></span>                            | <span data-ttu-id="28a90-173">denominato</span><span class="sxs-lookup"><span data-stu-id="28a90-173">named</span></span>                                |
| <span data-ttu-id="28a90-174">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="28a90-174">Default Value</span></span>                        | <span data-ttu-id="28a90-175">False</span><span class="sxs-lookup"><span data-stu-id="28a90-175">false</span></span>                                |
| <span data-ttu-id="28a90-176">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="28a90-176">Accept Pipeline Input?</span></span>               | <span data-ttu-id="28a90-177">False</span><span class="sxs-lookup"><span data-stu-id="28a90-177">false</span></span>                                |
| <span data-ttu-id="28a90-178">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="28a90-178">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="28a90-179">False</span><span class="sxs-lookup"><span data-stu-id="28a90-179">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="28a90-180">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="28a90-180">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="28a90-181">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="28a90-181">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="28a90-182">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="28a90-182">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="28a90-183">INPUT</span><span class="sxs-lookup"><span data-stu-id="28a90-183">INPUTS</span></span>

<span data-ttu-id="28a90-184">Questo cmdlet non accetta input.</span><span class="sxs-lookup"><span data-stu-id="28a90-184">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="28a90-185">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="28a90-185">OUTPUTS</span></span>

<span data-ttu-id="28a90-186">Questo cmdlet non restituisce output.</span><span class="sxs-lookup"><span data-stu-id="28a90-186">This cmdlet returns no output.</span></span>

## <a name="examples"></a><span data-ttu-id="28a90-187">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="28a90-187">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="28a90-188">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="28a90-188">EXAMPLE 1</span></span>

<span data-ttu-id="28a90-189">Questo comando disinstalla l'applicazione Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="28a90-189">This command uninstalls the Windows PowerShell Web Application.</span></span>
<span data-ttu-id="28a90-190">È possibile usare questo cmdlet per disinstallare l'applicazione Web Windows PowerShell se è stata installata usando i valori predefiniti.</span><span class="sxs-lookup"><span data-stu-id="28a90-190">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values.</span></span>

```PowerShell
Uninstall-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="28a90-191">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="28a90-191">EXAMPLE 2</span></span>

<span data-ttu-id="28a90-192">Questo comando disinstalla l'applicazione Web Windows PowerShell ed elimina il certificato di test associato all'applicazione.</span><span class="sxs-lookup"><span data-stu-id="28a90-192">This command uninstalls the Windows PowerShell Web Application, and deletes the test certificate associated with the application.</span></span>
<span data-ttu-id="28a90-193">È possibile usare questo cmdlet per disinstallare l'applicazione Web Windows PowerShell se è stata installata usando i valori predefiniti e se è stato creato un certificato di test.</span><span class="sxs-lookup"><span data-stu-id="28a90-193">You can use this cmdlet to uninstall the Windows PowerShell Web Application if you installed it using the default values and created a test certificate.</span></span>

```PowerShell
Uninstall-PswaWebApplication -DeleteTestCertificate
```

### <a name="example-3-example-3-subheading"></a><span data-ttu-id="28a90-194">ESEMPIO 3 {#example-3 .subHeading}</span><span class="sxs-lookup"><span data-stu-id="28a90-194">EXAMPLE 3 {#example-3 .subHeading}</span></span>

<span data-ttu-id="28a90-195">Questo comando disinstalla l'applicazione Web Windows PowerShell quando si specifica un sito Web personalizzato con la relativa applicazione durante l'installazione.</span><span class="sxs-lookup"><span data-stu-id="28a90-195">This command uninstalls the Windows PowerShell Web Application when a custom website and application were specified during the install.</span></span>
<span data-ttu-id="28a90-196">Il comando rimuove il sito Web denominato *MySite* e l'applicazione denominata *TestApplication* e specifica che anche i certificati di test associati all'applicazione vengono eliminati.</span><span class="sxs-lookup"><span data-stu-id="28a90-196">The command removes the website named *MySite* and the application named *TestApplication* and specifies that the test certificates associated with the application are also deleted.</span></span>

```
Uninstall-PswaWebApplication -WebApplicationName TestApplication -WebsiteName MySite -DeleteTestCertificate
```

##  <a name="related-topics"></a><span data-ttu-id="28a90-197">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="28a90-197">Related topics</span></span>

-  [<span data-ttu-id="28a90-198">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="28a90-198">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
-  [<span data-ttu-id="28a90-199">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="28a90-199">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
-  [<span data-ttu-id="28a90-200">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="28a90-200">Install-PswaWebApplication</span></span>](install-pswawebapplication.md)
-  [<span data-ttu-id="28a90-201">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="28a90-201">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
-  [<span data-ttu-id="28a90-202">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="28a90-202">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)
