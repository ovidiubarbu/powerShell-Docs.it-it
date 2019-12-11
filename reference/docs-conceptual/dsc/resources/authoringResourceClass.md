---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Scrittura di una risorsa DSC personalizzata con classi di PowerShell
ms.openlocfilehash: 34356f65bcb83153e7395a16d2a4a5cf2e507332
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71952828"
---
# <a name="writing-a-custom-dsc-resource-with-powershell-classes"></a><span data-ttu-id="4f67a-103">Scrittura di una risorsa DSC personalizzata con classi di PowerShell</span><span class="sxs-lookup"><span data-stu-id="4f67a-103">Writing a custom DSC resource with PowerShell classes</span></span>

> <span data-ttu-id="4f67a-104">Si applica a: Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4f67a-104">Applies To: Windows PowerShell 5.0</span></span>

<span data-ttu-id="4f67a-105">Con l'introduzione delle classi di PowerShell in Windows PowerShell 5.0, è ora possibile definire una risorsa DSC creando una classe.</span><span class="sxs-lookup"><span data-stu-id="4f67a-105">With the introduction of PowerShell classes in Windows PowerShell 5.0, you can now define a DSC resource by creating a class.</span></span> <span data-ttu-id="4f67a-106">La classe definisce sia lo schema sia l'implementazione della risorsa, quindi non è necessario creare un file MOF distinto.</span><span class="sxs-lookup"><span data-stu-id="4f67a-106">The class defines both the schema and the implementation of the resource, so there is no need to create a separate MOF file.</span></span> <span data-ttu-id="4f67a-107">La struttura di cartelle per una risorsa basata su classi è inoltre più semplice, perché non è necessaria una cartella **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-107">The folder structure for a class-based resource is also simpler, because a **DSCResources** folder is not necessary.</span></span>

<span data-ttu-id="4f67a-108">In una risorsa DSC basata su classi, lo schema viene definito come proprietà della classe che è possibile modificare con attributi per specificare il tipo di proprietà.</span><span class="sxs-lookup"><span data-stu-id="4f67a-108">In a class-based DSC resource, the schema is defined as properties of the class which can be modified with attributes to specify the property type..</span></span> <span data-ttu-id="4f67a-109">La risorsa è implementata dai metodi **Get()** , **Set()** e **Test()** (equivalenti alle funzioni **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** in una risorsa script.</span><span class="sxs-lookup"><span data-stu-id="4f67a-109">The resource is implemented by **Get()**, **Set()**, and **Test()** methods (equivalent to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="4f67a-110">In questo argomento verrà creata una risorsa semplice denominata **FileResource** che gestisce un file in un percorso specificato.</span><span class="sxs-lookup"><span data-stu-id="4f67a-110">In this topic, we will create a simple resource named **FileResource** that manages a file in a specified path.</span></span>

<span data-ttu-id="4f67a-111">Per altre informazioni sulle risorse DSC, vedere [Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate](authoringResource.md).</span><span class="sxs-lookup"><span data-stu-id="4f67a-111">For more information about DSC resources, see [Build Custom Windows PowerShell Desired State Configuration Resources](authoringResource.md)</span></span>

><span data-ttu-id="4f67a-112">**Nota:** le raccolte generiche non sono supportate nelle risorse basate su classi.</span><span class="sxs-lookup"><span data-stu-id="4f67a-112">**Note:** Generic collections are not supported in class-based resources.</span></span>

## <a name="folder-structure-for-a-class-resource"></a><span data-ttu-id="4f67a-113">Struttura di cartelle per una risorsa basata su classi</span><span class="sxs-lookup"><span data-stu-id="4f67a-113">Folder structure for a class resource</span></span>

<span data-ttu-id="4f67a-114">Per implementare una risorsa DSC personalizzata con una classe di PowerShell, creare la struttura di cartelle seguente.</span><span class="sxs-lookup"><span data-stu-id="4f67a-114">To implement a DSC custom resource with a PowerShell class, create the following folder structure.</span></span> <span data-ttu-id="4f67a-115">La classe è definita in **MyDscResource.psm1** e il manifesto del modulo è definito in **MyDscResource.psd1**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-115">The class is defined in **MyDscResource.psm1** and the module manifest is defined in **MyDscResource.psd1**.</span></span>

```
$env:ProgramFiles\WindowsPowerShell\Modules (folder)
    |- MyDscResource (folder)
        MyDscResource.psm1
        MyDscResource.psd1
```

## <a name="create-the-class"></a><span data-ttu-id="4f67a-116">Creare la classe</span><span class="sxs-lookup"><span data-stu-id="4f67a-116">Create the class</span></span>

<span data-ttu-id="4f67a-117">Per creare una classe di PowerShell, usare la parola chiave class.</span><span class="sxs-lookup"><span data-stu-id="4f67a-117">You use the class keyword to create a PowerShell class.</span></span> <span data-ttu-id="4f67a-118">Per specificare che una classe è una risorsa DSC, usare l'attributo **DscResource()** .</span><span class="sxs-lookup"><span data-stu-id="4f67a-118">To specify that a class is a DSC resource, use the **DscResource()** attribute.</span></span> <span data-ttu-id="4f67a-119">Il nome della classe è il nome della risorsa DSC.</span><span class="sxs-lookup"><span data-stu-id="4f67a-119">The name of the class is the name of the DSC resource.</span></span>

```powershell
[DscResource()]
class FileResource {
}
```

### <a name="declare-properties"></a><span data-ttu-id="4f67a-120">Dichiarare le proprietà</span><span class="sxs-lookup"><span data-stu-id="4f67a-120">Declare properties</span></span>

<span data-ttu-id="4f67a-121">Lo schema della risorsa DSC viene definito come proprietà della classe.</span><span class="sxs-lookup"><span data-stu-id="4f67a-121">The DSC resource schema is defined as properties of the class.</span></span> <span data-ttu-id="4f67a-122">Vengono dichiarate tre proprietà, come indicato di seguito.</span><span class="sxs-lookup"><span data-stu-id="4f67a-122">We declare three properties as follows.</span></span>

```powershell
[DscProperty(Key)]
[string]$Path

[DscProperty(Mandatory)]
[Ensure] $Ensure

[DscProperty(Mandatory)]
[string] $SourcePath

[DscProperty(NotConfigurable)]
[Nullable[datetime]] $CreationTime
```

<span data-ttu-id="4f67a-123">Si noti che le proprietà sono modificate dagli attributi.</span><span class="sxs-lookup"><span data-stu-id="4f67a-123">Notice that the properties are modified by attributes.</span></span> <span data-ttu-id="4f67a-124">Il significato degli attributi è il seguente:</span><span class="sxs-lookup"><span data-stu-id="4f67a-124">The meaning of the attributes is as follows:</span></span>

- <span data-ttu-id="4f67a-125">**DscProperty(Key)** : la proprietà è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="4f67a-125">**DscProperty(Key)**: The property is required.</span></span> <span data-ttu-id="4f67a-126">La proprietà è una chiave.</span><span class="sxs-lookup"><span data-stu-id="4f67a-126">The property is a key.</span></span> <span data-ttu-id="4f67a-127">I valori di tutte le proprietà contrassegnate come chiavi devono essere combinati per identificare in modo univoco un'istanza di risorsa all'interno di una configurazione.</span><span class="sxs-lookup"><span data-stu-id="4f67a-127">The values of all properties marked as keys must combine to uniquely identify a resource instance within a configuration.</span></span>
- <span data-ttu-id="4f67a-128">**DscProperty(Mandatory)** : la proprietà è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="4f67a-128">**DscProperty(Mandatory)**: The property is required.</span></span>
- <span data-ttu-id="4f67a-129">**DscProperty(NotConfigurable)** : la proprietà è di sola lettura.</span><span class="sxs-lookup"><span data-stu-id="4f67a-129">**DscProperty(NotConfigurable)**: The property is read-only.</span></span> <span data-ttu-id="4f67a-130">Le proprietà contrassegnate con questo attributo non possono essere impostate da una configurazione, ma vengono popolate dal metodo **Get()** , quando presente.</span><span class="sxs-lookup"><span data-stu-id="4f67a-130">Properties marked with this attribute cannot be set by a configuration, but are populated by the **Get()** method when present.</span></span>
- <span data-ttu-id="4f67a-131">**DscProperty()** : la proprietà è configurabile, ma non è obbligatoria.</span><span class="sxs-lookup"><span data-stu-id="4f67a-131">**DscProperty()**: The property is configurable, but it is not required.</span></span>

<span data-ttu-id="4f67a-132">Le proprietà **$Path** e **$SourcePath** sono entrambe stringhe.</span><span class="sxs-lookup"><span data-stu-id="4f67a-132">The **$Path** and **$SourcePath** properties are both strings.</span></span> <span data-ttu-id="4f67a-133">**$CreationTime** è una proprietà [DateTime](/dotnet/api/system.datetime).</span><span class="sxs-lookup"><span data-stu-id="4f67a-133">The **$CreationTime** is a [DateTime](/dotnet/api/system.datetime) property.</span></span> <span data-ttu-id="4f67a-134">La proprietà **$Ensure** è un tipo di enumerazione, definito come segue.</span><span class="sxs-lookup"><span data-stu-id="4f67a-134">The **$Ensure** property is an enumeration type, defined as follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}
```

### <a name="implementing-the-methods"></a><span data-ttu-id="4f67a-135">Implementare i metodi</span><span class="sxs-lookup"><span data-stu-id="4f67a-135">Implementing the methods</span></span>

<span data-ttu-id="4f67a-136">I metodi **Get()** , **Set()** e **Test()** sono analoghi alle funzioni **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource** in una risorsa script.</span><span class="sxs-lookup"><span data-stu-id="4f67a-136">The **Get()**, **Set()**, and **Test()** methods are analogous to the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** functions in a script resource.</span></span>

<span data-ttu-id="4f67a-137">Questo codice include anche la funzione CopyFile(), una funzione helper che copia il file da **$SourcePath** a **$Path**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-137">This code also includes the CopyFile() function, a helper function that copies the file from **$SourcePath** to **$Path**.</span></span>

```powershell
    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)

        if ($this.ensure -eq [Ensure]::Present)
        {
            if(-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ErrorAction Ignore

        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = New-Object -TypeName System.IO.FileInfo($this.Path)

        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
```

### <a name="the-complete-file"></a><span data-ttu-id="4f67a-138">File completo</span><span class="sxs-lookup"><span data-stu-id="4f67a-138">The complete file</span></span>

<span data-ttu-id="4f67a-139">Il file di classe completo è illustrato di seguito.</span><span class="sxs-lookup"><span data-stu-id="4f67a-139">The complete class file follows.</span></span>

```powershell
enum Ensure
{
    Absent
    Present
}

<#
   This resource manages the file in a specific path.
   [DscResource()] indicates the class is a DSC resource
#>

[DscResource()]
class FileResource
{
    <#
       This property is the fully qualified path to the file that is
       expected to be present or absent.

       The [DscProperty(Key)] attribute indicates the property is a
       key and its value uniquely identifies a resource instance.
       Defining this attribute also means the property is required
       and DSC will ensure a value is set before calling the resource.

       A DSC resource must define at least one key property.
    #>
    [DscProperty(Key)]
    [string]$Path

    <#
        This property indicates if the settings should be present or absent
        on the system. For present, the resource ensures the file pointed
        to by $Path exists. For absent, it ensures the file point to by
        $Path does not exist.

        The [DscProperty(Mandatory)] attribute indicates the property is
        required and DSC will guarantee it is set.

        If Mandatory is not specified or if it is defined as
        Mandatory=$false, the value is not guaranteed to be set when DSC
        calls the resource.  This is appropriate for optional properties.
    #>
    [DscProperty(Mandatory)]
    [Ensure] $Ensure

    <#
       This property defines the fully qualified path to a file that will
       be placed on the system if $Ensure = Present and $Path does not
        exist.

       NOTE: This property is required because [DscProperty(Mandatory)] is
        set.
    #>
    [DscProperty(Mandatory)]
    [string] $SourcePath

    <#
       This property reports the file's create timestamp.

       [DscProperty(NotConfigurable)] attribute indicates the property is
       not configurable in DSC configuration.  Properties marked this way
       are populated by the Get() method to report additional details
       about the resource when it is present.

    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $CreationTime

    <#
        This method is equivalent of the Set-TargetResource script function.
        It sets the resource to the desired state.
    #>
    [void] Set()
    {
        $fileExists = $this.TestFilePath($this.Path)
        if ($this.ensure -eq [Ensure]::Present)
        {
            if (-not $fileExists)
            {
                $this.CopyFile()
            }
        }
        else
        {
            if ($fileExists)
            {
                Write-Verbose -Message "Deleting the file $($this.Path)"
                Remove-Item -LiteralPath $this.Path -Force
            }
        }
    }

    <#
        This method is equivalent of the Test-TargetResource script function.
        It should return True or False, showing whether the resource
        is in a desired state.
    #>
    [bool] Test()
    {
        $present = $this.TestFilePath($this.Path)

        if ($this.Ensure -eq [Ensure]::Present)
        {
            return $present
        }
        else
        {
            return -not $present
        }
    }

    <#
        This method is equivalent of the Get-TargetResource script function.
        The implementation should use the keys to find appropriate resources.
        This method returns an instance of this class with the updated key
         properties.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)

        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.Ensure = [Ensure]::Absent
        }

        return $this
    }

    <#
        Helper method to check if the file exists and it is file
    #>
    [bool] TestFilePath([string] $location)
    {
        $present = $true

        $item = Get-ChildItem -LiteralPath $location -ea Ignore
        if ($item -eq $null)
        {
            $present = $false
        }
        elseif ($item.PSProvider.Name -ne "FileSystem")
        {
            throw "Path $($location) is not a file path."
        }
        elseif ($item.PSIsContainer)
        {
            throw "Path $($location) is a directory path."
        }

        return $present
    }

    <#
        Helper method to copy file from source to path
    #>
    [void] CopyFile()
    {
        if (-not $this.TestFilePath($this.SourcePath))
        {
            throw "SourcePath $($this.SourcePath) is not found."
        }

        [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
        if (-not $destFileInfo.Directory.Exists)
        {
            Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"

            <#
                Use CreateDirectory instead of New-Item to avoid code
                 to handle the non-terminating error
            #>
            [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
        }

        if (Test-Path -LiteralPath $this.Path -PathType Container)
        {
            throw "Path $($this.Path) is a directory path"
        }

        Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"

        # DSC engine catches and reports any error that occurs
        Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
    }
} # This module defines a class for a DSC "FileResource" provider.
```

## <a name="create-a-manifest"></a><span data-ttu-id="4f67a-140">Creare un manifesto</span><span class="sxs-lookup"><span data-stu-id="4f67a-140">Create a manifest</span></span>

<span data-ttu-id="4f67a-141">Per rendere disponibile una risorsa basata su classi per il motore DSC, è necessario includere un'istruzione **DscResourcesToExport** nel file manifesto per indicare al modulo di esportare la risorsa.</span><span class="sxs-lookup"><span data-stu-id="4f67a-141">To make a class-based resource available to the DSC engine, you must include a **DscResourcesToExport** statement in the manifest file that instructs the module to export the resource.</span></span> <span data-ttu-id="4f67a-142">Il manifesto è simile al seguente:</span><span class="sxs-lookup"><span data-stu-id="4f67a-142">Our manifest looks like this:</span></span>

```powershell
@{

# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

DscResourcesToExport = 'FileResource'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to uniquely identify this module
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'Microsoft Corporation'

# Company or vendor of this module
CompanyName = 'Microsoft Corporation'

# Copyright statement for this module
Copyright = '(c) 2014 Microsoft. All rights reserved.'

# Description of the functionality provided by this module
# Description = ''

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''
}
```

## <a name="test-the-resource"></a><span data-ttu-id="4f67a-143">Testare la risorsa</span><span class="sxs-lookup"><span data-stu-id="4f67a-143">Test the resource</span></span>

<span data-ttu-id="4f67a-144">Dopo aver salvato i file di classe e manifesto nella struttura di cartelle come descritto in precedenza, è possibile creare una configurazione che usa la nuova risorsa.</span><span class="sxs-lookup"><span data-stu-id="4f67a-144">After saving the class and manifest files in the folder structure as described earlier, you can create a configuration that uses the new resource.</span></span> <span data-ttu-id="4f67a-145">Per informazioni su come eseguire una configurazione DSC, vedere [Applicazione delle configurazioni](../pull-server/enactingConfigurations.md).</span><span class="sxs-lookup"><span data-stu-id="4f67a-145">For information about how to run a DSC configuration, see [Enacting configurations](../pull-server/enactingConfigurations.md).</span></span> <span data-ttu-id="4f67a-146">La configurazione seguente controlla se il file in `c:\test\test.txt` esiste e, in caso contrario, copia il file da `c:\test.txt` (è necessario creare `c:\test.txt` prima di eseguire la configurazione).</span><span class="sxs-lookup"><span data-stu-id="4f67a-146">The following configuration will check to see whether the file at `c:\test\test.txt` exists, and, if not, copies the file from `c:\test.txt` (you should create `c:\test.txt` before you run the configuration).</span></span>

```powershell
Configuration Test
{
    Import-DSCResource -module MyDscResource
    FileResource file
    {
        Path = "C:\test\test.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}
Test
Start-DscConfiguration -Wait -Force Test
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="4f67a-147">Supporto di PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="4f67a-147">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="4f67a-148">**Nota:** **PsDscRunAsCredential** è supportato in PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="4f67a-148">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="4f67a-149">La proprietà **PsDscRunAsCredential** può essere usata nel blocco di risorsa delle [configurazioni DSC](../configurations/configurations.md) per specificare che la risorsa deve essere eseguita in un insieme di credenziali specificato.</span><span class="sxs-lookup"><span data-stu-id="4f67a-149">The **PsDscRunAsCredential** property can be used in [DSC configurations](../configurations/configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="4f67a-150">Per altre informazioni, vedere [Esecuzione di DSC con le credenziali dell'utente](../configurations/runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="4f67a-150">For more information, see [Running DSC with user credentials](../configurations/runAsUser.md).</span></span>

### <a name="require-or-disallow-psdscrunascredential-for-your-resource"></a><span data-ttu-id="4f67a-151">Richiedere o non consentire PsDscRunAsCredential per la risorsa</span><span class="sxs-lookup"><span data-stu-id="4f67a-151">Require or disallow PsDscRunAsCredential for your resource</span></span>

<span data-ttu-id="4f67a-152">L'attributo **DscResource()** accetta un parametro facoltativo **RunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-152">The **DscResource()** attribute takes an optional parameter **RunAsCredential**.</span></span>
<span data-ttu-id="4f67a-153">Questo parametro accetta uno dei tre valori seguenti:</span><span class="sxs-lookup"><span data-stu-id="4f67a-153">This parameter takes one of three values:</span></span>

- <span data-ttu-id="4f67a-154">`Optional` **PsDscRunAsCredential** è facoltativo per le configurazioni che chiamano la risorsa.</span><span class="sxs-lookup"><span data-stu-id="4f67a-154">`Optional` **PsDscRunAsCredential** is optional for configurations that call this resource.</span></span> <span data-ttu-id="4f67a-155">Questo è il valore predefinito.</span><span class="sxs-lookup"><span data-stu-id="4f67a-155">This is the default value.</span></span>
- <span data-ttu-id="4f67a-156">`Mandatory` **PsDscRunAsCredential** deve essere usato per le configurazioni che chiamano la risorsa.</span><span class="sxs-lookup"><span data-stu-id="4f67a-156">`Mandatory` **PsDscRunAsCredential** must be used for any configuration that calls this resource.</span></span>
- <span data-ttu-id="4f67a-157">`NotSupported` Le configurazioni che chiamano la risorsa non possono usare **PsDscRunAsCredential**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-157">`NotSupported` Configurations that call this resource cannot use **PsDscRunAsCredential**.</span></span>
- <span data-ttu-id="4f67a-158">`Default` è uguale a `Optional`.</span><span class="sxs-lookup"><span data-stu-id="4f67a-158">`Default` Same as `Optional`.</span></span>

<span data-ttu-id="4f67a-159">Ad esempio, usare l'attributo seguente per specificare che la risorsa personalizzata non supporti l'uso di **PsDscRunAsCredential**:</span><span class="sxs-lookup"><span data-stu-id="4f67a-159">For example, use the following attribute to specify that your custom resource does not support using **PsDscRunAsCredential**:</span></span>

```powershell
[DscResource(RunAsCredential=NotSupported)]
class FileResource {
}
```

### <a name="declaring-multiple-class-resources-in-a-module"></a><span data-ttu-id="4f67a-160">Dichiarazione di più risorse di classe in un modulo</span><span class="sxs-lookup"><span data-stu-id="4f67a-160">Declaring multiple class resources in a module</span></span>

<span data-ttu-id="4f67a-161">Un modulo può definire più risorse DSC basate su classe.</span><span class="sxs-lookup"><span data-stu-id="4f67a-161">A module can define multiple class based DSC resources.</span></span> <span data-ttu-id="4f67a-162">È possibile creare la struttura di cartelle nei modi seguenti:</span><span class="sxs-lookup"><span data-stu-id="4f67a-162">You can create the folder structure in the following ways:</span></span>

1. <span data-ttu-id="4f67a-163">Definire la prima risorsa nel file "<ModuleName>psm1" e le risorse successive nella cartella **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-163">Define the first resource in the "<ModuleName>.psm1" file and subsequent resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- SecondResource.psm1
   ```

2. <span data-ttu-id="4f67a-164">Definire tutte le risorse nella cartella **DSCResources**.</span><span class="sxs-lookup"><span data-stu-id="4f67a-164">Define all resources under the **DSCResources** folder.</span></span>

   ```
   $env:ProgramFiles\WindowsPowerShell\Modules (folder)
        |- MyDscResource (folder)
           |- MyDscResource.psm1
              MyDscResource.psd1
        |- DSCResources
           |- FirstResource.psm1
              SecondResource.psm1
   ```

> [!NOTE]
> <span data-ttu-id="4f67a-165">Negli esempi precedenti, aggiungere eventuali file PSM1 nella cartella **DSCResources** alla chiave **NestedModules** nel file PSD1.</span><span class="sxs-lookup"><span data-stu-id="4f67a-165">In the examples above, add any PSM1 files under the **DSCResources** to the **NestedModules** key in your PSD1 file.</span></span>

### <a name="access-the-user-context"></a><span data-ttu-id="4f67a-166">Accedere al contesto utente</span><span class="sxs-lookup"><span data-stu-id="4f67a-166">Access the user context</span></span>

<span data-ttu-id="4f67a-167">Per accedere al contesto utente dall'interno di una risorsa personalizzata è possibile usare la variabile automatica `$global:PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="4f67a-167">To access the user context from within a custom resource, you can use the automatic variable `$global:PsDscContext`.</span></span>

<span data-ttu-id="4f67a-168">Ad esempio il codice seguente scrive il contesto utente in cui viene eseguita la risorsa nel flusso di output dettagliato:</span><span class="sxs-lookup"><span data-stu-id="4f67a-168">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if (PsDscContext.RunAsUser) {
    Write-Verbose "User: $global:PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="4f67a-169">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="4f67a-169">See Also</span></span>

[<span data-ttu-id="4f67a-170">Creare risorse Windows PowerShell DSC (Desired State Configuration) personalizzate</span><span class="sxs-lookup"><span data-stu-id="4f67a-170">Build Custom Windows PowerShell Desired State Configuration Resources</span></span>](authoringResource.md)
