---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: ricreare l'endpoint dimostrativo
ms.technology: powershell
translationtype: Human Translation
ms.sourcegitcommit: d20ea8418cb7389d756de94ea752cf604b8d07af
ms.openlocfilehash: acd2cfbd038250a26236c875d0e8b03a32cd84f9

---

# Ricreare l'endpoint dimostrativo
Questa sezione spiega come generare una replica esatta dell'endpoint dimostrativo usato nella sezione precedente.
Verranno introdotti i concetti essenziali per la comprensione di JEA, incluse le configurazioni di sessione di PowerShell e le capacità del ruolo.

## Configurazioni di sessione di PowerShell
Se è stato usato JEA nella sezione precedente, la procedura è iniziata con l'esecuzione di questo comando:

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEA_Demo -Credential $NonAdminCred
```

Benché nella maggior parte dei casi i parametri siano di chiara interpretazione, il parametro *ConfigurationName* inizialmente può generare confusione.
Il parametro specifica la configurazione di sessione di PowerShell a cui si è connessi.

Il termine *configurazione di sessione di PowerShell* indica un endpoint di PowerShell.
In senso figurato, si tratta del "posto" in cui gli utenti si connettono e accedono alla funzionalità PowerShell.
In base all'impostazione della configurazione di sessione, offre funzionalità diverse per la connessione degli utenti.
Per JEA, le configurazioni di sessione vengono usate per circoscrivere PowerShell a un set limitato di funzionalità e per l'esecuzione come account virtuale con privilegi.

Nel computer sono già disponibili alcune configurazioni di sessione di PowerShell registrate, ognuna impostata in modo leggermente diverso.
La maggior parte di esse è inclusa in Windows, ma la configurazione di sessione "JEA_Demo" è stata impostata nella sezione dei [prerequisiti](prerequisites.md).
Per visualizzare tutte le configurazioni di sessione registrate, eseguire il comando seguente in un prompt di PowerShell per amministratore:

```PowerShell
Get-PSSessionConfiguration
```

## File di configurazione di sessione di PowerShell
È possibile creare nuove configurazioni di sessione registrando nuovi *file di configurazione di sessione di PowerShell*.
I file di configurazione di sessione hanno estensione "pssc"
e possono essere creati con il cmdlet New-PSSessionConfigurationFile.

A questo punto è possibile creare e registrare una nuova configurazione di sessione per JEA.

## Generare e modificare la configurazione di sessione di PowerShell
Eseguire il comando seguente per generare un file "scheletro" per la configurazione di sessione di PowerShell.

```PowerShell
New-PSSessionConfigurationFile -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

> **Suggerimento:** per impostazione predefinita, solo le impostazioni di configurazione più comuni vengono incluse nel file scheletro.
> Usare il parametro `-Full` per includere tutte le impostazioni applicabili nel file PSSC generato.

Aprire il file in PowerShell ISE o in un editor di testo.

```PowerShell
ise "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Aggiornare i campi seguenti nel file con i valori seguenti (ricordarsi di sostituire i valori nel proprio gruppo di sicurezza non amministratore):

```PowerShell
# OLD: SessionType = 'Default'
SessionType = 'RestrictedRemoteServer'

# OLD: TranscriptDirectory = 'C:\Transcripts\'
TranscriptDirectory = "C:\ProgramData\JEAConfiguration\Transcripts"

# OLD: # RunAsVirtualAccount = $true
RunAsVirtualAccount = $true

# OLD: RoleDefinitions = @{ 'CONTOSO\SqlAdmins' = @{ RoleCapabilities = 'SqlAdministration' }; 'CONTOSO\ServerMonitors' = @{ VisibleCmdlets = 'Get-Process' } }
RoleDefinitions = @{'CONTOSO\JEA_NonAdmin_Operator' = @{ RoleCapabilities =  'Maintenance' }}
```

Le voci hanno il significato seguente:

1.  Il campo *SessionType* definisce le impostazioni predefinite da usare con questo endpoint.
*RestrictedRemoteServer* definisce le impostazioni minime necessarie per la gestione remota.
Per impostazione predefinita, un endpoint *RestrictedRemoteServer* espone Get-Command, Get-FormatData, Select-Object, Get-Help, Measure-Object, Exit-PSSession, Clear-Host e Out-Default.
*ExecutionPolicy* viene impostato su *RemoteSigned* e *LanguageMode* su *NoLanguage*.
L'effetto di queste impostazioni è un punto di partenza minimo e sicuro per la configurazione dell'endpoint.

2.  Il campo *RoleDefinitions* assegna le capacità del ruolo a gruppi specifici.
Definisce chi fa cosa come un account con privilegi.
Con questo campo è possibile specificare le funzionalità disponibili per qualsiasi utente connesso in base all'appartenenza al gruppo.
Questo è l'elemento di base della funzionalità RBAC di JEA.
In questo esempio, si espone la capacità del ruolo "Maintenance" predefinita per i membri del gruppo "Contoso\JEA_NonAdmin_Operator".

3.  Il campo *RunAsVirtualAccount* indica che PowerShell deve "essere eseguito come" account virtuale per questo endpoint.
Per impostazione predefinita, l'account virtuale è un membro del gruppo Administrators incorporato.
In un controller di dominio è anche un membro del gruppo di amministratori del dominio per impostazione predefinita.
Più avanti in questa guida si apprenderà come personalizzare i privilegi dell'account virtuale.

4.  Il campo *TranscriptDirectory* indica dove vengono salvate le trascrizioni "over-the-shoulder" di PowerShell dopo ogni sessione remota.
Queste trascrizioni consentono di esaminare le azioni eseguite in ogni sessione in un formato leggibile.
Per altre informazioni sulle trascrizioni di PowerShell, vedere questo [post del blog](http://blogs.msdn.com/b/powershell/archive/2015/06/09/powershell-the-blue-team.aspx).
Nota: anche la normale registrazione degli eventi di Windows acquisisce informazioni su ciò che ogni utente esegue con PowerShell.
Le trascrizioni sono semplicemente un po' più leggibili.

Infine, salvare le modifiche apportate a *JEADemo2.pssc*.

## Applicare la configurazione di sessione di PowerShell

Per creare un endpoint da un file di configurazione di sessione, è necessario registrare il file.
Questa operazione richiede alcune informazioni:

1. Il percorso del file di configurazione della sessione.
2. Il nome della configurazione di sessione registrata. Si tratta dello stesso nome immesso dagli utenti per il parametro "ConfigurationName" quando si connettono all'endpoint con `Enter-PSSession` o `New-PSSession`.

Per registrare la configurazione di sessione nel computer locale, eseguire il comando seguente:

```PowerShell
Register-PSSessionConfiguration -Name 'JEADemo2' -Path "$env:ProgramData\JEAConfiguration\JEADemo2.pssc"
```

Congratulazioni, l'impostazione dell'endpoint JEA è stata completata.

## Testare l'endpoint
Eseguire di nuovo i passaggi riportati nella sezione [Uso di JEA](using-jea.md) per il nuovo endpoint per verificare se funziona come previsto.
Assicurarsi di usare il nome del nuovo endpoint (JEADemo2) quando si specifica il nome della configurazione per `Enter-PSSession`.

```PowerShell
Enter-PSSession -ComputerName . -ConfigurationName JEADemo2 -Credential $NonAdminCred
```

## Concetti chiave
**Configurazione di sessione di PowerShell**: detta anche *Endpoint di PowerShell*, è il "posto" in senso figurato dove gli utenti si connettono e accedono alle funzionalità di PowerShell.
Per visualizzare le configurazioni di sessione registrate nel sistema eseguire `Get-PSSessionConfiguration`.
Quando è configurata in modo specifico, una configurazione di sessione di PowerShell può essere definita *Endpoint JEA*.

**File di configurazione di sessione di PowerShell (con estensione pssc)**: un file che, quando è registrato, definisce le impostazioni per una configurazione di sessione di PowerShell.
Contiene le specifiche per i ruoli utente che possono connettersi all'endpoint, l'account virtuale "RunAs" e altro ancora.     

**Definizioni ruolo**: campo del file di configurazione di sessione che definisce le capacità del ruolo per la connessione degli utenti.
Definisce *chi* può fare *cosa* come account con privilegi.
Questo è l'elemento di base delle funzionalità RBAC di JEA.

**SessionType**: campo del file di configurazione di sessione che rappresenta le impostazioni predefinite per una configurazione di sessione.
Per gli endpoint JEA, deve essere impostato su RestrictedRemoteServer.

**Trascrizione PowerShell**: file contenente una visualizzazione "over-the-shoulder" di una sessione di PowerShell.
È possibile impostare PowerShell in modo che generi le trascrizioni per le sessioni JEA usando il campo TranscriptDirectory.
Per altre informazioni sulle trascrizioni, vedere questo [post del blog](https://technet.microsoft.com/en-us/magazine/ff687007.aspx).




<!--HONumber=Jul16_HO1-->


