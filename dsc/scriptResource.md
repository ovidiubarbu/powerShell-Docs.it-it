# Risorsa Script DSC

 
> Si applica a: Windows PowerShell 4.0, Windows PowerShell 5.0

La risorsa **Script** in Windows PowerShell DSC (Desired State Configuration) fornisce un meccanismo per eseguire blocchi script di Windows PowerShell nei nodi di destinazione.

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
| GetScript| Fornisce un blocco script di Windows PowerShell eseguito quando si richiama il cmdlet [Get-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407379.aspx). Questo blocco deve restituire una tabella hash.| 
| SetScript| Fornisce un blocco script di Windows PowerShell. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), il blocco **TestScript** viene eseguito per primo. Se il blocco **TestScript** restituisce **$false**, il blocco **SetScript** viene eseguito. Se il blocco **TestScript** restituisce **$true**, il blocco **SetScript** non viene eseguito.| 
| TestScript| Fornisce un blocco script di Windows PowerShell. Quando si richiama il cmdlet [Start-DscConfiguration](https://technet.microsoft.com/en-us/library/dn521623.aspx), questo blocco viene eseguito. Se restituisce **$false**, il blocco SetScript viene eseguito. Se restituisce **$true**, il blocco SetScript non viene eseguito. Il blocco **TestScript** viene eseguito anche quando si richiama il cmdlet [Test-DscConfiguration](https://technet.microsoft.com/en-us/library/dn407382.aspx). In questo caso, tuttavia, il blocco **SetScript** non viene eseguito, indipendentemente dal valore restituito dal blocco TestScript. Il blocco **TestScript** deve restituire True se l'effettiva configurazione corrisponde alla configurazione dello stato desiderato corrente e False in caso contrario. La configurazione dello stato desiderato corrente è l'ultima configurazione applicata nel nodo che usa DSC.| 
| Credential| Indica le credenziali da usare per l'esecuzione dello script, se sono necessarie credenziali.| 
| DependsOn| Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa. Ad esempio, se l'ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.

## Esempio
```powershell
Script ScriptExample
{
    SetScript = { 
        $sw = New-Object System.IO.StreamWriter("C:\TempFolder\TestFile.txt")
        $sw.WriteLine("Some sample string")
        $sw.Close()
    }
    TestScript = { Test-Path "C:\TempFolder\TestFile.txt" }
    GetScript = { <# This must return a hash table #> }          
}
```

<!--HONumber=Feb16_HO4-->
