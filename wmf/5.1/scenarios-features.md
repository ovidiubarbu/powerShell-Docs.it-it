---
title: "Nuovi scenari e funzionalità in WMF 5.1 (anteprima)"
ms.date: 2016-07-13
keywords: PowerShell, DSC, WMF
description: 
ms.topic: article
author: keithb
manager: dongill
ms.prod: powershell
ms.technology: WMF
translationtype: Human Translation
ms.sourcegitcommit: 57049ff138604b0e13c8fd949ae14da05cb03a4b
ms.openlocfilehash: 01d7ac9815a8650f36150e36b4f6942f451dc368

---

# Nuovi scenari e funzionalità in WMF 5.1 (anteprima) #

> Nota: queste informazioni sono provvisorie e soggette a modifiche.

## Edizioni di PowerShell ##
A partire dalla versione 5.1, PowerShell è disponibile in diverse edizioni che indicano vari set di funzionalità e compatibilità della piattaforma.

- **Desktop Edition:** è basata su .NET Framework e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint complete di Windows, ad esempio Server Core e Windows Desktop.
- **Core Edition:** è basata su .NET Core e fornisce compatibilità con script e moduli destinati a versioni di PowerShell che eseguono edizioni footprint ridotte di Windows, ad esempio Nano Server e Windows IoT.

**Altre informazioni sull'uso delle edizioni di PowerShell**
- [Determinare l'edizione di PowerShell in esecuzione]()
- [Dichiarare la compatibilità di un modulo con versioni specifiche di PowerShell]()
- [Filtrare i risultati di Get-Module in base a CompatiblePSEditions]()
- [Impedire l'esecuzione di script a meno che non vengano eseguiti in un'edizione compatibile di PowerShell]()

## Cmdlet di catalogo  

Sono stati aggiunti due nuovi cmdlet nel modulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx); questi generano e convalidano i file di catalogo di Windows.  

###New-FileCatalog 
--------------------------------

New-FileCatalog crea un file di catalogo Windows per gruppi di cartelle e file. Questo file di catalogo contiene gli hash per tutti i file nei percorsi specificati. Gli utenti possono distribuire il gruppo di cartelle con il corrispondente file di catalogo che rappresenta le cartelle. Queste informazioni sono utili per convalidare se sono state apportate modifiche alle cartelle dall'ora di creazione del catalogo.    

```PowerShell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Sono supportate le versioni 1 e 2 del catalogo. La versione 1 usa l'algoritmo di hash SHA1 per creare hash di file; la versione 2 usa SHA256. La versione 2 del catalogo non è supportata in *Windows Server 2008 R2* e in *Windows 7*. È necessario usare la versione 2 del catalogo su *Windows 8*, *Windows Server 2012* e sistemi operativi successivi.  

![](../../images/NewFileCatalog.jpg)

Questa operazione crea il file di catalogo. 

![](../../images/CatalogFile1.jpg)  

![](../../images/CatalogFile2.jpg) 

Per verificare l'integrità dei file di catalogo (Pester.cat nell'esempio precedente), accedere tramite il cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).   


###Test-FileCatalog 
--------------------------------

Test-FileCatalog convalida il catalogo che rappresenta un gruppo di cartelle. 

```PowerShell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../../images/TestFileCatalog.jpg)

Questo cmdlet confronta tutti gli hash di file e i relativi percorsi trovati nel *catalogo* con altri sul *disco*. Se rileva eventuali mancate corrispondenze tra i percorsi e gli hash di file restituisce lo stato *ValidationFailed*. Gli utenti possono recuperare tutte queste informazioni aggiungendo il parametro *-Detailed* al cmdlet. Visualizza inoltre lo stato di accesso al catalogo nel campo *Firma* che è equivalente alla chiamata del cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) nel file di catalogo. Gli utenti possono inoltre ignorare alcuni file durante la convalida usando il parametro *- FilesToSkip*. 


## Modulo Analysis Cache ##
A partire da WMF 5.1, PowerShell fornisce il controllo sul file che viene usato per memorizzare nella cache i dati relativi a un modulo, ad esempio i comandi esportati.

Per impostazione predefinita, questa cache è archiviata nel file `${env:LOCALAPPDATA}\Microsoft\Windows\PowerShell\ModuleAnalysisCache`.
La cache viene in genere letta all'avvio durante la ricerca di un comando e viene scritta in un thread in background ad un certo punto dopo l'importazione di un modulo.

Per modificare il percorso predefinito della cache, impostare la variabile di ambiente PSModuleAnalysisCachePath prima di avviare PowerShell. Le modifiche apportate a questa variabile di ambiente influiranno solo sui processi figlio.
Il valore deve denominare un percorso completo (nome di file incluso) per il quale PowerShell dispone dell'autorizzazione per creare e scrivere file.
Per disabilitare la cache del file, impostare questo valore su un percorso non valido, ad esempio:

```PowerShell
$env:PSModuleAnalysisCachePath = 'nul'
```

Questo imposta il percorso su un dispositivo non valido. Se PowerShell non riesce a scrivere nel percorso, non verrà restituito alcun errore. Sarà tuttavia possibile visualizzare una segnalazione errori mediante un'utilità di traccia:

```PowerShell
Trace-Command -PSHost -Name Modules -Expression { Import-Module Microsoft.PowerShell.Management -Force }
```

Quando si scrive nella cache, PowerShell controllerà i moduli non più disponibili per evitare di aumentare inutilmente le dimensioni della cache.
Talvolta questi controlli non sono consigliabili. In questo caso, è possibile disattivarli impostando

```PowerShell
$env:PSDisableModuleAnalysisCacheCleanup = 1
```

L'impostazione di questa variabile di ambiente avrà effetto immediato nel processo corrente.

##Specifica della versione del modulo

In WMF 5.1 `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell. In precedenza, non era possibile specificare una versione particolare del modulo. Se erano presenti più versioni, veniva restituito un errore.


In WMF 5.1:

* L'utente può usare la [tabella hash](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx) `ModuleSpecification`. Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`.

**Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore. Comportamento analogo a `Import-Module` e `Import-DscResource`.








##Miglioramenti a Pester
In WMF 5.1, la versione di Pester fornita con PowerShell è stata aggiornata da versione 3.3.5 a versione 3.4.0 con l'aggiunta di Commit https://github.com/pester/Pester/pull/484/commits/3854ae8a1f215b39697ac6c2607baf42257b102e, che migliora il comportamento di Pester su Nano. 

Per conoscere le modifiche dalla versione 3.3.5 alla versione 3.4.0 vedere il file ChangeLog.md che si trova in https://github.com/pester/Pester/blob/master/CHANGELOG.md



<!--HONumber=Jul16_HO3-->


