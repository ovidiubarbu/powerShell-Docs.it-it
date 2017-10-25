---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: dsc,powershell,configurazione,impostazione
title: Creazione di una pipeline di integrazione continua e distribuzione continua con DSC
ms.openlocfilehash: 6d21faef6e58068456c6c454b4d50b7a9415850b
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="building-a-continuous-integration-and-continuous-deplyoment-pipeline-with-dsc"></a>Creazione di una pipeline di integrazione continua e distribuzione continua con DSC

In questo esempio viene illustrato come creare una pipeline di integrazione continua e distribuzione continua (CI/CD) tramite PowerShell, DSC, Pester e Visual Studio Team Foundation Server (TFS).

Dopo averla creata e configurata, è possibile usare la pipeline per eseguire una distribuzione, una configurazione e un test completi di un server DNS e dei record host associati. Questo processo simula la prima parte di una pipeline da usare in un ambiente di sviluppo.

Una pipeline CI/CD automatizzata consente di aggiornare il software in modo più rapido e affidabile, assicurandosi che tutto il codice venga testato e che una compilazione corrente del codice sia sempre disponibile.

## <a name="prerequisites"></a>Prerequisiti

Per usare questo esempio, è necessario avere familiarità con quanto segue:

- Concetti di CI/CD. Informazioni di riferimento utili sono disponibili in [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf) (Modello di pipeline di versione).
- Controllo del codice sorgente tramite [Git](https://git-scm.com/)
- Framework di test [Pester](https://github.com/pester/Pester)
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Materiale necessario

Per compilare ed eseguire questo esempio, è necessario un ambiente con più computer e/o macchine virtuali.

### <a name="client"></a>Client

Si tratta del computer in cui verranno eseguite tutte le operazioni di impostazione ed esecuzione dell'esempio.

Il computer client deve essere un computer Windows dotato dei componenti seguenti:
- [Git](https://git-scm.com/)
- un repository git locale clonato da https://github.com/PowerShell/Demo_CI
- un editor di testo, ad esempio [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Computer che ospita il server TFS in cui verranno definite la compilazione e la versione.
In questo computer deve essere installato [Team Foundation Server 2017](https://www.visualstudio.com/tfs/).

### <a name="buildagent"></a>BuildAgent

Computer che esegue l'agente di compilazione Windows che compila il progetto.
In questo computer deve essere installato e in esecuzione un agente di compilazione Windows.
Per istruzioni su come installare ed eseguire un agente di compilazione Windows, vedere [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) (Distribuire un agente in Windows).

In questo computer è anche necessario installare i moduli DSC `xDnsServer` e `xNetworking`.

### <a name="testagent1"></a>TestAgent1

In questo esempio si tratta del computer configurato come server DNS dalla configurazione DSC.
Nel computer deve essere in esecuzione [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Si tratta del computer che ospita il sito Web configurato in questo esempio.
Nel computer deve essere in esecuzione [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016). 

## <a name="add-the-code-to-tfs"></a>Aggiungere il codice a TFS

Come prima cosa si creerà un repository Git in TFS e si importerà il codice dal repository locale nel computer client.
Se il repository Demo_CI non è stato ancora clonato nel computer client, eseguire questa operazione ora tramite il comando Git seguente:

`git clone https://github.com/PowerShell/Demo_CI`

1. Dal computer client passare al server TFS in un Web browser.
1. In TFS [creare un nuovo progetto team](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) denominato Demo_CI.

    Assicurarsi che **Controllo versione** sia impostato su **Git**.
1. Dal computer client aggiungere un remote al repository appena creato in TFS con il comando seguente:

    `git remote add tfs <YourTFSRepoURL>`

    Dove `<YourTFSRepoURL>` è l'URL clone del repository TFS creato nel passaggio precedente.

    Se non si conosce la posizione di questo URL, vedere [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone) (Clonare un repository Git esistente).
1. Eseguire il push del codice dal repository locale al repository TFS con il comando seguente:

    `git push tfs --all`
1. Il repository TFS verrà popolato con il codice Demo_CI.

>**Nota:** questo esempio usa il codice nel ramo `ci-cd-example` del repository Git.
>Assicurarsi di specificare questo ramo come ramo predefinito nel progetto TFS e per i trigger CI/CD creati.

## <a name="understanding-the-code"></a>Informazioni sul codice

Prima di creare le pipeline di compilazione e distribuzione, verrà ora esaminata una parte del codice per comprendere le operazioni eseguite da quest'ultimo.
Nel computer client aprire l'editor di testo preferito e passare alla radice del repository Git Demo_CI.

### <a name="the-dsc-configuration"></a>Configurazione DSC

Aprire il file `DNSServer.ps1` dalla radice del repository locale Demo_CI, `./InfraDNS/Configs/DNSServer.ps1`.

Questo file contiene la configurazione DSC per l'impostazione del server DNS. Ecco il file completo:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Si noti l'istruzione `Node`:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Questa trova tutti i nodi definiti con il ruolo `DNSServer` nei [dati di configurazione](configData.md), creati tramite lo script `DevEnv.ps1`.

L'uso di dati di configurazione per definire i nodi è importante quando si esegue l'integrazione continua. È probabile infatti che le informazioni sui nodi siano diverse da un ambiente all'altro e l'uso di dati di configurazione consente di apportare facilmente modifiche a tali informazioni senza modificare il codice di configurazione.

Nel primo blocco di risorse la configurazione chiama [WindowsFeature](windowsFeatureResource.md) per assicurare che sia abilitata la funzionalità DNS. I blocchi di risorse che seguono chiamano risorse dal modulo [xDnsServer](https://github.com/PowerShell/xDnsServer) per configurare la zona primaria e i record DNS.

Si noti che i due blocchi `xDnsRecord` sono racchiusi all'interno di cicli `foreach` che eseguono un'iterazione attraverso matrici nei dati di configurazione.
Anche in questo caso i dati di configurazione vengono creati dallo script `DevEnv.ps1`, che verrà esaminato subito dopo.

### <a name="configuration-data"></a>Dati di configurazione

Il file `DevEnv.ps1`, nella radice del repository Demo_CI locale, `./InfraDNS/DevEnv.ps1`, specifica i dati di configurazione specifici dell'ambiente in una tabella hash e quindi passa la tabella hash alla funzione `New-DscConfigurationDataDocument`, definita in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Ecco il file `DevEnv.ps1`:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

La funzione `New-DscConfigurationDataDocument`, definita in `\Assets\DscPipelineTools\DscPipelineTools.psm1`, crea a livello di codice un documento di dati di configurazione dalla tabella hash (dati di nodo) e dalla matrice (dati non di nodo) passati come parametri `RawEnvData` e `OtherEnvData`.

In questo caso viene usato solo il parametro `RawEnvData`.

### <a name="the-psake-build-script"></a>Script di compilazione psake

Lo script di compilazione [psake](https://github.com/psake/psake) definito in `Build.ps1` (nella radice del repository Demo_CI, `./InfraDNS/Build.ps1`) definisce le attività che fanno parte della compilazione
e indica da quali altre attività ogni attività dipende. Quando viene richiamato, lo script psake assicura che l'attività specificata (o l'attività denominata `Default`, se non è specificata alcuna attività) venga eseguita,così come tutte le dipendenze. Questa esecuzione è ricorsiva, perché vengano eseguite anche le dipendenze delle dipendenze e così via.

In questo esempio l'attività `Default` è definita come:

```powershell
Task Default -depends UnitTests
```

L'attività `Default` di per sé non ha un'implementazione, ma presenta una dipendenza dall'attività `CompileConfigs`.
La catena di relazioni tra attività risultante garantisce che tutte le attività nello script di compilazione vengano eseguite.

In questo esempio lo script psake viene richiamato da una chiamata a `Invoke-PSake` nel file `Initiate.ps1`, nella radice del repository Demo_CI:

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

Quando si crea la definizione di compilazione per questo esempio in TFS, il file di script psake viene specificato come parametro `fileName` di questo script.

Lo script di compilazione definisce le attività seguenti:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Esegue `DevEnv.ps1`, che genera il file di dati di configurazione.

#### <a name="installmodules"></a>InstallModules

Installa i moduli necessari per il file `DNSServer.ps1` di configurazione.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Chiama [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Esegue gli unit test [Pester](https://github.com/pester/Pester/wiki).

#### <a name="compileconfigs"></a>CompileConfigs

Compila la configurazione (`DNSServer.ps1`) in un file MOF, usando i dati di configurazione generati dall'attività `GenerateEnvironmentFiles`.

#### <a name="clean"></a>Clean

Crea le cartelle usate per l'esempio e rimuove tutti i risultati dei test, i file di dati di configurazione e i moduli delle esecuzioni precedenti.

### <a name="the-psake-deploy-script"></a>Script di distribuzione psake

Lo script di distribuzione [psake](https://github.com/psake/psake) definito in `Deploy.ps1` (nella radice del repository Demo_CI, `./InfraDNS/Deploy.ps1`) definisce le attività che distribuiscono ed eseguono la configurazione.

`Deploy.ps1` definisce le attività seguenti:

#### <a name="deploymodules"></a>DeployModules

Avvia una sessione di PowerShell in `TestAgent1` e installa i moduli contenenti le risorse DSC necessarie per la configurazione.

#### <a name="deployconfigs"></a>DeployConfigs

Chiama il cmdlet [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) per eseguire la configurazione in `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Esegue i test di integrazione di [Pester](https://github.com/pester/Pester/wiki).

#### <a name="acceptancetests"></a>AcceptanceTests

Esegue i test di accettazione di [Pester](https://github.com/pester/Pester/wiki).

#### <a name="clean"></a>Clean

Rimuove tutti i moduli installati durante le esecuzioni precedenti e verifica l'esistenza della cartella dei risultati dei test.

### <a name="test-scripts"></a>Script di test

I test di accettazione e di integrazione e gli unit test sono definiti all'interno di script nella cartella `Tests` (nella radice del repository Demo_CI, `./InfraDNS/Tests`), ognuno all'interno di un file `DNSServer.tests.ps1` nella rispettiva cartella.

I test di script usano la sintassi di [Pester](https://github.com/pester/Pester/wiki) e [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="unit-tests"></a>Unit test

Gli unit test eseguono il test delle configurazioni DSC per garantire che durante l'esecuzione le configurazioni funzionino come previsto.
Gli script di unit test script usano [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Test di integrazione

I test di integrazione eseguono il test della configurazione del sistema per garantire che, quando integrato con altri componenti, il sistema sia configurato come previsto. Questi test vengono eseguiti nel nodo di destinazione dopo la configurazione di quest'ultimo con DSC.
Gli script dei test di integrazione usano una combinazione della sintassi di [Pester](https://github.com/pester/Pester/wiki) e di [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

#### <a name="acceptance-tests"></a>Test di accettazione

I test di accettazione eseguono il test del sistema per assicurarsi che funzioni come previsto.
I test verificano, ad esempio, che una query a una pagina Web restituisca le informazioni corrette.
Questi test vengono eseguiti in remoto dal nodo di destinazione per testare scenari reali.
Gli script dei test di integrazione usano una combinazione della sintassi di [Pester](https://github.com/pester/Pester/wiki) e di [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction).

## <a name="define-the-build"></a>Definire la compilazione

Dopo aver caricato il codice in TFS e averne osservato il funzionamento, è possibile definire la compilazione.

In questo esempio verranno trattati solo i passaggi di compilazione da aggiungere alla compilazione stessa. Per istruzioni su come creare una definizione di compilazione in TFS, vedere [Create your first build and release](https://www.visualstudio.com/en-us/docs/build/define/create) (Creare la prima compilazione e la prima versione).

Creare una nuova definizione di compilazione (selezionare il modello **vuoto**) denominato "InfraDNS".
Aggiungere alla definizione di compilazione i passaggi seguenti:

- Script PowerShell
- Pubblicazione dei risultati dei test
- Copia dei file
- Pubblicazione dell'elemento

Dopo l'aggiunta di queste istruzioni di compilazione, modificare le proprietà di ogni istruzione nel modo seguente:

### <a name="powershell-script"></a>Script PowerShell

1. Impostare la proprietà **Tipo** su `File Path`.
1. Impostare la proprietà **Percorso script** su `initiate.ps1`.
1. Aggiungere `-fileName build` alla proprietà **Argomenti**.

Questa istruzione di compilazione esegue il file `initiate.ps1`, che chiama lo script di compilazione psake.

### <a name="publish-test-results"></a>Pubblicazione dei risultati dei test

1. Impostare **Formato dei risultati test** su `NUnit`
1. Impostare **File dei risultati del test** su `InfraDNS/Tests/Results/*.xml`
1. Impostare **Titolo esecuzione dei test** su `Unit`.
1. Assicurarsi che in **Opzioni di controllo** le opzioni **Abilitato** ed **Esegui sempre** siano entrambe selezionate.

Questa istruzione di compilazione esegue gli unit test dello script Pester esaminato in precedenza e archivia i risultati nella cartella `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Copia dei file

1. Aggiungere ognuna delle righe seguenti a **Contenuto**:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Impostare **TargetFolder** su `$(BuildArtifactStagingDirectory)\`

Questa istruzione copia gli script di compilazione e di test nella directory di gestione temporanea, in modo che i risultati possano essere pubblicati come elementi di compilazione nel passaggio successivo.

### <a name="publish-artifact"></a>Pubblicazione dell'elemento

1. Impostare **Percorso per la pubblicazione** su `$(Build.ArtifactStagingDirectory)\`
1. Impostare **Nome elemento** su `Deploy`
1. Impostare **Tipo elemento** su `Server`
1. Selezionare `Enabled` in **Opzioni di controllo**

## <a name="enable-continuous-integration"></a>Abilitare l'integrazione continua

Ora verrà configurato un trigger che attiva la compilazione del progetto ogni volta che una modifica viene archiviata nel ramo `ci-cd-example` del repository Git.

1. In TFS fare clic sulla scheda **Compilazione e versione**
1. Selezionare la definizione di compilazione `DNS Infra` e fare clic su **Modifica**
1. Fare clic sulla scheda **Trigger**
1. Selezionare **Integrazione continua (CI)**e selezionare `refs/heads/ci-cd-example` nell'elenco a discesa dei rami
1. Fare clic su **Salva** e quindi su **OK**

Ora qualsiasi modifica al repository Git in TFS attiva una compilazione automatizzata.

## <a name="create-the-release-definition"></a>Creare la definizione di versione

Verrà ora creata una definizione di versione, in modo che il progetto venga distribuito nell'ambiente di sviluppo a ogni archiviazione di codice.

A tale scopo, aggiungere una nuova definizione di versione associata alla definizione di compilazione `InfraDNS` creata in precedenza.
Assicurarsi di selezionare **Distribuzione continua**, in modo che venga attivata una nuova versione ogni volta che viene completata una nuova compilazione
([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions) (Procedura: Usare le definizioni di versione)) e configurarla come segue:

Aggiungere alla definizione di versione i passaggi seguenti:

- Script PowerShell
- Pubblicazione dei risultati dei test
- Pubblicazione dei risultati dei test

Modificare i passaggi come segue:

### <a name="powershell-script"></a>Script PowerShell

1. Impostare il campo **Percorso script** su `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Impostare il campo **Argomenti** su `-fileName Deploy`

### <a name="first-publish-test-results"></a>Prima pubblicazione dei risultati dei test

1. Selezionare `NUnit` per il campo **Formato dei risultati test**
1. Impostare il campo **File dei risultati del test** su `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Impostare il campo **Titolo esecuzione dei test** su `Integration`
1. In **Opzioni di controllo** selezionare **Esegui sempre**

### <a name="second-publish-test-results"></a>Seconda pubblicazione dei risultati dei test

1. Selezionare `NUnit` per il campo **Formato dei risultati test**
1. Impostare il campo **File dei risultati del test** su `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Impostare il campo **Titolo esecuzione dei test** su `Acceptance`
1. In **Opzioni di controllo** selezionare **Esegui sempre**

## <a name="verify-your-results"></a>Verificare i risultati

A questo punto, ogni volta che si esegue il push delle modifiche apportate al ramo `ci-cd-example` in TFS viene avviata una nuova compilazione.
Se la compilazione viene completata correttamente, viene attivata una nuova distribuzione.

Per controllare il risultato della distribuzione, aprire un browser nel computer client e passare a `www.contoso.com`.

## <a name="next-steps"></a>Passaggi successivi

Questo esempio configura il server DNS `TestAgent1` in modo che l'URL `www.contoso.com` venga risolto in `TestAgent2` ma non distribuisca un sito Web.
Lo scheletro per questa operazione è disponibile nel repository nella cartella `WebApp`.
Per creare script psake, test Pester e configurazioni DSC per la distribuzione di un sito Web personale, è possibile usare gli stub forniti.







