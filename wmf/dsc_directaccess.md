# Accesso diretto ai metodi delle risorse DSC


È stato aggiunto il cmdlet `Invoke-DscResource` per consentire l'accesso diretto alle risorse DSC e ai rispettivi metodi (Get, Set o Test). Può essere usato da terze parti che intendono sfruttare le risorse DSC. Questo cmdlet viene in genere usato in combinazione con `refreshMode = ‘Disabled’`, ma può essere usato indipendentemente dall'impostazione di refreshMode. Di seguito sono riportati alcuni esempi di come usare il nuovo cmdlet:

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


<!--HONumber=Apr16_HO4-->


