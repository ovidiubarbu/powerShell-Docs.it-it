---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Ordinamento degli oggetti
ms.assetid: 8530caa8-3ed4-4c56-aed7-1295dd9ba199
ms.openlocfilehash: 06aa15d89888f1ecbe60b8e1dfb4efebb1d73673
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086052"
---
# <a name="sorting-objects"></a>Ordinamento degli oggetti

È possibile organizzare i dati visualizzati per semplificarne l'analisi usando il cmdlet `Sort-Object`. `Sort-Object` acquisisce il nome di una o più proprietà in base a cui ordinare i dati e li restituisce ordinati in base ai valori di tali proprietà.

## <a name="basic-sorting"></a>Ordinamento di base

Si consideri l'esigenza di elencare le sottodirectory e i file nella directory corrente.
Se si vuole ordinare in base a **LastWriteTime** e poi in base a **Name**, è possibile digitare:

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
11/6/2017 10:10:11 AM  .localization-config
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:15 AM  tests
6/6/2018 7:58:59 PM    CONTRIBUTING.md
6/6/2018 7:58:59 PM    README.md
...
```

È anche possibile ordinare gli oggetti in ordine inverso, specificando il parametro **Descending**.

```powershell
Get-ChildItem |
  Sort-Object -Property LastWriteTime, Name -Descending |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  reference
12/1/2018 10:13:50 PM  dsc
...
6/6/2018 7:58:59 PM    README.md
6/6/2018 7:58:59 PM    CONTRIBUTING.md
11/6/2017 10:10:15 AM  tests
11/6/2017 10:10:11 AM  ThirdPartyNotices
11/6/2017 10:10:11 AM  LICENSE-CODE
11/6/2017 10:10:11 AM  LICENSE
11/6/2017 10:10:11 AM  appveyor.yml
11/6/2017 10:10:11 AM  .openpublishing.build.ps1
11/6/2017 10:10:11 AM  .localization-config
```

## <a name="using-hash-tables"></a>Uso di tabelle hash

È possibile ordinare diversamente proprietà diverse usando le tabelle hash in una matrice.
Ogni tabella hash usa una chiave **Expression** per specificare il nome della proprietà e una chiave **Ascending** o **Descending** per specificare l'ordinamento `$true` o `$false`.
La chiave **Expression** è obbligatoria.
La chiave **Ascending** o **Descending** è facoltativa.

Nell'esempio seguente gli oggetti vengono ordinati in base a **LastWriteTime** (in ordine decrescente) e in base a **Name** (in ordine crescente).

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = 'LastWriteTime'; Descending = $true }, @{ Expression = 'Name'; Ascending = $true } |
  Format-Table -Property LastWriteTime, Name
```

```output
LastWriteTime          Name
-------------          ----
12/1/2018 10:13:50 PM  dsc
12/1/2018 10:13:50 PM  reference
11/29/2018 6:56:01 PM  .openpublishing.redirection.json
11/29/2018 6:56:01 PM  gallery
11/24/2018 10:33:22 AM developer
11/20/2018 7:22:19 PM  .markdownlint.json
...
```

È anche possibile impostare un blocco di script sulla chiave **Expression**.
Quando si esegue il cmdlet `Sort-Object` viene eseguito il blocco di script e il risultato viene usato per l'ordinamento.

L'esempio seguente dispone gli oggetti in ordine decrescente in base all'intervallo di tempo intercorso tra **CreationTime** e **LastWriteTime**.

```powershell
Get-ChildItem |
  Sort-Object -Property @{ Expression = { $_.LastWriteTime - $_.CreationTime }; Descending = $true } |
  Format-Table -Property LastWriteTime, CreationTime
```

```output
LastWriteTime          CreationTime
-------------          ------------
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
12/1/2018 10:13:50 PM  11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:11 AM
11/7/2018 6:52:24 PM   11/6/2017 10:10:15 AM
11/3/2018 9:58:17 AM   11/6/2017 10:10:11 AM
10/26/2018 4:50:21 PM  11/6/2017 10:10:11 AM
11/17/2018 1:10:57 PM  11/29/2017 5:48:30 PM
11/12/2018 6:29:53 PM  12/7/2017 7:57:07 PM
...
```

## <a name="tips"></a>Suggerimenti

È possibile omettere il nome del parametro **Property** come indicato di seguito:

```powershell
Sort-Object LastWriteTime, Name
```

È anche possibile fare riferimento a `Sort-Object` tramite il relativo alias predefinito, `sort`:

```powershell
sort LastWriteTime, Name
```

Le chiavi nelle tabelle hash per l'ordinamento possono essere abbreviate come segue:

```powershell
Sort-Object @{ e = 'LastWriteTime'; d = $true }, @{ e = 'Name'; a = $true }
```

In questo esempio **e** rappresenta **Expression**, **d** indica **Descending** e **a** **Ascending**.

Per migliorare la leggibilità, è possibile inserire le tabelle hash in una variabile separata:

```powershell
$order = @(
  @{ Expression = 'LastWriteTime'; Descending = $true }
  @{ Expression = 'Name'; Ascending = $true }
)

Get-ChildItem |
  Sort-Object $order |
  Format-Table LastWriteTime, Name
```