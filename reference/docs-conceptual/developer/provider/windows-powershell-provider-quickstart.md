---
title: Guida introduttiva del provider Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3e879ba7-c334-460b-94a1-3e9b63d3d8de
caps.latest.revision: 5
ms.openlocfilehash: 949c0d63b1e5bca1bfe670362df4297c29e98fcc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359920"
---
# <a name="windows-powershell-provider-quickstart"></a><span data-ttu-id="66651-102">Guida introduttiva del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="66651-102">Windows PowerShell Provider Quickstart</span></span>

<span data-ttu-id="66651-103">In questo argomento viene illustrato come creare un provider di Windows PowerShell con funzionalità di base per la creazione di una nuova unità.</span><span class="sxs-lookup"><span data-stu-id="66651-103">This topic explains how to create a Windows PowerShell provider that has basic functionality of creating a new drive.</span></span> <span data-ttu-id="66651-104">Per informazioni generali sui provider, vedere [Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="66651-104">For general information about providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="66651-105">Per esempi di provider con funzionalità più complete, vedere [esempi di provider](./provider-samples.md).</span><span class="sxs-lookup"><span data-stu-id="66651-105">For examples of providers with more complete functionality, see [Provider Samples](./provider-samples.md).</span></span>

## <a name="writing-a-basic-provider"></a><span data-ttu-id="66651-106">Scrittura di un provider di base</span><span class="sxs-lookup"><span data-stu-id="66651-106">Writing a basic provider</span></span>

<span data-ttu-id="66651-107">La funzionalità di base di un provider di Windows PowerShell consiste nel creare e rimuovere unità.</span><span class="sxs-lookup"><span data-stu-id="66651-107">The most basic functionality of a Windows PowerShell provider is to create and remove drives.</span></span> <span data-ttu-id="66651-108">In questo esempio vengono implementati i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) del [ Classe System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="66651-108">In this example, we implement the [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) and [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) methods of the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="66651-109">Si vedrà anche come dichiarare una classe di provider.</span><span class="sxs-lookup"><span data-stu-id="66651-109">You will also see how to declare a provider class.</span></span>

<span data-ttu-id="66651-110">Quando si scrive un provider, è possibile specificare unità predefinite che vengono create automaticamente quando il provider è disponibile.</span><span class="sxs-lookup"><span data-stu-id="66651-110">When you write a provider, you can specify default drives-drives that are created automatically when the provider is available.</span></span> <span data-ttu-id="66651-111">Si definisce anche un metodo per creare nuove unità che usano tale provider.</span><span class="sxs-lookup"><span data-stu-id="66651-111">You also define a method to create new drives that use that provider.</span></span>

<span data-ttu-id="66651-112">Gli esempi forniti in questo argomento si basano sull'esempio [AccessDBProviderSample02](./accessdbprovidersample02.md) , che fa parte di un esempio più ampio che rappresenta un database di Access come unità di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66651-112">The examples provided in this topic are based on the [AccessDBProviderSample02](./accessdbprovidersample02.md) sample, which is part of a larger sample that represents an Access database as a Windows PowerShell drive.</span></span>

### <a name="setting-up-the-project"></a><span data-ttu-id="66651-113">Impostazione del progetto</span><span class="sxs-lookup"><span data-stu-id="66651-113">Setting up the project</span></span>

<span data-ttu-id="66651-114">In Visual Studio creare un progetto libreria di classi denominato AccessDBProviderSample.</span><span class="sxs-lookup"><span data-stu-id="66651-114">In Visual Studio, create a Class Library project named AccessDBProviderSample.</span></span> <span data-ttu-id="66651-115">Completare i passaggi seguenti per configurare il progetto in modo che Windows PowerShell venga avviato e il provider verrà caricato nella sessione, quando si compila e si avvia il progetto.</span><span class="sxs-lookup"><span data-stu-id="66651-115">Complete the following steps to configure your project so that Windows PowerShell will start, and the provider will be loaded into the session, when you build and start your project.</span></span>

##### <a name="configure-the-provider-project"></a><span data-ttu-id="66651-116">Configurare il progetto del provider</span><span class="sxs-lookup"><span data-stu-id="66651-116">Configure the provider project</span></span>

1. <span data-ttu-id="66651-117">Aggiungere l'assembly System. Management. Automation come riferimento al progetto.</span><span class="sxs-lookup"><span data-stu-id="66651-117">Add the System.Management.Automation assembly as a reference to your project.</span></span>

2. <span data-ttu-id="66651-118">Fare clic su **progetto > proprietà AccessDBProviderSample > debug**.</span><span class="sxs-lookup"><span data-stu-id="66651-118">Click **Project > AccessDBProviderSample Properties > Debug**.</span></span> <span data-ttu-id="66651-119">In **Avvia progetto**, fare clic su **Avvia programma esterno**e passare al file eseguibile di Windows PowerShell (in genere c:\windows\system32\windowspowershell\ V1.0\\.powershell.exe).</span><span class="sxs-lookup"><span data-stu-id="66651-119">In **Start project**, click **Start external program**, and navigate to the Windows PowerShell executable (typically c:\Windows\System32\WindowsPowerShell\v1.0\\.powershell.exe).</span></span>

3. <span data-ttu-id="66651-120">In **Opzioni di avvio**immettere quanto segue nella casella **argomenti della riga di comando** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span><span class="sxs-lookup"><span data-stu-id="66651-120">Under **Start Options**, enter the following into the **Command line arguments** box: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="66651-121">Dichiarazione della classe provider</span><span class="sxs-lookup"><span data-stu-id="66651-121">Declaring the provider class</span></span>

<span data-ttu-id="66651-122">Il provider deriva dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="66651-122">Our provider derives from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class.</span></span> <span data-ttu-id="66651-123">La maggior parte dei provider che forniscono funzionalità reali (accesso e manipolazione di elementi, spostamento nell'archivio dati e recupero e impostazione del contenuto degli elementi) derivano dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="66651-123">Most providers that provide real functionality (accessing and manipulating items, navigating the data store, and getting and setting content of items) derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="66651-124">Oltre a specificare che la classe deriva da [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), è necessario decorarla con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) come illustrato nell'esempio .</span><span class="sxs-lookup"><span data-stu-id="66651-124">In addition to specifying that the class derives from [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), you must decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) as shown in the example.</span></span>

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

### <a name="implementing-newdrive"></a><span data-ttu-id="66651-125">Implementazione di nuovaunità</span><span class="sxs-lookup"><span data-stu-id="66651-125">Implementing NewDrive</span></span>

<span data-ttu-id="66651-126">Il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) viene chiamato dal motore di Windows PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) specificando il nome del provider.</span><span class="sxs-lookup"><span data-stu-id="66651-126">The [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) cmdlet specifying the name of your provider.</span></span> <span data-ttu-id="66651-127">Il parametro PSDriveInfo viene passato dal motore di Windows PowerShell e il metodo restituisce la nuova unità al motore di Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="66651-127">The PSDriveInfo parameter is passed by the Windows PowerShell engine, and the method returns the new drive to the Windows PowerShell engine.</span></span> <span data-ttu-id="66651-128">Questo metodo deve essere dichiarato all'interno della classe creata in precedenza.</span><span class="sxs-lookup"><span data-stu-id="66651-128">This method must be declared within the class created above.</span></span>

<span data-ttu-id="66651-129">Il metodo verifica prima di tutto che sia l'oggetto unità che la radice dell'unità passati, restituendo `null` se nessuna di esse.</span><span class="sxs-lookup"><span data-stu-id="66651-129">The method first checks to make sure both the drive object and the drive root that were passed in exist, returning `null` if either of them do not.</span></span> <span data-ttu-id="66651-130">USA quindi un costruttore della classe interna AccessDBPSDriveInfo per creare una nuova unità e una connessione al database di Access rappresentato dall'unità.</span><span class="sxs-lookup"><span data-stu-id="66651-130">It then uses a constructor of the internal class AccessDBPSDriveInfo to create a new drive and a connection to the Access database the drive represents.</span></span>

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

<span data-ttu-id="66651-131">Di seguito è riportata la classe interna AccessDBPSDriveInfo che include il costruttore utilizzato per creare una nuova unità e contiene le informazioni sullo stato per l'unità.</span><span class="sxs-lookup"><span data-stu-id="66651-131">The following is the AccessDBPSDriveInfo internal class that includes the constructor used to create a new drive, and contains the state information for the drive.</span></span>

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

### <a name="implementing-removedrive"></a><span data-ttu-id="66651-132">Implementazione di RemoveDrive</span><span class="sxs-lookup"><span data-stu-id="66651-132">Implementing RemoveDrive</span></span>

<span data-ttu-id="66651-133">Il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive \*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) viene chiamato dal motore di Windows PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) .</span><span class="sxs-lookup"><span data-stu-id="66651-133">The [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive\*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) method is called by the Windows PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) cmdlet.</span></span> <span data-ttu-id="66651-134">Il metodo in questo provider chiude la connessione al database di Access.</span><span class="sxs-lookup"><span data-stu-id="66651-134">The method in this provider closes the connection to the Access database.</span></span>

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