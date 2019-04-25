---
ms.date: 09/11/2018
contributor: JKeithB
keywords: raccolta,powershell,psgallery
title: Download manuale del pacchetto
ms.openlocfilehash: af628f99befe50c16c2c0c60f1a352647af34ff4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075362"
---
# <a name="manual-package-download"></a>Download manuale del pacchetto

PowerShell Gallery supporta il download di un pacchetto direttamente dal sito Web, senza usare i cmdlet PowerShellGet. È possibile scaricare qualsiasi pacchetto come file del pacchetto NuGet (con estensione nupkg) e poi copiarlo in un repository interno.

> [!NOTE]
> Il download manuale del pacchetto **non** deve essere inteso come sostituzione del cmdlet Install-Module.
> Il download del pacchetto non installa il modulo o lo script. Le dipendenze non sono incluse nel pacchetto NuGet scaricato. Le istruzioni seguenti sono incluse solo a scopo di riferimento.

## <a name="using-manual-download-to-acquire-a-package"></a>Uso del download manuale per acquisire un pacchetto

Ogni pagina contiene un collegamento per il download manuale, come illustrato di seguito:

![Download manuale](../../Images/packagedisplaypagewithpseditions.png)

Per eseguire manualmente il download, fare clic su **Download the raw nupkg file** (Scarica il file NUPKG non elaborato). Una copia del pacchetto viene copiata nella cartella di download del browser con il nome `<name>.<version>.nupkg`.

Un pacchetto NuGet è un archivio ZIP con file aggiuntivi che contengono informazioni sul contenuto del pacchetto. Alcuni browser, ad esempio Internet Explorer, sostituiscono automaticamente l'estensione di file `.nupkg` con `.zip`. Per espandere il pacchetto, rinominare il `.nupkg` file `.zip`, se necessario, quindi estrarre il contenuto in una cartella locale.

Un file del pacchetto NuGet include i seguenti elementi specifici di NuGet che non fanno parte del codice nel pacchetto originale:

- Una cartella denominata `_rels` che contiene un file `.rels` in cui sono elencate le dipendenze
- Una cartella denominata `package` che contiene i dati specifici di NuGet
- Un file denominato `[Content_Types].xml` che descrive il modo in cui alcune estensioni, ad esempio PowerShellGet, funzionano con NuGet
- Un file denominato `<name>.nuspec` che contiene la copia bulk dei metadati

## <a name="installing-powershell-modules-from-a-nuget-package"></a>Installazione dei moduli di PowerShell da un pacchetto NuGet

> [!NOTE]
> Queste istruzioni **NON** producono lo stesso risultato dell'esecuzione di `Install-Module`. Queste istruzioni soddisfano i requisiti minimi. Non sono progettate come sostituzione per `Install-Module`. Alcuni passaggi eseguiti da `Install-Module` non sono inclusi.

L'approccio più semplice consiste nel rimuovere gli elementi specifici di NuGet dalla cartella. In questo modo il codice di PowerShell creato dall'autore del pacchetto rimane inalterato. I passaggi sono:

1. Estrarre il contenuto del pacchetto NuGet in una cartella locale.
2. Eliminare gli elementi specifici di NuGet dalla cartella.
3. Rinominare la cartella. Il nome della cartella predefinita è in genere `<name>.<version>`. La versione può includere "-prerelease" se il modulo è contrassegnato come versione non definitiva. Rinominare la cartella usando solo il nome del modulo. Ad esempio, "azurerm.storage.5.0.4-preview" diventa "azurerm.storage".
4. Copiare la cartella in una delle cartelle in `$env:PSModulePath value`. `$env:PSModulePath` è un set di percorsi delimitati da punto e virgola in cui PowerShell ricerca i moduli.

> [!IMPORTANT]
> Il download manuale non include le dipendenze richieste dal modulo. Se il pacchetto ha dipendenze, devono essere installate nel sistema affinché questo modulo funzioni correttamente. PowerShell Gallery visualizza tutte le dipendenze richieste dal pacchetto.

## <a name="installing-powershell-scripts-from-a-nuget-package"></a>Installazione degli script di PowerShell da un pacchetto NuGet

> [!NOTE]
> Queste istruzioni **NON** producono lo stesso risultato dell'esecuzione di `Install-Script`. Queste istruzioni soddisfano i requisiti minimi. Non sono progettate come sostituzione per `Install-Script`.

L'approccio più semplice è estrarre il pacchetto NuGet e quindi usare direttamente lo script. I passaggi sono:

1. Estrarre il contenuto del pacchetto NuGet.
2. Il file `.PS1` presente nella cartella può essere usato direttamente da questo percorso.
3. Gli elementi specifici di NuGet si possono eliminare dalla cartella.

> [!IMPORTANT]
> Il download manuale non include le dipendenze richieste dal modulo. Se il pacchetto ha dipendenze, devono essere installate nel sistema affinché questo modulo funzioni correttamente. PowerShell Gallery visualizza tutte le dipendenze richieste dal pacchetto.
