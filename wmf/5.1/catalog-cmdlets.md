---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: wmf,powershell,installazione
title: Cmdlet di catalogo
ms.openlocfilehash: 7eaca09667af0eb5d719f23e987bb112e8514978
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/16/2018
ms.locfileid: "34189068"
---
# <a name="catalog-cmdlets"></a>Cmdlet di catalogo

Sono stati aggiunti due nuovi cmdlet nel modulo [Microsoft.Powershell.Secuity](https://technet.microsoft.com/en-us/library/hh847877.aspx) per generare e convalidare i file di catalogo di Windows.

## <a name="new-filecatalog"></a>New-FileCatalog
--------------------------------

`New-FileCatalog` crea un file di catalogo Windows per set di cartelle e file. Un file di catalogo contiene gli hash per tutti i file nei percorsi specificati. Gli utenti possono distribuire il set di cartelle con il corrispondente file di catalogo che rappresenta le cartelle. Un file di catalogo può essere usato dal destinatario del contenuto per convalidare le modifiche apportate alle cartelle dopo la creazione del catalogo.

```powershell
New-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-CatalogVersion <int>] [-WhatIf] [-Confirm] [<CommonParameters>]
```
Il catalogo della creazione dei file viene supportato nella versione 1 e 2. La versione 1 usa l'algoritmo di hash SHA1 per creare hash di file; la versione 2 usa SHA256. La versione 2 del catalogo non è supportata in *Windows Server 2008 R2* e in *Windows 7*. È consigliabile usare la versione 2 del catalogo se si usano le piattaforme *Windows 8*, *Windows Server 2012* e versioni successive.

Per usare questo comando in un modulo esistente, specificare le variabili CatalogFilePath e Path corrispondenti al percorso del manifesto del modulo. Nell'esempio seguente il manifesto del modulo è in C:\Programmi\Windows PowerShell\Moduli\Pester.

![](../images/NewFileCatalog.jpg)

Questa operazione crea il file di catalogo.

![](../images/CatalogFile1.jpg)

![](../images/CatalogFile2.jpg)

Per verificare l'integrità di un file di catalogo (Pester.cat nell'esempio precedente), è necessario che sia firmato con il cmdlet [Set-AuthenticodeSignature](https://technet.microsoft.com/library/hh849819.aspx).


## <a name="test-filecatalog"></a>Test-FileCatalog
--------------------------------

`Test-FileCatalog` convalida il catalogo che rappresenta un set di cartelle.

```powershell
Test-FileCatalog [-CatalogFilePath] <string> [[-Path] <string[]>] [-Detailed] [-FilesToSkip <string[]>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

![](../images/TestFileCatalog.jpg)

Questo cmdlet consente di confrontare gli hash di tutti i file e i relativi percorsi trovati nel file di catalogo con quelli salvati su disco. Se rileva eventuali mancate corrispondenze tra i percorsi e gli hash di file restituisce lo stato `ValidationFailed`.
L'utente può recuperare tutte queste informazioni usando il parametro `Detailed`. Lo stato di firma del catalogo viene visualizzato come campo `Signature` e ciò equivale a chiamare il cmdlet [Get-AuthenticodeSignature](https://technet.microsoft.com/en-us/library/hh849805.aspx) sul file di catalogo.
Gli utenti possono anche ignorare alcuni file durante la convalida usando il parametro `FilesToSkip`.
