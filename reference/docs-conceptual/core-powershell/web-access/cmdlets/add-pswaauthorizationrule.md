---
description: ''
ms.topic: article
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 12/12/2016
title: add pswaauthorizationrule
ms.technology: powershell
schema: 2.0.0
ms.openlocfilehash: 07ddd4df6a776f3ef6763242f8682747b9b97061
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="add-pswaauthorizationrule"></a><span data-ttu-id="0077f-103">Add-PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0077f-103">Add-PswaAuthorizationRule</span></span>

## <a name="synopsis"></a><span data-ttu-id="0077f-104">RIEPILOGO</span><span class="sxs-lookup"><span data-stu-id="0077f-104">SYNOPSIS</span></span>

<span data-ttu-id="0077f-105">Aggiunge una nuova regola di autorizzazione al set di regole di autorizzazione di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0077f-105">Adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

## <a name="syntax"></a><span data-ttu-id="0077f-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="0077f-106">Syntax</span></span>

### <a name="usergroupnamecomputergroupname"></a><span data-ttu-id="0077f-107">UserGroupNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0077f-107">UserGroupNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule -ComputerGroupName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usergroupnamecomputername"></a><span data-ttu-id="0077f-108">UserGroupNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0077f-108">UserGroupNameComputerName</span></span>
```
Add-PswaAuthorizationRule -ComputerName <String> -ConfigurationName <String> -UserGroupName <String[]> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputergroupname"></a><span data-ttu-id="0077f-109">UserNameComputerGroupName</span><span class="sxs-lookup"><span data-stu-id="0077f-109">UserNameComputerGroupName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> -ComputerGroupName <String> -ConfigurationName <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

### <a name="usernamecomputername"></a><span data-ttu-id="0077f-110">UserNameComputerName</span><span class="sxs-lookup"><span data-stu-id="0077f-110">UserNameComputerName</span></span>
```
Add-PswaAuthorizationRule [-UserName] <String[]> [-ComputerName] <String> [-ConfigurationName] <String> [-Credential <PSCredential> ] [-Force] [-RuleName <String> ] [ <CommonParameters>]
```

## <a name="description"></a><span data-ttu-id="0077f-111">DESCRIZIONE</span><span class="sxs-lookup"><span data-stu-id="0077f-111">DESCRIPTION</span></span>

<span data-ttu-id="0077f-112">Il cmdlet **Add-PswaAuthorizationRule** aggiunge una nuova regola di autorizzazione al set di regole di autorizzazione di Accesso Web Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="0077f-112">The **Add-PswaAuthorizationRule** cmdlet adds a new authorization rule to the Windows PowerShell® Web Access authorization rule set.</span></span>

<span data-ttu-id="0077f-113">È necessario specificare gli utenti, i computer e gli endpoint di Windows PowerShell per questa regola.</span><span class="sxs-lookup"><span data-stu-id="0077f-113">You must specify the users, computers, and Windows PowerShell endpoints for this rule.</span></span> <span data-ttu-id="0077f-114">È possibile specificare utenti e computer sia indicando singoli account utente e nomi di computer, sia specificando i gruppi.</span><span class="sxs-lookup"><span data-stu-id="0077f-114">You can specify both users and computers either by individual user accounts and computer names, or by specifying groups.</span></span>

<span data-ttu-id="0077f-115">Per un computer appartenente a un dominio Active Directory, il cmdlet usa l'ID di sicurezza (SID) del computer per creare la regola.</span><span class="sxs-lookup"><span data-stu-id="0077f-115">For a computer that is joined to an Active Directory domain, the cmdlet uses the security identifier (SID) of the computer to create the rule.</span></span>
<span data-ttu-id="0077f-116">Ciò consente di usare un nome breve, un nome di dominio completo (FQDN) o un indirizzo IP per il campo **Nome computer** della pagina di accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-116">This allows you to use a short name, a fully qualified domain name (FQDN), or an IP address for the **Computer Name** field on the sign-in page.</span></span>

<span data-ttu-id="0077f-117">Per un computer che non appartiene a un dominio Active Directory, il cmdlet crea la regola usando il nome di computer indicato dall'amministratore.</span><span class="sxs-lookup"><span data-stu-id="0077f-117">For a computer that is not joined to an Active Directory domain, the cmdlet creates the rule using the computer name provided by the administrator.</span></span> <span data-ttu-id="0077f-118">Per connettersi correttamente a questo computer, l'utente finale deve indicare il nome del computer esattamente come appare nella regola.</span><span class="sxs-lookup"><span data-stu-id="0077f-118">To successfully connect to this machine, the end user must provide the computer name exactly as it appears in the rule.</span></span>

<span data-ttu-id="0077f-119">Se nella rete sono presenti più computer con lo stesso nome, il nome breve può restituire più di un computer.</span><span class="sxs-lookup"><span data-stu-id="0077f-119">If there are multiple computers with the same name on the network, then short name can resolve to more than one computer.</span></span> <span data-ttu-id="0077f-120">Questo può causare ambiguità quando si stabilisce una connessione.</span><span class="sxs-lookup"><span data-stu-id="0077f-120">This can lead to ambiguity when establishing a connection.</span></span> <span data-ttu-id="0077f-121">Ad esempio, se esiste una regola per il computer del gruppo di lavoro denominato "*Server1*" e un nuovo computer denominato *server1.contoso.com* viene aggiunto alla rete, la convalida eseguita con le regole di autorizzazione ha esito positivo e Accesso Web Windows PowerShell tenta di stabilire una connessione al computer "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="0077f-121">For example, if a rule exists for the workgroup computer named "*Server1*” and a new computer named *server1.contoso.com* is joined to the network, validation using the authorization rules succeeds and Windows PowerShell Web Access attempts to establish a connection to the computer named “*Server1*”.</span></span> <span data-ttu-id="0077f-122">Non è garantito che la connessione venga stabilita con il computer del gruppo di lavoro specificato. Il tentativo può essere effettuato per il gruppo di lavoro o il computer del dominio denominato "*Server1*".</span><span class="sxs-lookup"><span data-stu-id="0077f-122">It is not guaranteed that the connection is established with the specified workgroup computer; the attempt could be made on either the workgroup or the domain computer named "*Server1*".</span></span> <span data-ttu-id="0077f-123">Per ridurre l'ambiguità, è consigliabile usare il nome FQDN del computer di destinazione ogni volta che è possibile per creare una regola di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0077f-123">To reduce ambiguity, it is recommended that you use the FQDN for the destination computer whenever possible to create an authorization rule.</span></span>

<span data-ttu-id="0077f-124">Le regole di autorizzazione verificano le credenziali di accesso primarie degli utenti di Accesso Web Windows PowerShell, non le credenziali alternative, ovvero il secondo set di credenziali indicato nella sezione **Impostazioni di connessione facoltative** della pagina di accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-124">The authorization rules evaluate the primary sign-in credential of the Windows PowerShell Web Access users, not the alternate credentials (the second set of credentials found in the **Optional connection settings** section of the sign-in page).</span></span> <span data-ttu-id="0077f-125">Per un esempio, vedere l'esempio 6.</span><span class="sxs-lookup"><span data-stu-id="0077f-125">For an example of this, see Example 6.</span></span>

## <a name="parameters"></a><span data-ttu-id="0077f-126">Parametri</span><span class="sxs-lookup"><span data-stu-id="0077f-126">Parameters</span></span>

### <a name="-computergroupnameltstringgt"></a><span data-ttu-id="0077f-127">-ComputerGroupName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-127">-ComputerGroupName&lt;String&gt;</span></span>

<span data-ttu-id="0077f-128">Specifica il nome di un gruppo di computer in Active Directory Domain Services (AD DS) o i gruppi locali a cui la regola concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-128">Specifies the name of a computer group in Active Directory Domain Services (AD DS) or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-129">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-129">Aliases</span></span>                              | <span data-ttu-id="0077f-130">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-130">none</span></span>                                 |
| <span data-ttu-id="0077f-131">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-131">Required?</span></span>                            | <span data-ttu-id="0077f-132">True</span><span class="sxs-lookup"><span data-stu-id="0077f-132">true</span></span>                                 |
| <span data-ttu-id="0077f-133">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-133">Position?</span></span>                            | <span data-ttu-id="0077f-134">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-134">named</span></span>                                |
| <span data-ttu-id="0077f-135">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-135">Default Value</span></span>                        | <span data-ttu-id="0077f-136">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-136">none</span></span>                                 |
| <span data-ttu-id="0077f-137">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-137">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-138">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-138">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0077f-139">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-139">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-140">False</span><span class="sxs-lookup"><span data-stu-id="0077f-140">false</span></span>                                |

### <a name="-computernameltstringgt"></a><span data-ttu-id="0077f-141">-ComputerName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-141">-ComputerName&lt;String&gt;</span></span>

<span data-ttu-id="0077f-142">Specifica il nome del computer a cui la regola concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-142">Specifies the computer name to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-143">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-143">Aliases</span></span>                              | <span data-ttu-id="0077f-144">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-144">none</span></span>                                 |
| <span data-ttu-id="0077f-145">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-145">Required?</span></span>                            | <span data-ttu-id="0077f-146">True</span><span class="sxs-lookup"><span data-stu-id="0077f-146">true</span></span>                                 |
| <span data-ttu-id="0077f-147">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-147">Position?</span></span>                            | <span data-ttu-id="0077f-148">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-148">named</span></span>                                |
| <span data-ttu-id="0077f-149">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-149">Default Value</span></span>                        | <span data-ttu-id="0077f-150">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-150">none</span></span>                                 |
| <span data-ttu-id="0077f-151">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-151">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-152">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-152">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0077f-153">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-153">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-154">False</span><span class="sxs-lookup"><span data-stu-id="0077f-154">false</span></span>                                |

### <a name="-configurationnameltstringgt"></a><span data-ttu-id="0077f-155">-ConfigurationName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-155">-ConfigurationName&lt;String&gt;</span></span>

<span data-ttu-id="0077f-156">Specifica il nome della configurazione di sessione di Windows PowerShell, nota anche come spazio di esecuzione, a cui la regola concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-156">Specifies the name of the Windows PowerShell session configuration, also known as runspace, to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-157">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-157">Aliases</span></span>                              | <span data-ttu-id="0077f-158">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-158">none</span></span>                                 |
| <span data-ttu-id="0077f-159">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-159">Required?</span></span>                            | <span data-ttu-id="0077f-160">True</span><span class="sxs-lookup"><span data-stu-id="0077f-160">true</span></span>                                 |
| <span data-ttu-id="0077f-161">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-161">Position?</span></span>                            | <span data-ttu-id="0077f-162">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-162">named</span></span>                                |
| <span data-ttu-id="0077f-163">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-163">Default Value</span></span>                        | <span data-ttu-id="0077f-164">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-164">none</span></span>                                 |
| <span data-ttu-id="0077f-165">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-165">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-166">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-166">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0077f-167">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-167">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-168">False</span><span class="sxs-lookup"><span data-stu-id="0077f-168">false</span></span>                                |

### <a name="-credentialltpscredentialgt"></a><span data-ttu-id="0077f-169">-Credential&lt;PSCredential&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-169">-Credential&lt;PSCredential&gt;</span></span>

<span data-ttu-id="0077f-170">Specifica un oggetto **PSCredential** per un account utente che verrà usato per modificare le regole di autorizzazione di Accesso Web Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="0077f-170">Specifies a **PSCredential** object for a user account that you want to use to change Windows PowerShell Web Access authorization rules.</span></span> <span data-ttu-id="0077f-171">Se non si aggiunge questo parametro, il cmdlet usa l'account utente attualmente connesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-171">If you do not add this parameter, the cmdlet uses the currently logged-on user account.</span></span> <span data-ttu-id="0077f-172">Per ottenere un oggetto **PSCredential**, necessario per aggiungere le regole di autorizzazione in modalità remota, eseguire il cmdlet [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential).</span><span class="sxs-lookup"><span data-stu-id="0077f-172">To get a **PSCredential** object, which is required to add authorization rules remotely, run the [Get-Credential](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.security/Get-Credential) cmdlet.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-173">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-173">Aliases</span></span>                              | <span data-ttu-id="0077f-174">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-174">none</span></span>                                 |
| <span data-ttu-id="0077f-175">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-175">Required?</span></span>                            | <span data-ttu-id="0077f-176">False</span><span class="sxs-lookup"><span data-stu-id="0077f-176">false</span></span>                                |
| <span data-ttu-id="0077f-177">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-177">Position?</span></span>                            | <span data-ttu-id="0077f-178">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-178">named</span></span>                                |
| <span data-ttu-id="0077f-179">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-179">Default Value</span></span>                        | <span data-ttu-id="0077f-180">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-180">none</span></span>                                 |
| <span data-ttu-id="0077f-181">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-181">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-182">False</span><span class="sxs-lookup"><span data-stu-id="0077f-182">false</span></span>                                |
| <span data-ttu-id="0077f-183">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-183">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-184">False</span><span class="sxs-lookup"><span data-stu-id="0077f-184">false</span></span>                                |

### <a name="-force"></a><span data-ttu-id="0077f-185">-Force</span><span class="sxs-lookup"><span data-stu-id="0077f-185">-Force</span></span>

<span data-ttu-id="0077f-186">Forza l'esecuzione del comando senza chiedere conferma all'utente.\\</span><span class="sxs-lookup"><span data-stu-id="0077f-186">Forces the command to run without asking for user confirmation.\\</span></span>
<span data-ttu-id="0077f-187">Richiede anche una conferma quando si immette un nome di computer semplice o breve, ad esempio un nome che non è un nome di dominio o non è completo.</span><span class="sxs-lookup"><span data-stu-id="0077f-187">In addition, it also prompts for confirmation when you enter a simple or short computer name (such as a name that is not a domain name or is not fully qualified).</span></span> <span data-ttu-id="0077f-188">La conferma è richiesta per motivi di sicurezza, in modo che sia possibile usare il nome semplice per aggiungere un computer solo se il computer fa parte di un gruppo di lavoro.</span><span class="sxs-lookup"><span data-stu-id="0077f-188">Confirmation is requested for security reasons, so that you can use the simple name to add a computer only if the computer is in a workgroup.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-189">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-189">Aliases</span></span>                              | <span data-ttu-id="0077f-190">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-190">none</span></span>                                 |
| <span data-ttu-id="0077f-191">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-191">Required?</span></span>                            | <span data-ttu-id="0077f-192">False</span><span class="sxs-lookup"><span data-stu-id="0077f-192">false</span></span>                                |
| <span data-ttu-id="0077f-193">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-193">Position?</span></span>                            | <span data-ttu-id="0077f-194">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-194">named</span></span>                                |
| <span data-ttu-id="0077f-195">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-195">Default Value</span></span>                        | <span data-ttu-id="0077f-196">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-196">none</span></span>                                 |
| <span data-ttu-id="0077f-197">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-197">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-198">False</span><span class="sxs-lookup"><span data-stu-id="0077f-198">false</span></span>                                |
| <span data-ttu-id="0077f-199">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-199">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-200">False</span><span class="sxs-lookup"><span data-stu-id="0077f-200">false</span></span>                                |

### <a name="-rulenameltstringgt"></a><span data-ttu-id="0077f-201">-RuleName&lt;String&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-201">-RuleName&lt;String&gt;</span></span>

<span data-ttu-id="0077f-202">Specifica il nome descrittivo per la regola.</span><span class="sxs-lookup"><span data-stu-id="0077f-202">Specifies the friendly name for this rule.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-203">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-203">Aliases</span></span>                              | <span data-ttu-id="0077f-204">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-204">none</span></span>                                 |
| <span data-ttu-id="0077f-205">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-205">Required?</span></span>                            | <span data-ttu-id="0077f-206">False</span><span class="sxs-lookup"><span data-stu-id="0077f-206">false</span></span>                                |
| <span data-ttu-id="0077f-207">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-207">Position?</span></span>                            | <span data-ttu-id="0077f-208">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-208">named</span></span>                                |
| <span data-ttu-id="0077f-209">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-209">Default Value</span></span>                        | <span data-ttu-id="0077f-210">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-210">none</span></span>                                 |
| <span data-ttu-id="0077f-211">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-211">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-212">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-212">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0077f-213">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-213">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-214">False</span><span class="sxs-lookup"><span data-stu-id="0077f-214">false</span></span>                                |

### <a name="-usergroupnameltstringgt"></a><span data-ttu-id="0077f-215">-UserGroupName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-215">-UserGroupName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0077f-216">Specifica il nome di uno o più gruppi di utenti in Active Directory Domain Services (AD DS) o gruppi locali a cui la regola concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-216">Specifies the name of one or more user groups in AD DS or local groups to which this rule grants access.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-217">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-217">Aliases</span></span>                              | <span data-ttu-id="0077f-218">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-218">none</span></span>                                 |
| <span data-ttu-id="0077f-219">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-219">Required?</span></span>                            | <span data-ttu-id="0077f-220">True</span><span class="sxs-lookup"><span data-stu-id="0077f-220">true</span></span>                                 |
| <span data-ttu-id="0077f-221">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-221">Position?</span></span>                            | <span data-ttu-id="0077f-222">denominato</span><span class="sxs-lookup"><span data-stu-id="0077f-222">named</span></span>                                |
| <span data-ttu-id="0077f-223">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-223">Default Value</span></span>                        | <span data-ttu-id="0077f-224">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-224">none</span></span>                                 |
| <span data-ttu-id="0077f-225">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-225">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-226">True (ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-226">True (ByPropertyName)</span></span>                |
| <span data-ttu-id="0077f-227">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-227">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-228">False</span><span class="sxs-lookup"><span data-stu-id="0077f-228">false</span></span>                                |

### <a name="-usernameltstringgt"></a><span data-ttu-id="0077f-229">-UserName&lt;String\[\]&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-229">-UserName&lt;String\[\]&gt;</span></span>

<span data-ttu-id="0077f-230">Specifica uno o più utenti a cui la regola concede l'accesso.</span><span class="sxs-lookup"><span data-stu-id="0077f-230">Specifies one or more users to which this rule grants access.</span></span> <span data-ttu-id="0077f-231">Il nome utente può essere un account utente locale nel computer gateway o un utente di Active Directory Domain Services (AD DS).</span><span class="sxs-lookup"><span data-stu-id="0077f-231">The user name can be a local user account on the gateway computer or a user in AD DS.</span></span>
<span data-ttu-id="0077f-232">Il formato è `domain\user` o `computer\user`.</span><span class="sxs-lookup"><span data-stu-id="0077f-232">The format is `domain\user` or `computer\user`.</span></span>

|||
|-|-|
| <span data-ttu-id="0077f-233">Alias</span><span class="sxs-lookup"><span data-stu-id="0077f-233">Aliases</span></span>                              | <span data-ttu-id="0077f-234">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-234">none</span></span>                                 |
| <span data-ttu-id="0077f-235">Obbligatorio?</span><span class="sxs-lookup"><span data-stu-id="0077f-235">Required?</span></span>                            | <span data-ttu-id="0077f-236">True</span><span class="sxs-lookup"><span data-stu-id="0077f-236">true</span></span>                                 |
| <span data-ttu-id="0077f-237">Posizione?</span><span class="sxs-lookup"><span data-stu-id="0077f-237">Position?</span></span>                            | <span data-ttu-id="0077f-238">1</span><span class="sxs-lookup"><span data-stu-id="0077f-238">1</span></span>                                    |
| <span data-ttu-id="0077f-239">Valore predefinito</span><span class="sxs-lookup"><span data-stu-id="0077f-239">Default Value</span></span>                        | <span data-ttu-id="0077f-240">Nessuno</span><span class="sxs-lookup"><span data-stu-id="0077f-240">none</span></span>                                 |
| <span data-ttu-id="0077f-241">Accetta input da pipeline?</span><span class="sxs-lookup"><span data-stu-id="0077f-241">Accept Pipeline Input?</span></span>               | <span data-ttu-id="0077f-242">True (ByValue, ByPropertyName)</span><span class="sxs-lookup"><span data-stu-id="0077f-242">True (ByValue, ByPropertyName)</span></span>       |
| <span data-ttu-id="0077f-243">Accetta caratteri jolly?</span><span class="sxs-lookup"><span data-stu-id="0077f-243">Accept Wildcard Characters?</span></span>          | <span data-ttu-id="0077f-244">False</span><span class="sxs-lookup"><span data-stu-id="0077f-244">false</span></span>                                |

### <a name="ltcommonparametersgt"></a><span data-ttu-id="0077f-245">&lt;CommonParameters&gt;</span><span class="sxs-lookup"><span data-stu-id="0077f-245">&lt;CommonParameters&gt;</span></span>

<span data-ttu-id="0077f-246">Questo cmdlet supporta i parametri comuni -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer e -OutVariable.</span><span class="sxs-lookup"><span data-stu-id="0077f-246">This cmdlet supports the common parameters: -Verbose, -Debug, -ErrorAction, -ErrorVariable, -OutBuffer, and -OutVariable.</span></span>
<span data-ttu-id="0077f-247">Per altre informazioni, vedere [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span><span class="sxs-lookup"><span data-stu-id="0077f-247">For more information, see [about_CommonParameters](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_commonparameters).</span></span>

## <a name="inputs"></a><span data-ttu-id="0077f-248">INPUT</span><span class="sxs-lookup"><span data-stu-id="0077f-248">INPUTS</span></span>

### <a name="string"></a><span data-ttu-id="0077f-249">String</span><span class="sxs-lookup"><span data-stu-id="0077f-249">String</span></span>

<span data-ttu-id="0077f-250">Questo cmdlet accetta una stringa o una matrice di stringhe come input.</span><span class="sxs-lookup"><span data-stu-id="0077f-250">This cmdlet accepts a string or an array of strings as input.</span></span>

### <a name="string"></a><span data-ttu-id="0077f-251">String\[\]</span><span class="sxs-lookup"><span data-stu-id="0077f-251">String\[\]</span></span>

<span data-ttu-id="0077f-252">Questo cmdlet accetta una stringa o una matrice di stringhe come input.</span><span class="sxs-lookup"><span data-stu-id="0077f-252">This cmdlet accepts a string or an array of strings as input.</span></span>

## <a name="outputs"></a><span data-ttu-id="0077f-253">Output</span><span class="sxs-lookup"><span data-stu-id="0077f-253">Outputs</span></span>

### <a name="microsoftmanagementpowershellwebaccesspswaauthorizationrule"></a><span data-ttu-id="0077f-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span><span class="sxs-lookup"><span data-stu-id="0077f-254">Microsoft.Management.PowerShellWebAccess.PswaAuthorizationRule</span></span>

<span data-ttu-id="0077f-255">Questo cmdlet restituisce un oggetto regola di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="0077f-255">This cmdlet returns the an authorization rule object.</span></span>

## <a name="examples"></a><span data-ttu-id="0077f-256">ESEMPI</span><span class="sxs-lookup"><span data-stu-id="0077f-256">EXAMPLES</span></span>

### <a name="example-1"></a><span data-ttu-id="0077f-257">ESEMPIO 1</span><span class="sxs-lookup"><span data-stu-id="0077f-257">EXAMPLE 1</span></span>

<span data-ttu-id="0077f-258">In questo esempio si concede l'accesso alla configurazione di sessione *PSWAEndpoint*, uno spazio di esecuzione con restrizioni, su *srv2* per gli utenti del gruppo *SMAdmins*. \\</span><span class="sxs-lookup"><span data-stu-id="0077f-258">This example grants access to the session configuration *PSWAEndpoint*, a restricted runspace, on *srv2* for users in the *SMAdmins* group.\\</span></span>
<span data-ttu-id="0077f-259">**Nota**: il nome del computer deve essere un nome di dominio completo (FQDN).</span><span class="sxs-lookup"><span data-stu-id="0077f-259">**Note**: The computer name must be a fully qualified domain name (FQDN).</span></span> <span data-ttu-id="0077f-260">Gli amministratori definiscono una configurazione di sessione o uno spazio di esecuzione con restrizioni, ovvero un intervallo limitato di cmdlet e attività che gli utenti finali possono eseguire.</span><span class="sxs-lookup"><span data-stu-id="0077f-260">Administrators define a restricted session configuration or runspace, which is a limited range of cmdlets and tasks that end users can run.</span></span> <span data-ttu-id="0077f-261">La definizione di uno spazio di esecuzione con restrizioni può impedire agli utenti di accedere ad altri computer che sono nello spazio di esecuzione di Windows PowerShell® consentito, offrendo così una connessione più protetta.</span><span class="sxs-lookup"><span data-stu-id="0077f-261">Defining a restricted runspace can prevent users from accessing other computers that are not in the allowed Windows PowerShell® runspace, thus offering a more secure connection.</span></span> <span data-ttu-id="0077f-262">Per altre informazioni sulle configurazioni di sessione, vedere [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) o [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md) (Installare e usare Accesso Web Windows PowerShell).</span><span class="sxs-lookup"><span data-stu-id="0077f-262">For more information on session configurations, see [about_Session_Configurations](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/about/about_session_configurations) or the [Install and Use Windows PowerShell Web Access](../install-and-use-windows-powershell-web-access.md).</span></span>

```PowerShell
Add-PswaAuthorizationRule -ComputerName srv2.contoso.com -UserGroupName contoso\SMAdmins -ConfigurationName PSWAEndpoint
```

### <a name="example-2"></a><span data-ttu-id="0077f-263">ESEMPIO 2</span><span class="sxs-lookup"><span data-stu-id="0077f-263">EXAMPLE 2</span></span>

<span data-ttu-id="0077f-264">In questo esempio si concede l'accesso alla configurazione di sessione predefinita di Windows PowerShell, `Microsoft.PowerShell`, su *srv2* per gli utenti denominati contoso\\user1, contoso\\user2 e contoso\\user3.</span><span class="sxs-lookup"><span data-stu-id="0077f-264">This example grants access to the default Windows PowerShell session configuration, `Microsoft.PowerShell`, on *srv2* for users in the users named contoso\\user1, contoso\\user2, and contoso\\user3.</span></span> <span data-ttu-id="0077f-265">Questo cmdlet crea tre regole, una per ogni persona.</span><span class="sxs-lookup"><span data-stu-id="0077f-265">This cmdlet creates three rules (1 per person).</span></span>

```PowerShell
Add-PswaAuthorizationRule –UserName contoso\user1, contoso\user2, contoso\user3 –ComputerName srv2.contoso.com -ConfigurationName Microsoft.PowerShell
```

### <a name="example-3"></a><span data-ttu-id="0077f-266">ESEMPIO 3</span><span class="sxs-lookup"><span data-stu-id="0077f-266">EXAMPLE 3</span></span>

<span data-ttu-id="0077f-267">Questo esempio illustra come inserire valori di nome utente usando la pipeline.</span><span class="sxs-lookup"><span data-stu-id="0077f-267">This example illustrates how to input user name values via the pipeline.</span></span>

```
"contoso\user1","contoso\user2" | Add-pswaAuthorizationRule –ComputerName srv2.contoso.com –ConfigurationName Microsoft.PowerShell
```

### <a name="example-4"></a><span data-ttu-id="0077f-268">ESEMPIO 4</span><span class="sxs-lookup"><span data-stu-id="0077f-268">EXAMPLE 4</span></span>

<span data-ttu-id="0077f-269">Questo esempio illustra come tutti i parametri accettano i valori dalla pipeline in base al nome di proprietà.</span><span class="sxs-lookup"><span data-stu-id="0077f-269">This example illustrates how all parameters take values from pipeline by property name.</span></span>

````PowerShell
$o = New-Object -TypeName PSObject |
    Add-Member -Type NoteProperty -Name "UserName" -Value "contoso\user1" -PassThru |
    Add-Member -Type NoteProperty -Name "ComputerName" -Value "srv2.contoso.com" -PassThru |
    Add-Member -Type NoteProperty -Name "ConfigurationName" -Value "Microsoft.PowerShell" –PassThru

$o | Add-PswaAuthorizationRule -UserName contoso\user1 -ConfigurationName Microsoft.PowerShell
````

### <a name="example-5"></a><span data-ttu-id="0077f-270">ESEMPIO 5</span><span class="sxs-lookup"><span data-stu-id="0077f-270">EXAMPLE 5</span></span>

<span data-ttu-id="0077f-271">In questo esempio viene aggiunta una regola per consentire all'utente locale denominato *PswaServer\\ChrisLocal* di accedere al server denominato *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="0077f-271">This example adds a rule to allow the local user named *PswaServer\\ChrisLocal* access to the server named *srv1.contoso.com*.</span></span>

<span data-ttu-id="0077f-272">L'esempio illustra uno scenario in cui il gateway è in un gruppo di lavoro e il computer di destinazione è in un dominio.</span><span class="sxs-lookup"><span data-stu-id="0077f-272">This example illustrates a scenario where the gateway is in a workgroup and the destination computer is in a domain.</span></span> <span data-ttu-id="0077f-273">La regola di autorizzazione si applica per gli utenti locali nel gateway.</span><span class="sxs-lookup"><span data-stu-id="0077f-273">The authorization rule applies to the local users on the gateway.</span></span> <span data-ttu-id="0077f-274">Per eseguire correttamente l'autenticazione, l'utente deve indicare nella pagina di accesso di Accesso Web Windows PowerShell un secondo set di credenziali nell'area **Impostazioni di connessione facoltative**.</span><span class="sxs-lookup"><span data-stu-id="0077f-274">On the Windows PowerShell Web Access sign-in page, to successfully authenticate, the user must provide a second set of credentials in the **Optional connection settings** area.</span></span> <span data-ttu-id="0077f-275">Il server gateway usa il set di credenziali aggiuntivo per autenticare l'utente nel computer di destinazione, il server *srv1.contoso.com*.</span><span class="sxs-lookup"><span data-stu-id="0077f-275">The gateway server uses the additional set of credentials to authenticate the user on the destination computer, a server named *srv1.contoso.com*.</span></span>

````
Add-PswaAuthorizationRule –UserName PswaServer\ChrisLocal –ComputerName srv1.contoso.com –ConfigurationName Microsoft.PowerShell
````

### <a name="example-6"></a><span data-ttu-id="0077f-276">ESEMPIO 6</span><span class="sxs-lookup"><span data-stu-id="0077f-276">EXAMPLE 6</span></span>

<span data-ttu-id="0077f-277">Questo esempio consente a tutti gli utenti di accedere a tutti gli endpoint in tutti i computer.</span><span class="sxs-lookup"><span data-stu-id="0077f-277">This example allows all users access to all endpoints on all computers.</span></span>
<span data-ttu-id="0077f-278">In pratica, disattiva le regole di autorizzazione.\\</span><span class="sxs-lookup"><span data-stu-id="0077f-278">This essentially turns off authorization rules.\\</span></span>
<span data-ttu-id="0077f-279">**Nota**: l'uso del carattere jolly `*` non è consigliato per le distribuzioni in cui la sicurezza è un fattore essenziale e deve essere considerato solo per gli ambienti di test o le distribuzioni in cui è possibile ridurre la protezione.</span><span class="sxs-lookup"><span data-stu-id="0077f-279">**Note**: Use of the `*` wildcard character is not recommended for security-sensitive deployments and should only be considered for test environments or used in deployments where security can be relaxed.</span></span>

````PowerShell
Add-PswaAuthorizationRule –UserName * -ComputerName * -ConfigurationName *
````

## <a name="see-also"></a><span data-ttu-id="0077f-280">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="0077f-280">See Also</span></span>

- <span data-ttu-id="0077f-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0077f-281">[Get-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592891(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0077f-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0077f-282">[Remove-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592893(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0077f-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0077f-283">[Test-PswaAuthorizationRule](https://technet.microsoft.com/en-us/library/jj592892(v=wps.630).aspx)</span></span>
- <span data-ttu-id="0077f-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span><span class="sxs-lookup"><span data-stu-id="0077f-284">[Install-PswaWebApplication](https://technet.microsoft.com/en-us/library/jj592894(v=wps.630).aspx)</span></span>
- [<span data-ttu-id="0077f-285">Add-Member</span><span class="sxs-lookup"><span data-stu-id="0077f-285">Add-Member</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113280)
- [<span data-ttu-id="0077f-286">New-Object</span><span class="sxs-lookup"><span data-stu-id="0077f-286">New-Object</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=113355)
- [<span data-ttu-id="0077f-287">Get-Credential</span><span class="sxs-lookup"><span data-stu-id="0077f-287">Get-Credential</span></span>](http://go.microsoft.com/fwlink/?LinkID=293936)