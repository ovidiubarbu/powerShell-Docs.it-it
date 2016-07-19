# Parametro NoNewLine
Per **Out-File**, **Add-Content** e **Set-Content** è ora disponibile una nuova opzione **-NoNewline** che omette semplicemente una nuova riga dopo l'output.
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt -NoNewline

PS C:\>; "a single " | Add-Content -Path Example.txt -NoNewline

PS C:\> "sentence." | Add-Content -Path Example.txt -NoNewline

PS C:\> Get-Content .\Example.txt

This is a single sentence.
```
Senza specificare **-NoNewline**, ogni frammento sarebbe su una riga separata:
```PowerShell
PS C:\> "This is " | Out-File -FilePath Example.txt

PS C:\> "a single " | Add-Content -Path Example.txt

PS C:\> "sentence." | Add-Content -Path Example.txt

PS C:\> Get-Content .\Example.txt

This is

a single

sentence.
```


<!--HONumber=Jun16_HO4-->


