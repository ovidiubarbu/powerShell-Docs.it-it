---
title: Scrittura di un provider di navigazione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 98bcfda0-6ee2-46f5-bbc7-5fab8b780d6a
caps.latest.revision: 5
ms.openlocfilehash: edb4d9944a527391983e068ddf07f4fac415c3f9
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359870"
---
# <a name="writing-a-navigation-provider"></a>Scrittura di un provider di navigazione

In questo argomento viene descritto come implementare i metodi di un provider di Windows PowerShell che supporta i contenitori annidati (archivi dati a più livelli), lo stato degli elementi e i percorsi relativi. Un provider di navigazione deve derivare dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .

Nel provider degli esempi di questo argomento viene utilizzato un database di Access come archivio dati. Sono disponibili diversi metodi e classi helper che consentono di interagire con il database. Per l'esempio completo che include i metodi helper, vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).

Per ulteriori informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sui provider di Windows PowerShell](./windows-powershell-provider-overview.md).

## <a name="implementing-navigation-methods"></a>Implementazione di metodi di navigazione

La classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementa i metodi che supportano i contenitori annidati, i percorsi relativi e gli elementi mobili. Per un elenco completo di questi metodi, vedere [Metodi NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).

> [!NOTE]
> Questo argomento si basa sulle informazioni fornite nella [Guida introduttiva del provider di Windows PowerShell](./windows-powershell-provider-quickstart.md). Questo argomento non illustra le nozioni di base su come configurare un progetto di provider o su come implementare i metodi ereditati dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) che creano e rimuovono unità. In questo argomento non viene inoltre illustrato come implementare metodi esposti dalle classi [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) . Per un esempio in cui viene illustrato come implementare i cmdlet di elemento, vedere [scrittura di un provider di elementi](./writing-an-item-provider.md). Per un esempio in cui viene illustrato come implementare i cmdlet del contenitore, vedere [scrittura di un provider di contenitori](./writing-a-container-provider.md).

### <a name="declaring-the-provider-class"></a>Dichiarazione della classe provider

Dichiarare il provider per la derivazione dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e decorarlo con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a>Implementazione di IsItemContainer

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. IsItemContainer *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) controlla se l'elemento in corrispondenza del percorso specificato è un contenitore.

```csharp
protected override bool IsItemContainer(string path)
      {
         if (PathIsDrive(path))
         {
             return true;
         }

         string[] pathChunks = ChunkPath(path);
         string tableName;
         int rowNumber;

         PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

         if (type == PathType.Table)
         {
            foreach (DatabaseTableInfo ti in GetTables())
            {
                if (string.Equals(ti.Name, tableName, StringComparison.OrdinalIgnoreCase))
                {
                    return true;
                }
            } // foreach (DatabaseTableInfo...
         } // if (pathChunks...

         return false;
      }
```

### <a name="implementing-getchildname"></a>Implementazione di getchildname

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. getchildname *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) ottiene la proprietà Name dell'elemento figlio nel percorso specificato. Se l'elemento in corrispondenza del percorso specificato non è figlio di un contenitore, questo metodo deve restituire il percorso.

```csharp
protected override string GetChildName(string path)
       {
           if (PathIsDrive(path))
           {
               return path;
           }

           string tableName;
           int rowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           if (type == PathType.Table)
           {
               return tableName;
           }
           else if (type == PathType.Row)
           {
               return rowNumber.ToString(CultureInfo.CurrentCulture);
           }
           else
           {
               ThrowTerminatingInvalidPathException(path);
           }

           return null;
       }
```

### <a name="implementing-getparentpath"></a>Implementazione di GetParentPath

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. GetParentPath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) ottiene il percorso dell'elemento padre dell'elemento nel percorso specificato. Se l'elemento in corrispondenza del percorso specificato è la radice dell'archivio dati (pertanto non ha un elemento padre), questo metodo deve restituire il percorso radice.

```csharp
protected override string GetParentPath(string path, string root)
       {
           // If root is specified then the path has to contain
           // the root. If not nothing should be returned
           if (!String.IsNullOrEmpty(root))
           {
               if (!path.Contains(root))
               {
                   return null;
               }
           }

           return path.Substring(0, path.LastIndexOf(pathSeparator, StringComparison.OrdinalIgnoreCase));
       }
```

### <a name="implementing-makepath"></a>Implementazione di MakePath

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) unisce un percorso padre specificato e un percorso figlio specificato per creare un percorso interno del provider. per informazioni sui tipi di percorso che i provider sono in grado di supportare, vedere [Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md). Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .

```csharp
protected override string MakePath(string parent, string child)
       {
           string result;

           string normalParent = NormalizePath(parent);
           normalParent = RemoveDriveFromPath(normalParent);
           string normalChild = NormalizePath(child);
           normalChild = RemoveDriveFromPath(normalChild);

           if (String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               result = String.Empty;
           }
           else if (String.IsNullOrEmpty(normalParent) && !String.IsNullOrEmpty(normalChild))
           {
               result = normalChild;
           }
           else if (!String.IsNullOrEmpty(normalParent) && String.IsNullOrEmpty(normalChild))
           {
               if (normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent;
               }
               else
               {
                   result = normalParent + pathSeparator;
               }
           } // else if (!String...
           else
           {
               if (!normalParent.Equals(String.Empty) &&
                   !normalParent.EndsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result = normalParent + pathSeparator;
               }
               else
               {
                   result = normalParent;
               }

               if (normalChild.StartsWith(pathSeparator, StringComparison.OrdinalIgnoreCase))
               {
                   result += normalChild.Substring(1);
               }
               else
               {
                   result += normalChild;
               }
           } // else

           return result;
       }
```

### <a name="implementing-normalizerelativepath"></a>Implementazione di NormalizeRelativePath

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) accetta i parametri `path` e `basepath` e restituisce un percorso normalizzato equivalente al parametro `path` e relativo a `basepath` parametro.

```csharp
protected override string NormalizeRelativePath(string path,
                                                            string basepath)
       {
           // Normalize the paths first
           string normalPath = NormalizePath(path);
           normalPath = RemoveDriveFromPath(normalPath);
           string normalBasePath = NormalizePath(basepath);
           normalBasePath = RemoveDriveFromPath(normalBasePath);

           if (String.IsNullOrEmpty(normalBasePath))
           {
               return normalPath;
           }
           else
           {
               if (!normalPath.Contains(normalBasePath))
               {
                   return null;
               }

               return normalPath.Substring(normalBasePath.Length + pathSeparator.Length);
           }
       }
```

### <a name="implementing-moveitem"></a>Implementazione di MoveItem

Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem *](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) sposta un elemento dal percorso specificato al percorso di destinazione specificato. Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .

```csharp
protected override void MoveItem(string path, string destination)
       {
           // Get type, table name and rowNumber from the path
           string tableName, destTableName;
           int rowNumber, destRowNumber;

           PathType type = GetNamesFromPath(path, out tableName, out rowNumber);

           PathType destType = GetNamesFromPath(destination, out destTableName,
                                    out destRowNumber);

           if (type == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(path);
           }

           if (destType == PathType.Invalid)
           {
               ThrowTerminatingInvalidPathException(destination);
           }

           if (type == PathType.Table)
           {
               ArgumentException e = new ArgumentException("Move not supported for tables");

               WriteError(new ErrorRecord(e, "MoveNotSupported",
                   ErrorCategory.InvalidArgument, path));

               throw e;
           }
           else
           {
               OdbcDataAdapter da = GetAdapterForTable(tableName);
               if (da == null)
               {
                   return;
               }

               DataSet ds = GetDataSetForTable(da, tableName);
               DataTable table = GetDataTable(ds, tableName);

               OdbcDataAdapter dda = GetAdapterForTable(destTableName);
               if (dda == null)
               {
                   return;
               }

               DataSet dds = GetDataSetForTable(dda, destTableName);
               DataTable destTable = GetDataTable(dds, destTableName);
               DataRow row = table.Rows[rowNumber];

               if (destType == PathType.Table)
               {
                   DataRow destRow = destTable.NewRow();

                   destRow.ItemArray = row.ItemArray;
               }
               else
               {
                   DataRow destRow = destTable.Rows[destRowNumber];

                   destRow.ItemArray = row.ItemArray;
               }

               // Update the changes
               if (ShouldProcess(path, "MoveItem"))
               {
                   WriteItemObject(row, path, false);
                   dda.Update(dds, destTableName);
               }
           }
       }
```

## <a name="see-also"></a>Vedere anche

[Scrittura di un provider di contenitori](./writing-a-container-provider.md)

[Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md)