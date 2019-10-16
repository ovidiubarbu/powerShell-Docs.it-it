---
title: Scrittura di un provider di contenitori | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 524fd900-c0fe-4d13-87f2-14903a8fd5a4
caps.latest.revision: 5
ms.openlocfilehash: 48ab9102e8f1b17b3b533cc3b0aa1dacef0e2076
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72366240"
---
# <a name="writing-a-container-provider"></a>Scrittura di un provider di contenitore

In questo argomento viene descritto come implementare i metodi di un provider di Windows PowerShell che supportano elementi che contengono altri elementi, ad esempio le cartelle del provider file system. Per poter supportare i contenitori, un provider deve derivare dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .

Nel provider degli esempi di questo argomento viene utilizzato un database di Access come archivio dati. Sono disponibili diversi metodi e classi helper che consentono di interagire con il database. Per l'esempio completo che include i metodi helper, vedere [AccessDBProviderSample04](./accessdbprovidersample04.md).

Per ulteriori informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sui provider di Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-container-methods"></a>Implementazione di metodi contenitore

La classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) implementa i metodi che supportano i contenitori, nonché creare, copiare e rimuovere elementi. Per un elenco completo di questi metodi, vedere [System. Management. Automation. provider. ContainerCmdletProvider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider?view=pscore-6.2.0#methods).

> [!NOTE]
> Questo argomento si basa sulle informazioni fornite nella [Guida introduttiva del provider di Windows PowerShell](./windows-powershell-provider-quickstart.md). Questo argomento non illustra le nozioni di base su come configurare un progetto di provider o su come implementare i metodi ereditati dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) che creano e rimuovono unità. In questo argomento non viene inoltre illustrato come implementare metodi esposti dalla classe [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) . Per un esempio in cui viene illustrato come implementare i cmdlet di elemento, vedere [scrittura di un provider di elementi](./writing-an-item-provider.md).

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe provider

Dichiarare il provider per la derivazione dalla classe [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) e decorarlo con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : ContainerCmdletProvider
   {

   }
```

### <a name="implementing-getchilditems"></a>Implementazione di getchilditems

Il motore di PowerShell chiama il metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. GetChildItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.Getchilditemcommand) . Questo metodo ottiene gli elementi figlio dell'elemento nel percorso specificato.

Nell'esempio di database di Access il comportamento del metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) dipende dal tipo dell'elemento specificato. Se l'elemento è l'unità, gli elementi figlio sono tabelle e il metodo restituisce il set di tabelle dal database. Se l'elemento specificato è una tabella, gli elementi figlio sono le righe di tale tabella. Se l'elemento è una riga, non ha elementi figlio e il metodo restituisce solo tale riga. Tutti gli elementi figlio vengono restituiti al motore di PowerShell dal metodo [System. Management. Automation. provider. CmdletProvider. Writeitemobject *](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) .

```csharp
protected override void GetChildItems(string path, bool recurse)
       {
           // If path represented is a drive then the children in the path are
           // tables. Hence all tables in the drive represented will have to be
           // returned
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table, path, true);

                   // if the specified item exists and recurse has been set then
                   // all child items within it have to be obtained as well
                   if (ItemExists(path) && recurse)
                   {
                       GetChildItems(path + pathSeparator + table.Name, recurse);
                   }
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get the table name, row number and type of path from the
               // path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Obtain all the rows within the table
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);
                   WriteItemObject(row, path + pathSeparator + row.RowNumber,
                               false);
               }
               else
               {
                   // In this case, the path specified is not valid
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-getchildnames"></a>Implementazione di GetChildNames

Il metodo [System. Management. Automation. provider. Containercmdletprovider. Getchildnames *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildNames) è simile al metodo [System. Management. Automation. provider. Containercmdletprovider. getchilditems *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.GetChildItems) , ad eccezione del fatto che restituisce solo Proprietà Name degli elementi e non gli elementi stessi.

```csharp
protected override void GetChildNames(string path,
                                     ReturnContainers returnContainers)
       {
           // If the path represented is a drive, then the child items are
           // tables. get the names of all the tables in the drive.
           if (PathIsDrive(path))
           {
               foreach (DatabaseTableInfo table in GetTables())
               {
                   WriteItemObject(table.Name, path, true);
               } // foreach (DatabaseTableInfo...
           } // if (PathIsDrive...
           else
           {
               // Get type, table name and row number from path specified
               string tableName;
               int rowNumber;

               PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

               if (type == PathType.Table)
               {
                   // Get all the rows in the table and then write out the
                   // row numbers.
                   foreach (DatabaseRowInfo row in GetRows(tableName))
                   {
                       WriteItemObject(row.RowNumber, path, false);
                   } // foreach (DatabaseRowInfo...
               }
               else if (type == PathType.Row)
               {
                   // In this case the user has directly specified a row, hence
                   // just give that particular row
                   DatabaseRowInfo row = GetRow(tableName, rowNumber);

                   WriteItemObject(row.RowNumber, path, false);
               }
               else
               {
                   ThrowTerminatingInvalidPathException(path);
               }
           } // else
       }
```

### <a name="implementing-newitem"></a>Implementazione di NewItem

Il metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) crea un nuovo elemento del tipo specificato nel percorso specificato. Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. NewItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.newitemcommand) .

In questo esempio, il metodo implementa la logica per determinare che il percorso e il tipo corrispondono. In altre condizioni, è possibile creare solo una tabella direttamente sotto l'unità (il database) ed è possibile creare solo una riga in una tabella. Se il percorso e il tipo di elemento specificati non corrispondono in questo modo, il metodo genera un'eccezione.

```csharp
protected override void NewItem(string path, string type,
                                   object newItemValue)
       {
           string tableName;
           int rowNumber;

           PathType pt = GetNamesFromPath(path, out tableName, out rowNumber);

           if (pt == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           // Check if type is either "table" or "row", if not throw an
           // exception
           if (!String.Equals(type, "table", StringComparison.OrdinalIgnoreCase)
               && !String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
           {
               WriteError(new ErrorRecord
                                 (new ArgumentException("Type must be either a table or row"),
                                     "CannotCreateSpecifiedObject",
                                        ErrorCategory.InvalidArgument,
                                             path
                                  )
                         );

               throw new ArgumentException("This provider can only create items of type \"table\" or \"row\"");
           }

           // Path type is the type of path of the container. So if a drive
           // is specified, then a table can be created under it and if a table
           // is specified, then a row can be created under it. For the sake of
           // completeness, if a row is specified, then if the row specified by
           // the path does not exist, a new row is created. However, the row
           // number may not match as the row numbers only get incremented based
           // on the number of rows

           if (PathIsDrive(path))
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   // Execute command using ODBC connection to create a table
                   try
                   {
                       // create the table using an sql statement
                       string newTableName = newItemValue.ToString();

                       if (!TableNameIsValid(newTableName))
                       {
                           return;
                       }
                       string sql = "create table " + newTableName
                                            + " (ID INT)";

                       // Create the table using the Odbc connection from the
                       // drive.
                       AccessDBPSDriveInfo di = this.PSDriveInfo as AccessDBPSDriveInfo;

                       if (di == null)
                       {
                           return;
                       }
                       OdbcConnection connection = di.Connection;

                       if (ShouldProcess(newTableName, "create"))
                       {
                           OdbcCommand cmd = new OdbcCommand(sql, connection);
                           cmd.ExecuteScalar();
                       }
                   }
                   catch (Exception ex)
                   {
                       WriteError(new ErrorRecord(ex, "CannotCreateSpecifiedTable",
                                 ErrorCategory.InvalidOperation, path)
                                 );
                   }
               } // if (String...
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   throw new
                       ArgumentException("A row cannot be created under a database, specify a path that represents a Table");
               }
           }// if (PathIsDrive...
           else
           {
               if (String.Equals(type, "table", StringComparison.OrdinalIgnoreCase))
               {
                   if (rowNumber < 0)
                   {
                       throw new
                           ArgumentException("A table cannot be created within another table, specify a path that represents a database");
                   }
                   else
                   {
                       throw new
                           ArgumentException("A table cannot be created inside a row, specify a path that represents a database");
                   }
               } //if (String.Equals....
               // if path specified is a row, create a new row
               else if (String.Equals(type, "row", StringComparison.OrdinalIgnoreCase))
               {
                   // The user is required to specify the values to be inserted
                   // into the table in a single string separated by commas
                   string value = newItemValue as string;

                   if (String.IsNullOrEmpty(value))
                   {
                       throw new
                           ArgumentException("Value argument must have comma separated values of each column in a row");
                   }
                   string[] rowValues = value.Split(',');

                   OdbcDataAdapter da = GetAdapterForTable(tableName);

                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   if (rowValues.Length != table.Columns.Count)
                   {
                       string message =
                            String.Format(CultureInfo.CurrentCulture,
                                            "The table has {0} columns and the value specified must have so many comma separated values",
                                                table.Columns.Count);

                       throw new ArgumentException(message);
                   }

                   if (!Force && (rowNumber >=0 && rowNumber < table.Rows.Count))
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                                        "The row {0} already exists. To create a new row specify row number as {1}, or specify path to a table, or use the -Force parameter",
                                                            rowNumber, table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   if (rowNumber > table.Rows.Count)
                   {
                       string message = String.Format(CultureInfo.CurrentCulture,
                                            "To create a new row specify row number as {0}, or specify path to a table",
                                                table.Rows.Count);

                       throw new ArgumentException(message);
                   }

                   // Create a new row and update the row with the input
                   // provided by the user
                   DataRow row = table.NewRow();
                   for (int i = 0; i < rowValues.Length; i++)
                   {
                       row[i] = rowValues[i];
                   }
                   table.Rows.Add(row);

                   if (ShouldProcess(tableName, "update rows"))
                   {
                       // Update the table from memory back to the data source
                       da.Update(ds, tableName);
                   }

               }// else if (String...
           }// else ...

       }
```

### <a name="implementing-copyitem"></a>Implementazione di CopyItem

[System. Management. Automation. provider. ContainerCmdletProvider. CopyItem](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.CopyItem) copia l'elemento specificato nel percorso specificato. Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. CopyItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.copyitemcommand) . Questo metodo può anche essere ricorsivo, copiando tutti gli elementi figlio oltre all'elemento stesso.

Analogamente al metodo [System. Management. Automation. provider. Containercmdletprovider. NewItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.NewItem) , questo metodo esegue la logica per assicurarsi che l'elemento specificato sia del tipo corretto per il percorso in cui viene copiato. Se, ad esempio, il percorso di destinazione è una tabella, l'elemento da copiare deve essere una riga.

```csharp
protected override void CopyItem(string path, string copyPath, bool recurse)
       {
           string tableName, copyTableName;
           int rowNumber, copyRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);
           PathType copyType = GetNamesFromPath(copyPath, out copyTableName, out copyRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(copyPath);
           }

           // Get the table and the table to copy to
           OdbcDataAdapter da = GetAdapterForTable(tableName);
           if (da == null)
           {
               return;
           }

           DataSet ds = GetDataSetForTable(da, tableName);
           DataTable table = GetDataTable(ds, tableName);

           OdbcDataAdapter cda = GetAdapterForTable(copyTableName);
           if (cda == null)
           {
               return;
           }

           DataSet cds = GetDataSetForTable(cda, copyTableName);
           DataTable copyTable = GetDataTable(cds, copyTableName);

           // if source represents a table
           if (type == PathType.Table)
           {
               // if copyPath does not represent a table
               if (copyType != PathType.Table)
               {
                   ArgumentException e = new ArgumentException("Table can only be copied on to another table location");

                   WriteError(new ErrorRecord(e, "PathNotValid",
                       ErrorCategory.InvalidArgument, copyPath));

                   throw e;
               }

               // if table already exists then force parameter should be set
               // to force a copy
               if (!Force && GetTable(copyTableName) != null)
               {
                   throw new ArgumentException("Specified path already exists");
               }

               for (int i = 0; i < table.Rows.Count; i++)
               {
                   DataRow row = table.Rows[i];
                   DataRow copyRow = copyTable.NewRow();

                   copyRow.ItemArray = row.ItemArray;
                   copyTable.Rows.Add(copyRow);
               }
           } // if (type == ...
           // if source represents a row
           else
           {
               if (copyType == PathType.Row)
               {
                   if (!Force && (copyRowNumber < copyTable.Rows.Count))
                   {
                       throw new ArgumentException("Specified path already exists.");
                   }

                   DataRow row = table.Rows[rowNumber];
                   DataRow copyRow = null;

                   if (copyRowNumber < copyTable.Rows.Count)
                   {
                       // copy to an existing row
                       copyRow = copyTable.Rows[copyRowNumber];
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                   }
                   else if (copyRowNumber == copyTable.Rows.Count)
                   {
                       // copy to the next row in the table that will
                       // be created
                       copyRow = copyTable.NewRow();
                       copyRow.ItemArray = row.ItemArray;
                       copyRow[0] = GetNextID(copyTable);
                       copyTable.Rows.Add(copyRow);
                   }
                   else
                   {
                       // attempting to copy to a nonexistent row or a row
                       // that cannot be created now - throw an exception
                       string message = String.Format(CultureInfo.CurrentCulture,
                                             "The item cannot be specified to the copied row. Specify row number as {0}, or specify a path to the table.",
                                                    table.Rows.Count);

                       throw new ArgumentException(message);
                   }
               }
               else
               {
                   // destination path specified represents a table,
                   // create a new row and copy the item
                   DataRow copyRow = copyTable.NewRow();
                   copyRow.ItemArray = table.Rows[rowNumber].ItemArray;
                   copyRow[0] = GetNextID(copyTable);
                   copyTable.Rows.Add(copyRow);
               }
           }

           if (ShouldProcess(copyTableName, "CopyItems"))
           {
               cda.Update(cds, copyTableName);
           }

       } //CopyItem
```

### <a name="implementing-removeitem"></a>Implementazione di RemoveItem

Il metodo [System. Management. Automation. provider. Containercmdletprovider. RemoveItem *](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider.RemoveItem) rimuove l'elemento in corrispondenza del percorso specificato. Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. RemoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.removeitemcommand) .

```csharp
protected override void RemoveItem(string path, bool recurse)
       {
           string tableName;
           int rowNumber = 0;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               // if recurse flag has been specified, delete all the rows as well
               if (recurse)
               {
                   OdbcDataAdapter da = GetAdapterForTable(tableName);
                   if (da == null)
                   {
                       return;
                   }

                   DataSet ds = GetDataSetForTable(da, tableName);
                   DataTable table = GetDataTable(ds, tableName);

                   for (int i = 0; i < table.Rows.Count; i++)
                   {
                       table.Rows[i].Delete();
                   }

                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       da.Update(ds, tableName);
                       RemoveTable(tableName);
                   }
               }//if (recurse...
               else
               {
                   // Remove the table
                   if (ShouldProcess(path, "RemoveItem"))
                   {
                       RemoveTable(tableName);
                   }
               }
           }
           else if (type == PathType.Row)
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               table.Rows[rowNumber].Delete();

               if (ShouldProcess(path, "RemoveItem"))
               {
                   da.Update(ds, tableName);
               }
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

       }
```

## <a name="next-steps"></a>Passaggi successivi

Un tipico provider reale è in grado di trasferire gli elementi da un percorso a un altro all'interno dell'unità. Per un esempio di provider che supporta lo spostamento di elementi, vedere [scrittura di un provider di navigazione](./writing-a-navigation-provider.md).

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di navigazione](./writing-a-navigation-provider.md)

[Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md)
