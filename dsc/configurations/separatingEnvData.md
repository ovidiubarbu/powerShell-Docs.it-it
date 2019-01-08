---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Separazione dei dati di configurazione e dell'ambiente
ms.openlocfilehash: 24a92e5e4f15959498b57a1488a688d5548f3585
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401291"
---
# <a name="separating-configuration-and-environment-data"></a>Separazione dei dati di configurazione e dell'ambiente

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Può essere utile separare i dati usati in una configurazione DSC dalla configurazione stessa usando i dati di configurazione.
In questo modo, è possibile usare una singola configurazione per più ambienti.

Ad esempio, se si sviluppa un'applicazione, è possibile usare una sola configurazione per l'ambiente di sviluppo e per quello di produzione e usare i dati di configurazione per specificare i dati per ogni ambiente.

## <a name="what-is-configuration-data"></a>Cosa sono i dati di configurazione?

I dati di configurazione sono dati definiti in una tabella hash e passati a una configurazione DSC quando si compila la configurazione.

Per una descrizione dettagliata della tabella hash **ConfigurationData**, vedere [Uso dei dati di configurazione](configData.md).

## <a name="a-simple-example"></a>Un esempio semplice

Di seguito è riportato un esempio molto semplice che illustra il funzionamento.
Verrà creata una singola configurazione che assicura che **IIS** sia presente in alcuni nodi e che **Hyper-V** sia presente in altri:

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

L'ultima riga in questo script consente di compilare la configurazione, passando `$MyData` come valore del parametro **ConfigurationData**.

Il risultato è che vengono creati due file MOF:

```
    Directory: C:\DscTests\MyDscConfiguration


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:09 PM           1968 VM-1.mof
-a----        3/31/2017   5:09 PM           1970 VM-2.mof
```

`$MyData` specifica due nodi diversi, ognuno con i propri `NodeName` e `Role`. La configurazione crea in modo dinamico i blocchi **Node** eseguendo la raccolta dei nodi che riceve da `$MyData` (in particolare, `$AllNodes`) e filtra tale raccolta usando la proprietà `Role`.

## <a name="using-configuration-data-to-define-development-and-production-environments"></a>Uso dei dati di configurazione per definire gli ambienti di sviluppo e produzione

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

### <a name="configuration-script-file"></a>File di script di configurazione

Nella configurazione, definita in un file `.ps1`, i nodi definiti in `DevProdEnvData.psd1` vengono ora filtrati in base al ruolo (`MSSQL`, `Dev` o entrambi) e configurati di conseguenza.
L'ambiente di sviluppo ha sia SQL Server sia IIS in un nodo, mentre per l'ambiente di produzione si trovano in nodi diversi.
Anche il contenuto del sito è diverso, come specificato dalle proprietà `SiteContents`.

Alla fine dello script di configurazione viene chiamata la configurazione (compilata in un documento MOF), passando `DevProdEnvData.psd1` come parametro `$ConfigurationData`.

>**Nota:** Questa configurazione richiede i moduli `xSqlPs` e `xWebAdministration` da installare nel nodo di destinazione.

Definire la configurazione in un file denominato `MyWebApp.ps1`:

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

Quando si esegue questa configurazione, vengono creati tre file MOF (uno per ogni voce denominata nella matrice **AllNodes**):

```
    Directory: C:\DscTests\MyWebApp


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/31/2017   5:47 PM           2944 Prod-SQL.mof
-a----        3/31/2017   5:47 PM           6994 Dev.mof
-a----        3/31/2017   5:47 PM           5338 Prod-IIS.mof
```

## <a name="using-non-node-data"></a>Uso di dati non specifici per un nodo

È possibile aggiungere chiavi aggiuntive alla tabella hash **ConfigurationData** per i dati che non sono specifici di un nodo.
La configurazione seguente garantisce la presenza di due siti Web.
I dati per ogni sito Web sono definiti nella matrice **AllNodes**.
Il file `Config.xml` viene usato per entrambi i siti Web, quindi viene definito in una chiave aggiuntiva con il nome `NonNodeData`.
Si noti che non sono previsti limiti per il numero di chiavi aggiuntive e il nome che è possibile assegnare.
`NonNodeData` non è una parola riservata, ma è semplicemente il nome di esempio scelto per la chiave aggiuntiva.

Per accedere alle chiavi aggiuntive, usare la variabile speciale **$ConfigurationData**.
In questo esempio, l'accesso a `ConfigFileContents` avviene con la riga:
```powershell
 Contents = $ConfigurationData.NonNodeData.ConfigFileContents
 ```
 nel blocco di risorse `File`.


```powershell
$MyData =
@{
    AllNodes =
    @(
        @{
            NodeName           = “*”
            LogPath            = “C:\Logs”
        },

        @{
            NodeName = “VM-1”
            SiteContents = “C:\Site1”
            SiteName = “Website1”
        },


        @{
            NodeName = “VM-2”;
            SiteContents = “C:\Site2”
            SiteName = “Website2”
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
            Ensure       = “Present”
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + “\\config.xml”
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```


## <a name="see-also"></a>Vedere anche
- [Uso dei dati di configurazione](configData.md)
- [Opzioni delle credenziali nei dati di configurazione](configDataCredentials.md)
- [Configurazioni DSC](configurations.md)
