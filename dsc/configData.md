---
title:   Separazione dei dati di configurazione e dell'ambiente
ms.date:  2016-05-16
keywords:  powershell,DSC
description:  
ms.topic:  article
author:  eslesar
manager:  dongill
ms.prod:  powershell
---

# Separazione dei dati di configurazione e dell'ambiente

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

In Windows PowerShell DSC (Desired State Configuration) è possibile separare i dati di configurazione dalla logica della configurazione. Un altro approccio a questo aspetto consiste nel considerare la configurazione strutturale (ad esempio, una configurazione potrebbe richiedere l'installazione di IIS) come separata dalla configurazione ambientale, ovvero nel caso di un ambiente di test rispetto a un ambiente di produzione, in cui i nomi dei nodi sarebbero diversi, ma la configurazione applicata sarebbe la stessa. I vantaggi di questo approccio sono i seguenti:

* È possibile riutilizzare i dati di configurazione per risorse, configurazioni e nodi diversi.
* La logica di configurazione è più riutilizzabile se non contiene dati hardcoded. Si tratta di una situazione analoga alla disponibilità di valide linee guida di scripting per le funzioni.
* Se alcuni dei dati devono cambiare, è possibile apportare le modifiche in una sola posizione, risparmiando tempo e riducendo gli errori.

## Concetti ed esempi di base

Per specificare la parte ambientale della configurazione, DSC usa il parametro **ConfigurationData**, che è una tabella hash (o può accettare un file PSD1 che contiene la tabella hash). Questa tabella hash deve avere almeno una chiave **AllNodes**, che ha un valore strutturato. Ad esempio:

```powershell
$MyData = 
@{
    AllNodes = @()
    NonNodeData = ""   
}
```

Notare la chiave AllNodes, il cui valore è una matrice. Anche ogni elemento di questa matrice è una tabella hash, che richiede NodeName come chiave:

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

Ogni voce della tabella hash in AllNodes corrisponde a dati di configurazione in un nodo nella configurazione. Oltre alla chiave NodeName obbligatoria, è possibile aggiungere altre chiavi alla tabella hash, ad esempio:

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

DSC offre tre variabili speciali da usare nello script di configurazione:

* **$AllNodes**: fa riferimento a tutti i nodi. È possibile usare filtri con **.Where()** e **.ForEach()** in modo che, invece di definire nomi di nodo hardcoded per la selezione di nodi specifici per l'azione, sia possibile scrivere qualcosa di simile al codice seguente per selezionare VM-1 e VM-3 nell'esempio precedente:

```powershell
configuration MyConfiguration
{
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
    }
}
```

* **$Node**: dopo aver filtrato il set di nodi, è possibile usare $Node per fare riferimento alla voce specifica. Ad esempio:

```powershell
configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite
    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }
    }
}
```

Per applicare una proprietà a tutti i nodi, è possibile impostare NodeName = "*". Ad esempio, per assegnare a ogni nodo la proprietà LogPath, è possibile usare lo script seguente:

```
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },

 
        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );
}
```

* **$ConfigurationData**: è possibile usare questa variabile all'interno di una configurazione per accedere alla tabella hash dei dati di configurazione passata come parametro. Ad esempio:

```powershell
$MyData = 
@{
    AllNodes = 
    @(
        @{
            NodeName           = "*"
            LogPath            = "C:\Logs"
        },

 
        @{
            NodeName = "VM-1"
            Role     = "WebServer"
            SiteContents = "C:\Site1"
            SiteName = "Website1"
        },

 
        @{
            NodeName = "VM-2"
            Role     = "SQLServer"
        },
 

        @{
            NodeName = "VM-3"
            Role     = "WebServer"
            SiteContents = "C:\Site2"
            SiteName = "Website3"
        }
    );

    NonNodeData = 
    @{
        ConfigFileContents = (Get-Content C:\Template\Config.xml)
     }   
} 

configuration MyConfiguration
{
    Import-DscResource -ModuleName xWebAdministration -Name MSFT_xWebsite

    node $AllNodes.Where{$_.Role -eq "WebServer"}.NodeName
    {
        xWebsite Site
        {
            Name         = $Node.SiteName
            PhysicalPath = $Node.SiteContents
            Ensure       = "Present"
        }

        File ConfigFile
        {
            DestinationPath = $Node.SiteContents + "\\config.xml"
            Contents = $ConfigurationData.NonNodeData.ConfigFileContents
        }
    }
}
```

Un esempio completo è incluso nel [modulo xWebAdministration](https://powershellgallery.com/packages/xWebAdministration).



<!--HONumber=Jun16_HO3-->


