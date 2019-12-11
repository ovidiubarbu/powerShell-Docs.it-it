---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxFile DSC per Linux
ms.openlocfilehash: be5f098d2fe1c8b354c07e6a8f882b8fdf00e1db
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954828"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="d4286-103">Risorsa nxFile DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="d4286-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="d4286-104">La risorsa **nxFile** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e directory in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="d4286-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="d4286-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="d4286-105">Syntax</span></span>

```Syntax
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage | ignore } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="d4286-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d4286-106">Properties</span></span>

|<span data-ttu-id="d4286-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d4286-107">Property</span></span> |<span data-ttu-id="d4286-108">Description</span><span class="sxs-lookup"><span data-stu-id="d4286-108">Description</span></span> |
|---|---|
|<span data-ttu-id="d4286-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="d4286-109">DestinationPath</span></span> |<span data-ttu-id="d4286-110">Indica il percorso in cui si vuole specificare lo stato di un file o una directory.</span><span class="sxs-lookup"><span data-stu-id="d4286-110">Specifies the location where you want to ensure the state for a file or directory.</span></span> |
|<span data-ttu-id="d4286-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="d4286-111">SourcePath</span></span> |<span data-ttu-id="d4286-112">Specifica il percorso da cui copiare la risorsa file o cartella.</span><span class="sxs-lookup"><span data-stu-id="d4286-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="d4286-113">Questo percorso può essere un percorso locale o un URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="d4286-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="d4286-114">Gli URL `http/https/ftp` remoti sono supportati solo quando il valore della proprietà **Type** è **file**.</span><span class="sxs-lookup"><span data-stu-id="d4286-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is **file**.</span></span> |
|<span data-ttu-id="d4286-115">Tipo</span><span class="sxs-lookup"><span data-stu-id="d4286-115">Type</span></span> |<span data-ttu-id="d4286-116">Specifica se la risorsa configurata è una directory o un file.</span><span class="sxs-lookup"><span data-stu-id="d4286-116">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="d4286-117">Impostare questa proprietà su **directory** per indicare che la risorsa è una directory.</span><span class="sxs-lookup"><span data-stu-id="d4286-117">Set this property to **directory** to indicate that the resource is a directory.</span></span> <span data-ttu-id="d4286-118">Impostarla su **file** per indicare che la risorsa è un file.</span><span class="sxs-lookup"><span data-stu-id="d4286-118">Set it to **file** to indicate that the resource is a file.</span></span> <span data-ttu-id="d4286-119">Il valore predefinito è **file**.</span><span class="sxs-lookup"><span data-stu-id="d4286-119">The default value is **file**.</span></span> |
|<span data-ttu-id="d4286-120">Contents</span><span class="sxs-lookup"><span data-stu-id="d4286-120">Contents</span></span> |<span data-ttu-id="d4286-121">Specifica il contenuto di un file, ad esempio una determinata stringa.</span><span class="sxs-lookup"><span data-stu-id="d4286-121">Specifies the contents of a file, such as a particular string.</span></span> |
|<span data-ttu-id="d4286-122">Checksum</span><span class="sxs-lookup"><span data-stu-id="d4286-122">Checksum</span></span> |<span data-ttu-id="d4286-123">Definisce il tipo da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="d4286-123">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="d4286-124">Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="d4286-124">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="d4286-125">I valori sono: **ctime**, **mtime** o **md5**.</span><span class="sxs-lookup"><span data-stu-id="d4286-125">Values are: **ctime**, **mtime**, or **md5**.</span></span> |
|<span data-ttu-id="d4286-126">Recurse</span><span class="sxs-lookup"><span data-stu-id="d4286-126">Recurse</span></span> |<span data-ttu-id="d4286-127">Indica se le sottodirectory sono incluse.</span><span class="sxs-lookup"><span data-stu-id="d4286-127">Indicates if subdirectories are included.</span></span> <span data-ttu-id="d4286-128">Impostare questa proprietà su `$true` per indicare che le sottodirectory devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="d4286-128">Set this property to `$true` to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="d4286-129">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="d4286-129">The default is `$false`.</span></span> <span data-ttu-id="d4286-130">Questa proprietà è valida solo quando la proprietà **Type** è impostata su **directory**.</span><span class="sxs-lookup"><span data-stu-id="d4286-130">This property is only valid when the **Type** property is set to **directory**.</span></span> |
|<span data-ttu-id="d4286-131">Force</span><span class="sxs-lookup"><span data-stu-id="d4286-131">Force</span></span> |<span data-ttu-id="d4286-132">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="d4286-132">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="d4286-133">Usando la proprietà **Force**, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="d4286-133">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="d4286-134">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="d4286-134">The default value is `$false`.</span></span> |
|<span data-ttu-id="d4286-135">Links</span><span class="sxs-lookup"><span data-stu-id="d4286-135">Links</span></span> |<span data-ttu-id="d4286-136">Specifica il comportamento desiderato per i collegamenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="d4286-136">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="d4286-137">Impostare questa proprietà su **follow** per seguire i collegamenti simbolici e agire sulla destinazione dei collegamenti.</span><span class="sxs-lookup"><span data-stu-id="d4286-137">Set this property to **follow** to follow symbolic links and act on the links target.</span></span> <span data-ttu-id="d4286-138">Ad esempio, copiare il file invece del collegamento.</span><span class="sxs-lookup"><span data-stu-id="d4286-138">For example, copy the file instead of the link.</span></span> <span data-ttu-id="d4286-139">Impostare questa proprietà su **manage** per agire sul collegamento.</span><span class="sxs-lookup"><span data-stu-id="d4286-139">Set this property to **manage** to act on the link.</span></span> <span data-ttu-id="d4286-140">Ad esempio, copiare il collegamento stesso.</span><span class="sxs-lookup"><span data-stu-id="d4286-140">For example, copy the link itself.</span></span> <span data-ttu-id="d4286-141">Impostare questa proprietà su **ignore** per ignorare i collegamenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="d4286-141">Set this property to **ignore** to ignore symbolic links.</span></span> |
|<span data-ttu-id="d4286-142">Group</span><span class="sxs-lookup"><span data-stu-id="d4286-142">Group</span></span> |<span data-ttu-id="d4286-143">Nome del **Group** che avrà le autorizzazioni per il file o la directory.</span><span class="sxs-lookup"><span data-stu-id="d4286-143">The name of the **Group** to have permissions to the file or directory.</span></span> |
|<span data-ttu-id="d4286-144">Mode</span><span class="sxs-lookup"><span data-stu-id="d4286-144">Mode</span></span> |<span data-ttu-id="d4286-145">Specifica le autorizzazioni desiderate per la risorsa, in notazione ottale o simbolica</span><span class="sxs-lookup"><span data-stu-id="d4286-145">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="d4286-146">Ad esempio, **777** o **rwxrwxrwx**.</span><span class="sxs-lookup"><span data-stu-id="d4286-146">For example, **777** or **rwxrwxrwx**.</span></span> <span data-ttu-id="d4286-147">Se si usa la notazione simbolica, non fornire il primo carattere che indica una directory o un file.</span><span class="sxs-lookup"><span data-stu-id="d4286-147">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span> |
|<span data-ttu-id="d4286-148">Proprietario</span><span class="sxs-lookup"><span data-stu-id="d4286-148">Owner</span></span> |<span data-ttu-id="d4286-149">Nome del gruppo proprietario del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="d4286-149">The name of the group to own the file or directory.</span></span> |

## <a name="common-properties"></a><span data-ttu-id="d4286-150">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="d4286-150">Common properties</span></span>

|<span data-ttu-id="d4286-151">Proprietà</span><span class="sxs-lookup"><span data-stu-id="d4286-151">Property</span></span> |<span data-ttu-id="d4286-152">Description</span><span class="sxs-lookup"><span data-stu-id="d4286-152">Description</span></span> |
|---|---|
|<span data-ttu-id="d4286-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="d4286-153">DependsOn</span></span> |<span data-ttu-id="d4286-154">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="d4286-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="d4286-155">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="d4286-155">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="d4286-156">Ensure</span><span class="sxs-lookup"><span data-stu-id="d4286-156">Ensure</span></span> |<span data-ttu-id="d4286-157">Determina se verificare l'esistenza del file.</span><span class="sxs-lookup"><span data-stu-id="d4286-157">Determines whether to check if the file exists.</span></span> <span data-ttu-id="d4286-158">Impostare questa proprietà su **Present** per assicurarsi che il file esista.</span><span class="sxs-lookup"><span data-stu-id="d4286-158">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="d4286-159">Impostarla su **Absent** per assicurarsi che il file non esista.</span><span class="sxs-lookup"><span data-stu-id="d4286-159">Set it to **Absent** to ensure the file does not exist.</span></span> <span data-ttu-id="d4286-160">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="d4286-160">The default value is **Present**.</span></span> |

## <a name="additional-information"></a><span data-ttu-id="d4286-161">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="d4286-161">Additional Information</span></span>

<span data-ttu-id="d4286-162">Linux e Windows usano per impostazione predefinita caratteri di interruzione di riga diversi nei file di testo e questo può causare risultati imprevisti quando si configurano alcuni file in un computer Linux con **nxFile**.</span><span class="sxs-lookup"><span data-stu-id="d4286-162">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with **nxFile**.</span></span> <span data-ttu-id="d4286-163">Ci sono diversi modi per gestire il contenuto di un file di Linux evitando i problemi causati da caratteri di interruzione di riga imprevisti:</span><span class="sxs-lookup"><span data-stu-id="d4286-163">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

1. <span data-ttu-id="d4286-164">Copiare il file da un'origine remota (HTTP, HTTPS o FTP)</span><span class="sxs-lookup"><span data-stu-id="d4286-164">Copy the file from a remote source (http, https, or ftp)</span></span>

   <span data-ttu-id="d4286-165">Creare un file in Linux con il contenuto desiderato e metterlo su un server Web o FTP accessibile dai nodi che verranno configurati.</span><span class="sxs-lookup"><span data-stu-id="d4286-165">Create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="d4286-166">Definire la proprietà **SourcePath** nella risorsa **nxFile** con l'URL Web o FTP del file.</span><span class="sxs-lookup"><span data-stu-id="d4286-166">Define the **SourcePath** property in the **nxFile** resource with the web or ftp URL to the file.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      nxFile resolvConf
      {
         SourcePath = "http://10.185.85.11/conf/resolv.conf"
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
      }
   }
   ```

1. <span data-ttu-id="d4286-167">leggere il contenuto del file nello script di PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) dopo avere impostato la proprietà **$OFS** per usare il carattere di interruzione di riga di Linux.</span><span class="sxs-lookup"><span data-stu-id="d4286-167">Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the **$OFS** property to use the Linux line-break character.</span></span>

   ```powershell
   Import-DSCResource -Module nx

   Node $Node
   {
      $OFS = "`n"
      $Contents = Get-Content C:\temp\resolv.conf

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = "$Contents"
      }
   }
   ```

1. <span data-ttu-id="d4286-168">usare una funzione di PowerShell per sostituire le interruzioni di riga di Windows con caratteri di interruzione di riga di Linux.</span><span class="sxs-lookup"><span data-stu-id="d4286-168">Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

   ```powershell
   Function LinuxString($inputStr){
      $outputStr = $inputStr.Replace("`r`n","`n")
      $outputStr += "`n"
      Return $outputStr
   }

   Import-DSCResource -Module nx

   Node $Node
   {
      $Contents = @'
   search contoso.com
   domain contoso.com
   nameserver 10.185.85.11
   '@
       $Contents = LinuxString $Contents

      nxFile resolvConf
      {
         DestinationPath = "/etc/resolv.conf"
         Mode = "644"
         Type = "file"
         Contents = $Contents
      }
   }
   ```

## <a name="example"></a><span data-ttu-id="d4286-169">Esempio</span><span class="sxs-lookup"><span data-stu-id="d4286-169">Example</span></span>

<span data-ttu-id="d4286-170">L'esempio seguente specifica che la directory `/opt/mydir` esiste e che nella directory è presente un file con il contenuto specificato.</span><span class="sxs-lookup"><span data-stu-id="d4286-170">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```powershell
Import-DSCResource -Module nx

Node $node {
    nxFile DirectoryExample
    {
        Ensure = "Present"
        DestinationPath = "/opt/mydir"
        Type = "Directory"
    }

    nxFile FileExample
    {
        Ensure = "Present"
        Destinationpath = "/opt/mydir/myfile"
        Contents=@"
#!/bin/bash`necho "hello world"`n
"@
        Mode = "755"
        DependsOn = "[nxFile]DirectoryExample"
    }
}
```