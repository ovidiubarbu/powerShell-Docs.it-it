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
# <a name="windows-powershell-provider-quickstart"></a>Guida introduttiva del provider di Windows PowerShell

Questo argomento illustra come creare un provider di Windows PowerShell con le funzionalità di base della creazione di una nuova unità. Per informazioni generali sui provider, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md). Per esempi di provider di funzionalità più complete, vedere [esempi di Provider](./provider-samples.md).

## <a name="writing-a-basic-provider"></a>La scrittura di un provider di base

La funzionalità di base di un provider di Windows PowerShell consiste nel creare e rimuovere le unità. In questo esempio, Implementiamo le [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) e [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) i metodi del [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. Si vedrà anche come dichiarare una classe di provider.

Quando si scrive un provider, è possibile specificare le unità-unità di predefiniti che vengono create automaticamente quando il provider è disponibile. È anche possibile definire un metodo per creare nuove unità che utilizzano tale provider.

Gli esempi forniti in questo argomento si basano le [AccessDBProviderSample02](./accessdbprovidersample02.md) esempio, che fa parte di un campione di dimensioni maggiori che rappresenta un database di Access come un'unità di Windows PowerShell.

### <a name="setting-up-the-project"></a>Impostazione del progetto

In Visual Studio, creare un progetto libreria di classi denominato AccessDBProviderSample. Completare i passaggi seguenti per configurare il progetto in modo che Windows PowerShell verrà avviato e il provider verrà caricato nella sessione, quando si compila e avvia il tuo progetto.

##### <a name="configure-the-provider-project"></a>Configurare il provider di progetto

1. Aggiungere l'assembly Automation come un riferimento al progetto.

2. Fare clic su **progetto > proprietà AccessDBProviderSample > Debug**. Nelle **progetto di avvio**, fare clic su **Avvia programma esterno**e passare al file eseguibile di Windows PowerShell (in genere c:\Windows\System32\WindowsPowerShell\v1.0\\. powershell.exe).

3. Sotto **opzioni di avvio**, immettere quanto segue nel **argomenti della riga di comando** casella: `-noexit -command "[reflection.assembly]::loadFrom(AccessDBProviderSample.dll' ) | import-module"`

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe di provider

Il provider di servizi deriva dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe. La maggior parte dei provider che forniscono funzionalità reale (l'accesso e la modifica di elementi, passando l'archivio dati e ottenere e impostare il contenuto degli elementi) derivano dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.

Oltre a specificare che la classe deriva da [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider), è necessario decorare con il [ System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute) come illustrato nell'esempio.

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

### <a name="implementing-newdrive"></a>Implementazione NewDrive

Il [System.Management.Automation.Provider.Drivecmdletprovider.Newdrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.NewDrive) metodo viene chiamato dal motore di Windows PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.New-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.New-PSDrive)che specifica il nome del provider di cmdlet. Il parametro PSDriveInfo viene passato dal motore di Windows PowerShell e il metodo restituisce la nuova unità al motore di Windows PowerShell. Questo metodo deve essere dichiarato all'interno della classe creata in precedenza.

Il metodo controlla prima di tutto per assicurarsi che l'oggetto unità sia alla radice dell'unità che sono stati passati esiste, restituendo `null` se una di esse non li supportano. Un costruttore della classe interna AccessDBPSDriveInfo viene quindi utilizzato per creare una nuova unità e rappresenta una connessione al database di Access, l'unità.

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

Di seguito è la classe interna AccessDBPSDriveInfo che include il costruttore usato per creare una nuova unità e contiene le informazioni sullo stato per l'unità.

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

### <a name="implementing-removedrive"></a>Implementazione RemoveDrive

Il [System.Management.Automation.Provider.Drivecmdletprovider.Removedrive*](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider.RemoveDrive) metodo viene chiamato dal motore di Windows PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.Remove-PSDrive](/dotnet/api/Microsoft.PowerShell.Commands.Remove-PSDrive) cmdlet. Il metodo di questo provider si chiude la connessione al database di Access.

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