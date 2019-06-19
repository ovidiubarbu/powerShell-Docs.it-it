---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Creazione di oggetti .NET e COM New Object
ms.openlocfilehash: 8bb0326d350be634a50897bdcd432e13ec93450c
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67030261"
---
# <a name="creating-net-and-com-objects-new-object"></a>Creazione di oggetti .NET e COM (New-Object)

Sono disponibili componenti software con interfacce .NET Framework e COM che consentono di eseguire molte attività di amministrazione di sistema. Windows PowerShell consente di usare questi componenti, in modo da non essere limitati alle attività eseguibili con i cmdlet. Molti dei cmdlet nella versione iniziale di Windows PowerShell non funzionano su computer remoti. Verrà illustrato come aggirare questa limitazione per la gestione dei registri eventi con la classe **System.Diagnostics.EventLog** di .NET Framework direttamente da Windows PowerShell.

## <a name="using-new-object-for-event-log-access"></a>Uso di New-Object per l'accesso ai registri eventi

La libreria di classi .NET Framework include una classe denominata **System.Diagnostics.EventLog** che può essere usata per gestire i registri eventi. È possibile creare una nuova istanza della classe di .NET Framework tramite il cmdlet **New-Object** con il parametro **TypeName**. Il comando seguente, ad esempio, crea un riferimento a un registro eventi:

```
PS> New-Object -TypeName System.Diagnostics.EventLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
```

Anche se il comando ha creato un'istanza della classe EventLog, l'istanza non include dati, perché non è stato specificato un registro eventi specifico. Come ottenere un registro eventi reale?

### <a name="using-constructors-with-new-object"></a>Uso dei costruttori con New-Object

Per fare riferimento a un registro eventi particolare, è necessario specificare il nome del registro. **New-Object** include il parametro **ArgumentList**. Gli argomenti passati come valori per questo parametro vengono usati da un metodo di avvio speciale dell'oggetto. Il metodo è chiamato *costruttore* perché viene usato per costruire l'oggetto. Ad esempio, per ottenere un riferimento al registro applicazioni, specificare la stringa 'Application' come argomento:

```
PS> New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application

Max(K) Retain OverflowAction        Entries Name
------ ------ --------------        ------- ----
16,384      7 OverwriteOlder          2,160 Application
```

> [!NOTE]
> Dato che la maggior parte delle classi principali di .NET Framework è contenuta nello spazio dei nomi System, Windows PowerShell tenterà automaticamente di trovare le classi specificate nello spazio dei nomi System se non viene trovata una corrispondenza per il nome di tipo specificato. Questo significa che è possibile specificare Diagnostics.EventLog invece di System.Diagnostics.EventLog.

### <a name="storing-objects-in-variables"></a>Archiviazione di oggetti nelle variabili

Può essere utile archiviare un riferimento a un oggetto, in modo da poterlo usare nella shell corrente. Anche se Windows PowerShell consente di eseguire numerose operazioni con le pipeline, riducendo la necessità di ricorrere alle variabili, in alcuni casi l'archiviazione di riferimenti agli oggetti nelle variabili rende più semplice la modifica di tali oggetti.

Windows PowerShell consente di creare variabili, che sono fondamentalmente oggetti denominati. L'output di qualsiasi comando di Windows PowerShell valido può essere archiviato in una variabile. I nomi di variabile iniziano sempre con il carattere $. Per archiviare il riferimento al registro applicazioni in una variabile denominata $AppLog, digitare il nome della variabile, seguito da un segno di uguale e quindi digitare il comando usato per creare l'oggetto registro applicazioni:

```
PS> $AppLog = New-Object -TypeName System.Diagnostics.EventLog -ArgumentList Application
```

Se poi si digita $AppLog, si noterà che contiene il registro applicazioni:

```
PS> $AppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
  16,384      7 OverwriteOlder          2,160 Application
```

### <a name="accessing-a-remote-event-log-with-new-object"></a>Accesso a un registro eventi remoto con New-Object

I comandi usati nella sezione precedente sono destinati al computer locale. Questa operazione può essere eseguita con il cmdlet **Get-EventLog**. Per accedere al registro applicazioni in un computer remoto, è necessario specificare sia il nome del registro che il nome (o indirizzo IP) di un computer come argomenti.

```
PS> $RemoteAppLog = New-Object -TypeName System.Diagnostics.EventLog Application,192.168.1.81
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder            262 Application
```

Dopo aver ottenuto un riferimento a un registro eventi archiviato nella variabile $RemoteAppLog, quali attività è possibile eseguire su di esso?

### <a name="clearing-an-event-log-with-object-methods"></a>Cancellazione di un registro eventi con i metodi degli oggetti

Gli oggetti spesso includono metodi che possono essere chiamati per eseguire attività. È possibile usare **Get-Member** per visualizzare i metodi associati a un oggetto. Il comando seguente e l'output selezionato mostrano alcuni dei metodi della classe EventLog:

```
PS> $RemoteAppLog | Get-Member -MemberType Method

   TypeName: System.Diagnostics.EventLog

Name                      MemberType Definition
----                      ---------- ----------
...
Clear                     Method     System.Void Clear()
Close                     Method     System.Void Close()
...
GetType                   Method     System.Type GetType()
...
ModifyOverflowPolicy      Method     System.Void ModifyOverflowPolicy(Overfl...
RegisterDisplayName       Method     System.Void RegisterDisplayName(String ...
...
ToString                  Method     System.String ToString()
WriteEntry                Method     System.Void WriteEntry(String message),...
WriteEvent                Method     System.Void WriteEvent(EventInstance in...
```

Il metodo **Clear ()** può essere usato per cancellare il registro eventi. Quando si chiama un metodo, è necessario far seguire sempre il nome del metodo dalle parentesi, anche se il metodo non richiede argomenti. In questo modo Windows PowerShell può distinguere tra il metodo e una proprietà potenziale con lo stesso nome. Digitare il comando seguente per chiamare il metodo **Clear**:

```
PS> $RemoteAppLog.Clear()
```

Digitare il comando seguente per visualizzare il log: Il risultato indica che il registro eventi è stato cancellato e ora ha 0 voci invece di 262:

```
PS> $RemoteAppLog

  Max(K) Retain OverflowAction        Entries Name
  ------ ------ --------------        ------- ----
     512      7 OverwriteOlder              0 Application
```

## <a name="creating-com-objects-with-new-object"></a>Creazione di oggetti COM con New-Object
È possibile usare **New-Object** per lavorare con componenti COM (Component Object Model). I componenti includono varie librerie incluse in Windows Script Host (WSH) e applicazioni ActiveX come Internet Explorer installate nella maggior parte dei sistemi.

**New-Object** usa Runtime Callable Wrapper di .NET Framework per creare oggetti COM, quindi esistono le stesse limitazioni valide per .NET Framework per la chiamata di oggetti COM. Per creare un oggetto COM, è necessario specificare il parametro **ComObject** con l'identificatore programmatico o *ProgId* della classe COM da usare. Una descrizione completa delle limitazioni per l'uso di COM e di come determinare i ProgId disponibili in un sistema esula dagli scopi di questo manuale dell'utente, ma la maggior parte degli oggetti noti da ambienti come WSH può essere usata all'interno di Windows PowerShell.

È possibile creare gli oggetti WSH specificando questi ProgID: **WScript.Shell**, **WScript.Network**, **Scripting.Dictionary** e **Scripting.FileSystemObject**. I comandi seguenti creano questi oggetti:

```powershell
New-Object -ComObject WScript.Shell
New-Object -ComObject WScript.Network
New-Object -ComObject Scripting.Dictionary
New-Object -ComObject Scripting.FileSystemObject
```

Anche se la maggior parte delle funzionalità di queste classi viene resa disponibile in altri modi in Windows PowerShell, alcune attività, come la creazione di collegamenti, sono ancora più semplici da eseguire usando le classi WSH.

## <a name="creating-a-desktop-shortcut-with-wscriptshell"></a>Creazione di un collegamento sul desktop con WScript.Shell

Un'attività che può essere eseguita rapidamente con un oggetto COM è la creazione di un collegamento. Si supponga di voler creare un collegamento sul desktop per la home directory di Windows PowerShell. È prima di tutto necessario creare un riferimento a **Wscript.Shell**, che verrà archiviato in una variabile denominata **$WshShell**:

```powershell
$WshShell = New-Object -ComObject WScript.Shell
```

Get-Member funziona con oggetti COM, quindi è possibile visualizzare i membri dell'oggetto digitando:

```
PS> $WshShell | Get-Member

   TypeName: System.__ComObject#{41904400-be18-11d3-a28b-00104bd35090}

Name                     MemberType            Definition
----                     ----------            ----------
AppActivate              Method                bool AppActivate (Variant, Va...
CreateShortcut           Method                IDispatch CreateShortcut (str...
...
```

**Get-Member** include un parametro facoltativo **InputObject** utilizzabile al posto dell'invio tramite pipe per fornire l'input a **Get-Member**. Si potrebbe ottenere lo stesso output di cui sopra usando il comando **Get-Member -InputObject $WshShell**. Se si usa **InputObject**, il relativo argomento viene gestito come singolo elemento. Questo significa che in presenza di più oggetti in una variabile, **Get-Member** li gestisce come una matrice di oggetti. Ad esempio:

```
PS> $a = 1,2,"three"
PS> Get-Member -InputObject $a
TypeName: System.Object[]
Name               MemberType    Definition
----               ----------    ----------
Count              AliasProperty Count = Length
...
```

Il metodo **WScript.Shell CreateShortcut** accetta un solo argomento, ovvero il percorso del file di collegamento da creare. È possibile digitare il percorso completo per il desktop, ma esiste un modo più semplice. Il desktop in genere è rappresentato da una cartella denominata Desktop all'interno della home directory dell'utente corrente. Windows PowerShell include una variabile **$Home** che contiene il percorso di questa cartella. È possibile specificare il percorso per la home directory usando questa variabile e quindi aggiungere il nome della cartella Desktop e il nome per il collegamento da creare digitando:

```powershell
$lnk = $WshShell.CreateShortcut("$Home\Desktop\PSHome.lnk")
```

Quando si usa un elemento che sembra un nome di variabile tra virgolette doppie, Windows PowerShell tenta la sostituzione di un valore corrispondente. Se si usano virgolette singole, Windows PowerShell non tenta di sostituire il valore della variabile. Ad esempio, provare a digitare i comandi seguenti:

```
PS> "$Home\Desktop\PSHome.lnk"
C:\Documents and Settings\aka\Desktop\PSHome.lnk
PS> '$Home\Desktop\PSHome.lnk'
$Home\Desktop\PSHome.lnk
```

Ora esiste una variabile denominata **$lnk** che contiene un riferimento al nuovo collegamento. Per visualizzarne tutti i membri, è possibile inviarla tramite pipe a **Get-Member**. L'output seguente mostra i membri che è necessario usare per completare la creazione del collegamento:

```
PS> $lnk | Get-Member
TypeName: System.__ComObject#{f935dc23-1cf0-11d0-adb9-00c04fd58a0b}
Name             MemberType   Definition
----             ----------   ----------
...
Save             Method       void Save ()
...
TargetPath       Property     string TargetPath () {get} {set}
```

È necessario specificare **TargetPath**, ovvero la cartella dell'applicazione per Windows PowerShell e quindi salvare il collegamento **$lnk** chiamando il metodo **Save**. Il percorso della cartella dell'applicazione Windows PowerShell è archiviato nella variabile **$PSHome**, quindi è possibile eseguire questa operazione digitando:

```powershell
$lnk.TargetPath = $PSHome
$lnk.Save()
```

## <a name="using-internet-explorer-from-windows-powershell"></a>Uso di Internet Explorer da Windows PowerShell

Molte applicazioni, compresa la famiglia di applicazioni Microsoft Office e Internet Explorer, possono essere automatizzate tramite COM. Internet Explorer dimostra alcune delle tecniche tipiche e dei problemi correlati all'uso delle applicazioni basate su COM.

Per creare un'istanza di Internet Explorer, è necessario specificare il ProgId di Internet Explorer, ovvero **InternetExplorer.Application**:

```powershell
$ie = New-Object -ComObject InternetExplorer.Application
```

Questo comando avvia Internet Explorer, ma non lo rende visibile. Se si digita Get-Process, si noterà che è in esecuzione un processo denominato iexplore. Infatti, se si esce da Windows PowerShell, l'esecuzione del processo continuerà. È necessario riavviare il computer o usare uno strumento come Gestione attività per terminare il processo iexplore.

> [!NOTE]
> Gli oggetti COM avviati come processo separato, comunemente noti come *eseguibili ActiveX*, potrebbero visualizzare o meno una finestra dell'interfaccia utente all'avvio. Se creano una finestra ma non la rendono visibile, come Internet Explorer, lo stato attivo passa in genere al desktop di Windows ed è necessario rendere visibile la finestra per poter interagire con essa.

È possibile digitare **$ie | Get-Member** per visualizzare le proprietà e i metodi per Internet Explorer. Per visualizzare la finestra di Internet Explorer, impostare la proprietà Visible su $true digitando:

```powershell
$ie.Visible = $true
```

È quindi possibile passare a un indirizzo Web specifico tramite il metodo Navigate:

```powershell
$ie.Navigate("http://www.microsoft.com/technet/scriptcenter/default.mspx")
```

È possibile recuperare contenuto di testo dalla pagina Web usando altri membri del modello a oggetti di Internet Explorer. Il comando seguente consente di visualizzare il testo HTML nel corpo della pagina Web corrente:

```powershell
$ie.Document.Body.InnerText
```

Per chiudere Internet Explorer da PowerShell, chiamare il metodo Quit():

```powershell
$ie.Quit()
```

Verrà così forzata la chiusura. La variabile $ie non contiene più un riferimento valido anche se risulta ancora essere un oggetto COM. Se si tenta di usarla, si otterrà un errore di automazione:

```
PS> $ie | Get-Member
Get-Member : Exception retrieving the string representation for property "Appli
cation" : "The object invoked has disconnected from its clients. (Exception fro
m HRESULT: 0x80010108 (RPC_E_DISCONNECTED))"
At line:1 char:16
+ $ie | Get-Member <<<<
```

È possibile rimuovere il riferimento rimanente con un comando come $ie = $null oppure rimuovere completamente la variabile digitando:

```powershell
Remove-Variable ie
```

> [!NOTE]
> Non esiste uno standard comune che stabilisce se gli eseguibili ActiveX devono essere interrotti o continuare l'esecuzione quando si rimuove un riferimento a uno di essi. L'applicazione può essere o meno chiusa a seconda delle circostanze, ad esempio se l'applicazione è visibile, se al suo interno è in esecuzione un documento modificato e persino se Windows PowerShell è ancora in esecuzione. Per questo motivo, è consigliabile testare il comportamento di terminazione per ogni eseguibile ActiveX da usare in Windows PowerShell.

## <a name="getting-warnings-about-net-framework-wrapped-com-objects"></a>Ottenere avvisi sugli oggetti COM con wrapping di .NET Framework

In alcuni casi, un oggetto COM potrebbe disporre di un *Runtime Callable Wrapper* (RCW) di .NET Framework associato e questo verrà usato da **New-Object**. Dato che il comportamento dell'RCW potrebbe essere diverso da quello del normale oggetto COM, **New-Object** include un parametro **Strict** per avvisare in caso di accesso a un RCW. Se si specifica il parametro **Strict** e poi si crea un oggetto COM che usa un RCW, viene visualizzato un messaggio di avviso:

```
PS> $xl = New-Object -ComObject Excel.Application -Strict
New-Object : The object written to the pipeline is an instance of the type "Mic
rosoft.Office.Interop.Excel.ApplicationClass" from the component's primary inte
rop assembly. If this type exposes different members than the IDispatch members
, scripts written to work with this object might not work if the primary intero
p assembly is not installed.
At line:1 char:17
+ $xl = New-Object  <<<< -ComObject Excel.Application -Strict
```

Anche se l'oggetto viene comunque creato, viene segnalato che non si tratta di un oggetto COM standard.
