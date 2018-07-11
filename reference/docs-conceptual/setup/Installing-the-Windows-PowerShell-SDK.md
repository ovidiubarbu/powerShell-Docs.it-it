---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Installazione di Windows PowerShell SDK
ms.assetid: c3636b45-61aa-4720-85f0-58312c4fc8f9
ms.openlocfilehash: fa876bac0c1afac24f93d11dd2e7ecfb1165cf5f
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893539"
---
# <a name="installing-the-windows-powershell-sdk"></a><span data-ttu-id="d7af1-103">Installazione di Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="d7af1-103">Installing the Windows PowerShell SDK</span></span>

<span data-ttu-id="d7af1-104">L'argomento seguente descrive come installare PowerShell SDK in diverse versioni di Windows.</span><span class="sxs-lookup"><span data-stu-id="d7af1-104">The following topic describes how to install the PowerShell SDK on different versions of Windows.</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-8-and-windows-server-2012"></a><span data-ttu-id="d7af1-105">Installazione di Windows PowerShell 3.0 SDK in Windows 8 e Windows Server 2012</span><span class="sxs-lookup"><span data-stu-id="d7af1-105">Installing Windows PowerShell 3.0 SDK for Windows 8 and Windows Server 2012</span></span>

<span data-ttu-id="d7af1-106">Windows PowerShell 3.0 viene installato automaticamente con Windows 8 e Windows Server 2012.</span><span class="sxs-lookup"><span data-stu-id="d7af1-106">Windows PowerShell 3.0 is automatically installed with Windows 8 and Windows Server 2012.</span></span>
<span data-ttu-id="d7af1-107">È inoltre possibile scaricare e installare gli assembly di riferimento per Windows PowerShell 3.0 come parte di Windows 8 SDK.</span><span class="sxs-lookup"><span data-stu-id="d7af1-107">In addition, you can download and install the reference assemblies for Windows PowerShell 3.0 as part of the Windows 8 SDK.</span></span>
<span data-ttu-id="d7af1-108">Questi assembly permettono di scrivere cmdlet, provider e programmi host per Windows PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d7af1-108">These assemblies allow you to write cmdlets, providers, and host programs for Windows PowerShell 3.0.</span></span>
<span data-ttu-id="d7af1-109">Quando si installa Windows SDK per Windows 8, gli assembly di Windows PowerShell vengono automaticamente installati nella cartella degli assembly di riferimento, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-109">When you install the Windows SDK for Windows 8, the Windows PowerShell assemblies are automatically installed in the reference assembly folder, in `\Program Files (x86)\Reference Assemblies\Microsoft\WindowsPowerShell\3.0`.</span></span>
<span data-ttu-id="d7af1-110">Per altre informazioni, vedere il [sito di download di Windows 8 SDK](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span><span class="sxs-lookup"><span data-stu-id="d7af1-110">For more information, see the [Windows 8 SDK download site](https://developer.microsoft.com/en-us/windows/downloads/sdk-archive).</span></span>
<span data-ttu-id="d7af1-111">Alcuni esempi di codice di Windows PowerShell sono disponibili anche in Dev Center.</span><span class="sxs-lookup"><span data-stu-id="d7af1-111">Windows PowerShell code samples are also available on the Development Center.</span></span>
<span data-ttu-id="d7af1-112">Per altre informazioni, vedere la pagina degli esempi di codice per sistemi desktop nel [sito Dev Center](https://code.msdn.microsoft.com:443/windowsdesktop/).</span><span class="sxs-lookup"><span data-stu-id="d7af1-112">For more information, see the Desktop code sample page on the [Dev center site](https://code.msdn.microsoft.com:443/windowsdesktop/).</span></span>

<span data-ttu-id="d7af1-113">Inoltre, Windows PowerShell 3.0 è compatibile con la versione precedente, Windows PowerShell 2.0 SDK, che include diversi esempi di codice.</span><span class="sxs-lookup"><span data-stu-id="d7af1-113">In addition, Windows PowerShell 3.0 is backwards-compatible with the Windows PowerShell 2.0 SDK, which includes a number of code samples.</span></span>
<span data-ttu-id="d7af1-114">Per altre informazioni su come scaricare Windows PowerShell 2.0 SDK, vedere di seguito.</span><span class="sxs-lookup"><span data-stu-id="d7af1-114">For more information on how to download the Windows PowerShell 2.0 SDK, see below.</span></span>
<span data-ttu-id="d7af1-115">Nota: benché gli esempi di codice della versione 2.0 siano compatibili con Windows 8 e Windows PowerShell 3.0, non è possibile installare Windows PowerShell 2.0 in una piattaforma Windows 8.</span><span class="sxs-lookup"><span data-stu-id="d7af1-115">(Note that while the 2.0 code samples are compatible with Windows 8 and Windows PowerShell 3.0, you cannot install Windows PowerShell 2.0 on a Windows 8 platform.)</span></span>

## <a name="installing-windows-powershell-30-sdk-for-windows-7-and-windows-server-2008-r2"></a><span data-ttu-id="d7af1-116">Installazione di Windows PowerShell 3.0 SDK in Windows 7 e Windows Server 2008 R2</span><span class="sxs-lookup"><span data-stu-id="d7af1-116">Installing Windows PowerShell 3.0 SDK for Windows 7 and Windows Server 2008 R2</span></span>

<span data-ttu-id="d7af1-117">In Windows 7 e Windows Server 2008 R2 PowerShell 2.0 è installato automaticamente.</span><span class="sxs-lookup"><span data-stu-id="d7af1-117">Windows 7 and Windows Server 2008 R2 automatically have PowerShell 2.0 installed.</span></span>
<span data-ttu-id="d7af1-118">In questi sistemi, inoltre, è possibile installare PowerShell 3.0.</span><span class="sxs-lookup"><span data-stu-id="d7af1-118">In addition, you can install PowerShell 3.0 on these systems.</span></span>
<span data-ttu-id="d7af1-119">Per altre informazioni, vedere [Installazione di Windows PowerShell](Installing-Windows-PowerShell.md).</span><span class="sxs-lookup"><span data-stu-id="d7af1-119">(For more information, see [Installing Windows PowerShell](Installing-Windows-PowerShell.md).).</span></span>
<span data-ttu-id="d7af1-120">Come descritto sopra, è possibile installare anche Windows 8 SDK in Windows 7 e Windows Server 2008 R2.</span><span class="sxs-lookup"><span data-stu-id="d7af1-120">As described above, you can also install the Windows 8 SDK on Windows 7 and Windows Server 2008 R2.</span></span>

## <a name="installing-windows-powershell-20-sdk-for-windows-7-vista-xp-server-2003-and-server-2008"></a><span data-ttu-id="d7af1-121">Installazione di Windows PowerShell 2.0 SDK in Windows 7, Vista, XP, Server 2003 e Server 2008</span><span class="sxs-lookup"><span data-stu-id="d7af1-121">Installing Windows PowerShell 2.0 SDK for Windows 7, Vista, XP, Server 2003, and Server 2008</span></span>

<span data-ttu-id="d7af1-122">Windows PowerShell 2.0 SDK fornisce gli assembly di riferimento necessari per scrivere cmdlet, provider e applicazioni di hosting, nonché il codice di esempio C# che può essere usato come punto di partenza quando si inizia a scrivere il codice.</span><span class="sxs-lookup"><span data-stu-id="d7af1-122">The Windows PowerShell 2.0 SDK provides the reference assemblies needed to write cmdlets, providers, and hosting applications, and it provides C# sample code that can be used as the starting point when you begin writing code.</span></span>

<span data-ttu-id="d7af1-123">Per installare questo SDK, vedere [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span><span class="sxs-lookup"><span data-stu-id="d7af1-123">To install this SDK, see [Windows PowerShell 2.0 SDK](http://www.microsoft.com/en-us/download/details.aspx?id=2560).</span></span>

## <a name="reference-assemblies"></a><span data-ttu-id="d7af1-124">Assembly di riferimento</span><span class="sxs-lookup"><span data-stu-id="d7af1-124">Reference assemblies</span></span>

<span data-ttu-id="d7af1-125">Gli assembly di riferimento sono installati per impostazione predefinita nel percorso seguente: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-125">Reference assemblies are installed in the following location by default: `c:\Program Files\Reference Assemblies\Microsoft\WindowsPowerShell\V1.0`.</span></span>

> [!NOTE] 
> <span data-ttu-id="d7af1-126">Il codice compilato per gli assembly di Windows PowerShell 2.0 non può essere caricato nelle installazioni di Windows PowerShell 1.0.</span><span class="sxs-lookup"><span data-stu-id="d7af1-126">Code that is compiled against the Windows PowerShell 2.0 assemblies cannot be loaded into Windows PowerShell 1.0 installations.</span></span>
> <span data-ttu-id="d7af1-127">Al contrario, il codice compilato per gli assembly di Windows PowerShell 1.0 può essere caricato nelle installazioni di Windows PowerShell 2.0.</span><span class="sxs-lookup"><span data-stu-id="d7af1-127">However, code that is compiled against the Windows PowerShell 1.0 assemblies can be loaded into Windows PowerShell 2.0 installations.</span></span>

## <a name="samples"></a><span data-ttu-id="d7af1-128">Esempi</span><span class="sxs-lookup"><span data-stu-id="d7af1-128">Samples</span></span>

<span data-ttu-id="d7af1-129">Gli esempi di codice sono installati per impostazione predefinita nel percorso seguente: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-129">Code samples are installed in the following location by default: `C:\Program Files\Microsoft SDKs\Windows\v7.0\Samples\sysmgmt\WindowsPowerShell\`.</span></span>

<span data-ttu-id="d7af1-130">La sezione seguente riporta una breve descrizione del funzionamento di ciascun esempio.</span><span class="sxs-lookup"><span data-stu-id="d7af1-130">The following sections provide a brief description of what each sample does.</span></span>

## <a name="cmdlet-samples"></a><span data-ttu-id="d7af1-131">Esempi di cmdlet</span><span class="sxs-lookup"><span data-stu-id="d7af1-131">Cmdlet samples</span></span>

### <a name="getprocesssample01"></a><span data-ttu-id="d7af1-132">GetProcessSample01</span><span class="sxs-lookup"><span data-stu-id="d7af1-132">GetProcessSample01</span></span>

<span data-ttu-id="d7af1-133">Illustra come scrivere un semplice cmdlet che ottiene tutti i processi nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="d7af1-133">Shows how to write a simple cmdlet that gets all the processes on the local computer.</span></span>

### <a name="getprocesssample02"></a><span data-ttu-id="d7af1-134">GetProcessSample02</span><span class="sxs-lookup"><span data-stu-id="d7af1-134">GetProcessSample02</span></span>

<span data-ttu-id="d7af1-135">Illustra come aggiungere parametri al cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d7af1-135">Shows how to add parameters to the cmdlet.</span></span>
<span data-ttu-id="d7af1-136">Il cmdlet accetta uno o più nomi di processo e restituisce i processi corrispondenti.</span><span class="sxs-lookup"><span data-stu-id="d7af1-136">The cmdlet takes one or more process names and returns the matching processes.</span></span>

### <a name="getprocesssample03"></a><span data-ttu-id="d7af1-137">GetProcessSample03</span><span class="sxs-lookup"><span data-stu-id="d7af1-137">GetProcessSample03</span></span>

<span data-ttu-id="d7af1-138">Illustra come aggiungere parametri che accettano input dalla pipeline.</span><span class="sxs-lookup"><span data-stu-id="d7af1-138">Shows how to add parameters that accept input from the pipeline.</span></span>

### <a name="getprocesssample04"></a><span data-ttu-id="d7af1-139">GetProcessSample04</span><span class="sxs-lookup"><span data-stu-id="d7af1-139">GetProcessSample04</span></span>

<span data-ttu-id="d7af1-140">Illustra come gestire errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="d7af1-140">Shows how to handle nonterminating errors.</span></span>

### <a name="getprocesssample05"></a><span data-ttu-id="d7af1-141">GetProcessSample05</span><span class="sxs-lookup"><span data-stu-id="d7af1-141">GetProcessSample05</span></span>

<span data-ttu-id="d7af1-142">Illustra come visualizzare un elenco di processi specificati.</span><span class="sxs-lookup"><span data-stu-id="d7af1-142">Shows how to display a list of specified processes.</span></span>

### <a name="selectobject"></a><span data-ttu-id="d7af1-143">SelectObject</span><span class="sxs-lookup"><span data-stu-id="d7af1-143">SelectObject</span></span>

<span data-ttu-id="d7af1-144">Illustra come scrivere un filtro per selezionare solo determinati oggetti.</span><span class="sxs-lookup"><span data-stu-id="d7af1-144">Shows how to write a filter to select only certain objects.</span></span>

### <a name="selectstring"></a><span data-ttu-id="d7af1-145">SelectString</span><span class="sxs-lookup"><span data-stu-id="d7af1-145">SelectString</span></span>

<span data-ttu-id="d7af1-146">Illustra come cercare modelli specificati nei file.</span><span class="sxs-lookup"><span data-stu-id="d7af1-146">Shows how to search files for specified patterns.</span></span>

### <a name="stopprocesssample01"></a><span data-ttu-id="d7af1-147">StopProcessSample01</span><span class="sxs-lookup"><span data-stu-id="d7af1-147">StopProcessSample01</span></span>

<span data-ttu-id="d7af1-148">Illustra come implementare un parametro *PassThru* e come richiedere commenti degli utenti tramite chiamate ai metodi [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) e [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue).</span><span class="sxs-lookup"><span data-stu-id="d7af1-148">Shows how to implement a *PassThru* parameter, and how to request user feedback by calls to the [ShouldProcess](/dotnet/api/system.management.automation.cmdlet.shouldprocess) and [ShouldContinue](/dotnet/api/system.management.automation.cmdlet.shouldcontinue) methods.</span></span>
<span data-ttu-id="d7af1-149">Gli utenti specificano il parametro *PassThru* per forzare il cmdlet a restituire un oggetto.</span><span class="sxs-lookup"><span data-stu-id="d7af1-149">Users specify the *PassThru* parameter when they want to force the cmdlet to return an object,</span></span>

### <a name="stopprocesssample02"></a><span data-ttu-id="d7af1-150">StopProcessSample02</span><span class="sxs-lookup"><span data-stu-id="d7af1-150">StopProcessSample02</span></span>

<span data-ttu-id="d7af1-151">Illustra come arrestare un processo specifico.</span><span class="sxs-lookup"><span data-stu-id="d7af1-151">Shows how to stop a specific process.</span></span>

### <a name="stopprocesssample03"></a><span data-ttu-id="d7af1-152">StopProcessSample03</span><span class="sxs-lookup"><span data-stu-id="d7af1-152">StopProcessSample03</span></span>

<span data-ttu-id="d7af1-153">Illustra come dichiarare gli alias per i parametri e come supportare i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="d7af1-153">Shows how to declare aliases for parameters and how to support wildcards.</span></span>

### <a name="stopprocesssample04"></a><span data-ttu-id="d7af1-154">StopProcessSample04</span><span class="sxs-lookup"><span data-stu-id="d7af1-154">StopProcessSample04</span></span>

<span data-ttu-id="d7af1-155">Illustra come dichiarare i set di parametri, l'oggetto che il cmdlet accetta come input e come specificare il set di parametri predefinito da usare.</span><span class="sxs-lookup"><span data-stu-id="d7af1-155">Shows how to declare parameter sets, the object that the cmdlet takes as input, and how to specify the default parameter set to use.</span></span>

## <a name="remoting-samples"></a><span data-ttu-id="d7af1-156">Esempi di comunicazione remota</span><span class="sxs-lookup"><span data-stu-id="d7af1-156">Remoting samples</span></span>

### <a name="remoterunspace01"></a><span data-ttu-id="d7af1-157">RemoteRunspace01</span><span class="sxs-lookup"><span data-stu-id="d7af1-157">RemoteRunspace01</span></span>

<span data-ttu-id="d7af1-158">Illustra come creare uno spazio di esecuzione remota che viene usato per stabilire una connessione remota.</span><span class="sxs-lookup"><span data-stu-id="d7af1-158">Shows how to create a remote runspace that is used to establish a remote connection.</span></span>

### <a name="remoterunspacepool01"></a><span data-ttu-id="d7af1-159">RemoteRunspacePool01</span><span class="sxs-lookup"><span data-stu-id="d7af1-159">RemoteRunspacePool01</span></span>

<span data-ttu-id="d7af1-160">Illustra come creare un pool di spazi di esecuzione remota e come eseguire contemporaneamente più comandi usando questo pool.</span><span class="sxs-lookup"><span data-stu-id="d7af1-160">Shows how to construct a remote runspace pool and how to run multiple commands concurrently by using this pool.</span></span>

### <a name="serialization01"></a><span data-ttu-id="d7af1-161">Serialization01</span><span class="sxs-lookup"><span data-stu-id="d7af1-161">Serialization01</span></span>

<span data-ttu-id="d7af1-162">Illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni provenienti da specifiche proprietà pubbliche di questa classe vengano mantenute nella serializzazione/deserializzazione.</span><span class="sxs-lookup"><span data-stu-id="d7af1-162">Shows how to look at an existing .NET class and make sure that information from selected public properties of this class is preserved across serialization/deserialization.</span></span>

### <a name="serialization02"></a><span data-ttu-id="d7af1-163">Serialization02</span><span class="sxs-lookup"><span data-stu-id="d7af1-163">Serialization02</span></span>

<span data-ttu-id="d7af1-164">Illustra come esaminare una classe .NET esistente e assicurarsi che le informazioni provenienti dall'istanza di questa classe vengano mantenute nella serializzazione/deserializzazione quando non sono disponibili nelle proprietà pubbliche della classe.</span><span class="sxs-lookup"><span data-stu-id="d7af1-164">Shows how to look at an existing .NET class and make sure that information from instance of this class is preserved across serialization/deserialization when the information is not available in public properties of the class.</span></span>

### <a name="serialization03"></a><span data-ttu-id="d7af1-165">Serialization03</span><span class="sxs-lookup"><span data-stu-id="d7af1-165">Serialization03</span></span>

<span data-ttu-id="d7af1-166">Illustra come esaminare una classe .NET esistente e assicurarsi che le istanze di questa classe e delle classi derivate vengano deserializzate (riattivate) in oggetti .NET attivi.</span><span class="sxs-lookup"><span data-stu-id="d7af1-166">Shows how to look at an existing .NET class and make sure that instances of this class and of derived classes are deserialized (rehydrated) into live .NET objects.</span></span>

## <a name="event-samples"></a><span data-ttu-id="d7af1-167">Esempi di evento</span><span class="sxs-lookup"><span data-stu-id="d7af1-167">Event samples</span></span>

### <a name="event01"></a><span data-ttu-id="d7af1-168">Event01</span><span class="sxs-lookup"><span data-stu-id="d7af1-168">Event01</span></span>

<span data-ttu-id="d7af1-169">Illustra come creare un cmdlet per la registrazione di eventi da ObjectEventRegistrationBase.</span><span class="sxs-lookup"><span data-stu-id="d7af1-169">Shows how to create a cmdlet for event registration by deriving from ObjectEventRegistrationBase.</span></span>

### <a name="event02"></a><span data-ttu-id="d7af1-170">Event02</span><span class="sxs-lookup"><span data-stu-id="d7af1-170">Event02</span></span>

<span data-ttu-id="d7af1-171">Illustra come ricevere notifiche di eventi di Windows PowerShell generati nei computer remoti.</span><span class="sxs-lookup"><span data-stu-id="d7af1-171">Shows how to shows how to receive notifications of Windows PowerShell events that are generated on remote computers.</span></span>
<span data-ttu-id="d7af1-172">Usa l'evento PSEventReceived esposto tramite la classe [Runspace](/dotnet/api/system.management.automation.runspaces.runspace).</span><span class="sxs-lookup"><span data-stu-id="d7af1-172">It uses the PSEventReceived event exposed through the [Runspace](/dotnet/api/system.management.automation.runspaces.runspace) class.</span></span>

## <a name="hosting-application-samples"></a><span data-ttu-id="d7af1-173">Esempi di applicazioni di hosting</span><span class="sxs-lookup"><span data-stu-id="d7af1-173">Hosting application samples</span></span>

### <a name="runspace01"></a><span data-ttu-id="d7af1-174">Runspace01</span><span class="sxs-lookup"><span data-stu-id="d7af1-174">Runspace01</span></span>

<span data-ttu-id="d7af1-175">Illustra come usare la classe [PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="d7af1-175">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet synchronously.</span></span>
<span data-ttu-id="d7af1-176">Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce oggetti [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) per ogni processo in esecuzione nel computer locale.</span><span class="sxs-lookup"><span data-stu-id="d7af1-176">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer.</span></span>

### <a name="runspace02"></a><span data-ttu-id="d7af1-177">Runspace02</span><span class="sxs-lookup"><span data-stu-id="d7af1-177">Runspace02</span></span>

<span data-ttu-id="d7af1-178">Illustra come usare la classe [PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire i cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="d7af1-178">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) and [Sort-Object](/powershell/module/Microsoft.PowerShell.Utility/Sort-Object) cmdlets synchronously.</span></span>
<span data-ttu-id="d7af1-179">Il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) restituisce oggetti [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) per ogni processo in esecuzione nel computer locale e `Sort-Object` ordina gli oggetti in base alle loro proprietà [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx).</span><span class="sxs-lookup"><span data-stu-id="d7af1-179">The [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet returns [Process](https://technet.microsoft.com/library/system.diagnostics.process.aspx) objects for each process running on the local computer, and the `Sort-Object` sorts the objects based on their [Id](https://technet.microsoft.com/library/system.diagnostics.process.id.aspx) property.</span></span>
<span data-ttu-id="d7af1-180">I risultati di questi comandi vengono visualizzati usando un controllo [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx).</span><span class="sxs-lookup"><span data-stu-id="d7af1-180">The results of these commands is displayed by using a [DataGridView](https://technet.microsoft.com/library/system.windows.forms.datagridview.aspx) control.</span></span>

### <a name="runspace03"></a><span data-ttu-id="d7af1-181">Runspace03</span><span class="sxs-lookup"><span data-stu-id="d7af1-181">Runspace03</span></span>

<span data-ttu-id="d7af1-182">Illustra come usare la classe [PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script in modo sincrono e come gestire gli errori non fatali.</span><span class="sxs-lookup"><span data-stu-id="d7af1-182">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run a script synchronously, and how to handle non-terminating errors.</span></span>
<span data-ttu-id="d7af1-183">Lo script riceve un elenco di nomi di processo e quindi recupera tali processi.</span><span class="sxs-lookup"><span data-stu-id="d7af1-183">The script receives a list of process names and then retrieves those processes.</span></span>
<span data-ttu-id="d7af1-184">I risultati dello script, compresi gli errori non fatali che si sono generati durante l'esecuzione dello script, vengono visualizzati in una finestra della console.</span><span class="sxs-lookup"><span data-stu-id="d7af1-184">The results of the script, including any non-terminating errors that were generated when running the script, are displayed in a console window.</span></span>

### <a name="runspace04"></a><span data-ttu-id="d7af1-185">Runspace04</span><span class="sxs-lookup"><span data-stu-id="d7af1-185">Runspace04</span></span>

<span data-ttu-id="d7af1-186">Illustra come usare la classe [PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire i comandi e come recuperare gli errori fatali generati durante l'esecuzione di comandi.</span><span class="sxs-lookup"><span data-stu-id="d7af1-186">Shows how to use the [PowerShell](/dotnet/api/system.management.automation.powershell) class to run commands, and how to catch terminating errors that are thrown when running the commands.</span></span>
<span data-ttu-id="d7af1-187">Vengono eseguiti due comandi e all'ultimo viene passato un argomento di parametro non valido.</span><span class="sxs-lookup"><span data-stu-id="d7af1-187">Two commands are run, and the last command is passed a parameter argument that is not valid.</span></span>
<span data-ttu-id="d7af1-188">Di conseguenza, non viene restituito alcun oggetto e viene generato un errore non fatale.</span><span class="sxs-lookup"><span data-stu-id="d7af1-188">As a result, no objects are returned and a terminating error is thrown.</span></span>

### <a name="runspace05"></a><span data-ttu-id="d7af1-189">Runspace05</span><span class="sxs-lookup"><span data-stu-id="d7af1-189">Runspace05</span></span>

<span data-ttu-id="d7af1-190">Illustra come aggiungere uno snap-in a un oggetto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) in modo che il cmdlet dello snap-in sia disponibile quando viene aperto lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d7af1-190">Shows how to add a snap-in to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the cmdlet of the snap-in is available when the runspace is opened.</span></span>
<span data-ttu-id="d7af1-191">Lo snap-in include un cmdlet Get-Process (definito dall'esempio [GetProcessSample01](https://technet.microsoft.com/library/ff602028.aspx)) che viene eseguito in modo sincrono tramite un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="d7af1-191">The snap-in provides a Get-Proc cmdlet (defined by the [GetProcessSample01 Sample](https://technet.microsoft.com/library/ff602028.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace06"></a><span data-ttu-id="d7af1-192">Runspace06</span><span class="sxs-lookup"><span data-stu-id="d7af1-192">Runspace06</span></span>

<span data-ttu-id="d7af1-193">Illustra come aggiungere un modulo a un oggetto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) in modo che il modulo venga caricato quando viene aperto lo spazio di esecuzione.</span><span class="sxs-lookup"><span data-stu-id="d7af1-193">Shows how to add a module to an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object so that the module is loaded when the runspace is opened.</span></span>
<span data-ttu-id="d7af1-194">Il modulo include un cmdlet Get-Proc (definito dall'esempio [GetProcessSample02](https://technet.microsoft.com/library/ff602027.aspx)) che viene eseguito in modo sincrono tramite un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="d7af1-194">The module provides a Get-Proc cmdlet (defined by the [GetProcessSample02 Sample](https://technet.microsoft.com/library/ff602027.aspx)) that is run synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace07"></a><span data-ttu-id="d7af1-195">Runspace07</span><span class="sxs-lookup"><span data-stu-id="d7af1-195">Runspace07</span></span>

<span data-ttu-id="d7af1-196">Illustra come creare uno spazio di esecuzione e quindi usare tale spazio di esecuzione per eseguire due cmdlet in modo sincrono tramite un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="d7af1-196">Shows how to create a runspace, and then use that runspace to run two cmdlets synchronously by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace08"></a><span data-ttu-id="d7af1-197">Runspace08</span><span class="sxs-lookup"><span data-stu-id="d7af1-197">Runspace08</span></span>

<span data-ttu-id="d7af1-198">Illustra come aggiungere comandi e argomenti alla pipeline di un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire i comandi in modo sincrono.</span><span class="sxs-lookup"><span data-stu-id="d7af1-198">Shows how to add commands and arguments to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the commands synchronously.</span></span>

### <a name="runspace09"></a><span data-ttu-id="d7af1-199">Runspace09</span><span class="sxs-lookup"><span data-stu-id="d7af1-199">Runspace09</span></span>

<span data-ttu-id="d7af1-200">Illustra come aggiungere uno script alla pipeline di un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell) e come eseguire lo script in modo asincrono.</span><span class="sxs-lookup"><span data-stu-id="d7af1-200">Shows how to add a script to the pipeline of a [PowerShell](/dotnet/api/system.management.automation.powershell) object and how to run the script asynchronously.</span></span>
<span data-ttu-id="d7af1-201">Gli eventi vengono usati per gestire l'output dello script.</span><span class="sxs-lookup"><span data-stu-id="d7af1-201">Events are used to handle the output of the script.</span></span>

### <a name="runspace10"></a><span data-ttu-id="d7af1-202">Runspace10</span><span class="sxs-lookup"><span data-stu-id="d7af1-202">Runspace10</span></span>

<span data-ttu-id="d7af1-203">Illustra come creare uno stato di sessione iniziale predefinito, come aggiungere un cmdlet a [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), come creare uno spazio di esecuzione che usa lo stato sessione iniziale e come eseguire il comando usando un oggetto [PowerShell](/dotnet/api/system.management.automation.powershell).</span><span class="sxs-lookup"><span data-stu-id="d7af1-203">Shows how to create a default initial session state, how to add a cmdlet to the [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate), how to create a runspace that uses the initial session state, and how to run the command by using a [PowerShell](/dotnet/api/system.management.automation.powershell) object.</span></span>

### <a name="runspace11"></a><span data-ttu-id="d7af1-204">Runspace11</span><span class="sxs-lookup"><span data-stu-id="d7af1-204">Runspace11</span></span>

<span data-ttu-id="d7af1-205">Illustra come usare la classe [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) per creare un comando proxy che chiama un cmdlet esistente, ma limita il set di parametri disponibili.</span><span class="sxs-lookup"><span data-stu-id="d7af1-205">Shows how to use the [ProxyCommand](/dotnet/api/system.management.automation.proxycommand) class to create a proxy command that calls an existing cmdlet, but restricts the set of available parameters.</span></span>
<span data-ttu-id="d7af1-206">Il comando proxy viene quindi aggiunto a uno stato sessione iniziale usato per creare uno spazio di esecuzione vincolato.</span><span class="sxs-lookup"><span data-stu-id="d7af1-206">The proxy command is then added to an initial session state that is used to create a constrained runspace.</span></span>
<span data-ttu-id="d7af1-207">Ciò significa che l'utente può accedere alla funzionalità del cmdlet solo tramite il comando proxy.</span><span class="sxs-lookup"><span data-stu-id="d7af1-207">This means that the user can access the functionality of the cmdlet only through the proxy command.</span></span>

### <a name="powershell01"></a><span data-ttu-id="d7af1-208">PowerShell01</span><span class="sxs-lookup"><span data-stu-id="d7af1-208">PowerShell01</span></span>

<span data-ttu-id="d7af1-209">Illustra come creare uno spazio di esecuzione vincolato usando un oggetto [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate).</span><span class="sxs-lookup"><span data-stu-id="d7af1-209">Shows how to create a constrained runspace using an [InitialSessionState](/dotnet/api/system.management.automation.runspaces.initialsessionstate) object.</span></span>

### <a name="powershell02"></a><span data-ttu-id="d7af1-210">PowerShell02</span><span class="sxs-lookup"><span data-stu-id="d7af1-210">PowerShell02</span></span>

<span data-ttu-id="d7af1-211">Illustra come usare un pool di spazi di esecuzione per eseguire più comandi contemporaneamente.</span><span class="sxs-lookup"><span data-stu-id="d7af1-211">Shows how to use a runspace pool to run multiple commands concurrently.</span></span>

## <a name="host-samples"></a><span data-ttu-id="d7af1-212">Esempi di host</span><span class="sxs-lookup"><span data-stu-id="d7af1-212">Host samples</span></span>

### <a name="host01"></a><span data-ttu-id="d7af1-213">Host01</span><span class="sxs-lookup"><span data-stu-id="d7af1-213">Host01</span></span>

<span data-ttu-id="d7af1-214">Illustra come implementare un'applicazione host che usa un host personalizzato.</span><span class="sxs-lookup"><span data-stu-id="d7af1-214">Shows how to implement a host application that uses a custom host.</span></span>
<span data-ttu-id="d7af1-215">In questo esempio viene creato uno spazio di esecuzione che usa l'host personalizzato e quindi viene usata l'API [PowerShell](/dotnet/api/system.management.automation.powershell) per eseguire uno script che chiama "exit".</span><span class="sxs-lookup"><span data-stu-id="d7af1-215">In this sample a runspace is created that uses the custom host, and then the [PowerShell](/dotnet/api/system.management.automation.powershell) API is used to run a script that calls "exit".</span></span>
<span data-ttu-id="d7af1-216">L'applicazione host esamina l'output dello script e stampa i risultati.</span><span class="sxs-lookup"><span data-stu-id="d7af1-216">The host application then looks at the output of the script and prints out the results.</span></span>

### <a name="host02"></a><span data-ttu-id="d7af1-217">Host02</span><span class="sxs-lookup"><span data-stu-id="d7af1-217">Host02</span></span>

<span data-ttu-id="d7af1-218">Illustra come scrivere un'applicazione host che usa il runtime di Windows PowerShell insieme a un'implementazione host personalizzata.</span><span class="sxs-lookup"><span data-stu-id="d7af1-218">Shows how to write a host application that uses the Windows PowerShell runtime along with a custom host implementation.</span></span>
<span data-ttu-id="d7af1-219">L'applicazione host imposta le impostazioni cultura dell'host per la lingua tedesca, esegue il cmdlet [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) e visualizza i risultati allo stesso modo di quando si usa pwrsh.exe e quindi stampa i dati e l'ora correnti in tedesco.</span><span class="sxs-lookup"><span data-stu-id="d7af1-219">The host application sets the host culture to German, runs the [Get-Process](/powershell/module/Microsoft.PowerShell.Management/Get-Process) cmdlet and displays the results as you would see them by using pwrsh.exe, and then prints out the current data and time in German.</span></span>

### <a name="host03"></a><span data-ttu-id="d7af1-220">Host03</span><span class="sxs-lookup"><span data-stu-id="d7af1-220">Host03</span></span>

<span data-ttu-id="d7af1-221">Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="d7af1-221">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>

### <a name="host04"></a><span data-ttu-id="d7af1-222">Host04</span><span class="sxs-lookup"><span data-stu-id="d7af1-222">Host04</span></span>

<span data-ttu-id="d7af1-223">Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="d7af1-223">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="d7af1-224">L'applicazione host supporta anche la visualizzazione di messaggi di richiesta che consentono all'utente di specificare più opzioni.</span><span class="sxs-lookup"><span data-stu-id="d7af1-224">This host application also supports displaying prompts that allow the user to specify multiple choices.</span></span>

### <a name="host05"></a><span data-ttu-id="d7af1-225">Host05</span><span class="sxs-lookup"><span data-stu-id="d7af1-225">Host05</span></span>

<span data-ttu-id="d7af1-226">Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="d7af1-226">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="d7af1-227">L'applicazione host supporta anche le chiamate a computer remoti tramite i cmdlet [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) e [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession).</span><span class="sxs-lookup"><span data-stu-id="d7af1-227">This host application also supports calls to remote computers by using the [Enter-PsSession](/powershell/module/Microsoft.PowerShell.Core/Enter-PSSession) and [Exit-PsSession](/powershell/module/Microsoft.PowerShell.Core/Exit-PSSession) cmdlets.</span></span>

### <a name="host06"></a><span data-ttu-id="d7af1-228">Host06</span><span class="sxs-lookup"><span data-stu-id="d7af1-228">Host06</span></span>

<span data-ttu-id="d7af1-229">Illustra come creare un'applicazione host basata su console interattiva che legge i comandi dalla riga di comando, esegue i comandi e quindi visualizza i risultati nella console.</span><span class="sxs-lookup"><span data-stu-id="d7af1-229">Shows how to build an interactive console-based host application that reads commands from the command line, executes the commands, and then displays the results to the console.</span></span>
<span data-ttu-id="d7af1-230">Questo esempio usa inoltre le API del tokenizer per specificare il colore del testo immesso dall'utente.</span><span class="sxs-lookup"><span data-stu-id="d7af1-230">In addition, this sample uses the Tokenizer APIs to specify the color of the text that is entered by the user.</span></span>

## <a name="provider-samples"></a><span data-ttu-id="d7af1-231">Esempi di provider</span><span class="sxs-lookup"><span data-stu-id="d7af1-231">Provider samples</span></span>

### <a name="accessdbprovidersample01"></a><span data-ttu-id="d7af1-232">AccessDBProviderSample01</span><span class="sxs-lookup"><span data-stu-id="d7af1-232">AccessDBProviderSample01</span></span>

<span data-ttu-id="d7af1-233">Illustra come dichiarare una classe di provider che deriva direttamente dalla classe [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-233">Shows how to declare a provider class that derives directly from the [CmdletProvider](/dotnet/api/system.management.automation.provider.cmdletprovider) class.</span></span>
<span data-ttu-id="d7af1-234">È incluso solo per motivi di completezza.</span><span class="sxs-lookup"><span data-stu-id="d7af1-234">It is included here only for completeness.</span></span>

### <a name="accessdbprovidersample02"></a><span data-ttu-id="d7af1-235">AccessDBProviderSample02</span><span class="sxs-lookup"><span data-stu-id="d7af1-235">AccessDBProviderSample02</span></span>

<span data-ttu-id="d7af1-236">Illustra come sovrascrivere i metodi [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) e [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) per il supporto alle chiamate ai cmdlet `New-PSDrive` e `Remove-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-236">Shows how to overwrite the [NewDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.newdrive) and [RemoveDrive](/dotnet/api/system.management.automation.provider.drivecmdletprovider.removedrive) methods to support calls to the `New-PSDrive` and `Remove-PSDrive` cmdlets.</span></span>
<span data-ttu-id="d7af1-237">La classe del provider in questo esempio deriva dalla classe [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-237">The provider class in this sample derives from the [DriveCmdletProvider](/dotnet/api/system.management.automation.provider.drivecmdletprovider) class.</span></span>

### <a name="accessdbprovidersample03"></a><span data-ttu-id="d7af1-238">AccessDBProviderSample03</span><span class="sxs-lookup"><span data-stu-id="d7af1-238">AccessDBProviderSample03</span></span>

<span data-ttu-id="d7af1-239">Illustra come sovrascrivere i metodi [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) e [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) per il supporto alle chiamate ai cmdlet `Get-Item` e `Set-Item`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-239">Shows how to overwrite the [GetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.getitem) and [SetItem](/dotnet/api/system.management.automation.provider.itemcmdletprovider.setitem) methods to support calls to the `Get-Item` and `Set-Item` cmdlets.</span></span>
<span data-ttu-id="d7af1-240">La classe del provider in questo esempio deriva dalla classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-240">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample04"></a><span data-ttu-id="d7af1-241">AccessDBProviderSample04</span><span class="sxs-lookup"><span data-stu-id="d7af1-241">AccessDBProviderSample04</span></span>

<span data-ttu-id="d7af1-242">Illustra come sovrascrivere i metodi contenitore per il supporto alle chiamate ai cmdlet `Copy-Item`, `Get-ChildItem`, `New-Item` e `Remove-Item`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-242">Shows how to overwrite container methods to support calls to the `Copy-Item`, `Get-ChildItem`, `New-Item`, and `Remove-Item` cmdlets.</span></span>
<span data-ttu-id="d7af1-243">Questi metodi devono essere implementati quando l'archivio dati contiene elementi che sono contenitori.</span><span class="sxs-lookup"><span data-stu-id="d7af1-243">These methods should be implemented when the data store contains items that are containers.</span></span>
<span data-ttu-id="d7af1-244">Un contenitore è un gruppo di elementi figlio all'interno di un elemento padre comune.</span><span class="sxs-lookup"><span data-stu-id="d7af1-244">A container is a group of child items under a common parent item.</span></span>
<span data-ttu-id="d7af1-245">La classe del provider in questo esempio deriva dalla classe [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-245">The provider class in this sample derives from the [ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample05"></a><span data-ttu-id="d7af1-246">AccessDBProviderSample05</span><span class="sxs-lookup"><span data-stu-id="d7af1-246">AccessDBProviderSample05</span></span>

<span data-ttu-id="d7af1-247">Illustra come sovrascrivere i metodi contenitore per il supporto alle chiamate ai cmdlet `Move-Item` e `Join-Path`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-247">Shows how to overwrite container methods to support calls to the `Move-Item` and `Join-Path` cmdlets.</span></span>
<span data-ttu-id="d7af1-248">Questi metodi devono essere implementati quando l'utente deve spostare elementi all'interno di un contenitore e se l'archivio dati contiene contenitori annidati.</span><span class="sxs-lookup"><span data-stu-id="d7af1-248">These methods should be implemented when the user needs to move items within a container and if the data store contains nested containers.</span></span>
<span data-ttu-id="d7af1-249">La classe del provider in questo esempio deriva dalla classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-249">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class.</span></span>

### <a name="accessdbprovidersample06"></a><span data-ttu-id="d7af1-250">AccessDBProviderSample06</span><span class="sxs-lookup"><span data-stu-id="d7af1-250">AccessDBProviderSample06</span></span>

<span data-ttu-id="d7af1-251">Illustra come sovrascrivere i metodi contenitore per il supporto alle chiamate ai cmdlet `Clear-Content`, `Get-Content` e `Set-Content`.</span><span class="sxs-lookup"><span data-stu-id="d7af1-251">Shows how to overwrite content methods to support calls to the `Clear-Content`, `Get-Content`, and `Set-Content` cmdlets.</span></span>
<span data-ttu-id="d7af1-252">Questi metodi devono essere implementati quando l'utente deve gestire il contenuto degli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="d7af1-252">These methods should be implemented when the user needs to manage the content of the items in the data store.</span></span>
<span data-ttu-id="d7af1-253">La classe del provider in questo esempio deriva dalla classe [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) che implementa l'interfaccia [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider).</span><span class="sxs-lookup"><span data-stu-id="d7af1-253">The provider class in this sample derives from the [NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider) class, and it implements the [IContentCmdletProvider](/dotnet/api/system.management.automation.provider.icontentcmdletprovider) interface.</span></span>