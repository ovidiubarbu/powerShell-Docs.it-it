---
title: Creazione di un Provider di unità di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- drive providers [PowerShell Programmer's Guide]
- providers [PowerShell Programmer's Guide], drive provider
- drives [PowerShell Programmer's Guide]
ms.assetid: 2b446841-6616-4720-9ff8-50801d7576ed
caps.latest.revision: 6
ms.openlocfilehash: d1546ab0b0e6b5502f35c92c01ce148211c53db2
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56855797"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="5a47c-102">Creazione di un provider di unità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a47c-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="5a47c-103">Questo argomento descrive come creare un provider di unità di Windows PowerShell che fornisce un modo per accedere a un archivio dati tramite un'unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a47c-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="5a47c-104">Questo tipo di provider è detta anche i provider di unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a47c-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="5a47c-105">Le unità di Windows PowerShell utilizzate dal provider forniscono i mezzi per la connessione all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="5a47c-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="5a47c-106">Il provider dell'unità Windows PowerShell descritto di seguito fornisce l'accesso a un database Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="5a47c-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="5a47c-107">Per questo provider, l'unità di Windows PowerShell rappresenta il database (è possibile aggiungere qualsiasi numero di unità a un provider dell'unità), i contenitori di primo livello dell'unità rappresentano le tabelle nel database e gli elementi dei contenitori rappresentano le righe in le tabelle.</span><span class="sxs-lookup"><span data-stu-id="5a47c-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

<span data-ttu-id="5a47c-108">Ecco un elenco delle sezioni in questo argomento.</span><span class="sxs-lookup"><span data-stu-id="5a47c-108">Here is a list of the sections in this topic.</span></span> <span data-ttu-id="5a47c-109">Se non si ha familiarità con la scrittura di un provider di unità di Windows PowerShell, leggere le sezioni riportate nell'ordine in cui appaiono.</span><span class="sxs-lookup"><span data-stu-id="5a47c-109">If you are unfamiliar with writing a Windows PowerShell drive provider, read these sections in the order that they appear.</span></span> <span data-ttu-id="5a47c-110">Tuttavia, se si ha familiarità con la scrittura di un provider dell'unità, passare direttamente alle informazioni necessarie.</span><span class="sxs-lookup"><span data-stu-id="5a47c-110">However, if you are familiar with writing a drive provider, please go directly to the information that you need.</span></span>

- [<span data-ttu-id="5a47c-111">Definizione della classe di Provider PowerShell per Windows</span><span class="sxs-lookup"><span data-stu-id="5a47c-111">Defining the Windows PowerShell Provider Class</span></span>](#Defining-the-Windows-PowerShell-Provider-Class)

- [<span data-ttu-id="5a47c-112">Definizione funzionalità di Base</span><span class="sxs-lookup"><span data-stu-id="5a47c-112">Defining Base Functionality</span></span>](#Defining-Base-Functionality)

- [<span data-ttu-id="5a47c-113">Creazione di informazioni sullo stato unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-113">Creating Drive State Information</span></span>](#Creating-Drive-State-Information)

- [<span data-ttu-id="5a47c-114">Creazione di un'unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-114">Creating a Drive</span></span>](#Creating-a-Drive)

- [<span data-ttu-id="5a47c-115">Associazione di parametri dinamici a NewDrive</span><span class="sxs-lookup"><span data-stu-id="5a47c-115">Attaching Dynamic Parameters to NewDrive</span></span>](#Attaching-Dynamic-Parameters-to-NewDrive)

- [<span data-ttu-id="5a47c-116">Rimozione di un'unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-116">Removing a Drive</span></span>](#Removing-a-Drive)

- [<span data-ttu-id="5a47c-117">L'inizializzazione predefinita di unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-117">Initializing Default Drives</span></span>](#Initializing-Default-Drives)

- [<span data-ttu-id="5a47c-118">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="5a47c-118">Code Sample</span></span>](#Code-Sample)

- [<span data-ttu-id="5a47c-119">Test del Provider di unità di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="5a47c-119">Testing the Windows PowerShell Drive Provider</span></span>](#Testing-the-Windows-PowerShell-Drive-Provider)

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="5a47c-120">Definizione della classe di Provider PowerShell per Windows</span><span class="sxs-lookup"><span data-stu-id="5a47c-120">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="5a47c-121">Il provider dell'unità deve definire una classe .NET che deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe di base.</span><span class="sxs-lookup"><span data-stu-id="5a47c-121">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="5a47c-122">Ecco la definizione di classe per questo provider dell'unità:</span><span class="sxs-lookup"><span data-stu-id="5a47c-122">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5a47c-123">Si noti che in questo esempio, il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attributo specifica un nome descrittivo per il provider e le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando.</span><span class="sxs-lookup"><span data-stu-id="5a47c-123">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="5a47c-124">I valori possibili per le funzionalità del provider sono definiti per il [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumerazione.</span><span class="sxs-lookup"><span data-stu-id="5a47c-124">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="5a47c-125">Questo provider dell'unità non supporta uno qualsiasi di queste funzionalità.</span><span class="sxs-lookup"><span data-stu-id="5a47c-125">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="5a47c-126">Definizione funzionalità di Base</span><span class="sxs-lookup"><span data-stu-id="5a47c-126">Defining Base Functionality</span></span>

<span data-ttu-id="5a47c-127">Come descritto in [Provider di progettazione di Windows PowerShell](./designing-your-windows-powershell-provider.md), il [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) deriva dalla classe di [ System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) classe base che definisce i metodi necessari per l'inizializzazione e annullamento dell'inizializzazione del provider.</span><span class="sxs-lookup"><span data-stu-id="5a47c-127">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="5a47c-128">Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio delle risorse usate dal provider, vedere [creazione di un PowerShell Provider di Windows base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5a47c-128">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="5a47c-129">Tuttavia, la maggior parte dei fornitori (tra cui il provider descritto di seguito) è possono usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5a47c-129">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="5a47c-130">Creazione di informazioni sullo stato unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-130">Creating Drive State Information</span></span>

<span data-ttu-id="5a47c-131">Tutti i provider Windows PowerShell sono considerati senza stati, il che significa che il provider di unità deve creare eventuali informazioni sullo stato necessarie per il runtime di Windows PowerShell quando si chiama il provider.</span><span class="sxs-lookup"><span data-stu-id="5a47c-131">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="5a47c-132">Per questo provider dell'unità, le informazioni sullo stato includono la connessione al database che viene mantenuto come parte di informazioni sull'unità.</span><span class="sxs-lookup"><span data-stu-id="5a47c-132">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="5a47c-133">Ecco il codice che illustra come queste informazioni vengono archiviate nel [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità:</span><span class="sxs-lookup"><span data-stu-id="5a47c-133">Here is code that shows how this information is stored in the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="5a47c-134">Creazione di un'unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-134">Creating a Drive</span></span>

<span data-ttu-id="5a47c-135">Per consentire al runtime di Windows PowerShell creare un'unità, il provider dell'unità deve implementare il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) (metodo).</span><span class="sxs-lookup"><span data-stu-id="5a47c-135">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="5a47c-136">Il codice seguente viene illustrata l'implementazione del [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodo per questo provider dell'unità:</span><span class="sxs-lookup"><span data-stu-id="5a47c-136">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5a47c-137">L'override di questo metodo deve eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="5a47c-137">Your override of this method should do the following:</span></span>

- <span data-ttu-id="5a47c-138">Verificare che il [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) membro esista e che può essere stabilita una connessione all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="5a47c-138">Verify that the [System.Management.Automation.Psdriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="5a47c-139">Creare un'unità e popolare il membro di connessione, supportare la `New-PSDrive` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5a47c-139">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="5a47c-140">Convalidare il [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) oggetto per l'unità proposto.</span><span class="sxs-lookup"><span data-stu-id="5a47c-140">Validate the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="5a47c-141">Modificare il [psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) dell'oggetto che descrive l'unità con qualsiasi informazione di affidabilità o le prestazioni necessarie o fornire dati aggiuntivi per i chiamanti utilizzano l'unità.</span><span class="sxs-lookup"><span data-stu-id="5a47c-141">Modify the [System.Management.Automation.Psdriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="5a47c-142">Gestire gli errori usando il [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) metodo e quindi restituirla `null`.</span><span class="sxs-lookup"><span data-stu-id="5a47c-142">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.Writeerror\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="5a47c-143">Questo metodo restituisce le informazioni unità che è state passate al metodo o una versione specifica del provider.</span><span class="sxs-lookup"><span data-stu-id="5a47c-143">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="5a47c-144">Associazione di parametri dinamici a NewDrive</span><span class="sxs-lookup"><span data-stu-id="5a47c-144">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="5a47c-145">Il `New-PSDrive` cmdlet supportati dal provider di unità potrebbero richiedere parametri aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="5a47c-145">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="5a47c-146">Per collegare questi parametri dinamici al cmdlet, il provider implementa il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) (metodo).</span><span class="sxs-lookup"><span data-stu-id="5a47c-146">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="5a47c-147">Questo metodo restituisce un oggetto che dispone di proprietà e campi con analisi degli attributi simili a una classe cmdlet o una [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) oggetto.</span><span class="sxs-lookup"><span data-stu-id="5a47c-147">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="5a47c-148">Questo provider dell'unità non esegue l'override di questo metodo.</span><span class="sxs-lookup"><span data-stu-id="5a47c-148">This drive provider does not override this method.</span></span> <span data-ttu-id="5a47c-149">Tuttavia, il codice seguente illustra l'implementazione predefinita di questo metodo:</span><span class="sxs-lookup"><span data-stu-id="5a47c-149">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="5a47c-150">Rimozione di un'unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-150">Removing a Drive</span></span>

<span data-ttu-id="5a47c-151">Per chiudere la connessione al database, il provider dell'unità deve implementare il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) (metodo).</span><span class="sxs-lookup"><span data-stu-id="5a47c-151">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="5a47c-152">Questo metodo chiude la connessione all'unità dopo la pulizia di eventuali informazioni specifiche del provider.</span><span class="sxs-lookup"><span data-stu-id="5a47c-152">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="5a47c-153">Il codice seguente viene illustrata l'implementazione del [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo per questo provider dell'unità:</span><span class="sxs-lookup"><span data-stu-id="5a47c-153">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="5a47c-154">Se l'unità può essere rimosso, il metodo deve restituire le informazioni passate al metodo attraverso il `drive` parametro.</span><span class="sxs-lookup"><span data-stu-id="5a47c-154">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="5a47c-155">Se l'unità non può essere rimosso, il metodo deve scrivere un'eccezione e quindi restituire `null`.</span><span class="sxs-lookup"><span data-stu-id="5a47c-155">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="5a47c-156">Se il provider non esegue l'override di questo metodo, l'implementazione predefinita di questo metodo restituisce solo le informazioni dell'unità passate come input.</span><span class="sxs-lookup"><span data-stu-id="5a47c-156">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="5a47c-157">L'inizializzazione predefinita di unità</span><span class="sxs-lookup"><span data-stu-id="5a47c-157">Initializing Default Drives</span></span>

<span data-ttu-id="5a47c-158">Implementa il provider unità il [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) metodo montare unità.</span><span class="sxs-lookup"><span data-stu-id="5a47c-158">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="5a47c-159">Il provider di Active Directory, ad esempio, potrebbe essere montata un'unità per il contesto dei nomi se il computer è unito a un dominio predefinito.</span><span class="sxs-lookup"><span data-stu-id="5a47c-159">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="5a47c-160">Questo metodo restituisce una raccolta di unità di informazioni sulle unità inizializzata o una raccolta vuota.</span><span class="sxs-lookup"><span data-stu-id="5a47c-160">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="5a47c-161">Viene effettuata la chiamata a questo metodo dopo le chiamate di runtime di Windows PowerShell il [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) metodo per inizializzare il provider.</span><span class="sxs-lookup"><span data-stu-id="5a47c-161">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="5a47c-162">Questo provider dell'unità non esegue l'override di [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) (metodo).</span><span class="sxs-lookup"><span data-stu-id="5a47c-162">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="5a47c-163">Tuttavia, il codice seguente illustra l'implementazione predefinita che restituisce una raccolta di unità vuote:</span><span class="sxs-lookup"><span data-stu-id="5a47c-163">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="5a47c-164">Aspetti da ricordare sull'implementazione InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="5a47c-164">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="5a47c-165">Tutti i provider di unità è consigliabile montare un'unità radice per consentire all'utente con l'individuazione.</span><span class="sxs-lookup"><span data-stu-id="5a47c-165">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="5a47c-166">L'unità radice potrebbe elencare i percorsi che fungono da radici di altre unità montate.</span><span class="sxs-lookup"><span data-stu-id="5a47c-166">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="5a47c-167">Ad esempio, il provider di Active Directory potrebbe creare un'unità in cui sono elencati i contesti dei nomi disponibili nel `namingContext` attributi nella directory principale ambiente di sistema distribuita (DSE).</span><span class="sxs-lookup"><span data-stu-id="5a47c-167">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="5a47c-168">Ciò consente agli utenti di individuare i punti di montaggio per le altre unità.</span><span class="sxs-lookup"><span data-stu-id="5a47c-168">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="5a47c-169">Esempio di codice</span><span class="sxs-lookup"><span data-stu-id="5a47c-169">Code Sample</span></span>

<span data-ttu-id="5a47c-170">Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="5a47c-170">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="5a47c-171">Test del Provider di unità di PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="5a47c-171">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="5a47c-172">Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile eseguirne il test eseguendo il cmdlet supportati nella riga di comando, inclusi tutti i cmdlet resi disponibili dalla derivazione.</span><span class="sxs-lookup"><span data-stu-id="5a47c-172">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="5a47c-173">È possibile testare il provider di unità di esempio.</span><span class="sxs-lookup"><span data-stu-id="5a47c-173">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="5a47c-174">Eseguire il `Get-PSProvider` cmdlet per recuperare l'elenco dei provider per assicurare che il provider dell'unità AccessDB sia presente:</span><span class="sxs-lookup"><span data-stu-id="5a47c-174">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="5a47c-175">**PS> `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="5a47c-175">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="5a47c-176">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="5a47c-176">The following output appears:</span></span>

   ```output
   Name                 Capabilities                  Drives
   ----                 ------------                  ------
   AccessDB             None                          {}
   Alias                ShouldProcess                 {Alias}
   Environment          ShouldProcess                 {Env}
   FileSystem           Filter, ShouldProcess         {C, Z}
   Function             ShouldProcess                 {function}
   Registry             ShouldProcess                 {HKLM, HKCU}
   ```

2. <span data-ttu-id="5a47c-177">Verificare l'esistenza di un nome di server di database (DSN) per il database tramite l'accesso di **Zdroje dat** parte del **strumenti di amministrazione** per il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="5a47c-177">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="5a47c-178">Nel **DSN utente** tabella, fare doppio clic su **MS accesso Database** e aggiungere il percorso di unità C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="5a47c-178">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="5a47c-179">Creare una nuova unità utilizzando il provider di unità di esempio:</span><span class="sxs-lookup"><span data-stu-id="5a47c-179">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="5a47c-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="5a47c-180">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="5a47c-181">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="5a47c-181">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="5a47c-182">Convalidare la connessione.</span><span class="sxs-lookup"><span data-stu-id="5a47c-182">Validate the connection.</span></span> <span data-ttu-id="5a47c-183">Poiché la connessione è definita come membro dell'unità, è possibile archiviarlo tramite il cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="5a47c-183">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="5a47c-184">L'utente non è ancora interagire con il provider come un'unità, quando la funzionalità contenitore sono necessari per il provider per tale interazione.</span><span class="sxs-lookup"><span data-stu-id="5a47c-184">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="5a47c-185">Per altre informazioni, vedere [creazione di un Provider di contenitore di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="5a47c-185">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="5a47c-186">**PS > .connection (mydb get-psdrive)**</span><span class="sxs-lookup"><span data-stu-id="5a47c-186">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="5a47c-187">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="5a47c-187">The following output appears:</span></span>

   ```output
   ConnectionString  : Driver={Microsoft Access Driver (*.mdb)};DBQ=c:\ps\northwind.mdb
   ConnectionTimeout : 15
   Database          : c:\ps\northwind
   DataSource        : ACCESS
   ServerVersion     : 04.00.0000
   Driver            : odbcjt32.dll
   State             : Open
   Site              :
   Container         :
   ```

5. <span data-ttu-id="5a47c-188">Rimuovere l'unità e uscire dalla shell:</span><span class="sxs-lookup"><span data-stu-id="5a47c-188">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="5a47c-189">**PS > remove-psdrive mydb**</span><span class="sxs-lookup"><span data-stu-id="5a47c-189">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="5a47c-190">**PS > uscire**</span><span class="sxs-lookup"><span data-stu-id="5a47c-190">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="5a47c-191">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="5a47c-191">See Also</span></span>

[<span data-ttu-id="5a47c-192">Creazione di provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a47c-192">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="5a47c-193">Progettare il Provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a47c-193">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="5a47c-194">Creazione di un Provider PowerShell di Windows di base</span><span class="sxs-lookup"><span data-stu-id="5a47c-194">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)