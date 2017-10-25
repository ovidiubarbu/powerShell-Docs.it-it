---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 3392db954c22030bb64ae5093619d23952e1fcdb
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="uninstallation-instructions"></a>Istruzioni di disinstallazione

## <a name="using-command-prompt"></a>Dal prompt dei comandi
1.  Aprire **Prompt dei comandi**.
2.  Eseguire il [programma di avvio di Windows Update autonomo](https://support.microsoft.com/en-us/kb/934307) come indicato di seguito:

In Windows Server 2012 R2 e Windows 8.1:
```powershell
wusa /uninstall /kb:3134758
```
In Windows Server 2012:
```powershell
wusa /uninstall /kb:3134759
```
In Windows Server 2008 R2 SP1 e Windows 7 SP1:
```powershell
wusa /uninstall /kb:3134760
```

## <a name="using-control-panel"></a>Dal Pannello di controllo
1.  Aprire il **Pannello di controllo**.
2.  Aprire **Programmi** e quindi **Disinstalla un programma**.
3.  Fare clic su **Visualizza aggiornamenti installati**.
4.  Selezionare **Windows Management Framework 5.0** nell'elenco degli aggiornamenti installati. Questi aggiornamenti corrispondono a *KB3134758*, *KB3134759* o *KB3134760*. Fare clic su **Disinstalla**.

