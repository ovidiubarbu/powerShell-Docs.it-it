# Save-Script

Il cmdlet Save-Script consente di verificare il file di script salvandolo in una posizione specificata.

## Descrizione

Il cmdlet Save-Script salva lo script specificato.

## Sintassi del cmdlet

```powershell
Get-Command -Name Save-Script -Module PowerShellGet -Syntax
```
## Riferimento per la Guida online sui cmdlet

[Save-Script](http://go.microsoft.com/fwlink/?LinkId=619786)

## Comandi di esempio

### Esempio 1: salvare uno script da un repository
Questo comando salva la versione più recente dello script Fabrikam-ClientScript dal repository GalleryINT alla cartella locale C:\ScriptSharingDemo

```powershell
Save-Script -Name Fabrikam-ClientScript -Repository GalleryINT -Path C:\ScriptSharingDemo
```

### Esempio 2: salvare una versione di uno script eseguendo il piping dal cmdlet Find-Script

Il primo comando trova la versione 1.5 di Fabrikam-ClientScript dal repository GalleryINT e la salva nella cartella C:\ScriptSharingDemo

Il secondo comando convalida i metadati di script salvati.

```powershell
Find-Script -Name Fabrikam-ClientScript -Repository GalleryINT -RequiredVersion 1.5 | Save-Script -Path C:\\ScriptSharingDemo
Test-ScriptFileInfo C:\\ScriptSharingDemo\\Fabrikam-ClientScript.ps1

Version Name Author Description
------- ---- ------ -----------
1.5 Fabrikam-ClientScript manikb Description for the Fabrikam-ClientScript script
```


<!--HONumber=Aug16_HO3-->


