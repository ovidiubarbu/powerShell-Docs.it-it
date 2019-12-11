---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Gestione delle unità di Windows PowerShell
ms.openlocfilehash: 5d1aba459caeaab2542e17e74534da6713b0faa9
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "70215516"
---
# <a name="managing-windows-powershell-drives"></a>Gestione delle unità di Windows PowerShell

Un'*unità di Windows PowerShell* è un percorso di archivio dati a cui è possibile accedere come un'unità di file system in Windows PowerShell. I provider di Windows PowerShell creano automaticamente alcune unità, ad esempio le unità di file system (incluse C: e D:), le unità del Registro di sistema (HKCU: e HKLM:) e l'unità dei certificati (Cert:). È inoltre possibile creare unità di Windows PowerShell personalizzate. Queste unità sono molto utili, ma sono disponibili solo all'interno di Windows PowerShell. Non è possibile accedervi con altri strumenti di Windows, ad esempio Esplora file o Cmd.exe.

Windows PowerShell usa il sostantivo **PSDrive** per i comandi da usare con le unità di Windows PowerShell. Per visualizzare un elenco delle unità di Windows PowerShell presenti nella propria sessione di Windows PowerShell, usare il cmdlet **Get-PSDrive**.

```
PS> Get-PSDrive

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
Alias      Alias
C          FileSystem    C:\                                 ...And Settings\me
cert       Certificate   \
D          FileSystem    D:\
Env        Environment
Function   Function
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
Variable   Variable
```

Anche se le unità visualizzate variano in base a quelle disponibili nel sistema, l'elenco sarà simile all'output del comando **Get-PSDrive** illustrato sopra.

Le unità di file system sono un sottoinsieme delle unità di Windows PowerShell. È possibile identificarle dalla voce FileSystem nella colonna Provider. Le unità di file system di Windows PowerShell sono supportate dal provider FileSystem.

Per visualizzare la sintassi del cmdlet **Get-PSDrive**, digitare un comando **Get-Command** con il parametro **Syntax**:

```
PS> Get-Command -Name Get-PSDrive -Syntax

Get-PSDrive [[-Name] <String[]>] [-Scope <String>] [-PSProvider <String[]>] [-V
erbose] [-Debug] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-
OutVariable <String>] [-OutBuffer <Int32>]
```

Il parametro **PSProvider** consente di visualizzare solo le unità di Windows PowerShell supportate da uno specifico provider. Ad esempio, per visualizzare solo le unità di Windows PowerShell supportate dal provider FileSystem di Windows PowerShell, digitare il comando **Get-PSDrive** con il parametro **PSProvider** e il valore **FileSystem**:

```
PS> Get-PSDrive -PSProvider FileSystem

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
A          FileSystem    A:\
C          FileSystem    C:\                           ...nd Settings\PowerUser
D          FileSystem    D:\
```

Per visualizzare le unità di Windows PowerShell che rappresentano hive del Registro di sistema, usare il parametro **PSProvider** in modo da visualizzare solo le unità di Windows PowerShell supportate dal provider Registry di Windows PowerShell:

```
PS> Get-PSDrive -PSProvider Registry

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
HKCU       Registry      HKEY_CURRENT_USER
HKLM       Registry      HKEY_LOCAL_MACHINE
```

È anche possibile usare i cmdlet Location standard con le unità di Windows PowerShell:

```
PS> Set-Location HKLM:\SOFTWARE
PS> Push-Location .\Microsoft
PS> Get-Location

Path
----
HKLM:\SOFTWARE\Microsoft
```

## <a name="adding-new-windows-powershell-drives-new-psdrive"></a>Aggiunta di nuove unità di Windows PowerShell (New-PSDrive)

È possibile aggiungere unità di Windows PowerShell personalizzate tramite il comando **New-PSDrive**. Per ottenere la sintassi del comando **New-PSDrive**, immettere il comando **Get-Command** con il parametro **Syntax**:

```
PS> Get-Command -Name New-PSDrive -Syntax

New-PSDrive [-Name] <String> [-PSProvider] <String> [-Root] <String> [-Descript
ion <String>] [-Scope <String>] [-Credential <PSCredential>] [-Verbose] [-Debug
] [-ErrorAction <ActionPreference>] [-ErrorVariable <String>] [-OutVariable <St
ring>] [-OutBuffer <Int32>] [-WhatIf] [-Confirm]
```

Per creare una nuova unità di Windows PowerShell, è necessario specificare tre parametri:

- Il nome dell'unità (è possibile usare qualsiasi nome valido di Windows PowerShell)

- Il PSProvider (usare "FileSystem" per i percorsi del file system e "Registry" per i percorsi del Registro di sistema)

- La radice, ossia il percorso della radice della nuova unità

Ad esempio, è possibile creare un'unità denominata "Office" mappata alla cartella contenente le applicazioni Microsoft Office nel computer, ad esempio **C:\\Program Files\\Microsoft Office\\OFFICE11**. Per creare l'unità, digitare il comando seguente:

```
PS> New-PSDrive -Name Office -PSProvider FileSystem -Root "C:\Program Files\Microsoft Office\OFFICE11"

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
Office     FileSystem    C:\Program Files\Microsoft Offic...
```

> [!NOTE]
> In generale, per i percorsi non viene fatta distinzione tra maiuscole e minuscole.

È possibile fare riferimento alla nuova unità di Windows PowerShell come di consueto, ossia specificando il nome seguito da due punti ( **:** ).

Le unità di Windows PowerShell semplificano notevolmente molte attività. Ad esempio, alcune delle chiavi più importanti del Registro di sistema hanno percorsi estremamente lunghi, che sono complicati da accedere e difficili da ricordare. Le informazioni di configurazione critiche si trovano in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**. Per visualizzare e cambiare elementi nella chiave del Registro di sistema CurrentVersion, è possibile creare un'unità di Windows PowerShell la cui radice si trova in tale chiave digitando:

```
PS> New-PSDrive -Name cvkey -PSProvider Registry -Root HKLM\Software\Microsoft\Windows\CurrentVersion

Name       Provider      Root                                   CurrentLocation
----       --------      ----                                   ---------------
cvkey      Registry      HKLM\Software\Microsoft\Windows\...
```

È quindi possibile passare all'unità **cvkey:** come si farebbe per qualsiasi altra unità:

```
PS> cd cvkey:
```

oppure:

```
PS> Set-Location cvkey: -PassThru

Path
----
cvkey:\
```

Il cmdlet New-PsDrive aggiunge la nuova unità solo nella sessione corrente di Windows PowerShell. Se si chiude la finestra di Windows PowerShell, la nuova unità va persa. Per salvare un'unità di Windows PowerShell, usare il cmdlet Export-Console per esportare la sessione corrente di Windows PowerShell e quindi il parametro **PSConsoleFile** di PowerShell.exe per importarla. In alternativa, aggiungere la nuova unità nel proprio profilo Windows PowerShell.

## <a name="deleting-windows-powershell-drives-remove-psdrive"></a>Eliminazione di unità di Windows PowerShell (Remove-PSDrive)

Per eliminare unità da Windows PowerShell, è possibile usare il cmdlet **Remove-PSDrive**. Il cmdlet **Remove-PSDrive** è facile da usare. Per eliminare una specifica unità di Windows PowerShell, è sufficiente specificare il relativo nome.

Ad esempio, se è stata aggiunta l'unità **Office:** di Windows PowerShell, come illustrato nell'argomento **New-PSDrive**, è possibile eliminarla digitando:

```powershell
Remove-PSDrive -Name Office
```

Per eliminare l'unità **cvkey:** di Windows PowerShell, anch'essa illustrata nell'argomento **New-PSDrive**, usare il comando seguente:

```powershell
Remove-PSDrive -Name cvkey
```

Anche se l'eliminazione di unità è un'operazione facile, non è possibile eseguirla sulle unità al momento attive. Ad esempio:

```
PS> cd office:
PS Office:\> remove-psdrive -name office
Remove-PSDrive : Cannot remove drive 'Office' because it is in use.
At line:1 char:15
+ remove-psdrive  <<<< -name office
```

## <a name="adding-and-removing-drives-outside-windows-powershell"></a>Aggiunta e rimozione di unità all'esterno di Windows PowerShell

Windows PowerShell rileva le unità di file system aggiunte o rimosse da Windows, incluse le unità di rete mappate, le unità USB collegate e le unità eliminate con il comando **net use** o con i metodi **WScript.NetworkMapNetworkDrive** e **RemoveNetworkDrive** di uno script WSH (Windows Script Host).
