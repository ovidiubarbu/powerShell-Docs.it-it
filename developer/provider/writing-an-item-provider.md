---
title: La scrittura di un provider di elementi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734708"
---
# <a name="writing-an-item-provider"></a>Scrittura di un provider di elementi

Questo argomento descrive come implementare i metodi di un provider di Windows PowerShell accedano e modificano gli elementi nell'archivio dati. Per essere in grado di accedere agli elementi, un provider deve derivare dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.

Il provider negli esempi in questo argomento Usa un database di Access come suo archivio dati. Esistono diversi metodi helper e classi che consentono di interagire con il database. Per l'esempio completo che include i metodi di supporto, vedere [AccessDBProviderSample03](./accessdbprovidersample03.md)

Per altre informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementazione dei metodi di elemento

Il [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe espone diversi metodi che possono essere usati per accedere e modificare gli elementi in un archivio dati. Per un elenco completo di questi metodi, vedere [ItemCmdletProvider metodi](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods). In questo esempio verrà implementato quattro di questi metodi. [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Ottiene un elemento in un percorso specificato. [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) imposta il valore dell'elemento specificato. [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica l'esistenza di un elemento nel percorso specificato. [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controlla un percorso per verificare se viene eseguito il mapping a una posizione nell'archivio dati.

> [!NOTE]
> Questo argomento si basa sulle informazioni presenti [avvio rapido di Provider di Windows PowerShell](./windows-powershell-provider-quickstart.md). In questo argomento non comprende le nozioni di base di come configurare un progetto di provider, o come implementare i metodi ereditati dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe che creare e rimuovere le unità.

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe di provider

Dichiarare il provider di derivare dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe e decorarla con il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementazione GetItem

Il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) viene chiamato dal motore di PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) cmdlet il provider. Il metodo restituisce l'elemento nel percorso specificato. Nell'esempio del database l'accesso, il metodo controlla se l'elemento è l'unità, una tabella nel database o una riga nel database. Il metodo invia l'elemento al motore di PowerShell chiamando il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (metodo).

```csharp
protected override void GetItem(string path)
      {
          // check if the path represented is a drive
          if (PathIsDrive(path))
          {
              WriteItemObject(this.PSDriveInfo, path, true);
              return;
          }// if (PathIsDrive...

           // Get table name and row information from the path and do
           // necessary actions
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               DatabaseTableInfo table = GetTable(tableName);
               WriteItemObject(table, path, true);
           }
           else if (type == PathType.Row)
           {
               DatabaseRowInfo row = GetRow(tableName, rowNumber);
               WriteItemObject(row, path, false);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

### <a name="implementing-setitem"></a>Implementazione SetItem

Il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo viene chiamato per il motore chiama PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) cmdlet. Imposta il valore dell'elemento nel percorso specificato.

Nell'esempio del database di Access, è opportuno impostare il valore di un elemento solo se tale elemento è una riga, in modo che il metodo genera un'eccezione [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) quando l'elemento non è una riga.

```csharp
protected override void SetItem(string path, object values)
       {
           // Get type, table name and row number from the path specified
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type != PathType.Row)
           {
               WriteError(new ErrorRecord(new NotSupportedException(
                     "SetNotSupported"), "",
                  ErrorCategory.InvalidOperation, path));

               return;
           }

           // Get in-memory representation of table
           OdbcDataAdapter da = GetAdapterForTable(tableName);

           if (da == null)
           {
               return;
           }
           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           if (rowNumber >= table.Rows.Count)
           {
               // The specified row number has to be available. If not
               // NewItem has to be used to add a new row
               throw new ArgumentException("Row specified is not available");
           } // if (rowNum...

           string[] colValues = (values as string).Split(',');

           // set the specified row
           DataRow row = table.Rows[rowNumber];

           for (int i = 0; i < colValues.Length; i++)
           {
               row[i] = colValues[i];
           }

           // Update the table
           if (ShouldProcess(path, "SetItem"))
           {
               da.Update(ds, tableName);
           }

       }
```

### <a name="implementing-itemexists"></a>Implementazione ItemExists

Il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodo viene chiamato dal motore di PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) cmdlet. Il metodo determina se è presente un elemento nel percorso specificato. Se l'elemento esiste, il metodo passa al motore di PowerShell chiamando [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

```csharp
protected override bool ItemExists(string path)
       {
           // check if the path represented is a drive
           if (PathIsDrive(path))
           {
               return true;
           }

           // Obtain type, table name and row number from path
           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           DatabaseTableInfo table = GetTable(tableName);

           if (type == PathType.Table)
           {
               // if specified path represents a table then DatabaseTableInfo
               // object for the same should exist
               if (table != null)
               {
                   return true;
               }
           }
           else if (type == PathType.Row)
           {
               // if specified path represents a row then DatabaseTableInfo should
               // exist for the table and then specified row number must be within
               // the maximum row count in the table
               if (table != null && rowNumber < table.RowCount)
               {
                   return true;
               }
           }

           return false;

       }
```

### <a name="implementing-isvalidpath"></a>Implementazione IsValidPath

Il [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodo controlla se il percorso specificato è sintatticamente valido per il provider corrente. Non controlla se un elemento presente nel percorso.

```csharp
protected override bool IsValidPath(string path)
       {
           bool result = true;

           // check if the path is null or empty
           if (String.IsNullOrEmpty(path))
           {
               result = false;
           }

           // convert all separators in the path to a uniform one
           path = NormalizePath(path);

           // split the path into individual chunks
           string[] pathChunks = path.Split(pathSeparator.ToCharArray());

           foreach (string pathChunk in pathChunks)
           {
               if (pathChunk.Length == 0)
               {
                   result = false;
               }
           }
           return result;
       }
```

## <a name="next-steps"></a>Passaggi successivi

Un provider del mondo reale tipico è in grado di supportare gli elementi che contengono altri elementi e di spostamento di elementi da un percorso a un altro all'interno dell'unità. Per un esempio di un provider che supporti i contenitori, vedere [scrittura di un provider di contenitore](./writing-a-container-provider.md). Per un esempio di un provider che supporta lo spostamento di elementi, vedere [scrittura di un provider di navigazione](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di contenitore](./writing-a-container-provider.md)

[Scrittura di un provider di navigazione](./writing-a-navigation-provider.md)

[Cenni preliminari sul Provider PowerShell di Windows](./windows-powershell-provider-overview.md)
