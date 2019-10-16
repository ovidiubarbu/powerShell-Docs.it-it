---
title: Come creare e caricare file CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72367330"
---
# <a name="how-to-create-and-upload-cab-files"></a>Come creare e caricare i file CAB

In questo argomento viene illustrato come creare file CAB della Guida aggiornabili e come caricarli nel percorso in cui possono essere individuati dai cmdlet della Guida aggiornabili.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Come creare e caricare file CAB della Guida aggiornabile

È possibile utilizzare la funzionalità Guida aggiornabile per fornire file della Guida nuovi o aggiornati per un modulo in più lingue e impostazioni cultura. Un pacchetto della Guida aggiornabile per un modulo è costituito da un file XML HelpInfo e da uno o più file CAB (. File CAB). Ogni file CAB contiene i file della Guida per il modulo in un'unica lingua dell'interfaccia utente. Utilizzare la seguente procedura per creare file CAB per la guida aggiornabile.

1. Organizzare i file della Guida per il modulo in base alle impostazioni cultura dell'interfaccia utente. Ogni file CAB della Guida aggiornabile contiene i file della Guida per un modulo in un'unica lingua dell'interfaccia utente. È possibile distribuire più file CAB della Guida per il modulo, ciascuno per impostazioni cultura dell'interfaccia utente diverse.

2. Verificare che i file della Guida includano solo i tipi di file consentiti per la guida aggiornabile e convalidarli rispetto a uno schema file della Guida Se il cmdlet `Update-Help` rileva un file che non è valido o non è un tipo consentito, non installa il file non valido e interrompe l'installazione dei file dal file CAB. Per un elenco dei tipi di file consentiti, vedere [tipi di file consentiti in un file CAB della Guida aggiornabile](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Firma digitalmente i file della guida. Le firme digitali non sono necessarie, ma sono una procedura consigliata.

4. Includere tutti i file della Guida per il modulo nelle impostazioni cultura dell'interfaccia utente, non solo i file nuovi o modificati. Se il file CAB è incompleto, gli utenti che scaricano i file della Guida per la prima volta o non scaricano ogni aggiornamento, non disporrà di tutti i file della guida del modulo.

5. Utilizzare un'utilità che crea file CAB, ad esempio MakeCab. exe. Windows PowerShell non include i cmdlet per la creazione di file CAB.

6. Assegnare un nome ai file CAB. Per ulteriori informazioni, vedere [come denominare un file CAB della Guida aggiornabile](./how-to-name-an-updatable-help-cab-file.md).

7. Caricare i file CAB per il modulo nel percorso specificato dall'elemento **HelpContentUri** nel file XML HELPINFO per il modulo. Caricare quindi il file XML HelpInfo nel percorso specificato dalla chiave **HelpInfoUri** del manifesto del modulo. **HelpContentUri** e **HelpInfoUri** possono puntare alla stessa posizione.

> [!CAUTION]
> Il valore della chiave **HelpInfoUri** e dell'elemento **HelpContentUri** deve iniziare con "http" o "https". Il valore deve indicare un percorso Internet e non deve includere un nome file.