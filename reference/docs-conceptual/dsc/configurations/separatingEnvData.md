---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Separazione dei dati di configurazione e dell'ambiente
ms.openlocfilehash: b16243fc9096f786a25ed20868e94a3aa85e403e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71954438"
---
# <a name="separating-configuration-and-environment-data"></a><span data-ttu-id="b76e2-103">Separazione dei dati di configurazione e dell'ambiente</span><span class="sxs-lookup"><span data-stu-id="b76e2-103">Separating configuration and environment data</span></span>

><span data-ttu-id="b76e2-104">Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="b76e2-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="b76e2-105">Può essere utile separare i dati usati in una configurazione DSC dalla configurazione stessa usando i dati di configurazione.</span><span class="sxs-lookup"><span data-stu-id="b76e2-105">It can be useful to separate the data used in a DSC configuration from the configuration itself by using configuration data.</span></span>
<span data-ttu-id="b76e2-106">In questo modo, è possibile usare una singola configurazione per più ambienti.</span><span class="sxs-lookup"><span data-stu-id="b76e2-106">By doing this, you can use a single configuration for multiple environments.</span></span>

<span data-ttu-id="b76e2-107">Ad esempio, se si sviluppa un'applicazione, è possibile usare una sola configurazione per l'ambiente di sviluppo e per quello di produzione e usare i dati di configurazione per specificare i dati per ogni ambiente.</span><span class="sxs-lookup"><span data-stu-id="b76e2-107">For example, if you are developing an application, you can use one configuration for both development and production environments, and use configuration data to specify data for each environment.</span></span>

## <a name="what-is-configuration-data"></a><span data-ttu-id="b76e2-108">Cosa sono i dati di configurazione?</span><span class="sxs-lookup"><span data-stu-id="b76e2-108">What is configuration data?</span></span>

<span data-ttu-id="b76e2-109">I dati di configurazione sono dati definiti in una tabella hash e passati a una configurazione DSC quando si compila la configurazione.</span><span class="sxs-lookup"><span data-stu-id="b76e2-109">Configuration data is data that is defined in a hashtable and passed to a DSC configuration when you compile that configuration.</span></span>

<span data-ttu-id="b76e2-110">Per una descrizione dettagliata della tabella hash **ConfigurationData**, vedere [Uso dei dati di configurazione](configData.md).</span><span class="sxs-lookup"><span data-stu-id="b76e2-110">For a detailed description of the **ConfigurationData** hashtable, see [Using configuration data](configData.md).</span></span>

## <a name="a-simple-example"></a><span data-ttu-id="b76e2-111">Un esempio semplice</span><span class="sxs-lookup"><span data-stu-id="b76e2-111">A simple example</span></span>

<span data-ttu-id="b76e2-112">Di seguito è riportato un esempio molto semplice che illustra il funzionamento.</span><span class="sxs-lookup"><span data-stu-id="b76e2-112">Let's look at a very simple example to see how this works.</span></span>
<span data-ttu-id="b76e2-113">Verrà creata una singola configurazione che assicura che **IIS** sia presente in alcuni nodi e che **Hyper-V** sia presente in altri:</span><span class="sxs-lookup"><span data-stu-id="b76e2-113">We'll create a single configuration that ensures that **IIS** is present on some nodes, and that **Hyper-V** is present on others:</span></span>

```powershell
Configuration MyDscConfiguration {

    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }

    }
    Node $AllNodes.Where{$_.Role -eq "VMHost"}.NodeName
    {
        WindowsFeature HyperVInstall {
            Ensure = 'Present'
            Name   = 'Hyper-V'
        }
    }
}

$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            Role = 'WebServer'
        },

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

<span data-ttu-id="b76e2-114">L'ultima riga in questo script consente di compilare la configurazione, passando `$MyData` come valore del parametro **ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b76e2-114">The last line in this script compiles the configuration, passing `$MyData` as the value **ConfigurationData** parameter.</span></span>

<span data-ttu-id="b76e2-115">Il risultato è che vengono creati due file MOF:</span><span class="sxs-lookup"><span data-stu-id="b76e2-115">The result is that two MOF files are created:</span></span>

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

<span data-ttu-id="b76e2-116">`$MyData` specifica due nodi diversi, ognuno con i propri `NodeName` e `Role`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-116">`$MyData` specifies two different nodes, each with its own `NodeName` and `Role`.</span></span> <span data-ttu-id="b76e2-117">La configurazione crea in modo dinamico i blocchi **Node** eseguendo la raccolta dei nodi che riceve da `$MyData` (in particolare, `$AllNodes`) e filtra tale raccolta usando la proprietà `Role`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-117">The configuration dynamically creates **Node** blocks by taking the collection of nodes it gets from `$MyData` (specifically, `$AllNodes`) and filters that collection against the `Role` property..</span></span>

## <a name="using-configuration-data-to-define-development-and-production-environments"></a><span data-ttu-id="b76e2-118">Uso dei dati di configurazione per definire gli ambienti di sviluppo e produzione</span><span class="sxs-lookup"><span data-stu-id="b76e2-118">Using configuration data to define development and production environments</span></span>

<span data-ttu-id="b76e2-119">Di seguito è riportato un esempio completo che usa una singola configurazione per impostare sia l'ambiente di sviluppo che quello di produzione di un sito Web.</span><span class="sxs-lookup"><span data-stu-id="b76e2-119">Let's look at a complete example that uses a single configuration to set up both development and production environments of a website.</span></span> <span data-ttu-id="b76e2-120">Nell'ambiente di sviluppo IIS e SQL Server vengono installati in un singolo nodo.</span><span class="sxs-lookup"><span data-stu-id="b76e2-120">In the development environment, both IIS and SQL Server are installed on a single nodes.</span></span> <span data-ttu-id="b76e2-121">Nell'ambiente di produzione IIS e SQL Server vengono installati in nodi separati.</span><span class="sxs-lookup"><span data-stu-id="b76e2-121">In the production environment, IIS and SQL Server are installed on separate nodes.</span></span> <span data-ttu-id="b76e2-122">Nell'esempio verrà usato un file di dati di configurazione con estensione psd1 per specificare i dati per i due diversi ambienti.</span><span class="sxs-lookup"><span data-stu-id="b76e2-122">We'll use a configuration data .psd1 file to specify the data for the two different environments.</span></span>

### <a name="configuration-data-file"></a><span data-ttu-id="b76e2-123">File di dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="b76e2-123">Configuration data file</span></span>

<span data-ttu-id="b76e2-124">I dati degli ambienti di sviluppo e produzione verranno definiti in un file denominato `DevProdEnvData.psd1` come indicato di seguito:</span><span class="sxs-lookup"><span data-stu-id="b76e2-124">We'll define the development and production environment data in a file named `DevProdEnvData.psd1` as follows:</span></span>

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
        WebSiteName     = "New website"
        },

        @{
            NodeName        = "Prod-SQL"
            Role            = "MSSQL"
        },

        @{
            NodeName        = "Prod-IIS"
            Role            = "Web"
            SiteContents    = "C:\Website\Prod\SiteContents\"
            SitePath        = "\\Prod-IIS\Website\"
        },

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"
        }
    )
}
```

### <a name="configuration-script-file"></a><span data-ttu-id="b76e2-125">File di script di configurazione</span><span class="sxs-lookup"><span data-stu-id="b76e2-125">Configuration script file</span></span>

<span data-ttu-id="b76e2-126">Nella configurazione, definita in un file `.ps1`, i nodi definiti in `DevProdEnvData.psd1` vengono ora filtrati in base al ruolo (`MSSQL`, `Dev` o entrambi) e configurati di conseguenza.</span><span class="sxs-lookup"><span data-stu-id="b76e2-126">Now, in the configuration, which is defined in a `.ps1` file, we filter the nodes we defined in `DevProdEnvData.psd1` by their role (`MSSQL`, `Dev`, or both), and configure them accordingly.</span></span>
<span data-ttu-id="b76e2-127">L'ambiente di sviluppo ha sia SQL Server sia IIS in un nodo, mentre per l'ambiente di produzione si trovano in nodi diversi.</span><span class="sxs-lookup"><span data-stu-id="b76e2-127">The development environment has both the SQL Server and IIS on one node, while the production environment has them on two different nodes.</span></span>
<span data-ttu-id="b76e2-128">Anche il contenuto del sito è diverso, come specificato dalle proprietà `SiteContents`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-128">The site contents is also different, as specified by the `SiteContents` properties.</span></span>

<span data-ttu-id="b76e2-129">Alla fine dello script di configurazione viene chiamata la configurazione (compilata in un documento MOF), passando `DevProdEnvData.psd1` come parametro `$ConfigurationData`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-129">At the end of the configuration script, we call the configuration (compile it into a MOF document), passing `DevProdEnvData.psd1` as the `$ConfigurationData` parameter.</span></span>

><span data-ttu-id="b76e2-130">**Nota:** per questa configurazione è necessario installare i moduli `xSqlPs` e `xWebAdministration` nel nodo di destinazione.</span><span class="sxs-lookup"><span data-stu-id="b76e2-130">**Note:** This configuration requires the modules `xSqlPs` and `xWebAdministration` to be installed on the target node.</span></span>

<span data-ttu-id="b76e2-131">Definire la configurazione in un file denominato `MyWebApp.ps1`:</span><span class="sxs-lookup"><span data-stu-id="b76e2-131">Let's define the configuration in a file named `MyWebApp.ps1`:</span></span>

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs
    Import-DscResource -Module xWebAdministration

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.NodeName
   {
        # Install prerequisites
        WindowsFeature installdotNet35
        {
            Ensure      = "Present"
            Name        = "Net-Framework-Core"
            Source      = "c:\software\sxs"
        }

        # Install SQL Server
        xSqlServerInstall InstallSqlServer
        {
            InstanceName = $Node.SQLServerName
            SourcePath   = $Node.SqlSource
            Features     = "SQLEngine,SSMS"
            DependsOn    = "[WindowsFeature]installdotNet35"

        }
   }

   Node $AllNodes.Where{$_.Role -contains "Web"}.NodeName
   {
        # Install the IIS role
        WindowsFeature IIS
        {
            Ensure       = 'Present'
            Name         = 'Web-Server'
        }

        # Install the ASP .NET 4.5 role
        WindowsFeature AspNet45
        {
            Ensure       = 'Present'
            Name         = 'Web-Asp-Net45'

        }

        # Stop the default website
        xWebsite DefaultSite
        {
            Ensure       = 'Present'
            Name         = 'Default Web Site'
            State        = 'Stopped'
            PhysicalPath = 'C:\inetpub\wwwroot'
            DependsOn    = '[WindowsFeature]IIS'

        }

        # Copy the website content
        File WebContent

        {
            Ensure          = 'Present'
            SourcePath      = $Node.SiteContents
            DestinationPath = $Node.SitePath
            Recurse         = $true
            Type            = 'Directory'
            DependsOn       = '[WindowsFeature]AspNet45'

        }


        # Create the new Website

        xWebsite NewWebsite

        {

            Ensure          = 'Present'
            Name            = $Node.WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

<span data-ttu-id="b76e2-132">Quando si esegue questa configurazione, vengono creati tre file MOF (uno per ogni voce denominata nella matrice **AllNodes**):</span><span class="sxs-lookup"><span data-stu-id="b76e2-132">When you run this configuration, three MOF files are created (one for each named entry in the **AllNodes** array):</span></span>

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a><span data-ttu-id="b76e2-133">Uso di dati non specifici per un nodo</span><span class="sxs-lookup"><span data-stu-id="b76e2-133">Using non-node data</span></span>

<span data-ttu-id="b76e2-134">È possibile aggiungere chiavi aggiuntive alla tabella hash **ConfigurationData** per i dati che non sono specifici di un nodo.</span><span class="sxs-lookup"><span data-stu-id="b76e2-134">You can add additional keys to the **ConfigurationData** hashtable for data that is not specific to a node.</span></span>
<span data-ttu-id="b76e2-135">La configurazione seguente garantisce la presenza di due siti Web.</span><span class="sxs-lookup"><span data-stu-id="b76e2-135">The following configuration ensures the presence of two websites.</span></span>
<span data-ttu-id="b76e2-136">I dati per ogni sito Web sono definiti nella matrice **AllNodes**.</span><span class="sxs-lookup"><span data-stu-id="b76e2-136">Data for each website are defined in the **AllNodes** array.</span></span>
<span data-ttu-id="b76e2-137">Il file `Config.xml` viene usato per entrambi i siti Web, quindi viene definito in una chiave aggiuntiva con il nome `NonNodeData`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-137">The file `Config.xml` is used for both websites, so we define it in an additional key with the name `NonNodeData`.</span></span>
<span data-ttu-id="b76e2-138">Si noti che non sono previsti limiti per il numero di chiavi aggiuntive e il nome che è possibile assegnare.</span><span class="sxs-lookup"><span data-stu-id="b76e2-138">Note that you can have as many additional keys as you want, and you can name them anything you want.</span></span>
<span data-ttu-id="b76e2-139">`NonNodeData` non è una parola riservata, ma è semplicemente il nome di esempio scelto per la chiave aggiuntiva.</span><span class="sxs-lookup"><span data-stu-id="b76e2-139">`NonNodeData` is not a reserved word, it is just what we decided to name the additional key.</span></span>

<span data-ttu-id="b76e2-140">Per accedere alle chiavi aggiuntive, usare la variabile speciale **$ConfigurationData**.</span><span class="sxs-lookup"><span data-stu-id="b76e2-140">You access additional keys by using the special variable **$ConfigurationData**.</span></span>
<span data-ttu-id="b76e2-141">In questo esempio, l'accesso a `ConfigFileContents` avviene con la riga:</span><span class="sxs-lookup"><span data-stu-id="b76e2-141">In this example, `ConfigFileContents` is accessed with the line:</span></span>
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 <span data-ttu-id="b76e2-142">nel blocco di risorse `File`.</span><span class="sxs-lookup"><span data-stu-id="b76e2-142">in the `File` resource block.</span></span>


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

        @{
            NodeName = "VM-1"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },


        @{
            NodeName = "VM-2"
            SiteContents = "C:\Site2"
            SiteName = "Website2"
        }
    );

    NonNodeData =
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }
}

configuration WebsiteConfig
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a><span data-ttu-id="b76e2-143">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="b76e2-143">See Also</span></span>
- [<span data-ttu-id="b76e2-144">Uso dei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="b76e2-144">Using configuration data</span></span>](configData.md)
- [<span data-ttu-id="b76e2-145">Opzioni delle credenziali nei dati di configurazione</span><span class="sxs-lookup"><span data-stu-id="b76e2-145">Credentials Options in Configuration Data</span></span>](configDataCredentials.md)
- [<span data-ttu-id="b76e2-146">Configurazioni DSC</span><span class="sxs-lookup"><span data-stu-id="b76e2-146">DSC Configurations</span></span>](configurations.md)
