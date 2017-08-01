---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ricreare l&quot;endpoint dimostrativo
ms.technology: powershell
ms.openlocfilehash: 4a56272b6f995500d443d441f5e03db85dac6f96
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
ms.translationtype: HT
ms.contentlocale: it-IT
---
# <a name="remake-the-demo-endpoint"></a><span data-ttu-id="8b15a-103">Ricreare l'endpoint dimostrativo</span><span class="sxs-lookup"><span data-stu-id="8b15a-103">Remake the Demo Endpoint</span></span>
<span data-ttu-id="8b15a-104">Questa sezione spiega come generare una replica esatta dell'endpoint dimostrativo usato nella sezione precedente.</span><span class="sxs-lookup"><span data-stu-id="8b15a-104">In this section, you will learn how to generate an exact replica of the demo endpoint you used in the above section.</span></span>
<span data-ttu-id="8b15a-105">Verranno introdotti i concetti essenziali per la comprensione di JEA, incluse le configurazioni di sessione di PowerShell e le capacità del ruolo.</span><span class="sxs-lookup"><span data-stu-id="8b15a-105">This will introduce core concepts that are necessary to understand JEA, including PowerShell Session Configurations and Role Capabilities.</span></span>

## <a name="powershell-session-configurations"></a><span data-ttu-id="8b15a-106">Configurazioni di sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b15a-106">PowerShell Session Configurations</span></span>
<span data-ttu-id="8b15a-107">Se è stato usato JEA nella sezione precedente, la procedura è iniziata con l'esecuzione di questo comando:</span><span class="sxs-lookup"><span data-stu-id="8b15a-107">When you used JEA in the above section, you started by running the following command:</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

<span data-ttu-id="8b15a-108">Benché nella maggior parte dei casi i parametri siano di chiara interpretazione, il parametro *ConfigurationName* inizialmente può generare confusione.</span><span class="sxs-lookup"><span data-stu-id="8b15a-108">While most of the parameters are self-explanatory, the *ConfigurationName* parameter may seem confusing at first.</span></span>
<span data-ttu-id="8b15a-109">Il parametro specifica la configurazione di sessione di PowerShell a cui si è connessi.</span><span class="sxs-lookup"><span data-stu-id="8b15a-109">That parameter specified the PowerShell Session Configuration to which you were connecting.</span></span>

<span data-ttu-id="8b15a-110">Il termine *configurazione di sessione di PowerShell* indica un endpoint di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-110">*PowerShell Session Configuration* is a fancy term for a PowerShell endpoint.</span></span>
<span data-ttu-id="8b15a-111">In senso figurato, si tratta del "posto" in cui gli utenti si connettono e accedono alla funzionalità PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-111">It is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="8b15a-112">In base all'impostazione della configurazione di sessione, offre funzionalità diverse per la connessione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="8b15a-112">Based on how you set up a Session Configuration, it can provide different functionality to connecting users.</span></span>
<span data-ttu-id="8b15a-113">Per JEA, le configurazioni di sessione vengono usate per circoscrivere PowerShell a un set limitato di funzionalità e per l'esecuzione come account virtuale con privilegi.</span><span class="sxs-lookup"><span data-stu-id="8b15a-113">For JEA, we use Session Configurations to restrict PowerShell to a limited set of functionality and to run as a privileged virtual account.</span></span>

<span data-ttu-id="8b15a-114">Nel computer sono già disponibili alcune configurazioni di sessione di PowerShell registrate, ognuna impostata in modo leggermente diverso.</span><span class="sxs-lookup"><span data-stu-id="8b15a-114">You already have several registered PowerShell Session Configurations on your machine, each set up slightly differently.</span></span>
<span data-ttu-id="8b15a-115">La maggior parte di esse è inclusa in Windows, ma la configurazione di sessione "JEA_Demo" è stata impostata nella sezione dei [prerequisiti](prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="8b15a-115">Most of them come with Windows, but the "JEA_Demo" Session Configuration was set up in the [prerequisites](prerequisites.md) section.</span></span>
<span data-ttu-id="8b15a-116">Per visualizzare tutte le configurazioni di sessione registrate, eseguire il comando seguente in un prompt di PowerShell per amministratore:</span><span class="sxs-lookup"><span data-stu-id="8b15a-116">You can see all registered Session Configurations by running the following command in an Administrator PowerShell prompt:</span></span>

```PowerShell
Get-PSSessionConfiguration
```

## <a name="powershell-session-configuration-files"></a><span data-ttu-id="8b15a-117">File di configurazione di sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b15a-117">PowerShell Session Configuration Files</span></span>
<span data-ttu-id="8b15a-118">È possibile creare nuove configurazioni di sessione registrando nuovi *file di configurazione di sessione di PowerShell*.</span><span class="sxs-lookup"><span data-stu-id="8b15a-118">You can make new Session Configurations by registering new *PowerShell Session Configuration Files*.</span></span>
<span data-ttu-id="8b15a-119">I file di configurazione di sessione hanno estensione "pssc"</span><span class="sxs-lookup"><span data-stu-id="8b15a-119">Session Configuration Files have ".pssc" file extensions.</span></span>
<span data-ttu-id="8b15a-120">e possono essere creati con il cmdlet New-PSSessionConfigurationFile.</span><span class="sxs-lookup"><span data-stu-id="8b15a-120">You can generate Session Configuration Files with the New-PSSessionConfigurationFile cmdlet.</span></span>

<span data-ttu-id="8b15a-121">A questo punto è possibile creare e registrare una nuova configurazione di sessione per JEA.</span><span class="sxs-lookup"><span data-stu-id="8b15a-121">Next, you are going to create and register a new Session Configuration for JEA.</span></span>

## <a name="generate-and-modify-your-powershell-session-configuration"></a><span data-ttu-id="8b15a-122">Generare e modificare la configurazione di sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b15a-122">Generate and Modify your PowerShell Session Configuration</span></span>
<span data-ttu-id="8b15a-123">Eseguire il comando seguente per generare un file "scheletro" per la configurazione di sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-123">Run the following command to generate a PowerShell Session Configuration "skeleton" file.</span></span>

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> <span data-ttu-id="8b15a-124">**Suggerimento:** per impostazione predefinita, solo le impostazioni di configurazione più comuni vengono incluse nel file scheletro.</span><span class="sxs-lookup"><span data-stu-id="8b15a-124">**TIP:** Only the most common configuration settings are included in the skeleton file by default.</span></span>
> <span data-ttu-id="8b15a-125">Usare il parametro `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.</span><span class="sxs-lookup"><span data-stu-id="8b15a-125">Use the `-Full` parameter to include all applicable settings in the generated PSSC.</span></span>

<span data-ttu-id="8b15a-126">Aprire il file in PowerShell ISE o in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="8b15a-126">Open the file in PowerShell ISE, or your favorite text editor.</span></span>

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="8b15a-127">Aggiornare i campi seguenti nel file con i valori seguenti (ricordarsi di sostituire i valori nel proprio gruppo di sicurezza non amministratore):</span><span class="sxs-lookup"><span data-stu-id="8b15a-127">Update the following fields in the file with the values below (remember to substitute in your own non-administrator security group):</span></span>

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

<span data-ttu-id="8b15a-128">Le voci hanno il significato seguente:</span><span class="sxs-lookup"><span data-stu-id="8b15a-128">Here is what each of those entries mean:</span></span>

1.  <span data-ttu-id="8b15a-129">Il campo *SessionType* definisce le impostazioni predefinite da usare con questo endpoint.</span><span class="sxs-lookup"><span data-stu-id="8b15a-129">The *SessionType* field defines preset default settings to use with this endpoint.</span></span>
<span data-ttu-id="8b15a-130">*RestrictedRemoteServer* definisce le impostazioni minime necessarie per la gestione remota.</span><span class="sxs-lookup"><span data-stu-id="8b15a-130">*RestrictedRemoteServer* defines the minimal settings necessary for remote management.</span></span>
<span data-ttu-id="8b15a-131">Per impostazione predefinita, un endpoint *RestrictedRemoteServer* espone Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.</span><span class="sxs-lookup"><span data-stu-id="8b15a-131">By default, a *RestrictedRemoteServer* endpoint will expose Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host, and Out-Default.</span></span>
<span data-ttu-id="8b15a-132">*ExecutionPolicy* viene impostato su *RemoteSigned* e *LanguageMode* su *NoLanguage*.</span><span class="sxs-lookup"><span data-stu-id="8b15a-132">It will set the *ExecutionPolicy* to *RemoteSigned*, and the *LanguageMode* to *NoLanguage*.</span></span>
<span data-ttu-id="8b15a-133">L'effetto di queste impostazioni è un punto di partenza minimo e sicuro per la configurazione dell'endpoint.</span><span class="sxs-lookup"><span data-stu-id="8b15a-133">The net effect of these settings is a secure and minimal starting point for configuring your endpoint.</span></span>

2.  <span data-ttu-id="8b15a-134">Il campo *RoleDefinitions* assegna le capacità del ruolo a gruppi specifici.</span><span class="sxs-lookup"><span data-stu-id="8b15a-134">The *RoleDefinitions* field assigns Role Capabilities to specific groups.</span></span>
<span data-ttu-id="8b15a-135">Definisce chi fa cosa come un account con privilegi.</span><span class="sxs-lookup"><span data-stu-id="8b15a-135">It defines who can do what as a privileged account.</span></span>
<span data-ttu-id="8b15a-136">Con questo campo è possibile specificare le funzionalità disponibili per qualsiasi utente connesso in base all'appartenenza al gruppo.</span><span class="sxs-lookup"><span data-stu-id="8b15a-136">With this field, you can specify the functionality available to any connecting user based on group membership.</span></span>
<span data-ttu-id="8b15a-137">Questo è l'elemento di base della funzionalità RBAC di JEA.</span><span class="sxs-lookup"><span data-stu-id="8b15a-137">This is the core of JEA's RBAC functionality.</span></span>
<span data-ttu-id="8b15a-138">In questo esempio, si espone la capacità del ruolo "Maintenance" predefinita per i membri del gruppo "Contoso\JEA_NonAdmin_Operator".</span><span class="sxs-lookup"><span data-stu-id="8b15a-138">In this example, you are exposing the pre-made "Maintenance" RoleCapability to members of the "Contoso\JEA_NonAdmin_Operator" group.</span></span>

3.  <span data-ttu-id="8b15a-139">Il campo *RunAsVirtualAccount* indica che PowerShell deve "essere eseguito come" account virtuale per questo endpoint.</span><span class="sxs-lookup"><span data-stu-id="8b15a-139">The *RunAsVirtualAccount* field indicates that PowerShell should "run as" a Virtual Account at this endpoint.</span></span>
<span data-ttu-id="8b15a-140">Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators incorporato.</span><span class="sxs-lookup"><span data-stu-id="8b15a-140">By default, the Virtual Account is a member of the built in Administrators group.</span></span>
<span data-ttu-id="8b15a-141">In un controller di dominio è anche un membro del gruppo di amministratori del dominio per impostazione predefinita.</span><span class="sxs-lookup"><span data-stu-id="8b15a-141">On a domain controller, it is also a member of the Domain Administrators group by default.</span></span>
<span data-ttu-id="8b15a-142">Più avanti in questa guida si apprenderà come personalizzare i privilegi dell'account virtuale.</span><span class="sxs-lookup"><span data-stu-id="8b15a-142">Later in this guide, you will learn how to customize the privileges of the Virtual Account.</span></span>

4.  <span data-ttu-id="8b15a-143">Il campo *TranscriptDirectory* indica dove vengono salvate le trascrizioni "over-the-shoulder" di PowerShell dopo ogni sessione remota.</span><span class="sxs-lookup"><span data-stu-id="8b15a-143">The *TranscriptDirectory* field defines where "over-the-shoulder" PowerShell transcripts are saved after each remote session.</span></span>
<span data-ttu-id="8b15a-144">Queste trascrizioni consentono di esaminare le azioni eseguite in ogni sessione in un formato leggibile.</span><span class="sxs-lookup"><span data-stu-id="8b15a-144">These transcripts allow you to inspect the actions taken in each session in a readable way.</span></span>
<span data-ttu-id="8b15a-145">Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span><span class="sxs-lookup"><span data-stu-id="8b15a-145">For more information about PowerShell transcripts, check out this [blog post](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).</span></span>
<span data-ttu-id="8b15a-146">Nota: anche la normale registrazione degli eventi di Windows acquisisce informazioni su ciò che ogni utente esegue con PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-146">Note: regular Windows Eventing also captures information about what each user ran with PowerShell.</span></span>
<span data-ttu-id="8b15a-147">Le trascrizioni sono semplicemente un po' più leggibili.</span><span class="sxs-lookup"><span data-stu-id="8b15a-147">Transcripts are just a bit more readable.</span></span>

<span data-ttu-id="8b15a-148">Infine, salvare le modifiche apportate a *JEADemo2.pssc*.</span><span class="sxs-lookup"><span data-stu-id="8b15a-148">Finally, save your changes to *JEADemo2.pssc*.</span></span>

## <a name="apply-the-powershell-session-configuration"></a><span data-ttu-id="8b15a-149">Applicare la configurazione di sessione di PowerShell</span><span class="sxs-lookup"><span data-stu-id="8b15a-149">Apply the PowerShell Session Configuration</span></span>

<span data-ttu-id="8b15a-150">Per creare un endpoint da un file di configurazione di sessione, è necessario registrare il file.</span><span class="sxs-lookup"><span data-stu-id="8b15a-150">To create an endpoint from a Session Configuration file, you need to register the file.</span></span>
<span data-ttu-id="8b15a-151">Questa operazione richiede alcune informazioni:</span><span class="sxs-lookup"><span data-stu-id="8b15a-151">This requires a few pieces of information:</span></span>

1. <span data-ttu-id="8b15a-152">Il percorso del file di configurazione della sessione.</span><span class="sxs-lookup"><span data-stu-id="8b15a-152">The path to the Session Configuration file.</span></span>
2. <span data-ttu-id="8b15a-153">Il nome della configurazione di sessione registrata.</span><span class="sxs-lookup"><span data-stu-id="8b15a-153">The name of your registered Session Configuration.</span></span> <span data-ttu-id="8b15a-154">Si tratta dello stesso nome immesso dagli utenti per il parametro "ConfigurationName" quando si connettono all'endpoint con `Enter-PSSession` o `New-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="8b15a-154">This is the same name users provide to the "ConfigurationName" parameter when they connect to your endpoint with `Enter-PSSession` or `New-PSSession`.</span></span>

<span data-ttu-id="8b15a-155">Per registrare la configurazione di sessione nel computer locale, eseguire il comando seguente:</span><span class="sxs-lookup"><span data-stu-id="8b15a-155">To register the Session Configuration on your local machine, run the following command:</span></span>

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

<span data-ttu-id="8b15a-156">Congratulazioni,</span><span class="sxs-lookup"><span data-stu-id="8b15a-156">Congratulations!</span></span> <span data-ttu-id="8b15a-157">l'impostazione dell'endpoint JEA è stata completata.</span><span class="sxs-lookup"><span data-stu-id="8b15a-157">You have set up your JEA endpoint.</span></span>

## <a name="test-out-your-endpoint"></a><span data-ttu-id="8b15a-158">Testare l'endpoint</span><span class="sxs-lookup"><span data-stu-id="8b15a-158">Test Out Your Endpoint</span></span>
<span data-ttu-id="8b15a-159">Eseguire di nuovo i passaggi riportati nella sezione [Uso di JEA](using-jea.md) per il nuovo endpoint per verificare se funziona come previsto.</span><span class="sxs-lookup"><span data-stu-id="8b15a-159">Re-run the steps listed in the [Using JEA](using-jea.md) section against your new endpoint to confirm it is operating as intended.</span></span>
<span data-ttu-id="8b15a-160">Assicurarsi di usare il nome del nuovo endpoint (JEADemo2) quando si specifica il nome della configurazione per `Enter-PSSession`.</span><span class="sxs-lookup"><span data-stu-id="8b15a-160">Be sure to use the new endpoint name (JEADemo2) when providing the configuration name to `Enter-PSSession`.</span></span>

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## <a name="key-concepts"></a><span data-ttu-id="8b15a-161">Concetti chiave</span><span class="sxs-lookup"><span data-stu-id="8b15a-161">Key Concepts</span></span>
<span data-ttu-id="8b15a-162">**Configurazione di sessione di PowerShell**: detta anche *Endpoint di PowerShell*, è il "posto" in senso figurato dove gli utenti si connettono e accedono alle funzionalità di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-162">**PowerShell Session Configuration**: Sometimes referred to as *PowerShell Endpoint*, this is the figurative "place" where users connect and get access to PowerShell functionality.</span></span>
<span data-ttu-id="8b15a-163">Per visualizzare le configurazioni di sessione registrate nel sistema eseguire `Get-PSSessionConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="8b15a-163">You can list the registered Session Configurations on your system by running `Get-PSSessionConfiguration`.</span></span>
<span data-ttu-id="8b15a-164">Quando è configurata in modo specifico, una configurazione di sessione di PowerShell può essere definita *Endpoint JEA*.</span><span class="sxs-lookup"><span data-stu-id="8b15a-164">When configured in a specific way, a PowerShell Session Configuration can be called a *JEA Endpoint*.</span></span>

<span data-ttu-id="8b15a-165">**File di configurazione di sessione di PowerShell (con estensione pssc)**: un file che, quando è registrato, definisce le impostazioni per una configurazione di sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-165">**PowerShell Session Configuration File (.pssc)**: A file that, when registered, defines settings for a PowerShell Session Configuration.</span></span>
<span data-ttu-id="8b15a-166">Contiene le specifiche per i ruoli utente che possono connettersi all'endpoint, l'account virtuale "RunAs" e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="8b15a-166">It contains specifications for user roles that can connect to the endpoint, the "run as" Virtual Account, and more.</span></span>     

<span data-ttu-id="8b15a-167">**Definizioni ruolo**: campo del file di configurazione di sessione che definisce le capacità del ruolo per la connessione degli utenti.</span><span class="sxs-lookup"><span data-stu-id="8b15a-167">**Role Definitions**: The field in a Session Configuration File that defines the Role Capabilities granted to connecting users.</span></span>
<span data-ttu-id="8b15a-168">Definisce *chi* può fare *cosa* come account con privilegi.</span><span class="sxs-lookup"><span data-stu-id="8b15a-168">It defines *who* can do *what* as a privileged account.</span></span>
<span data-ttu-id="8b15a-169">Questo è l'elemento di base delle funzionalità RBAC di JEA.</span><span class="sxs-lookup"><span data-stu-id="8b15a-169">This is the core of JEA's RBAC capabilities.</span></span>

<span data-ttu-id="8b15a-170">**SessionType**: campo del file di configurazione di sessione che rappresenta le impostazioni predefinite per una configurazione di sessione.</span><span class="sxs-lookup"><span data-stu-id="8b15a-170">**SessionType**: A field in a Session Configuration File that represents default settings for a Session Configuration.</span></span>
<span data-ttu-id="8b15a-171">Per gli endpoint JEA, deve essere impostato su RestrictedRemoteServer.</span><span class="sxs-lookup"><span data-stu-id="8b15a-171">For JEA endpoints, this must be set to RestrictedRemoteServer.</span></span>

<span data-ttu-id="8b15a-172">**Trascrizione PowerShell**: file contenente una visualizzazione "over-the-shoulder" di una sessione di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8b15a-172">**PowerShell Transcript**: A file containing an "over-the-shoulder" view of a PowerShell session.</span></span>
<span data-ttu-id="8b15a-173">È possibile impostare PowerShell in modo che generi le trascrizioni per le sessioni JEA usando il campo TranscriptDirectory.</span><span class="sxs-lookup"><span data-stu-id="8b15a-173">You can set PowerShell to generate transcripts for JEA sessions using the TranscriptDirectory field.</span></span>
<span data-ttu-id="8b15a-174">Per altre informazioni sulle trascrizioni, vedere questo [post del blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span><span class="sxs-lookup"><span data-stu-id="8b15a-174">For more information on transcripts, check out this [blog post](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).</span></span>

