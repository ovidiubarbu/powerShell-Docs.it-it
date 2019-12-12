---
title: Creazione di un provider di unità di Windows PowerShell | Microsoft Docs
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
ms.openlocfilehash: 2e3d97e224b06bdf36ac0bc1237911e029ea762d
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72366830"
---
# <a name="creating-a-windows-powershell-drive-provider"></a><span data-ttu-id="b9efb-102">Creazione di un provider di unità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9efb-102">Creating a Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b9efb-103">Questo argomento descrive come creare un provider di unità di Windows PowerShell che fornisce un modo per accedere a un archivio dati tramite un'unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9efb-103">This topic describes how to create a Windows PowerShell drive provider that provides a way to access a data store through a Windows PowerShell drive.</span></span> <span data-ttu-id="b9efb-104">Questo tipo di provider è anche noto come provider di unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9efb-104">This type of provider is also referred to as Windows PowerShell drive providers.</span></span> <span data-ttu-id="b9efb-105">Le unità di Windows PowerShell utilizzate dal provider forniscono i mezzi per connettersi all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="b9efb-105">The Windows PowerShell drives used by the provider provide the means to connect to the data store.</span></span>

<span data-ttu-id="b9efb-106">Il provider di unità di Windows PowerShell descritto di seguito consente di accedere a un database di Microsoft Access.</span><span class="sxs-lookup"><span data-stu-id="b9efb-106">The Windows PowerShell drive provider described here provides access to a Microsoft Access database.</span></span> <span data-ttu-id="b9efb-107">Per questo provider, l'unità di Windows PowerShell rappresenta il database (è possibile aggiungere un numero qualsiasi di unità a un provider di unità), i contenitori di livello superiore dell'unità rappresentano le tabelle nel database e gli elementi dei contenitori rappresentano le righe in tabelle.</span><span class="sxs-lookup"><span data-stu-id="b9efb-107">For this provider, the Windows PowerShell drive represents the database (it is possible to add any number of drives to a drive provider), the top-level containers of the drive represent the tables in the database, and the items of the containers represent the rows in the tables.</span></span>

## <a name="defining-the-windows-powershell-provider-class"></a><span data-ttu-id="b9efb-108">Definizione della classe del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9efb-108">Defining the Windows PowerShell Provider Class</span></span>

<span data-ttu-id="b9efb-109">Il provider di unità deve definire una classe .NET che deriva dalla classe di base [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-109">Your drive provider must define a .NET class that derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) base class.</span></span> <span data-ttu-id="b9efb-110">Di seguito è illustrata la definizione di classe per questo provider di unità:</span><span class="sxs-lookup"><span data-stu-id="b9efb-110">Here is the class definition for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L29-L30 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b9efb-111">Si noti che in questo esempio l'attributo [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) specifica un nome descrittivo per il provider e le funzionalità specifiche di Windows PowerShell che il provider espone al runtime di Windows PowerShell durante l'elaborazione del comando.</span><span class="sxs-lookup"><span data-stu-id="b9efb-111">Notice that in this example, the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) attribute specifies a user-friendly name for the provider and the Windows PowerShell specific capabilities that the provider exposes to the Windows PowerShell runtime during command processing.</span></span> <span data-ttu-id="b9efb-112">I valori possibili per le funzionalità del provider sono definiti dall'enumerazione [System. Management. Automation. provider. ProviderCapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-112">The possible values for the provider capabilities are defined by the [System.Management.Automation.Provider.Providercapabilities](/dotnet/api/System.Management.Automation.Provider.ProviderCapabilities) enumeration.</span></span> <span data-ttu-id="b9efb-113">Questo provider di unità non supporta nessuna di queste funzionalità.</span><span class="sxs-lookup"><span data-stu-id="b9efb-113">This drive provider does not support any of these capabilities.</span></span>

## <a name="defining-base-functionality"></a><span data-ttu-id="b9efb-114">Definizione della funzionalità di base</span><span class="sxs-lookup"><span data-stu-id="b9efb-114">Defining Base Functionality</span></span>

<span data-ttu-id="b9efb-115">Come descritto nella pagina relativa alla [progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md), la classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) deriva dalla classe di base [System. Management. Automation. provider. CmdletProvider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) che definisce i metodi necessari per l'inizializzazione e l'annullamento dell'inizializzazione del provider.</span><span class="sxs-lookup"><span data-stu-id="b9efb-115">As described in [Design Your Windows PowerShell Provider](./designing-your-windows-powershell-provider.md), the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class derives from the [System.Management.Automation.Provider.Cmdletprovider](/dotnet/api/System.Management.Automation.Provider.CmdletProvider) base class that defines the methods needed for initializing and uninitializing the provider.</span></span> <span data-ttu-id="b9efb-116">Per implementare la funzionalità per l'aggiunta di informazioni di inizializzazione specifiche della sessione e per il rilascio di risorse utilizzate dal provider, vedere [creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b9efb-116">To implement functionality for adding session-specific initialization information and for releasing resources that are used by the provider, see [Creating a Basic Windows PowerShell Provider](./creating-a-basic-windows-powershell-provider.md).</span></span> <span data-ttu-id="b9efb-117">Tuttavia, la maggior parte dei provider (incluso il provider descritto qui) può usare l'implementazione predefinita di questa funzionalità fornita da Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b9efb-117">However, most providers (including the provider described here) can use the default implementation of this functionality that is provided by Windows PowerShell.</span></span>

## <a name="creating-drive-state-information"></a><span data-ttu-id="b9efb-118">Creazione di informazioni sullo stato dell'unità</span><span class="sxs-lookup"><span data-stu-id="b9efb-118">Creating Drive State Information</span></span>

<span data-ttu-id="b9efb-119">Tutti i provider di Windows PowerShell sono considerati senza stato, il che significa che il provider di unità deve creare tutte le informazioni sullo stato necessarie al runtime di Windows PowerShell quando chiama il provider.</span><span class="sxs-lookup"><span data-stu-id="b9efb-119">All Windows PowerShell providers are considered stateless, which means that your drive provider needs to create any state information that is needed by the Windows PowerShell runtime when it calls your provider.</span></span>

<span data-ttu-id="b9efb-120">Per questo provider di unità, le informazioni sullo stato includono la connessione al database mantenuto come parte delle informazioni sull'unità.</span><span class="sxs-lookup"><span data-stu-id="b9efb-120">For this drive provider, state information includes the connection to the database that is kept as part of the drive information.</span></span> <span data-ttu-id="b9efb-121">Ecco il codice che Mostra come queste informazioni vengono archiviate nell'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità:</span><span class="sxs-lookup"><span data-stu-id="b9efb-121">Here is code that shows how this information is stored in the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L130-L151 "AccessDBProviderSample02.cs")]

## <a name="creating-a-drive"></a><span data-ttu-id="b9efb-122">Creazione di un'unità</span><span class="sxs-lookup"><span data-stu-id="b9efb-122">Creating a Drive</span></span>

<span data-ttu-id="b9efb-123">Per consentire al runtime di Windows PowerShell di creare un'unità, il provider di unità deve implementare il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-123">To allow the Windows PowerShell runtime to create a drive, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method.</span></span> <span data-ttu-id="b9efb-124">Il codice seguente illustra l'implementazione del metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per questo provider di unità:</span><span class="sxs-lookup"><span data-stu-id="b9efb-124">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L42-L84 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b9efb-125">L'override di questo metodo deve eseguire le operazioni seguenti:</span><span class="sxs-lookup"><span data-stu-id="b9efb-125">Your override of this method should do the following:</span></span>

- <span data-ttu-id="b9efb-126">Verificare che il membro [System. Management. Automation. PSDriveinfo. root \*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) esista e che sia possibile effettuare una connessione all'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="b9efb-126">Verify that the [System.Management.Automation.PSDriveinfo.Root\*](/dotnet/api/System.Management.Automation.PSDriveInfo.Root) member exists and that a connection to the data store can be made.</span></span>

- <span data-ttu-id="b9efb-127">Creare un'unità e popolare il membro della connessione, in supporto del cmdlet `New-PSDrive`.</span><span class="sxs-lookup"><span data-stu-id="b9efb-127">Create a drive and populate the connection member, in support of the `New-PSDrive` cmdlet.</span></span>

- <span data-ttu-id="b9efb-128">Convalidare l'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) per l'unità proposta.</span><span class="sxs-lookup"><span data-stu-id="b9efb-128">Validate the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object for the proposed drive.</span></span>

- <span data-ttu-id="b9efb-129">Modificare l'oggetto [System. Management. Automation. PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) che descrive l'unità con le informazioni sulle prestazioni o sull'affidabilità richieste oppure fornire dati aggiuntivi per i chiamanti che usano l'unità.</span><span class="sxs-lookup"><span data-stu-id="b9efb-129">Modify the [System.Management.Automation.PSDriveinfo](/dotnet/api/System.Management.Automation.PSDriveInfo) object that describes the drive with any required performance or reliability information, or provide extra data for callers using the drive.</span></span>

- <span data-ttu-id="b9efb-130">Gestire gli errori usando il metodo [System. Management. Automation. provider. CmdletProvider. WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) e quindi restituire `null`.</span><span class="sxs-lookup"><span data-stu-id="b9efb-130">Handle failures using the [System.Management.Automation.Provider.Cmdletprovider.WriteError](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteError) method and then return `null`.</span></span>

  <span data-ttu-id="b9efb-131">Questo metodo restituisce le informazioni sull'unità passate al metodo o a una versione specifica del provider.</span><span class="sxs-lookup"><span data-stu-id="b9efb-131">This method returns either the drive information that was passed to the method or a provider-specific version of it.</span></span>

## <a name="attaching-dynamic-parameters-to-newdrive"></a><span data-ttu-id="b9efb-132">Associazione di parametri dinamici a nuovaunità</span><span class="sxs-lookup"><span data-stu-id="b9efb-132">Attaching Dynamic Parameters to NewDrive</span></span>

<span data-ttu-id="b9efb-133">Il cmdlet `New-PSDrive` supportato dal provider di unità potrebbe richiedere parametri aggiuntivi.</span><span class="sxs-lookup"><span data-stu-id="b9efb-133">The `New-PSDrive` cmdlet supported by your drive provider might require additional parameters.</span></span> <span data-ttu-id="b9efb-134">Per alleghi questi parametri dinamici al cmdlet, il provider implementa il metodo [System. Management. Automation. provider. Drivecmdletprovider. Newdrivedynamicparameters \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-134">To attach these dynamic parameters to the cmdlet, the provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrivedynamicparameters\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDriveDynamicParameters) method.</span></span> <span data-ttu-id="b9efb-135">Questo metodo restituisce un oggetto con proprietà e campi con attributi di analisi simili a una classe di cmdlet o a un oggetto [System. Management. Automation. RuntimeDefinedParameterDictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-135">This method returns an object that has properties and fields with parsing attributes similar to a cmdlet class or a [System.Management.Automation.Runtimedefinedparameterdictionary](/dotnet/api/System.Management.Automation.RuntimeDefinedParameterDictionary) object.</span></span>

<span data-ttu-id="b9efb-136">Questo provider di unità non esegue l'override di questo metodo.</span><span class="sxs-lookup"><span data-stu-id="b9efb-136">This drive provider does not override this method.</span></span> <span data-ttu-id="b9efb-137">Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita di questo metodo:</span><span class="sxs-lookup"><span data-stu-id="b9efb-137">However, the following code shows the default implementation of this method:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters](Msh_samplestestcmdlets#testprovidernewdrivedynamicparameters)]  -->

## <a name="removing-a-drive"></a><span data-ttu-id="b9efb-138">Rimozione di un'unità</span><span class="sxs-lookup"><span data-stu-id="b9efb-138">Removing a Drive</span></span>

<span data-ttu-id="b9efb-139">Per chiudere la connessione al database, il provider di unità deve implementare il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-139">To close the database connection, the drive provider must implement the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method.</span></span> <span data-ttu-id="b9efb-140">Questo metodo chiude la connessione all'unità dopo avere pulito le informazioni specifiche del provider.</span><span class="sxs-lookup"><span data-stu-id="b9efb-140">This method closes the connection to the drive after cleaning up any provider-specific information.</span></span>

<span data-ttu-id="b9efb-141">Il codice seguente illustra l'implementazione del metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per questo provider di unità:</span><span class="sxs-lookup"><span data-stu-id="b9efb-141">The following code shows the implementation of the [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method for this drive provider:</span></span>

[!code-csharp[AccessDBProviderSample02.cs](../../../../powershell-sdk-samples/SDK-2.0/csharp/AccessDBProviderSample02/AccessDBProviderSample02.cs#L91-L116 "AccessDBProviderSample02.cs")]

<span data-ttu-id="b9efb-142">Se è possibile rimuovere l'unità, il metodo deve restituire le informazioni passate al metodo tramite il parametro `drive`.</span><span class="sxs-lookup"><span data-stu-id="b9efb-142">If the drive can be removed, the method should return the information passed to the method through the `drive` parameter.</span></span> <span data-ttu-id="b9efb-143">Se non è possibile rimuovere l'unità, il metodo deve scrivere un'eccezione e quindi restituire `null`.</span><span class="sxs-lookup"><span data-stu-id="b9efb-143">If the drive cannot be removed, the method should write an exception and then return `null`.</span></span> <span data-ttu-id="b9efb-144">Se il provider non esegue l'override di questo metodo, l'implementazione predefinita di questo metodo restituisce solo le informazioni sull'unità passate come input.</span><span class="sxs-lookup"><span data-stu-id="b9efb-144">If your provider does not override this method, the default implementation of this method just returns the drive information passed as input.</span></span>

## <a name="initializing-default-drives"></a><span data-ttu-id="b9efb-145">Inizializzazione di unità predefinite</span><span class="sxs-lookup"><span data-stu-id="b9efb-145">Initializing Default Drives</span></span>

<span data-ttu-id="b9efb-146">Il provider di unità implementa il metodo [System. Management. Automation. provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) per montare le unità.</span><span class="sxs-lookup"><span data-stu-id="b9efb-146">Your drive provider implements the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method to mount drives.</span></span> <span data-ttu-id="b9efb-147">Il provider di Active Directory, ad esempio, può montare un'unità per il contesto dei nomi predefinito se il computer è aggiunto a un dominio.</span><span class="sxs-lookup"><span data-stu-id="b9efb-147">For example, the Active Directory provider might mount a drive for the default naming context if the computer is joined to a domain.</span></span>

<span data-ttu-id="b9efb-148">Questo metodo restituisce una raccolta di informazioni sulle unità inizializzate o una raccolta vuota.</span><span class="sxs-lookup"><span data-stu-id="b9efb-148">This method returns a collection of drive information about the initialized drives, or an empty collection.</span></span> <span data-ttu-id="b9efb-149">La chiamata a questo metodo viene eseguita dopo che il runtime di Windows PowerShell chiama il metodo [System. Management. Automation. provider. CmdletProvider. Start \*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) per inizializzare il provider.</span><span class="sxs-lookup"><span data-stu-id="b9efb-149">The call to this method is made after the Windows PowerShell runtime calls the [System.Management.Automation.Provider.Cmdletprovider.Start\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.Start) method to initialize the provider.</span></span>

<span data-ttu-id="b9efb-150">Questo provider di unità non esegue l'override del metodo [System. Management. Automation. provider. Drivecmdletprovider. Initializedefaultdrives \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) .</span><span class="sxs-lookup"><span data-stu-id="b9efb-150">This drive provider does not override the [System.Management.Automation.Provider.Drivecmdletprovider.Initializedefaultdrives\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.InitializeDefaultDrives) method.</span></span> <span data-ttu-id="b9efb-151">Tuttavia, nel codice seguente viene illustrata l'implementazione predefinita, che restituisce una raccolta di unità vuota:</span><span class="sxs-lookup"><span data-stu-id="b9efb-151">However, the following code shows the default implementation, which returns an empty drive collection:</span></span>

<!-- TODO!!!: review snippet reference  [!CODE [Msh_samplestestcmdlets#testproviderinitializedefaultdrives](Msh_samplestestcmdlets#testproviderinitializedefaultdrives)]  -->

#### <a name="things-to-remember-about-implementing-initializedefaultdrives"></a><span data-ttu-id="b9efb-152">Aspetti da ricordare sull'implementazione di InitializeDefaultDrives</span><span class="sxs-lookup"><span data-stu-id="b9efb-152">Things to Remember About Implementing InitializeDefaultDrives</span></span>

<span data-ttu-id="b9efb-153">Tutti i provider di unità devono montare un'unità radice per aiutare l'utente a individuarlo.</span><span class="sxs-lookup"><span data-stu-id="b9efb-153">All drive providers should mount a root drive to help the user with discoverability.</span></span> <span data-ttu-id="b9efb-154">L'unità radice potrebbe elencare le posizioni che funge da radice per altre unità montate.</span><span class="sxs-lookup"><span data-stu-id="b9efb-154">The root drive might list locations that serve as roots for other mounted drives.</span></span> <span data-ttu-id="b9efb-155">Ad esempio, il provider di Active Directory potrebbe creare un'unità in cui sono elencati i contesti di denominazione trovati negli attributi di `namingContext` sull'ambiente di sistema distribuito radice (DSE).</span><span class="sxs-lookup"><span data-stu-id="b9efb-155">For example, the Active Directory provider might create a drive that lists the naming contexts found in the `namingContext` attributes on the root Distributed System Environment (DSE).</span></span> <span data-ttu-id="b9efb-156">Ciò consente agli utenti di individuare i punti di montaggio per altre unità.</span><span class="sxs-lookup"><span data-stu-id="b9efb-156">This helps users discover mount points for other drives.</span></span>

## <a name="code-sample"></a><span data-ttu-id="b9efb-157">Codice di esempio</span><span class="sxs-lookup"><span data-stu-id="b9efb-157">Code Sample</span></span>

<span data-ttu-id="b9efb-158">Per il codice di esempio completo, vedere [esempio di codice AccessDbProviderSample02](./accessdbprovidersample02-code-sample.md).</span><span class="sxs-lookup"><span data-stu-id="b9efb-158">For complete sample code, see [AccessDbProviderSample02 Code Sample](./accessdbprovidersample02-code-sample.md).</span></span>

## <a name="testing-the-windows-powershell-drive-provider"></a><span data-ttu-id="b9efb-159">Test del provider di unità di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9efb-159">Testing the Windows PowerShell Drive Provider</span></span>

<span data-ttu-id="b9efb-160">Quando il provider di Windows PowerShell è stato registrato con Windows PowerShell, è possibile testarlo eseguendo i cmdlet supportati dalla riga di comando, inclusi tutti i cmdlet resi disponibili dalla derivazione.</span><span class="sxs-lookup"><span data-stu-id="b9efb-160">When your Windows PowerShell provider has been registered with Windows PowerShell, you can test it by running the supported cmdlets on the command line, including any cmdlets made available by derivation.</span></span> <span data-ttu-id="b9efb-161">Testiamo il provider di unità di esempio.</span><span class="sxs-lookup"><span data-stu-id="b9efb-161">Let's test the sample drive provider.</span></span>

1. <span data-ttu-id="b9efb-162">Eseguire il cmdlet `Get-PSProvider` per recuperare l'elenco dei provider per verificare che sia presente il provider dell'unità AccessDB:</span><span class="sxs-lookup"><span data-stu-id="b9efb-162">Run the `Get-PSProvider` cmdlet to retrieve the list of providers to ensure that the AccessDB drive provider is present:</span></span>

   <span data-ttu-id="b9efb-163">**> PS `Get-PSProvider`**</span><span class="sxs-lookup"><span data-stu-id="b9efb-163">**PS> `Get-PSProvider`**</span></span>

   <span data-ttu-id="b9efb-164">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="b9efb-164">The following output appears:</span></span>

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

2. <span data-ttu-id="b9efb-165">Assicurarsi che esista un nome del server di database (DSN) per il database accedendo alla parte **origini dati** degli **strumenti di amministrazione** per il sistema operativo.</span><span class="sxs-lookup"><span data-stu-id="b9efb-165">Ensure that a database server name (DSN) exists for the database by accessing the **Data Sources** portion of the **Administrative Tools** for the operating system.</span></span> <span data-ttu-id="b9efb-166">Nella tabella **DSN utente** fare doppio clic su **database di MS Access** e aggiungere il percorso dell'unità C:\ps\northwind.mdb.</span><span class="sxs-lookup"><span data-stu-id="b9efb-166">In the **User DSN** table, double-click **MS Access Database** and add the drive path C:\ps\northwind.mdb.</span></span>

3. <span data-ttu-id="b9efb-167">Creare una nuova unità utilizzando il provider di unità di esempio:</span><span class="sxs-lookup"><span data-stu-id="b9efb-167">Create a new drive using the sample drive provider:</span></span>

   <span data-ttu-id="b9efb-168">**PS > New-PSDrive-Name MyDB-root c:\ps\northwind.mdb-PSProvider AccessDb**</span><span class="sxs-lookup"><span data-stu-id="b9efb-168">**PS> new-psdrive -name mydb -root c:\ps\northwind.mdb -psprovider AccessDb**</span></span>

   <span data-ttu-id="b9efb-169">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="b9efb-169">The following output appears:</span></span>

   ```output
   Name     Provider     Root                   CurrentLocation
   ----     --------     ----                   ---------------
   mydb     AccessDB     c:\ps\northwind.mdb
   ```

4. <span data-ttu-id="b9efb-170">Convalidare la connessione.</span><span class="sxs-lookup"><span data-stu-id="b9efb-170">Validate the connection.</span></span> <span data-ttu-id="b9efb-171">Poiché la connessione è definita come membro dell'unità, è possibile verificarla utilizzando il cmdlet Get-PDDrive.</span><span class="sxs-lookup"><span data-stu-id="b9efb-171">Because the connection is defined as a member of the drive, you can check it using the Get-PDDrive cmdlet.</span></span>

   > [!NOTE]
   > <span data-ttu-id="b9efb-172">L'utente non può ancora interagire con il provider come unità, perché il provider richiede la funzionalità del contenitore per tale interazione.</span><span class="sxs-lookup"><span data-stu-id="b9efb-172">The user cannot yet interact with the provider as a drive, as the provider needs container functionality for that interaction.</span></span> <span data-ttu-id="b9efb-173">Per ulteriori informazioni, vedere [creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="b9efb-173">For more information, see [Creating a Windows PowerShell Container Provider](./creating-a-windows-powershell-container-provider.md).</span></span>

   <span data-ttu-id="b9efb-174">**PS > (Get-PSDrive MyDB). Connection**</span><span class="sxs-lookup"><span data-stu-id="b9efb-174">**PS> (get-psdrive mydb).connection**</span></span>

   <span data-ttu-id="b9efb-175">Viene visualizzato l'output seguente:</span><span class="sxs-lookup"><span data-stu-id="b9efb-175">The following output appears:</span></span>

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

5. <span data-ttu-id="b9efb-176">Rimuovere l'unità e uscire dalla shell:</span><span class="sxs-lookup"><span data-stu-id="b9efb-176">Remove the drive and exit the shell:</span></span>

   <span data-ttu-id="b9efb-177">**PS > Remove-PSDrive MyDB**</span><span class="sxs-lookup"><span data-stu-id="b9efb-177">**PS> remove-psdrive mydb**</span></span>

   <span data-ttu-id="b9efb-178">**Uscita da PS >**</span><span class="sxs-lookup"><span data-stu-id="b9efb-178">**PS> exit**</span></span>

## <a name="see-also"></a><span data-ttu-id="b9efb-179">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b9efb-179">See Also</span></span>

[<span data-ttu-id="b9efb-180">Creazione di provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9efb-180">Creating Windows PowerShell Providers</span></span>](./how-to-create-a-windows-powershell-provider.md)

[<span data-ttu-id="b9efb-181">Progettare il provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="b9efb-181">Design Your Windows PowerShell Provider</span></span>](./designing-your-windows-powershell-provider.md)

[<span data-ttu-id="b9efb-182">Creazione di un provider di Windows PowerShell di base</span><span class="sxs-lookup"><span data-stu-id="b9efb-182">Creating a Basic Windows PowerShell Provider</span></span>](./creating-a-basic-windows-powershell-provider.md)
