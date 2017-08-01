---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: FILE LEGGIMI
ms.technology: powershell
ms.openlocfilehash: b0ef4ff685b82e1a4e9ab83a45736720df7b39a2
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="just-enough-administration"></a><span data-ttu-id="d7dfa-103">Just Enough Administration</span><span class="sxs-lookup"><span data-stu-id="d7dfa-103">Just Enough Administration</span></span>
<span data-ttu-id="d7dfa-104">Just Enough Administration (JEA) è una tecnologia di protezione che consente l'amministrazione delegata per qualsiasi elemento che possa essere gestito con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-104">Just Enough Administration (JEA) is a security technology that enables delegated administration for anything that can be managed with PowerShell.</span></span>
<span data-ttu-id="d7dfa-105">Con JEA, è possibile:</span><span class="sxs-lookup"><span data-stu-id="d7dfa-105">With JEA, you can:</span></span>
- <span data-ttu-id="d7dfa-106">**Ridurre il numero di amministratori dei computer** sfruttando gli account virtuali che eseguono azioni con privilegi per conto degli utenti normali.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-106">**Reduce the number of administrators on your machines** by leveraging virtual accounts that perform privileged actions on behalf of regular users.</span></span>
- <span data-ttu-id="d7dfa-107">**Limitare le operazioni consentite agli utenti** specificando quali cmdlet, funzioni e comandi esterni possono eseguire.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-107">**Limit what users can do** by specifying which cmdlets, functions, and external commands they can run.</span></span>
- <span data-ttu-id="d7dfa-108">**Seguire da vicino le attività degli utenti** e capirle meglio grazie a trascrizioni "over-the-shoulder" che indicano esattamente quali comandi eseguono gli utenti durante una sessione.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-108">**Better understand what your users are doing** with "over the shoulder" transcriptions that show you exactly what commands a user executed during a session.</span></span>

<span data-ttu-id="d7dfa-109">**Perché tutto questo è importante?**</span><span class="sxs-lookup"><span data-stu-id="d7dfa-109">**Why is this important?**</span></span>  
<span data-ttu-id="d7dfa-110">Si consideri uno scenario comune in cui i server DNS condividono il percorso con i controller di dominio Active Directory.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-110">Consider the common scenario where your DNS servers are co-located with your Active Directory Domain Controllers.</span></span>
<span data-ttu-id="d7dfa-111">Gli amministratori DNS devono avere privilegi di amministratore locale per risolvere i problemi del server DNS, ma per farlo è necessario che siano membri del gruppo di sicurezza con privilegi elevati "Domain Admins".</span><span class="sxs-lookup"><span data-stu-id="d7dfa-111">Your DNS administrators need to have local administrator privileges to fix issues with the DNS server, but in order to do so you have to make them members of the highly privileged "Domain Admins" security group.</span></span>
<span data-ttu-id="d7dfa-112">Con questo approccio gli amministratori DNS saranno in grado di controllare l'intero dominio e di accedere a tutte le risorse del computer.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-112">This approach effectively gives DNS Administrators control over your whole domain and access to all resources on that machine.</span></span>

<span data-ttu-id="d7dfa-113">Se JEA è installato, è possibile configurare un ruolo per gli amministratori DNS che consenta l'accesso a tutti i comandi necessari per svolgere il proprio lavoro, ma niente di più.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-113">With JEA in place, you can configure a role for your DNS administrators that gives them access to all the commands they need to get their job done, but nothing more.</span></span>
<span data-ttu-id="d7dfa-114">Ciò significa che è possibile specificare l'accesso appropriato per ripristinare una cache DNS danneggiata senza concedere inavvertitamente diritti per usare Active Directory, sfogliare il file system o eseguire script potenzialmente pericolosi.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-114">This means you can provide the appropriate access to repair a poisoned DNS cache without unintentionally giving them rights to Active Directory, or to browse the file system, or run potentially dangerous scripts.</span></span>
<span data-ttu-id="d7dfa-115">In più, quando la sessione JEA è configurata per l'uso di account virtuali monouso con privilegi, gli amministratori DNS possono connettersi al server usando credenziali *non privilegiate* ed eseguire comunque comandi con privilegi.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-115">Better yet, when the JEA session is configured to use one-time privileged virtual accounts, your DNS administrators can connect to the server using *unprivileged* credentials and still be able to run privileged commands.</span></span>

## <a name="availability"></a><span data-ttu-id="d7dfa-116">Disponibilità</span><span class="sxs-lookup"><span data-stu-id="d7dfa-116">Availability</span></span>
<span data-ttu-id="d7dfa-117">La soluzione JEA è stata sviluppata in parallelo a Windows Server 2016 ed è disponibile nelle versioni precedenti di Windows con gli aggiornamenti di Windows Management Framework.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-117">JEA is being developed in parallel to Windows Server 2016, and is available on older versions of Windows through Windows Management Framework updates.</span></span>
<span data-ttu-id="d7dfa-118">La versione corrente di JEA è disponibile nelle piattaforme seguenti:</span><span class="sxs-lookup"><span data-stu-id="d7dfa-118">The current release of JEA is available on the following platforms:</span></span>

<span data-ttu-id="d7dfa-119">**Windows Server**</span><span class="sxs-lookup"><span data-stu-id="d7dfa-119">**Windows Server**</span></span>
- <span data-ttu-id="d7dfa-120">Windows Server 2016 Technical Preview 4 e versioni successive</span><span class="sxs-lookup"><span data-stu-id="d7dfa-120">Windows Server 2016 Technical Preview 4 and higher</span></span>
- <span data-ttu-id="d7dfa-121">Windows Server 2012 R2, 2012 e 2008 R2\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato</span><span class="sxs-lookup"><span data-stu-id="d7dfa-121">Windows Server 2012 R2, 2012, and 2008 R2\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="d7dfa-122">**Client Windows**</span><span class="sxs-lookup"><span data-stu-id="d7dfa-122">**Windows Client**</span></span>
- <span data-ttu-id="d7dfa-123">Windows 10 con l'aggiornamento di novembre (1511) installato</span><span class="sxs-lookup"><span data-stu-id="d7dfa-123">Windows 10 with the November Update (1511) installed</span></span>
- <span data-ttu-id="d7dfa-124">Windows 8.1, 8 e 7\* con [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installato</span><span class="sxs-lookup"><span data-stu-id="d7dfa-124">Windows 8.1, 8, and 7\* with [Windows Management Framework 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) installed</span></span>

<span data-ttu-id="d7dfa-125">\* Il supporto per gli account virtuali nelle sessioni JEA attualmente non è disponibile in Windows Server 2008 R2 o Windows 7.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-125">\* Support for virtual accounts in JEA sessions is currently not available on Windows Server 2008 R2 or Windows 7.</span></span>


## <a name="explore-the-experience-guide"></a><span data-ttu-id="d7dfa-126">Esplorare la guida all'esperienza</span><span class="sxs-lookup"><span data-stu-id="d7dfa-126">Explore the experience guide</span></span>
<span data-ttu-id="d7dfa-127">A questo punto si può iniziare a imparare come creare, distribuire e usare il proprio endpoint JEA.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-127">Ready to learn how to author, deploy, and use your own JEA endpoint?</span></span>

<span data-ttu-id="d7dfa-128">Questa guida consente di iniziare rapidamente con un endpoint JEA predefinito per avere un'idea di come sarà l'esperienza per l'utente finale, quindi spiega come ricreare l'endpoint da zero illustrando concetti come le configurazioni di sessione e le capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-128">This guide gets you started quickly with a pre-built JEA endpoint to get an idea of what the end-user experience is like, then walks you through recreating an endpoint from scratch to help demonstrate concepts like session configurations and Role Capabilities.</span></span>

1.  <span data-ttu-id="d7dfa-129">[Introduzione](introduction.md) </span><span class="sxs-lookup"><span data-stu-id="d7dfa-129">[Introduction](introduction.md) </span></span>  
<span data-ttu-id="d7dfa-130">Brevi considerazioni sul perché è opportuno prendere in considerazione JEA</span><span class="sxs-lookup"><span data-stu-id="d7dfa-130">Briefly review why you should care about JEA</span></span>

2.  [<span data-ttu-id="d7dfa-131">Prerequisiti</span><span class="sxs-lookup"><span data-stu-id="d7dfa-131">Prerequisites</span></span>](prerequisites.md)  
<span data-ttu-id="d7dfa-132">Viene illustrato come configurare l'ambiente</span><span class="sxs-lookup"><span data-stu-id="d7dfa-132">Explains how to set up your environment</span></span>

3.  [<span data-ttu-id="d7dfa-133">Uso di JEA</span><span class="sxs-lookup"><span data-stu-id="d7dfa-133">Using JEA</span></span>](using-jea.md)  
<span data-ttu-id="d7dfa-134">Informazioni preliminari sull'esperienza dell'operatore con JEA</span><span class="sxs-lookup"><span data-stu-id="d7dfa-134">Helps you start by understanding the operator experience of using JEA</span></span>

4.  [<span data-ttu-id="d7dfa-135">Ricreare la demo</span><span class="sxs-lookup"><span data-stu-id="d7dfa-135">Remake the Demo</span></span>](remake-the-demo-endpoint.md)  
<span data-ttu-id="d7dfa-136">Creare una configurazione di sessione JEA da zero</span><span class="sxs-lookup"><span data-stu-id="d7dfa-136">Create a JEA Session Configuration from scratch</span></span>

5.  [<span data-ttu-id="d7dfa-137">Capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="d7dfa-137">Role Capabilities</span></span>](role-capabilities.md)  
<span data-ttu-id="d7dfa-138">Informazioni su come personalizzare le funzionalità JEA con i file di capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="d7dfa-138">Learn about how to customize JEA capabilities with Role Capability Files</span></span>

6.  [<span data-ttu-id="d7dfa-139">End-to-end - Active Directory</span><span class="sxs-lookup"><span data-stu-id="d7dfa-139">End to End - Active Directory</span></span>](end-to-end---active-directory.md)  
<span data-ttu-id="d7dfa-140">Creare un endpoint completamente nuovo per la gestione di Active Directory</span><span class="sxs-lookup"><span data-stu-id="d7dfa-140">Make a whole new endpoint for managing Active Directory</span></span>

7.  [<span data-ttu-id="d7dfa-141">Distribuzione e manutenzione con più computer</span><span class="sxs-lookup"><span data-stu-id="d7dfa-141">Multi-machine Deployment and Maintenance</span></span>](multi-machine-deployment-and-maintenance.md)  
<span data-ttu-id="d7dfa-142">Scoprire in che modo le modalità di distribuzione e creazione cambiano con le dimensioni</span><span class="sxs-lookup"><span data-stu-id="d7dfa-142">Discover how deployment and authoring changes with scale</span></span>

8.  [<span data-ttu-id="d7dfa-143">Creazione di report per JEA</span><span class="sxs-lookup"><span data-stu-id="d7dfa-143">Reporting on JEA</span></span>](reporting-on-jea.md)  
<span data-ttu-id="d7dfa-144">Informazioni su come controllare tutte le azioni e l'infrastruttura di JEA e creare i relativi report</span><span class="sxs-lookup"><span data-stu-id="d7dfa-144">Discover how to audit and report on all JEA actions and infrastructure</span></span>

9.  <span data-ttu-id="d7dfa-145">Appendici</span><span class="sxs-lookup"><span data-stu-id="d7dfa-145">Appendixes</span></span>
  - [<span data-ttu-id="d7dfa-146">Concetti principali usati in questa guida</span><span class="sxs-lookup"><span data-stu-id="d7dfa-146">Key Concepts Used Throughout This Guide</span></span>](key-concepts-used-throughout-this-guide.md)  
  -  [<span data-ttu-id="d7dfa-147">Creazione di un controller di dominio</span><span class="sxs-lookup"><span data-stu-id="d7dfa-147">Creating a Domain Controller</span></span>](creating-a-domain-controller.md)  
  -  [<span data-ttu-id="d7dfa-148">Blacklist</span><span class="sxs-lookup"><span data-stu-id="d7dfa-148">On Blacklisting</span></span>](on-blacklisting.md)  
  -  [<span data-ttu-id="d7dfa-149">Considerazioni per la limitazione dei comandi</span><span class="sxs-lookup"><span data-stu-id="d7dfa-149">Considerations When Limiting Commands</span></span>](considerations-when-limiting-commands.md)  
  -  [<span data-ttu-id="d7dfa-150">Problemi comuni delle capacità del ruolo</span><span class="sxs-lookup"><span data-stu-id="d7dfa-150">Common Role Capability Pitfalls</span></span>](common-role-capability-pitfalls.md)

## <a name="start-authoring-your-own-jea-endpoints"></a><span data-ttu-id="d7dfa-151">Iniziare a creare i propri endpoint JEA</span><span class="sxs-lookup"><span data-stu-id="d7dfa-151">Start authoring your own JEA endpoints</span></span>
<span data-ttu-id="d7dfa-152">È facile creare un endpoint JEA: è sufficiente un sistema abilitato per JEA e un editor di testo, ad esempio PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-152">It's easy to author a JEA endpoint -- all you need is a JEA-enabled system and a text editor (like PowerShell ISE).</span></span>
<span data-ttu-id="d7dfa-153">Un suggerimento utile per iniziare è creare i file scheletro usando [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) e [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) senza altri argomenti.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-153">One helpful tip to get started is to create skeleton files using [`New-PSRoleCapabilityFile -Path <path>`](https://technet.microsoft.com/library/mt631422.aspx) and [`New-PSSessionConfigurationFile -Path <Path>`](https://technet.microsoft.com/library/mt631422.aspx) without any other arguments.</span></span>
<span data-ttu-id="d7dfa-154">I file scheletro contengono tutti i campi di configurazione applicabili oltre a commenti utili che spiegano per cosa può essere usato ogni campo.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-154">These skeleton files contain all of the applicable configuration fields along with helpful comments to explain what each field can be used for.</span></span>

<span data-ttu-id="d7dfa-155">Per semplificare ulteriormente la creazione degli endpoint JEA, vedere il [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) che offre un'interfaccia utente grafica con cui è possibile creare file di configurazione di sessione e file di capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-155">To make authoring JEA endpoints even easier, check out the [JEA Toolkit Helper](http://blogs.technet.com/b/privatecloud/archive/2015/12/20/introducing-the-updated-jea-helper-tool.aspx) which provides a GUI with which you can author Session Configuration and Role Capability files.</span></span>
<span data-ttu-id="d7dfa-156">È supportata anche la generazione di capacità del ruolo in base ai registri di PowerShell per iniziare a gestire i comandi eseguiti regolarmente dagli utenti per svolgere le proprie attività.</span><span class="sxs-lookup"><span data-stu-id="d7dfa-156">It even supports generating Role Capabilities based on PowerShell logs to start you off with the commands your users regularly run to get their jobs done.</span></span>

