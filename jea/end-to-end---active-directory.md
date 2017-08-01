---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: end-to-end Active Directory
ms.technology: powershell
ms.openlocfilehash: 3108f5dad96ef54feb3cf559fae38812ed46849c
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="end-to-end---active-directory"></a><span data-ttu-id="255a2-103">End-to-end - Active Directory</span><span class="sxs-lookup"><span data-stu-id="255a2-103">End to End - Active Directory</span></span>
<span data-ttu-id="255a2-104">Si supponga che l'ambito del programma sia aumentato</span><span class="sxs-lookup"><span data-stu-id="255a2-104">Imagine the scope of your program has increased.</span></span>
<span data-ttu-id="255a2-105">e di essere responsabili dell'aggiunta di JEA ai controller di dominio per eseguire azioni di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="255a2-105">You are now responsible for adding JEA to Domain Controllers to perform Active Directory actions.</span></span>
<span data-ttu-id="255a2-106">Il personale dell'help desk userà JEA per sbloccare gli account, reimpostare le password ed eseguire altre operazioni simili.</span><span class="sxs-lookup"><span data-stu-id="255a2-106">The help desk people are going to use JEA to unlock accounts, reset passwords, and do other similar actions.</span></span>

<span data-ttu-id="255a2-107">È necessario esporre un set di comandi completamente nuovo per un altro gruppo di persone.</span><span class="sxs-lookup"><span data-stu-id="255a2-107">You need to expose a completely new set of commands to a different group of people.</span></span>
<span data-ttu-id="255a2-108">In più, si dovrà esporre anche una serie di script di Active Directory già esistenti.</span><span class="sxs-lookup"><span data-stu-id="255a2-108">On top of that, you have a bunch of existing Active Directory scripts you need to expose.</span></span>
<span data-ttu-id="255a2-109">In questa sezione verrà illustrata la creazione di una configurazione di sessione e delle capacità del ruolo per questa attività.</span><span class="sxs-lookup"><span data-stu-id="255a2-109">This section will walk through authoring a Session Configuration and Role Capability for this task.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="255a2-110">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="255a2-110">Prerequisites</span></span>
<span data-ttu-id="255a2-111">Per seguire le istruzioni dettagliate di questa sezione, è necessario lavorare su un controller di dominio.</span><span class="sxs-lookup"><span data-stu-id="255a2-111">To follow this section step-by-step, you'll need to be operating on a domain controller.</span></span>
<span data-ttu-id="255a2-112">Se non si ha accesso al proprio controller di dominio non è un problema.</span><span class="sxs-lookup"><span data-stu-id="255a2-112">If you don't have access to your domain controller, don't worry.</span></span>
<span data-ttu-id="255a2-113">Provare a seguire la procedura lavorando in un altro scenario o ruolo con cui si ha familiarità.</span><span class="sxs-lookup"><span data-stu-id="255a2-113">Try to follow along with by working against some other scenario or role with which you are familiar.</span></span>
<span data-ttu-id="255a2-114">Per configurare rapidamente un nuovo controller di dominio, vedere l'appendice [Creazione di un controller di dominio](.\creating-a-domain-controller.md).</span><span class="sxs-lookup"><span data-stu-id="255a2-114">If you want to quickly set up a new domain controller, check out the [Creating a Domain Controller appendix](.\creating-a-domain-controller.md).</span></span>

## <a name="steps-to-make-a-new-role-capability-and-session-configuration"></a><span data-ttu-id="255a2-115">Procedura per la creazione di una nuova capacità del ruolo e una configurazione di sessione</span><span class="sxs-lookup"><span data-stu-id="255a2-115">Steps to Make a new Role Capability and Session Configuration</span></span>

<span data-ttu-id="255a2-116">Creare una nuova capacità del ruolo può essere scoraggiante all'inizio, ma l'operazione può essere suddivisa in passaggi abbastanza semplici:</span><span class="sxs-lookup"><span data-stu-id="255a2-116">Making a new role capability can seem daunting at first, but it can be broken into fairly simple steps:</span></span>

1.  <span data-ttu-id="255a2-117">Identificare le attività che è necessario abilitare</span><span class="sxs-lookup"><span data-stu-id="255a2-117">Identify the tasks you need to enable</span></span>
2.  <span data-ttu-id="255a2-118">Limitare le attività secondo le esigenze</span><span class="sxs-lookup"><span data-stu-id="255a2-118">Restrict those tasks as necessary</span></span>
3.  <span data-ttu-id="255a2-119">Verificare che funzionino con JEA</span><span class="sxs-lookup"><span data-stu-id="255a2-119">Confirm they work with JEA</span></span>
4.  <span data-ttu-id="255a2-120">Inserirle in un file di capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="255a2-120">Put them in a Role Capability file</span></span>
5.  <span data-ttu-id="255a2-121">Registrare una configurazione di sessione che espone la capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="255a2-121">Register a Session Configuration that exposes that Role Capability</span></span>

## <a name="step-1-identify-what-needs-to-be-exposed"></a><span data-ttu-id="255a2-122">Passaggio 1: Identificare gli elementi da esporre</span><span class="sxs-lookup"><span data-stu-id="255a2-122">Step 1: Identify What Needs to Be Exposed</span></span>
<span data-ttu-id="255a2-123">Prima di creare una nuova capacità del ruolo o configurazione di sessione, è necessario identificare tutte le attività che gli utenti dovranno svolgere attraverso l'endpoint JEA, nonché le modalità di gestione con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="255a2-123">Before you make a new Role Capability or Session Configuration, you need to identify all of the things users will need to do through the JEA endpoint, as well as how to do them through PowerShell.</span></span>
<span data-ttu-id="255a2-124">Questo comporta un discreto lavoro di ricerca e raccolta dei requisiti.</span><span class="sxs-lookup"><span data-stu-id="255a2-124">This will involve a fair amount of requirement gathering and research.</span></span>
<span data-ttu-id="255a2-125">Il modo di procedere dipende dall'organizzazione e dagli obiettivi.</span><span class="sxs-lookup"><span data-stu-id="255a2-125">How you go about this process will depend on your organization and goals.</span></span>
<span data-ttu-id="255a2-126">È importante sottolineare che la ricerca e la raccolta dei requisiti costituiscono una parte essenziale del processo reale.</span><span class="sxs-lookup"><span data-stu-id="255a2-126">It is important to call out requirement gathering and research as a critical part of the real world process.</span></span>
<span data-ttu-id="255a2-127">Potrebbe trattarsi del passaggio più difficile del processo di adozione di JEA.</span><span class="sxs-lookup"><span data-stu-id="255a2-127">This may be the most difficult step in the process of adopting JEA.</span></span>

### <a name="find-resources"></a><span data-ttu-id="255a2-128">Reperire le risorse</span><span class="sxs-lookup"><span data-stu-id="255a2-128">Find Resources</span></span>
<span data-ttu-id="255a2-129">Di seguito sono riportate alcune risorse online che potrebbero apparire nella ricerca in relazione alla creazione di un endpoint di gestione di Active Directory:</span><span class="sxs-lookup"><span data-stu-id="255a2-129">Here is a set of online resources that might have come up in your research on creating an Active Directory management endpoint:</span></span>
-   [<span data-ttu-id="255a2-130">Panoramica di Active Directory PowerShell</span><span class="sxs-lookup"><span data-stu-id="255a2-130">Active Directory PowerShell Overview</span></span>](http://blogs.msdn.com/b/adpowershell/archive/2009/03/05/active-directory-powershell-overview.aspx)
-   [<span data-ttu-id="255a2-131">Guida per il passaggio da CMD a PowerShell per Active Directory</span><span class="sxs-lookup"><span data-stu-id="255a2-131">CMD to PowerShell Guide for Active Directory</span></span>](http://blogs.technet.com/b/ashleymcglone/archive/2013/01/02/free-download-cmd-to-powershell-guide-for-ad.aspx)

### <a name="make-a-list"></a><span data-ttu-id="255a2-132">Creare un elenco</span><span class="sxs-lookup"><span data-stu-id="255a2-132">Make a List</span></span>
<span data-ttu-id="255a2-133">Ecco una serie di dieci azioni che verranno usate più avanti in questa sezione.</span><span class="sxs-lookup"><span data-stu-id="255a2-133">Here is a set of ten actions that you will be working from in the remainder of this section.</span></span>
<span data-ttu-id="255a2-134">Tenere presente che si tratta semplicemente di un esempio, i requisiti della propria organizzazione possono essere diversi:</span><span class="sxs-lookup"><span data-stu-id="255a2-134">Keep in mind this is simply an example, your organizations requirements may be different:</span></span>

|<span data-ttu-id="255a2-135">Azione</span><span class="sxs-lookup"><span data-stu-id="255a2-135">Action</span></span>                                                         |<span data-ttu-id="255a2-136">Comando di PowerShell</span><span class="sxs-lookup"><span data-stu-id="255a2-136">PowerShell Command</span></span>                                             |
|---------------------------------------------------------------|---------------------------------------------------------------|
|<span data-ttu-id="255a2-137">Sblocco dell'account</span><span class="sxs-lookup"><span data-stu-id="255a2-137">Account Unlock</span></span>                                                 |`Unlock-ADAccount`                                             |
|<span data-ttu-id="255a2-138">Reimpostazione della password</span><span class="sxs-lookup"><span data-stu-id="255a2-138">Password Reset</span></span>                                                 |<span data-ttu-id="255a2-139">`Set-ADAccountPassword` e `Set-ADUser -ChangePasswordAtLogon`</span><span class="sxs-lookup"><span data-stu-id="255a2-139">`Set-ADAccountPassword` and `Set-ADUser -ChangePasswordAtLogon`</span></span>|
|<span data-ttu-id="255a2-140">Modifica del titolo di un utente</span><span class="sxs-lookup"><span data-stu-id="255a2-140">Change a User's Title</span></span>                                          |`Set-ADUser -Title`                                            |  
|<span data-ttu-id="255a2-141">Ricerca di account di Active Directory bloccati, disabilitati, inattivi e così via</span><span class="sxs-lookup"><span data-stu-id="255a2-141">Find AD Accounts that are locked out, disabled, inactive, etc.</span></span> |`Search-ADAccount`                                             |
|<span data-ttu-id="255a2-142">Aggiunta di un utente a un gruppo</span><span class="sxs-lookup"><span data-stu-id="255a2-142">Add User to Group</span></span>                                              |`Add-ADGroupMember -Identity (with whitelist) -Members`        |
|<span data-ttu-id="255a2-143">Rimozione di un utente da un gruppo</span><span class="sxs-lookup"><span data-stu-id="255a2-143">Remove User from Group</span></span>                                         |`Remove-ADGroupMember -Identity (with whitelist) -Members`     |
|<span data-ttu-id="255a2-144">Abilitazione di un account utente</span><span class="sxs-lookup"><span data-stu-id="255a2-144">Enable a user account</span></span>                                          |`Enable-ADAccount`                                             |
|<span data-ttu-id="255a2-145">Disabilitazione di un account utente</span><span class="sxs-lookup"><span data-stu-id="255a2-145">Disable a user account</span></span>                                         |`Disable-ADAccount`                                            |

## <a name="step-2-restrict-tasks-as-necessary"></a><span data-ttu-id="255a2-146">Passaggio 2: Limitare le attività secondo le esigenze</span><span class="sxs-lookup"><span data-stu-id="255a2-146">Step 2: Restrict Tasks as Necessary</span></span>

<span data-ttu-id="255a2-147">Ora che si ha a disposizione un elenco di azioni, è necessario valutare la funzionalità di ogni comando.</span><span class="sxs-lookup"><span data-stu-id="255a2-147">Now that you have your list of actions, you need to think through the capabilities of each command.</span></span>
<span data-ttu-id="255a2-148">Esistono due motivi principali per eseguire questa operazione:</span><span class="sxs-lookup"><span data-stu-id="255a2-148">There are two important reasons to do this:</span></span>

1.  <span data-ttu-id="255a2-149">È semplice offrire agli utenti più funzionalità del previsto.</span><span class="sxs-lookup"><span data-stu-id="255a2-149">It is easy to give users more capabilities than you intend.</span></span>
<span data-ttu-id="255a2-150">Ad esempio, `Set-ADUser` è un comando incredibilmente potente e flessibile.</span><span class="sxs-lookup"><span data-stu-id="255a2-150">For example, `Set-ADUser` is an incredibly powerful and flexible command.</span></span>
<span data-ttu-id="255a2-151">È opportuno evitare di esporre tutto ciò che è in grado di fare agli utenti dell'help desk.</span><span class="sxs-lookup"><span data-stu-id="255a2-151">You may not want to expose everything it can do to help desk users.</span></span>  

2.  <span data-ttu-id="255a2-152">Peggio ancora, è possibile esporre comandi che consentono agli utenti di evitare le restrizioni di JEA.</span><span class="sxs-lookup"><span data-stu-id="255a2-152">Even worse, it's possible to expose commands that allow users to escape JEA's restrictions.</span></span>
<span data-ttu-id="255a2-153">In questo caso JEA smette di funzionare come limite di sicurezza.</span><span class="sxs-lookup"><span data-stu-id="255a2-153">If this happens, JEA ceases to function as a security boundary.</span></span>
<span data-ttu-id="255a2-154">Prestare attenzione quando si selezionano i comandi.</span><span class="sxs-lookup"><span data-stu-id="255a2-154">Please be careful when selecting commands.</span></span>
<span data-ttu-id="255a2-155">Ad esempio, Invoke-Expression consentirà agli utenti di eseguire codice senza restrizioni.</span><span class="sxs-lookup"><span data-stu-id="255a2-155">For example, Invoke-Expression will allow users to run unrestricted code.</span></span>
<span data-ttu-id="255a2-156">Per altre informazioni su questo argomento, vedere la sezione relativa alla limitazione dei comandi.</span><span class="sxs-lookup"><span data-stu-id="255a2-156">For more discussion on this topic, check out the Considerations When Restricting Commands section.</span></span>

<span data-ttu-id="255a2-157">Dopo aver esaminato ogni comando, si decide di limitare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="255a2-157">After reviewing each command, you decide to restrict the following:</span></span>

1.  <span data-ttu-id="255a2-158">`Set-ADUser` deve essere eseguito solo con il parametro -Title</span><span class="sxs-lookup"><span data-stu-id="255a2-158">`Set-ADUser` should only be allowed to run with the -Title parameter</span></span>

2.  <span data-ttu-id="255a2-159">`Add-ADGroupMember` e `Remove-ADGroupMember` devono funzionare solo con alcuni gruppi</span><span class="sxs-lookup"><span data-stu-id="255a2-159">`Add-ADGroupMember` and `Remove-ADGroupMember` should only work with certain groups</span></span>

### <a name="step-3-confirm-the-tasks-work-with-jea"></a><span data-ttu-id="255a2-160">Passaggio 3: Verificare se le attività funzionano con JEA</span><span class="sxs-lookup"><span data-stu-id="255a2-160">Step 3: Confirm the Tasks Work with JEA</span></span>
<span data-ttu-id="255a2-161">Usare i cmdlet potrebbe non essere semplice nell'ambiente JEA con restrizioni.</span><span class="sxs-lookup"><span data-stu-id="255a2-161">Actually using those cmdlets may not be straightforward in the restricted JEA environment.</span></span>
<span data-ttu-id="255a2-162">JEA viene eseguito in modalità *NoLanguage* che, tra l'altro, impedisce agli utenti di usare le variabili.</span><span class="sxs-lookup"><span data-stu-id="255a2-162">JEA runs in *NoLanguage* mode which, among other things, prevents users from using variables.</span></span>
<span data-ttu-id="255a2-163">Per garantire che gli utenti finali usufruiscano di un'esperienza ottimale, è importante verificare alcuni aspetti.</span><span class="sxs-lookup"><span data-stu-id="255a2-163">In order to ensure that end users have a smooth experience, it's important to check for a few things.</span></span>

<span data-ttu-id="255a2-164">Ad esempio, considerare `Set-ADAccountPassword`.</span><span class="sxs-lookup"><span data-stu-id="255a2-164">As an example, consider `Set-ADAccountPassword`.</span></span>
<span data-ttu-id="255a2-165">Il parametro -NewPassword richiede una stringa sicura.</span><span class="sxs-lookup"><span data-stu-id="255a2-165">The -NewPassword parameter requires a secure string.</span></span>
<span data-ttu-id="255a2-166">Spesso gli utenti creano un stringa sicura e la passano come variabile, come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="255a2-166">Often, users create a secure string and pass it in as a variable (as below):</span></span>

```PowerShell
$newPassword = Read-Host -Prompt "Specify a new password" -AsSecureString
Set-ADAccountPassword -Identity mollyd -NewPassword $newPassword -Reset
```

<span data-ttu-id="255a2-167">La modalità *NoLanguage* impedisce, tuttavia, l'utilizzo delle variabili.</span><span class="sxs-lookup"><span data-stu-id="255a2-167">However, *NoLanguage* mode prevents the usage of variables.</span></span>
<span data-ttu-id="255a2-168">È possibile aggirare questa restrizione in due modi:</span><span class="sxs-lookup"><span data-stu-id="255a2-168">You can get around this restriction in two ways:</span></span>

1.  <span data-ttu-id="255a2-169">È possibile richiedere agli utenti di eseguire il comando senza assegnare variabili.</span><span class="sxs-lookup"><span data-stu-id="255a2-169">You can require users run the command without assigning variables.</span></span>
<span data-ttu-id="255a2-170">La relativa configurazione è semplice, ma può diventare macchinosa per gli operatori che usano l'endpoint,</span><span class="sxs-lookup"><span data-stu-id="255a2-170">This is easy to configure, but can be painful for the operators using the endpoint.</span></span>
<span data-ttu-id="255a2-171">che ad ogni reimpostazione di una password dovrebbero digitare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="255a2-171">Who wants to type this out every time you reset a password?</span></span>
```PowerShell
Set-ADAccountPassword -Identity mollyd -NewPassword (Read-Host -Prompt "Specify a new password" -AsSecureString) -Reset
```

2.  <span data-ttu-id="255a2-172">È possibile ridurre la complessità usando uno script o una funzione da esporre agli utenti finali.</span><span class="sxs-lookup"><span data-stu-id="255a2-172">You can wrap the complexity in a script or a function that you expose to end users.</span></span>
<span data-ttu-id="255a2-173">Le funzioni e gli script esposti vengono eseguiti in un contesto senza restrizioni. È possibile scrivere funzioni che usano le variabili e chiamano altri comandi senza alcun problema.</span><span class="sxs-lookup"><span data-stu-id="255a2-173">Scripts and functions that you expose run in an unrestricted context; you can write functions that use variables and call other commands without any issue.</span></span>
<span data-ttu-id="255a2-174">Questo approccio semplifica l'esperienza dell'utente finale, impedisce gli errori, riduce la competenza necessaria con PowerShell ed evita che vengano esposte involontariamente funzionalità in eccesso.</span><span class="sxs-lookup"><span data-stu-id="255a2-174">This approach simplifies the end user experience, prevents errors, reduces required PowerShell knowledge, and reduces unintentionally exposing excess functionality.</span></span>
<span data-ttu-id="255a2-175">L'unico svantaggio è costituito dai costi di creazione e gestione della funzione.</span><span class="sxs-lookup"><span data-stu-id="255a2-175">The only downside is the cost of authoring and maintaining the function.</span></span>

### <a name="aside-adding-a-function-to-your-module"></a><span data-ttu-id="255a2-176">Approfondimento: Aggiunta di una funzione al modulo</span><span class="sxs-lookup"><span data-stu-id="255a2-176">Aside: Adding a Function to your Module</span></span>
<span data-ttu-id="255a2-177">Con l'approccio n. 2 si scrive una funzione di PowerShell denominata `Reset-ContosoUserPassword`.</span><span class="sxs-lookup"><span data-stu-id="255a2-177">Taking approach #2, you are going to write a PowerShell function called `Reset-ContosoUserPassword`.</span></span>
<span data-ttu-id="255a2-178">Questa funzione dovrà eseguire tutte le operazioni necessarie quando si reimposta la password di un utente.</span><span class="sxs-lookup"><span data-stu-id="255a2-178">This function is going to do everything that needs to happen when you reset a user's password.</span></span>
<span data-ttu-id="255a2-179">In un'organizzazione questo può significare dover svolgere attività elaborate e complesse.</span><span class="sxs-lookup"><span data-stu-id="255a2-179">In your organization, this may involve doing fancy and complicated things.</span></span>
<span data-ttu-id="255a2-180">Poiché si tratta semplicemente di un esempio, il comando si limiterà a reimpostare la password e a richiedere all'utente di cambiare la password all'accesso.</span><span class="sxs-lookup"><span data-stu-id="255a2-180">Because this is just an example, your command will just reset the password and require the user change the password at logon.</span></span>
<span data-ttu-id="255a2-181">Il comando verrà inserito nel modulo Contoso_AD_Module creato nell'ultima sezione.</span><span class="sxs-lookup"><span data-stu-id="255a2-181">We will put it in the Contoso_AD_Module module you made in the last section.</span></span>

1. <span data-ttu-id="255a2-182">In PowerShell ISE aprire "Contoso_AD_Module.psm1"</span><span class="sxs-lookup"><span data-stu-id="255a2-182">In PowerShell ISE, open "Contoso_AD_Module.psm1"</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1'
```

2. <span data-ttu-id="255a2-183">Premere CTRL + J per aprire il menu dei frammenti di codice.</span><span class="sxs-lookup"><span data-stu-id="255a2-183">Press Crtl+J to open the snippets menu.</span></span>

3. <span data-ttu-id="255a2-184">Premere la freccia in basso finché non appare "function" e premere INVIO.</span><span class="sxs-lookup"><span data-stu-id="255a2-184">Key down until you find "function" and press enter.</span></span>
<span data-ttu-id="255a2-185">In questo modo viene creato uno "scheletro" molto essenziale di funzione.</span><span class="sxs-lookup"><span data-stu-id="255a2-185">This puts up a super basic skeleton of a function.</span></span>

4. <span data-ttu-id="255a2-186">Rinominare la funzione "Reset-ContosoUserPassword".</span><span class="sxs-lookup"><span data-stu-id="255a2-186">Rename the function "Reset-ContosoUserPassword".</span></span>  

5. <span data-ttu-id="255a2-187">Rinominare uno dei parametri "Identity" ed eliminare il secondo.</span><span class="sxs-lookup"><span data-stu-id="255a2-187">Rename one of the parameters "Identity" and delete the second.</span></span>

6. <span data-ttu-id="255a2-188">Copiare quanto segue nel corpo della funzione.</span><span class="sxs-lookup"><span data-stu-id="255a2-188">Copy the following into the body of the function.</span></span>
```PowerShell
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
```

7. <span data-ttu-id="255a2-189">Salvare il file.</span><span class="sxs-lookup"><span data-stu-id="255a2-189">Save the file.</span></span>
<span data-ttu-id="255a2-190">Il risultato dovrebbe essere simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="255a2-190">You should end up with something that looks like this:</span></span>
```PowerShell
function Reset-ContosoUserPassword ($Identity)
{
# Get the new password
$NewPassword = Read-Host -Prompt "Enter a new password" -AsSecureString
# Reset the password
Set-ADAccountPassword -Identity $Identity -NewPassword $NewPassword -Reset
# Require the user to reset at next logon
Set-ADUser -Identity $Identity -ChangePasswordAtLogon
}
```
<span data-ttu-id="255a2-191">A questo punto, gli utenti possono semplicemente chiamare `Reset-ContosoUserPassword` senza dover ricordare la sintassi richiesta per creare una stringa sicura inline.</span><span class="sxs-lookup"><span data-stu-id="255a2-191">Now, your users can simply call `Reset-ContosoUserPassword` and not have to remember the syntax to create a secure string inline.</span></span>

## <a name="step-4-edit-the-role-capability-file"></a><span data-ttu-id="255a2-192">Passaggio 4: Modificare il file di capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="255a2-192">Step 4: Edit the Role Capability File</span></span>
<span data-ttu-id="255a2-193">Nella sezione [Creazione di capacità del ruolo](./role-capabilities.md#role-capability-creation) è stato creato un file di capacità del ruolo vuoto.</span><span class="sxs-lookup"><span data-stu-id="255a2-193">In the [Role Capability Creation](./role-capabilities.md#role-capability-creation) section, you created a blank Role Capability file.</span></span>
<span data-ttu-id="255a2-194">In questa sezione verranno inseriti i valori nel file.</span><span class="sxs-lookup"><span data-stu-id="255a2-194">In this section, you will fill in the values in that file.</span></span>

<span data-ttu-id="255a2-195">Innanzitutto, aprire il file di capacità del ruolo in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="255a2-195">Start by opening the role capability file in PowerShell ISE.</span></span>
```PowerShell
ise 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```
<span data-ttu-id="255a2-196">Aggiornare il file con le seguenti modifiche:</span><span class="sxs-lookup"><span data-stu-id="255a2-196">Update the file with the following changes:</span></span>
```PowerShell
# OLD: VisibleCmdlets = 'Invoke-Cmdlet1', @{ Name = 'Invoke-Cmdlet2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleCmdlets =
    'Unlock-ADAccount',
    'Search-ADAccount',
    'Enable-ADAccount',
    'Disable-ADAccount',
    @{ Name = 'Set-ADUser'; Parameters = @{ Name = 'Title'; ValidateSet = 'Manager', 'Engineer' }},
    @{ Name = 'Add-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}},
    @{ Name = 'Remove-ADGroupMember'; Parameters =
        @{Name = 'Identity'; ValidateSet = 'TestGroup'},
        @{Name = 'Members'}}

# OLD: VisibleFunctions = 'Invoke-Function1', @{ Name = 'Invoke-Function2'; Parameters = @{ Name = 'Parameter1'; ValidateSet = 'Item1', 'Item2' }, @{ Name = 'Parameter2'; ValidatePattern = 'L*' } }
VisibleFunctions = 'Reset-ContosoUserPassword'
```

<span data-ttu-id="255a2-197">Riguardo al codice riportato sopra è necessario osservare quanto segue:</span><span class="sxs-lookup"><span data-stu-id="255a2-197">There are a few things to note about the above:</span></span>
1.  <span data-ttu-id="255a2-198">PowerShell tenterà di caricare automaticamente i moduli necessari per la capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="255a2-198">PowerShell will attempt to auto-load the modules needed for your Role Capability.</span></span>
<span data-ttu-id="255a2-199">Può essere necessario indicare in modo esplicito i nomi dei moduli nel campo "ModulesToImport" se si riscontrano problemi con un modulo che non viene caricato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="255a2-199">You may need to explicitly list module names in the "ModulesToImport" field if you notice problems with a module not being autoloaded.</span></span>

2.  <span data-ttu-id="255a2-200">Per verificare se un comando è un cmdlet o una funzione, eseguire `Get-Command` e controllare la proprietà "CommandType"</span><span class="sxs-lookup"><span data-stu-id="255a2-200">If you aren't sure if a command is a cmdlet or a function, run `Get-Command` and look at the "CommandType" property</span></span>

3.  <span data-ttu-id="255a2-201">ValidatePattern consente di usare un'espressione regolare per limitare gli argomenti di parametro, nel caso in cui non sia facile definire un set di valori consentiti.</span><span class="sxs-lookup"><span data-stu-id="255a2-201">The ValidatePattern allows you to use a regular expression to restrict parameter arguments if it is not easy to define a set of allowable values.</span></span>
<span data-ttu-id="255a2-202">Non è possibile definire sia un valore ValidatePattern che un valore ValidateSet per un singolo parametro.</span><span class="sxs-lookup"><span data-stu-id="255a2-202">You cannot define both a ValidatePattern and ValidateSet for a single parameter.</span></span>

## <a name="step-5-register-a-new-session-configuration"></a><span data-ttu-id="255a2-203">Passaggio 5: Registrare una nuova configurazione di sessione</span><span class="sxs-lookup"><span data-stu-id="255a2-203">Step 5: Register a new Session Configuration</span></span>
<span data-ttu-id="255a2-204">È necessario creare un nuovo file di configurazione di sessione che esporrà la capacità del ruolo ai membri del gruppo "JEA_NonAdmin_HelpDesk" di Active Directory.</span><span class="sxs-lookup"><span data-stu-id="255a2-204">Next, you will create a new session configuration file that will expose your Role Capability to members of the "JEA_NonAdmin_HelpDesk" AD group.</span></span>

<span data-ttu-id="255a2-205">Per iniziare, creare e aprire un nuovo file di configurazione di sessione vuoto in PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="255a2-205">Start by creating and opening a new blank Session Configuration file in PowerShell ISE.</span></span>
```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
ise "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
<span data-ttu-id="255a2-206">Modificare i campi seguenti nel file PSSC.</span><span class="sxs-lookup"><span data-stu-id="255a2-206">Modify the following fields in the PSSC file.</span></span>
<span data-ttu-id="255a2-207">Se si lavora nel proprio ambiente, è necessario sostituire "CONTOSO\JEA_NonAdmins_Helpdesk" con il proprio utente o gruppo non amministratore.</span><span class="sxs-lookup"><span data-stu-id="255a2-207">If you are working in your own environment, you should replace "CONTOSO\JEA_NonAdmins_Helpdesk" with your own non-administrator user or group.</span></span>
```PowerShell
# OLD: Description = ''
Description = 'An endpoint for Active Directory tasks.'

# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{ 'CONTOSO\JEA_NonAdmin_HelpDesk' = @{ RoleCapabilities =  'ADHelpDesk' }}
```
<span data-ttu-id="255a2-208">Salvare e registrare la configurazione di sessione</span><span class="sxs-lookup"><span data-stu-id="255a2-208">Save and register the Session Configuration</span></span>
```PowerShell
Register-PSSessionConfiguration -Name ADHelpDesk -Path "$env:ProgramData\JEAConfiguration\HelpDeskDemo.pssc"
```
## <a name="test-it-out"></a><span data-ttu-id="255a2-209">Testare la configurazione</span><span class="sxs-lookup"><span data-stu-id="255a2-209">Test It Out!</span></span>
<span data-ttu-id="255a2-210">Ottenere le credenziali di utente non amministratore:</span><span class="sxs-lookup"><span data-stu-id="255a2-210">Get your non-administrator user credentials:</span></span>
```PowerShell
$HelpDeskCred = Get-Credential
```
<span data-ttu-id="255a2-211">Se si è seguita la sezione [Configurare utenti e gruppi](creating-a-domain-controller.md#set-up-users-and-groups) le credenziali sono:</span><span class="sxs-lookup"><span data-stu-id="255a2-211">If you followed the [Set Up Users and Groups](creating-a-domain-controller.md#set-up-users-and-groups) section, the credentials will be:</span></span>
-   <span data-ttu-id="255a2-212">Username = "HelpDeskUser"</span><span class="sxs-lookup"><span data-stu-id="255a2-212">Username = "HelpDeskUser"</span></span>
-   <span data-ttu-id="255a2-213">Password = "pa$$w0rd"</span><span class="sxs-lookup"><span data-stu-id="255a2-213">Password = "pa$$w0rd"</span></span>

<span data-ttu-id="255a2-214">Accedere in remoto all'endpoint dell'help desk di Active Directory usando le credenziali di utente non amministratore:</span><span class="sxs-lookup"><span data-stu-id="255a2-214">Remote into the ADHelpdesk endpoint using the non-admin credential:</span></span>
```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName ADHelpDesk -Credential $HelpDeskCred
```
<span data-ttu-id="255a2-215">Usare Set-ADUser per reimpostare il titolo di un utente.</span><span class="sxs-lookup"><span data-stu-id="255a2-215">Use Set-ADUser to reset a user's title.</span></span>
```PowerShell
Set-ADUser -Identity OperatorUser -Title Engineer
```
<span data-ttu-id="255a2-216">Verificare che il titolo è stato modificato.</span><span class="sxs-lookup"><span data-stu-id="255a2-216">Verify that the title has changed.</span></span>
```PowerShell
Get-ADUser -Identity OperatorUser -Property Title
```
<span data-ttu-id="255a2-217">A questo punto, usare Add-ADGroupMember per aggiungere un utente al gruppo TestGroup.</span><span class="sxs-lookup"><span data-stu-id="255a2-217">Now, use Add-ADGroupMember to add a user to the TestGroup.</span></span>
<span data-ttu-id="255a2-218">Nota: verificare che TestGroup sia già stato creato.</span><span class="sxs-lookup"><span data-stu-id="255a2-218">Note: make sure you've created the TestGroup beforehand.</span></span>
```PowerShell
Add-ADGroupMember TestGroup -Member OperatorUser -Verbose
```
<span data-ttu-id="255a2-219">Chiudere la sessione:</span><span class="sxs-lookup"><span data-stu-id="255a2-219">Exit the session:</span></span>
```PowerShell
Exit-PSSession
```
## <a name="key-concepts"></a><span data-ttu-id="255a2-220">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="255a2-220">Key Concepts</span></span>
<span data-ttu-id="255a2-221">**Modalità NoLanguage**: quando PowerShell è in modalità "NoLanguage", gli utenti possono solo eseguire i comandi e non possono usare elementi del linguaggio.</span><span class="sxs-lookup"><span data-stu-id="255a2-221">**NoLanguage Mode**: When PowerShell is in "NoLanguage" mode, users may only run commands; they cannot use any language elements.</span></span>
<span data-ttu-id="255a2-222">Per altre informazioni, eseguire `Get-Help about_Language_Modes`.</span><span class="sxs-lookup"><span data-stu-id="255a2-222">For more information, run `Get-Help about_Language_Modes`.</span></span>

<span data-ttu-id="255a2-223">**Funzioni di PowerShell**: le funzioni di PowerShell sono parti di codice di PowerShell che è possibile chiamare in base al nome.</span><span class="sxs-lookup"><span data-stu-id="255a2-223">**PowerShell Functions**: PowerShell functions are bits of PowerShell code that you can call by name.</span></span>
<span data-ttu-id="255a2-224">Per altre informazioni, eseguire `Get-Help about_Functions`.</span><span class="sxs-lookup"><span data-stu-id="255a2-224">For more information, run `Get-Help about_Functions`.</span></span>

<span data-ttu-id="255a2-225">**ValidateSet/ValidatePattern**: quando si espone un comando, è possibile limitare gli argomenti validi per parametri specifici.</span><span class="sxs-lookup"><span data-stu-id="255a2-225">**ValidateSet/ValidatePattern**: When exposing a command, you can restrict valid arguments for specific parameters.</span></span>
<span data-ttu-id="255a2-226">ValidateSet è un elenco specifico di argomenti validi.</span><span class="sxs-lookup"><span data-stu-id="255a2-226">A ValidateSet is a specific list of valid arguments.</span></span>
<span data-ttu-id="255a2-227">ValidatePattern è un'espressione regolare a cui gli argomenti per il parametro devono corrispondere.</span><span class="sxs-lookup"><span data-stu-id="255a2-227">A ValidatePattern is a regular expression that the arguments for that parameter must match.</span></span>

