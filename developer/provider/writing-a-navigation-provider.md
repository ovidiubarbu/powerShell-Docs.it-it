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
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 07/10/2019
ms.locfileid: "67734737"
---
# <a name="writing-a-navigation-provider"></a><span data-ttu-id="ba924-102">Scrittura di un provider di navigazione</span><span class="sxs-lookup"><span data-stu-id="ba924-102">Writing a navigation provider</span></span>

<span data-ttu-id="ba924-103">In questo argomento viene descritto come implementare i metodi di un provider di Windows PowerShell che supportano i contenitori nidificati (archivi dati a più livelli), lo spostamento di elementi e i percorsi relativi.</span><span class="sxs-lookup"><span data-stu-id="ba924-103">This topic describes how to implement the methods of a Windows PowerShell provider that support nested containers (multi-level data stores), moving items, and relative paths.</span></span> <span data-ttu-id="ba924-104">Un provider di navigazione deve derivare dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="ba924-104">A navigation provider must derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class.</span></span>

<span data-ttu-id="ba924-105">Il provider negli esempi in questo argomento Usa un database di Access come suo archivio dati.</span><span class="sxs-lookup"><span data-stu-id="ba924-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="ba924-106">Esistono diversi metodi helper e classi che consentono di interagire con il database.</span><span class="sxs-lookup"><span data-stu-id="ba924-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="ba924-107">Per l'esempio completo che include i metodi di supporto, vedere [AccessDBProviderSample05](./accessdbprovidersample05.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample05](./accessdbprovidersample05.md).</span></span>

<span data-ttu-id="ba924-108">Per altre informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-navigation-methods"></a><span data-ttu-id="ba924-109">Implementazione dei metodi di navigazione</span><span class="sxs-lookup"><span data-stu-id="ba924-109">Implementing navigation methods</span></span>

<span data-ttu-id="ba924-110">Il [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe implementa metodi che supportano i contenitori nidificati, i percorsi relativi e spostamento di elementi.</span><span class="sxs-lookup"><span data-stu-id="ba924-110">The [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class implements methods that support nested containers, relative paths, and moving items.</span></span> <span data-ttu-id="ba924-111">Per un elenco completo di questi metodi, vedere [NavigationCmdletProvider metodi](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span><span class="sxs-lookup"><span data-stu-id="ba924-111">For a complete list of these methods, see [NavigationCmdletProvider Methods](/dotnet/api/system.management.automation.provider.navigationcmdletprovider?view=pscore-6.2.0#methods).</span></span>

> [!NOTE]
> <span data-ttu-id="ba924-112">Questo argomento si basa sulle informazioni presenti [avvio rapido di Provider di Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-112">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="ba924-113">In questo argomento non comprende le nozioni di base di come configurare un progetto di provider, o come implementare i metodi ereditati dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe che creare e rimuovere le unità.</span><span class="sxs-lookup"><span data-stu-id="ba924-113">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span> <span data-ttu-id="ba924-114">In questo argomento non illustra anche come implementare i metodi esposti dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) o [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classi.</span><span class="sxs-lookup"><span data-stu-id="ba924-114">This topic also does not cover how to implement methods exposed by the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) or [System.Management.Automation.Provider.Containercmdletprovider](/dotnet/api/System.Management.Automation.Provider.ContainerCmdletProvider) classes.</span></span> <span data-ttu-id="ba924-115">Per un esempio che illustra come implementare i cmdlet item, vedere [scrittura di un elemento provider](./writing-an-item-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-115">For an example that shows how to implement item cmdlets, see [Writing an item provider](./writing-an-item-provider.md).</span></span> <span data-ttu-id="ba924-116">Per un esempio che illustra come implementare i cmdlet di contenitore, vedere [scrittura di un provider di contenitore](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-116">For an example that shows how to implement container cmdlets, see [Writing a container provider](./writing-a-container-provider.md).</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="ba924-117">Dichiarazione della classe di provider</span><span class="sxs-lookup"><span data-stu-id="ba924-117">Declaring the provider class</span></span>

<span data-ttu-id="ba924-118">Dichiarare il provider di derivare dal [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) classe e decorarla con il [System.Management.Automation.Provider.Cmdletproviderattribute ](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="ba924-118">Declare the provider to derive from the [System.Management.Automation.Provider.Navigationcmdletprovider](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```
[CmdletProvider("AccessDB", ProviderCapabilities.None)]
   public class AccessDBProvider : NavigationCmdletProvider
   {

   }
```

### <a name="implementing-isitemcontainer"></a><span data-ttu-id="ba924-119">Implementazione IsItemContainer</span><span class="sxs-lookup"><span data-stu-id="ba924-119">Implementing IsItemContainer</span></span>

<span data-ttu-id="ba924-120">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) metodo controlla se l'elemento nel percorso specificato è un contenitore.</span><span class="sxs-lookup"><span data-stu-id="ba924-120">The [System.Management.Automation.Provider.Navigationcmdletprovider.Isitemcontainer\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.IsItemContainer) method checks whether the item at the specified path is a container.</span></span>

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

### <a name="implementing-getchildname"></a><span data-ttu-id="ba924-121">Implementazione GetChildName</span><span class="sxs-lookup"><span data-stu-id="ba924-121">Implementing GetChildName</span></span>

<span data-ttu-id="ba924-122">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) metodo ottiene la proprietà name dell'elemento figlio nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="ba924-122">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getchildname\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetChildName) method gets the name property of the child item at the specified path.</span></span> <span data-ttu-id="ba924-123">Se l'elemento nel percorso specificato non è un elemento figlio di un contenitore, questo metodo deve restituire il percorso.</span><span class="sxs-lookup"><span data-stu-id="ba924-123">If the item at the specified path is not a child of a container, then this method should return the path.</span></span>

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

### <a name="implementing-getparentpath"></a><span data-ttu-id="ba924-124">Implementazione GetParentPath</span><span class="sxs-lookup"><span data-stu-id="ba924-124">Implementing GetParentPath</span></span>

<span data-ttu-id="ba924-125">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) metodo ottiene il percorso dell'elemento padre dell'elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="ba924-125">The [System.Management.Automation.Provider.Navigationcmdletprovider.Getparentpath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.GetParentPath) method gets the path of the parent of the item at the specified path.</span></span> <span data-ttu-id="ba924-126">Se l'elemento nel percorso specificato è la radice dell'archivio dati (in modo che non ha elementi padre), questo metodo deve restituire il percorso radice.</span><span class="sxs-lookup"><span data-stu-id="ba924-126">If the item at the specified path is the root of the data store (so it has no parent), then this method should return the root path.</span></span>

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

### <a name="implementing-makepath"></a><span data-ttu-id="ba924-127">Implementazione MakePath</span><span class="sxs-lookup"><span data-stu-id="ba924-127">Implementing MakePath</span></span>

<span data-ttu-id="ba924-128">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) metodo viene aggiunto un percorso padre specificato e un percorso figlio specificato per creare un percorso di provider interne (per tipi di informazioni sul percorso i provider possono supportare, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="ba924-128">The [System.Management.Automation.Provider.Navigationcmdletprovider.Makepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MakePath) method joins a specified parent path and a specified child path to create a provider-internal path (for information about path types that providers can support, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span> <span data-ttu-id="ba924-129">Il motore di PowerShell chiama questo metodo quando un utente chiama il [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ba924-129">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.JoinPathCommand](/dotnet/api/Microsoft.PowerShell.Commands.joinpathcommand) cmdlet.</span></span>

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

### <a name="implementing-normalizerelativepath"></a><span data-ttu-id="ba924-130">Implementazione NormalizeRelativePath</span><span class="sxs-lookup"><span data-stu-id="ba924-130">Implementing NormalizeRelativePath</span></span>

<span data-ttu-id="ba924-131">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) metodo accetta `path` e `basepath` parametri e restituisce un percorso normalizzato equivalente per il `path`parametro e rispetto al `basepath` parametro.</span><span class="sxs-lookup"><span data-stu-id="ba924-131">The [System.Management.Automation.Provider.Navigationcmdletprovider.Normalizerelativepath\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.NormalizeRelativePath) method takes `path` and `basepath` parameters, and returns a normalized path that is equivalent to the `path` parameter and relative to the `basepath` parameter.</span></span>

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

### <a name="implementing-moveitem"></a><span data-ttu-id="ba924-132">Implementazione MoveItem</span><span class="sxs-lookup"><span data-stu-id="ba924-132">Implementing MoveItem</span></span>

<span data-ttu-id="ba924-133">Il [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) metodo sposta un elemento dal percorso specificato nel percorso di destinazione specificato.</span><span class="sxs-lookup"><span data-stu-id="ba924-133">The [System.Management.Automation.Provider.Navigationcmdletprovider.Moveitem\*](/dotnet/api/System.Management.Automation.Provider.NavigationCmdletProvider.MoveItem) method moves an item from the specified path to the specified destination path.</span></span> <span data-ttu-id="ba924-134">Il motore di PowerShell chiama questo metodo quando un utente chiama il [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ba924-134">The PowerShell engine calls this method when a user calls the [Microsoft.PowerShell.Commands.MoveItemCommand](/dotnet/api/Microsoft.PowerShell.Commands.moveitemcommand) cmdlet.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ba924-135">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ba924-135">See Also</span></span>

[<span data-ttu-id="ba924-136">Scrittura di un provider di contenitore</span><span class="sxs-lookup"><span data-stu-id="ba924-136">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="ba924-137">Cenni preliminari sul Provider PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="ba924-137">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)