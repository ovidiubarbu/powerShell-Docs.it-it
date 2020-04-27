---
title: Migrazione da Windows PowerShell 5.1 a PowerShell 7
description: Aggiornamento da PowerShell 5.1 a PowerShell 7 per le piattaforme Windows.
ms.date: 03/25/2020
ms.openlocfilehash: 8f19297bdb4825f3bbd50544dc5737997e3c83e3
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81440493"
---
# <a name="migrating-from-windows-powershell-51-to-powershell-7"></a>Migrazione da Windows PowerShell 5.1 a PowerShell 7

PowerShell 7 è progettato per ambienti cloud, locali e ibridi e include miglioramenti e [nuove funzionalità](What-s-New-in-PowerShell-70.md).

- Installazione ed esecuzione side-by-side con Windows PowerShell
- Compatibilità migliorata con i moduli di Windows PowerShell esistenti
- Nuove funzionalità di linguaggio, come operatori ternari e `ForEach-Object -Parallel`
- prestazioni migliorate
- Comunicazione remota basata su SSH
- Interoperabilità tra piattaforme
- Supporto per i contenitori Docker

PowerShell 7 viene eseguito side-by-side con Windows PowerShell in modo da consentire l'esecuzione semplificata di test e confronti tra le edizioni prima della distribuzione. La migrazione è semplice, rapida e sicura. Le probabilità di esito negativo sono molto ridotte.

PowerShell 7 è supportato nei sistemi operativi Windows seguenti:

- Windows 8.1 e 10
- Windows Server 2012, 2012 R2, 2016 e 2019

PowerShell 7 viene eseguito anche in macOS e in diverse distribuzioni di Linux. Per un elenco dei sistemi operativi supportati e informazioni sul ciclo di vita del supporto, vedere [Ciclo di vita del supporto di PowerShell](/powershell/scripting/powershell-support-lifecycle).

## <a name="installing-powershell-7"></a>Installazione di PowerShell 7

Per garantire flessibilità e per supportare le esigenze dell'IT, dei i tecnici DevOps e degli sviluppatori, sono disponibili diverse opzioni per l'installazione di PowerShell 7. Nella maggior parte dei casi le opzioni di installazione possono essere ridotte ai metodi seguenti:

- Distribuire PowerShell usando il [pacchetto MSI](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-msi-package)
- Distribuire PowerShell usando il [ pacchetto ZIP](/powershell/scripting/install/installing-powershell-core-on-windows#installing-the-zip-package)

> [!NOTE]
> Il pacchetto MSI può essere distribuito e aggiornato con prodotti gestionali come [System Center Configuration Manager (SCCM)](/configmgr/apps/). Scaricare i pacchetti dalla [pagina della versione di GitHub](https://github.com/PowerShell/PowerShell/releases).

La distribuzione del pacchetto MSI richiede l'autorizzazione di amministratore. Il pacchetto ZIP può essere distribuito da qualsiasi utente. Il pacchetto ZIP è il modo più semplice per installare PowerShell 7 per i test, prima di eseguire il commit in un'installazione completa.

## <a name="using-powershell-7-side-by-side-with-windows-powershell-51"></a>Uso di PowerShell 7 side-by-side con Windows PowerShell 5.1

PowerShell 7 è progettato per coesistere con Windows PowerShell 5.1. Le funzionalità seguenti garantiscono la protezione dell'investimento in PowerShell e la semplicità della migrazione a PowerShell 7.

- Percorso di installazione separato e nome dell'eseguibile
- PSModulePath separato
- Profili separati per ogni versione
- Compatibilità dei moduli migliorata
- Nuovi endpoint remoti
- Supporto di Criteri di gruppo
- Registri eventi separati

### <a name="separate-installation-path-and-executable-name"></a>Percorso di installazione separato e nome dell'eseguibile

PowerShell 7 viene installato in una nuova directory, consentendo l'esecuzione side-by-side con Windows PowerShell 5.1.

Percorsi di installazione per versione:

- Windows PowerShell 5.1: `$env:WINDIR\System32\WindowsPowerShell\v1.0`
- PowerShell Core 6.x: `$env:ProgramFiles\PowerShell\6`
- PowerShell 7: `$env:ProgramFiles\PowerShell\7`

La nuova posizione viene aggiunta all'elemento PATH in modo che sia possibile eseguire sia Windows PowerShell 5.1 che PowerShell 7. Se si sta eseguendo la migrazione da PowerShell Core 6.x a PowerShell 7, PowerShell 6 viene rimosso e l'elemento PATH viene sostituito.

In Windows PowerShell l'eseguibile di PowerShell è denominato `powershell.exe`. A partire dalla versione 6 l'eseguibile è denominato `pwsh.exe`. Il nuovo nome consente di semplificare il supporto dell'esecuzione side-by-side di entrambe le versioni.

### <a name="separate-psmodulepath"></a>PSModulePath separato

Per impostazione predefinita, Windows PowerShell e PowerShell 7 archiviano i moduli in percorsi diversi. PowerShell 7 combina tali percorsi nella variabile di ambiente `$Env:PSModulePath`. Quando si importa un modulo in base al nome, PowerShell controlla il percorso specificato da `$Env:PSModulePath`. Questo consente a PowerShell 7 di caricare sia i moduli Core che Desktop.

|            Ambito di installazione            |                Windows PowerShell 5.1                 |             PowerShell 7.0             |
| ----------------------------------- | ----------------------------------------------------- | -------------------------------------- |
| Moduli di PowerShell                  | `$env:WINDIR\system32\WindowsPowerShell\v1.0\Modules` | `$PSHOME\Modules`                      |
| Installato da utente -<br>Ambito AllUsers    | `$env:ProgramFiles\WindowsPowerShell\Modules`         | `$env:ProgramFiles\PowerShell\Modules` |
| Installato da utente -<br>Ambito CurrentUser | `$HOME\Documents\WindowsPowerShell\Modules`           | `$HOME\Documents\PowerShell\Modules`   |

Negli esempi seguenti vengono illustrati i valori predefiniti di `$Env:PSModulePath` per ogni versione.

- Per Windows PowerShell 5.1:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\WindowsPowerShell\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

- Per PowerShell 7:

  ```powershell
  $Env:PSModulePath -split (';')
  ```

  ```Output
  C:\Users\<user>\Documents\PowerShell\Modules
  C:\Program Files\PowerShell\Modules
  C:\Program Files\PowerShell\7\Modules
  C:\Program Files\WindowsPowerShell\Modules
  C:\WINDOWS\System32\WindowsPowerShell\v1.0\Modules
  ```

Si noti che PowerShell 7 include i percorsi di Windows PowerShell e i percorsi di PowerShell 7 per consentire il caricamento automatico dei moduli.

> [!NOTE]
> Potrebbero esistere percorsi aggiuntivi se è stata modificata la variabile di ambiente PSModulePath o se sono stati installati moduli o applicazioni personalizzati.

Per altre informazioni, vedere `PSModulePath` in [Informazioni sulle variabili di ambiente](/powershell/module/microsoft.powershell.core/about/about_environment_variables#environment-variables-that-store-preferences).

Per altre informazioni sui moduli, vedere [Informazioni sui moduli](/powershell/module/Microsoft.PowerShell.Core/About/about_Modules).

### <a name="separate-profiles"></a>Profili separati

Il profilo di PowerShell è uno script che viene eseguito all'avvio di PowerShell. Questo script personalizza l'ambiente tramite l'aggiunta di comandi, alias, funzioni, variabili, moduli e unità PowerShell. Lo script del profilo rende disponibili queste personalizzazioni in ogni sessione senza che sia necessario ricrearle manualmente.

Il percorso della posizione del profilo è stato modificato in PowerShell 7.

- In Windows PowerShell 5.1 il percorso del profilo è `$HOME\Documents\WindowsPowerShell`.
- In PowerShell 7 il percorso del profilo è `$HOME\Documents\PowerShell`.

Sono stati modificati anche i nomi file del profilo:

   ```powershell
   PS> $PROFILE | Select-Object *Host* | Format-List

   AllUsersAllHosts       : C:\Program Files\PowerShell\7\profile.ps1
   AllUsersCurrentHost    : C:\Program Files\PowerShell\7\Microsoft.PowerShell_profile.ps1
   CurrentUserAllHosts    : C:\Users\<user>\Documents\PowerShell\profile.ps1
   CurrentUserCurrentHost : C:\Users\<user>\Documents\PowerShell\Microsoft.PowerShell_profile.ps1
   ```

Per altre informazioni, vedere [Informazioni sui profili](/powershell/module/microsoft.powershell.core/about/about_profiles).

### <a name="powershell-7-compatibility-with-windows-powershell-51-modules"></a>Compatibilità di PowerShell 7 con i moduli di Windows PowerShell 5.1

La maggior parte dei moduli usati in Windows PowerShell 5.1, tra cui Azure PowerShell e Active Directory, funziona già con PowerShell 7. Stiamo continuando a collaborare con altri team per aggiungere il supporto nativo di PowerShell 7 per altri moduli, tra cui Microsoft Graph, Office 365 e altri ancora. Per l'elenco corrente dei moduli supportati, vedere [Compatibilità dei moduli di PowerShell 7](/powershell/scripting/whats-new/module-compatibility).

> [!NOTE]
> In Windows è stato aggiunto anche un commutatore **UseWindowsPowerShell** per `Import-Module` per semplificare la transizione a PowerShell 7 per chi usa moduli incompatibili. Per altre informazioni su questa funzionalità, vedere [Informazioni sulla compatibilità di Windows PowerShell](/powershell/module/Microsoft.PowerShell.Core/About/about_windows_powershell_compatibility).

### <a name="powershell-remoting"></a>Comunicazione remota di PowerShell

La comunicazione remota di Windows PowerShell consente di eseguire qualsiasi comando di PowerShell in uno o più computer remoti. È possibile stabilire connessioni permanenti, avviare sessioni interattive ed eseguire script in computer remoti.

#### <a name="ws-management-remoting"></a>Comunicazione remota di WS-Management

Windows PowerShell 5.1 e versioni precedenti usano il protocollo WS-Management (WSMAN) per la negoziazione della connessione e il trasporto dei dati. Gestione remota Windows (WinRM) usa il protocollo WSMAN. Se WinRM è stato abilitato, PowerShell 7 usa l'endpoint di Windows PowerShell 5.1 esistente denominato `Microsoft.PowerShell` per le connessioni remote. Per aggiornare PowerShell 7 in modo da includere il proprio endpoint, eseguire il cmdlet `Enable-PSRemoting`. Per informazioni sulla connessione a endpoint specifici, vedere [Comunicazione remota di WS-Management in PowerShell Core](/powershell/scripting/learn/remoting/wsman-remoting-in-powershell-core)

Per usare la comunicazione remota di Windows PowerShell, è necessario che il computer remoto sia configurato per la gestione remota.
Per altre informazioni, incluse le istruzioni, vedere [about_Remote_Requirements](/powershell/module/microsoft.powershell.core/about/about_remote_requirements).

Per altre informazioni sull'uso della comunicazione remota, vedere [Informazioni sulla comunicazione remota](/powershell/module/microsoft.powershell.core/about/about_remote)

#### <a name="ssh-based-remoting"></a>Comunicazione remota basata su SSH

La comunicazione remota basata su SSH è stata aggiunta in PowerShell Core 6.x per supportare altri sistemi operativi che non possono usare componenti nativi di Windows come **WinRM**. La comunicazione remota SSH crea un processo host di PowerShell nel computer di destinazione come sottosistema SSH. Per informazioni dettagliate ed esempi su come configurare la comunicazione remota basata su SSH in Windows o Linux, vedere: [Comunicazione remota di PowerShell su SSH](/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core).

> [!NOTE]
> PowerShell Gallery (PSGallery) contiene un modulo e un cmdlet che configura automaticamente la comunicazione remota basata su SSH. Installare il modulo `Microsoft.PowerShell.RemotingTools` da [PSGallery](https://www.powershellgallery.com/packages/Microsoft.PowerShell.RemotingTools/0.1.0) ed eseguire il cmdlet `Enable-SSH`.

I cmdlet `New-PSSession`, `Enter-PSSession` e `Invoke-Command` includono nuovi set di parametri per supportare le connessioni SSH.

```powershell
[-HostName <string>]  [-UserName <string>]  [-KeyFilePath <string>]
```

Per creare una sessione remota, specificare il computer di destinazione con il parametro **HostName** e il nome utente con il parametro **UserName**. Quando si eseguono i cmdlet in modo interattivo, viene chiesto di immettere una password.

```powershell
Enter-PSSession -HostName <Computer> -UserName <Username>
```

In alternativa, quando si usa il parametro **HostName**, specificare le informazioni sul nome utente seguite dal simbolo di chiocciola (`@`), seguito dal nome del computer.

```powershell
Enter-PSSession -HostName <Username>@<Computer>
```

È anche possibile configurare l'autenticazione con chiave SSH con il parametro **KeyFilePath**.
Per altre informazioni, vedere [Gestione delle chiavi OpenSSH](/windows-server/administration/openssh/openssh_keymanagement).

### <a name="group-policy-supported"></a>Supporto di Criteri di gruppo

PowerShell include le impostazioni Criteri di gruppo che consentono di definire valori di opzioni coerenti per i server in un ambiente aziendale. Tali impostazioni includono:

- Configurazione della sessione della console: imposta un endpoint di configurazione in cui viene eseguito PowerShell.
- Attiva registrazione moduli: imposta la proprietà LogPipelineExecutionDetails dei moduli.
- Attiva la registrazione del blocco di script di PowerShell: abilita la registrazione dettagliata di tutti gli script di PowerShell.
- Attiva l'esecuzione di script: imposta i criteri di esecuzione di PowerShell.
- Attiva trascrizione di PowerShell: abilita l'acquisizione di input e output di comandi PowerShell in trascrizioni basate su testo.
- Imposta il percorso di origine predefinito per Update-Help: imposta l'origine per la Guida aggiornabile su una directory e non su Internet.

Per altre informazioni, vedere [Informazioni sulle impostazioni di Criteri di gruppo](/powershell/module/microsoft.powershell.core/about/about_group_policy_settings).

PowerShell 7 include modelli di Criteri di gruppo e uno script di installazione in `$PSHOME`.

Gli strumenti di Criteri di gruppo usano i file di modello amministrativi (`.admx`, `.adml`) per popolare le impostazioni dei criteri nell'interfaccia utente. Ciò consente agli amministratori di gestire le impostazioni dei criteri basate sul Registro di sistema. Lo script `InstallPSCorePolicyDefinitions.ps1` installa i modelli amministrativi di PowerShell Core nel computer locale.

```powershell
Get-ChildItem -Path $PSHOME -Filter *Core*Policy*
```

```Output
    Directory: C:\Program Files\PowerShell\7

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           2/27/2020 12:38 AM          15861 InstallPSCorePolicyDefinitions.ps1
-a---           2/27/2020 12:28 AM           9675 PowerShellCoreExecutionPolicy.adml
-a---           2/27/2020 12:28 AM           6201 PowerShellCoreExecutionPolicy.admx
```

### <a name="separate-event-logs"></a>Registri eventi separati

Gli eventi di registro di Windows PowerShell e PowerShell 7 consentono di separare i registri eventi. Usare il comando seguente per visualizzare un elenco dei registri di PowerShell.

```powershell
Get-WinEvent -ListLog *PowerShell*
```

Per altre informazioni, vedere [Informazioni sui registri di Windows](/powershell/module/microsoft.powershell.core/about/about_logging_windows).

## <a name="improved-editing-experience-with-visual-studio-code"></a>Esperienza di modifica migliorata con Visual Studio Code

[Visual Studio Code (VSCode)](https://code.visualstudio.com/) con l'[estensione PowerShell](https://code.visualstudio.com/docs/languages/powershell) è l'ambiente di scripting supportato per PowerShell 7. Windows PowerShell Integrated Scripting Environment (ISE) supporta solo Windows PowerShell.

L'estensione di PowerShell aggiornata include:

- Nuova modalità di compatibilità di ISE
- PSReadLine nella console integrata, inclusa l'evidenziazione della sintassi, la modifica a più righe e la ricerca a ritroso
- Miglioramenti alla stabilità e alle prestazioni
- Nuova integrazione con CodeLens
- Completamento automatico del percorso migliorato

Per semplificare la transizione a Visual Studio Code, usare la funzione **Enable ISE Mode** (Abilita modalità ISE) disponibile in **Riquadro comandi**. Questa funzione consente a VSCode di passare a un layout di tipo ISE. Il layout di tipo ISE offre tutte le nuove funzionalità di PowerShell in un'esperienza utente familiare.

Per passare al nuovo layout ISE, premere <kbd>CTRL</kbd>+<kbd>MAIUSC</kbd>+<kbd>P</kbd> per aprire **Riquadro comandi**, digitare `PowerShell` e selezionare **PowerShell: Enable ISE Mode** (Abilita modalità ISE).

Per impostare il layout sul layout originale, aprire **Riquadro comandi**, selezionare **PowerShell: Disable ISE Mode (restore to defaults)** (Disabilita modalità ISE - ripristino impostazioni predefinite).

Per informazioni dettagliate sulla personalizzazione del layout di VSCode in ISE, vedere [Come replicare l'esperienza ISE in Visual Studio Code](/powershell/scripting/components/vscode/how-to-replicate-the-ise-experience-in-vscode)

> [!NOTE]
> L'aggiornamento di ISE con le nuove funzionalità non è attualmente in programma. ISE è ora una funzionalità disinstallabile dall'utente nelle versioni più recenti di Windows 10 e Windows Server. La rimozione definitiva di ISE non è attualmente in programma. Il team di PowerShell e i relativi partner sono concentrati sul miglioramento dell'esperienza di scripting nell'estensione di PowerShell per Visual Studio Code.

## <a name="next-steps"></a>Passaggi successivi

Una volta apprese le informazioni necessarie per eseguire la migrazione, è possibile [installare PowerShell 7](/powershell/scripting/install/installing-powershell-core-on-windows).
