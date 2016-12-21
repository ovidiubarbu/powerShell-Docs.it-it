---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Utilizzo delle chiavi del Registro di sistema
ms.technology: powershell
ms.assetid: 91bfaecd-8684-48b4-ad86-065dfe6dc90a
ms.openlocfilehash: 8554bd1752ecddd87d70c2f31de357ce5da26ba5
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="working-with-registry-keys"></a>Utilizzo delle chiavi del Registro di sistema
Dato che le chiavi del Registro di sistema sono elementi nelle unità di Windows PowerShell, il loro utilizzo è molto simile a quello di file e cartelle. Una differenza fondamentale è che ogni elemento in un'unità di Windows PowerShell basata sul Registro di sistema è un contenitore, come una cartella in un'unità del file system. Tuttavia, le voci del Registro di sistema e i relativi valori associati sono proprietà degli elementi e non elementi distinti.

### <a name="listing-all-subkeys-of-a-registry-key"></a>Elenco di tutte le sottochiavi di una chiave del Registro di sistema
È possibile usare **Get-ChildItem** per visualizzare tutti gli elementi direttamente all'interno di una chiave del Registro di sistema. Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema. Questo comando, ad esempio, visualizza gli elementi direttamente all'interno dell'unità di Windows PowerShell HKCU:, che corrisponde all'hive del Registro di sistema HKEY_CURRENT_USER:

```
PS> Get-ChildItem -Path hkcu:\

   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

SKC  VC Name                           Property
---  -- ----                           --------
  2   0 AppEvents                      {}
  7  33 Console                        {ColorTable00, ColorTable01, ColorTab...
 25   1 Control Panel                  {Opened}
  0   5 Environment                    {APR_ICONV_PATH, INCLUDE, LIB, TEMP...}
  1   7 Identities                     {Last Username, Last User ...
  4   0 Keyboard Layout                {}
...
```

Si tratta delle chiavi di primo livello visibili in HKEY_CURRENT_USER nell'editor del Registro di sistema (Regedit.exe).

È possibile specificare questo percorso del Registro di sistema anche specificando il nome del provider del Registro di sistema, seguito da "**::**". Il nome completo del provider del Registro di sistema è **Microsoft.PowerShell.Core\\Registry**, ma può essere abbreviato semplicemente in **Registry**. I comandi seguenti consentono di elencare il contenuto direttamente in HKCU:

```
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Questi comandi consentono di elencare solo gli elementi contenuti direttamente, in modo molto simile al comando **DIR** di Cmd.exe o a **ls** in una shell UNIX. Per visualizzare gli elementi contenuti, è necessario specificare il parametro **Recurse**. Per elencare tutte le chiavi del Registro di sistema in HKCU, usare il comando seguente (questa operazione può richiedere tempi estremamente lunghi):

```
Get-ChildItem -Path hkcu:\ -Recurse
```

**Get-ChildItem** consente di applicare funzionalità di filtro complesse tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome. È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi tramite il cmdlet **Where-Object**. Il comando seguente consente di trovare tutte le chiavi all'interno di HKCU:\\Software che non hanno più di una sottochiave e hanno inoltre esattamente quattro valori:

```
Get-ChildItem -Path HKCU:\Software -Recurse | Where-Object -FilterScript {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

### <a name="copying-keys"></a>Copia di chiavi
La copia viene eseguita con **Copy-Item**. Il comando seguente copia HKLM:\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion e tutte le relative proprietà in HKCU:\\, creando una nuova chiave denominata "CurrentVersion":

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu:
```

Se si esamina questa nuova chiave nell'editor del Registro di sistema o tramite **Get-ChildItem**, si noterà che non sono disponibili copie delle sottochiavi contenute nella nuova posizione. Per copiare tutto il contenuto di un contenitore, è necessario specificare il parametro **Recurse**. Per rendere ricorsivo il comando di copia precedente, è possibile usare questo comando:

```
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination hkcu: -Recurse
```

Per eseguire copie nel file system, è comunque possibile continuare a usare altri strumenti già disponibili. È possibile usare dall'interno di Windows PowerShell qualsiasi strumento di modifica del Registro di sistema (tra cui reg.exe, regini.exe e regedit.exe) e gli oggetti COM che supportano la modifica del Registro di sistema (come WScript.Shell e la classe WMI StdRegProv).

### <a name="creating-keys"></a>Creazione di chiavi
La creazione di nuove chiavi nel Registro di sistema è più semplice rispetto alla creazione di un nuovo elemento in un file system. Dato che tutte le chiavi del Registro di sistema sono contenitori, non è necessario specificare il tipo di elemento, ma è sufficiente indicare un percorso esplicito, ad esempio:

```
New-Item -Path hkcu:\software_DeleteMe
```

Per specificare una chiave, è anche possibile usare un percorso basato su provider:

```
New-Item -Path Registry::HKCU_DeleteMe
```

### <a name="deleting-keys"></a>Eliminazione di chiavi
L'eliminazione di elementi è un'attività fondamentalmente identica per tutti i provider. I comandi seguenti consentono di rimuovere elementi in modo invisibile all'utente:

```
Remove-Item -Path hkcu:\Software_DeleteMe
Remove-Item -Path 'hkcu:\key with spaces in the name'
```

### <a name="removing-all-keys-under-a-specific-key"></a>Rimozione di tutte le chiavi in una chiave specifica
È possibile rimuovere gli elementi contenuti tramite **Remove-Item**, ma verrà richiesto di confermare la rimozione, se l'elemento contiene altri elementi. Ad esempio, se si tenta di eliminare la sottochiave HKCU:\\CurrentVersion creata, verrà visualizzato il messaggio seguente:

```
Remove-Item -Path hkcu:\CurrentVersion

Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
 the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

Per eliminare gli elementi contenuti senza che venga richiesta la conferma dell'eliminazione, specificare il parametro **-Recurse**:

```
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Per rimuovere tutti gli elementi all'interno di HKCU:\\CurrentVersion ma non la cartella HKCU:\\CurrentVersion stessa, è possibile invece usare:

```
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```

