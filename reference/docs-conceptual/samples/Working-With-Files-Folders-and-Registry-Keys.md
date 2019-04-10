---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Uso di file, cartelle e chiavi del Registro di sistema
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: cd20cc50b573435ba80b52b51e164e60625dc1b6
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293096"
---
# <a name="working-with-files-folders-and-registry-keys"></a>Gestione di file, cartelle e chiavi del Registro di sistema

Windows PowerShell usa il sostantivo **Item** per fare riferimento agli elementi presenti in un'unità di Windows PowerShell. Nel caso del provider FileSystem di Windows PowerShell, il sostantivo **Item** può fare riferimento a un file, a una cartella o all'unità di Windows PowerShell. La visualizzazione e l'uso di questi elementi rappresentano attività di base fondamentali nella maggior parte delle impostazioni amministrative, quindi verranno descritte in dettaglio.

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a>Enumerazione di file, cartelle e chiavi del Registro di sistema (Get-ChildItem)

Poiché il recupero di una raccolta di elementi da una specifica posizione è un'attività molto comune, il cmdlet **Get-ChildItem** è stato progettato specificamente per restituire tutti gli elementi presenti in un contenitore, ad esempio una cartella.

Se si vuole restituire tutti i file e le cartelle contenuti direttamente nella cartella C:\\Windows, digitare:

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

L'elenco visualizzato è simile a quello che si otterrebbe immettendo il comando **dir** in **Cmd.exe** o il comando **ls** in una shell di comandi di UNIX.

È possibile ottenere elenchi molto complessi usando i parametri del cmdlet **Get-ChildItem**. Verranno esaminati alcuni scenari in seguito. È possibile visualizzare la sintassi del cmdlet **Get-ChildItem** digitando:

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

Questi parametri possono essere combinati in vari modi per ottenere un output estremamente personalizzato.

### <a name="listing-all-contained-items--recurse"></a>Visualizzazione di tutti gli elementi contenuti (-Recurse)

Per visualizzare sia gli elementi all'interno di una cartella di Windows sia quelli contenuti nelle sottocartelle, usare il parametro **Recurse** di **Get-ChildItem**. L'elenco visualizza tutto il contenuto della cartella di Windows e tutti gli elementi delle relative sottocartelle. Ad esempio:

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a>Filtraggio degli elementi per nome (-Name)

Per visualizzare solo i nomi degli elementi, usare il parametro **Name** di **Get-Childitem**:

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a>Visualizzazione forzata degli elementi nascosti (-Force)

Gli elementi che sono in genere invisibili in Esplora file o in Cmd.exe non vengono visualizzati nell'output di un comando **Get-ChildItem**. Per visualizzare gli elementi nascosti, usare il parametro **Force** di **Get-ChildItem**. Ad esempio:

```powershell
Get-ChildItem -Path C:\Windows -Force
```

Questo parametro si chiama Force perché è possibile eseguire forzatamente l'override del normale comportamento del comando **Get-ChildItem**. Force è un parametro ampiamente usato che forza un'azione che un cmdlet non eseguirebbe normalmente, anche se non esegue nessuna azione che comprometterebbe la sicurezza del sistema.

### <a name="matching-item-names-with-wildcards"></a>Ricerca di corrispondenze con i nomi degli elementi tramite caratteri jolly

Il comando **Get-ChildItem** accetta i caratteri jolly nel percorso degli elementi da elencare.

Poiché la corrispondenza tramite caratteri jolly viene gestita dal motore di Windows PowerShell, tutti i cmdlet che accettano caratteri jolly usano la stessa notazione e hanno lo stesso comportamento. La notazione dei caratteri jolly di Windows PowerShell include:

- L'asterisco (\*) trova la corrispondenza con zero o più occorrenze di qualsiasi carattere.

- Il punto interrogativo (?) trova la corrispondenza con un unico carattere.

- La parentesi quadra sinistra (\[) e quella destra (]) racchiudono un set di caratteri con cui trovare la corrispondenza.

Ecco alcuni esempi del funzionamento dei caratteri jolly.

Per trovare tutti i file nella directory Windows con il suffisso **.log** e un nome di base costituito esattamente da cinque caratteri, immettere il comando seguente:

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

Per trovare tutti i file che iniziano con la lettera **x** nella directory Windows, digitare:

```powershell
Get-ChildItem -Path C:\Windows\x*
```

Per trovare tutti i file che iniziano con **x** o **z**, digitare:

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a>Esclusione di elementi (-Exclude)

È possibile escludere elementi specifici usando il parametro **Exclude** di Get-ChildItem. In questo modo è possibile eseguire complesse operazioni di filtro in un'unica istruzione.

Si supponga ad esempio di voler trovare la DLL Windows Time Service nella cartella System32 e che non si ricordi il nome della DLL, ma solo che inizia con "W" e che contiene "32".

Con un'espressione come **w\&#42;32\&#42;.dll** sarà possibile trovare tutte le DLL che soddisfano le condizioni, ma i risultati potrebbero restituire anche le DLL di compatibilità di Windows per Windows 95 e Windows a 16 bit che includono "95" o "16" nei relativi nomi. È possibile omettere i file i cui nomi contengono questi numeri usando il parametro **Exclude** con il modello **\&#42;\[9516]\&#42;**:

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a>Combinazione di parametri Get-ChildItem

È possibile usare diversi parametri del cmdlet **Get-ChildItem** nello stesso comando. Prima di combinare i parametri, assicurarsi di comprendere la ricerca di corrispondenze con caratteri jolly. Ad esempio, il comando seguente non restituisce risultati:

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

Non ci sono risultati, nonostante ci siano due DLL che iniziano con la lettera "z" nella cartella Windows.

Il motivo è che nel percorso è stato specificato il carattere jolly. Anche se il comando è ricorsivo, il cmdlet **Get-ChildItem** restituisce solo gli elementi che si trovano nella cartella Windows e i cui nomi terminano con ".dll".

Per specificare una ricerca ricorsiva dei file i cui nomi corrispondono a un modello specifico, usare il parametro **-Include**.

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```