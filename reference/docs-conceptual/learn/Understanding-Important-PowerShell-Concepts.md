---
ms.date: 08/23/2018
keywords: powershell,cmdlet
title: Concetti importanti relativi a PowerShell
ms.assetid: 3e601e38-4520-4578-a48d-b6779f1d35ee
ms.openlocfilehash: fad64563d1a7a6abd4f0e430331f81f91f43d312
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401146"
---
# <a name="understanding-important-powershell-concepts"></a>Concetti importanti relativi a PowerShell

La progettazione di PowerShell riunisce concetti correlati a molti ambienti diversi. Diversi di questi concetti saranno già familiari a utenti con esperienza in shell o ambienti di programmazione. Tuttavia, saranno pochi gli utenti che ne hanno una comprensione completa. La comprensione di alcuni di questi concetti assicura un'utile conoscenza generale della shell.

## <a name="output-is-object-based"></a>L'output è basato sugli oggetti

Diversamente dalle interfacce della riga di comando tradizionali, i cmdlet di PowerShell sono progettati per gestire oggetti.
Un oggetto è un'informazione strutturata che è molto più della semplice stringa di caratteri visualizzata sullo schermo. L'output dei comandi include sempre informazioni aggiuntive da usare in caso di necessità.

Se in passato sono stati usati strumenti di elaborazione del testo per elaborare i dati, si noterà che questi strumenti si comportano in modo diverso se usati in PowerShell. Nella maggior parte dei casi, non sono necessari strumenti di elaborazione del testo per estrarre informazioni specifiche. È possibile accedere direttamente a parti dei dati usando la sintassi a oggetti standard di PowerShell.

## <a name="the-command-family-is-extensible"></a>La famiglia di comandi è estendibile

Interfacce come **cmd.exe** non consentono di estendere direttamente il set di comandi predefinito. È possibile creare strumenti da riga di comando esterni da eseguire in **cmd.exe**. Tuttavia, questi strumenti esterni non includono servizi, come l'integrazione della Guida. **cmd.exe** non riconosce automaticamente questi strumenti esterni come comandi validi.

I comandi nativi in PowerShell sono noti con il nome di *cmdlet* (pronunciato command-let). È possibile creare moduli e funzioni di cmdlet personalizzati usando codice compilato o script. I moduli possono aggiungere cmdlet e provider alla shell. PowerShell supporta anche script analoghi a quelli della shell UNIX e ai file batch di **cmd.exe**.

## <a name="powershell-handles-console-input-and-display"></a>PowerShell gestisce l'input e la visualizzazione della console

Quando si digita un comando, PowerShell elabora sempre l'input della riga di comando direttamente. PowerShell formatta anche l'output visualizzato sullo schermo. Questa differenza è significativa perché riduce le attività necessarie per ogni cmdlet. Assicura inoltre che sia sempre possibile eseguire le operazioni allo stesso modo con qualsiasi cmdlet. Gli sviluppatori di cmdlet non devono scrivere codice per analizzare gli argomenti della riga di comando o formattare l'output.

Gli strumenti da riga di comando tradizionali hanno i propri schemi per la richiesta e la visualizzazione della Guida. Alcuni strumenti da riga di comando usano **/?** per attivare la visualizzazione della Guida, altri usano **-?**, **/H** o addirittura **//**. Alcuni visualizzano la Guida in una finestra GUI, invece che nella visualizzazione della console. Se si usa un parametro errato, lo strumento può ignorare l'input digitato e avviare l'esecuzione di un'attività automaticamente.
Poiché PowerShell analizza ed elabora automaticamente la riga di comando, il parametro **-?** significa sempre "Mostra la Guida per il comando".

> [!NOTE]
> Se si esegue un'applicazione grafica in PowerShell, viene visualizzata la finestra dell'applicazione.
> PowerShell interviene solo per l'elaborazione dell'input della riga di comando immesso o dell'output dell'applicazione restituito nella finestra della console, senza influire sul funzionamento interno dell'applicazione.

## <a name="powershell-uses-some-c-syntax"></a>PowerShell parte della sintassi C#

PowerShell è integrato in .NET Framework e condivide alcune funzionalità e parole chiave della propria sintassi con il linguaggio di programmazione C#. Una certa esperienza in PowerShell può semplificare l'apprendimento di C#. Se invece si ha già familiarità con C#, queste analogie possono semplificare l'apprendimento di PowerShell.
