---
title: Come creare e caricare i file CAB | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8d35f233-5447-48a2-a961-9fbca763262b
caps.latest.revision: 7
ms.openlocfilehash: 9928a0b31a57d42eb39cea1af0509613c483caf7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62082380"
---
# <a name="how-to-create-and-upload-cab-files"></a>Come creare e caricare i file CAB

Questo argomento illustra come creare i file CAB di Guida aggiornabile e caricarli nel percorso in essi sono disponibili i cmdlet per la Guida aggiornabile.

## <a name="how-to-create-and-upload-updatable-help-cab-files"></a>Come creare e caricare i file CAB di Guida aggiornabile

È possibile usare la funzionalità Guida aggiornabile per recapitare i file della Guida nuovi o aggiornati per un modulo in più lingue e culture. Un pacchetto per la Guida aggiornabile per un modulo è costituito da un file XML HelpInfo e uno o più file CAB (. File CAB). Ogni file CAB contiene i file della Guida per il modulo in una delle impostazioni cultura dell'interfaccia utente. Usare la procedura seguente per creare i file CAB per la Guida aggiornabile.

1. Organizzare i file della Guida per il modulo delle impostazioni cultura dell'interfaccia utente. Ogni file CAB di Guida aggiornabile contiene i file della Guida per un modulo in una delle impostazioni cultura dell'interfaccia utente. È possibile recapitare la Guida più file CAB per il modulo, ognuna per diverse impostazioni cultura dell'interfaccia utente.

2. Verificare che i file della Guida include solo i tipi di file consentiti per la Guida aggiornabile e la successiva convalida rispetto a uno schema di file della Guida. Se il `Update-Help` cmdlet rileva un file che non è valido o non è un tipo consentito, ma non viene installato il file non valido e arresta l'installazione dei file dal CAB. Per un elenco dei tipi di file consentite, vedere [tipi di File consentiti in un File CAB Guida aggiornabile](./file-types-permitted-in-an-updatable-help-cab-file.md).

3. Firmare digitalmente i file della Guida. Non sono necessarie le firme digitali, ma sono una procedura consigliata.

4. Includere tutto aiuto di file per il modulo nell'interfaccia utente delle impostazioni cultura, non solo i file che sono nuovi o sono stati modificati. Se il file CAB è incompleto, gli utenti che scaricano i file della Guida per la prima volta o non scaricare tutti gli aggiornamenti, non avrà tutti i file della Guida di modulo.

5. Usare un'utilità che crea file CAB, ad esempio MakeCab.exe. Windows PowerShell non include i cmdlet che creano i file CAB.

6. Denominare i file CAB. Per altre informazioni, vedere [convenzioni di denominazione di un File CAB della Guida aggiornabile](./how-to-name-an-updatable-help-cab-file.md).

7. Caricare i file CAB per il modulo nel percorso specificato per il **HelpContentUri** elemento nel file XML HelpInfo per il modulo. Quindi caricare il file XML HelpInfo per il percorso specificato dal **HelpInfoUri** principali del manifesto del modulo. Il **HelpContentUri** e **HelpInfoUri** possono puntare allo stesso percorso.

> [!CAUTION]
> Il valore della **HelpInfoUri** chiave e il **HelpContentUri** elemento deve iniziare con "http" o "https". Il valore deve indicare un percorso Internet e non deve includere un nome di file.