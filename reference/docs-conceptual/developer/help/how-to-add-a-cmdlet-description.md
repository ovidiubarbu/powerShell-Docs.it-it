---
title: Come aggiungere una descrizione del cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 47af9d57-bd63-4596-816a-0b717418476b
caps.latest.revision: 10
ms.openlocfilehash: a2e4c4d42566d5a52006924eab02295c37cf3159
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72361280"
---
# <a name="how-to-add-a-cmdlet-description"></a>Come aggiungere una descrizione del cmdlet

In questa sezione viene descritto come aggiungere contenuto che viene visualizzato nella sezione Descrizione della guida del cmdlet. Nel file della guida, questo contenuto viene aggiunto al nodo del comando per ogni cmdlet.

> [!NOTE]
> Per una visualizzazione completa di un file della guida, aprire uno dei file dll-Help. XML che si trovano nella directory di installazione di Windows PowerShell. Il file Microsoft. PowerShell. Commands. Management. dll-Help. XML, ad esempio, contiene contenuto per diversi cmdlet di Windows PowerShell.

### <a name="to-add-a-description"></a>Per aggiungere una descrizione

- Per iniziare, è necessario illustrare in modo più dettagliato le funzionalità di base del cmdlet. In molti casi, è possibile spiegare i termini usati nel nome del cmdlet e illustrare concetti non noti con un esempio. Se, ad esempio, il cmdlet aggiunge dati a un file, spiega che aggiunge dati alla fine di un file esistente.

- Per trovare tutte le funzionalità del cmdlet, esaminare l'elenco dei parametri. Descrivere la funzione principale del cmdlet e quindi includere altre funzioni e funzionalità. Se, ad esempio, la funzione principale del cmdlet è la modifica di una proprietà, ma il cmdlet può modificare tutte le proprietà, ad esempio nella descrizione dettagliata. Se i parametri del cmdlet consentono agli utenti di richiedere informazioni in modi diversi, spiegarlo.

- Includere informazioni sui modi in cui gli utenti possono utilizzare il cmdlet, oltre agli utilizzi più evidenti. Ad esempio, è possibile usare l'oggetto recuperato dal cmdlet `Get-Host` per modificare il colore del testo nella finestra di comando di Windows PowerShell.

  Esempio: "il cmdlet `Get-Acl` ottiene gli oggetti che rappresentano il descrittore di sicurezza di un file o di una risorsa. Il descrittore di sicurezza contiene gli elenchi di controllo di accesso della risorsa. L'ACL specifica le autorizzazioni che gli utenti e i gruppi di utenti devono accedere alla risorsa ".

- La descrizione dettagliata dovrebbe descrivere il cmdlet, ma non deve descrivere i concetti usati dal cmdlet. Inserire le definizioni dei concetti in note aggiuntive.

## <a name="see-also"></a>Vedere anche

[Windows PowerShell SDK](../windows-powershell-reference.md)
