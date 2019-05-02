---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle voci del Registro di sistema
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086035"
---
# <a name="working-with-registry-entries"></a>Gestione delle voci del Registro di sistema

Poiché le voci del Registro di sistema sono proprietà di chiavi e, in quanto tali, non possono essere esplorate direttamente, è necessario adottare un approccio leggermente diverso per gestirle.

## <a name="listing-registry-entries"></a>Visualizzazione di un elenco di voci del Registro di sistema

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

È possibile usare la notazione `*.*` per fare riferimento al percorso corrente. È possibile usare `Set-Location` per passare prima al contenitore del Registro di sistema **CurrentVersion**:

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

In alternativa è possibile usare la proprietà predefinita HKLM PSDrive con `Set-Location`:

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

È quindi possibile usare la notazione `*.*` del percorso corrente per elencare le proprietà senza specificare un percorso completo:

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

L'espansione del percorso funziona come nel file system, quindi da questo percorso è possibile ottenere l'elenco **ItemProperty** per `HKLM:\SOFTWARE\Microsoft\Windows\Help` tramite `Get-ItemProperty -Path ..\Help`.

## <a name="getting-a-single-registry-entry"></a>Recupero di una singola voce del Registro di sistema

Per recuperare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili. In questo esempio viene trovato il valore di **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.

Usare `Get-ItemProperty` con il parametro **Path** per specificare il nome della chiave e il parametro **Name** per specificare il nome della voce **DevicePath**.

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
> Anche se `Get-ItemProperty` include i parametri **Filter**, **Include** ed **Exclude**, non è possibile usarli per applicare un filtro in base al nome di proprietà. Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi e non voci del Registro di sistema. Voci del Registro di sistema che corrispondono a proprietà di elementi.

Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe. Per informazioni su reg.exe, digitare `reg.exe /?` al prompt dei comandi. Per trovare la voce DevicePath, usare reg.exe come illustrato nel comando seguente:

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

È anche possibile usare l'oggetto COM **WshShell** per trovare alcune voci del Registro di sistema, ma questo metodo non funziona con dati binari di grandi dimensioni o con nomi di voci del Registro di sistema che includono caratteri come "\\". Aggiungere il nome di proprietà al percorso dell'elemento con un separatore \\:

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a>Impostazione di una singola voce del Registro di sistema

Per modificare una voce specifica di una chiave del Registro di sistema, è possibile usare uno dei diversi approcci disponibili. Questo esempio modificata voce **Path** in `HKEY_CURRENT_USER\Environment`. La voce **Path** specifica dove trovare i file eseguibili.

1. Recuperare il valore corrente della voce **Path** tramite `Get-ItemProperty`.
2. Aggiungere il nuovo valore, separandolo con `;`.
3. Usare `Set-ItemProperty` con la chiave, il nome della voce e il valore specificati per modificare la voce del Registro di sistema.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> Anche se `Set-ItemProperty` include i parametri **Filter**, **Include** ed **Exclude**, non è possibile usarli per applicare un filtro in base al nome di proprietà. Questi parametri fanno riferimento a chiavi del Registro di sistema, che sono percorsi di elementi, e non a voci del Registro di sistema, che sono invece proprietà di elementi.

Un'altra opzione consiste nell'usare lo strumento da riga di comando Reg.exe. Per informazioni su reg.exe, digitare **reg.exe /?**
al prompt dei comandi.

Nell'esempio seguente la voce **Path** viene modificata rimuovendo il percorso aggiunto nell'esempio precedente.
`Get-ItemProperty` viene ancora usato per recuperare il valore corrente per evitare la necessità di analizzare la stringa restituita da `reg query`. I metodi **SubString** e **LastIndexOf** vengono usati per recuperare l'ultimo percorso aggiunto alla voce **Path**.

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a>Creazione di nuove voci del Registro di sistema

Per aggiungere una nuova voce denominata "PowerShellPath" alla chiave **CurrentVersion**, usare `New-ItemProperty` con il percorso della chiave e il nome e il valore della voce. Per questo esempio, verrà usato il valore della variabile `$PSHome` di Windows PowerShell, in cui è archiviato il percorso della directory di installazione di Windows PowerShell.

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

È anche possibile sovrascrivere un valore preesistente di una voce del Registro di sistema aggiungendo il parametro **Force** a qualsiasi comando `New-ItemProperty`.

## <a name="renaming-registry-entries"></a>Ridenominazione delle voci del Registro di sistema

Per rinominare la voce **PowerShellPath** in "PSHome", usare `Rename-ItemProperty`:

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

Per visualizzare il valore rinominato, aggiungere il parametro **PassThru** al comando.

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a>Eliminazione di voci del Registro di sistema

Per eliminare le voci del Registro di sistema PSHome e PowerShellPath, usare `Remove-ItemProperty`:

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
