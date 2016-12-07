---
title: Pipeline degli oggetti
ms.date: 2016-05-11
keywords: powershell,cmdlet
description: 
ms.topic: article
author: jpjofre
manager: dongill
ms.prod: powershell
ms.assetid: 523d8ae4-d743-47a4-b79a-806130ca688a
ms.openlocfilehash: 570805d6ceb4613f0efc8095f08ce79d90514f62
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="object-pipeline"></a>Pipeline degli oggetti
Le pipeline si comportano come una serie di segmenti di pipe connessi. Gli elementi che si muovono nella pipeline passano tramite ogni segmento. Per creare una pipeline in Windows PowerShell, è necessario connettere i comandi con l'operatore di pipe "|". L'output di ogni comando viene usato come input per il comando successivo.

Le pipeline sono senza dubbio il concetto più importante usato nelle interfacce della riga di comando. Se usate correttamente, le pipeline non solo semplificano l'attività di immissione di comandi complessi, ma rendono anche più semplice la visualizzazione del flusso di lavoro nei comandi. Un'utile caratteristica correlata delle pipeline è che, operando in ogni elemento separatamente, non è necessario apportare modifiche a seconda che nella pipeline siano presenti zero, uno o molti elementi. Ogni comando in una pipeline (definito elemento della pipeline) in genere passa anche l'output al comando successivo nella pipeline elemento per elemento. Di solito questo consente di ridurre la richiesta di risorse da parte dei comandi complessi e di iniziare immediatamente ad acquisire output.

Questo capitolo descrive le differenze tra la pipeline di Windows PowerShell e le pipeline di shell più popolari e quindi illustra alcuni strumenti di base che è possibile usare per controllare l'output della pipeline e per osservare come funziona la pipeline.

