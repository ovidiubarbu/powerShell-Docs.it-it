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
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="4a46f-102">Scrittura di un provider di navigazione</span><span class="sxs-lookup"><span data-stu-id="4a46f-102">Writing a navigation provider</span></span>

<span data-ttu-id="4a46f-103">In questo argomento viene descritto come implementare i metodi di un provider di Windows PowerShell che supporta i contenitori annidati (archivi dati a più livelli), lo stato degli elementi e i percorsi relativi.</span><span class="sxs-lookup"><span data-stu-id="4a46f-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="4a46f-104">Un provider di navigazione deve derivare dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="4a46f-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="4a46f-105">Nel provider degli esempi di questo argomento viene utilizzato un database di Access come archivio dati.</span><span class="sxs-lookup"><span data-stu-id="4a46f-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="4a46f-106">Sono disponibili diversi metodi e classi helper che consentono di interagire con il database.</span><span class="sxs-lookup"><span data-stu-id="4a46f-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="4a46f-107">Per l'esempio completo che include i metodi helper, vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="4a46f-108">Per ulteriori informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sui provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="4a46f-109">Implementazione di metodi di navigazione</span><span class="sxs-lookup"><span data-stu-id="4a46f-109">Implementing navigation methods</span></span>

<span data-ttu-id="4a46f-110">La classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) implementa i metodi che supportano i contenitori annidati, i percorsi relativi e gli elementi mobili.</span><span class="sxs-lookup"><span data-stu-id="4a46f-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="4a46f-111">Per un elenco completo di questi metodi, vedere [Metodi NavigationCmdletProvider](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="4a46f-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="4a46f-112">Questo argomento si basa sulle informazioni fornite nella [Guida introduttiva del provider di Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="4a46f-113">Questo argomento non illustra le nozioni di base su come configurare un progetto di provider o su come implementare i metodi ereditati dalla classe [System. Management. Automation. provider. Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) che creano e rimuovono unità.</span><span class="sxs-lookup"><span data-stu-id="4a46f-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="4a46f-114">In questo argomento non viene inoltre illustrato come implementare metodi esposti dalle classi [System. Management. Automation. provider. Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o [System. Management. Automation. provider. Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) .</span><span class="sxs-lookup"><span data-stu-id="4a46f-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="4a46f-115">Per un esempio in cui viene illustrato come implementare i cmdlet di elemento, vedere [scrittura di un provider di elementi](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="4a46f-116">Per un esempio in cui viene illustrato come implementare i cmdlet del contenitore, vedere [scrittura di un provider di contenitori](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="4a46f-117">Dichiarazione della classe provider</span><span class="sxs-lookup"><span data-stu-id="4a46f-117">Declaring the provider class</span></span>

<span data-ttu-id="4a46f-118">Dichiarare il provider per la derivazione dalla classe [System. Management. Automation. provider. Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) e decorarlo con [System. Management. Automation. provider. CmdletProviderAttribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="4a46f-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="4a46f-119">Implementazione di IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="4a46f-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="4a46f-120">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. IsItemContainer \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) controlla se l'elemento in corrispondenza del percorso specificato è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="4a46f-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="4a46f-121">Implementazione di getchildname</span><span class="sxs-lookup"><span data-stu-id="4a46f-121">Implementing GetChildName</span></span>

<span data-ttu-id="4a46f-122">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. getchildname \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) ottiene la proprietà Name dell'elemento figlio nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="4a46f-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="4a46f-123">Se l'elemento in corrispondenza del percorso specificato non è figlio di un contenitore, questo metodo deve restituire il percorso.</span><span class="sxs-lookup"><span data-stu-id="4a46f-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="4a46f-124">Implementazione di GetParentPath</span><span class="sxs-lookup"><span data-stu-id="4a46f-124">Implementing GetParentPath</span></span>

<span data-ttu-id="4a46f-125">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. GetParentPath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) ottiene il percorso dell'elemento padre dell'elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="4a46f-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="4a46f-126">Se l'elemento in corrispondenza del percorso specificato è la radice dell'archivio dati (pertanto non ha un elemento padre), questo metodo deve restituire il percorso radice.</span><span class="sxs-lookup"><span data-stu-id="4a46f-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="4a46f-127">Implementazione di MakePath</span><span class="sxs-lookup"><span data-stu-id="4a46f-127">Implementing MakePath</span></span>

<span data-ttu-id="4a46f-128">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. makepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) unisce un percorso padre specificato e un percorso figlio specificato per creare un percorso interno del provider. per informazioni sui tipi di percorso che i provider sono in grado di supportare, vedere [Panoramica del provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="4a46f-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="4a46f-129">Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) .</span><span class="sxs-lookup"><span data-stu-id="4a46f-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="4a46f-130">Implementazione di NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="4a46f-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="4a46f-131">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. Normalizerelativepath \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) accetta i parametri `path` e `basepath` e restituisce un percorso normalizzato equivalente al parametro `path` e relativo a `basepath` parametro.</span><span class="sxs-lookup"><span data-stu-id="4a46f-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="4a46f-132">Implementazione di MoveItem</span><span class="sxs-lookup"><span data-stu-id="4a46f-132">Implementing MoveItem</span></span>

<span data-ttu-id="4a46f-133">Il metodo [System. Management. Automation. provider. Navigationcmdletprovider. MoveItem \*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) sposta un elemento dal percorso specificato al percorso di destinazione specificato.</span><span class="sxs-lookup"><span data-stu-id="4a46f-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="4a46f-134">Il motore di PowerShell chiama questo metodo quando un utente chiama il cmdlet [Microsoft. PowerShell. Commands. MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) .</span><span class="sxs-lookup"><span data-stu-id="4a46f-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4a46f-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4a46f-135">See Also</span></span>

[<span data-ttu-id="4a46f-136">Scrittura di un provider di contenitori</span><span class="sxs-lookup"><span data-stu-id="4a46f-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="4a46f-137">Panoramica del provider di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="4a46f-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)