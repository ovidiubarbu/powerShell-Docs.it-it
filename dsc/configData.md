---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: dsc,powershell,configurazione,installazione
title: Uso dei dati di configurazione
ms.openlocfilehash: 19544494a547a06d87701b38585844cb11d03e33
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="using-configuration-data-in-dsc"></a>Uso dei dati di configurazione in DSC

>Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Con il parametro DSC predefinito **ConfigurationData** è possibile definire i dati che possono essere usati in una configurazione.
Ciò consente di creare una singola configurazione da usare per più nodi o ambienti diversi.
Ad esempio, se si sviluppa un'applicazione, è possibile usare una sola configurazione per l'ambiente di sviluppo e per quello di produzione e usare i dati di configurazione per specificare i dati per ogni ambiente.

Questo argomento descrive la struttura della tabella hash **ConfigurationData**.
Per esempi di come usare i dati di configurazione, vedere [Separazione dei dati di configurazione e dell'ambiente](separatingEnvData.md).

## <a name="the-configurationdata-common-parameter"></a>Parametro comune ConfigurationData

Una configurazione DSC accetta il parametro comune **ConfigurationData** specificato quando si compila la configurazione.
Per informazioni sulla compilazione delle configurazioni, vedere [Configurazioni DSC](configurations.md).

Il parametro **ConfigurationData** è una tabella hash che deve avere almeno una chiave denominata **AllNodes**.
Può avere anche una o più chiavi aggiuntive.

>**Nota:** gli esempi di questo argomento usano una singola chiave aggiuntiva (diverso dalla chiave denominata **AllNodes**) denominata `NonNodeData`, ma è possibile includere qualsiasi numero di chiavi aggiuntive e assegnare loro un nome qualsiasi.

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

Per applicare una proprietà a tutti i nodi, è possibile creare un membro della matrice **AllNodes** ha come **NodeName** `*`.
Ad esempio, per assegnare a ogni nodo una proprietà `LogPath`, è possibile usare questo script:

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

È possibile definire **ConfigurationData** come variabile all'interno dello stesso file di script di una configurazione, come negli esempi precedenti, o in un file `.psd1` separato.
Per definire **ConfigurationData** in un file `.psd1`, creare un file che contiene solo la tabella hash che rappresenta i dati di configurazione.

Ad esempio, è possibile creare un file denominato `MyData.psd1` con il seguente contenuto:

```powershell
@{
    AllNodes =
    @(
        @{
            NodeName    = 'VM-1'
            FeatureName = 'Web-Server'
        },

        @{
            NodeName    = 'VM-2'
            FeatureName = 'Hyper-V'
        }
    )
}
```

## <a name="compiling-a-configuration-with-configuration-data"></a>Compilazione di una configurazione con i dati di configurazione

Per compilare una configurazione per la quale sono stati definiti i dati di configurazione, passare i dati della configurazione come valore del parametro **ConfigurationData**.

Viene creato un file MOF per ogni voce della matrice **AllNodes**.
Ogni file MOF è denominato con la proprietà `NodeName` della voce della matrice corrispondente.

Ad esempio, se si definiscono i dati di configurazione come nel file `MyData.psd1` precedente, la compilazione di una configurazione crea entrambi i file `VM-1.mof` e `VM-2.mof`.

### <a name="compiling-a-configuration-with-configuration-data-using-a-variable"></a>Compilazione di una configurazione con i dati di configurazione usando una variabile

Per usare dati di configurazione definiti come variabile nello stesso file `.ps1`, passare il nome della variabile come valore del parametro **ConfigurationData** durante la compilazione della configurazione:

```powershell
MyDscConfiguration -ConfigurationData $MyData
```

### <a name="compiling-a-configuration-with-configuration-data-using-a-data-file"></a>Compilazione di una configurazione con i dati di configurazione usando un file di dati

Per usare i dati di configurazione definiti in un file .psd1, passare il percorso e il nome del file come valore del parametro **ConfigurationData** durante la compilazione della configurazione:

```powershell
MyDscConfiguration -ConfigurationData .\MyData.psd1
```

## <a name="using-configurationdata-variables-in-a-configuration"></a>Uso delle variabili ConfigurationData in una configurazione

DSC offre tre variabili speciali che possono essere usate in uno script di configurazione: **$AllNodes**, **$Node** e **$ConfigurationData**.

- **$AllNodes** si riferisce all'intera raccolta di nodi definita in **ConfigurationData**. È possibile filtrare la raccolta **AllNodes** usando **.Where()** e **.Foreach()**.
- **Node** fa riferimento a una particolare voce della raccolta **AllNodes** dopo che viene filtrato usando **.Where()** o **.Foreach()**.
- **ConfigurationData** fa riferimento all'intera tabella hash che viene passata come parametro durante la compilazione di una configurazione.

## <a name="using-non-node-data"></a>Uso di dati non specifici per un nodo

Come illustrato negli esempi precedenti, la tabella hash **ConfigurationData** può avere una o più chiavi oltre alla chiave obbligatoria **AllNodes**.
Negli esempi di questo argomento è stato usato un solo nodo aggiuntivo che è stato denominato `NonNodeData`.
È comunque possibile definire qualsiasi numero di chiavi aggiuntive e assegnare alle chiavi qualsiasi nome.

Per un esempio d'uso di dati non nodo, vedere [Separazione dei dati di configurazione e dell'ambiente](separatingEnvData.md).

## <a name="see-also"></a>Vedere anche
- [Opzioni delle credenziali nei dati di configurazione](configDataCredentials.md)
- [Configurazioni DSC](configurations.md)