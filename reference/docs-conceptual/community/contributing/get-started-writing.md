---
title: Guida introduttiva ai contributi alla documentazione di PowerShell
description: Questo articolo offre una panoramica su come contribuire alla documentazione di PowerShell.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: fdf29feb75abb6592205aaf1726c07a60ce3a924
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005517"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Guida introduttiva ai contributi alla documentazione di PowerShell

Questo articolo offre una panoramica su come contribuire alla documentazione di PowerShell.

## <a name="powershell-docs-structure"></a>Struttura PowerShell-Docs

Il [repository PowerShell-Docs][psdocs] è suddiviso in due gruppi di contenuti. Per gestire la modalità e il momento in cui la documentazione viene pubblicata vengono usati i rami Git.

### <a name="reference-content"></a>Contenuto di riferimento

Il contenuto di riferimento è il riferimento dei cmdlet di PowerShell per i cmdlet inclusi in PowerShell.
Il [riferimento][ref] viene raccolto nelle cartelle delle versioni, 5.1, 6, 7.0 e 7.1. Questo contenuto raccoglie solo il riferimento dei cmdlet per i moduli inclusi in PowerShell. Viene usato anche per creare le informazioni della Guida visualizzate dal cmdlet `Get-Help`.

> [!NOTE]
> Il sommario del contenuto di riferimento viene generato automaticamente dal sistema di pubblicazione. Non è necessario aggiornarlo.

### <a name="conceptual-content"></a>Contenuto concettuale

La documentazione concettuale include i contenuti seguenti:

- Note sulla versione
- Istruzioni di configurazione
- Script di esempio e procedure dettagliate
- Documentazione DSC
- Documentazione SDK

La [documentazione concettuale][conceptual] non è organizzata in base alla versione. Tutti gli articoli vengono visualizzati per ogni versione di PowerShell. Stiamo lavorando per creare articoli specifici per versione. Questa guida verrà aggiornata con le informazioni appropriate quando la funzionalità sarà disponibile nella documentazione.

> [!NOTE]
> Ogni volta che un articolo concettuale viene aggiunto, rimosso o rinominato, il sommario deve essere aggiornato e incluso nella richiesta pull.

## <a name="using-git-branches"></a>Uso dei rami Git

Il ramo predefinito per PowerShell-Docs è il ramo `staging`. Le modifiche apportate ai rami di lavoro vengono uniti al ramo `staging` prima di essere pubblicate. All'incirca una volta alla settimana il ramo `staging` viene unito al ramo `live`. Il ramo `live` include il contenuto pubblicato in docs.microsoft.com. Le modifiche non devono mai essere apportate direttamente nel ramo `live`.

Se si sta inviando una modifica alla documentazione che si applica solo a una versione non rilasciata di PowerShell, verificare se esiste un ramo di rilascio per tale versione. Tutte le modifiche che si applicano a una versione futura specifica devono essere destinate al ramo di rilascio. I rami di rilascio hanno il seguente modello di denominazione: `release-<version>`.

Prima di iniziare ad apportare qualsiasi modifica, creare un ramo di lavoro nella copia locale del repository PowerShell-Docs. La [copia tramite fork][fork] deve essere come illustrato. Assicurarsi di sincronizzare il repository locale prima di creare il ramo di lavoro. Il ramo di lavoro deve essere creato da una copia da aggiornamento a data del ramo `staging` o `release`.

Apportare le modifiche dopo il processo nella sezione [Apportare le modifiche][making-changes] della guida per i contributi.

### <a name="creating-new-articles"></a>Creazione di nuovi articoli

Per ogni nuovo documento con cui si vuole contribuire è necessario creare un problema di GitHub. Verificare i problemi esistenti per assicurarsi di non inserire problemi duplicati. I problemi assegnati a un utente sono considerati "in corso". Se si vuole collaborare a un problema, contattare la persona assegnata al problema.

In modo analogo al [processo di RFC][rfc] di PowerShell, creare un problema prima di scrivere il contenuto consente di evitare di lavorare su un elemento che viene poi rifiutato dal team di PowerShell-Docs. Questo consente anche al team di consultare l'utente in merito all'ambito del contenuto e al suo posizionamento nella documentazione di PowerShell.

### <a name="updating-existing-articles"></a>Aggiornamento di articoli esistenti

Laddove possibile, gli articoli dei riferimenti dei cmdlet vengono duplicati in tutte le versioni di PowerShell. Quando si segnala un problema relativo a un riferimento di un cmdlet o a un articolo `About_`, è necessario specificare quali versioni sono interessate dal problema. Il modello di problema in GitHub include un elenco di controllo delle versioni. Usare le caselle di controllo per specificare le versioni del contenuto interessate. Quando si invia una modifica a un articolo per un problema che interessa più versioni del contenuto, è necessario applicare la modifica appropriata a ogni versione del file.

## <a name="next-steps"></a>Passaggi successivi

Vedere [Invio di una richiesta pull](pull-requests.md)

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md