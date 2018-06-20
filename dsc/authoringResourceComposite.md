---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Risorse composite--Uso di una configurazione DSC come risorsa
ms.openlocfilehash: 246cab3b437546490d650e45be263a43fd0c84c3
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189364"
---
# <a name="composite-resources-using-a-dsc-configuration-as-a-resource"></a><span data-ttu-id="8c9cc-103">Risorse composite: uso di una configurazione DSC come risorsa</span><span class="sxs-lookup"><span data-stu-id="8c9cc-103">Composite resources: Using a DSC configuration as a resource</span></span>

> <span data-ttu-id="8c9cc-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="8c9cc-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="8c9cc-105">In situazioni reali, le configurazioni possono diventare lunghe e complesse, includere chiamate a molte risorse diverse e richiedere l'impostazione di un elevato numero di proprietà.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-105">In real-world situations, configurations can become long and complex, calling many different resources and setting a vast number of properties.</span></span> <span data-ttu-id="8c9cc-106">Per risolvere questa complessità, è possibile usare una configurazione di Windows PowerShell DSC (Desired State Configuration) come risorsa per altre configurazioni.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-106">To help address this complexity, you can use a Windows PowerShell Desired State Configuration (DSC) configuration as a resource for other configurations.</span></span> <span data-ttu-id="8c9cc-107">In questo caso si parla di risorsa composita.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-107">We call this a composite resource.</span></span> <span data-ttu-id="8c9cc-108">Una risorsa composita è una configurazione DSC che accetta parametri.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-108">A composite resource is a DSC configuration that takes parameters.</span></span> <span data-ttu-id="8c9cc-109">I parametri della configurazione fungono da proprietà della risorsa.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-109">The parameters of the configuration act as the properties of the resource.</span></span> <span data-ttu-id="8c9cc-110">La configurazione viene salvata come file con un'estensione **.schema.psm1** e sostituisce sia lo schema MOF sia lo script di risorsa in una risorsa DSC tipica. Per altre informazioni sulle risorse DSC, vedere [Risorse Windows PowerShell DSC (Desired State Configuration)](resources.md).</span><span class="sxs-lookup"><span data-stu-id="8c9cc-110">The configuration is saved as a file with a **.schema.psm1** extension, and takes the place of both the MOF schema and the resource script in a typical DSC resource (for more information about DSC resources, see [Windows PowerShell Desired State Configuration Resources](resources.md).</span></span>

## <a name="creating-the-composite-resource"></a><span data-ttu-id="8c9cc-111">Creazione della risorsa composita</span><span class="sxs-lookup"><span data-stu-id="8c9cc-111">Creating the composite resource</span></span>

<span data-ttu-id="8c9cc-112">In questo esempio viene creata una configurazione che richiama diverse risorse esistenti per configurare le macchine virtuali.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-112">In our example, we create a configuration that invokes a number of existing resources to configure virtual machines.</span></span> <span data-ttu-id="8c9cc-113">Invece di specificare i valori da impostare in blocchi di configurazione, la configurazione accetta diversi parametri che vengono quindi usati nei blocchi di configurazione.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-113">Instead of specifying the values to be set in configuration blocks, the configuration takes a number of parameters that are then used in the configuration blocks.</span></span>

```powershell
Configuration xVirtualMachine
{
    param
    (
        # Name of VMs
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String[]] $VMName,

        # Name of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchName,

        # Type of Switch to create
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $SwitchType,

        # Source Path for VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDParentPath,

        # Destination path for diff VHD
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VHDPath,

        # Startup Memory for VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMStartupMemory,

        # State of the VM
        [Parameter(Mandatory)]
        [ValidateNotNullOrEmpty()]
        [String] $VMState
    )

    # Import the module that defines custom resources
    Import-DscResource -Module xComputerManagement,xHyper-V

    # Install the Hyper-V role
    WindowsFeature HyperV
    {
        Ensure = "Present"
        Name = "Hyper-V"
    }

    # Create the virtual switch
    xVMSwitch $SwitchName
    {
        Ensure = "Present"
        Name = $SwitchName
        Type = $SwitchType
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check for Parent VHD file
    File ParentVHDFile
    {
        Ensure = "Present"
        DestinationPath = $VHDParentPath
        Type = "File"
        DependsOn = "[WindowsFeature]HyperV"
    }

    # Check the destination VHD folder
    File VHDFolder
    {
        Ensure = "Present"
        DestinationPath = $VHDPath
        Type = "Directory"
        DependsOn = "[File]ParentVHDFile"
    }

    # Create VM specific diff VHD
    foreach ($Name in $VMName)
    {
        xVHD "VHD$Name"
        {
            Ensure = "Present"
            Name = $Name
            Path = $VHDPath
            ParentPath = $VHDParentPath
            DependsOn = @("[WindowsFeature]HyperV",
                          "[File]VHDFolder")
        }
    }

    # Create VM using the above VHD
    foreach($Name in $VMName)
    {
        xVMHyperV "VMachine$Name"
        {
            Ensure = "Present"
            Name = $Name
            VhDPath = (Join-Path -Path $VHDPath -ChildPath $Name)
            SwitchName = $SwitchName
            StartupMemory = $VMStartupMemory
            State = $VMState
            MACAddress = $MACAddress
            WaitForIP = $true
            DependsOn = @("[WindowsFeature]HyperV",
                          "[xVHD]VHD$Name")
        }
    }
}
```

### <a name="saving-the-configuration-as-a-composite-resource"></a><span data-ttu-id="8c9cc-114">Salvataggio della configurazione come risorsa composita</span><span class="sxs-lookup"><span data-stu-id="8c9cc-114">Saving the configuration as a composite resource</span></span>

<span data-ttu-id="8c9cc-115">Per usare la configurazione con parametri come risorsa DSC, salvarla in una struttura di directory come quella di qualsiasi altra risorsa basata su MOF e denominarla usando un'estensione **.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-115">To use the parameterized configuration as a DSC resource, save it in a directory structure like that of any other MOF-based resource, and name it with a **.schema.psm1** extension.</span></span> <span data-ttu-id="8c9cc-116">Per questo esempio, il file sarà denominato **xVirtualMachine.schema.psm1**.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-116">For this example, we’ll name the file **xVirtualMachine.schema.psm1**.</span></span> <span data-ttu-id="8c9cc-117">È anche necessario creare un manifesto denominato **xVirtualMachine.psd1** che contiene la riga seguente.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-117">You also need to create a manifest named **xVirtualMachine.psd1** that contains the following line.</span></span> <span data-ttu-id="8c9cc-118">Si noti che questo si aggiunge a **MyDscResources.psd1**, il manifesto del modulo per tutte le risorse nella cartella **MyDscResources**.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-118">Note that this is in addition to **MyDscResources.psd1**, the module manifest for all resources under the **MyDscResources** folder.</span></span>

```powershell
RootModule = 'xVirtualMachine.schema.psm1'
```

<span data-ttu-id="8c9cc-119">Al termine, la struttura di cartelle deve essere simile a quella illustrata di seguito.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-119">When you are done, the folder structure should be as follows.</span></span>

```
$env: psmodulepath
    |- MyDscResources
           MyDscResources.psd1
        |- DSCResources
            |- xVirtualMachine
                |- xVirtualMachine.psd1
                |- xVirtualMachine.schema.psm1
```

<span data-ttu-id="8c9cc-120">La risorsa è ora individuabile usando il cmdlet Get-DscResource e le sue proprietà sono individuabili usando tale cmdlet oppure il completamento automatico con **CTRL+BARRA SPAZIATRICE** in Windows PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-120">The resource is now discoverable by using the Get-DscResource cmdlet, and its properties are discoverable by either that cmdlet or by using **Ctrl+Space** auto-complete in the Windows PowerShell ISE.</span></span>

## <a name="using-the-composite-resource"></a><span data-ttu-id="8c9cc-121">Uso della risorsa composita</span><span class="sxs-lookup"><span data-stu-id="8c9cc-121">Using the composite resource</span></span>

<span data-ttu-id="8c9cc-122">Verrà quindi creata una configurazione che chiama la risorsa composita.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-122">Next we create a configuration that calls the composite resource.</span></span> <span data-ttu-id="8c9cc-123">Questa configurazione chiama la risorsa composita xVirtualMachine per creare una macchina virtuale e quindi chiama la risorsa **xComputer** per rinominarla.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-123">This configuration calls the xVirtualMachine composite resource to create a virtual machine, and then calls the **xComputer** resource to rename it.</span></span>

```powershell

configuration RenameVM
{

    Import-DscResource -Module xVirtualMachine
    Node localhost
    {
        xVirtualMachine VM
        {
            VMName = "Test"
            SwitchName = "Internal"
            SwitchType = "Internal"
            VhdParentPath = "C:\Demo\VHD\RTM.vhd"
            VHDPath = "C:\Demo\VHD"
            VMStartupMemory = 1024MB
            VMState = "Running"
        }
    }

    Node "192.168.10.1"
    {
        xComputer Name
        {
            Name = "SQL01"
            DomainName = "fourthcoffee.com"
        }
    }
}
```

## <a name="supporting-psdscrunascredential"></a><span data-ttu-id="8c9cc-124">Supporto di PsDscRunAsCredential</span><span class="sxs-lookup"><span data-stu-id="8c9cc-124">Supporting PsDscRunAsCredential</span></span>

><span data-ttu-id="8c9cc-125">**Nota:** **PsDscRunAsCredential** è supportato in PowerShell 5.0 e versioni successive.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-125">**Note:** **PsDscRunAsCredential** is supported in PowerShell 5.0 and later.</span></span>

<span data-ttu-id="8c9cc-126">La proprietà **PsDscRunAsCredential** può essere usata nel blocco di risorsa delle [configurazioni DSC](configurations.md) per specificare che la risorsa deve essere eseguita in un insieme di credenziali specificato.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-126">The **PsDscRunAsCredential** property can be used in [DSC configurations](configurations.md) resource block to specify that the resource should be run under a specified set of credentials.</span></span>
<span data-ttu-id="8c9cc-127">Per altre informazioni, vedere [Esecuzione di DSC con le credenziali dell'utente](runAsUser.md).</span><span class="sxs-lookup"><span data-stu-id="8c9cc-127">For more information, see [Running DSC with user credentials](runAsUser.md).</span></span>

<span data-ttu-id="8c9cc-128">Per accedere al contesto utente dall'interno di una risorsa personalizzata è possibile usare la variabile automatica `$PsDscContext`.</span><span class="sxs-lookup"><span data-stu-id="8c9cc-128">To access the user context from within a custom resource, you can use the automatic variable `$PsDscContext`.</span></span>

<span data-ttu-id="8c9cc-129">Ad esempio il codice seguente scrive il contesto utente in cui viene eseguita la risorsa nel flusso di output dettagliato:</span><span class="sxs-lookup"><span data-stu-id="8c9cc-129">For example the following code would write the user context under which the resource is running to the verbose output stream:</span></span>

```powershell
if ($PsDscContext.RunAsUser) {
    Write-Verbose "User: $PsDscContext.RunAsUser";
}
```

## <a name="see-also"></a><span data-ttu-id="8c9cc-130">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8c9cc-130">See Also</span></span>
### <a name="concepts"></a><span data-ttu-id="8c9cc-131">Concetti</span><span class="sxs-lookup"><span data-stu-id="8c9cc-131">Concepts</span></span>
* [<span data-ttu-id="8c9cc-132">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="8c9cc-132">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
* [<span data-ttu-id="8c9cc-133">Introduzione a Windows PowerShell DSC (Desired State Configuration)</span><span class="sxs-lookup"><span data-stu-id="8c9cc-133">Get Started with Windows PowerShell Desired State Configuration</span></span>](overview.md)