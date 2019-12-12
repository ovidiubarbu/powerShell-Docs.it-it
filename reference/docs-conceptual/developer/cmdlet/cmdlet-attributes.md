---
title: Attributi cmdlet | Microsoft Docs
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
ms.openlocfilehash: 326cd408e86402974569fc76d5e473be5a56f0b6
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369960"
---
# <a name="cmdlet-attributes"></a>Attributi dei cmdlet

Windows PowerShell definisce diversi attributi che è possibile usare per aggiungere funzionalità comuni ai cmdlet senza implementare tale funzionalità all'interno del proprio codice. Questo include l'attributo cmdlet che identifica una classe Microsoft .NET Framework come classe di cmdlet, l'attributo OutputType che specifica i tipi di .NET Framework restituiti dal cmdlet, l'attributo Parameter che identifica le proprietà pubbliche come cmdlet. parametri e altro ancora.

## <a name="in-this-section"></a>Contenuto della sezione

[Attributi nel codice del cmdlet](./attributes-in-cmdlet-code.md) Viene descritto il vantaggio dell'utilizzo degli attributi nel codice del cmdlet.

[Tipi di attributi](./attribute-types.md) Vengono descritti i diversi attributi che possono decorare una classe di cmdlet.

[Dichiarazione dell'attributo alias](./alias-attribute-declaration.md) Viene descritto come definire gli alias per il nome di un parametro di un cmdlet.

[Dichiarazione dell'attributo cmdlet](./cmdlet-attribute-declaration.md) Viene descritto come definire una classe .NET Framework come cmdlet.

[Dichiarazione dell'attributo Credential](./credential-attribute-declaration.md) Viene descritto come aggiungere il supporto per la conversione di un input di stringa in un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .

[Dichiarazione dell'attributo OutputType](./outputtype-attribute-declaration.md) Viene descritto come specificare i tipi di .NET Framework restituiti dal cmdlet.

[Dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md) Viene descritto come definire i parametri di un cmdlet.

[Dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md) Viene descritto come definire il numero di argomenti consentiti per un parametro.

[Dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md) Viene descritto come definire la lunghezza (in caratteri) di un argomento di parametro.

[Dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md) Viene descritto come definire i modelli validi per un argomento di parametro.

[Dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md) Viene descritto come definire l'intervallo valido per un argomento di parametro.

[Dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md) Viene descritto come definire i valori possibili per un argomento di parametro.

## <a name="reference"></a>Riferimento

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
