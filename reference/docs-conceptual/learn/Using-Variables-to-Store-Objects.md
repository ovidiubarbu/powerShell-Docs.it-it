---
ms.date: 08/27/2018
keywords: powershell,cmdlet
title: Uso di variabili per l'archiviazione di oggetti
ms.openlocfilehash: 2d20d84e48d3f68cab5c1ffa05d689b46415ebc8
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030364"
---
# <a name="using-variables-to-store-objects"></a>Uso di variabili per l'archiviazione di oggetti

PowerShell opera sugli oggetti. PowerShell permette di creare oggetti denominati noti come variabili.
I nomi delle variabili possono includere il carattere di sottolineatura e qualsiasi carattere alfanumerico. Se usata in PowerShell, una variabile viene sempre specificata tramite il carattere \$ seguito dal nome della variabile.

## <a name="creating-a-variable"></a>Creazione di una variabile

È possibile creare una variabile digitando un nome di variabile valido:

```
PS> $loc
PS>
```

Questo esempio non restituisce alcun risultato, perché `$loc` non ha un valore. È possibile creare una variabile e assegnarle un valore nello stesso passaggio. PowerShell crea la variabile solo se non esiste.
In caso contrario, assegna il valore specificato alla variabile esistente. L'esempio seguente archivia il percorso corrente nella variabile `$loc`:

```powershell
$loc = Get-Location
```

Quando si digita questo comando, PowerShell non visualizza alcun output. PowerShell invia l'output di "Get-Location" a `$loc`. In PowerShell i dati che non vengono assegnati o reindirizzati vengono inviati allo schermo. Se si digita `$loc`, viene visualizzato il percorso corrente:

```
PS> $loc

Path
----
C:\temp
```

È possibile usare `Get-Member` per visualizzare informazioni sul contenuto delle variabili. `Get-Member` mostra che `$loc` è un oggetto **PathInfo**, proprio come l'output di `Get-Location`:

```powershell
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

## <a name="manipulating-variables"></a>Modifica delle variabili

PowerShell include diversi comandi per la manipolazione delle variabili. È possibile visualizzare un elenco completo in un formato leggibile digitando:

```powershell
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

PowerShell crea anche diverse variabili definite dal sistema. È possibile usare il cmdlet `Remove-Variable` per rimuovere dalla sessione corrente le variabili che non sono controllate da PowerShell. Digitare il comando seguente per cancellare tutte le variabili:

```powershell
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Dopo aver eseguito il comando precedente, il cmdlet `Get-Variable` mostra le variabili di sistema di PowerShell.

PowerShell crea anche un'unità di variabili. Usare l'esempio seguente per visualizzare tutte le variabili di PowerShell usando l'unità delle variabili:

```powershell
Get-ChildItem variable:
```

## <a name="using-cmdexe-variables"></a>Uso di variabili di cmd.exe

PowerShell può usare le stesse variabili di ambiente disponibili per qualsiasi processo Windows, incluso **cmd.exe**. Queste variabili vengono esposte tramite un'unità denominata `env:`. È possibile visualizzare queste variabili digitando il comando seguente:

```powershell
Get-ChildItem env:
```

I cmdlet `*-Variable` standard non sono progettati per funzionare con variabili di ambiente. È possibile accedere alle variabili di ambiente usando il prefisso di unità `env:`. Ad esempio, la variabile **%SystemRoot%** in **cmd.exe** contiene il nome della directory radice del sistema operativo. In PowerShell è possibile usare `$env:SystemRoot` per accedere allo stesso valore.

```
PS> $env:SystemRoot
C:\WINDOWS
```

È anche possibile creare e modificare le variabili di ambiente da PowerShell. Le variabili di ambiente in PowerShell seguono le stesse regole per le variabili di ambiente usate altrove nel sistema operativo. L'esempio seguente crea una nuova variabile di ambiente:

```powershell
$env:LIB_PATH='/usr/local/lib'
```

Benché non sia necessario, spesso i nomi delle variabili di ambiente usano tutte lettere maiuscole.
