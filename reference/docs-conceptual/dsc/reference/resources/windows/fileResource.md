---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa File DSC
ms.openlocfilehash: 4c6945d4cdcbc64ac6d52db563823efe8fd0247e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954678"
---
# <a name="dsc-file-resource"></a><span data-ttu-id="7f193-103">Risorsa File DSC</span><span class="sxs-lookup"><span data-stu-id="7f193-103">DSC File Resource</span></span>

> <span data-ttu-id="7f193-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x</span><span class="sxs-lookup"><span data-stu-id="7f193-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.x</span></span>

<span data-ttu-id="7f193-105">La risorsa **File** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire file e cartelle nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-105">The **File** resource in Windows PowerShell Desired State Configuration (DSC) provides a mechanism to manage files and folders on the target node.</span></span> <span data-ttu-id="7f193-106">**DestinationPath** e **SourcePath** devono entrambi essere accessibili per il nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-106">**DestinationPath** and **SourcePath** must both be accessible by the target Node.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f193-107">Sintassi</span><span class="sxs-lookup"><span data-stu-id="7f193-107">Syntax</span></span>

```Syntax
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a><span data-ttu-id="7f193-108">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7f193-108">Properties</span></span>

|<span data-ttu-id="7f193-109">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7f193-109">Property</span></span> |<span data-ttu-id="7f193-110">Description</span><span class="sxs-lookup"><span data-stu-id="7f193-110">Description</span></span> |
|---|---|
|<span data-ttu-id="7f193-111">DestinationPath</span><span class="sxs-lookup"><span data-stu-id="7f193-111">DestinationPath</span></span> |<span data-ttu-id="7f193-112">Il percorso, nel nodo di destinazione, per il quale ci si vuole assicurare che sia **Present** o **Absent** con **Ensure**.</span><span class="sxs-lookup"><span data-stu-id="7f193-112">The location, on the target node, you want to ensure is **Present** or **Absent** with **Ensure**.</span></span> |
|<span data-ttu-id="7f193-113">Attributi</span><span class="sxs-lookup"><span data-stu-id="7f193-113">Attributes</span></span> |<span data-ttu-id="7f193-114">Lo stato desiderato degli attributi per il file o la directory di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-114">The desired state of the attributes for the targeted file or directory.</span></span> <span data-ttu-id="7f193-115">I valori validi sono _Archive_, _Hidden_, _ReadOnly_ e _System_.</span><span class="sxs-lookup"><span data-stu-id="7f193-115">Valid values are _Archive_, _Hidden_, _ReadOnly_, and _System_.</span></span> |
|<span data-ttu-id="7f193-116">Checksum</span><span class="sxs-lookup"><span data-stu-id="7f193-116">Checksum</span></span> |<span data-ttu-id="7f193-117">Il tipo di checksum da usare per determinare se due file sono uguali.</span><span class="sxs-lookup"><span data-stu-id="7f193-117">The checksum type to use when determining whether two files are the same.</span></span> <span data-ttu-id="7f193-118">I valori validi includono: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span><span class="sxs-lookup"><span data-stu-id="7f193-118">Valid values include: **SHA-1**, **SHA-256**, **SHA-512**, **createdDate**, **modifiedDate**.</span></span> |
|<span data-ttu-id="7f193-119">Contenuti</span><span class="sxs-lookup"><span data-stu-id="7f193-119">Contents</span></span> |<span data-ttu-id="7f193-120">Valido solo se usato con **Type** **File**.</span><span class="sxs-lookup"><span data-stu-id="7f193-120">Only valid when used with **Type** **File**.</span></span> <span data-ttu-id="7f193-121">Indica il contenuto per il quale ci si vuole assicurare (**Ensure**) che sia **Present** o **Absent** nel file di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-121">Indicates the contents to **Ensure** are **Present** or **Absent** from the targeted file.</span></span> |
|<span data-ttu-id="7f193-122">Credential</span><span class="sxs-lookup"><span data-stu-id="7f193-122">Credential</span></span> |<span data-ttu-id="7f193-123">Le credenziali necessarie per accedere alle risorse, ad esempio i file di origine.</span><span class="sxs-lookup"><span data-stu-id="7f193-123">The credentials that are required to access resources, such as source files.</span></span> |
|<span data-ttu-id="7f193-124">Force</span><span class="sxs-lookup"><span data-stu-id="7f193-124">Force</span></span> |<span data-ttu-id="7f193-125">Esegue l'override di operazioni di accesso che genererebbero un errore, ad esempio quando si sovrascrive un file o si elimina una directory non vuota.</span><span class="sxs-lookup"><span data-stu-id="7f193-125">Overrides access operations that would result in an error (such as overwriting a file or deleting a directory that is not empty).</span></span> <span data-ttu-id="7f193-126">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="7f193-126">Default value is `$false`.</span></span> |
|<span data-ttu-id="7f193-127">Recurse</span><span class="sxs-lookup"><span data-stu-id="7f193-127">Recurse</span></span> |<span data-ttu-id="7f193-128">Valido solo se usato con **Type** **Directory**.</span><span class="sxs-lookup"><span data-stu-id="7f193-128">Only valid when used with **Type** **Directory**.</span></span> <span data-ttu-id="7f193-129">Esegue in modo ricorsivo l'operazione di stato per tutte le sottodirectory.</span><span class="sxs-lookup"><span data-stu-id="7f193-129">Performs the state operation recursively to all subdirectories.</span></span> <span data-ttu-id="7f193-130">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="7f193-130">Default value is `$false`.</span></span> |
|<span data-ttu-id="7f193-131">SourcePath</span><span class="sxs-lookup"><span data-stu-id="7f193-131">SourcePath</span></span> |<span data-ttu-id="7f193-132">Il percorso da cui copiare la risorsa file o cartella.</span><span class="sxs-lookup"><span data-stu-id="7f193-132">The path from which to copy the file or folder resource.</span></span> |
|<span data-ttu-id="7f193-133">Type</span><span class="sxs-lookup"><span data-stu-id="7f193-133">Type</span></span> |<span data-ttu-id="7f193-134">Il tipo di risorsa configurata.</span><span class="sxs-lookup"><span data-stu-id="7f193-134">The type of resource being configured.</span></span> <span data-ttu-id="7f193-135">I valori validi sono **Directory** e **File**.</span><span class="sxs-lookup"><span data-stu-id="7f193-135">Valid values are **Directory** and **File**.</span></span> <span data-ttu-id="7f193-136">Il valore predefinito è **File**.</span><span class="sxs-lookup"><span data-stu-id="7f193-136">Default value is **File**.</span></span> |
|<span data-ttu-id="7f193-137">MatchSource</span><span class="sxs-lookup"><span data-stu-id="7f193-137">MatchSource</span></span> |<span data-ttu-id="7f193-138">Determina se la risorsa deve monitorare i nuovi file aggiunti alla directory di origine dopo la copia iniziale.</span><span class="sxs-lookup"><span data-stu-id="7f193-138">Determines if the resource should monitor for new files added to the source directory after the initial copy.</span></span> <span data-ttu-id="7f193-139">Un valore di `$true` indica che, dopo la copia iniziale, i nuovi file di origine devono essere copiati nella destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-139">A value of `$true` indicates that, after the initial copy, any new source files should be copied to the destination.</span></span> <span data-ttu-id="7f193-140">Se impostato su `$false`, la risorsa memorizza nella cache il contenuto della directory di origine e ignora eventuali file aggiunti dopo la copia iniziale.</span><span class="sxs-lookup"><span data-stu-id="7f193-140">If set to `$false`, the resource caches the contents of the source directory and ignores any files added after the initial copy.</span></span> <span data-ttu-id="7f193-141">Il valore predefinito è `$false`.</span><span class="sxs-lookup"><span data-stu-id="7f193-141">Default value is `$false`.</span></span> |

> [!WARNING]
> <span data-ttu-id="7f193-142">Se non si specifica un valore per **Credential** o **PSRunAsCredential**, la risorsa userà l'account computer del nodo di destinazione per accedere a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="7f193-142">If you do not specify a value for **Credential** or **PSRunAsCredential**, the resource will use the computer account of the target node to access the **SourcePath**.</span></span> <span data-ttu-id="7f193-143">Quando **SourcePath** è una condivisione UNC, ciò potrebbe causare un errore di "Accesso negato".</span><span class="sxs-lookup"><span data-stu-id="7f193-143">When the **SourcePath** is a UNC share, this could result in an "Access Denied" error.</span></span> <span data-ttu-id="7f193-144">Assicurarsi che le autorizzazioni siano impostate di conseguenza o usino le proprietà **Credential** o **PSRunAsCredential** per specificare l'account da usare.</span><span class="sxs-lookup"><span data-stu-id="7f193-144">Please ensure your permissions are set accordingly, or use the **Credential** or **PSRunAsCredential** properties to specify the account that should be used.</span></span>

## <a name="common-properties"></a><span data-ttu-id="7f193-145">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="7f193-145">Common properties</span></span>

|<span data-ttu-id="7f193-146">Proprietà</span><span class="sxs-lookup"><span data-stu-id="7f193-146">Property</span></span> |<span data-ttu-id="7f193-147">Description</span><span class="sxs-lookup"><span data-stu-id="7f193-147">Description</span></span> |
|---|---|
|<span data-ttu-id="7f193-148">DependsOn</span><span class="sxs-lookup"><span data-stu-id="7f193-148">DependsOn</span></span> |<span data-ttu-id="7f193-149">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="7f193-149">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="7f193-150">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="7f193-150">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="7f193-151">Ensure</span><span class="sxs-lookup"><span data-stu-id="7f193-151">Ensure</span></span> |<span data-ttu-id="7f193-152">Determina se il file e **Contents** in **Destination** devono esistere o meno.</span><span class="sxs-lookup"><span data-stu-id="7f193-152">Determines whether the file and **Contents** at the **Destination** should exist or not.</span></span> <span data-ttu-id="7f193-153">Impostare questa proprietà su **Present** per assicurarsi che il file esista.</span><span class="sxs-lookup"><span data-stu-id="7f193-153">Set this property to **Present** to ensure the file exists.</span></span> <span data-ttu-id="7f193-154">Impostarla su **Absent** per specificare che il contenuto non esiste.</span><span class="sxs-lookup"><span data-stu-id="7f193-154">Set it to **Absent** to ensure they do not exist.</span></span> <span data-ttu-id="7f193-155">Il valore predefinito è **Present**.</span><span class="sxs-lookup"><span data-stu-id="7f193-155">The default value is **Present**.</span></span> |
|<span data-ttu-id="7f193-156">PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="7f193-156">PsDscRunAsCredential</span></span> |<span data-ttu-id="7f193-157">Imposta le credenziali per l'esecuzione dell'intera risorsa.</span><span class="sxs-lookup"><span data-stu-id="7f193-157">Sets the credential for running the entire resource as.</span></span> |

> [!NOTE]
> <span data-ttu-id="7f193-158">La proprietà comune **PsDscRunAsCredential** è stata aggiunta in WMF 5.0 per consentire l'esecuzione di qualsiasi risorsa DSC nel contesto di altre credenziali.</span><span class="sxs-lookup"><span data-stu-id="7f193-158">The **PsDscRunAsCredential** common property was added in WMF 5.0 to allow running any DSC resource in the context of other credentials.</span></span> <span data-ttu-id="7f193-159">Per altre informazioni, vedere [Usare credenziali con risorse DSC](../../../configurations/runasuser.md).</span><span class="sxs-lookup"><span data-stu-id="7f193-159">For more information, see [Use Credentials with DSC Resources](../../../configurations/runasuser.md).</span></span>

### <a name="additional-information"></a><span data-ttu-id="7f193-160">Altre informazioni</span><span class="sxs-lookup"><span data-stu-id="7f193-160">Additional information</span></span>

- <span data-ttu-id="7f193-161">Quando si specifica solo un **DestinationPath**, la risorsa garantisce che il percorso esista se **Present** o non esista se **Absent**.</span><span class="sxs-lookup"><span data-stu-id="7f193-161">When you only specify a **DestinationPath**, the resource ensures that the path exists if **Present** or does not exist if **Absent**.</span></span>
- <span data-ttu-id="7f193-162">Quando si specifica un **SourcePath** e un **DestinationPath** con un valore **Type** **Directory**, la risorsa copia la directory di origine nel percorso di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-162">When you specify a **SourcePath** and a **DestinationPath** with a **Type** value of **Directory**, the resource copies source directory to the destination path.</span></span> <span data-ttu-id="7f193-163">Le proprietà **Recurse**, **Force** e **MatchSource** modificano il tipo di operazione di copia eseguita, mentre **Credential** determina quale account usare per accedere alla directory di origine.</span><span class="sxs-lookup"><span data-stu-id="7f193-163">The properties **Recurse**, **Force**, and **MatchSource** change the type of copy operation performed, while **Credential** determines which account to use to access the source directory.</span></span>
- <span data-ttu-id="7f193-164">Se si specifica il valore **ReadOnly** per la proprietà **Attributes** insieme a un **DestinationPath**, **Ensure** **Present** crea il percorso specificato, mentre **Contents** imposta il contenuto del file.</span><span class="sxs-lookup"><span data-stu-id="7f193-164">If you specified a value of **ReadOnly** for the **Attributes** property alongside a **DestinationPath**, **Ensure** **Present** would create the path specified, while **Contents** would set the contents of the file.</span></span> <span data-ttu-id="7f193-165">Con l'impostazione **Absent** per **Ensure** la proprietà **Attributes** verrebbe ignorata interamente e verrebbe rimosso qualsiasi file nel percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="7f193-165">An **Ensure** **Absent** setting would ignore the **Attributes** property entirely, and remove any file at the specified path.</span></span>

## <a name="example"></a><span data-ttu-id="7f193-166">Esempio</span><span class="sxs-lookup"><span data-stu-id="7f193-166">Example</span></span>

<span data-ttu-id="7f193-167">L'esempio copia una directory e le relative sottodirectory da un server di pull a un nodo di destinazione usando la risorsa File.</span><span class="sxs-lookup"><span data-stu-id="7f193-167">The following example copies a directory and its subdirectories from a pull server to a target node using the File Resource.</span></span> <span data-ttu-id="7f193-168">Se l'operazione ha esito positivo, la risorsa Log scrive un messaggio di conferma nel registro eventi.</span><span class="sxs-lookup"><span data-stu-id="7f193-168">If the operation succeeds, the Log resource writes a confirmation message to the event log.</span></span>

<span data-ttu-id="7f193-169">La directory di origine è un percorso UNC (`\\PullServer\DemoSource`) condiviso dal server di pull.</span><span class="sxs-lookup"><span data-stu-id="7f193-169">The source directory is a UNC path (`\\PullServer\DemoSource`) shared from the Pull Server.</span></span> <span data-ttu-id="7f193-170">La proprietà **Recurse** garantisce che vengano copiate anche tutte le sottodirectory.</span><span class="sxs-lookup"><span data-stu-id="7f193-170">The **Recurse** property ensures that all subdirectories are copied as well.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7f193-171">La gestione configurazione locale (LCM) nel nodo di destinazione viene eseguita per impostazione predefinita nel contesto dell'account di sistema locale.</span><span class="sxs-lookup"><span data-stu-id="7f193-171">The LCM on the target Node executes in the context of the local system account by default.</span></span> <span data-ttu-id="7f193-172">Per concedere l'accesso a **SourcePath**, assegnare autorizzazioni appropriate all'account computer del nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="7f193-172">To grant access to the **SourcePath**, give the target Node's computer account appropriate permissions.</span></span> <span data-ttu-id="7f193-173">**Credential** e **PSDSCRunAsCredential** modificano entrambi il contesto usato da Gestione configurazione locale (LCM) per accedere a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="7f193-173">The **Credential** and **PSDSCRunAsCredential** both change the context the LCM uses to access the **SourcePath**.</span></span> <span data-ttu-id="7f193-174">È comunque necessario concedere l'accesso all'account che verrà usato per l'accesso a **SourcePath**.</span><span class="sxs-lookup"><span data-stu-id="7f193-174">You still need to grant access to the account that will be used to access the **SourcePath**.</span></span>

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present" # Ensure the directory is Present on the target node.
            Type = "Directory" # The default is File.
            Recurse = $true # Recursively copy all subdirectories.
            SourcePath = "\\PullServer\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # Depends on successful execution of the File resource.
        }
    }
}
```

<span data-ttu-id="7f193-175">Per altre informazioni sull'uso delle **Credenziali** in DSC, [Usare credenziali con risorse DSC](../../../configurations/runAsUser.md) o [Opzioni delle credenziali nei dati di configurazione](../../../configurations/configDataCredentials.md).</span><span class="sxs-lookup"><span data-stu-id="7f193-175">For more on using **Credentials** in DSC see [Run As User](../../../configurations/runAsUser.md) or [Config Data Credentials](../../../configurations/configDataCredentials.md).</span></span>