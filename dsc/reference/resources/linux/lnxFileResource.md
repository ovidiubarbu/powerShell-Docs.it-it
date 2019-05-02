---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxFile DSC per Linux
ms.openlocfilehash: 80969ba2ea6247fcd616a301d951403a840c851d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62078028"
---
# <a name="dsc-for-linux-nxfile-resource"></a><span data-ttu-id="66e16-103">Risorsa nxFile DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="66e16-103">DSC for Linux nxFile Resource</span></span>

<span data-ttu-id="66e16-104">La risorsa **nxFile** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e directory in un nodo Linux.</span><span class="sxs-lookup"><span data-stu-id="66e16-104">The **nxFile** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and directories on a Linux node.</span></span>

## <a name="syntax"></a><span data-ttu-id="66e16-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="66e16-105">Syntax</span></span>

```
nxFile <string> #ResourceName
{
    DestinationPath = <string>
    [ SourcePath = <string> ]
    [ Ensure = <string> { Absent | Present }  ]
    [ Type = <string> { directory | file | link } ]
    [ Contents = <string> ]
    [ Checksum = <string> { ctime | mtime | md5 }  ]
    [ Recurse = <bool> ]
    [ Force = <bool> ]
    [ Links = <string> { follow | manage } ]
    [ Group = <string> ]
    [ Mode = <string> ]
    [ Owner = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="66e16-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="66e16-106">Properties</span></span>

|  <span data-ttu-id="66e16-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="66e16-107">Property</span></span> |  <span data-ttu-id="66e16-108">Description</span><span class="sxs-lookup"><span data-stu-id="66e16-108">Description</span></span> |
|---|---|
| <span data-ttu-id="66e16-109">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="66e16-109">DestinationPath</span></span>| <span data-ttu-id="66e16-110">Indica il percorso in cui si vuole specificare lo stato di un file o una directory.</span><span class="sxs-lookup"><span data-stu-id="66e16-110">Specifies the location where you want to ensure the state for a file or directory.</span></span>|
| <span data-ttu-id="66e16-111">SourcePath</span><span class="sxs-lookup"><span data-stu-id="66e16-111">SourcePath</span></span>| <span data-ttu-id="66e16-112">Specifica il percorso da cui copiare la risorsa file o cartella.</span><span class="sxs-lookup"><span data-stu-id="66e16-112">Specifies the path from which to copy the file or folder resource.</span></span> <span data-ttu-id="66e16-113">Questo percorso può essere un percorso locale o un URL `http/https/ftp`.</span><span class="sxs-lookup"><span data-stu-id="66e16-113">This path may be a local path, or an `http/https/ftp` URL.</span></span> <span data-ttu-id="66e16-114">Gli URL `http/https/ftp` remoti sono supportati solo quando il valore della proprietà **Type** è file.</span><span class="sxs-lookup"><span data-stu-id="66e16-114">Remote `http/https/ftp` URLs are only supported when the value of the **Type** property is file.</span></span>|
| <span data-ttu-id="66e16-115">Ensure</span><span class="sxs-lookup"><span data-stu-id="66e16-115">Ensure</span></span>| <span data-ttu-id="66e16-116">Determina se verificare l'esistenza del file.</span><span class="sxs-lookup"><span data-stu-id="66e16-116">Determines whether to check if the file exists.</span></span> <span data-ttu-id="66e16-117">Impostare questa proprietà su "Present" per specificare che il file esiste.</span><span class="sxs-lookup"><span data-stu-id="66e16-117">Set this property to "Present" to ensure the file exists.</span></span> <span data-ttu-id="66e16-118">Impostarla su "Absent" per specificare che il file non esiste.</span><span class="sxs-lookup"><span data-stu-id="66e16-118">Set it to "Absent" to ensure the file does not exist.</span></span> <span data-ttu-id="66e16-119">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="66e16-119">The default value is "Present".</span></span>|
| <span data-ttu-id="66e16-120">Tipo</span><span class="sxs-lookup"><span data-stu-id="66e16-120">Type</span></span>| <span data-ttu-id="66e16-121">Specifica se la risorsa configurata è una directory o un file.</span><span class="sxs-lookup"><span data-stu-id="66e16-121">Specifies whether the resource being configured is a directory or a file.</span></span> <span data-ttu-id="66e16-122">Impostare questa proprietà su "directory" per indicare che la risorsa è una directory.</span><span class="sxs-lookup"><span data-stu-id="66e16-122">Set this property to "directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="66e16-123">Impostarla su "file" per indicare che la risorsa è un file.</span><span class="sxs-lookup"><span data-stu-id="66e16-123">Set it to "file" to indicate that the resource is a file.</span></span> <span data-ttu-id="66e16-124">Il valore predefinito è "file".</span><span class="sxs-lookup"><span data-stu-id="66e16-124">The default value is "file"</span></span>|
| <span data-ttu-id="66e16-125">Contents</span><span class="sxs-lookup"><span data-stu-id="66e16-125">Contents</span></span>| <span data-ttu-id="66e16-126">Specifica il contenuto di un file, ad esempio una determinata stringa.</span><span class="sxs-lookup"><span data-stu-id="66e16-126">Specifies the contents of a file, such as a particular string.</span></span>|
| <span data-ttu-id="66e16-127">Checksum</span><span class="sxs-lookup"><span data-stu-id="66e16-127">Checksum</span></span>| <span data-ttu-id="66e16-128">Definisce il tipo da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="66e16-128">Defines the type to use when determining whether two files are the same.</span></span> <span data-ttu-id="66e16-129">Se la proprietà **Checksum** non è specificata, per il confronto viene usato solo il nome del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="66e16-129">If **Checksum** is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="66e16-130">I valori sono: "ctime", "mtime" e "md5".</span><span class="sxs-lookup"><span data-stu-id="66e16-130">Values are: "ctime", "mtime", or "md5".</span></span>|
| <span data-ttu-id="66e16-131">Recurse</span><span class="sxs-lookup"><span data-stu-id="66e16-131">Recurse</span></span>| <span data-ttu-id="66e16-132">Indica se le sottodirectory sono incluse.</span><span class="sxs-lookup"><span data-stu-id="66e16-132">Indicates if subdirectories are included.</span></span> <span data-ttu-id="66e16-133">Impostare questa proprietà su **$true** per indicare che le sottodirectory devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="66e16-133">Set this property to **$true** to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="66e16-134">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="66e16-134">The default is **$false**.</span></span> <span data-ttu-id="66e16-135">**Nota:** questa proprietà è valida solo quando la proprietà **Type** è impostata su directory.</span><span class="sxs-lookup"><span data-stu-id="66e16-135">**Note:** This property is only valid when the **Type** property is set to directory.</span></span>|
| <span data-ttu-id="66e16-136">Force</span><span class="sxs-lookup"><span data-stu-id="66e16-136">Force</span></span>| <span data-ttu-id="66e16-137">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="66e16-137">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="66e16-138">Usando la proprietà **Force**, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="66e16-138">Using the **Force** property overrides such errors.</span></span> <span data-ttu-id="66e16-139">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="66e16-139">The default value is **$false**.</span></span>|
| <span data-ttu-id="66e16-140">Links</span><span class="sxs-lookup"><span data-stu-id="66e16-140">Links</span></span>| <span data-ttu-id="66e16-141">Specifica il comportamento desiderato per i collegamenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="66e16-141">Specifies the desired behavior for symbolic links.</span></span> <span data-ttu-id="66e16-142">Impostare questa proprietà su "follow" per seguire i collegamenti simbolici e agire sulla destinazione dei collegamenti (ad esempio,</span><span class="sxs-lookup"><span data-stu-id="66e16-142">Set this property to "follow" to follow symbolic links and act on the links target (for example.</span></span> <span data-ttu-id="66e16-143">copiare il file invece del collegamento).</span><span class="sxs-lookup"><span data-stu-id="66e16-143">copy the file instead of the link).</span></span> <span data-ttu-id="66e16-144">Impostare questa proprietà su "manage" per agire sul collegamento (ad esempio,</span><span class="sxs-lookup"><span data-stu-id="66e16-144">Set this property to "manage" to act on the link (for example.</span></span> <span data-ttu-id="66e16-145">copiare il collegamento stesso).</span><span class="sxs-lookup"><span data-stu-id="66e16-145">copy the link itself).</span></span> <span data-ttu-id="66e16-146">Impostare questa proprietà su "ignore" per ignorare i collegamenti simbolici.</span><span class="sxs-lookup"><span data-stu-id="66e16-146">Set this property to "ignore" to ignore symbolic links.</span></span>|
| <span data-ttu-id="66e16-147">Group</span><span class="sxs-lookup"><span data-stu-id="66e16-147">Group</span></span>| <span data-ttu-id="66e16-148">Nome del **gruppo** proprietario del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="66e16-148">The name of the **Group** to own the file or directory.</span></span>|
| <span data-ttu-id="66e16-149">Mode</span><span class="sxs-lookup"><span data-stu-id="66e16-149">Mode</span></span>| <span data-ttu-id="66e16-150">Specifica le autorizzazioni desiderate per la risorsa, in notazione ottale o simbolica</span><span class="sxs-lookup"><span data-stu-id="66e16-150">Specifies the desired permissions for the resource, in octal or symbolic notation.</span></span> <span data-ttu-id="66e16-151">(ad esempio, 777 o rwxrwxrwx).</span><span class="sxs-lookup"><span data-stu-id="66e16-151">(for example, 777 or rwxrwxrwx).</span></span> <span data-ttu-id="66e16-152">Se si usa la notazione simbolica, non fornire il primo carattere che indica una directory o un file.</span><span class="sxs-lookup"><span data-stu-id="66e16-152">If using symbolic notation, do not provide the first character which indicates directory or file.</span></span>|
| <span data-ttu-id="66e16-153">DependsOn</span><span class="sxs-lookup"><span data-stu-id="66e16-153">DependsOn</span></span> | <span data-ttu-id="66e16-154">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="66e16-154">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="66e16-155">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="66e16-155">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="additional-information"></a><span data-ttu-id="66e16-156">Informazioni aggiuntive</span><span class="sxs-lookup"><span data-stu-id="66e16-156">Additional Information</span></span>


<span data-ttu-id="66e16-157">Linux e Windows usano per impostazione predefinita caratteri di interruzione di riga diversi nei file di testo e questo può causare risultati imprevisti quando si configurano alcuni file in un computer Linux con __nxFile__.</span><span class="sxs-lookup"><span data-stu-id="66e16-157">Linux and Windows use different line break characters in text files by default, and this can cause unexpected results when configuring some files on a Linux computer with __nxFile__.</span></span> <span data-ttu-id="66e16-158">Ci sono diversi modi per gestire il contenuto di un file di Linux evitando i problemi causati da caratteri di interruzione di riga imprevisti:</span><span class="sxs-lookup"><span data-stu-id="66e16-158">There are multiple ways to manage the content of a Linux file while avoiding issues caused by unexpected line break characters:</span></span>

<span data-ttu-id="66e16-159">Passaggio 1: copiare il file da un'origine remota (http, https o ftp). Creare un file in Linux con il contenuto desiderato e metterlo su un server Web o FTP accessibile dai nodi che verranno configurati.</span><span class="sxs-lookup"><span data-stu-id="66e16-159">Step 1: Copy the file from a remote source (http, https, or ftp): create a file on Linux with the desired contents, and stage it on a web or ftp server accessible the node(s) you will configure.</span></span> <span data-ttu-id="66e16-160">Definire la proprietà __SourcePath__ nella risorsa __nxFile__ con l'URL Web o FTP del file.</span><span class="sxs-lookup"><span data-stu-id="66e16-160">Define the __SourcePath__ property in the __nxFile__ resource with the web or ftp URL to the file.</span></span>

```
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


<span data-ttu-id="66e16-161">Passaggio 2: leggere il contenuto del file nello script di PowerShell con [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) dopo avere impostato la proprietà __$OFS__ per usare il carattere di interruzione di riga di Linux.</span><span class="sxs-lookup"><span data-stu-id="66e16-161">Step 2: Read the file contents in the PowerShell script with [Get-Content](https://technet.microsoft.com/library/hh849787.aspx) after setting the __$OFS__ property to use the Linux line-break character.</span></span>


```
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


<span data-ttu-id="66e16-162">Passaggio 3: usare una funzione di PowerShell per sostituire le interruzioni di riga di Windows con caratteri di interruzione di riga di Linux.</span><span class="sxs-lookup"><span data-stu-id="66e16-162">Step 3: Use a PowerShell function to replace Windows line breaks with Linux line-break characters.</span></span>

```
Function LinuxString($inputStr){
    $outputStr = $inputStr.Replace("`r`n","`n")
    $ouputStr += "`n"
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

## <a name="example"></a><span data-ttu-id="66e16-163">Esempio</span><span class="sxs-lookup"><span data-stu-id="66e16-163">Example</span></span>

<span data-ttu-id="66e16-164">L'esempio seguente specifica che la directory `/opt/mydir` esiste e che nella directory è presente un file con il contenuto specificato.</span><span class="sxs-lookup"><span data-stu-id="66e16-164">The following example ensures that the directory `/opt/mydir` exists, and that a file with specified contents exists this directory.</span></span>

```
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
    Mode = “755”
    DependsOn = "[nxFile]DirectoryExample"
}
}
```