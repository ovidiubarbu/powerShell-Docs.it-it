---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: concetti principali usati in questa guida
ms.technology: powershell
ms.openlocfilehash: 873ab19fdf43ec4ac41cc546aa94b64fbc607984
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="key-concepts-used-throughout-this-guide"></a><span data-ttu-id="c7b0d-103">Concetti principali usati in questa guida</span><span class="sxs-lookup"><span data-stu-id="c7b0d-103">Key Concepts Used Throughout This Guide</span></span>
<span data-ttu-id="c7b0d-104">**Che cos'è esattamente JEA?**</span><span class="sxs-lookup"><span data-stu-id="c7b0d-104">**What exactly is JEA?**</span></span>

<span data-ttu-id="c7b0d-105">JEA è un'estensione degli [endpoint vincolati](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) di PowerShell che aggiunge definizioni di ruoli, account virtuali e diversi altri miglioramenti per semplificare ulteriormente il blocco degli endpoint di gestione.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-105">JEA is an extension of PowerShell [constrained endpoints](http://blogs.technet.com/b/heyscriptingguy/archive/2014/03/31/introduction-to-powershell-endpoints.aspx) that adds in role definitions, virtual accounts, and several other improvements to make it even easier to lock down your management endpoints.</span></span>
<span data-ttu-id="c7b0d-106">Un endpoint JEA è costituito da un file di configurazione di sessione di PowerShell e da uno o più file di capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-106">A JEA endpoint consists of a PowerShell Session Configuration file and one or more Role Capability files.</span></span>

<span data-ttu-id="c7b0d-107">**Che cosa sono i file di configurazione di sessione e i file di capacità del ruolo?**</span><span class="sxs-lookup"><span data-stu-id="c7b0d-107">**What are Session Configuration and Role Capability files?**</span></span>

<span data-ttu-id="c7b0d-108">I file di configurazione di sessione di PowerShell (estensione pssc) specificano *chi* può connettersi a un endpoint di PowerShell e *come* viene configurato l'endpoint.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-108">PowerShell Session Configuration files (.pssc) define *who* can connect to a PowerShell endpoint and *how* it is configured.</span></span>
<span data-ttu-id="c7b0d-109">Consentono di mappare utenti e gruppi di sicurezza a ruoli di gestione specifici e di configurare impostazioni globali come gli account virtuali e i criteri di trascrizione.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-109">This is where you would map users and security groups to specific management roles and configure global settings like virtual accounts and transcription policies.</span></span>
<span data-ttu-id="c7b0d-110">I file di configurazione di sessione sono specifici di ogni computer e questo consente di controllare l'accesso in base al computer, se necessario.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-110">Session configuration files are specific to each machine, which allows you to control access on a per-machine basis if desired.</span></span>

<span data-ttu-id="c7b0d-111">I file di capacità del ruolo di PowerShell (estensione psrc) definiscono *che cosa* sono in grado di eseguire nel sistema gli utenti appartenenti a un ruolo.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-111">PowerShell Role Capability files (.psrc) define *what* users belonging to a role are able to do on the system.</span></span>
<span data-ttu-id="c7b0d-112">Consentono di limitare i cmdlet, le funzioni, i provider e i programmi esterni che un utente può usare nella sessione di JEA.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-112">Here, you can restrict which cmdlets, functions, providers, and external programs a user may use in their JEA session.</span></span>
<span data-ttu-id="c7b0d-113">I file capacità del ruolo sono spesso generici per il ruolo servito (amministratore DNS, supporto tecnico di livello 1, controllo di sola lettura dell'inventario e così via) e appartengono ai moduli di PowerShell, rendendo più semplice la condivisione nel proprio ambiente e con altri utenti.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-113">Role Capability files are often generic for the role being served (DNS admin, level 1 helpdesk, read-only inventory auditing, etc.) and belong to PowerShell modules, making it easy to share them across your environment and with others.</span></span>

<span data-ttu-id="c7b0d-114">**In che modo JEA usa gli account virtuali?**</span><span class="sxs-lookup"><span data-stu-id="c7b0d-114">**How does JEA leverage virtual accounts?**</span></span>

<span data-ttu-id="c7b0d-115">Nel file di configurazione di sessione di PowerShell è possibile configurare le sessioni JEA per usare gli account virtuali "RunAs".</span><span class="sxs-lookup"><span data-stu-id="c7b0d-115">In the PowerShell Session Configuration file, you can configure JEA sessions to use virtual "run as" accounts.</span></span>
<span data-ttu-id="c7b0d-116">Gli account virtuali sono account monouso con privilegi eseguiti per la connessione di un utente specifico in una sessione specifica nel cui contesto vengono eseguiti i comandi dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-116">Virtual accounts are one-time privileged accounts spun up for the specific connecting user in that specific session under which context the user's commands are executed.</span></span>
<span data-ttu-id="c7b0d-117">Gli account virtuali appartengono al gruppo di sicurezza "Administrators" locale per impostazione predefinita, ma se necessario possono essere configurati in modo da appartenere solo a gruppi di sicurezza specificati.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-117">Virtual accounts belong to the local "Administrators" security group by default, but can optionally be configured to only belong to security groups you specify.</span></span>

<span data-ttu-id="c7b0d-118">**Comunicazione remota di PowerShell**: consente di eseguire i comandi di PowerShell nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-118">**PowerShell Remoting**: PowerShell remoting allows you to run PowerShell commands against remote machines.</span></span>
<span data-ttu-id="c7b0d-119">È possibile lavorare con uno o più computer e usare connessioni temporanee o permanenti.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-119">You can operate against one or many computers, and use either temporary or persistent connections.</span></span>
<span data-ttu-id="c7b0d-120">In questa demo la comunicazione remota viene eseguita nel computer locale con una sessione interattiva.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-120">In this demo, you remoted into your local machine with an interactive session.</span></span>
<span data-ttu-id="c7b0d-121">JEA limita le funzionalità disponibili attraverso la comunicazione remota di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-121">JEA restricts the functionality available through PowerShell remoting.</span></span>
<span data-ttu-id="c7b0d-122">Per altre informazioni sulla comunicazione remota di PowerShell, eseguire `Get-Help about_Remote`.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-122">For more information about PowerShell remoting, run `Get-Help about_Remote`.</span></span>

<span data-ttu-id="c7b0d-123">**Utente "RunAs"**: quando si usa JEA, un utente non amministratore viene eseguito come "account virtuale" con privilegi.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-123">**"RunAs" User**: When using JEA, a non-administrator "runs as" a privileged "Virtual Account."</span></span>
<span data-ttu-id="c7b0d-124">L'account virtuale esiste solo durante la sessione remota.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-124">The Virtual Account only lasts the duration of the remote session.</span></span>
<span data-ttu-id="c7b0d-125">Vale a dire, viene creato quando un utente si connette all'endpoint ed eliminato quando l'utente termina la sessione.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-125">That is to say, it is created when a user connects to the endpoint, and destroyed when the user ends the session.</span></span>
<span data-ttu-id="c7b0d-126">Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators locale.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-126">By default, the Virtual Account is a member of the local Administrators group.</span></span>
<span data-ttu-id="c7b0d-127">In un controller di dominio è un membro del gruppo Domain Admins.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-127">On a domain controller, it is a member of Domain Admins.</span></span>
<span data-ttu-id="c7b0d-128">Gli account virtuali sono locali nel computer in cui vengono creati e non usufruiscono di autorizzazioni di fuori di tale computer.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-128">Virtual Accounts are local to the machine on which they are created, and do not have permissions outside of that machine.</span></span>
<span data-ttu-id="c7b0d-129">Ciò significa che non vengono registrati in Active Directory e che non viene assegnato alcun RID.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-129">This means that they are not registered in Active Directory (no RID is assigned).</span></span>
<span data-ttu-id="c7b0d-130">Inoltre, se un comando o script consentito tenta di accedere alle risorse esterne al computer locale, accederà a tali risorse con l'identità del computer, non l'identità dell'account virtuale.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-130">Additionally, if an allowed command/script tries to access resources outside of the local machine, it will be accessing those resources under the machine's identity, not the Virtual Account identity.</span></span>

<span data-ttu-id="c7b0d-131">**Utente "connesso"**: l'utente non amministratore che si connette all'endpoint JEA e a cui vengono assegnati i ruoli.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-131">**"Connected" User**: The non-administrator user who connects to the JEA endpoint and to whom roles are assigned.</span></span>
<span data-ttu-id="c7b0d-132">I comandi eseguiti da questo utente vengono eseguiti nel contesto dell'utente RunAs o dell'account virtuale.</span><span class="sxs-lookup"><span data-stu-id="c7b0d-132">Any commands this user runs are run under the context of the RunAs User or virtual account.</span></span>

