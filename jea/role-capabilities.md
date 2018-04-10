---
ms.date: 06/12/2017
author: rpsqrd
ms.topic: conceptual
keywords: jea,powershell,sicurezza
title: Funzionalità del ruolo JEA
ms.openlocfilehash: bd6d61443faf30e4056930a010103e6807c015c9
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2018
---
# <a name="jea-role-capabilities"></a>Funzionalità del ruolo JEA

> Si applica a: Windows PowerShell 5.0

Quando si crea un endpoint JEA, è necessario definire una o più "funzioni del ruolo" che descrivono *cosa* può eseguire un utente in una sessione JEA.
Una funzionalità del ruolo è un file di dati di PowerShell con l'estensione psrc che elenca tutti i cmdlet, le funzioni, i provider e i programmi esterni che devono essere resi disponibili per connettere gli utenti.

Questo argomento illustra come creare un file delle funzionalità del ruolo di PowerShell per gli utenti JEA.

## <a name="determine-which-commands-to-allow"></a>Determinare i comandi da consentire

Il primo passaggio durante la creazione di un file delle funzionalità del ruolo è considerare gli elementi a cui gli utenti assegnati al ruolo devono accedere.
Questo processo di raccolta dei requisiti potrebbe impiegare del tempo, ma è un processo molto importante.
L'accesso a un numero limitato di cmdlet e funzioni potrebbe impedire agli utenti di svolgere il loro lavoro in maniera completa.
L'accesso a un numero eccessivo di cmdlet e funzioni che non rientrano nei privilegi amministrativi impliciti degli utenti potrebbe creare problemi di sicurezza.

L'esecuzione di questo processo dipende dagli obiettivi della società. I suggerimenti seguenti tuttavia possono aiutare a capire se si è nella direzione giusta.

1. **Identificare** i comandi usati dagli utenti necessari per eseguire il loro lavoro. Questa operazione potrebbe comportare il controllo delle azioni del personale IT, degli script di automazione o l'analisi dei log o delle trascrizioni delle sessioni di PowerShell.
2. **Aggiornare** l'uso degli strumenti della riga di comando per renderli equivalenti, se possibile, a quelli di PowerShell, per un miglior controllo e una migliore esperienza di personalizzazione di JEA. I programmi esterni non possono essere vincolati in modo granulare come le funzioni e i cmdlet nativi di PowerShell in JEA.
3. **Limitare** l'ambito dei cmdlet, se necessario, per consentire solo parametri o valori di parametri specifici. Ciò è particolarmente importante nel caso in cui gli utenti debbano gestire solo parte di un sistema.
4. **Creare** funzioni personalizzate per sostituire i comandi complessi o difficili da vincolare in JEA. Una funzione semplice che esegue il wrapping di un comando complesso o applica una logica di convalida aggiuntiva può offrire un controllo maggiore agli amministratori e agli utenti finali.
5. **Testare** l'elenco relativo all'ambito di comandi consentiti per utenti e/o servizi di automazione e apportare le modifiche necessarie.

È importante ricordare che i comandi in una sessione JEA sono spesso eseguiti con privilegi amministrativi o comunque elevati.
Un'attenta selezione dei comandi disponibili è importante per garantire che l'endpoint JEA non consenta all'utente che si connette di elevare le proprie autorizzazioni.
Di seguito sono riportati alcuni esempi di comandi che possono essere usati maliziosamente in uno stato non vincolato.
Si noti che questo non è un elenco completo e deve essere usato solo come punto di partenza per l'analisi.

### <a name="examples-of-potentially-dangerous-commands"></a>Esempi di comandi potenzialmente pericolosi

Rischio | Esempio | Comandi correlati
-----|---------|-----------------
Concessione dei privilegi di amministratore all'utente che si connette per ignorare JEA | `Add-LocalGroupMember -Member 'CONTOSO\jdoe' -Group 'Administrators'` | `Add-ADGroupMember`, `Add-LocalGroupMember`, `net.exe`, `dsadd.exe`
Esecuzione di codice arbitrario, ad esempio malware, attacchi o script personalizzati per ignorare le protezioni | `Start-Process -FilePath '\\san\share\malware.exe'` | `Start-Process`, `New-Service`, `Invoke-Item`, `Invoke-WmiMethod`, `Invoke-CimMethod`, `Invoke-Expression`, `Invoke-Command`, `New-ScheduledTask`, `Register-ScheduledJob`

## <a name="create-a-role-capability-file"></a>Creare un file delle funzionalità del ruolo

È possibile creare un nuovo file delle funzionalità del ruolo di PowerShell con il cmdlet [New-PSRoleCapabilityFile](https://msdn.microsoft.com/powershell/reference/5.1/microsoft.powershell.core/New-PSRoleCapabilityFile).

```powershell
New-PSRoleCapabilityFile -Path .\MyFirstJEARole.psrc
```

Il file delle funzionalità del ruolo creato può essere aperto in un editor di testo e modificato per consentire i comandi appropriati per il ruolo.
La documentazione della Guida di PowerShell contiene molti esempi su come configurare il file.

### <a name="allowing-powershell-cmdlets-and-functions"></a>Consentire l'uso di funzioni e i cmdlet di PowerShell

Per autorizzare gli utenti a eseguire i cmdlet o le funzioni di PowerShell, aggiungere il nome del cmdlet o della funzione nei campi VisibleCmdlets o VisibleFunctions.
Nel caso in cui non si è certi se un comando è una funzione o un cmdlet, è possibile eseguire `Get-Command <name>` e verificare la proprietà "CommandType" nell'output.

```powershell
VisibleCmdlets = 'Restart-Computer', 'Get-NetIPAddress'
```

In alcuni casi l'ambito di una funzione o di cmdlet specifico è troppo esteso per le esigenze degli utenti.
Un amministratore DNS, ad esempio, deve probabilmente solo accedere per riavviare il servizio DNS.
In un ambiente multi-tenant dove i tenant hanno accesso agli strumenti di gestione self-service, questi dovrebbero essere limitati alla gestione con le proprie risorse.
In questi casi, è possibile limitare i parametri offerti dal cmdlet o dalla funzione.

```powershell

VisibleCmdlets = @{ Name = 'Restart-Computer'; Parameters = @{ Name = 'Name' }}

```

Negli scenari più avanzati, è necessario anche limitare i valori che un utente può specificare per tali parametri.
Le funzionalità del ruolo consentono di definire un set di valori consentiti o un modello di espressione regolare che viene valutato per determinare se è consentito un input specifico.

```powershell
VisibleCmdlets = @{ Name = 'Restart-Service'; Parameters = @{ Name = 'Name'; ValidateSet = 'Dns', 'Spooler' }},
                 @{ Name = 'Start-Website'; Parameters = @{ Name = 'Name'; ValidatePattern = 'HR_*' }}
```

> [!NOTE]
> I [parametri comuni di PowerShell](https://technet.microsoft.com/library/hh847884.aspx) sono sempre consentiti, anche se si limita la disponibilità dei parametri.
> È consigliabile non elencarli in maniera esplicita nel campo Parameters.

La tabella seguente illustra le varie modalità per personalizzare una funzione o un cmdlet visibile.
È possibile combinare le varie modalità descritte di seguito nel campo VisibleCmdlets.

Esempio                                                                                      | Caso d'uso
---------------------------------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------
`'My-Func'` o `@{ Name = 'My-Func' }`                                                       | Consente all'utente di eseguire `My-Func` senza limitazioni sui parametri.
`'MyModule\My-Func'`                                                                         | Consente all'utente di eseguire `My-Func` dal modulo `MyModule` senza limitazioni sui parametri.
`'My-*'`                                                                                     | Consente all'utente di eseguire qualsiasi cmdlet o funzione con il verbo `My`.
`'*-Func'`                                                                                   | Consente all'utente di eseguire qualsiasi cmdlet o funzione con il sostantivo `Func`.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'}, @{ Name = 'Param2' }}`               | Consente all'utente di eseguire `My-Func` con il parametro `Param1` e/o `Param2`. È possibile specificare qualsiasi valore per i parametri.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidateSet = 'Value1', 'Value2' }}`  | Consente all'utente di eseguire `My-Func` con il parametro `Param1`. Solo "Value1" e "Value2" possono essere specificati per il parametro.
`@{ Name = 'My-Func'; Parameters = @{ Name = 'Param1'; ValidatePattern = 'contoso.*' }}`     | Consente all'utente di eseguire `My-Func` con il parametro `Param1`. Per il parametro può essere specificato qualsiasi valore che inizia con "contoso".


> [!WARNING]
> In base alle procedure consigliate sulla sicurezza, è consigliabile non usare caratteri jolly nella definizione di cmdlet o funzioni visibili.
> In alternativa, è necessario elencare in modo esplicito ogni comando attendibile per assicurarsi che nessun altro comando che condivide lo stesso schema di denominazione venga involontariamente autorizzato.

Non è possibile applicare un ValidatePattern e ValidateSet allo stesso cmdlet o funzione.

In caso contrario, il ValidatePattern sostituirà il ValidateSet.

Per altre informazioni su ValidatePattern, vedere [questo *post* Hey, Scripting Guy!](https://blogs.technet.microsoft.com/heyscriptingguy/2011/01/11/validate-powershell-parameters-before-running-the-script/) e il contenuto dei riferimenti [Espressioni regolari di PowerShell](https://technet.microsoft.com/library/hh847880.aspx).

### <a name="allowing-external-commands-and-powershell-scripts"></a>Consentire l'uso di comandi esterni e degli script di PowerShell

Per consentire agli utenti di usare file eseguibili e script di PowerShell (ps1) in una sessione JEA, è necessario aggiungere il percorso completo per ogni programma nel campo VisibleExternalCommands.

```powershell
VisibleExternalCommands = 'C:\Windows\System32\whoami.exe', 'C:\Program Files\Contoso\Scripts\UpdateITSoftware.ps1'
```

È consigliabile, se possibile, usare i cmdlet e le funzioni equivalenti di PowerShell di tutti i file eseguibili esterni autorizzati dal momento che si ha il controllo sui parametri consentiti con le funzioni e i cmdlet di PowerShell.

Molti file eseguibili consentono di leggere lo stato attuale e quindi modificarlo specificando parametri diversi.

Si consideri ad esempio il ruolo di amministratore di un file server che vuole controllare quali condivisioni di rete sono ospitate dal computer locale.
Un modo per eseguire questa operazione è usare `net share`.
Tuttavia, consentire l'uso di net.exe è molto pericoloso perché l'amministratore può facilmente usare il comando per ottenere privilegi di amministratore con `net group Administrators unprivilegedjeauser /add`.
Un approccio migliore consiste nell'usare [Get-SmbShare](https://technet.microsoft.com/library/jj635704.aspx) che consente di ottenere lo stesso risultato, ma ha un ambito più ristretto.

Quando si rendono disponibili comandi esterni per gli utenti di una sessione JEA, specificare sempre il percorso completo del file eseguibile per assicurarsi che non venga eseguito un programma denominato in modo analogo (e potenzialmente pericoloso) che si trova in un'altra posizione nel sistema.

### <a name="allowing-access-to-powershell-providers"></a>Consentire accesso ai provider di PowerShell

Per impostazione predefinita, non sono disponibili provider di PowerShell nelle sessioni JEA.

In questo modo si riduce il rischio di accesso a informazioni sensibili e alle impostazioni di configurazione da parte dell'utente che si connette.

Se necessario, è possibile consentire l'accesso ai provider di PowerShell usando il comando `VisibleProviders`.
Per un elenco completo dei provider, eseguire `Get-PSProvider`.

```powershell
VisibleProviders = 'Registry'
```

Per eseguire semplici operazioni che richiedono l'accesso al file system, al Registro di sistema, all'archivio dei certificati o ad altri provider sensibili, è anche possibile scrivere una funzione personalizzata che interagisca con il provider per conto dell'utente.
Le funzioni, i cmdlet e i programmi esterni disponibili in una sessione JEA non sono soggetti agli stessi vincoli di JEA e possono accedere a qualsiasi provider per impostazione predefinita.
Si consideri anche l'uso dell'[unità utente](session-configurations.md#user-drive) quando è necessario copiare file da o in un endpoint JEA.

### <a name="creating-custom-functions"></a>Creazione di funzioni personalizzate

È possibile creare funzioni personalizzate in un file delle funzionalità del ruolo per semplificare attività complesse per gli utenti finali.
Le funzioni personalizzate sono utili anche quando è necessaria una logica di convalida avanzata per i valori dei parametri dei cmdlet.
È possibile scrivere funzioni semplici nel campo **FunctionDefinitions**:

```powershell
VisibleFunctions = 'Get-TopProcess'

FunctionDefinitions = @{
    Name = 'Get-TopProcess'

    ScriptBlock = {
        param($Count = 10)

        Get-Process | Sort-Object -Property CPU -Descending | Microsoft.PowerShell.Utility\Select-Object -First $Count
    }
}
```

> [!IMPORTANT]
> Non dimenticare di aggiungere il nome delle funzioni personalizzate per il campo **VisibleFunctions** in modo che possano essere eseguite dagli utenti JEA.


Il corpo (blocco di script) di funzioni personalizzate viene eseguito nella modalità linguaggio predefinita per il sistema e non è soggetto ai vincoli di linguaggio di JEA.
Ciò significa che le funzioni possono accedere al file system e al Registro di sistema ed eseguire comandi che non sono stati resi visibili nel file delle funzionalità del ruolo.
Evitare l'esecuzione di codice arbitrario quando si usano parametri ed evitare il piping dell'input dell'utente direttamente nei cmdlet, ad esempio `Invoke-Expression`.

Nell'esempio precedente, si noterà che è stato usato il nome del modulo qualificato completo (FQMN) `Microsoft.PowerShell.Utility\Select-Object`al posto della sintassi abbreviata`Select-Object`.
Le funzioni definite nei file delle funzionalità del ruolo sono comunque soggette all'ambito delle sessioni JEA, che include le funzioni proxy che JEA crea per vincolare i comandi esistenti.

Select-Object è un'impostazione predefinita, un cmdlet vincolato in tutte le sessioni JEA che non consente di selezionare le proprietà arbitrarie in oggetti.
Per usare Select-Object non vincolato in funzioni, è necessario richiedere in modo esplicito l'implementazione completa, specificando il nome FQMN.
Tutti i cmdlet vincolati in una sessione JEA hanno lo stesso comportamento se chiamati da una funzione, in linea con la [precedenza dei comandi](https://msdn.microsoft.com/en-us/powershell/reference/3.0/microsoft.powershell.core/about/about_command_precedence) di PowerShell.

Se si creano molte funzioni personalizzate, potrebbe risultare più facile inserirle in un [modulo di script di PowerShell](https://msdn.microsoft.com/en-us/library/dd878340(v=vs.85).aspx).
È possibile quindi rendere tali funzioni visibili nella sessione JEA tramite il campo VisibleFunctions, così come si farebbe con i moduli incorporati e di terze parti.

## <a name="place-role-capabilities-in-a-module"></a>Inserire le funzionalità del ruolo in un modulo

Per fare in modo che PowerShell trovi il file delle funzionalità del ruolo, è necessario inserire il file in una cartella "RoleCapabilities" in un modulo di PowerShell.
Il modulo può essere archiviato in qualsiasi cartella inclusa nella variabile di ambiente `$env:PSModulePath`, tuttavia non deve essere collocato in System32 (riservato per i moduli predefiniti) o in una cartella in cui gli utenti non attendibili che si connettono possano modificare i file.
Di seguito è riportato un esempio di creazione di un modulo di script di PowerShell di base denominato *ContosoJEA* nel percorso "Programmi".

```powershell
# Create a folder for the module
$modulePath = Join-Path $env:ProgramFiles "WindowsPowerShell\Modules\ContosoJEA"
New-Item -ItemType Directory -Path $modulePath

# Create an empty script module and module manifest. At least one file in the module folder must have the same name as the folder itself.
New-Item -ItemType File -Path (Join-Path $modulePath "ContosoJEAFunctions.psm1")
New-ModuleManifest -Path (Join-Path $modulePath "ContosoJEA.psd1") -RootModule "ContosoJEAFunctions.psm1"

# Create the RoleCapabilities folder and copy in the PSRC file
$rcFolder = Join-Path $modulePath "RoleCapabilities"
New-Item -ItemType Directory $rcFolder
Copy-Item -Path .\MyFirstJEARole.psrc -Destination $rcFolder
```

Per altre informazioni sui moduli di PowerShell, sui manifesti dei moduli e sulla variabile di ambiente PSModulePath, vedere [Understanding a PowerShell Module](https://msdn.microsoft.com/en-us/library/dd878324.aspx) (Informazioni sui moduli di PowerShell).

## <a name="updating-role-capabilities"></a>Aggiornamento delle funzionalità del ruolo


È possibile aggiornare un file delle funzionalità del ruolo in qualsiasi momento semplicemente salvando le modifiche.
Ogni nuova sessione JEA avviata dopo l'aggiornamento delle funzionalità del ruolo includerà le funzionalità modificate.

Per questo motivo il controllo dell'accesso alla cartella delle funzionalità del ruolo è molto importante.
Solo gli amministratori estremamente attendibili dovrebbero aver accesso per modificare i file delle funzionalità del ruolo.
Se un utente non attendibile può modificare i file delle funzionalità del ruolo, sarà in grado di ottenere accesso ai cmdlet che consentono di elevare i privilegi.


Gli amministratori che vogliono bloccare l'accesso alle funzionalità del ruolo devono assicurarsi che il sistema locale abbia accesso di lettura ai file delle funzionalità del ruolo e ai moduli inclusi.

## <a name="how-role-capabilities-are-merged"></a>Come vengono uniti le funzionalità del ruolo

È possibile concedere agli utenti accesso a più funzionalità del ruolo quando accedono a una sessione JEA a seconda dei mapping del ruolo nel [file di configurazione sessione](session-configurations.md).
In questo caso, JEA prova ad assegnare all'utente il set di comandi *più permissivo* consentito da uno dei ruoli.

**VisibleCmdlets e VisibleFunctions**

La logica di unione più complessa influisce su cmdlet e funzioni, che possono avere i parametri e i valori di parametro limitati in JEA.

Di seguito vengono definite le regole:

1. Se un cmdlet viene reso visibile solo in un ruolo, sarà visibile all'utente con i vincoli del parametro applicabile.
2. Se un cmdlet viene reso visibile in più di un ruolo e ogni ruolo ha gli stessi vincoli sul cmdlet, il cmdlet sarà visibile all'utente con tali vincoli.
3. Se un cmdlet viene reso visibile in più di un ruolo e ogni ruolo consente un set diverso di parametri, il cmdlet e tutti i parametri definiti in ogni ruolo saranno visibili all'utente. Se un ruolo non ha vincoli sui parametri, tutti i parametri saranno consentiti.
4. Se un ruolo definisce un set di convalida o un modello di convalida per un parametro di cmdlet e l'altro ruolo consente il parametro, ma non vincola i valori del parametro, il set di convalida o il modello verrà ignorato.
5. Se viene definito un set di convalida per lo stesso parametro del cmdlet in più di un ruolo, saranno consentiti tutti i valori da tutti i set di convalida.
6. Se viene definito un modello di convalida per lo stesso parametro del cmdlet in più di un ruolo, saranno consentiti tutti i valori che corrispondono ai modelli.
7. Se viene definito un set di convalida in uno o più ruoli e un modello di convalida è definito in un altro ruolo per lo stesso parametro del cmdlet, il set di convalida viene ignorato e si applica la regola (6) ai modelli di convalida rimanenti.

Di seguito è riportato un esempio di come i ruoli vengono uniti in base a queste regole:

```powershell
# Role A Visible Cmdlets
$roleA = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client' } }
}

# Role B Visible Cmdlets
$roleB = @{
    VisibleCmdlets = @{ Name = 'Get-Service'; Parameters = @{ Name = 'DisplayName'; ValidatePattern = 'DNS.*' } },
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Server' } }
}

# Resulting permisisons for a user who belongs to both role A and B
# - The constraint in role B for the DisplayName parameter on Get-Service is ignored becuase of rule #4
# - The ValidateSets for Restart-Service are merged because both roles use ValidateSet on the same parameter per rule #5
$mergedAandB = @{
    VisibleCmdlets = 'Get-Service',
                     @{ Name = 'Restart-Service'; Parameters = @{ Name = 'DisplayName'; ValidateSet = 'DNS Client', 'DNS Server' } }
}
```



**VisibleExternalCommands, VisibleAliases, VisibleProviders, ScriptsToProcess**

Tutti gli altri campi nel file delle funzionalità del ruolo vengono aggiunti a un set cumulativo di comandi esterni consentiti, alias, provider e script di avvio.
Qualsiasi comando, alias, provider o script disponibile in una funzionalità del ruolo sarà disponibile per l'utente JEA.

Accertarsi che il set combinato di provider da una sola funzionalità del ruoli e i cmdlet/funzioni/comandi da un'altra funzionalità non consentano agli utenti che si connettono di accedere non intenzionalmente alle risorse di sistema.
Ad esempio, se un ruolo consente l'uso del cmdlet `Remove-Item` e un altro il provider `FileSystem`, c'è il rischio che un utente JEA possa eliminare file arbitrari nel computer.
Altre informazioni sull'identificazione delle autorizzazioni effettive degli utenti sono disponibili nell'[argomento Controllo di JEA](audit-and-report.md).

## <a name="next-steps"></a>Passaggi successivi

- [Creare un file di configurazione sessione](session-configurations.md)