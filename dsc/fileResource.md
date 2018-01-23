---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Risorsa File DSC
ms.openlocfilehash: 54d01bf0769eeed0354606eb3543973b0f850a6f
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-file-resource"></a><span data-ttu-id="372f4-103">Risorsa File DSC</span><span class="sxs-lookup"><span data-stu-id="372f4-103">DSC File Resource</span></span>

> <span data-ttu-id="372f4-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="372f4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="372f4-105">La risorsa File in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-105">The File resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span>

><span data-ttu-id="372f4-106">**Nota:** se la proprietà **MatchSource** è impostata su **$false**, che è il valore predefinito, i contenuti che devono essere copiati vengono memorizzati nella cache la prima volta in cui viene applicata la configurazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-106">**Note:** If the **MatchSource** property is set to **$false** (which is the default value), the contents to be copied are cached the first time the configuration is applied.</span></span> 
><span data-ttu-id="372f4-107">Alle applicazioni successive della configurazione non verrà eseguito il controllo dei file o delle cartelle aggiornati nel percorso specificato in **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="372f4-107">Subsequent applications of the configuration will not check for updated files and/or folders in the path specified by **SourcePath**.</span></span> <span data-ttu-id="372f4-108">Se si vuole cercare gli aggiornamenti per il file o le cartelle in **SourcePath** ogni volta che viene applicata la configurazione, impostare **MatchSource** su **$true**.</span><span class="sxs-lookup"><span data-stu-id="372f4-108">If you want to check for updates to the files and/or folders in **SourcePath** every time the configuration is applied, set **MatchSource** to **$true**.</span></span> 

## <a name="syntax"></a><span data-ttu-id="372f4-109">Sintassi</span><span class="sxs-lookup"><span data-stu-id="372f4-109">Syntax</span></span>
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ] 
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ] 
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a><span data-ttu-id="372f4-110">Proprietà</span><span class="sxs-lookup"><span data-stu-id="372f4-110">Properties</span></span>

|  <span data-ttu-id="372f4-111">Proprietà</span><span class="sxs-lookup"><span data-stu-id="372f4-111">Property</span></span>  |  <span data-ttu-id="372f4-112">Description</span><span class="sxs-lookup"><span data-stu-id="372f4-112">Description</span></span>   | 
|---|---| 
| <span data-ttu-id="372f4-113">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="372f4-113">DestinationPath</span></span>| <span data-ttu-id="372f4-114">Indica il percorso in cui si vuole specificare lo stato di un file o una directory.</span><span class="sxs-lookup"><span data-stu-id="372f4-114">Indicates the location where you want to ensure the state for a file or directory.</span></span>| 
| <span data-ttu-id="372f4-115">Attributes</span><span class="sxs-lookup"><span data-stu-id="372f4-115">Attributes</span></span>| <span data-ttu-id="372f4-116">Specifica lo stato desiderato degli attributi per il file o la directory di destinazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-116">Specifies the desired state of the attributes for the targeted file or directory.</span></span>| 
| <span data-ttu-id="372f4-117">Checksum</span><span class="sxs-lookup"><span data-stu-id="372f4-117">Checksum</span></span>| <span data-ttu-id="372f4-118">Indica il tipo di checksum da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="372f4-118">Indicates the checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="372f4-119">Se la proprietà __Checksum__ non è specificata, per il confronto viene usato solo il nome del file o della directory.</span><span class="sxs-lookup"><span data-stu-id="372f4-119">If __Checksum__ is not specified, only the file or directory name is used for comparison.</span></span> <span data-ttu-id="372f4-120">I valori validi includono: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span><span class="sxs-lookup"><span data-stu-id="372f4-120">Valid values include: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.</span></span>| 
| <span data-ttu-id="372f4-121">Contents</span><span class="sxs-lookup"><span data-stu-id="372f4-121">Contents</span></span>| <span data-ttu-id="372f4-122">Specifica il contenuto di un file, ad esempio una determinata stringa.</span><span class="sxs-lookup"><span data-stu-id="372f4-122">Specifies the contents of a file, such as a particular string.</span></span>| 
| <span data-ttu-id="372f4-123">Credential</span><span class="sxs-lookup"><span data-stu-id="372f4-123">Credential</span></span>| <span data-ttu-id="372f4-124">Indica le credenziali necessarie per accedere alle risorse, ad esempio i file di origine, se tale accesso è necessario.</span><span class="sxs-lookup"><span data-stu-id="372f4-124">Indicates the credentials that are required to access resources, such as source files, if such access is required.</span></span>| 
| <span data-ttu-id="372f4-125">Ensure</span><span class="sxs-lookup"><span data-stu-id="372f4-125">Ensure</span></span>| <span data-ttu-id="372f4-126">Indica se il file o la directory esiste.</span><span class="sxs-lookup"><span data-stu-id="372f4-126">Indicates if the file or directory exists.</span></span> <span data-ttu-id="372f4-127">Impostare questa proprietà su "Absent" per specificare che il file o la directory non esiste.</span><span class="sxs-lookup"><span data-stu-id="372f4-127">Set this property to "Absent" to ensure that the file or directory does not exist.</span></span> <span data-ttu-id="372f4-128">Impostarla su "Present" per specificare che il file o la directory esiste.</span><span class="sxs-lookup"><span data-stu-id="372f4-128">Set it to "Present" to ensure that the file or directory does exist.</span></span> <span data-ttu-id="372f4-129">Il valore predefinito è "Present".</span><span class="sxs-lookup"><span data-stu-id="372f4-129">The default is "Present".</span></span>| 
| <span data-ttu-id="372f4-130">Force</span><span class="sxs-lookup"><span data-stu-id="372f4-130">Force</span></span>| <span data-ttu-id="372f4-131">Determinate operazioni sui file, ad esempio quando si sovrascrive un file o si elimina una directory non vuota, generano un errore.</span><span class="sxs-lookup"><span data-stu-id="372f4-131">Certain file operations (such as overwriting a file or deleting a directory that is not empty) will result in an error.</span></span> <span data-ttu-id="372f4-132">Usando la proprietà Force, tali errori vengono ignorati.</span><span class="sxs-lookup"><span data-stu-id="372f4-132">Using the Force property overrides such errors.</span></span> <span data-ttu-id="372f4-133">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="372f4-133">The default value is __$false__.</span></span>| 
| <span data-ttu-id="372f4-134">Recurse</span><span class="sxs-lookup"><span data-stu-id="372f4-134">Recurse</span></span>| <span data-ttu-id="372f4-135">Indica se le sottodirectory sono incluse.</span><span class="sxs-lookup"><span data-stu-id="372f4-135">Indicates if subdirectories are included.</span></span> <span data-ttu-id="372f4-136">Impostare questa proprietà su __$true__ per indicare che le sottodirectory devono essere incluse.</span><span class="sxs-lookup"><span data-stu-id="372f4-136">Set this property to __$true__ to indicate that you want subdirectories to be included.</span></span> <span data-ttu-id="372f4-137">Il valore predefinito è __$false__.</span><span class="sxs-lookup"><span data-stu-id="372f4-137">The default is __$false__.</span></span> <span data-ttu-id="372f4-138">**Nota**: questa proprietà è valida solo quando la proprietà Type è impostata su Directory.</span><span class="sxs-lookup"><span data-stu-id="372f4-138">**Note**: This property is only valid when the Type property is set to Directory.</span></span>| 
| <span data-ttu-id="372f4-139">DependsOn</span><span class="sxs-lookup"><span data-stu-id="372f4-139">DependsOn</span></span> | <span data-ttu-id="372f4-140">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="372f4-140">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="372f4-141">Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è __ResourceName__ e il tipo è __ResourceType__, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="372f4-141">For example, if the ID of the resource configuration script block that you want to run first is __ResourceName__ and its type is __ResourceType__, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>| 
| <span data-ttu-id="372f4-142">SourcePath</span><span class="sxs-lookup"><span data-stu-id="372f4-142">SourcePath</span></span>| <span data-ttu-id="372f4-143">Indica il percorso da cui copiare la risorsa file o cartella.</span><span class="sxs-lookup"><span data-stu-id="372f4-143">Indicates the path from which to copy the file or folder resource.</span></span>| 
| <span data-ttu-id="372f4-144">Tipo</span><span class="sxs-lookup"><span data-stu-id="372f4-144">Type</span></span>| <span data-ttu-id="372f4-145">Indica se la risorsa configurata è una directory o un file.</span><span class="sxs-lookup"><span data-stu-id="372f4-145">Indicates if the resource being configured is a directory or a file.</span></span> <span data-ttu-id="372f4-146">Impostare questa proprietà su "Directory" per indicare che la risorsa è una directory.</span><span class="sxs-lookup"><span data-stu-id="372f4-146">Set this property to "Directory" to indicate that the resource is a directory.</span></span> <span data-ttu-id="372f4-147">Impostarla su "File" per indicare che la risorsa è un file.</span><span class="sxs-lookup"><span data-stu-id="372f4-147">Set it to "File" to indicate that the resource is a file.</span></span> <span data-ttu-id="372f4-148">Il valore predefinito è "File".</span><span class="sxs-lookup"><span data-stu-id="372f4-148">The default value is “File”.</span></span>| 
| <span data-ttu-id="372f4-149">MatchSource</span><span class="sxs-lookup"><span data-stu-id="372f4-149">MatchSource</span></span>| <span data-ttu-id="372f4-150">Se questa proprietà è impostata sul valore predefinito __$false__, tutti i file nell'origine (ad esempio i file A, B e C) verranno aggiunti nella destinazione la prima volta che viene applicata la configurazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-150">If set to the default value of __$false__, then any files on the source (say, files A, B, and C) will be added to the destination the first time the configuration is applied.</span></span> <span data-ttu-id="372f4-151">Se viene aggiunto un nuovo file (D) nell'origine, non verrà aggiunto nella destinazione, anche quando la configurazione viene applicata di nuovo in un secondo momento.</span><span class="sxs-lookup"><span data-stu-id="372f4-151">If a new file (D) is added to the source, it will not be added to the destination, even when the configuration is re-applied later.</span></span> <span data-ttu-id="372f4-152">Se il valore è __$true__, ogni volta che la configurazione viene applicata, i nuovi file trovati successivamente nell'origine (ad esempio il file D in questo esempio) vengono aggiunti nella destinazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-152">If the value is __$true__, then each time the configuration is applied, new files subsequently found on the source (such as file D in this example) are added to the destination.</span></span> <span data-ttu-id="372f4-153">Il valore predefinito è **$false**.</span><span class="sxs-lookup"><span data-stu-id="372f4-153">The default value is **$false**.</span></span>| 

## <a name="example"></a><span data-ttu-id="372f4-154">Esempio</span><span class="sxs-lookup"><span data-stu-id="372f4-154">Example</span></span>

<span data-ttu-id="372f4-155">L'esempio seguente mostra come usare la risorsa File per specificare che una cartella con il percorso `C:\Users\Public\Documents\DSCDemo\DemoSource` in un computer di origine (ad esempio, il server di pull) deve essere presente anche (insieme a tutte le sottodirectory) nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-155">The following example shows how to use the File resource to ensure that a directory with the path `C:\Users\Public\Documents\DSCDemo\DemoSource` on a source computer (such as the “pull” server) is also present (along with all subdirectories) on the target node.</span></span> <span data-ttu-id="372f4-156">Viene anche scritto nel registro un messaggio di conferma al termine dell'operazione e viene inclusa un'istruzione per specificare che l'operazione di controllo dei file venga eseguita prima dell'operazione di registrazione.</span><span class="sxs-lookup"><span data-stu-id="372f4-156">It also writes a confirmatory message to the log when complete and includes a statement to ensure that the file-checking operation runs prior to the logging operation.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"    
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```

