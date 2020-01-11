---
title: Come creare un provider di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- providers [PowerShell Programmer's Guide]
- providers [PowerShellProgrammer's Guide], creating
- Windows PowerShell Programmer's Guide, providers
ms.assetid: 863e48e9-7206-4c6a-a59a-2ab2d30396bc
caps.latest.revision: 5
ms.openlocfilehash: 4c84d015aba327c0ab039558414c5777d43ec4ba
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870881"
---
# <a name="how-to-create-a-windows-powershell-provider"></a>Come creare un provider di Windows PowerShell

In questa sezione viene descritto come compilare un provider di Windows PowerShell. Un provider di Windows PowerShell può essere considerato in due modi. Per l'utente, il provider rappresenta un set di dati archiviati. Ad esempio, i dati archiviati possono essere la metabase Internet Information Services (IIS), il registro di sistema di Microsoft Windows, i file system Windows, Active Directory e la variabile e i dati alias archiviati da Windows PowerShell.

Per lo sviluppatore, il provider di Windows PowerShell è l'interfaccia tra l'utente e i dati a cui l'utente deve accedere. Da questo punto di vista, ogni tipo di provider descritto in questa sezione supporta un set di classi di base e interfacce specifiche che consentono al runtime di Windows PowerShell di esporre determinati cmdlet all'utente in modo comune.

## <a name="providers-provided-by-windows-powershell"></a>Provider forniti da Windows PowerShell

Windows PowerShell offre diversi provider, ad esempio il provider FileSystem, il provider del registro di sistema e il provider di alias, usati per accedere agli archivi dati noti. Per ulteriori informazioni sui provider forniti da Windows PowerShell, utilizzare il comando seguente per accedere alla Guida in linea:

**PS > get-help about_providers**

## <a name="accessing-the-stored-data-using-windows-powershell-paths"></a>Accesso ai dati archiviati usando i percorsi di Windows PowerShell

I provider di Windows PowerShell sono accessibili al runtime di Windows PowerShell e ai comandi a livello di codice tramite l'uso dei percorsi di Windows PowerShell. Nella maggior parte dei casi, questi percorsi vengono utilizzati per accedere direttamente ai dati tramite il provider. Tuttavia, è possibile risolvere alcuni percorsi in percorsi interni del provider che consentono a un cmdlet di usare le API (Application Programming Interface) non Windows PowerShell per accedere ai dati. Per ulteriori informazioni sul funzionamento dei provider di Windows PowerShell in Windows PowerShell, vedere funzionamento di [Windows PowerShell](/previous-versions/ms714658(v=vs.85)).

## <a name="exposing-provider-cmdlets-using-windows-powershell-drives"></a>Esposizione di cmdlet del provider con le unità di Windows PowerShell

Un provider di Windows PowerShell espone i relativi cmdlet supportati tramite le unità virtuali di Windows PowerShell.
Windows PowerShell applica le seguenti regole per un'unità di Windows PowerShell:

- Il nome di un'unità può essere qualsiasi sequenza alfanumerica.
- Un'unità può essere specificata in qualsiasi punto valido in un percorso, denominato "radice".
- Un'unità può essere implementata per tutti i dati archiviati, non solo per i file system.
- Ogni unità mantiene il proprio percorso di lavoro corrente, consentendo all'utente di mantenere il contesto durante lo spostamento tra le unità.

## <a name="in-this-section"></a>Contenuto della sezione

Nella tabella seguente sono elencati gli argomenti che includono esempi di codice che si compilano tra loro. A partire dal secondo argomento, il provider di base di Windows PowerShell può essere inizializzato e non inizializzato dal runtime di Windows PowerShell. l'argomento successivo aggiunge la funzionalità per l'accesso ai dati. l'argomento successivo aggiunge la funzionalità per la modifica dei dati ( gli elementi nei dati archiviati) e così via.

|                                                    Argomento                                                    |                                                                                         Definizione                                                                                          |
| ----------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Progettazione del provider di Windows PowerShell](./designing-your-windows-powershell-provider.md)               | In questo argomento vengono illustrati gli aspetti da considerare prima di implementare un provider di Windows PowerShell. Riepiloga le classi e le interfacce di base del provider di Windows PowerShell utilizzate. |
| [Creazione di un provider di Windows PowerShell di base](./creating-a-basic-windows-powershell-provider.md)           | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente al runtime di Windows PowerShell di inizializzare e annullare l'inizializzazione del provider.                                        |
| [Creazione di un provider di unità di Windows PowerShell](./creating-a-windows-powershell-drive-provider.md)           | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di accedere a un archivio dati tramite un'unità di Windows PowerShell.                                                |
| [Creazione di un provider di elementi di Windows PowerShell](./creating-a-windows-powershell-item-provider.md)             | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare gli elementi in un archivio dati.                                                                  |
| [Creazione di un provider di contenitori di Windows PowerShell](./creating-a-windows-powershell-container-provider.md)   | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di lavorare sugli archivi dati multistrato.                                                                        |
| [Creazione di un provider di navigazione di Windows PowerShell](./creating-a-windows-powershell-navigation-provider.md) | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di spostarsi tra gli elementi di un archivio dati in modo gerarchico.                                           |
| [Creazione di un provider di contenuti Windows PowerShell](./creating-a-windows-powershell-content-provider.md)       | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare il contenuto degli elementi in un archivio dati.                                                       |
| [Creazione di un provider di proprietà di Windows PowerShell](./creating-a-windows-powershell-property-provider.md)     | In questo argomento viene illustrato come creare un provider di Windows PowerShell che consente all'utente di modificare le proprietà degli elementi in un archivio dati.                                                    |

## <a name="see-also"></a>Vedere anche

[Funzionamento di Windows PowerShell](/previous-versions/ms714658(v=vs.85))

[Windows PowerShell SDK](../windows-powershell-reference.md)

[Guida per programmatori di Windows PowerShell](./windows-powershell-programmer-s-guide.md)
