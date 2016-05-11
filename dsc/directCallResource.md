# Chiamata diretta dei metodi delle risorse DSC

>Si applica a: Windows PowerShell 5.0

È possibile usare il cmdlet [Invoke-DscResource](https://technet.microsoft.com/en-us/library/mt517869.aspx) per chiamare direttamente le funzioni o i metodi di una risorsa DSC (le funzioni **Get-TargetResource**,
**Set-TargetResource**e **Test-TargetResource** della risorsa basata su MOF i metodi **Get**, **Set** e **Test** della risorsa basata su una classe). 
Il cmdlet può essere usato da terze parti che desiderano usare risorse DSC o come strumento utile d'aiuto durante lo sviluppo delle risorse. 

Questo cmdlet viene in genere usato in combinazione con una proprietà di metaconfigurazione `refreshMode = 'Disabled'`, ma può essere usato indipendentemente dall'impostazione di **refreshMode**.

Quando si chiama il cmdlet **Invoke-DscResource**, specificare il metodo o la funzione da chiamare usando il parametro **Method**. Specificare le proprietà della risorsa passando una 
tabella di hash come valore del parametro **Property**.

Di seguito vengono riportati alcuni esempi di chiamate dirette ai metodi della risorsa:

## Verificare che sia presente un file

```powershell
$result = Invoke-DscResource -Name File -Method Set -Property @{
                            DestinationPath = "$env:SystemDrive\\DirectAccess.txt";
                            Contents = 'This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Eseguire un test per verificare la presenza di un file

```powershell
$result = Invoke-DscResource -Name File -Method Test -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result | fl
```

## Ottenere il contenuto del file

```powershell
$result = Invoke-DscResource -Name File -Method Get -Property @{
                            DestinationPath="$env:SystemDrive\\DirectAccess.txt";
                            Contents='This file is create by Invoke-DscResource'} -Verbose
$result.ItemValue | fl
```

## Vedere anche
- [Scrittura di una risorsa DSC personalizzata con MOF](authoringResourceMOF.md) 
- [Scrittura di una risorsa DSC personalizzata con classi di PowerShell](authoringResourceClass.md)
- [Debug di risorse DSC](debugResource.md)

<!--HONumber=Apr16_HO4-->


