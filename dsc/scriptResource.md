---
title: Risorsa Script DSC
ms.date: 2016-05-16
keywords: powershell,DSC
description: 
ms.topic: article
author: eslesar
manager: dongill
ms.prod: powershell
translationtype: Human Translation
ms.sourcegitcommit: e1d217b8e633779f55e195fbf80aeee83db01409
ms.openlocfilehash: ad2b20a3a977dc33b27f8a1096a2b48fcb3abe0e

---

# Risorsa Script DSC

 
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **Script** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire blocchi script di Windows PowerShell nei nodi di destinazione. La risorsa `Script` dispone delle proprietà `GetScript`, `SetScript` e `TestScript`. Queste proprietà devono essere impostate per i blocchi di script che verranno eseguiti in ogni nodo di destinazione. 

Il blocco di script `GetScript` deve restituire una tabella hash che rappresenta lo stato del nodo corrente. La tabella hash deve contenere solo una chiave `Result` e il valore deve essere di tipo `String`. Non è necessario restituire alcun valore. DSC non esegue alcuna operazione con l'output di questo blocco di script.

Il blocco di script `TestScript` dovrebbe indicare se il nodo corrente necessita di modifica. Il blocco restituirà `$true` se il nodo è aggiornato. Il blocco restituirà `$false` se la configurazione del nodo non è aggiornata e deve essere aggiornata per il blocco di script `SetScript`. Il blocco di script `TestScript` viene chiamato da DSC.

Il blocco di script `SetScript` deve modificare il nodo. Se il blocco `TestScript` restituisce `$false`, viene chiamato da DSC.

Se è necessario usare le variabili dallo script di configurazione nei blocchi di script `GetScript`, `TestScript` o `SetScript`, usare l'ambito `$using:` (vedere l'esempio di seguito).


## Sintassi

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

## Proprietà

|  Proprietà  |  Descrizione   | 
|---|---| 
| GetScript| Fornisce un blocco script di Windows PowerShell eseguito quando si richiama il cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx). Questo blocco deve restituire una tabella hash. La tabella hash deve contenere solo una chiave **Result** e il valore deve essere di tipo **String**.| 
| SetScript| Fornisce un blocco script di Windows PowerShell. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), il blocco **TestScript** viene eseguito per primo. Se il blocco **TestScript** restituisce **$false**, il blocco **SetScript** viene eseguito. Se il blocco **TestScript** restituisce **$true**, il blocco **SetScript** non viene eseguito.| 
| TestScript| Fornisce un blocco script di Windows PowerShell. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), questo blocco viene eseguito. Se restituisce **$false**, il blocco SetScript viene eseguito. Se restituisce **$true**, il blocco SetScript non viene eseguito. Il blocco **TestScript** viene eseguito anche quando si richiama il cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal valore restituito dal blocco TestScript. Il blocco **TestScript** deve restituire True se l'effettiva configurazione corrisponde alla configurazione dello stato desiderato corrente e False in caso contrario. La configurazione dello stato desiderato corrente è l'ultima configurazione applicata nel nodo che usa DSC.| 
| Credential| Indica le credenziali da usare per l'esecuzione dello script, se sono necessarie credenziali.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.

## Esempio 1
```powershell
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
```

## Esempio 2
```powershell
$version = Get-Content 'version.txt'
Script UpdateConfigurationVersion
{
    GetScript = { 
        $currentVersion = Get-Content (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
        return @{ 'Result' = "Version: $currentVersion" }
    }          
    TestScript = { 
        $state = GetScript
        if( $state['Version'] -eq $using:version )
        {
            Write-Verbose -Message ('{0} -eq {1}' -f $state['Version'],$using:version)
            return $true
        }
        Write-Verbose -Message ('Version up-to-date: {0}' -f $using:version)
        return $false
    }
    SetScript = { 
        $using:version | Set-Content -Path (Join-Path -Path $env:SYSTEMDRIVE -ChildPath 'version.txt')
    }
}
```

Questa risorsa scrive la versione della configurazione di un file di testo. Questa versione è disponibile nel computer client, ma non su tutti i nodi, quindi deve essere passata su tutti i blocchi di script della risorsa `Script` con l'ambito `using` di PowerShell. Durante la generazione del file MOF del nodo, il valore della variabile `$version` viene letto da un file di testo nel computer client. DSC sostituisce le variabili `$using:version` in ogni blocco di script con il valore della variabile `$version`.




<!--HONumber=Jul16_HO1-->


