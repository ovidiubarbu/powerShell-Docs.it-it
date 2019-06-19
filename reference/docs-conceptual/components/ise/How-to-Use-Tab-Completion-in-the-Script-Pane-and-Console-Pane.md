---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console
ms.openlocfilehash: 9fcb85668673adb1de596660d37e56f6607a4064
ms.sourcegitcommit: a6f13c16a535acea279c0ddeca72f1f0d8a8ce4c
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2019
ms.locfileid: "67031005"
---
# <a name="how-to-use-tab-completion-in-the-script-pane-and-console-pane"></a>Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console

La funzionalità di completamento tramite tasto TAB offre supporto automatico durante la digitazione nel riquadro di script o nel riquadro dei comandi. Per sfruttare i vantaggi di questa funzionalità, procedere come segue:

## <a name="to-automatically-complete-a-command-entry"></a>Per completare automaticamente una voce di comando

Nel riquadro dei comandi o nel riquadro di script digitare alcuni caratteri di un comando e quindi premere TAB per selezionare il testo di completamento desiderato. Se più elementi iniziano con il testo digitato originariamente, continuare a premere TAB fino a quando non verrà visualizzato l'elemento desiderato. La funzionalità di completamento tramite tasto TAB consente di digitare il nome di un cmdlet, il nome di un parametro, il nome di una variabile, il nome di una proprietà oggetto o il percorso di un file.

> [!NOTE]
> Premendo il tasto TAB nel riquadro di script verrà automaticamente completato un comando solo durante la modifica dei file con estensione ps1, psd1 o psm1. La funzionalità di completamento tramite tasto TAB funziona in qualsiasi momento durante la digitazione nel riquadro dei comandi.

## <a name="to-automatically-complete-a-cmdlet-parameter-entry"></a>Per completare automaticamente una voce di parametro cmdlet

Nel riquadro dei comandi o nel riquadro di script digitare un cmdlet seguito da un trattino e quindi premere TAB.

Ad esempio, digitare `Get-Process -` e quindi premere più volte TAB per visualizzare ognuno dei parametri per il cmdlet.

## <a name="see-also"></a>Vedere anche

- [Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)
- [Come creare una scheda di PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)
