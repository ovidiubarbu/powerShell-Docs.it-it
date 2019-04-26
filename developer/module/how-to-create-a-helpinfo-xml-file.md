---
title: Come creare un File XML HelpInfo | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3971ce1f-271c-4938-a9d3-47ff3aaf7219
caps.latest.revision: 9
ms.openlocfilehash: 7df9764fd573b75f285fec592448a550e481bea3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082414"
---
# <a name="how-to-create-a-helpinfo-xml-file"></a>Come creare un file XML HelpInfo

Gli argomenti in questa sezione illustra come creare e popolare un file di informazioni della Guida, comunemente noto come un "file XML HelpInfo," per la funzionalità Guida aggiornabile di Windows PowerShell.

## <a name="helpinfo-xml-file-overview"></a>Panoramica del File XML HelpInfo

Il file XML HelpInfo è la fonte principale di informazioni sulla Guida aggiornabile per il modulo. Include il percorso dei file della Guida per i moduli, le impostazioni cultura dell'interfaccia utente supportate e i numeri di versione utilizzato per determinare se l'utente ha i file della Guida più recente della Guida aggiornabile.

Ogni modulo ha solo un file XML HelpInfo, anche se il modulo include più file della Guida per più impostazioni cultura dell'interfaccia utente. Autore del modulo Crea il file XML HelpInfo e lo inserisce nel percorso specificato da Internet i **HelpInfoUri** chiave nel manifesto del modulo. Quando i file della Guida dei moduli sono aggiornati e caricati, l'autore del modulo Aggiorna il file XML HelpInfo e sostituisce il file XML HelpInfo originale con la nuova versione.

È fondamentale che il file XML HelpInfo venga mantenuto con attenzione. Se si carica nuovo file, ma dimentica di incrementare i numeri di versione, la Guida aggiornabile non verranno scaricati i nuovi file sui computer degli utenti. Se si aggiungono i file della Guida per impostazioni cultura dell'interfaccia utente nuova, ma non aggiornare il file XML HelpInfo o inserirlo nella posizione corretta, la Guida aggiornabile è possibile che non verranno scaricati i nuovi file.

## <a name="in-this-section"></a>Contenuto della sezione

Questa sezione include gli argomenti seguenti.

- [Schema XML HelpInfo](./helpinfo-xml-schema.md)

- [File di esempio XML HelpInfo](./helpinfo-xml-sample-file.md)

- [Come assegnare un nome di un File XML HelpInfo](./how-to-name-a-helpinfo-xml-file.md)

- [Come impostare i numeri di versione XML HelpInfo](./how-to-set-helpinfo-xml-version-numbers.md)

## <a name="see-also"></a>Vedere anche

[Supporto per la Guida aggiornabile](./supporting-updatable-help.md)