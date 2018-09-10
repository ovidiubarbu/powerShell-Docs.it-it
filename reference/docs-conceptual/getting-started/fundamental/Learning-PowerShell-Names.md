---
ms.date: 08/24/2018
keywords: powershell,cmdlet
title: Imparare i nomi usati in PowerShell
ms.assetid: b4d0fd22-8298-4ee6-82ae-9b6f2907c986
ms.openlocfilehash: 44c66488a20c38d8528c92d753f6b32dda5a2dcb
ms.sourcegitcommit: c170a1608d20d3c925d79c35fa208f650d014146
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/31/2018
ms.locfileid: "43353267"
---
# <a name="learning-powershell-names"></a>Imparare i nomi usati in PowerShell

L'apprendimento dei nomi dei comandi e dei parametri richiede un notevole investimento di tempo con la maggior parte delle interfacce della riga di comando. Il problema è l'assenza di modelli generali. La memorizzazione è l'unico modo per apprendere i comandi e i parametri usati più di frequente.

Quando si usa un nuovo comando o parametro, non è sempre possibile usare gli elementi già noti. È necessario trovare e apprendere un nuovo nome. Normalmente, le interfacce della riga di comando iniziano con un piccolo set di strumenti e quindi crescono attraverso aggiunte incrementali. Per questo motivo, è facile comprendere come non vi sia una struttura standard.
Questo approccio sembra logico per i nomi di comando, poiché ogni comando è uno strumento separato. PowerShell usa un metodo migliore per gestire i nomi di comando.

## <a name="learning-command-names-in-traditional-shells"></a>Apprendimento dei nomi di comando nelle shell tradizionali

La maggior parte dei comandi serve per gestire elementi del sistema operativo o applicazioni, ad esempio servizi o processi. I comandi hanno nomi che possono o meno appartenere a una famiglia. Ad esempio, nei sistemi Windows è possibile usare i comandi `net start` e `net stop` per avviare e arrestare un servizio. **Sc.exe** è un altro strumento di controllo dei servizi per Windows. Questo nome non corrisponde al modello di denominazione per i comandi del servizio **net.exe**. Per la gestione dei processi, Windows offre il comando **tasklist.exe** per elencare i processi e il comando **taskkill.exe** per terminarli.

Inoltre, questi comandi prevedono specifiche irregolari per i parametri. Non è possibile usare il comando `net start` per avviare un servizio in un computer remoto. Il comando **sc.exe** può avviare un servizio in un computer remoto. Tuttavia, per specificare il computer remoto, è necessario aggiungere al nome un prefisso costituito da una doppia barra rovesciata. Per avviare il servizio spooler in un computer remoto denominato DC01, è necessario digitare `sc.exe \\DC01 start spooler`.
Per elencare le attività in esecuzione in DC01, usare il parametro **/S** e il nome del computer senza barre rovesciate. Ad esempio, `tasklist /S DC01`

> [!NOTE]
> Prima di PowerShell v6, `sc` era un alias per il cmdlet `Set-Content`. Per eseguire il comando **sc.exe**, è necessario includere l'estensione del file.

I servizi e i processi sono esempi di elementi gestibili in un computer che hanno cicli di vita ben definiti. Puoi avviare o arrestare i servizi e i processi oppure ottenere un elenco di tutti i servizi e i processi attualmente in esecuzione. Anche se vi sono importanti distinzioni di natura tecnica, le operazioni eseguite su servizi e processi sono concettualmente identiche. Inoltre, anche le scelte adottate per personalizzare un'operazione specificando parametri possono essere concettualmente simili.

Windows PowerShell sfrutta queste analogie per ridurre il numero di nomi diversi che è necessario ricordare per comprendere e usare i cmdlet.

## <a name="cmdlets-use-verb-noun-names-to-reduce-command-memorization"></a>Formato verbo-sostantivo per semplificare la memorizzazione dei cmdlet

PowerShell usa un sistema di denominazione nel formato "verbo-sostantivo". Ogni nome di cmdlet è costituito da un verbo standard separato con un trattino da un sostantivo. I verbi di PowerShell non sono sempre verbi inglesi, ma esprimono operazioni specifiche in PowerShell. I sostantivi sono parole con significati simili in qualsiasi altra lingua. I sostantivi descrivono tipi specifici di oggetti importanti nell'amministrazione del sistema. Osservando alcuni esempi, è facile notare come questi nomi in due parti semplifichino l'apprendimento.

PowerShell include un set consigliato di verbi standard. Ai sostantivi si applicano meno restrizioni, ma devono sempre descrivere l'elemento su cui agisce il verbo. PowerShell include comandi come `Get-Process`, `Stop-Process`, `Get-Service` e `Stop-Service`.

In questo esempio con due sostantivi e verbi la coerenza non semplifica troppo l'apprendimento. Estendendo questo elenco a un set standardizzato di 10 verbi e 10 sostantivi, i nomi da apprendere sono solo 20.
Tuttavia, questi termini possono essere combinati fino a formare 100 nomi di comando diversi.

È facile identificare l'operazione eseguita da un comando di PowerShell leggendone il nome. Il comando per arrestare un computer è `Stop-Computer`. Il comando per elencare tutti i computer in una rete è `Get-Computer`. Il comando per ottenere la data del sistema è `Get-Date`.

È possibile elencare tutti i comandi che includono un verbo specifico con il parametro **Verb** per `Get-Command`. Ad esempio, per visualizzare tutti i cmdlet che usano il verbo `Get`, digitare:

```
PS> Get-Command -Verb Get

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Acl                         Get-Acl [[-Path] <String[]>]...
Cmdlet          Get-Alias                       Get-Alias [[-Name] <String[]...
Cmdlet          Get-AuthenticodeSignature       Get-AuthenticodeSignature [-...
Cmdlet          Get-ChildItem                   Get-ChildItem [[-Path] <Stri...
...
```

Usare il parametro **Noun** per visualizzare una famiglia di comandi che agiscono sullo stesso tipo di oggetto. Ad esempio, eseguire il comando seguente per visualizzare i comandi disponibili per la gestione dei servizi:

```
PS> Get-Command -Noun Service

CommandType     Name                            Definition
-----------     ----                            ----------
Cmdlet          Get-Service                     Get-Service [[-Name] <String...
Cmdlet          New-Service                     New-Service [-Name] <String>...
Cmdlet          Restart-Service                 Restart-Service [-Name] <Str...
Cmdlet          Resume-Service                  Resume-Service [-Name] <Stri...
Cmdlet          Set-Service                     Set-Service [-Name] <String>...
Cmdlet          Start-Service                   Start-Service [-Name] <Strin...
Cmdlet          Stop-Service                    Stop-Service [-Name] <String...
Cmdlet          Suspend-Service                 Suspend-Service [-Name] <Str...
...
```

## <a name="cmdlets-use-standard-parameters"></a>Uso di parametri standard nei cmdlet

Come indicato in precedenza, i comandi usati nelle interfacce della riga di comando tradizionali non sempre hanno nomi di parametro coerenti. I parametri sono spesso parole a un carattere o abbreviate semplici da digitare, ma che non sono facili da comprendere per i nuovi utenti.

A differenza di molte altre interfacce della riga di comando tradizionali, PowerShell elabora direttamente i parametri e usa questo accesso diretto ai parametri insieme a indicazioni rivolte agli sviluppatori per la standardizzazione dei nomi di parametro. Queste indicazioni favoriscono ma non garantiscono la conformità di ogni cmdlet agli standard.

PowerShell standardizza anche il separatore di parametri. In un comando di PowerShell i nomi di parametro sono sempre preceduti da un carattere '-'. Prendere in considerazione gli esempi seguenti:

```powershell
Get-Command -Name Clear-Host
```

Il nome del parametro è **Name**, ma viene digitato come `-Name` quando viene usato nella riga di comando come parametro.

Ecco alcune delle caratteristiche generali relativi all'uso e ai nomi di parametro standard.

### <a name="the-help-parameter-"></a>Parametro Help (?)

Quando si specifica il parametro `-Help` o `-?` in qualsiasi cmdlet, PowerShell visualizza informazioni della Guida per il cmdlet. Il cmdlet non viene eseguito.

### <a name="common-parameters"></a>Parametri comuni

PowerShell include diversi *parametri comuni*. Questi parametri vengono controllati dal motore di PowerShell. I parametri comuni si comportano sempre allo stesso modo. I parametri comuni sono **WhatIf**, **Confirm**, **Verbose**, **Debug**, **Warn**, **ErrorAction**, **ErrorVariable**, **OutVariable** e **OutBuffer**.

### <a name="recommended-parameter-names"></a>Nomi di parametro consigliati

I cmdlet più importanti di PowerShell usano nomi standard per parametri simili. Anche se l'uso di questi nomi standard non è obbligatorio, esistono linee guida esplicite per favorire la standardizzazione.

Ad esempio, il nome consigliato per un parametro che fa riferimento a un computer è **ComputerName** anziché Server, Host, System, Node o altre alternative comuni. Altri importanti nomi di parametro consigliati sono **Force**, **Exclude**, **Include**, **PassThru**, **Path** e **CaseSensitive**.