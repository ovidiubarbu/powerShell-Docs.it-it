---
title: 'Creazione della Guida aggiornabile: Step-by-Step | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: fbc77cc0fafce93d239da1c459d4b761b21ef3cb
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56860317"
---
# <a name="updatable-help-authoring-step-by-step"></a>Creazione della Guida aggiornabile: istruzioni dettagliate

Questo documento Elenca i passaggi del processo di creazione della Guida aggiornabile.

## <a name="authoring-updatable-help-step-by-step"></a>Creazione di una Guida aggiornabile: istruzioni dettagliate

La Guida aggiornabile è progettata per gli utenti finali, ma fornisce inoltre una serie di vantaggi significativi per gli autori di moduli e gli autori della Guida in linea, inclusa la possibilità di aggiungere contenuto, correggere gli errori, offrono più impostazioni cultura dell'interfaccia utente e rispondono ai commenti degli utenti e le richieste, tempo dopo il modulo è stato spedito. Questo argomento viene illustrato come è creare un pacchetto e Guida di caricamento file in modo che gli utenti possono scaricarli e installarli usando il [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) cmdlet.

I passaggi seguenti offrono una panoramica del processo di supporto della Guida aggiornabile.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Passaggio 1: Trovare un sito Internet per i file della Guida

Il primo passaggio nella creazione di una Guida aggiornabile è trovare un percorso Internet per i file della Guida del modulo. In realtà, è possibile usare due posizioni diverse. È possibile mantenere i file di informazioni del modulo della Guida (HelpInfo XML - descritto di seguito) in una posizione di Internet e i file CAB del contenuto della Guida in un altro percorso Internet. Tutti i file della Guida contenuti CAB un modulo devono essere nella stessa posizione. È possibile inserire i file CAB del contenuto della Guida per moduli diversi nello stesso percorso.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Passaggio 2: Aggiungere una chiave HelpInfoURI per il manifesto del modulo

Aggiungere un **HelpInfoURI** chiave per il manifesto del modulo. Il valore della chiave è l'identificatore URI (Uniform Resource) della posizione del file di informazioni XML HelpInfo per il modulo. Per la sicurezza, l'indirizzo deve iniziare con "http" o "https". L'URI deve specificare un percorso Internet, ma non deve includere il nome del file XML HelpInfo.

Ad esempio:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'http://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Passaggio 3: Creare un file XML HelpInfo

Il file di informazioni XML HelpInfo contiene l'URI del percorso Internet i file della Guida e i numeri di versione dei file della Guida più recenti per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente supportato. Ogni modulo Windows PowerShell ha un unico file XML HelpInfo. Quando si aggiornano i file della Guida, si modifica o sostituire il file XML HelpInfo; non si aggiunge un altro. Per altre informazioni, vedere [come creare un File XML HelpInfo](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Passaggio 4: Firmare i file della Guida

Non sono necessarie le firme digitali, ma ogni volta che si stanno condividendo file sono una raccomandazione di procedure consigliate.

### <a name="step-5-create-cab-files"></a>Passaggio 5: Creare i file CAB

Usare uno strumento che consente di creare file cabinet (CAB), ad esempio MakeCab.exe, per creare una. File CAB che contiene i file della Guida per il modulo. Creare un file CAB per i file della Guida in ognuna delle impostazioni cultura dell'interfaccia utente supportato. Per altre informazioni, vedere [come preparare aggiornabile aiutare i file CAB](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Passaggio 6: Caricamento dei file

Per pubblicare i file della Guida nuovi o aggiornati, caricare i file CAB al percorso specificato da Internet i **HelpContentUri** elemento nel file XML HelpInfo. Quindi, caricare il file XML HelpInfo per il percorso Internet specificato dal valore della **HelpInfoUri** chiave nel manifesto del modulo.
