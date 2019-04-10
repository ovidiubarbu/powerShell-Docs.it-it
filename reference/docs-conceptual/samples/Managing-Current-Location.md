---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione del percorso corrente
ms.assetid: a9f9e7a7-3ea8-47d3-bbb4-6e437f6d4a4a
ms.openlocfilehash: f5e0653b2c3bbc9d2526c7a1c2ff88a8a6641695
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293186"
---
# <a name="managing-current-location"></a>Gestione del percorso corrente

Nei sistemi di cartelle in Esplora file è in genere presente un percorso di lavoro specifico, ossia la cartella attualmente aperta. Per manipolare gli elementi della cartella, è sufficiente fare clic su di essi. Per le interfacce della riga di comando come Cmd.exe, quando ci si trova nella stessa cartella di un determinato file è possibile accedervi specificando un nome relativamente breve, invece dell'intero percorso del file. La directory corrente si chiama directory di lavoro.

Windows PowerShell usa il sostantivo **Location** per fare riferimento alla directory di lavoro e implementa una famiglia di cmdlet per esaminare e manipolare questo percorso.

## <a name="getting-your-current-location-get-location"></a>Recupero del percorso corrente (Get-Location)

Per determinare il percorso della directory corrente, immettere il comando **Get-Location**:

```
PS> Get-Location
Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Il cmdlet Get-Location è simile al comando **pwd** della shell BASH. Il cmdlet Set-Location è simile al comando **cd** di Cmd.exe.

## <a name="setting-your-current-location-set-location"></a>Impostazione del percorso corrente (Set-Location)

Il comando **Get-Location** viene usato con il comando **Set-Location**. Il comando **Set-Location** consente di specificare il percorso della directory corrente.

```powershell
Set-Location -Path C:\Windows
```

Dopo aver immesso il comando non si riceve nessun feedback diretto sul relativo effetto. La maggior parte dei comandi di Windows PowerShell che esegue un'azione produce un output nullo o irrilevante, perché non è sempre utile riceverlo. Per verificare se il cambio di directory è stato completato correttamente quando si immette il comando **Set-Location**, includere il parametro **-PassThru** insieme al comando **Set-Location**:

```
PS> Set-Location -Path C:\Windows -PassThru

Path
----
C:\WINDOWS
```

Il parametro **-PassThru** può essere usato con molti comandi Set in Windows PowerShell per restituire informazioni sul risultato nei casi in cui non ci sia un output predefinito.

È possibile specificare percorsi relativi al percorso corrente con la stessa procedura richiesta dalla maggior parte delle shell di comandi di UNIX e Windows. Nella notazione standard dei percorsi relativi un punto (**.**) rappresenta la cartella corrente e un doppio punto (**..**) rappresenta la directory padre del percorso corrente.

Ad esempio, nel percorso della cartella **C:\\Windows** un punto (**.**) rappresenta **C:\\Windows** e un doppio punto (**..**) rappresenta **C:**. Per passare dal percorso corrente alla radice dell'unità C:, digitare:

```
PS> Set-Location -Path .. -PassThru

Path
----
C:\
```

La stessa tecnica funziona nelle unità di Windows PowerShell diverse dalle unità di file system, ad esempio **HKLM:**. Per impostare il percorso sulla chiave \\Software nel Registro di sistema, digitare:

```
PS> Set-Location -Path HKLM:\SOFTWARE -PassThru

Path
----
HKLM:\SOFTWARE
```

È quindi possibile impostare il percorso sulla directory padre, che è la radice dell'unità HKLM: di Windows PowerShell usando un percorso relativo:

```
PS> Set-Location -Path .. -PassThru

Path
----
HKLM:\
```

È possibile digitare Set-Location o usare uno degli alias predefiniti di Windows PowerShell per Set-Location (cd, chdir, sl). Ad esempio:

```powershell
cd -Path C:\Windows
```

```powershell
chdir -Path .. -PassThru
```

```powershell
sl -Path HKLM:\SOFTWARE -PassThru
```

## <a name="saving-and-recalling-recent-locations-push-location-and-pop-location"></a>Salvataggio e richiamo dei percorsi recenti (Push-Location e Pop-Location)

Quando si cambia percorso, risulta utile tenere traccia del percorso precedente e avere la possibilità di tornarci. Il cmdlet **Push-Location** di Windows PowerShell crea una cronologia ordinata ("stack") dei percorsi di directory visitati ed è possibile risalire in questa cronologia usando il cmdlet complementare **Pop-Location**.

Ad esempio, Windows PowerShell viene in genere avviato nella home directory dell'utente.

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser
```

> [!NOTE]
> Il termine *stack* ha un significato speciale in molte impostazioni di programmazione, tra cui .NET Framework. L'ultimo elemento inserito nello stack è il primo che è possibile prelevare. L'aggiunta di un elemento allo stack si definisce normalmente con il termine "push". Il prelievo di un elemento dallo stack è invece noto come operazione "pop".

Per effettuare il push del percorso corrente nello stack e quindi passare alla cartella Local Settings, digitare:

```powershell
Push-Location -Path "Local Settings"
```

È quindi possibile effettuare il push del percorso Local Settings nello stack e passare alla cartella Temp digitando:

```powershell
Push-Location -Path Temp
```

Per verificare se il cambio di directory è stato effettuato, immettere il comando **Get-Location**:

```
PS> Get-Location

Path
----
C:\Documents and Settings\PowerUser\Local Settings\Temp
```

È quindi possibile prelevare la directory visitata più di recente immettendo il comando **Pop-Location** e verificare se il cambio è stato effettuato con il comando **Get-Location**:

```
PS> Pop-Location
PS> Get-Location

Path
----
C:\Documents and Settings\me\Local Settings
```

Come per il cmdlet **Set-Location**, è possibile includere il parametro **-PassThru** quando si immette il cmdlet **Pop-Location** per visualizzare la directory a cui si è passati:

```
PS> Pop-Location -PassThru

Path
----
C:\Documents and Settings\PowerUser
```

È possibile usare i cmdlet Location anche con i percorsi di rete. Se si ha un server denominato FS01 con una condivisione denominata Public, è possibile cambiare percorso digitando

```powershell
Set-Location \\FS01\Public
```

o

```powershell
Push-Location \\FS01\Public
```

È possibile usare i comandi **Push-Location** e **Set-Location** per passare a una delle unità disponibili. Ad esempio, se si ha un'unità CD-ROM locale con la lettera di unità D che contiene un CD dati, è possibile passare all'unità CD immettendo il comando **Set-Location D:**.

Se l'unità è vuota, verrà visualizzato il messaggio di errore seguente:

```
PS> Set-Location D:
Set-Location : Cannot find path 'D:\' because it does not exist.
```

Se si usa un'interfaccia della riga di comando, non è consigliabile usare Esplora file per esaminare le unità fisiche disponibili. Inoltre, Esplora file non visualizza tutte le unità di Windows PowerShell. Windows PowerShell prevede un set di comandi per manipolare le unità di Windows PowerShell, che verranno descritti in seguito.
