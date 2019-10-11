---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Creazione di una risorsa DSC in C#
ms.openlocfilehash: 6f2bb4d411237f13e2735c2e5f630b4f40dc6842
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/04/2019
ms.locfileid: "71954318"
---
# <a name="authoring-a-dsc-resource-in-c"></a><span data-ttu-id="49f9d-103">Creazione di una risorsa DSC in C\#</span><span class="sxs-lookup"><span data-stu-id="49f9d-103">Authoring a DSC resource in C\#</span></span>

> <span data-ttu-id="49f9d-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="49f9d-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="49f9d-105">In genere, una risorsa personalizzata di Windows PowerShell DSC (Desired State Configuration) viene implementata in uno script di PowerShell.</span><span class="sxs-lookup"><span data-stu-id="49f9d-105">Typically, a Windows PowerShell Desired State Configuration (DSC) custom resource is implemented in a PowerShell script.</span></span> <span data-ttu-id="49f9d-106">È tuttavia anche possibile implementare la funzionalità di una risorsa DSC personalizzata scrivendo cmdlet in C#.</span><span class="sxs-lookup"><span data-stu-id="49f9d-106">However, you can also implement the functionality of a DSC custom resource by writing cmdlets in C#.</span></span> <span data-ttu-id="49f9d-107">Per informazioni introduttive sulla scrittura di cmdlet in C#, vedere [Scrittura di un cmdlet di Windows PowerShell](/powershell/developer/windows-powershell).</span><span class="sxs-lookup"><span data-stu-id="49f9d-107">For an introduction on writing cmdlets in C#, see [Writing a Windows PowerShell Cmdlet](/powershell/developer/windows-powershell).</span></span>

<span data-ttu-id="49f9d-108">A parte l'implementazione della risorsa in C# come cmdlet, i processi di creazione dello schema MOF, creazione della struttura di cartelle, importazione e uso della risorsa DSC personalizzata sono uguali a quelli descritti in [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md).</span><span class="sxs-lookup"><span data-stu-id="49f9d-108">Aside from implementing the resource in C# as cmdlets, the process of creating the MOF schema, creating the folder structure, importing and using your custom DSC resource are the same as described in [Writing a custom DSC resource with MOF](authoringResourceMOF.md).</span></span>

## <a name="writing-a-cmdlet-based-resource"></a><span data-ttu-id="49f9d-109">Scrittura di una risorsa basata su cmdlet</span><span class="sxs-lookup"><span data-stu-id="49f9d-109">Writing a cmdlet-based resource</span></span>
<span data-ttu-id="49f9d-110">Per questo esempio verrà implementata una risorsa semplice che gestisce un file di testo e il relativo contenuto.</span><span class="sxs-lookup"><span data-stu-id="49f9d-110">For this example, we will implement a simple resource that manages a text file and its contents.</span></span>

### <a name="writing-the-mof-schema"></a><span data-ttu-id="49f9d-111">Scrittura dello schema MOF</span><span class="sxs-lookup"><span data-stu-id="49f9d-111">Writing the MOF schema</span></span>

<span data-ttu-id="49f9d-112">Di seguito è illustrata la definizione di risorsa MOF.</span><span class="sxs-lookup"><span data-stu-id="49f9d-112">The following is the MOF resource definition.</span></span>

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;
};
```

### <a name="setting-up-the-visual-studio-project"></a><span data-ttu-id="49f9d-113">Impostazione del progetto di Visual Studio</span><span class="sxs-lookup"><span data-stu-id="49f9d-113">Setting up the Visual Studio project</span></span>
#### <a name="setting-up-a-cmdlet-project"></a><span data-ttu-id="49f9d-114">Impostazione di un progetto di cmdlet</span><span class="sxs-lookup"><span data-stu-id="49f9d-114">Setting up a cmdlet project</span></span>

1. <span data-ttu-id="49f9d-115">Aprire Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="49f9d-115">Open Visual Studio.</span></span>
1. <span data-ttu-id="49f9d-116">Creare un progetto C# e specificare il nome.</span><span class="sxs-lookup"><span data-stu-id="49f9d-116">Create a C# project and provide the name.</span></span>
1. <span data-ttu-id="49f9d-117">Selezionare **Libreria di classi** dai modelli di progetto disponibili.</span><span class="sxs-lookup"><span data-stu-id="49f9d-117">Select **Class Library** from the available project templates.</span></span>
1. <span data-ttu-id="49f9d-118">Fare clic su **OK**.</span><span class="sxs-lookup"><span data-stu-id="49f9d-118">Click **Ok**.</span></span>
1. <span data-ttu-id="49f9d-119">Aggiungere un riferimento all'assembly System.Automation.Management.dll al progetto.</span><span class="sxs-lookup"><span data-stu-id="49f9d-119">Add an assembly reference to System.Automation.Management.dll to your project.</span></span>
1. <span data-ttu-id="49f9d-120">Modificare il nome dell'assembly in modo che corrisponda al nome della risorsa.</span><span class="sxs-lookup"><span data-stu-id="49f9d-120">Change the assembly name to match the resource name.</span></span> <span data-ttu-id="49f9d-121">In questo caso, il nome dell'assembly deve essere **MSFT_XDemoFile**.</span><span class="sxs-lookup"><span data-stu-id="49f9d-121">In this case, the assembly should be named **MSFT_XDemoFile**.</span></span>

### <a name="writing-the-cmdlet-code"></a><span data-ttu-id="49f9d-122">Scrittura del codice del cmdlet</span><span class="sxs-lookup"><span data-stu-id="49f9d-122">Writing the cmdlet code</span></span>

<span data-ttu-id="49f9d-123">Il codice C# seguente implementa i cmdlet **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**.</span><span class="sxs-lookup"><span data-stu-id="49f9d-123">The following C# code implements the **Get-TargetResource**, **Set-TargetResource**, and **Test-TargetResource** cmdlets.</span></span>

```C#


namespace cSharpDSCResourceExample
{
    using System;
    using System.Collections.Generic;
    using System.IO;
    using System.Management.Automation;  // Windows PowerShell assembly.

    #region Get-TargetResource

    [OutputType(typeof(System.Collections.Hashtable))]
    [Cmdlet(VerbsCommon.Get, "TargetResource")]
    public class GetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        /// <summary>
        /// Implement the logic to return the current state of the resource as a hashtable with keys being the resource properties
        /// and the values are the corresponding current value on the machine.
        /// </summary>
        protected override void ProcessRecord()
        {
            var currentResourceState = new Dictionary<string, string>();
            if (File.Exists(Path))
            {
                currentResourceState.Add("Ensure", "Present");

                // read current content
                string CurrentContent = "";
                using (var reader = new StreamReader(Path))
                {
                    CurrentContent = reader.ReadToEnd();
                }
                currentResourceState.Add("Content", CurrentContent);
            }
            else
            {
                currentResourceState.Add("Ensure", "Absent");
                currentResourceState.Add("Content", "");
            }
            // write the hashtable in the PS console.
            WriteObject(currentResourceState);
        }
    }

    # endregion

    #region Set-TargetResource
    [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure {
            get
            {
                // set the default to present.
               return (this._ensure ?? "Present") ;
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Implement the logic to set the state of the machine to the desired state.
        /// </summary>
        protected override void ProcessRecord()
        {
            WriteVerbose(string.Format("Running set with parameters {0}{1}{2}", Path, Ensure, Content));
            if (File.Exists(Path))
            {
                if (Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    File.Delete(Path);
                }
                else
                {
                    // file already exist and ensure "present" is specified. start writing the content to a file
                    if (!string.IsNullOrEmpty(Content))
                    {
                        string existingContent = null;
                        using (var reader = new StreamReader(Path))
                        {
                            existingContent = reader.ReadToEnd();
                        }
                        // check if the content of the file mathes the content passed
                        if (!existingContent.Equals(Content, StringComparison.InvariantCultureIgnoreCase))
                        {
                            WriteVerbose("Existing content did not match with desired content updating the content of the file");
                            using (var writer = new StreamWriter(Path))
                            {
                                writer.Write(Content);
                                writer.Flush();
                            }
                        }
                    }
                }

            }
            else
            {
                if (Ensure.Equals("present", StringComparison.InvariantCultureIgnoreCase))
                {
                    // if nothing is passed for content just write "" otherwise write the content passed.
                    using (var writer = new StreamWriter(Path))
                    {
                        WriteVerbose(string.Format("Creating a file under path {0} with content {1}", Path, Content));
                        writer.Write(Content);
                    }
                }

            }

            /* if you need to reboot the VM. please add the following two line of code.
            PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
            this.SessionState.PSVariable.Set(DscMachineStatus);
             */

        }

    }

    # endregion

    #region Test-TargetResource

    [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {
        [Parameter(Mandatory = true)]
        public string Path { get; set; }

        [Parameter(Mandatory = false)]

        [ValidateSet("Present", "Absent", IgnoreCase = true)]
        public string Ensure
        {
            get
            {
                // set the default to present.
                return (this._ensure ?? "Present");
            }
            set
            {
                this._ensure = value;
            }
        }

        [Parameter(Mandatory = false)]
        public string Content
        {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }

        private string _ensure;
        private string _content;

        /// <summary>
        /// Return a boolean value which indicates wheather the current machine is in desired state or not.
        /// </summary>
        protected override void ProcessRecord()
        {
            if (File.Exists(Path))
            {
                if( Ensure.Equals("absent", StringComparison.InvariantCultureIgnoreCase))
                {
                    WriteObject(false);
                }
                else
                {
                    // check if the content matches

                    string existingContent = null;
                    using (var stream = new StreamReader(Path))
                    {
                        existingContent = stream.ReadToEnd();
                    }

                    WriteObject(Content.Equals(existingContent, StringComparison.InvariantCultureIgnoreCase));
                }
            }
            else
            {
                WriteObject(Ensure.Equals("Absent", StringComparison.InvariantCultureIgnoreCase));
            }
        }
    }

    # endregion

}
```

### <a name="deploying-the-resource"></a><span data-ttu-id="49f9d-124">Distribuzione della risorsa</span><span class="sxs-lookup"><span data-stu-id="49f9d-124">Deploying the resource</span></span>

<span data-ttu-id="49f9d-125">Il file DLL compilato deve essere salvato in una struttura di file simile a una risorsa basata su script.</span><span class="sxs-lookup"><span data-stu-id="49f9d-125">The compiled dll file should be saved in a file structure similar to a script-based resource.</span></span> <span data-ttu-id="49f9d-126">Di seguito è illustrata la struttura di cartelle per questa risorsa.</span><span class="sxs-lookup"><span data-stu-id="49f9d-126">The following is the folder structure for this resource.</span></span>

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- MyDscResources.psd1 (file, required)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### <a name="see-also"></a><span data-ttu-id="49f9d-127">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="49f9d-127">See Also</span></span>
#### <a name="concepts"></a><span data-ttu-id="49f9d-128">Concetti</span><span class="sxs-lookup"><span data-stu-id="49f9d-128">Concepts</span></span>
[<span data-ttu-id="49f9d-129">Scrittura di una risorsa DSC personalizzata con MOF</span><span class="sxs-lookup"><span data-stu-id="49f9d-129">Writing a custom DSC resource with MOF</span></span>](authoringResourceMOF.md)
#### <a name="other-resources"></a><span data-ttu-id="49f9d-130">Risorse aggiuntive</span><span class="sxs-lookup"><span data-stu-id="49f9d-130">Other Resources</span></span>
[<span data-ttu-id="49f9d-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="49f9d-131">Writing a Windows PowerShell Cmdlet</span></span>](/powershell/developer/windows-powershell)