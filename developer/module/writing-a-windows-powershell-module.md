---
title: Scrittura di un modulo di PowerShell di Windows | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: 58fb23c854f5a8b40ad1f952d3323aeeccac7a24
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 05/07/2019
ms.locfileid: "65229341"
---
# <a name="writing-a-windows-powershell-module"></a>Scrittura di un modulo di Windows PowerShell

Questo documento è scritto per gli amministratori, sviluppatori di script e gli sviluppatori di cmdlet che hanno bisogno per creare un pacchetto e distribuire i cmdlet di Windows PowerShell. Usando moduli di Windows PowerShell, è possibile creare un pacchetto e distribuire soluzioni di Windows PowerShell senza usare un linguaggio compilato.

I moduli di Windows PowerShell consentono di partizione, organizzare e astraggono del codice di Windows PowerShell in unità indipendente e riutilizzabile. Con queste unità riutilizzabile, è possibile condividere facilmente i moduli direttamente con altri utenti. Se sei uno sviluppatore di script, è anche possibile riassemblare i moduli di terze parti per creare applicazioni personalizzate basate su script. I moduli, simili a moduli in altri linguaggi di script come Perl e Python, abilitare soluzioni di scripting di produzione che usano i componenti ridistribuibili e riutilizzabili, con l'ulteriore vantaggio di poter ricreare il pacchetto e astrarre più componenti creare soluzioni personalizzate.

Al loro più elementare, Windows PowerShell considererà qualsiasi codice di script Windows PowerShell validi salvato in un file con estensione psm1 come modulo. PowerShell considererà automaticamente anche tutti gli assembly binari cmdlet come un modulo. Tuttavia, è possibile utilizzare anche un modulo o, più specificamente, un manifesto del modulo per raccogliere un'intera soluzione. Di seguito sono descritti gli utilizzi tipici dei moduli di Windows PowerShell.

### <a name="libraries"></a>Librerie

I moduli possono essere usati assemblare e distribuire le librerie coesa di funzioni che eseguono attività comuni. In genere, i nomi di queste funzioni condividono uno o più sostantivi che riflettono l'attività più comune che vengono utilizzati per. Queste funzioni possono anche essere simile a classi di .NET Framework in quanto possono avere membri privati e pubblici. Ad esempio, una libreria può contenere un set di funzioni per i trasferimenti di file. In questo caso, il sostantivo che riflettono l'attività comune potrebbe essere "file".

### <a name="configuration"></a>Configurazione

I moduli possono essere usati per personalizzare l'ambiente mediante l'aggiunta di variabili, i provider, funzioni e cmdlet specifici.

### <a name="compiled-code-development-and-distribution"></a>Sviluppo di codice compilato e la distribuzione

Gli sviluppatori di cmdlet e provider possono usare i moduli a testare e distribuire il proprio codice compilato senza dover creare snap-in. È possibile importare l'assembly che contiene il codice compilato come modulo (un modulo binario) senza la necessità di creare e registrare gli snap-in.

## <a name="see-also"></a>Vedere anche

[Understanding a PowerShell Module di Windows](./understanding-a-windows-powershell-module.md)

[Come scrivere un modulo di Script di PowerShell](./how-to-write-a-powershell-script-module.md)

[Come scrivere un modulo di file binari di PowerShell](./how-to-write-a-powershell-binary-module.md)

[Come scrivere un manifesto del modulo di PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modifica il percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importazione di un modulo di PowerShell](./importing-a-powershell-module.md)

[Installazione di un modulo di PowerShell](./installing-a-powershell-module.md)
