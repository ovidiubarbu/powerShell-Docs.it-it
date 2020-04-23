---
ms.date: 12/23/2019
keywords: powershell,cmdlet
title: Utilizzo delle chiavi del Registro di sistema
ms.openlocfilehash: 3feaf6d26db51a507434a6cec1f1095c9013efc8
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "75736846"
---
# <a name="working-with-registry-keys"></a>Utilizzo delle chiavi del Registro di sistema

Dato che le chiavi del Registro di sistema sono elementi nelle unità PowerShell, il loro uso è molto simile a quello di file e cartelle. Una differenza fondamentale è che ogni elemento in un'unità PowerShell basata sul Registro di sistema è un contenitore, come una cartella in un'unità del file system. Tuttavia, le voci del Registro di sistema e i relativi valori associati sono proprietà degli elementi e non elementi distinti.

## <a name="listing-all-subkeys-of-a-registry-key"></a>Elenco di tutte le sottochiavi di una chiave del Registro di sistema

È possibile visualizzare tutti gli elementi direttamente all'interno di una chiave del Registro di sistema usando `Get-ChildItem`. Aggiungere il parametro facoltativo **Force** per visualizzare elementi nascosti o di sistema. Questo comando, ad esempio, visualizza gli elementi direttamente all'interno dell'unità PowerShell `HKCU:`, che corrisponde all'hive del Registro di sistema `HKEY_CURRENT_USER`:

```powershell
Get-ChildItem -Path HKCU:\ | Select-Object Name
```

```Output
   Hive: Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER

Name
----
HKEY_CURRENT_USER\AppEvents
HKEY_CURRENT_USER\Console
HKEY_CURRENT_USER\Control Panel
HKEY_CURRENT_USER\DirectShow
HKEY_CURRENT_USER\dummy
HKEY_CURRENT_USER\Environment
HKEY_CURRENT_USER\EUDC
HKEY_CURRENT_USER\Keyboard Layout
HKEY_CURRENT_USER\MediaFoundation
HKEY_CURRENT_USER\Microsoft
HKEY_CURRENT_USER\Network
HKEY_CURRENT_USER\Printers
HKEY_CURRENT_USER\Software
HKEY_CURRENT_USER\System
HKEY_CURRENT_USER\Uninstall
HKEY_CURRENT_USER\WXP
HKEY_CURRENT_USER\Volatile Environment
```

Si tratta delle chiavi di primo livello visibili in `HKEY_CURRENT_USER` nell'editor del Registro di sistema (Regedit.exe).

È possibile specificare questo percorso del Registro di sistema anche specificando il nome del provider del Registro di sistema, seguito da `::`. Il nome completo del provider del Registro di sistema è `Microsoft.PowerShell.Core\Registry`, ma può essere abbreviato semplicemente in `Registry`. I comandi seguenti consentono di elencare il contenuto direttamente in `HKCU:`.

```powershell
Get-ChildItem -Path Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKEY_CURRENT_USER
Get-ChildItem -Path Registry::HKCU
Get-ChildItem -Path Microsoft.PowerShell.Core\Registry::HKCU
Get-ChildItem HKCU:
```

Questi comandi consentono di elencare solo gli elementi contenuti direttamente, in modo molto simile a `DIR` in **Cmd.exe** o `ls` in una shell UNIX. Per visualizzare gli elementi contenuti, è necessario specificare il parametro **Recurse**. Per elencare tutte le chiavi del Registro di sistema in `HKCU:`, usare il comando seguente.

```powershell
Get-ChildItem -Path HKCU:\ -Recurse
```

`Get-ChildItem` consente di applicare funzionalità di filtro complesse tramite i parametri **Path**, **Filter**, **Include** ed **Exclude**, ma questi parametri sono solitamente basati solo sul nome. È possibile eseguire operazioni di filtraggio complesse in base ad altre proprietà degli elementi usando il cmdlet `Where-Object`. Il comando seguente consente di trovare tutte le chiavi all'interno di `HKCU:\Software` che hanno non più di una sottochiave e hanno inoltre esattamente quattro valori:

```powershell
Get-ChildItem -Path HKCU:\Software -Recurse |
  Where-Object {($_.SubKeyCount -le 1) -and ($_.ValueCount -eq 4) }
```

## <a name="copying-keys"></a>Copia di chiavi

La copia viene eseguita con `Copy-Item`. Nell'esempio seguente viene copiata la sottochiave `CurrentVersion` di `HKLM:\SOFTWARE\Microsoft\Windows\` e tutte le relative proprietà in `HKCU:\`.

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU:
```

Se si esamina questa nuova chiave nell'editor del Registro di sistema o tramite `Get-ChildItem`, si noterà che nella nuova posizione non sono presenti copie delle sottochiavi contenute. Per copiare tutto il contenuto di un contenitore, è necessario specificare il parametro **Recurse**. Per rendere ricorsivo il comando di copia precedente, è possibile usare questo comando:

```powershell
Copy-Item -Path 'HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion' -Destination HKCU: -Recurse
```

Per eseguire copie nel file system, è comunque possibile continuare a usare altri strumenti già disponibili. In Windows PowerShell è possibile usare qualsiasi strumento di modifica del Registro di sistema, tra cui **reg.exe**, **regini.exe**, **regedit.exe** e gli oggetti COM che supportano la modifica del Registro di sistema, ad esempio **WScript.Shell** e la classe **StdRegProv** di WMI.

## <a name="creating-keys"></a>Creazione di chiavi

La creazione di nuove chiavi nel Registro di sistema è più semplice rispetto alla creazione di un nuovo elemento in un file system. Dato che tutte le chiavi del Registro di sistema sono contenitori, non è necessario specificare il tipo di elemento, ma è sufficiente indicare un percorso esplicito, ad esempio:

```powershell
New-Item -Path HKCU:\Software_DeleteMe
```

Per specificare una chiave, è anche possibile usare un percorso basato su provider:

```powershell
New-Item -Path Registry::HKCU\Software_DeleteMe
```

## <a name="deleting-keys"></a>Eliminazione di chiavi

L'eliminazione di elementi è un'attività fondamentalmente identica per tutti i provider. I comandi seguenti consentono di rimuovere elementi in modo invisibile all'utente:

```powershell
Remove-Item -Path HKCU:\Software_DeleteMe
Remove-Item -Path 'HKCU:\key with spaces in the name'
```

## <a name="removing-all-keys-under-a-specific-key"></a>Rimozione di tutte le chiavi in una chiave specifica

È possibile rimuovere gli elementi contenuti tramite `Remove-Item`, ma verrà richiesto di confermare la rimozione se l'elemento ne contiene altri. Ad esempio, se si tenta di eliminare la sottochiave `HKCU:\CurrentVersion` creata, verrà visualizzato il messaggio seguente:

```powershell
Remove-Item -Path HKCU:\CurrentVersion
```

```Output
Confirm
The item at HKCU:\CurrentVersion\AdminDebug has children and the -recurse
parameter was not specified. If you continue, all children will be removed with
the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
```

Per eliminare gli elementi contenuti senza che venga richiesta la conferma dell'eliminazione, specificare il parametro **Recurse**:

```powershell
Remove-Item -Path HKCU:\CurrentVersion -Recurse
```

Per rimuovere tutti gli elementi all'interno di `HKCU:\CurrentVersion` ma non lo stesso `HKCU:\CurrentVersion`, è invece possibile usare:

```powershell
Remove-Item -Path HKCU:\CurrentVersion\* -Recurse
```
