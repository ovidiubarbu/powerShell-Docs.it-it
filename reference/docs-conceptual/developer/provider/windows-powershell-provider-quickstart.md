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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359920"
---
# <a name="windows-powershell-provider-quickstart"></a>Guida introduttiva del provider di Windows PowerShell

In questo argomento viene illustrato come creare un provider di Windows PowerShell con funzionalità di base per la creazione di una nuova unità. Per informazioni generali sui provider, vedere [Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md). Per esempi di provider con funzionalità più complete, vedere [esempi di provider](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>Scrittura di un provider di base

La funzionalità di base di un provider di Windows PowerShell consiste nel creare e rimuovere unità. In questo esempio vengono implementati i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) della classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . Si vedrà anche come dichiarare una classe di provider.

Quando si scrive un provider, è possibile specificare unità predefinite che vengono create automaticamente quando il provider è disponibile. Si definisce anche un metodo per creare nuove unità che usano tale provider.

Gli esempi forniti in questo argomento si basano sull'esempio [AccessDBProviderSample02](./accessdbprovidersample02.md) , che fa parte di un esempio più ampio che rappresenta un database di Access come unità di Windows PowerShell.

### <a name="setting-up-the-project"></a>Impostazione del progetto

In Visual Studio creare un progetto libreria di classi denominato AccessDBProviderSample. Completare i passaggi seguenti per configurare il progetto in modo che Windows PowerShell venga avviato e il provider verrà caricato nella sessione, quando si compila e si avvia il progetto.

##### <a name="configure-the-provider-project"></a>Configurare il progetto del provider

1. Aggiungere l'assembly System. Management. Automation come riferimento al progetto.

2. Fare clic su **progetto > proprietà AccessDBProviderSample > debug**. In **Avvia progetto**, fare clic su **Avvia programma esterno**e passare al file eseguibile di Windows PowerShell (in genere c:\Windows\system32\WindowsPowerShell\v1.0\\. PowerShell. exe).

3. In **Opzioni di avvio**immettere quanto segue nella casella **argomenti della riga di comando** : `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe provider

Il provider deriva dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) . La maggior parte dei provider che forniscono funzionalità reali (accesso e manipolazione di elementi, spostamento nell'archivio dati e recupero e impostazione del contenuto degli elementi) derivano dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Oltre a specificare che la classe deriva da [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), è necessario decorarla con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) come illustrato nell'esempio.

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

### <a name="implementing-newdrive"></a>Implementazione di nuovaunità

Il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) viene chiamato dal motore di Windows PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. NewPSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.Newpsdrivecommand) specificando il nome del provider. Il parametro PSDriveInfo viene passato dal motore di Windows PowerShell e il metodo restituisce la nuova unità al motore di Windows PowerShell. Questo metodo deve essere dichiarato all'interno della classe creata in precedenza.

Il metodo verifica prima di tutto che sia l'oggetto unità che la radice dell'unità passati, restituendo `null` se nessuna di esse. USA quindi un costruttore della classe interna AccessDBPSDriveInfo per creare una nuova unità e una connessione al database di Access rappresentato dall'unità.

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

Di seguito è riportata la classe interna AccessDBPSDriveInfo che include il costruttore utilizzato per creare una nuova unità e contiene le informazioni sullo stato per l'unità.

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

### <a name="implementing-removedrive"></a>Implementazione di RemoveDrive

Il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) viene chiamato dal motore di Windows PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. RemovePSDriveCommand](/dotnet/api/Microsoft.PowerShell.Commands.removepsdrivecommand) . Il metodo in questo provider chiude la connessione al database di Access.

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