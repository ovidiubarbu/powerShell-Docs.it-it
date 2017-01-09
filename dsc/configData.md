---
title: Separazione dei dati di configurazione e dell&quot;ambiente
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
ms.openlocfilehash: f8f8ef06cd79af294bad7bb8cf3d6676ab9a69bc
ms.sourcegitcommit: f06ef671c0a646bdd277634da89cc11bc2a78a41
translationtype: HT
---
# <a name="separating-configuration-and-environment-data"></a>Separazione dei dati di configurazione e dell'ambiente

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Con il parametro DSC predefinito **ConfigurationData** è possibile definire i dati che possono essere usati in una configurazione. Ciò consente di creare una singola configurazione da usare per più nodi o ambienti diversi. Ad esempio, se si sviluppa un'applicazione, è possibile usare una sola configurazione per l'ambiente di sviluppo e per quello di produzione e usare i dati di configurazione per specificare i dati per ogni ambiente.

Di seguito è riportato un esempio molto semplice che illustra il funzionamento. Verrà creata una singola configurazione che assicura che **IIS** sia presente in alcuni nodi e che **Hyper-V** sia presente in altri: 

```powershell
Configuration MyDscConfiguration {
    
    Node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        WindowsFeature IISInstall {
            Ensure = 'Present'
            Name   = 'Web-Server'
        }
        
    }
    Node $AllNodes.Where($_.Role -eq "VMHost").NodeName
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
        }

        @{
            NodeName    = 'VM-2'
            Role = 'VMHost'
        }
    )
}

MyDscConfiguration -ConfigurationData $MyData
```

L'ultima riga in questo script consente di compilare la configurazione in documenti MOF, passando `$MyData` come valore del parametro **ConfigurationData**. `$MyData` specifica due nodi diversi, ognuno con i propri `NodeName` e `Role`. La configurazione crea in modo dinamico i blocchi **Node** eseguendo la raccolta dei nodi che riceve da `$MyData` (in particolare, `$AllNodes`) e filtra tale raccolta usando la proprietà `Role`.

La sezione che segue illustra in dettaglio il funzionamento.

## <a name="the-configurationdata-parameter"></a>Il parametro ConfigurationData

Una configurazione DSC accetta un parametro denominato **ConfigurationData**, che si specifica quando si compila la configurazione. Per informazioni sulla compilazione delle configurazioni, vedere [Configurazioni DSC](configurations.md).

Il parametro **ConfigurationData** è una tabella hash che deve avere almeno una chiave denominata **AllNodes**. Può avere anche altre chiavi:

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Il valore della chiave **AllNodes** è una matrice. Ogni elemento della matrice è anche una tabella hash che deve avere almeno una chiave denominata **NodeName**:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
        },

 
        @{
            NodeName = "VM-2"
        },

 
        @{
            NodeName = "VM-3"
        }
    );

    NonNodeData = ""   
}
```

È anche possibile aggiungere altre chiavi a ogni tabella hash:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
        }
    );

    NonNodeData = ""   
}
```

Per applicare una proprietà a tutti i nodi, è possibile creare un membro della matrice **AllNodes** ha come **NodeName** `*`. Ad esempio, per assegnare a ogni nodo una proprietà `LogPath`, è possibile usare questo script:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName     = "*"
            LogPath      = "C:\Logs"
        },

 
        @{
            NodeName     = "VM-1"
            Role         = "WebServer"
            SiteContents = "C:\Site1"
            SiteName     = "Website1"
        },

 
        @{
            NodeName     = "VM-2"
            Role         = "SQLServer"
        },

 
        @{
            NodeName     = "VM-3"
            Role         = "WebServer"
            SiteContents = "C:\Site2"
            SiteName     = "Website3"
        }
    );
}
```

Questo equivale ad aggiungere una proprietà con nome `LogPath` e valore `"C:\Logs"` a ciascuno degli altri blocchi (`VM-1`, `VM-2` e `VM-3`).

## <a name="defining-the-configurationdata-hashtable"></a>Definizione della tabella hash ConfigurationData

È possibile definire **ConfigurationData** come variabile all'interno dello stesso file di script di una configurazione (come negli esempi precedenti) o in un file separato con estensione psd1. Per definire **ConfigurationData** in un file .psd1, creare un file che contiene solo la tabella hash che rappresenta i dati di configurazione.

Ad esempio, è possibile creare un file denominato `MyData.psd1` con il seguente contenuto:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        }

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

Per usare i dati di configurazione definiti in un file .psd1, passare il percorso e il nome del file come valore del parametro **ConfigurationData** durante la compilazione della configurazione:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Uso delle variabili ConfigurationData in una configurazione

DSC offre tre variabili speciali che possono essere usate in uno script di configurazione: **$AllNodes**, **$Node** e **$ConfigurationData**.

- **$AllNodes** si riferisce all'intera raccolta di nodi definita in **ConfigurationData**. È possibile filtrare la raccolta **AllNodes** usando **.Where()** e **.Foreach()**.
- **Node** fa riferimento a una particolare voce della raccolta **AllNodes** dopo che viene filtrato usando **.Where()** o **.Foreach()**.
- **ConfigurationData** fa riferimento all'intera tabella hash che viene passata come parametro durante la compilazione di una configurazione.

## <a name="devops-example"></a>Esempio di DevOps

Di seguito è riportato un esempio completo che usa una singola configurazione per impostare sia l'ambiente di sviluppo che quello di produzione di un sito Web. Nell'ambiente di sviluppo IIS e SQL Server vengono installati in un singolo nodo. Nell'ambiente di produzione IIS e SQL Server vengono installati in nodi separati. Nell'esempio verrà usato un file di dati di configurazione con estensione psd1 per specificare i dati per i due diversi ambienti.

### <a name="configuration-data-file"></a>File di dati di configurazione

I dati degli ambienti di sviluppo e produzione verranno definiti in un file denominato `DevProdEnvData.psd1` come indicato di seguito:

```powershell
@{

    AllNodes = @(

        @{
            NodeName        = "*"
            SQLServerName   = "MySQLServer"
            SqlSource       = "C:\Software\Sql"
            DotNetSrc       = "C:\Software\sxs"
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
        }

        @{
            NodeName         = "Dev"
            Role             = "MSSQL", "Web"
            SiteContents     = "C:\Website\Dev\SiteContents\"
            SitePath         = "\\Dev\Website\"

        }

    )

}

    )

}
```

### <a name="configuration-file"></a>File di configurazione

Ora, nella configurazione i nodi definiti in `DevProdEnvData.psd1` vengono filtrati in base al ruolo (`MSSQL`, `Dev` o entrambi) e configurati di conseguenza. L'ambiente di sviluppo ha sia SQL Server sia IIS in un nodo, mentre per l'ambiente di produzione si trovano in nodi diversi. Anche il contenuto del sito è diverso, come specificato dalle proprietà `SiteContents`.

Alla fine dello script di configurazione viene chiamata la configurazione (compilata in un documento MOF), passando `DevProdEnvData.psd1` come parametro `$ConfigurationData`.

```powershell
Configuration MyWebApp
{
    Import-DscResource -Module PSDesiredStateConfiguration
    Import-DscResource -Module xSqlPs

    Node $AllNodes.Where{$_.Role -contains "MSSQL"}.Nodename
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

   Node $AllNodes.Where($_.Role -contains "Web")
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
            Name            = $WebSiteName
            State           = 'Started'
            PhysicalPath    = $Node.SitePath
            DependsOn       = '[File]WebContent'
        }

    }

}

MyWebApp -ConfigurationData DevProdEnvData.psd1
```

## <a name="see-also"></a>Vedere anche
- [Opzioni delle credenziali nei dati di configurazione](configDataCredentials.md)
- [Configurazioni DSC](configurations.md)
