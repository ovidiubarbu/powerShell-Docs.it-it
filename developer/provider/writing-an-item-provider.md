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
ms.openlocfilehash: 9285a2f0e673de8b86084157423512bdeeda109d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58058191"
---
# <a name="writing-an-item-provider"></a><span data-ttu-id="8d70c-102">Scrittura di un provider di elementi</span><span class="sxs-lookup"><span data-stu-id="8d70c-102">Writing an item provider</span></span>

<span data-ttu-id="8d70c-103">Questo argomento descrive come implementare i metodi di un provider di Windows PowerShell accedano e modificano gli elementi nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="8d70c-103">This topic describes how to implement the methods of a Windows PowerShell provider that access and manipulate items in the data store.</span></span> <span data-ttu-id="8d70c-104">Per essere in grado di accedere agli elementi, un provider deve derivare dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe.</span><span class="sxs-lookup"><span data-stu-id="8d70c-104">To be able to access items, a provider must derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class.</span></span>

<span data-ttu-id="8d70c-105">Il provider negli esempi in questo argomento Usa un database di Access come suo archivio dati.</span><span class="sxs-lookup"><span data-stu-id="8d70c-105">The provider in the examples in this topic uses an Access database as its data store.</span></span> <span data-ttu-id="8d70c-106">Esistono diversi metodi helper e classi che consentono di interagire con il database.</span><span class="sxs-lookup"><span data-stu-id="8d70c-106">There are several helper methods and classes that are used to interact with the database.</span></span> <span data-ttu-id="8d70c-107">Per l'esempio completo che include i metodi di supporto, vedere [AccessDBProviderSample03](./accessdbprovidersample03.md)</span><span class="sxs-lookup"><span data-stu-id="8d70c-107">For the complete sample that includes the helper methods, see [AccessDBProviderSample03](./accessdbprovidersample03.md)</span></span>

<span data-ttu-id="8d70c-108">Per altre informazioni sui provider di Windows PowerShell, vedere [Cenni preliminari sul Provider di Windows PowerShell](./windows-powershell-provider-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8d70c-108">For more information about Windows PowerShell providers, see [Windows PowerShell Provider Overview](./windows-powershell-provider-overview.md).</span></span>

## <a name="implementing-item-methods"></a><span data-ttu-id="8d70c-109">Implementazione dei metodi di elemento</span><span class="sxs-lookup"><span data-stu-id="8d70c-109">Implementing item methods</span></span>

<span data-ttu-id="8d70c-110">Il [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe espone diversi metodi che possono essere usati per accedere e modificare gli elementi in un archivio dati.</span><span class="sxs-lookup"><span data-stu-id="8d70c-110">The [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class exposes several methods that can be used to access and manipulate the items in a data store.</span></span> <span data-ttu-id="8d70c-111">Per un elenco completo di questi metodi, vedere [ItemCmdletProvider metodi](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="8d70c-111">For a complete list of these methods, see [ItemCmdletProvider Methods](http://msdn.microsoft.com/library/system.management.automation.provider.itemcmdletprovider_methods\(v=vs.85\).aspx).</span></span> <span data-ttu-id="8d70c-112">In questo esempio verrà implementato quattro di questi metodi.</span><span class="sxs-lookup"><span data-stu-id="8d70c-112">In this example, we will implement four of these methods.</span></span> <span data-ttu-id="8d70c-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) Ottiene un elemento in un percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-113">[System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) gets an item at a specified path.</span></span> <span data-ttu-id="8d70c-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) imposta il valore dell'elemento specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-114">[System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) sets the value of the specified item.</span></span> <span data-ttu-id="8d70c-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) verifica l'esistenza di un elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-115">[System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) checks whether an item exists at the specified path.</span></span> <span data-ttu-id="8d70c-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) controlla un percorso per verificare se viene eseguito il mapping a una posizione nell'archivio dati.</span><span class="sxs-lookup"><span data-stu-id="8d70c-116">[System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) checks a path to see if it maps to a location in the data store.</span></span>

> [!NOTE]
> <span data-ttu-id="8d70c-117">Questo argomento si basa sulle informazioni presenti [avvio rapido di Provider di Windows PowerShell](./windows-powershell-provider-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="8d70c-117">This topic builds on the information in [Windows PowerShell Provider QuickStart](./windows-powershell-provider-quickstart.md).</span></span> <span data-ttu-id="8d70c-118">In questo argomento non comprende le nozioni di base di come configurare un progetto di provider, o come implementare i metodi ereditati dal [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) classe che creare e rimuovere le unità.</span><span class="sxs-lookup"><span data-stu-id="8d70c-118">This topic does not cover the basics of how to set up a provider project, or how to implement the methods inherited from the [System.Management.Automation.Provider.Drivecmdletprovider](/dotnet/api/System.Management.Automation.Provider.DriveCmdletProvider) class that create and remove drives.</span></span>

### <a name="declaring-the-provider-class"></a><span data-ttu-id="8d70c-119">Dichiarazione della classe di provider</span><span class="sxs-lookup"><span data-stu-id="8d70c-119">Declaring the provider class</span></span>

<span data-ttu-id="8d70c-120">Dichiarare il provider di derivare dal [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) classe e decorarla con il [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span><span class="sxs-lookup"><span data-stu-id="8d70c-120">Declare the provider to derive from the [System.Management.Automation.Provider.Itemcmdletprovider](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider) class, and decorate it with the [System.Management.Automation.Provider.Cmdletproviderattribute](/dotnet/api/System.Management.Automation.Provider.CmdletProviderAttribute).</span></span>

```csharp
[CmdletProvider("AccessDB", ProviderCapabilities.None)]

   public class AccessDBProvider : ItemCmdletProvider
   {

  }

```

### <a name="implementing-getitem"></a><span data-ttu-id="8d70c-121">Implementazione GetItem</span><span class="sxs-lookup"><span data-stu-id="8d70c-121">Implementing GetItem</span></span>

<span data-ttu-id="8d70c-122">Il [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) viene chiamato dal motore di PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.Get-elemento](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet di provider.</span><span class="sxs-lookup"><span data-stu-id="8d70c-122">The [System.Management.Automation.Provider.Itemcmdletprovider.Getitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.GetItem) is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Get-Item](/dotnet/api/Microsoft.PowerShell.Commands.Get-Item) cmdlet on your provider.</span></span> <span data-ttu-id="8d70c-123">Il metodo restituisce l'elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-123">The method returns the item at the specified path.</span></span> <span data-ttu-id="8d70c-124">Nell'esempio del database l'accesso, il metodo controlla se l'elemento è l'unità, una tabella nel database o una riga nel database.</span><span class="sxs-lookup"><span data-stu-id="8d70c-124">In the Access database example, the method checks whether the item is the drive itself, a table in the database, or a row in the database.</span></span> <span data-ttu-id="8d70c-125">Il metodo invia l'elemento al motore di PowerShell chiamando il [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) (metodo).</span><span class="sxs-lookup"><span data-stu-id="8d70c-125">The method sends the item to the PowerShell engine by calling the [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject) method.</span></span>

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

### <a name="implementing-setitem"></a><span data-ttu-id="8d70c-126">Implementazione SetItem</span><span class="sxs-lookup"><span data-stu-id="8d70c-126">Implementing SetItem</span></span>

<span data-ttu-id="8d70c-127">Il [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) metodo viene chiamato per il motore chiama PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet .</span><span class="sxs-lookup"><span data-stu-id="8d70c-127">The [System.Management.Automation.Provider.Itemcmdletprovider.Setitem\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.SetItem) method is called by the PowerShell engine calls when a user calls the [Microsoft.PowerShell.Commands.Set-Item](/dotnet/api/Microsoft.PowerShell.Commands.Set-Item) cmdlet.</span></span> <span data-ttu-id="8d70c-128">Imposta il valore dell'elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-128">It sets the value of the item at the specified path.</span></span>

<span data-ttu-id="8d70c-129">Nell'esempio del database di Access, è opportuno impostare il valore di un elemento solo se tale elemento è una riga, in modo che il metodo genera un'eccezione [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) quando l'elemento non è una riga.</span><span class="sxs-lookup"><span data-stu-id="8d70c-129">In the Access database example, it makes sense to set the value of an item only if that item is a row, so the method throws [NotSupportedException](http://msdn.microsoft.com/library/system.notsupportedexception\(v=vs.110\).aspx) when the item is not a row.</span></span>

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

### <a name="implementing-itemexists"></a><span data-ttu-id="8d70c-130">Implementazione ItemExists</span><span class="sxs-lookup"><span data-stu-id="8d70c-130">Implementing ItemExists</span></span>

<span data-ttu-id="8d70c-131">Il [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) metodo viene chiamato dal motore di PowerShell quando un utente chiama il [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8d70c-131">The [System.Management.Automation.Provider.Itemcmdletprovider.Itemexists\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.ItemExists) method is called by the PowerShell engine when a user calls the [Microsoft.PowerShell.Commands.Test-Path](/dotnet/api/Microsoft.PowerShell.Commands.Test-Path) cmdlet.</span></span> <span data-ttu-id="8d70c-132">Il metodo determina se è presente un elemento nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="8d70c-132">The method determines whether there is an item at the specified path.</span></span> <span data-ttu-id="8d70c-133">Se l'elemento esiste, il metodo passa al motore di PowerShell chiamando [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span><span class="sxs-lookup"><span data-stu-id="8d70c-133">If the item does exist, the method passes it back to the PowerShell engine by calling [System.Management.Automation.Provider.Cmdletprovider.Writeitemobject\*](/dotnet/api/System.Management.Automation.Provider.CmdletProvider.WriteItemObject).</span></span>

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

### <a name="implementing-isvalidpath"></a><span data-ttu-id="8d70c-134">Implementazione IsValidPath</span><span class="sxs-lookup"><span data-stu-id="8d70c-134">Implementing IsValidPath</span></span>

<span data-ttu-id="8d70c-135">Il [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) metodo controlla se il percorso specificato è sintatticamente valido per il provider corrente.</span><span class="sxs-lookup"><span data-stu-id="8d70c-135">The [System.Management.Automation.Provider.Itemcmdletprovider.Isvalidpath\*](/dotnet/api/System.Management.Automation.Provider.ItemCmdletProvider.IsValidPath) method checks whether the specified path is syntactically valid for the current provider.</span></span> <span data-ttu-id="8d70c-136">Non controlla se un elemento presente nel percorso.</span><span class="sxs-lookup"><span data-stu-id="8d70c-136">It does not check whether an item exists at the path.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="8d70c-137">Passaggi successivi</span><span class="sxs-lookup"><span data-stu-id="8d70c-137">Next steps</span></span>

<span data-ttu-id="8d70c-138">Un provider del mondo reale tipico è in grado di supportare gli elementi che contengono altri elementi e di spostamento di elementi da un percorso a un altro all'interno dell'unità.</span><span class="sxs-lookup"><span data-stu-id="8d70c-138">A typical real-world provider is capable of supporting items that contain other items, and of moving items from one path to another within the drive.</span></span> <span data-ttu-id="8d70c-139">Per un esempio di un provider che supporti i contenitori, vedere [scrittura di un provider di contenitore](./writing-a-container-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8d70c-139">For an example of a provider that supports containers, see [Writing a container provider](./writing-a-container-provider.md).</span></span> <span data-ttu-id="8d70c-140">Per un esempio di un provider che supporta lo spostamento di elementi, vedere [scrittura di un provider di navigazione](./writing-a-navigation-provider.md).</span><span class="sxs-lookup"><span data-stu-id="8d70c-140">For an example of a provider that supports moving items, see [Writing a navigation provider](./writing-a-navigation-provider.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8d70c-141">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8d70c-141">See Also</span></span>

[<span data-ttu-id="8d70c-142">Scrittura di un provider di contenitore</span><span class="sxs-lookup"><span data-stu-id="8d70c-142">Writing a container provider</span></span>](./writing-a-container-provider.md)

[<span data-ttu-id="8d70c-143">Scrittura di un provider di navigazione</span><span class="sxs-lookup"><span data-stu-id="8d70c-143">Writing a navigation provider</span></span>](./writing-a-navigation-provider.md)

[<span data-ttu-id="8d70c-144">Cenni preliminari sul Provider PowerShell di Windows</span><span class="sxs-lookup"><span data-stu-id="8d70c-144">Windows PowerShell Provider Overview</span></span>](./windows-powershell-provider-overview.md)