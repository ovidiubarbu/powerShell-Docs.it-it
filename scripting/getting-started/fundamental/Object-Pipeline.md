---
description: 
manager: carmonm
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet
ms.date: 2016-12-12
title: Pipeline degli oggetti
ms.technology: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 531c3c00ddcc0cc8299875392832fb1dad9f49d8
ms.sourcegitcommit: 8acbf9827ad8f4ef9753f826ecaff58495ca51b0
translationtype: HT
---
# <a name="object-pipeline"></a>Pipeline degli oggetti
Le pipeline si comportano come una serie di segmenti di pipe connessi. Gli elementi che si muovono nella pipeline passano tramite ogni segmento. Per creare una pipeline in Windows PowerShell, è necessario connettere i comandi con l'operatore di pipe "|". L'output di ogni comando viene usato come input per il comando successivo.

Le pipeline sono senza dubbio il concetto più importante usato nelle interfacce della riga di comando. Se usate correttamente, le pipeline non solo semplificano l'attività di immissione di comandi complessi, ma rendono anche più semplice la visualizzazione del flusso di lavoro nei comandi. Un'utile caratteristica correlata delle pipeline è che, operando in ogni elemento separatamente, non è necessario apportare modifiche a seconda che nella pipeline siano presenti zero, uno o molti elementi. Ogni comando in una pipeline (definito elemento della pipeline) in genere passa anche l'output al comando successivo nella pipeline elemento per elemento. Di solito questo consente di ridurre la richiesta di risorse da parte dei comandi complessi e di iniziare immediatamente ad acquisire output.

Questo capitolo descrive le differenze tra la pipeline di Windows PowerShell e le pipeline di shell più popolari e quindi illustra alcuni strumenti di base che è possibile usare per controllare l'output della pipeline e per osservare come funziona la pipeline.

