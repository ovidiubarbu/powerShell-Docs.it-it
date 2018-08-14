---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Rimozione di oggetti dalla pipeline Where Object
ms.assetid: 01df8b22-2d22-4e2c-a18d-c004cd3cc284
ms.openlocfilehash: c060b93a3823be26ad6c7757acc633bb4fc2fcfa
ms.sourcegitcommit: 01ac77cd0b00e4e5e964504563a9212e8002e5e0
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/07/2018
ms.locfileid: "39587143"
---
# <a name="removing-objects-from-the-pipeline-where-object"></a>Rimozione di oggetti dalla pipeline (Where-Object)

In Windows PowerShell spesso si generano e si passano più oggetti a una pipeline di quelli desiderati. È possibile specificare le proprietà di oggetti specifici da visualizzare usando i cmdlet **Format**, ma questo non consente di risolvere il problema della rimozione di interi oggetti dalla visualizzazione. Si consiglia di filtrare gli oggetti prima della fine di una pipeline, in modo da eseguire operazioni solo su un sottoinsieme degli oggetti generati inizialmente.

Windows PowerShell include un cmdlet `Where-Object` che consente di testare ogni oggetto nella pipeline e passarlo lungo la pipeline solo se soddisfa una specifica condizione di test. Gli oggetti che non superano il test vengono rimossi dalla pipeline. La condizione di test viene specificata sotto forma di valore del parametro `Where-Object` **FilterScript**.

### <a name="performing-simple-tests-with-where-object"></a>Esecuzione di test semplici con Where-Object

Il valore di **FilterScript** è un *blocco di script*, uno o più comandi di Windows PowerShell racchiusi tra parentesi graffe {}, che restituisce true o false. Questi blocchi di script possono essere molto semplici, ma per la loro creazione è richiesta familiarità con un altro concetto di Windows PowerShell, gli operatori di confronto. Un operatore di confronto mette a confronto gli elementi visualizzati alle sue due estremità. Gli operatori di confronto iniziano con un carattere "-" e sono seguiti da un nome. Gli operatori di confronto di base possono essere usati con qualsiasi tipo di oggetto. Quelli più avanzati potrebbero funzionare solo su testo o array.

> [!NOTE]
> Per impostazione predefinita, quando si lavora sul testo, gli operatori di confronto di Windows PowerShell non fanno distinzione tra maiuscole e minuscole.

In base a considerazioni a livello di analisi, i simboli come <, > e = non sono usati come operatori di confronto. Al contrario, gli operatori di confronto possono essere costituiti da lettere. Nella tabella seguente sono elencati gli operatori di confronto di base.

|Operatore di confronto|Significato|Esempio (restituisce true)|
|-----------------------|-----------|--------------------------|
|-eq|È uguale a|1 -eq 1|
|-ne|Non è uguale a|1 -ne 2|
|-lt|È minore di|1 -lt 2|
|-le|È minore o uguale a|1 -le 2|
|-gt|È maggiore di|2 -gt 1|
|-ge|È maggiore o uguale a|2 -ge 1|
|-like|Corrisponde (confronto con caratteri jolly per il testo)|"file.doc" -like "f\*.do?"|
|-notlike|Non corrisponde (confronto con caratteri jolly per il testo)|"file.doc" -notlike "p\*.doc"|
|-contains|Contiene|1,2,3 -contains 1|
|-notcontains|Non contiene|1,2,3 -notcontains 4|

I blocchi di script di Where-Object usano la variabile speciale `$_` per fare riferimento all'oggetto corrente nella pipeline. Di seguito è riportato un esempio del funzionamento. Se si ha un elenco di numeri e si vogliono restituire solo quelli minori di 3, è possibile usare Where-Object per filtrare i numeri digitando:

```
PS> 1,2,3,4 | Where-Object -FilterScript {$_ -lt 3}
1
2
```

### <a name="filtering-based-on-object-properties"></a>Filtro in base alle proprietà dell'oggetto

Dal momento che `$_` fa riferimento all'oggetto della pipeline corrente, è possibile accedere alle relative proprietà per i test.

È ad esempio possibile esaminare la classe Win32_SystemDriver in Strumentazione gestione Windows (WMI). Potrebbero esserci centinaia di driver di sistema in un determinato sistema, ma solo uno specifico set di driver di sistema potrebbe essere interessante, ad esempio quello dei driver attualmente in esecuzione. Se si usa Get-Member per visualizzare i membri di Win32_SystemDriver (**Get-WmiObject -Class Win32_SystemDriver | Get-Member -MemberType Property**), si noterà che la proprietà pertinente è State e che ha il valore "Running" quando il driver è in esecuzione. È possibile filtrare i driver di sistema selezionando solo quelli in esecuzione digitando:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq 'Running'}
```

Questa operazione genera comunque un lungo elenco. Si consiglia di applicare un filtro per selezionare solo i driver impostati per l'avvio automatico testando anche il valore StartMode:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Auto"}

DisplayName : RAS Asynchronous Media Driver
Name        : AsyncMac
State       : Running
Status      : OK
Started     : True

DisplayName : Audio Stub Driver
Name        : audstub
State       : Running
Status      : OK
Started     : True
```

Questa operazione produce numerose informazioni che non sono più necessarie poiché è noto che i driver sono in esecuzione. In effetti, le uniche informazioni che a questo punto risultano probabilmente necessarie sono il nome e il nome visualizzato. Il comando seguente include solo queste due proprietà, generando un output molto più semplice:

```
PS> Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript {$_.State -eq "Running"} | Where-Object -FilterScript {$_.StartMode -eq "Manual"} | Format-Table -Property Name,DisplayName

Name                                    DisplayName
----                                    -----------
AsyncMac                                RAS Asynchronous Media Driver
Fdc                                     Floppy Disk Controller Driver
Flpydisk                                Floppy Disk Driver
Gpc                                     Generic Packet Classifier
IpNat                                   IP Network Address Translator
mouhid                                  Mouse HID Driver
MRxDAV                                  WebDav Client Redirector
mssmbios                                Microsoft System Management BIOS Driver
```

Sono presenti due elementi Where-Object nel comando precedente, ma possono essere espressi con un unico elemento Where-Object usando l'operatore logico -and, come nell'esempio seguente:

```powershell
Get-WmiObject -Class Win32_SystemDriver | Where-Object -FilterScript { ($_.State -eq 'Running') -and ($_.StartMode -eq 'Manual') } | Format-Table -Property Name,DisplayName
```

Nella tabella seguente sono elencati gli operatori logici standard.

|Operatore logico|Significato|Esempio (restituisce true)|
|--------------------|-----------|--------------------------|
|-and|AND logico; true se i valori a entrambe le estremità sono true|(1 -eq 1) -and (2 -eq 2)|
|-or|OR logico; true se i valori a entrambe le estremità sono true|(1 -eq 1) -or (1 -eq 2)|
|-not|NOT logico; inverte true e false|-not (1 -eq 2)|
|\!|NOT logico; inverte true e false|\!(1 -eq 2)|
