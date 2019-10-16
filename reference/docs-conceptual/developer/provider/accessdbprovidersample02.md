---
title: AccessDBProviderSample02 | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aaf9351e-157f-4d48-8b8f-1fd64855b682
caps.latest.revision: 10
ms.openlocfilehash: d291e401bbf3da998735ebb00f1eb35521f9a19c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366370"
---
# <a name="accessdbprovidersample02"></a>AccessDBProviderSample02

Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per supportare le chiamate al `New-PSDrive` e i cmdlet `Remove-PSDrive`. La classe del provider in questo esempio deriva dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

## <a name="demonstrates"></a>Dimostra

> [!IMPORTANT]
> È probabile che la classe del provider derivi da una delle classi seguenti e possa implementare altre interfacce del provider:
>
> -   Classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Vedere [AccessDBProviderSample03](./accessdbprovidersample03.md).
> -   Classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).
> -   Classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) . Vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).
>
> Per ulteriori informazioni sulla scelta della classe del provider da derivare da in base alle funzionalità del provider, vedere [progettazione del provider di Windows PowerShell](./provider-types.md).

In questo esempio vengono illustrate le operazioni seguenti:

- Dichiarazione dell'attributo `CmdletProvider`.

- Definizione di una classe di provider che guida dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) .

- Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) per supportare la creazione di nuove unità. In questo esempio non viene illustrato come aggiungere parametri dinamici al cmdlet `New-PSDrive`.

- Sovrascrivere il metodo [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) per supportare la rimozione delle unità esistenti.

## <a name="example"></a>Esempio

Questo esempio illustra come sovrascrivere i metodi [System. Management. Automation. provider. Drivecmdletprovider. nuovaunità *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System. Management. Automation. provider. Drivecmdletprovider. Removedrive *](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) . Per questo provider di esempio, quando viene creata un'unità, le informazioni di connessione vengono archiviate in un oggetto `AccessDBPsDriveInfo`.

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

  /// <summary>
  /// This sample implements a Windows PowerShell provider class
  /// that acts upon an Access database.
  /// </summary>
  /// <remarks>
  /// This example demonstrates only the drive overrides used to
  /// add and remove drives from the database.</remarks>
  [CmdletProvider("AccessDB", ProviderCapabilities.None)]
  public class AccessDBProvider : DriveCmdletProvider
  {
    #region Drive Manipulation

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// New-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method creates a connection to the database
    /// file and sets the Connection property of the PSDriveInfo object.
    /// </summary>
    /// <param name="drive">
    /// Information describing the drive to create.
    /// </param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the new drive.</returns>
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
    } // End NewDrive.

    /// <summary>
    /// The Windows PowerShell engine calls this method when the
    /// Remove-PSDrive cmdlet is run and the path to this provider is
    /// specified. This method closes the ODBC connection of the drive.
    /// </summary>
    /// <param name="drive">The drive to remove.</param>
    /// <returns>An accessDBPSDriveInfo object that represents
    /// the removed drive.</returns>
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
    } // End RemoveDrive.

    #endregion Drive Manipulation
  } // End AccessDBProvider class.

  #endregion AccessDBProvider

  #region AccessDBPSDriveInfo

  /// <summary>
  /// Any state associated with the drive is held here. In this
  /// case, the state information is the connection to the database.
  /// </summary>
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
  } // End AccessDBPSDriveInfo class.

  #endregion AccessDBPSDriveInfo
}
```

## <a name="see-also"></a>Vedere anche

[System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider)

[System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider)

[System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider)

[Progettazione del provider di Windows PowerShell](./provider-types.md)