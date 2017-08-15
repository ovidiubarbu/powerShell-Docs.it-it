---
ms.date: 2017-06-12T00:00:00.000Z
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Introduzione a DSC (Desired State Configuration)
ms.openlocfilehash: e8a73296827297bab3229392c4193fed940c53bf
ms.sourcegitcommit: 46feddbc753523f464f139b5d272794620072fc8
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/02/2017
---
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="desired-state-configuration-quick-start"></a>Introduzione a DSC (Desired State Configuration)

Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).
L'esempio che verrà usato garantisce che in un server sia abilitata la funzionalità `Web-Server` (IIS) e che il contenuto di un semplice sito Web "Hello World" sia presente nella directory `intetpub\wwwroot` di tale server.

Per una panoramica di DSC e del relativo funzionamento, vedere [Panoramica di DSC (Desired State Configuration) per decision maker](decisionMaker.md).

## <a name="requirements"></a>Requisiti

Per eseguire questo esempio, è necessario un computer che esegue Windows Server 2012 o versione successiva e PowerShell 4.0 o versione successiva.

## <a name="write-and-place-the-indexhtm-file"></a>Scrivere e posizionare il file index.htm

Verrà innanzitutto creato il file HTML usato come contenuto del sito Web.

Nella cartella radice creare una cartella denominata `test`.

In un editor di testo digitare il testo seguente:

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

Salvare il file come `index.htm` nella cartella `test` creata in precedenza. 

## <a name="write-the-configuration"></a>Scrivere la configurazione

Una [configurazione DSC](configurations.md) è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).

In PowerShell ISE digitare il codice seguente:

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

Salvare il file come `WebsiteTest.ps1`.

Si può notare che assomiglia a una funzione di PowerShell con l'aggiunta della parola chiave **Configuration** usata prima del nome della funzione.

Il blocco **Node** specifica il nodo di destinazione da configurare, in questo caso `localhost`.

La configurazione chiama due [risorse](resources.md), [WindowsFeature](windowsFeatureResource.md) e [File](fileResource.md).
Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.

## <a name="compile-the-configuration"></a>Compilare la configurazione

Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.
A tale scopo, la configurazione viene eseguita come una funzione.
In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire i comandi seguenti per compilare la configurazione in un file MOF:

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

Verrà generato l'output seguente:

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

La prima riga rende la funzione di configurazione disponibile nella console.
La seconda riga esegue la configurazione.
Il risultato è la creazione di una nuova cartella denominata `WebsiteTest` come sottocartella della cartella corrente.
La cartella `WebsiteTest` contiene un file denominato `localhost.mof`.
Si tratta del file che può quindi essere applicato al nodo di destinazione.

## <a name="apply-the-configuration"></a>Applicare la configurazione

Ora che è disponibile il file MOF compilato, è possibile applicare la configurazione al nodo di destinazione, in questo caso il computer locale, chiamando il cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration).

Il cmdlet `Start-DscConfiguration` indica a [Gestione configurazione locale](metaConfig.md), ovvero il motore di DSC, di applicare la configurazione.
Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.

In una console di PowerShell passare alla stessa cartella in cui è stata salvata la configurazione ed eseguire il comando seguente:

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a>Verificare la configurazione

È possibile chiamare il cmdlet [DscConfigurationStatus Get](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) per verificare se la configurazione è stata applicata. 

È anche possibile testare i risultati direttamente, in questo caso passando a `http://localhost/` in un Web browser.
Dovrebbe essere visualizzata la pagina HTML "Hello World" creata nel primo passaggio di questo esempio.

## <a name="next-steps"></a>Passaggi successivi

- Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](configurations.md).
- Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](resources.md).
- Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).



