# Creazione di una risorsa DSC in C`#`

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

In genere, una risorsa personalizzata di Windows PowerShell DSC (Desired State Configuration) viene implementata in uno script di PowerShell. È tuttavia anche possibile implementare la funzionalità di una risorsa DSC personalizzata scrivendo cmdlet in C#. Per informazioni introduttive sulla scrittura di cmdlet in C#, vedere [Scrittura di un cmdlet di Windows PowerShell](https://technet.microsoft.com/en-us/library/dd878294.aspx).

A parte l'implementazione della risorsa in C# come cmdlet, i processi di creazione dello schema MOF, creazione della struttura di cartelle, importazione e uso della risorsa DSC personalizzata sono uguali a quelli descritti in [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md).

## Scrittura di una risorsa basata su cmdlet
Per questo esempio verrà implementata una risorsa semplice che gestisce un file di testo e il relativo contenuto.

### Scrittura dello schema MOF

Di seguito è illustrata la definizione di risorsa MOF.

```
[ClassVersion("1.0.0"), FriendlyName("xDemoFile")]
class MSFT_XDemoFile : OMI_BaseResource
{
                [Key, Description("path")] String Path;
                [Write, Description("Should the file be present"), ValueMap{"Present","Absent"}, Values{"Present","Absent"}] String Ensure;
                [Write, Description("Contentof file.")] String Content;                   
};
```

### Impostazione del progetto di Visual Studio
#### Impostazione di un progetto di cmdlet

1. Aprire Visual Studio.
1. Creare un progetto C# e specificare il nome.
1. Selezionare **Libreria di classi** dai modelli di progetto disponibili.
1. Fare clic su **OK**.
1. Aggiungere un riferimento all'assembly System.Automation.Management.dll al progetto.
1. Modificare il nome dell'assembly in modo che corrisponda al nome della risorsa. In questo caso, il nome dell'assembly deve essere **MSFT_XDemoFile**.

### Scrittura del codice del cmdlet

Il codice C# seguente implementa i cmdlet **Get-TargetResource**, **Set-TargetResource** e **Test-TargetResource**.

```C#
Get-TargetResource
       [OutputType(typeof(System.Collections.Hashtable))]
       [Cmdlet(VerbsCommon.Get, "TargetResource")]
       public class GetTargetResource : PSCmdlet
       {
              [Parameter(Mandatory = true)]
              public string Path { get; set; }
 
///<summary>
/// Implement the logic to write the current state of the resource as a 
/// Hash table with keys being the resource properties 
/// and the Values are the corresponding current values on the target machine.
 
///</summary>
              protected override void ProcessRecord()
              {
// Download the zip file at the end of this blog to see sample implementation.
 }
 
Set-TargetResouce
         [OutputType(typeof(void))]
    [Cmdlet(VerbsCommon.Set, "TargetResource")]
    public class SetTargetResource : PSCmdlet
    {
        privatestring _ensure;
        privatestring _content;
        
[Parameter(Mandatory = true)]
        public string Path { get; set; }
        
[Parameter(Mandatory = false)]      
       [ValidateSet("Present", "Absent", IgnoreCase = true)]
       public string Ensure {
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
            public string Content {
            get { return (string.IsNullOrEmpty(this._content) ? "" : this._content); }
            set { this._content = value; }
        }
 
///<summary>
        /// Implement the logic to set the state of the machine to the desired state.
        ///</summary>
        protected override void ProcessRecord()
        {
//Implement the set method of the resource 
/* Uncomment this section if your resource needs a machine reboot.
PSVariable DscMachineStatus = new PSVariable("DSCMachineStatus", 1, ScopedItemOptions.AllScope);
                this.SessionState.PSVariable.Set(DscMachineStatus);
*/     
  }
    }
Test-TargetResource    
       [Cmdlet("Test", "TargetResource")]
    [OutputType(typeof(Boolean))]
    public class TestTargetResource : PSCmdlet
    {   
        
        private string _ensure;
        private string _content;
 
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
            get { return (string.IsNullOrEmpty(this._content) ? "“:this._content);}
            set { this._content = value; }
        }
 
///<summary>
/// Write a Boolean value which indicates whether the current machine is in    
/// desired state or not.
        ///</summary>
        protected override void ProcessRecord()
        {
                // Implement the test method of the resource.
        }
}
```

### Distribuzione della risorsa

Il file DLL compilato deve essere salvato in una struttura di file simile a una risorsa basata su script. Di seguito è illustrata la struttura di cartelle per questa risorsa.

```
$env: psmodulepath (folder)
    |- MyDscResources (folder)
        |- DSCResources (folder)
            |- MSFT_XDemoFile (folder)
                |- MSFT_XDemoFile.psd1 (file, optional)
                |- MSFT_XDemoFile.dll (file, required)
                |- MSFT_XDemoFile.schema.mof (file, required)
```

### Vedere anche
#### Concetti
[Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md)
#### Risorse aggiuntive
[Scrittura di un cmdlet di Windows PowerShell](https://msdn.microsoft.com/en-us/library/dd878294.aspx)<!--HONumber=Feb16_HO4-->
