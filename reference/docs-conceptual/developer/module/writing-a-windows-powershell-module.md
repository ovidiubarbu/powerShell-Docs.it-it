---
title: Scrittura di un modulo di Windows PowerShell | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: bfbccc5b-2b2b-432a-a971-9f8ab503cdc3
caps.latest.revision: 17
ms.openlocfilehash: 0b7263ea19745e902fff04b993933e443d4d6333
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72360620"
---
# <a name="writing-a-windows-powershell-module"></a>Scrittura di un modulo di Windows PowerShell

Questo documento è stato scritto per gli amministratori, gli sviluppatori di script e gli sviluppatori di cmdlet che devono creare pacchetti e distribuire i cmdlet di Windows PowerShell. Usando i moduli di Windows PowerShell, è possibile creare pacchetti e distribuire le soluzioni di Windows PowerShell senza usare un linguaggio compilato.

I moduli di Windows PowerShell consentono di partizionare, organizzare ed estrarre il codice di Windows PowerShell in unità autosufficienti e riutilizzabili. Con queste unità riutilizzabili, è possibile condividere facilmente i moduli direttamente con altri utenti. Gli sviluppatori di script possono anche riassemblare moduli di terze parti per creare applicazioni personalizzate basate su script. I moduli, simili ai moduli di altri linguaggi di scripting, ad esempio Perl e Python, abilitano soluzioni di scripting pronte per la produzione che usano componenti riutilizzabili e ridistribuibili, con l'ulteriore vantaggio di consentire di riassemblare ed estrarre più componenti in creare soluzioni personalizzate.

Al massimo, Windows PowerShell considererà tutti i codici di script di Windows PowerShell validi salvati in un file con estensione psm1 come modulo. PowerShell considererà inoltre automaticamente qualsiasi assembly di cmdlet binario come modulo. Tuttavia, è anche possibile usare un modulo (o più specificamente un manifesto del modulo) per raggruppare un'intera soluzione. Negli scenari seguenti vengono descritti gli utilizzi tipici dei moduli di Windows PowerShell.

### <a name="libraries"></a>Librerie

I moduli possono essere usati per creare pacchetti e distribuire librerie coerenti di funzioni che eseguono attività comuni. In genere, i nomi di queste funzioni condividono uno o più sostantivi che riflettono l'attività comune per cui vengono usati. Queste funzioni possono anche essere simili alle classi .NET Framework in quanto possono avere membri pubblici e privati. Una libreria, ad esempio, può contenere un set di funzioni per i trasferimenti di file. In questo caso, il sostantivo che riflette l'attività comune potrebbe essere "file".

### <a name="configuration"></a>Configurazione

I moduli possono essere utilizzati per personalizzare l'ambiente mediante l'aggiunta di cmdlet, provider, funzioni e variabili specifici.

### <a name="compiled-code-development-and-distribution"></a>Sviluppo e distribuzione di codice compilato

Gli sviluppatori di cmdlet e provider possono utilizzare moduli per testare e distribuire il codice compilato senza la necessità di creare snap-in. Possono importare l'assembly che contiene il codice compilato come modulo (un modulo binario) senza dover creare e registrare gli snap-in.

## <a name="see-also"></a>Vedere anche

[Informazioni su un modulo di Windows PowerShell](./understanding-a-windows-powershell-module.md)

[Come scrivere un modulo di script di PowerShell](./how-to-write-a-powershell-script-module.md)

[Come scrivere un modulo binario di PowerShell](./how-to-write-a-powershell-binary-module.md)

[Come scrivere un manifesto del modulo PowerShell](how-to-write-a-powershell-module-manifest.md)

[Modifica del percorso di installazione di PSModulePath](./modifying-the-psmodulepath-installation-path.md)

[Importazione di un modulo di PowerShell](./importing-a-powershell-module.md)

[Installazione di un modulo di PowerShell](./installing-a-powershell-module.md)
