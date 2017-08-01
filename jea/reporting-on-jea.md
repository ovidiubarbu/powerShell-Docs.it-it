---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: creazione di report per JEA
ms.technology: powershell
ms.openlocfilehash: 3e7bd2755281f491bba8a905df018fb2e1cac6ff
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="reporting-on-jea"></a><span data-ttu-id="c8eef-103">Creazione di report per JEA</span><span class="sxs-lookup"><span data-stu-id="c8eef-103">Reporting on JEA</span></span>
<span data-ttu-id="c8eef-104">Poiché JEA consente agli utenti senza privilegi l'esecuzione in un contesto con privilegi, la registrazione e il controllo sono estremamente importanti.</span><span class="sxs-lookup"><span data-stu-id="c8eef-104">Because JEA allows non-privileged users to run in a privileged context, logging and auditing are extremely important.</span></span>
<span data-ttu-id="c8eef-105">In questa sezione vengono illustrati gli strumenti che agevolano le procedure di registrazione e creazione di report.</span><span class="sxs-lookup"><span data-stu-id="c8eef-105">In this section, we'll run through the tools you can use to help you with logging and reporting.</span></span>

## <a name="reporting-on-jea-actions"></a><span data-ttu-id="c8eef-106">Creazione di report per azioni JEA</span><span class="sxs-lookup"><span data-stu-id="c8eef-106">Reporting on JEA Actions</span></span>
### <a name="over-the-shoulder-transcription"></a><span data-ttu-id="c8eef-107">Trascrizione over-the-shoulder</span><span class="sxs-lookup"><span data-stu-id="c8eef-107">Over-the-Shoulder Transcription</span></span>
<span data-ttu-id="c8eef-108">Uno dei modi più rapidi per ottenere un riepilogo delle operazioni eseguite in una sessione di PowerShell è osservare da vicino l'attività dell'utente.</span><span class="sxs-lookup"><span data-stu-id="c8eef-108">One of the quickest ways to get a summary of what's happening in a PowerShell session is to look over the shoulder of the person typing.</span></span>
<span data-ttu-id="c8eef-109">Vengono visualizzati i comandi in uso, l'output di tali comandi e tutto appare in ordine.</span><span class="sxs-lookup"><span data-stu-id="c8eef-109">You see their commands, the output of those commands, and all is well.</span></span>
<span data-ttu-id="c8eef-110">Oppure no, ma almeno si viene a sapere.</span><span class="sxs-lookup"><span data-stu-id="c8eef-110">Or it's not, but at least you'll know.</span></span>
<span data-ttu-id="c8eef-111">Le trascrizioni di PowerShell sono progettate in modo da offrire una visualizzazione simile al termine dell'attività.</span><span class="sxs-lookup"><span data-stu-id="c8eef-111">PowerShell transcription is designed to give you a similar view after the fact.</span></span>

<span data-ttu-id="c8eef-112">Quando si usa il campo "TranscriptDirectory" nella configurazione di sessione, PowerShell registra automaticamente una trascrizione di tutte le azioni intraprese in una determinata sessione.</span><span class="sxs-lookup"><span data-stu-id="c8eef-112">When using the "TranscriptDirectory" field in your Session Configuration, PowerShell will automatically record a transcript of all actions taken in a given session.</span></span>
<span data-ttu-id="c8eef-113">Le trascrizioni dalle sessioni sono contenute in questo documento: "$env: ProgramData\JEAConfiguration\Transcripts"</span><span class="sxs-lookup"><span data-stu-id="c8eef-113">You can find transcripts from your sessions in this document here: "$env:ProgramData\JEAConfiguration\Transcripts"</span></span>

<span data-ttu-id="c8eef-114">Come si può vedere, la trascrizione registra informazioni sull'utente "connesso", l'utente "RunAs", i comandi eseguiti nella sessione e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="c8eef-114">As you can tell, the transcript records information about the "Connected" user, the "Run As" user, the commands run in the session, and more.</span></span>
<span data-ttu-id="c8eef-115">Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="c8eef-115">For more information about PowerShell transcription, check out [this blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>

### <a name="powershell-event-logs"></a><span data-ttu-id="c8eef-116">Registri eventi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="c8eef-116">PowerShell Event Logs</span></span>
<span data-ttu-id="c8eef-117">Dopo aver attivato la registrazione dei moduli, anche tutte le azioni di PowerShell vengono registrate nei normali registri eventi di Windows.</span><span class="sxs-lookup"><span data-stu-id="c8eef-117">When you have module logging turned on, all PowerShell actions are also recorded in regular Windows Event logs.</span></span>
<span data-ttu-id="c8eef-118">Questa attività è leggermente più complessa da gestire rispetto alle trascrizioni, ma può essere utile il livello di dettaglio che offre.</span><span class="sxs-lookup"><span data-stu-id="c8eef-118">This is slightly messier to deal with when compared to transcripts, but the level of detail it gives you can be useful.</span></span>

<span data-ttu-id="c8eef-119">Nel registro operativo "PowerShell", l'ID evento 4104 registrerà ogni comando richiamato se è stata abilitata la registrazione dei moduli.</span><span class="sxs-lookup"><span data-stu-id="c8eef-119">In the "PowerShell" operational log, Event ID 4104 will record each command invoked if you have enabled module logging.</span></span>

### <a name="other-event-logs"></a><span data-ttu-id="c8eef-120">Altri registri eventi</span><span class="sxs-lookup"><span data-stu-id="c8eef-120">Other Event Logs</span></span>
<span data-ttu-id="c8eef-121">A differenza dei registri e delle trascrizioni di PowerShell, altri meccanismi di registrazione non acquisiscono l'utente "connesso".</span><span class="sxs-lookup"><span data-stu-id="c8eef-121">Unlike PowerShell logs and transcripts, other logging mechanisms will not capture the "Connected User".</span></span>
<span data-ttu-id="c8eef-122">È necessario stabilire una certa correlazione tra gli altri registri e i registri di PowerShell per la corrispondenza tra le azioni intraprese.</span><span class="sxs-lookup"><span data-stu-id="c8eef-122">You will need to do some correlation between other logs and PowerShell logs to match up actions taken.</span></span>

<span data-ttu-id="c8eef-123">Nel registro operativo di "Gestione remota Windows", l'ID evento 193 registrerà il SID e il nome dell'utente connesso, nonché il SID dell'account virtuale RunAs per agevolare questa correlazione.</span><span class="sxs-lookup"><span data-stu-id="c8eef-123">In the "Windows Remote Management" operational log, Event ID 193 will record the Connecting User's SID and Name, as well as the RunAs Virtual Account's SID to assist with this correlation.</span></span>
<span data-ttu-id="c8eef-124">Come forse si è notato, il nome dell'account virtuale RunAs include alla fine il dominio e il nome utente dell'utente connesso.</span><span class="sxs-lookup"><span data-stu-id="c8eef-124">You may have also noticed that the name of the RunAs Virtual Account includes the connecting user's domain and username at the end.</span></span>

## <a name="reporting-on-jea-configuration"></a><span data-ttu-id="c8eef-125">Creazione di report per la configurazione JEA</span><span class="sxs-lookup"><span data-stu-id="c8eef-125">Reporting on JEA Configuration</span></span>
### <a name="get-pssessionconfiguration"></a><span data-ttu-id="c8eef-126">Get-PSSessionConfiguration</span><span class="sxs-lookup"><span data-stu-id="c8eef-126">Get-PSSessionConfiguration</span></span>
<span data-ttu-id="c8eef-127">Per segnalare con precisione lo stato dell'ambiente, è importante sapere quanti endpoint JEA sono impostati sul computer.</span><span class="sxs-lookup"><span data-stu-id="c8eef-127">In order to accurately report on the state of your environment, it's important to know how many JEA endpoints you have set up on your machine.</span></span>
<span data-ttu-id="c8eef-128">`Get-PSSessionConfiguration` esegue questa operazione.</span><span class="sxs-lookup"><span data-stu-id="c8eef-128">`Get-PSSessionConfiguration` does just that.</span></span>

### <a name="get-pssessioncapability"></a><span data-ttu-id="c8eef-129">Get-PSSessionCapability</span><span class="sxs-lookup"><span data-stu-id="c8eef-129">Get-PSSessionCapability</span></span>
<span data-ttu-id="c8eef-130">Creare manualmente report sulle capacità di ogni utente usando un endpoint JEA può essere molto complesso.</span><span class="sxs-lookup"><span data-stu-id="c8eef-130">Manually reporting on the capabilities of any given user through a JEA endpoint can be quite complex.</span></span>
<span data-ttu-id="c8eef-131">Potenzialmente occorre controllare diverse capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="c8eef-131">You would potentially need to inspect several role capabilities.</span></span>
<span data-ttu-id="c8eef-132">Fortunatamente il cmdlet "Get-PSSessionCapability" esegue questa operazione.</span><span class="sxs-lookup"><span data-stu-id="c8eef-132">Fortunately, the "Get-PSSessionCapability" cmdlet does this.</span></span>

<span data-ttu-id="c8eef-133">Per testarlo, eseguire il comando seguente dal prompt dei comandi di PowerShell come amministratore:</span><span class="sxs-lookup"><span data-stu-id="c8eef-133">To test this out, run the following command from an administrator PowerShell prompt:</span></span>
```PowerShell
Get-PSSessionCapability -Username 'CONTOSO\OperatorUser' -ConfigurationName JEADemo
```

