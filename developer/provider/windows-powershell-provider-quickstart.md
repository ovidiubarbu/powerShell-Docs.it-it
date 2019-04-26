---
title: Guida introduttiva di Provider PowerShell per Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 151b7125afe1b0d386467a0e5f89225716857ac2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080884"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="483ee-102">Guida introduttiva del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="483ee-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="483ee-103">Questo argomento illustra come creare un provider di Windows PowerShell con le funzionalità di base della creazione di una nuova unità.</span><span class="sxs-lookup"><span data-stu-id="483ee-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="483ee-104">Per informazioni generali sui provider, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="483ee-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="483ee-105">Per esempi di provider di funzionalità più complete, vedere [esempi di Provider](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="483ee-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="483ee-106">La scrittura di un provider di base</span><span class="sxs-lookup"><span data-stu-id="483ee-106">Writing a basic provider</span></span>

<span data-ttu-id="483ee-107">La funzionalità di base di un provider di Windows PowerShell consiste nel creare e rimuovere le unità.</span><span class="sxs-lookup"><span data-stu-id="483ee-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="483ee-108">In questo esempio, Implementiamo le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="483ee-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="483ee-109">Si vedrà anche come dichiarare una classe di provider.</span><span class="sxs-lookup"><span data-stu-id="483ee-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="483ee-110">Quando si scrive un provider, è possibile specificare le unità-unità di predefiniti che vengono create automaticamente quando il provider è disponibile.</span><span class="sxs-lookup"><span data-stu-id="483ee-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="483ee-111">È anche possibile definire un metodo per creare nuove unità che utilizzano tale provider.</span><span class="sxs-lookup"><span data-stu-id="483ee-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="483ee-112">Gli esempi forniti in questo argomento si basano le [AccessDBProviderSample02](./accessdbprovidersample02.md) esempio, che fa parte di un campione di dimensioni maggiori che rappresenta un database di Access come un'unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="483ee-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="483ee-113">Impostazione del progetto</span><span class="sxs-lookup"><span data-stu-id="483ee-113">Setting up the project</span></span>

<span data-ttu-id="483ee-114">In Visual Studio, creare un progetto libreria di classi denominato AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="483ee-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="483ee-115">Completare i passaggi seguenti per configurare il progetto in modo che Windows PowerShell verrà avviato e il provider verrà caricato nella sessione, quando si compila e avvia il tuo progetto.</span><span class="sxs-lookup"><span data-stu-id="483ee-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="483ee-116">Configurare il provider di progetto</span><span class="sxs-lookup"><span data-stu-id="483ee-116">Configure the provider project</span></span>

1. <span data-ttu-id="483ee-117">Aggiungere l'assembly Automation come un riferimento al progetto.</span><span class="sxs-lookup"><span data-stu-id="483ee-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="483ee-118">Fare clic su **progetto > proprietà AccessDBProviderSample > Debug**.</span><span class="sxs-lookup"><span data-stu-id="483ee-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="483ee-119">Nelle **progetto di avvio**, fare clic su **Avvia programma esterno**e passare al file eseguibile di Windows PowerShell (in genere c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="483ee-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="483ee-120">Sotto **opzioni di avvio**, immettere quanto segue nel **argomenti della riga di comando** casella: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="483ee-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="483ee-121">Dichiarazione della classe di provider</span><span class="sxs-lookup"><span data-stu-id="483ee-121">Declaring the provider class</span></span>

<span data-ttu-id="483ee-122">Il provider di servizi deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="483ee-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="483ee-123">La maggior parte dei provider che forniscono funzionalità reale (l'accesso e la modifica di elementi, passando l'archivio dati e ottenere e impostare il contenuto degli elementi) derivano dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="483ee-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="483ee-124">Oltre a specificare che la classe deriva da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), è necessario decorare con il [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) come illustrato nell'esempio.</span><span class="sxs-lookup"><span data-stu-id="483ee-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

```csharp
namespace Microsoft.Samples.PowerShell.Providers
{
  using System;
  using System.Data;
  using System.Data.Odbc;
  using System.IO;
  using System.Management.Automation;
  using System.Management.Automation.Provider;

  #region AccessDBProvider

  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {

}
}
```

### <a name="implementing-newdrive"></a><span data-ttu-id="483ee-125">Implementazione NewDrive</span><span class="sxs-lookup"><span data-stu-id="483ee-125">Implementing NewDrive</span></span>

<span data-ttu-id="483ee-126">Il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodo viene chiamato dal motore di Windows PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)che specifica il nome del provider di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="483ee-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="483ee-127">Il parametro PSDriveInfo viene passato dal motore di Windows PowerShell e il metodo restituisce la nuova unità al motore di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="483ee-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="483ee-128">Questo metodo deve essere dichiarato all'interno della classe creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="483ee-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="483ee-129">Il metodo controlla prima di tutto per assicurarsi che l'oggetto unità sia alla radice dell'unità che sono stati passati esiste, restituendo `null` se una di esse non li supportano.</span><span class="sxs-lookup"><span data-stu-id="483ee-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="483ee-130">Un costruttore della classe interna AccessDBPSDriveInfo viene quindi utilizzato per creare una nuova unità e rappresenta una connessione al database di Access, l'unità.</span><span class="sxs-lookup"><span data-stu-id="483ee-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

```csharp
protected override PSDriveInfo NewDrive(PSDriveInfo drive)
    {
      // Check if the drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   null));

        return null;
      }

      // Check if the drive root is not null or empty
      // and if it is an existing file.
      if (String.IsNullOrEmpty(drive.Root) || (File.Exists(drive.Root) == false))
      {
        WriteError(new ErrorRecord(
                   new ArgumentException("drive.Root"),
                   "NoRoot",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Create a new drive and create an ODBC connection to the new drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = new AccessDBPSDriveInfo(drive);
      OdbcConnectionStringBuilder builder = new OdbcConnectionStringBuilder();

      builder.Driver = "Microsoft Access Driver (*.mdb)";
      builder.Add("DBQ", drive.Root);

      OdbcConnection conn = new OdbcConnection(builder.ConnectionString);
      conn.Open();
      accessDBPSDriveInfo.Connection = conn;

      return accessDBPSDriveInfo;
    }
```

<span data-ttu-id="483ee-131">Di seguito è la classe interna AccessDBPSDriveInfo che include il costruttore usato per creare una nuova unità e contiene le informazioni sullo stato per l'unità.</span><span class="sxs-lookup"><span data-stu-id="483ee-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

```csharp
internal class AccessDBPSDriveInfo : PSDriveInfo
  {
    /// <summary>
    /// A reference to the connection to the database.
    /// </summary>
    private OdbcConnection connection;

    /// <summary>
    /// Initializes a new instance of the AccessDBPSDriveInfo class.
    /// The constructor takes a single argument.
    /// </summary>
    /// <param name="driveInfo">Drive defined by this provider</param>
    public AccessDBPSDriveInfo(PSDriveInfo driveInfo)
           : base(driveInfo)
    {
    }

    /// <summary>
    /// Gets or sets the ODBC connection information.
    /// </summary>
    public OdbcConnection Connection
    {
        get { return this.connection; }
        set { this.connection = value; }
    }
  }
```

### <a name="implementing-removedrive"></a><span data-ttu-id="483ee-132">Implementazione RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="483ee-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="483ee-133">Il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo viene chiamato dal motore di Windows PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="483ee-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet.</span></span> <span data-ttu-id="483ee-134">Il metodo di questo provider si chiude la connessione al database di Access.</span><span class="sxs-lookup"><span data-stu-id="483ee-134">The method in this provider closes the connection to the Access database.</span></span>

```csharp
protected override PSDriveInfo RemoveDrive(PSDriveInfo drive)
    {
      // Check if drive object is null.
      if (drive == null)
      {
        WriteError(new ErrorRecord(
                   new ArgumentNullException("drive"),
                   "NullDrive",
                   ErrorCategory.InvalidArgument,
                   drive));

        return null;
      }

      // Close the ODBC connection to the drive.
      AccessDBPSDriveInfo accessDBPSDriveInfo = drive as AccessDBPSDriveInfo;

      if (accessDBPSDriveInfo == null)
      {
         return null;
      }

      accessDBPSDriveInfo.Connection.Close();

      return accessDBPSDriveInfo;
    }
```