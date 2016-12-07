---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: blacklist
ms.technology: powershell
ms.openlocfilehash: e823cc0b130500fb7ea60e65acf27f90ad3f3802
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
### <a name="on-blacklisting"></a>Blacklist
Dopo essersi esercitati con JEA, ci si potrebbe chiedere se è possibile disattivare i comandi.
Si tratta di una domanda legittima, ma l'operazione non è attualmente prevista per JEA per i motivi seguenti:

1.  JEA è stato progettato per limitare gli operatori solo alle azioni che devono svolgere.
La blacklist è un concetto opposto.

2.  Gli autori dei comandi di PowerShell non hanno progettato i comandi di PowerShell prendendo in considerazione JEA.
In una nuova installazione di Windows Server 2016 sono immediatamente disponibili circa 1520 comandi.
I modelli di rischio per questi comandi non includono la possibilità che un utente esegua i comandi come account con più privilegi.
Ad esempio, alcuni comandi consentono l'inserimento di codice a livello di progettazione (Add-Type e Invoke-Command nel modulo core di PowerShell).
JEA visualizza un avviso quando si espongono i comandi visti in precedenza, ma tutti gli altri comandi di Windows non sono stati nuovamente valutati in base al nuovo modello di rischio.
È necessario comprendere le capacità dei comandi che si espongono con JEA.  

3.  E anche se JEA blocca tutti i comandi con vulnerabilità tipo "code injection", non vi sono garanzie che un utente malintenzionato non sia in grado di eseguire un'azione inserita nella blacklist con un altro comando correlato.
Se non si comprendono tutti i comandi che si intende esporre, non è possibile garantire che una determinata operazione non venga eseguita.
L'impegno consiste nel comprendere i comandi esposti e se tali comandi usano una whitelist o una blacklist.
Il numero di comandi che possono essere esposti in base a una blacklist è da gestire, quindi JEA viene implementato usando invece delle whitelist.

