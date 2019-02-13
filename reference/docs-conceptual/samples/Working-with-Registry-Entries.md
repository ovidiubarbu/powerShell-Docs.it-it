---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle voci del Registro di sistema
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 8483b6f98739697b24a13055dfffbc7b5bacc2cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55681542"
---
# <a name="working-with-registry-entries"></a>Gestione delle voci del Registro di sistema

Poiché le voci del Registro di sistema sono proprietà di chiavi e, in quanto tali, non possono essere esplorate direttamente, è necessario adottare un approccio leggermente diverso per gestirle.

### <a name="listing-registry-entries"></a>Visualizzazione di un elenco di voci del Registro di sistema

Esistono molti modi diversi per esaminare le voci del Registro di sistema. Il modo più semplice consiste nell'ottenere i nomi di proprietà associati a una chiave. Ad esempio, per visualizzare i nomi delle voci nella chiave del Registro di sistema `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, usare `Get-Item`. Le chiavi del Registro di sistema hanno una proprietà con il nome generico "Property" che corrisponde a un elenco delle voci contenute al loro interno.
Il comando seguente seleziona la proprietà Property ed espande gli elementi in modo che vengano visualizzati in un elenco:

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Per visualizzare le voci del Registro di sistema in un formato più leggibile, usare `Get-ItemProperty`:

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

Le proprietà correlate a Windows PowerShell per la chiave sono precedute tutte dal prefisso "PS", ad esempio **PSPath**, **PSParentPath**, **PSChildName** e **PSProvider**.

È possibile usare la notazione "`*.*`." per fare riferimento al percorso corrente. È possibile usare `Set-Location` per modificare il **CurrentVersion** contenitore del Registro di sistema prima:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

In alternativa, è possibile usare la proprietà predefinita HKLM PSDrive con `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

È quindi possibile usare la notazione "`*.*`." del percorso corrente per elencare le proprietà senza specificare un percorso completo:

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

Espansione di percorso funziona allo stesso modo che nel file system, in modo da questo percorso è possibile ottenere il **ItemProperty** listato `HKLM:\SOFTWARE\Microsoft\Windows\Help` usando `Get-ItemProperty -Path ..\Help`.

### <a name="getting-a-single-registry-entry"></a>Recupero di una singola voce del Registro di sistema

Per recuperare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili. In questo esempio viene trovato il valore di **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Usando `Get-ItemProperty`, usare il **percorso** parametro per specificare il nome della chiave e il **nome** parametro per specificare il nome del **DevicePath** voce.

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

Questo comando restituisce le proprietà standard di Windows PowerShell oltre alla proprietà **DevicePath**.

> [!NOTE]
> Sebbene `Get-ItemProperty` ha **filtro**, **inclusione**, e **escludere** parametri, non possono essere usati per filtrare in base al nome della proprietà. Questi parametri fanno riferimento alle chiavi del Registro di sistema, quali sono i percorsi degli elementi e non le voci del Registro di sistema. Voci del Registro di sistema che sono proprietà degli elementi.

Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe. Per informazioni su reg.exe, digitare `reg.exe /?` un prompt dei comandi. Per trovare la voce DevicePath, usare reg.exe come illustrato nel comando seguente:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

È anche possibile usare l'oggetto **WshShell COM** per trovare alcune voci del Registro di sistema, ma questo metodo non funziona con dati binari di grandi dimensioni o con nomi di voci del Registro di sistema che includono caratteri come "\\". Aggiungere il nome di proprietà al percorso dell'elemento con un separatore \\:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

### <a name="setting-a-single-registry-entry"></a>L'impostazione di una voce del Registro di sistema Single

Se si desidera modificare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci possibili. Questo esempio viene modificata la **tracciato** voce sotto `HKEY_CURRENT_USER\Environment`. Il **percorso** voce specifica dove trovare i file eseguibili.

1. Recuperare il valore corrente del **tracciato** voce usando `Get-ItemProperty`.
2. Aggiungere il nuovo valore, separandolo con una `;`.
3. Usare `Set-ItemProperty` con la chiave specificata, nome e valore per modificare la voce del Registro di sistema.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Sebbene `Set-ItemProperty` ha **filtro**, **inclusione**, e **escludere** parametri, non possono essere usati per filtrare in base al nome della proprietà. Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi, e non a voci del Registro di sistema, che sono invece proprietà di elementi.

Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe. Per informazioni su reg.exe, digitare **reg.exe /?**
al prompt dei comandi.

Nell'esempio seguente il **percorso** voce rimuovendo il percorso aggiunto nell'esempio precedente.
`Get-ItemProperty` viene ancora usato per recuperare il valore corrente per evitare la necessità di analizzare la stringa restituita dal `reg query`. Il **sottostringa** e **LastIndexOf** vengono utilizzati metodi per recuperare l'ultimo percorso aggiunto per il **percorso** voce.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

### <a name="creating-new-registry-entries"></a>Creazione di nuove voci del Registro di sistema

Per aggiungere una nuova voce denominata "PowerShellPath" per il **CurrentVersion** l'uso delle chiavi, `New-ItemProperty` con il percorso della chiave, il nome della voce e il valore della voce. In questo esempio verrà usato il valore della variabile di Windows PowerShell `$PSHome`, cui è archiviato il percorso della directory di installazione di Windows PowerShell.

È possibile aggiungere la nuova voce alla chiave usando il comando seguente, che restituisce anche informazioni sulla nuova voce:

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

**PropertyType** deve essere il nome di un membro dell'enumerazione **Microsoft.Win32.RegistryValueKind** della tabella seguente:

|Valore di PropertyType|Significato|
|----------------------|-----------|
|Binary|Dati binari|
|DWord|Numero che corrisponde a un valore UInt32 valido|
|ExpandString|Stringa che può contenere variabili di ambiente espanse dinamicamente|
|MultiString|Stringa su più righe|
|String|Qualsiasi valore di stringa|
|QWord|8 byte di dati binari|

> [!NOTE]
> È possibile aggiungere una voce del Registro di sistema in più posizioni specificando una matrice di valori nel parametro **Path**:

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

È anche possibile sovrascrivere un valore preesistente di voce del Registro di sistema aggiungendo il **Force** parametro per qualsiasi `New-ItemProperty` comando.

### <a name="renaming-registry-entries"></a>Ridenominazione delle voci del Registro di sistema

Per rinominare la **PowerShellPath** voce in "PSHome", usare `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Per visualizzare il valore rinominato, aggiungere il parametro **PassThru** al comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Eliminazione di voci del Registro di sistema

Per eliminare le voci del Registro di sistema PSHome e PowerShellPath, usare `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
