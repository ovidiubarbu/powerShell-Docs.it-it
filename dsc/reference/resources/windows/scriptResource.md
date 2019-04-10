---
ms.date: 08/24/2018
keywords: dsc,powershell,configurazione,installazione
title: Risorsa Script DSC
ms.openlocfilehash: 4eee5625add4d96ade7ababf7f534f597a26712d
ms.sourcegitcommit: 0ca836d1044e46d3a7dcbc69fa93d84f74848559
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/04/2019
ms.locfileid: "58920357"
---
# <a name="dsc-script-resource"></a>Risorsa Script DSC

> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.x

La risorsa **Script** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire blocchi script di Windows PowerShell nei nodi di destinazione. La risorsa **Script** usa le proprietà `GetScript`, `SetScript` e `TestScript` che contengono blocchi di script definiti per eseguire le operazioni per lo stato DSC corrispondente.

## <a name="syntax"></a>Sintassi

```
Script [string] #ResourceName
{
    GetScript = [string]
    SetScript = [string]
    TestScript = [string]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

> [!NOTE]
> I blocchi `GetScript`, `TestScript` e `SetScript` vengono archiviati come stringhe.

## <a name="properties"></a>Proprietà

|Proprietà|Description|
|--------|-----------|
|GetScript|Blocco di script che restituisce lo stato corrente del nodo.|
|SetScript|Blocco di script usato da DSC per garantire la conformità quando il nodo non è nello stato desiderato.|
|TestScript|Blocco di script che determina se il nodo è nello stato desiderato.|
|Credential| Indica le credenziali da usare per l'esecuzione dello script, se sono necessarie credenziali.|
|DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.

### <a name="getscript"></a>GetScript

DSC non usa l'output generato da `GetScript`. Il cmdlet [Get-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Get-DscConfiguration) esegue `GetScript` per recuperare lo stato corrente di un nodo. Non è necessario che venga restituito un valore da `GetScript`. Se si specifica un valore restituito, deve essere un valore `hashtable` contenente una chiave **Result** con valore `String`.

### <a name="testscript"></a>TestScript

Il blocco di script `TestScript` viene eseguito da DSC per determinare se eseguire `SetScript`. Se `TestScript` restituisce `$false`, DSC esegue `SetScript` per riportare il nodo allo stato desiderato. Deve restituire un valore `boolean`. Se il risultato è `$true`, il nodo è conforme e non è necessario eseguire `SetScript`.

Il cmdlet [Test-DscConfiguration](/powershell/module/PSDesiredStateConfiguration/Test-DscConfiguration) esegue `TestScript` per recuperare la conformità dei nodi alle risorse **Script**. Tuttavia, in questo caso il blocco `SetScript` non viene eseguito, indipendentemente dall'output restituito dal blocco `TestScript`.

> [!NOTE]
> Tutto l'output restituito da `TestScript` fa parte del valore restituito. PowerShell interpreta l'output non eliminato come diverso da zero e questo significa che `TestScript` restituisce `$true` indipendentemente dallo stato del nodo.
> Questo comportamento provoca risultati imprevedibili, falsi positivi e difficoltà durante la risoluzione dei problemi.

### <a name="setscript"></a>SetScript

`SetScript` modifica il nodo per applicare lo stato desiderato. Il blocco viene chiamato da DSC se il blocco di script `TestScript` restituisce `$false`. `SetScript` non deve avere alcun valore restituito.

## <a name="examples"></a>Esempi

### <a name="example-1-write-sample-text-using-a-script-resource"></a>Esempio 1: Scrivere testo di esempio tramite una risorsa Script

Questo esempio testa la presenza di `C:\TempFolder\TestFile.txt` in ogni nodo. Se il file non esiste, viene creato tramite `SetScript`. `GetScript` restituisce il contenuto del file, senza usare il valore restituito.

```powershell
Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script ScriptExample
        {
            SetScript = {
                $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
                $sw.WriteLine("Some sample string")
                $sw.Close()
            }
            TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
            GetScript = { @{ Result = (Get-Content C:\TempFolder\TestFile.txt) } }
        }
    }
}
```

### <a name="example-2-compare-version-information-using-a-script-resource"></a>Esempio 2: Confrontare le informazioni sulla versione tramite una risorsa Script

Questo esempio recupera informazioni sulla versione *conforme* da un file di testo nel computer di creazione e le archivia nella variabile `$version`. Durante la generazione del file MOF del nodo, DSC sostituisce le variabili `$using:version` in ogni blocco di script con il valore della variabile `$version`. Durante l'esecuzione, la versione *conforme* viene archiviata in un file di testo in ogni nodo e confrontata e aggiornata nelle esecuzioni successive.

```powershell
$version = Get-Content 'version.txt'

Configuration ScriptTest
{
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node localhost
    {
        Script UpdateConfigurationVersion
        {
            GetScript = {
                $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
                return @{ 'Result' = "$currentVersion" }
            }
            TestScript = {
                # Create and invoke a scriptblock using the $GetScript automatic variable, which contains a string representation of the GetScript.
                $state = [scriptblock]::Create($GetScript).Invoke()

                if( $state['Result'] -eq $using:version )
                {
                    Write-Verbose -Message ('{0} -eq {1}' -f $state['Result'],$using:version)
                    return $true
                }
                Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
                return $false
            }
            SetScript = {
                $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
            }
        }
    }
}
```
