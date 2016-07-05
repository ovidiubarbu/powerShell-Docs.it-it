---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: "capacità del ruolo"
ms.technology: powershell
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 5b6dcb205d2c3cbb1a98c6465cb1002b9ed61459

---

# Capacità del ruolo

## Panoramica
Nella sezione precedente si è appreso che il campo "RoleDefinitions" definisce quali gruppi hanno accesso a quali capacità del ruolo.
Questa sezione spiega
che cosa sono le capacità del ruolo.  

## Introduzione alle capacità del ruolo di PowerShell
Le capacità del ruolo di PowerShell definiscono le operazioni che un utente può eseguire in corrispondenza di un endpoint JEA.
Indicano in dettaglio una serie di elementi, tra cui comandi visibili, applicazioni visibili e altro ancora.
Le capacità del ruolo vengono definite da file con estensione "psrc".

## Contenuto della capacità del ruolo
Per prima cosa è necessario esaminare e modificare il file di capacità del ruolo dimostrativo usato in precedenza.
Si supponga di aver distribuito la configurazione di sessione nel proprio ambiente, ma di aver ricevuto un feedback che indica che è necessario modificare le funzionalità esposte agli utenti.
Gli operatori devono avere la possibilità di riavviare i computer e vogliono essere in grado di ottenere informazioni sulle impostazioni di rete.
Gli addetti alla protezione hanno anche indicato che consentire agli utenti di eseguire "Restart-Service" senza restrizioni non è accettabile.
È necessario limitare i servizi che gli operatori possono riavviare.

Per apportare queste modifiche, eseguire PowerShell ISE come amministratore e aprire il file seguente:

```
C:\Program Files\WindowsPowerShell\Modules\Demo_Module\RoleCapabilities\Maintenance.psrc
```

Ora individuare e aggiornare le righe seguenti nel file:

```PowerShell
# OLD: VisibleCmdlets = 'Restart-Service'
VisibleCmdlets = 'Restart-Computer',
                 @{
                     Name = 'Restart-Service'
                     Parameters = @{ Name = 'Name'; ValidateSet = 'Spooler' }
                 },
                 'NetTCPIP\Get-*'

# OLD: VisibleExternalCommands = 'Item1', 'Item2'
VisibleExternalCommands = 'C:\Windows\system32\ipconfig.exe'
```

Il file contiene alcuni esempi interessanti:

1.  Restart-Service è stato limitato in modo che gli operatori possano usare Restart-Service solo con il parametro -Name e siano autorizzati solo a specificare "Spooler" come argomento per tale parametro.
Se necessario, è anche possibile limitare gli argomenti usando un'espressione regolare con "ValidatePattern" anziché "ValidateSet".

2.  Tutti i comandi con il verbo "Get" dal modulo NetTCPIP sono stati esposti.
Poiché i comandi "Get" in genere non modificano lo stato del sistema, si tratta di un'operazione relativamente sicura.
Detto questo, è assolutamente necessario esaminare ogni comando che si espone con JEA.

3.  È possibile esporre un eseguibile (ipconfig) usando VisibleExternalCommands.
Si possono anche esporre script completi di PowerShell con questo campo.
È importante specificare sempre il percorso completo per i comandi esterni per assicurarsi che non venga eseguito un programma con un nome simile, e potenzialmente dannoso, presente nel percorso dell'utente.

Salvare il file, quindi connettersi all'endpoint dimostrativo per verificare se le modifiche hanno avuto esito positivo.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
Get-Command
```
Poiché è stato modificato solo il file di capacità del ruolo, non è necessario registrare nuovamente la configurazione di sessione.
PowerShell troverà automaticamente la capacità del ruolo aggiornata quando un utente si connette.
Poiché le capacità del ruolo vengono caricate all'avvio della sessione, le sessioni esistenti non sono interessate dagli aggiornamenti dei file di capacità del ruolo.

A questo punto, verificare se è possibile riavviare il computer eseguendo Restart-Computer con il parametro -WhatIf, a meno che non si voglia riavviare il computer.

```PowerShell
Restart-Computer -WhatIf
```

Verificare che sia possibile eseguire "ipconfig"

```PowerShell
ipconfig
```

E infine verificare che Restart-Service funzioni solo per il servizio Spooler.

```PowerShell
Restart-Service Spooler # This should work
Restart-Service WSearch # This should fail
```

Al termine, chiudere la sessione.

```PowerShell
Exit-PSSession
```

## Creazione di capacità del ruolo
Nella sezione successiva verrà creato un endpoint JEA per gli utenti dell'help desk di Active Directory.
Per prima cosa verrà creato un file di capacità del ruolo vuoto da compilare in tale sezione.
Le capacità del ruolo devono essere create in una cartella "RoleCapabilities" all'interno di un modulo di PowerShell valido per poter essere risolte quando si avvia una sessione.

I moduli di PowerShell sono essenzialmente pacchetti di funzionalità di PowerShell.
Possono contenere funzioni di PowerShell, cmdlet, risorse DSC, capacità del ruolo e altro ancora.
È possibile trovare informazioni sui moduli eseguendo `Get-Help about_Modules` nella console di PowerShell.

Per creare un nuovo modulo di PowerShell con un file di capacità del ruolo vuoto, eseguire questi comandi:  

```PowerShell
# Create a new folder for the module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module' -ItemType Directory

# Add a module manifest to contain metadata for this module.
New-ModuleManifest -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psd1' -RootModule Contoso_AD_Module.psm1

# Create a blank script module. You'll use this for custom functions in the next section.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\Contoso_AD_Module.psm1' -ItemType File

# Create a RoleCapabilities folder in the AD_Module folder. PowerShell expects Role Capabilities to be located in a "RoleCapabilities" folder within a module.
New-Item -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities' -ItemType Directory

# Create a blank Role Capability in your RoleCapabilities folder. Running this command without any additional parameters just creates a blank template.
New-PSRoleCapabilityFile -Path 'C:\Program Files\WindowsPowerShell\Modules\Contoso_AD_Module\RoleCapabilities\ADHelpDesk.psrc'
```

Il file di capacità del ruolo è stato creato
e potrà essere usato nella sezione successiva.

## Concetti chiave
**Capacità del ruolo (estensione psrc)**: file che definisce le operazioni che un utente può eseguire in corrispondenza di un endpoint JEA.
Indica in dettaglio una serie di elementi, tra cui comandi visibili, applicazioni visibili della console e altro ancora.
Per fare in modo che PowerShell rilevi le capacità del ruolo, è necessario inserirle in una cartella "RoleCapabilities" in un modulo di PowerShell valido.

**Modulo di PowerShell**: pacchetto di funzionalità di PowerShell.
Può contenere funzioni di PowerShell, cmdlet, risorse DSC, capacità del ruolo e altro ancora.
Per essere caricati automaticamente, i moduli di PowerShell devono trovarsi in un percorso in `$env:PSModulePath`.




<!--HONumber=Jun16_HO4-->


