---
ms.date: 12/12/2018
keywords: DSC, powershell, configurazione, service, il programma di installazione
title: Scrivere, compilare e applicare una configurazione
ms.openlocfilehash: fa4d98fd12202439ba7025fd8af3fa398653ca05
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55677841"
---
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

# <a name="write-compile-and-apply-a-configuration"></a>Scrivere, compilare e applicare una configurazione

Questo esercizio illustra nei dettagli tutti i passaggi per creare e applicare una configurazione DSC (Desired State Configuration).
Nell'esempio seguente, si apprenderà come scrivere e applicare una configurazione molto semplice. La configurazione garantirà che esiste un file "HelloWorld.txt" nel computer locale. Se si elimina il file, DSC, ricreare la volta successiva che viene aggiornata.

Per una panoramica di DSC What ' s e il relativo funzionamento, vedere [Desired State Configuration di panoramica per gli sviluppatori](../overview/overview.md).

## <a name="requirements"></a>Requisiti

Per eseguire questo esempio, è necessario un computer che esegue PowerShell 4.0 o versione successiva.

## <a name="write-the-configuration"></a>Scrivere la configurazione

Una [configurazione](configurations.md) DSC è una funzione speciale di PowerShell che definisce come si vogliono configurare uno o più computer di destinazione (nodi).

In PowerShell ISE, o altri editor di PowerShell, digitare quanto segue:

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

Salvare il file come "HelloWorld.ps1".

La definizione di una configurazione è simile a definizione di una funzione. Il blocco **Node** specifica il nodo di destinazione da configurare, in questo caso `localhost`.

La configurazione chiama uno [le risorse](../resources/resources.md), il `File` risorsa. Le risorse si occupano di assicurarsi che il nodo di destinazione sia nello stato definito dalla configurazione.

## <a name="compile-the-configuration"></a>Compilare la configurazione

Per applicare una configurazione DSC a un nodo, è prima necessario compilarla in un file MOF.
Eseguire la configurazione, ad esempio una funzione, verrà compilato un solo file "MOF" per ogni nodo definito dal `Node` blocco.
Per eseguire la configurazione, è necessario *dot sourcing* script "HelloWorld.ps1" nell'ambito corrente.
Per altre informazioni, vedere [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).

*Dot sourcing* lo script "HelloWorld.ps1", digitare il percorso in cui è archiviato, dopo il `. ` (punto, lo spazio). È quindi possibile eseguire la configurazione quando viene chiamata una funzione simile.

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

Il `Start-DscConfiguration` cmdlet informa il [Configuration Manager locale](../managing-nodes/metaConfig.md), il motore di DSC, per applicare la configurazione.
Gestione configurazione locale si occupa di chiamare le risorse DSC per applicare la configurazione.

Usare il codice seguente per eseguire il `Start-DSCConfiguration` cmdlet. Specificare il percorso della directory in cui è archiviato il "localhost.mof" per il `-Path` parametro. Il `Start-DSCConfiguration` tramite la directory specificata per qualsiasi cmdlet eseguita una ricerca "\<computername\>MOF" file. Il `Start-DSCConfiguration` cmdlet tenta di applicare ogni file "MOF" trovata per il nome del computer specificato dal nome di file ("localhost", "server01", "controller di dominio-02" e così via).

> [!NOTE]
> Se il `-Wait` parametro viene omesso, `Start-DSCConfiguration` crea un processo in background per eseguire l'operazione. Specifica la `-Verbose` parametro consente di controllare il **Verbose** output dell'operazione. `-Wait`, e `-Verbose` sono entrambi i parametri facoltativi.

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a>Verificare la configurazione

Una volta il `Start-DSCConfiguration` cmdlet è stata completata, verrà visualizzato un file "HelloWorld.txt" nel percorso specificato. È possibile verificare il contenuto con il [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.

È anche possibile *testare* lo stato corrente usando [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).

L'output dovrebbe essere "True" se il nodo è attualmente compatibile con la configurazione applicata.

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

## <a name="re-applying-the-configuration"></a>Applicando nuovamente la configurazione

Per visualizzare la configurazione viene applicato anche in questo caso, è possibile rimuovere il file di testo creato dalla configurazione. L'uso di `Start-DSCConfiguration` cmdlet con il `-UseExisting` parametro. Il `-UseExisting` istruisce `Start-DSCConfiguration` per riapplicare il file "MOF", che rappresenta l'ultimo stato configurazione applicata.

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a>Passaggi successivi

- Ulteriori informazioni sulle configurazioni DSC sono disponibili in [Configurazioni DSC](configurations.md).
- Per informazioni sulle risorse DSC disponibili e su come creare risorse DSC personalizzate, vedere [Risorse DSC](../resources/resources.md).
- Le configurazioni e le risorse DSC sono disponibili in [PowerShell Gallery](https://www.powershellgallery.com/).
