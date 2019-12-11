---
ms.date: 12/12/2018
keywords: dsc,powershell,configurazione,installazione
title: Configurazioni DSC
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "71954498"
---
# <a name="dsc-configurations"></a>Configurazioni DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

Le configurazioni DSC sono script di PowerShell che definiscono un tipo speciale di funzione.
Per definire una configurazione, usare la parola chiave **Configuration** di PowerShell.

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

Salvare lo script come file `.ps1`.

## <a name="configuration-syntax"></a>Sintassi di configurazione

Uno script di configurazione è costituito dalle parti seguenti:

- Blocco **Configuration**. Si tratta del blocco più esterno dello script. Per definirlo, usare la parola chiave **Configuration** e specificare un nome. In questo caso, il nome della configurazione è "MyDscConfiguration".
- Uno o più blocchi **Node**. Definiscono i nodi (computer o macchine virtuali) configurati. La configurazione precedente include un blocco **Node** che ha come destinazione un computer chiamato "TEST-PC1". Il blocco del nodo può accettare più nomi di computer.
- Uno o più blocchi di risorse. Si tratta del punto in cui la configurazione imposta le proprietà per le risorse configurate. In questo caso, sono presenti due blocchi di risorse, ognuno dei quali chiama la risorsa "WindowsFeature".

All'interno di un blocco **Configuration** è possibile eseguire tutte le operazioni che sono consentite anche in una funzione di PowerShell. Ad esempio, se nell'esempio precedente non si vuole codificare il nome del computer di destinazione nella configurazione, è possibile aggiungere un parametro per il nome del nodo:

In questo esempio è necessario specificare il nome del nodo passandolo come parametro **ComputerName** quando si compila la configurazione. Per impostazione predefinita, il nome è "localhost".

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

Il blocco **Node** può accettare anche più nomi di computer. Nell'esempio precedente è possibile usare il parametro `-ComputerName` o passare un elenco di computer delimitato da virgole direttamente al blocco **Node**.

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

Quando si specifica un elenco di computer per il blocco **Node** dall'interno di una configurazione, è necessario usare la notazione con matrice.

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a>Compilazione della configurazione

Prima di poter applicare una configurazione, è necessario compilarla in un documento MOF.
A questo scopo, è necessario chiamare la configurazione allo stesso modo in cui si chiama una funzione di PowerShell.
L'ultima riga dell'esempio contenente solo il nome della configurazione, chiama la configurazione.

> [!NOTE]
> Per chiamare una configurazione, la funzione deve essere nell'ambito globale (come per qualsiasi funzione di PowerShell).
> A questo scopo, è possibile effettuare il "dot-sourcing" dello script oppure eseguire lo script di configurazione premendo F5 o facendo clic sul pulsante **Esegui script** in ISE.
> Per effettuare il dot-sourcing dello script, eseguire il comando `. .\myConfig.ps1`, dove `myConfig.ps1` è il nome del file di script che contiene la configurazione.

Quando si chiama la configurazione, si verificano gli scenari seguenti:

- Risoluzione di tutte le variabili
- Creazione di una cartella nella directory corrente con lo stesso nome della configurazione.
- Creazione di un file denominato _NomeNodo_.mof nella nuova directory, dove _NomeNodo_ è il nome del nodo di destinazione della configurazione.
  In presenza di più nodi, verrà creato un file MOF per ognuno.

> [!NOTE]
> Il file MOF contiene tutte le informazioni di configurazione per il nodo di destinazione. Per questo motivo, è importante garantirne la sicurezza.
> Per altre informazioni, vedere [Protezione del file MOF](../pull-server/secureMOF.md).

La compilazione della prima configurazione sopra produce la struttura di cartelle seguente:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

Se la configurazione accetta un parametro, come nel secondo esempio, il parametro deve essere specificato in fase di compilazione. La configurazione avrà un aspetto simile al seguente:

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a>Uso di nuove risorse nella configurazione

Eseguendo gli esempi precedenti, si ricevere un avviso che informa che è stata usata una risorsa senza importarla in modo esplicito.
Oggi DSC include 12 risorse come parte del modulo PSDesiredStateConfiguration.

È possibile usare il cmdlet [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource) per determinare le risorse installate nel sistema e disponibili per l'uso da parte di Gestione configurazione locale.
Dopo che i moduli vengono inseriti in `$env:PSModulePath` e sono riconosciuti correttamente da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), devono comunque essere caricati nella configurazione.

**Import-DscResource** è una parola chiave dinamica che può essere riconosciuta solo all'interno di un blocco **Configuration** e non è un cmdlet.
**Import-DscResource** supporta due parametri:

- **ModuleName** corrisponde al modo consigliato di usare **Import-DscResource**. Questo parametro accetta il nome del modulo che contiene le risorse da importare, nonché una matrice di stringhe di nomi di modulo.
- **Name** è il nome della risorsa da importare. Non si tratta del nome descrittivo restituito come "Name" da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), ma del nome di classe usato per definire lo schema della risorsa (restituito come **ResourceType** da [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).

Per altre informazioni sull'uso di `Import-DSCResource`, vedere [Uso di Import-DSCResource](import-dscresource.md)

## <a name="powershell-v4-and-v5-differences"></a>Differenze tra PowerShell v4 e v5

Esistono alcune differenze per la posizione di archiviazione delle risorse DSC in PowerShell 4.0. Per altre informazioni, vedere [Posizione delle risorse](import-dscresource.md#resource-location).

## <a name="see-also"></a>Vedere anche

- [Panoramica di Windows PowerShell DSC (Desired State Configuration)](../overview/overview.md).
- [Risorse DSC](../resources/resources.md)
- [Configurazione di Gestione configurazione locale](../managing-nodes/metaConfig.md)
