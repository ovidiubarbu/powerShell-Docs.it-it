---
title: 'Creazione di una guida aggiornabile: procedura dettagliata | Microsoft Docs'
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10098160-c6b4-4339-b8ff-2c4f8cc0699b
caps.latest.revision: 13
ms.openlocfilehash: a5290265f3d729504983b95195c793b88c4a2613
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995994"
---
# <a name="updatable-help-authoring-step-by-step"></a>Creazione della Guida aggiornabile: istruzioni dettagliate

In questo documento sono elencati i passaggi del processo di creazione della Guida aggiornabile.

## <a name="authoring-updatable-help-step-by-step"></a>Creazione della Guida aggiornabile: procedura dettagliata

La guida aggiornabile è progettata per gli utenti finali, ma offre anche vantaggi significativi agli autori dei moduli e ai writer di supporto, inclusa la possibilità di aggiungere contenuto, correggere errori, distribuire più impostazioni cultura dell'interfaccia utente e rispondere a richieste e commenti degli utenti, molto dopo il il modulo è stato spedito. In questo argomento viene illustrato come creare un pacchetto e caricare i file della Guida in modo che gli utenti possano scaricarli e installarli usando i cmdlet [Update-Help](/powershell/module/Microsoft.PowerShell.Core/Update-Help) e [Save-Help](/powershell/module/Microsoft.PowerShell.Core/Save-Help) .

Nei passaggi seguenti viene fornita una panoramica del processo di supporto della Guida aggiornabile.

### <a name="step-1-find-an-internet-site-for-your-help-files"></a>Passaggio 1: trovare un sito Internet per i file della Guida

Il primo passaggio nella creazione della Guida aggiornabile è trovare un percorso Internet per i file della guida del modulo. In realtà, è possibile usare due posizioni diverse. È possibile salvare il file di informazioni della guida del modulo (HelpInfo XML, descritto di seguito) in un percorso Internet e i file CAB del contenuto della Guida in un altro percorso Internet. Tutti i file CAB del contenuto della Guida per un modulo devono trovarsi nella stessa posizione. È possibile inserire i file CAB del contenuto della Guida per moduli diversi nello stesso percorso.

### <a name="step-2-add-a-helpinfouri-key-to-your-module-manifest"></a>Passaggio 2: aggiungere una chiave HelpInfoURI al manifesto del modulo

Aggiungere una chiave **HelpInfoURI** al manifesto del modulo. Il valore della chiave è il Uniform Resource Identifier (URI) del percorso del file di informazioni XML HelpInfo per il modulo. Per la sicurezza, l'indirizzo deve iniziare con "http" o "https". L'URI deve specificare un percorso Internet, ma non deve includere il nome del file XML HelpInfo.

Ad esempio:

```powershell

@{
RootModule = TestModule.psm1
ModuleVersion = '2.0'
HelpInfoURI = 'https://go.microsoft.com/fwlink/?LinkID=0123'
}
```

### <a name="step-3-create-a-helpinfo-xml-file"></a>Passaggio 3: creare un file XML HelpInfo

Il file di informazioni XML HelpInfo contiene l'URI del percorso Internet dei file della guida e i numeri di versione dei file della guida più recenti per il modulo in ognuna delle impostazioni cultura dell'interfaccia utente supportate. Ogni modulo di Windows PowerShell include un file XML HelpInfo. Quando si aggiornano i file della guida, si modifica o si sostituisce il file XML HelpInfo. non è possibile aggiungerne un altro. Per ulteriori informazioni, vedere [come creare un file XML HELPINFO](./how-to-create-a-helpinfo-xml-file.md).

### <a name="step-4-sign-your-help-files"></a>Passaggio 4: firmare i file della Guida

Le firme digitali non sono necessarie, ma sono consigliate per le procedure consigliate ogni volta che si condividono i file.

### <a name="step-5-create-cab-files"></a>Passaggio 5: creare file CAB

Usare uno strumento che crea file CAB (con estensione cab), ad esempio MakeCab. exe, per creare un. File CAB contenente i file della Guida per il modulo. Creare un file CAB separato per i file della Guida in ognuna delle impostazioni cultura dell'interfaccia utente supportate. Per ulteriori informazioni, vedere [come preparare i file CAB della Guida aggiornabile](./how-to-prepare-updatable-help-cab-files.md).

### <a name="step-6-upload-your-files"></a>Passaggio 6: caricare i file

Per pubblicare file della Guida nuovi o aggiornati, caricare i file CAB nel percorso Internet specificato dall'elemento **HelpContentUri** nel file XML HELPINFO. Caricare quindi il file XML HelpInfo nel percorso Internet specificato dal valore della chiave **HelpInfoUri** nel manifesto del modulo.
