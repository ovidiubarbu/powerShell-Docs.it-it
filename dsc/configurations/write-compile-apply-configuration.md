---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,servizio,impostazione
title: Scrivere, compilare e applicare una configurazione
ms.openlocfilehash: c884af9d92ac375457d6eb75d815ae9a9159e273
ms.sourcegitcommit: 5990f04b8042ef2d8e571bec6d5b051e64c9921c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/12/2019
ms.locfileid: "57795420"
---
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Scrivere, compilare e applicare una configurazione

Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).
Nell'esempio seguente si apprenderà come scrivere e applicare una configurazione molto semplice. La configurazione garantirà la presenza di un file "HelloWorld.txt" nel computer locale. Se si elimina il file, DSC lo crea nuovamente al successivo aggiornamento.

Per una panoramica di DSC e del relativo funzionamento, vedere [Panoramica di DSC (Desired State Configuration) per sviluppatori](../overview/overview.md).

## <a name="requirements"></a>Requisiti

Per eseguire questo esempio, è necessario un computer che esegue PowerShell 4.0 o versione successiva.

## <a name="write-the-configuration"></a>Scrivere la configurazione

Una [configurazione](configurations.md) DSC è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).

In PowerShell ISE o altri editor di PowerShell digitare quanto segue:

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

Salvare il file con nome "HelloWorld.ps1".

La definizione di una configurazione è simile a definizione di una funzione. Il blocco **Node** specifica il nodo di destinazione da configurare, in questo caso `localhost`.

La configurazione chiama un'unica [risorsa](../resources/resources.md), la risorsa `File`. Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.

## <a name="compile-the-configuration"></a>Compilare la configurazione

Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.
L'esecuzione della configurazione, come una funzione, compila un unico file con estensione "mof" per ogni nodo definito dal blocco `Node`.
Per eseguire la configurazione, è necessario *eseguire tramite l'operatore '.'* lo script "HelloWorld.ps1" nell'ambito corrente.
Per altre informazioni, vedere [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

<!-- markdownlint-disable MD038 -->
*Eseguire tramite l'operatore '.'* lo script "HelloWorld.ps1" digitando nel percorso in cui è archiviato, dopo `. ` (punto, spazio). È quindi possibile eseguire la configurazione chiamandola come una funzione.
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\WebsiteTest.ps1
HelloWolrd
```

Verrà generato l'output seguente:

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a>Applicare la configurazione

Ora che è disponibile il file MOF compilato, è possibile applicare la configurazione al nodo di destinazione, in questo caso il computer locale, chiamando il cmdlet [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration).

Il cmdlet `Start-DscConfiguration` indica a [Gestione configurazione locale](../managing-nodes/metaConfig.md), il motore di DSC, di applicare la configurazione.
Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.

Usare il codice seguente per eseguire il cmdlet `Start-DSCConfiguration`. Specificare il percorso della directory in cui è archiviato il file "localhost.mof" nel parametro `-Path`. Il cmdlet `Start-DSCConfiguration` ricerca nella directory specificata i file "\<nomecomputer\>.mof". Il cmdlet `Start-DSCConfiguration` tenta di applicare ogni file con estensione "mof" trovato al nome computer specificato dal nome file ("hostlocale", "server01", "dc-02" e così via).

> [!NOTE]
> Se il parametro `-Wait` non è specificato, `Start-DSCConfiguration` crea un processo in background per eseguire l'operazione. La specifica del parametro `-Verbose` consente di controllare l'output **dettagliato** dell'operazione. `-Wait` e `-Verbose` sono entrambi parametri facoltativi.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Verificare la configurazione

Al termine del cmdlet `Start-DSCConfiguration`, viene visualizzato un file "HelloWorld.txt" nel percorso specificato. È possibile verificare il contenuto con il cmdlet [Get-Content](/powershell/module/microsoft.powershell.management/get-content).

È anche possibile *testare* lo stato corrente usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

L'output sarà "True" se il nodo è attualmente compatibile con la configurazione applicata.

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a>Riapplicazione della configurazione

Per applicare nuovamente la configurazione, è possibile rimuovere il file di testo creato dalla configurazione. Quindi usare il cmdlet `Start-DSCConfiguration` con il parametro `-UseExisting`. Il parametro `-UseExisting` indica a `Start-DSCConfiguration` di riapplicare il file "current.mof" che rappresenta l'ultima configurazione applicata correttamente.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Passaggi successivi

- Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](configurations.md).
- Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](../resources/resources.md).
- Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).
