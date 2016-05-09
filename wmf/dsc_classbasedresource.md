# Risorse DSC basate su classi

## Definizione delle risorse DSC con le classi

In base ai commenti e ai suggerimenti ricevuti, la creazione di risorse DSC basate su classi è stata semplificata ed è di più facile comprensione. 
Le principali differenze tra una risorsa DSC basata su classe e un provider di risorse DSC basato su cmdlet sono:

* Non è necessario un file MOF per lo schema.
* Non è necessaria una sottocartella **DSCResource** nella cartella del modulo.
* Un file di modulo di PowerShell può contenere più classi di risorse DSC.

Di seguito è riportato un esempio di una risorsa DSC basata su classe che estende l'altra risorsa DSC classe nello stesso file. Viene salvata come modulo, **MyDSCResource.psm1**.. 
Si noti che è necessario includere sempre almeno una proprietà Key e un metodo Get, Set, Test in una risorsa DSC basata su classe o nelle relative classi di base.

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
class BaseFileResource
{
<#
This property is the fully qualified path to the file that is expected to be present or absent.

The [DscProperty(Key)] attribute indicates the property is a key and its value uniquely identifies a resource instance. Defining this attribute also means the property is required and DSC will ensure a value is set before calling the resource.

A DSC resource must define at least one key property.
#>

[DscProperty(Key)]
[string]$Path

<#
This property indicates if the settings should be present or absent on the system.

For present, the resource ensures the file pointed to by $Path exists. For absent, it ensures the file that $Path points to does not exist.

The [DscProperty(Mandatory)] attribute indicates the property is required and DSC will guarantee it is set.

If Mandatory is not specified or if it is defined as Mandatory=$false, the value is not guaranteed to be set when DSC calls the resource. This is appropriate for optional properties.
#>

[DscProperty(Mandatory)]
[Ensure] $Ensure

<#
This property defines the fully qualified path to a file that will be placed on the system if $Ensure = Present and $Path does not exist.
NOTE: This property is required because [DscProperty(Mandatory)] is set.
#>

[DscProperty(Mandatory)]
[string] $SourcePath

<#
This property reports the file creation timestamp.

[DscProperty(NotConfigurable)] attribute indicates the property is not configurable in a DSC configuration. Properties marked this way are populated by the Get() method to report additional details about the resource when it is present.
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
    if($this.ensure -eq [Ensure]::Present)
    {
        if(-not $fileExists)
        {
            $this.CopyFile()
        }
    }

    else
    {
        if($fileExists)
        {
            Write-Verbose -Message "Deleting the file $($this.Path)"
            Remove-Item -LiteralPath $this.Path -Force
        }
    }
}

<#
This method is equivalent of the Test-TargetResource script function.
It should return True or False, showing whether the resource is in a desired state.
#>

[bool] Test()
{
    $present = $this.TestFilePath($this.Path)

    if($this.Ensure -eq [Ensure]::Present)
    {
        return $present
    }

    else
    {
        return -not $present
    }
}

<#
This method is equal to the Get-TargetResource script function.
The implementation should use the keys to find appropriate resources.
This method returns an instance of this class with the updated key properties.
#>

[BaseFileResource] Get()
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
Helper method to check if the file exists and it is the right file
#>

[bool] TestFilePath([string] $location)
{
    $present = $true
    $item = Get-ChildItem -LiteralPath $location -ea Ignore
    
    if ($item -eq $null)
    {
        $present = $false
    }
    elseif($item.PSProvider.Name -ne "FileSystem")
    {
        throw "Path $($location) is not a file path."
    }
    elseif($item.PSIsContainer)
    {
        throw "Path $($location) is a directory path."
    }

return $present
}

<#
Helper method to copy the file from source to path
#>

[void] CopyFile()
{
    if(-not $this.TestFilePath($this.SourcePath))
    {
        throw "SourcePath $($this.SourcePath) is not found."
    }

    [System.IO.FileInfo] $destFileInfo = new-object System.IO.FileInfo($this.Path)
    if (-not $destFileInfo.Directory.Exists)
    {
        Write-Verbose -Message "Creating directory $($destFileInfo.Directory.FullName)"
    
        # use CreateDirectory instead of New-Item to avoid code
        # to handle the non-terminating error
        [System.IO.Directory]::CreateDirectory($destFileInfo.Directory.FullName)
    }

    if(Test-Path -LiteralPath $this.Path -PathType Container)
    {
        throw "Path $($this.Path) is a directory path"
    }

    Write-Verbose -Message "Copying $($this.SourcePath) to $($this.Path)"
    # DSC engine catches and reports any error that occurs
    Copy-Item -LiteralPath $this.SourcePath -Destination $this.Path -Force
}
}

<#
This resource inherits from the [BaseFileResource]
It reports additional information in Get method
#>

[DscResource()]
class FileResource : BaseFileResource
{
    <#
    This property reports if it is a readonly file
    #>
    [DscProperty(NotConfigurable)]
    [bool] $IsReadOnly

    <#
    This property reports the file LastAccessTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastAccessTime

    <#
    This property reports the file LastWriteTime timestamp.
    #>
    [DscProperty(NotConfigurable)]
    [Nullable[datetime]] $LastWriteTime

    <#
    This method overrides the Get method in the base class.
    #>
    [FileResource] Get()
    {
        $present = $this.TestFilePath($this.Path)
        if ($present)
        {
            $file = Get-ChildItem -LiteralPath $this.Path
            $this.CreationTime = $file.CreationTime
            $this.IsReadOnly = $file.IsReadOnly
            $this.LastAccessTime = $file.LastAccessTime
            $this.LastWriteTime = $file.LastWriteTime
            $this.Ensure = [Ensure]::Present
        }
        else
        {
            $this.CreationTime = $null
            $this.LastAccessTime = $null
            $this.LastWriteTime = $null
            $this.Ensure = [Ensure]::Absent
        }

    return $this
}

}
```

Dopo aver creato il provider di risorse DSC basato su classe e averlo salvato come modulo, creare un manifesto del modulo per il modulo. Il manifesto del modulo nell'esempio seguente viene salvato come **MyDscResource.psd1**.

```powershell
@{
# Script module or binary module file associated with this manifest.
RootModule = 'MyDscResource.psm1'

# Version number of this module.
ModuleVersion = '1.0'

# ID used to identify this module uniquely
GUID = '81624038-5e71-40f8-8905-b1a87afe22d7'

# Author of this module
Author = 'User01'

# Company or vendor of this module
CompanyName = 'Unknown'

# Copyright statement for this module
Copyright = '(c) 2015 User01. All rights reserved.'

# Description of the functionality provided by this module
Description = 'DSC resource provider for FileResource.'

# Minimum version of the Windows PowerShell engine required by this module
PowerShellVersion = '5.0'

# Name of the Windows PowerShell host required by this module
# PowerShellHostName = ''

# Required for DSC to detect PS class-based resources.
DscResourcesToExport = @('BaseFileResource','FileResource')
}
```

Distribuire il nuovo provider di risorse DSC creando una cartella **MyDscResource** in `$env:SystemDrive\Program Files\WindowsPowerShell\Modules`.
Non è necessario creare una sottocartella DSCResource.
Copiare i file del modulo e del manifesto del modulo (**MyDscResource.psm1** e **MyDscResource.psd1**) nella cartella **MyDscResource**.

A questo punto, creare ed eseguire uno script di configurazione come si farebbe con qualsiasi risorsa DSC. 
Quella che segue è una configurazione che fa riferimento al modulo MyDSCResource. 
Salvarla come script con il nome **MyResource.ps1**.

```powershell
Configuration MyConfig
{
    Import-Dscresource -ModuleName MyDscResource
    BaseFileResource file
    {
        Path = "C:\test\baseFile.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }

    FileResource file
    {
        Path = "C:\test\File.txt"
        SourcePath = "c:\test.txt"
        Ensure = "Present"
    }
}

MyConfig
```

Eseguire questo script, come per qualsiasi script di configurazione DSC. Per avviare la configurazione, in una console di Windows PowerShell con privilegi elevati eseguire il cmdlet seguente. 
Si noterà che l'output di Get-DscConfiguration da FileResource contiene più informazioni rispetto a BaseFileResource.

```powershell
.\MyResource.ps1
Start-DscConfiguration c:\test\MyConfig –Wait –Verbose
Get-DscConfiguration
```

## Problemi noti

In questa versione, sono presenti i seguenti problemi noti per le risorse DSC basate su classi:

* Get-DscConfiguration può restituire valori vuoti (null) o errori se viene restituito un tipo complesso dalla funzione Get() di una risorsa DSC basata su classe.
* Le risorse composite non possono essere scritte come risorsa basata su classe.


<!--HONumber=Apr16_HO5-->


