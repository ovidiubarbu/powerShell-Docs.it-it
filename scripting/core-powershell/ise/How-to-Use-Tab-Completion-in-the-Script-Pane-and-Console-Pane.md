---
title: "Come usare la funzionalità di completamento tramite TAB nel riquadro di script e nel riquadro della console"
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 3b752c3c-0bd0-4eca-a2d3-2d5a37fd9d84
ms.openlocfilehash: 803470be4a680d47ccec8b5b19bc873626aec15e
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
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
- [Utilizzo di Windows PowerShell ISE](using-the-windows-powershell-ise.md)
- [Come creare una scheda di PowerShell](How-to-Create-a-PowerShell-Tab-in-Windows-PowerShell-ISE.md)

