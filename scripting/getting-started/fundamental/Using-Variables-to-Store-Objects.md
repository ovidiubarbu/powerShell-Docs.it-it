---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Uso di variabili per l&quot;archiviazione di oggetti
ms.technology: powershell
ms.assetid: b1688d73-c173-491e-9ba6-6d0c1cc852de
ms.openlocfilehash: 232296f8db3ea665fcdf14dfe4962b96d230d733
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="using-variables-to-store-objects"></a>Uso di variabili per l'archiviazione di oggetti
Windows PowerShell opera sugli oggetti. Windows PowerShell consente di creare variabili, fondamentalmente oggetti denominati, per salvare l'output in modo da portelo usare in seguito. Se si è abituati a usare le variabili in altre shell, tenere presente che le variabili di Windows PowerShell sono oggetti e non testo.

Le variabili vengono sempre specificate con il carattere iniziale $ e possono includere qualsiasi carattere alfanumerico o carattere di sottolineatura nei nomi.

### <a name="creating-a-variable"></a>Creazione di una variabile
È possibile creare una variabile digitando un nome di variabile valido:

```
PS> $loc
PS>
```

Non verrà restituito alcun risultato perché **$loc** non ha un valore. È possibile creare una variabile e assegnarle un valore nello stesso passaggio. Windows PowerShell crea la variabile solo se non esiste. In caso contrario, assegna il valore specificato alla variabile esistente. Per archiviare la posizione corrente nella variabile **$loc**, digitare:

```
$loc = Get-Location
```

Non viene visualizzato alcun output quando si digita il comando perché l'output viene inviato a $loc. In Windows PowerShell, l'output visualizzato è un effetto collaterale del fatto che i dati non indirizzati diversamente vengono sempre inviati allo schermo. Digitando $loc verrà visualizzata la posizione corrente:

```
PS> $loc

Path
----
C:\temp
```

È possibile usare **Get-Member** per visualizzare informazioni sul contenuto delle variabili. L'invio attraverso la pipe di $loc a Get-Member indicherà che si tratta di un oggetto **PathInfo**, proprio come l'output da Get-Location:

```
PS> $loc | Get-Member -MemberType Property

   TypeName: System.Management.Automation.PathInfo

Name         MemberType Definition
----         ---------- ----------
Drive        Property   System.Management.Automation.PSDriveInfo Drive {get;}
Path         Property   System.String Path {get;}
Provider     Property   System.Management.Automation.ProviderInfo Provider {...
ProviderPath Property   System.String ProviderPath {get;}
```

### <a name="manipulating-variables"></a>Manipolazione delle variabili
Windows PowerShell include diversi comandi per la manipolazione delle variabili. È possibile visualizzare un elenco completo in un formato leggibile digitando:

```
Get-Command -Noun Variable | Format-Table -Property Name,Definition -AutoSize -Wrap
```

Oltre alle variabili create nella sessione corrente di Windows PowerShell, esistono diverse variabili definite dal sistema. È possibile usare il cmdlet **Remove-Variable** per cancellare tutte le variabili non controllate da Windows PowerShell. Digitare il comando seguente per cancellare tutte le variabili:

```
Remove-Variable -Name * -Force -ErrorAction SilentlyContinue
```

Verrà restituito il prompt di conferma visualizzato di seguito.

```
Confirm
Are you sure you want to perform this action?
Performing operation "Remove Variable" on Target "Name: Error".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):A
```

Se si esegue poi il cmdlet **Get-Variable**, verranno visualizzate le variabili di Windows PowerShell rimanenti. Dato che esiste anche un'unità di Windows PowerShell per le variabili, è possibile visualizzare tutte le variabili di Windows PowerShell anche digitando:

```
Get-ChildItem variable:
```

### <a name="using-cmdexe-variables"></a>Uso delle variabili di Cmd.exe
Anche se Windows PowerShell non è Cmd.exe, viene eseguito in un ambiente della shell di comando e può usare le stesse variabili disponibili in qualsiasi ambiente in Windows. Queste variabili vengono esposte tramite un'unità denominata **env:**. È possibile visualizzare queste variabili digitando:

```
Get-ChildItem env:
```

Sebbene i cmdlet per le variabili standard non siano progettati per l'utilizzo con le variabili **env:**, è comunque possibile usarle specificando il prefisso **env:**. Per visualizzare la directory radice del sistema operativo, ad esempio, è possibile usare la variabile **%SystemRoot%** della shell dei comandi da Windows PowerShell digitando:

```
PS> $env:SystemRoot
C:\WINDOWS
```

È anche possibile creare e modificare le variabili di ambiente da Windows PowerShell. Le variabili di ambiente a cui si accede da Windows PowerShell rispettano le normali regole per le variabili di ambiente valide in altre posizioni in Windows.

