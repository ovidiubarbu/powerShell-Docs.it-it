---
title: Scrittura di un provider di elementi | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 606c880c-6cf1-4ea6-8730-dbf137bfabff
caps.latest.revision: 5
ms.openlocfilehash: 12d2cb8c40c9fd6278bb964a6259d03167536195
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359880"
---
# <a name="writing-an-item-provider"></a>Scrittura di un provider di elementi

In questo argomento viene descritto come implementare i metodi di un provider di Windows PowerShell per l'accesso e la modifica di elementi nell'archivio dati. Per poter accedere agli elementi, un provider deve derivare dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) .

Nel provider degli esempi di questo argomento viene utilizzato un database di Access come archivio dati. Sono disponibili diversi metodi e classi helper che consentono di interagire con il database. Per l'esempio completo che include i metodi helper, vedere [AccessDBProviderSample03](./accessdbprovidersample03.md)

Per ulteriori informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sui provider di Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-item-methods"></a>Implementazione di metodi di elemento

La classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) espone diversi metodi che possono essere usati per accedere e modificare gli elementi in un archivio dati. Per un elenco completo di questi metodi, vedere [Metodi ItemCmdletProvider](/dotnet/api/system.management.automation.provider.itemcmdletprovider?view=pscore-6.2.0#methods). In questo esempio vengono implementati quattro di questi metodi. [System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) ottiene un elemento in un percorso specificato. [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) imposta il valore dell'elemento specificato. [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) controlla se un elemento esiste nel percorso specificato. [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controlla un percorso per verificare se è mappato a una posizione nell'archivio dati.

> [!NOTE]
> Questo argomento si basa sulle informazioni fornite nella [Guida introduttiva del provider di Windows PowerShell](./windows-powershell-provider-quickstart.md). Questo argomento non illustra le nozioni di base su come configurare un progetto di provider o su come implementare i metodi ereditati dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) che creano e rimuovono unità.

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe provider

Dichiarare il provider per la derivazione dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) e decorarlo con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a>Implementazione di GetItem

[System. Management. Automation. provider. Itemcmdletprovider. GetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) viene chiamato dal motore di PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. GetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.getitemcommand) sul provider. Il metodo restituisce l'elemento in corrispondenza del percorso specificato. Nell'esempio database di Access il metodo controlla se l'elemento è l'unità stessa, una tabella nel database o una riga nel database. Il metodo invia l'elemento al motore di PowerShell chiamando il metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

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

### <a name="implementing-setitem"></a>Implementazione di SetItem

Il metodo [System. Management. Automation. provider. Itemcmdletprovider. SetItem *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) viene chiamato dal motore di PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. SetItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.setitemcommand) . Imposta il valore dell'elemento in corrispondenza del percorso specificato.

Nell'esempio di database di Access, è consigliabile impostare il valore di un elemento solo se tale elemento è una riga, quindi il metodo genera [NotSupportedException](/dotnet/api/system.notsupportedexception?view=netframework-4.8) quando l'elemento non è una riga.

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

### <a name="implementing-itemexists"></a>Implementazione di ItemExists

Il metodo [System. Management. Automation. provider. Itemcmdletprovider. itemExists *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) viene chiamato dal motore di PowerShell quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. TestPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.Testpathcommand) . Il metodo determina se è presente un elemento nel percorso specificato. Se l'elemento esiste, il metodo lo passa di nuovo al motore di PowerShell chiamando [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).

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

### <a name="implementing-isvalidpath"></a>Implementazione di IsValidPath

Il metodo [System. Management. Automation. provider. Itemcmdletprovider. IsValidPath *](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controlla se il percorso specificato è sintatticamente valido per il provider corrente. Non verifica se un elemento esiste nel percorso.

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

Un tipico provider reale è in grado di supportare elementi che contengono altri elementi e di trasferire gli elementi da un percorso a un altro all'interno dell'unità. Per un esempio di provider che supporta i contenitori, vedere [scrittura di un provider di contenitori](./writing-a-container-provider.md). Per un esempio di provider che supporta lo spostamento di elementi, vedere [scrittura di un provider di navigazione](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di contenitori](./writing-a-container-provider.md)

[Scrittura di un provider di navigazione](./writing-a-navigation-provider.md)

[Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md)
