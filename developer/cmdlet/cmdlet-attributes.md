---
title: Gli attributi di cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- attributes [PowerShell SDK]
- attributes [PowerShell SDK], described
ms.assetid: d3f4f652-d929-4c27-9358-9baa390a094c
caps.latest.revision: 14
ms.openlocfilehash: b06faf7204213b383b25685837941ad63dcb225b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56853917"
---
# <a name="cmdlet-attributes"></a>Attributi dei cmdlet

Windows PowerShell consente di definire diversi attributi che è possibile usare per aggiungere funzionalità comuni per i cmdlet senza implementare tale funzionalità all'interno del proprio codice. Ciò include l'attributo di Cmdlet che identifica una classe di Microsoft .NET Framework come una classe di cmdlet, l'attributo OutputType che specifica i tipi di .NET Framework restituiti dal cmdlet, l'attributo di parametro che identifica le proprietà pubbliche del cmdlet i parametri e così via.

## <a name="in-this-section"></a>Contenuto della sezione

[Gli attributi nel codice del Cmdlet](./attributes-in-cmdlet-code.md) descrive il vantaggio dell'uso di attributi nel codice del cmdlet.

[Tipi di attributo](./attribute-types.md) descrive i diversi attributi che possono decorare una classe cmdlet.

[Dichiarazione di attributo alias](./alias-attribute-declaration.md) viene descritto come definire gli alias per il nome di un parametro di cmdlet.

[Dichiarazione di attributo cmdlet](./cmdlet-attribute-declaration.md) viene descritto come definire una classe .NET Framework come cmdlet.

[Dichiarazione di attributo di credenziali](./credential-attribute-declaration.md) viene descritto come aggiungere il supporto per la conversione di input di stringa in un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto.

[Attributo OutputType dichiarazione](./outputtype-attribute-declaration.md) viene descritto come specificare i tipi di .NET Framework restituiti dal cmdlet.

[Dichiarazione di attributo parametro](./parameter-attribute-declaration.md) viene descritto come definire i parametri di un cmdlet.

[Dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md) viene descritto come definire il numero degli argomenti è consentito per un parametro.

[Dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md) viene descritto come definire la lunghezza (in caratteri) di un argomento del parametro.

[Dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md) viene descritto come definire i modelli validi per un argomento del parametro.

[Dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md) viene descritto come definire l'intervallo valido per un argomento del parametro.

[Dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md) viene descritto come definire i valori possibili per un argomento del parametro.

## <a name="reference"></a>Riferimento

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
