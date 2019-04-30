---
title: Uso di Visual Studio Code per la modifica e il debug remoti
description: Uso di Visual Studio Code per la modifica e il debug remoti
ms.date: 08/06/2018
ms.openlocfilehash: fbc1ee3556e822b4afb2b37111d0688dc89fdab3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086673"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Uso di Visual Studio Code per la modifica e il debug remoti

Per coloro hanno familiarità con l'ambiente ISE, si ricorderà che è possibile eseguire `psedit file.ps1` dalla console integrata per aprire i file, locali o remoti, direttamente in ISE.

Questa funzionalità è disponibile anche nell'estensione di PowerShell per VSCode. Questa guida illustrerà come eseguire queste operazioni.

## <a name="prerequisites"></a>Prerequisiti

Questa guida presuppone che si disponga di quanto segue:

- una risorsa remota ( ad esempio, una macchina virtuale, un contenitore) a cui si ha accesso
- PowerShell in esecuzione su di essi e il computer host
- VSCode e l'estensione di PowerShell per VSCode

Questa funzionalità funziona in Windows PowerShell e PowerShell Core.

Questa funzionalità funziona anche quando ci si connette a un computer remoto tramite Gestione remota Windows, PowerShell Direct o SSH. Se si desidera usare SSH, ma si usa Windows, verificare la [versione Win32 di SSH](https://github.com/PowerShell/Win32-OpenSSH).

## <a name="lets-go"></a>Partiamo

In questa sezione, verranno esaminati la modifica e il debug remoti dal MacBook Pro a una macchina virtuale Ubuntu in esecuzione in Azure. Si potrebbe non usare Windows, ma **il processo è identico**.

### <a name="local-file-editing-with-open-editorfile"></a>Modifica dei file locali con Open-EditorFile

Con l'estensione di PowerShell per VSCode avviata e la console integrata di PowerShell aperta, è possibile digitare `Open-EditorFile foo.ps1` o `psedit foo.ps1` per aprire il file locale foo.ps1 si direttamente nell'editor.

![Open-EditorFile foo.ps1 funziona localmente](https://user-images.githubusercontent.com/2644648/34895897-7c2c46ac-f79c-11e7-9410-a252aff52f13.png)

>[!NOTE]
> foo.ps1 deve esistere già.

Da qui, è possibile:

aggiungere i punti di interruzione alla barra ![aggiunta di un punto di interruzione alla barra](https://user-images.githubusercontent.com/2644648/34895893-7bdc38e2-f79c-11e7-8026-8ad53f9a1bad.png)

e premere F5 per eseguire il debug dello script di PowerShell.
![Debug dello script locale di PowerShell](https://user-images.githubusercontent.com/2644648/34895894-7bedb874-f79c-11e7-9180-7e0dc2d02af8.png)

Durante il debug, è possibile interagire con la console di debug, verificare le variabili nell'ambito a sinistra e tutti gli altri gli strumenti standard di debug.

### <a name="remote-file-editing-with-open-editorfile"></a>Modifica dei file remoti con Open-EditorFile

A questo punto passiamo alla modifica e debug dei file remoti. I passaggi sono quasi gli stessi, occorre solo fare prima di tutto una cosa: avviare la sessione di PowerShell nel server remoto.

È disponibile un cmdlet per eseguire questa operazione. È denominato `Enter-PSSession`.

La spiegazione semplificata del cmdlet è:

- `Enter-PSSession -ComputerName foo` avvia una sessione tramite Gestione remota Windows
- `Enter-PSSession -ContainerId foo` e `Enter-PSSession -VmId foo` avviano una sessione tramite PowerShell Direct
- `Enter-PSSession -HostName foo` avvia una sessione tramite SSH

Per altre informazioni su `Enter-PSSession`, vedere la documentazione [qui](https://docs.microsoft.com/powershell/module/microsoft.powershell.core/enter-pssession?view=powershell-6).

Per la comunicazione remota verrà usato SSH poiché si sta passando da macOS a una macchina virtuale Ubuntu in Azure.

In primo luogo, nella console integrata, eseguire Enter-PSSession. Si saprà di essere entrati nella sessione perché verrà visualizzato `[something]` a sinistra del prompt dei comandi.

![La chiamata a Enter-PSSession](https://user-images.githubusercontent.com/2644648/34895896-7c18e0bc-f79c-11e7-9b36-6f4bd0e9b0db.png)

Da qui, è possibile eseguire gli stessi passaggi che si eseguono per modificare uno script locale.

1. Eseguire `Open-EditorFile test.ps1` o `psedit test.ps1` per aprire il file remoto `test.ps1` ![Open-EditorFile file test.ps1](https://user-images.githubusercontent.com/2644648/34895898-7c3e6a12-f79c-11e7-8bdf-549b591ecbcb.png)
2. Modificare i file/impostare punti di interruzione ![modificare i file e impostare punti di interruzione](https://user-images.githubusercontent.com/2644648/34895892-7bb68246-f79c-11e7-8c0a-c2121773afbb.png)
3. Avviare il debug del file remoto (F5)

![debug del file remoto](https://user-images.githubusercontent.com/2644648/34895895-7c040782-f79c-11e7-93ea-47724fa5c10d.png)

Questo è tutto. Ci auguriamo che questa guida abbia contribuito a rispondere a eventuali domande sul debug e la modifica remoti di PowerShell in VSCode.

Se si verificano problemi, è possibile segnalarli [nel repository GitHub](http://github.com/powershell/vscode-powershell).
