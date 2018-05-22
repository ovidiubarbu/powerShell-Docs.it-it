---
ms.topic: reference
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: Install-PswaWebApplication
ms.openlocfilehash: 68455d9490f7d5c33c1a928ac262a76a78ad7128
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
---
# <a name="install-pswawebapplication"></a><span data-ttu-id="ae63a-103">Install-PswaWebApplication</span><span class="sxs-lookup"><span data-stu-id="ae63a-103">Install-PswaWebApplication</span></span>

## <a name="synopsis"></a><span data-ttu-id="ae63a-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="ae63a-104">SYNOPSIS</span></span>

<span data-ttu-id="ae63a-105">Configura l'applicazione Web Accesso Web Windows PowerShell® in IIS.</span><span class="sxs-lookup"><span data-stu-id="ae63a-105">Configures the Windows PowerShell® Web Access web application in IIS.</span></span>

## <a name="syntax"></a><span data-ttu-id="ae63a-106">SINTASSI</span><span class="sxs-lookup"><span data-stu-id="ae63a-106">SYNTAX</span></span>

### <a name="default"></a><span data-ttu-id="ae63a-107">Default</span><span class="sxs-lookup"><span data-stu-id="ae63a-107">Default</span></span>
```
Install-PswaWebApplication [[-WebApplicationName] <String> ] [-UseTestCertificate] [-WebSiteName <String> ] [-Confirm] [-WhatIf] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="ae63a-108">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="ae63a-108">DESCRIPTION</span></span>

<span data-ttu-id="ae63a-109">Il cmdlet **Install-PswaWebApplication** consente di configurare l'applicazione Web Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae63a-109">The **Install-PswaWebApplication** cmdlet configures Windows PowerShell Web Access web application.</span></span> <span data-ttu-id="ae63a-110">Questo cmdlet installa l'applicazione Web, la associa a un sito Web e, se necessario, crea un certificato SSL di test usando il parametro **useTestCertificate**.</span><span class="sxs-lookup"><span data-stu-id="ae63a-110">This cmdlet installs the web application, associates it with a web site, and optionally creates a test SSL certificate using the **useTestCertificate** parameter.</span></span> <span data-ttu-id="ae63a-111">Per motivi di sicurezza, gli amministratori Web non devono usare un certificato di test per gli ambienti di produzione.</span><span class="sxs-lookup"><span data-stu-id="ae63a-111">For security reasons web administrators should not use a test certificate for production environments.</span></span>

## <a name="parameters"></a><span data-ttu-id="ae63a-112">PARAMETRI</span><span class="sxs-lookup"><span data-stu-id="ae63a-112">PARAMETERS</span></span>

### <a name="-usetestcertificate"></a><span data-ttu-id="ae63a-113">-UseTestCertificate</span><span class="sxs-lookup"><span data-stu-id="ae63a-113">-UseTestCertificate</span></span>

<span data-ttu-id="ae63a-114">Specifica che viene creato un certificato di test.</span><span class="sxs-lookup"><span data-stu-id="ae63a-114">Specifies that a test certificate is created.</span></span> <span data-ttu-id="ae63a-115">Se questo parametro è impostato su true, il cmdlet crea un certificato di test e configura l'applicazione Web Accesso Web Windows PowerShell in modo che usi il certificato per le richieste HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ae63a-115">If this parameter is set to true, then this cmdlet creates a test certificate and configures the Windows PowerShell Web Access web application to use the certificate for HTTPS requests.</span></span> <span data-ttu-id="ae63a-116">Se questo parametro è impostato su false, non viene creato alcun certificato o binding.</span><span class="sxs-lookup"><span data-stu-id="ae63a-116">If this parameter is set to false, then no certificate or binding is created.</span></span> <span data-ttu-id="ae63a-117">Impostare questo valore su false se si usa un altro certificato per Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae63a-117">Set this value to false if another certificate is used for Windows PowerShell Web Access.</span></span>

|||
|-|-|
| <span data-ttu-id="ae63a-118">Alias</span><span class="sxs-lookup"><span data-stu-id="ae63a-118">Aliases</span></span>                              | <span data-ttu-id="ae63a-119">Nessuno</span><span class="sxs-lookup"><span data-stu-id="ae63a-119">none</span></span>                                 |
| <span data-ttu-id="ae63a-120">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="ae63a-120">Required?</span></span>                            | <span data-ttu-id="ae63a-121">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-121">false</span></span>                                |
| <span data-ttu-id="ae63a-122">Posizione?</span><span class="sxs-lookup"><span data-stu-id="ae63a-122">Position?</span></span>                            | <span data-ttu-id="ae63a-123">denominato</span><span class="sxs-lookup"><span data-stu-id="ae63a-123">named</span></span>                                |
| <span data-ttu-id="ae63a-124">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-124">Default Value</span></span>                        | <span data-ttu-id="ae63a-125">True</span><span class="sxs-lookup"><span data-stu-id="ae63a-125">true</span></span>                                 |
| <span data-ttu-id="ae63a-126">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="ae63a-126">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ae63a-127">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-127">false</span></span>                                |
| <span data-ttu-id="ae63a-128">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="ae63a-128">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ae63a-129">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-129">false</span></span>                                |

### <a name="-webapplicationnameltstringgt"></a><span data-ttu-id="ae63a-130">-WebApplicationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ae63a-130">-WebApplicationName&lt;String&gt;</span></span>

<span data-ttu-id="ae63a-131">Specifica il nome per l'applicazione Web.</span><span class="sxs-lookup"><span data-stu-id="ae63a-131">Specifies the name for your web application.</span></span> <span data-ttu-id="ae63a-132">Il nome viene visualizzato come parte finale dell'URL di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae63a-132">This is displayed as the last part of the Windows PowerShell Web Access URL.</span></span>

|||
|-|-|
| <span data-ttu-id="ae63a-133">Alias</span><span class="sxs-lookup"><span data-stu-id="ae63a-133">Aliases</span></span>                              | <span data-ttu-id="ae63a-134">Nessuno</span><span class="sxs-lookup"><span data-stu-id="ae63a-134">none</span></span>                                 |
| <span data-ttu-id="ae63a-135">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="ae63a-135">Required?</span></span>                            | <span data-ttu-id="ae63a-136">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-136">false</span></span>                                |
| <span data-ttu-id="ae63a-137">Posizione?</span><span class="sxs-lookup"><span data-stu-id="ae63a-137">Position?</span></span>                            | <span data-ttu-id="ae63a-138">1</span><span class="sxs-lookup"><span data-stu-id="ae63a-138">1</span></span>                                    |
| <span data-ttu-id="ae63a-139">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-139">Default Value</span></span>                        | <span data-ttu-id="ae63a-140">pswa</span><span class="sxs-lookup"><span data-stu-id="ae63a-140">pswa</span></span>                                 |
| <span data-ttu-id="ae63a-141">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="ae63a-141">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ae63a-142">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-142">false</span></span>                                |
| <span data-ttu-id="ae63a-143">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="ae63a-143">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ae63a-144">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-144">false</span></span>                                |

### <a name="-websitenameltstringgt"></a><span data-ttu-id="ae63a-145">-WebSiteName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="ae63a-145">-WebSiteName&lt;String&gt;</span></span>

<span data-ttu-id="ae63a-146">Specifica il nome del sito Web del server Web (IIS) in cui installare l'applicazione Web Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ae63a-146">Specifies the name of the Web Server (IIS) website on which to install this Windows PowerShell Web Access web application.</span></span>

|||
|-|-|
| <span data-ttu-id="ae63a-147">Alias</span><span class="sxs-lookup"><span data-stu-id="ae63a-147">Aliases</span></span>                              | <span data-ttu-id="ae63a-148">Nessuno</span><span class="sxs-lookup"><span data-stu-id="ae63a-148">none</span></span>                                 |
| <span data-ttu-id="ae63a-149">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="ae63a-149">Required?</span></span>                            | <span data-ttu-id="ae63a-150">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-150">false</span></span>                                |
| <span data-ttu-id="ae63a-151">Posizione?</span><span class="sxs-lookup"><span data-stu-id="ae63a-151">Position?</span></span>                            | <span data-ttu-id="ae63a-152">denominato</span><span class="sxs-lookup"><span data-stu-id="ae63a-152">named</span></span>                                |
| <span data-ttu-id="ae63a-153">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-153">Default Value</span></span>                        | <span data-ttu-id="ae63a-154">Sito Web predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-154">Default Web Site</span></span>                     |
| <span data-ttu-id="ae63a-155">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="ae63a-155">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ae63a-156">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-156">false</span></span>                                |
| <span data-ttu-id="ae63a-157">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="ae63a-157">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ae63a-158">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-158">false</span></span>                                |

### <a name="-confirm"></a><span data-ttu-id="ae63a-159">-Confirm</span><span class="sxs-lookup"><span data-stu-id="ae63a-159">-Confirm</span></span>

<span data-ttu-id="ae63a-160">Richiede conferma prima di eseguire il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae63a-160">Prompts you for confirmation before running the cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="ae63a-161">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="ae63a-161">Required?</span></span>                            | <span data-ttu-id="ae63a-162">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-162">false</span></span>                                |
| <span data-ttu-id="ae63a-163">Posizione?</span><span class="sxs-lookup"><span data-stu-id="ae63a-163">Position?</span></span>                            | <span data-ttu-id="ae63a-164">denominato</span><span class="sxs-lookup"><span data-stu-id="ae63a-164">named</span></span>                                |
| <span data-ttu-id="ae63a-165">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-165">Default Value</span></span>                        | <span data-ttu-id="ae63a-166">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-166">false</span></span>                                |
| <span data-ttu-id="ae63a-167">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="ae63a-167">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ae63a-168">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-168">false</span></span>                                |
| <span data-ttu-id="ae63a-169">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="ae63a-169">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ae63a-170">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-170">false</span></span>                                |

### <a name="-whatif"></a><span data-ttu-id="ae63a-171">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="ae63a-171">-WhatIf</span></span>

<span data-ttu-id="ae63a-172">Mostra gli effetti dell'esecuzione del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ae63a-172">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="ae63a-173">Il cmdlet non viene eseguito.</span><span class="sxs-lookup"><span data-stu-id="ae63a-173">The cmdlet is not run.</span></span>

|||
|-|-|
| <span data-ttu-id="ae63a-174">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="ae63a-174">Required?</span></span>                            | <span data-ttu-id="ae63a-175">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-175">false</span></span>                                |
| <span data-ttu-id="ae63a-176">Posizione?</span><span class="sxs-lookup"><span data-stu-id="ae63a-176">Position?</span></span>                            | <span data-ttu-id="ae63a-177">denominato</span><span class="sxs-lookup"><span data-stu-id="ae63a-177">named</span></span>                                |
| <span data-ttu-id="ae63a-178">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="ae63a-178">Default Value</span></span>                        | <span data-ttu-id="ae63a-179">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-179">false</span></span>                                |
| <span data-ttu-id="ae63a-180">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="ae63a-180">Accept Pipeline Input?</span></span>               | <span data-ttu-id="ae63a-181">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-181">false</span></span>                                |
| <span data-ttu-id="ae63a-182">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="ae63a-182">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="ae63a-183">False</span><span class="sxs-lookup"><span data-stu-id="ae63a-183">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="ae63a-184">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="ae63a-184">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="ae63a-185">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="ae63a-185">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="ae63a-186">Per altre informazioni, vedere [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="ae63a-186">For more information, see [about_CommonParameters](http://go.microsoft.com/fwlink/p/?LinkID=113216).</span></span>

## <a name="inputs"></a><span data-ttu-id="ae63a-187">INPUT</span><span class="sxs-lookup"><span data-stu-id="ae63a-187">INPUTS</span></span>

<span data-ttu-id="ae63a-188">Questo cmdlet non accetta input.</span><span class="sxs-lookup"><span data-stu-id="ae63a-188">This cmdlet takes no input.</span></span>

## <a name="outputs"></a><span data-ttu-id="ae63a-189">OUTPUT</span><span class="sxs-lookup"><span data-stu-id="ae63a-189">OUTPUTS</span></span>

<span data-ttu-id="ae63a-190">Questo cmdlet non genera alcun output.</span><span class="sxs-lookup"><span data-stu-id="ae63a-190">This cmdlet produces no output.</span></span>

## <a name="examples"></a><span data-ttu-id="ae63a-191">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="ae63a-191">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="ae63a-192">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="ae63a-192">EXAMPLE 1</span></span>

<span data-ttu-id="ae63a-193">In questo esempio si installa l'applicazione Web PSWA usando i valori predefiniti per i parametri **WebApplicationName** (*pswa*) e **WebSiteName** (*sito Web predefinito*).</span><span class="sxs-lookup"><span data-stu-id="ae63a-193">This example installs the PSWA web application using the default values for the **WebApplicationName** (*pswa*) and **WebSiteName** (*Default Web Site*) parameters .</span></span>

```
Install-PswaWebApplication
```

### <a name="example-2"></a><span data-ttu-id="ae63a-194">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="ae63a-194">EXAMPLE 2</span></span>

<span data-ttu-id="ae63a-195">In questo esempio viene installata l'applicazione Web PSWA con un certificato di test, usando i valori predefiniti per i parametri **WebApplicationName** e **WebSiteName**.</span><span class="sxs-lookup"><span data-stu-id="ae63a-195">This example installs the PSWA web application with a test certificate, and using the default values for the **WebApplicationName** and **WebSiteName** parameters.</span></span>

```
Install-PswaWebApplication -UseTestCertificate
```

## <a name="related-topics"></a><span data-ttu-id="ae63a-196">Argomenti correlati</span><span class="sxs-lookup"><span data-stu-id="ae63a-196">Related topics</span></span>

- [<span data-ttu-id="ae63a-197">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ae63a-197">Add-PswaAuthorizationRule</span></span>](add-pswaauthorizationrule.md)
- [<span data-ttu-id="ae63a-198">Get-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ae63a-198">Get-PswaAuthorizationRule</span></span>](get-pswaauthorizationrule.md)
- [<span data-ttu-id="ae63a-199">Remove-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ae63a-199">Remove-PswaAuthorizationRule</span></span>](remove-pswaauthorizationrule.md)
- [<span data-ttu-id="ae63a-200">Test-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="ae63a-200">Test-PswaAuthorizationRule</span></span>](test-pswaauthorizationrule.md)