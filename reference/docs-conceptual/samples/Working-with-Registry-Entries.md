---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle voci del Registro di sistema
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401854"
---
# <a name="working-with-registry-entries"></a>Gestione delle voci del Registro di sistema

Poiché le voci del Registro di sistema sono proprietà di chiavi e, in quanto tali, non possono essere esplorate direttamente, è necessario adottare un approccio leggermente diverso per gestirle.

### <a name="listing-registry-entries"></a>Visualizzazione di un elenco di voci del Registro di sistema

Esistono molti modi diversi per esaminare le voci del Registro di sistema. Il modo più semplice consiste nell'ottenere i nomi di proprietà associati a una chiave. Ad esempio, per visualizzare i nomi delle voci nella chiave del Registro di sistema **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, usare **Get-Item**. Le chiavi del Registro di sistema hanno una proprietà con il nome generico "Property" che corrisponde a un elenco delle voci contenute al loro interno. Il comando seguente seleziona la proprietà Property ed espande gli elementi in modo che vengano visualizzati in un elenco:

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

Per visualizzare le voci del Registro di sistema in un formato più leggibile, usare **Get-ItemProperty**:

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

È possibile usare la notazione "**.**" per fare riferimento al percorso corrente. È possibile usare **Set-Location** per passare prima al contenitore del Registro di sistema **CurrentVersion**:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

In alternativa è possibile usare la proprietà predefinita HKLM PSDrive con **Set-Location**:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

È quindi possibile usare la notazione "**.**" del percorso corrente per elencare le proprietà senza specificare un percorso completo:

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

L'espansione del percorso funziona come nel file system, quindi da questo percorso è possibile ottenere l'elenco **ItemProperty** per **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** usando **Get-ItemProperty -Path ..\\Help**.

### <a name="getting-a-single-registry-entry"></a>Recupero di una singola voce del Registro di sistema

Per recuperare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili. In questo esempio viene trovato il valore di **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.

Usare **Get-ItemProperty** con il parametro **Path** per specificare il nome della chiave e il parametro **Name** per specificare il nome della voce **DevicePath**.

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

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
> Anche se **Get-ItemProperty** include i parametri **Filter**, **Include** ed **Exclude**, non è possibile usarli per applicare un filtro in base al nome di proprietà. Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi, e non a voci del Registro di sistema, che sono invece proprietà di elementi.

Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe. Per informazioni su reg.exe, digitare **reg.exe /?** al prompt dei comandi. Per trovare la voce DevicePath, usare reg.exe come illustrato nel comando seguente:

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

È anche possibile usare l'oggetto **WshShell COM** per trovare alcune voci del Registro di sistema, ma questo metodo non funziona con dati binari di grandi dimensioni o con nomi di voci del Registro di sistema che includono caratteri come "\\". Aggiungere il nome di proprietà al percorso dell'elemento con un separatore \\:

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a>Creazione di nuove voci del Registro di sistema

Per aggiungere una nuova voce denominata "PowerShellPath" alla chiave **CurrentVersion**, usare **New-ItemProperty** con il percorso della chiave e il nome e il valore della voce. Per questo esempio, verrà usato il valore della variabile **$PSHome** di Windows PowerShell, in cui è archiviato il percorso della directory di installazione di Windows PowerShell.

È possibile aggiungere la nuova voce alla chiave usando il comando seguente, che restituisce anche informazioni sulla nuova voce:

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
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
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

È anche possibile sovrascrivere un valore preesistente di una voce del Registro di sistema aggiungendo il parametro **Force** a qualsiasi comando **New-ItemProperty**.

### <a name="renaming-registry-entries"></a>Ridenominazione delle voci del Registro di sistema

Per rinominare la voce **PowerShellPath** in "PSHome", usare **Rename-ItemProperty**:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Per visualizzare il valore rinominato, aggiungere il parametro **PassThru** al comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a>Eliminazione di voci del Registro di sistema

Per eliminare le voci del Registro di sistema PSHome e PowerShellPath, usare **Remove-ItemProperty**:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```