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
# <a name="cmdlet-attributes"></a><span data-ttu-id="fd500-102">Attributi dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="fd500-102">Cmdlet Attributes</span></span>

<span data-ttu-id="fd500-103">Windows PowerShell definisce diversi attributi che è possibile usare per aggiungere funzionalità comuni ai cmdlet senza implementare tale funzionalità all'interno del proprio codice.</span><span class="sxs-lookup"><span data-stu-id="fd500-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="fd500-104">Questo include l'attributo cmdlet che identifica una classe Microsoft .NET Framework come classe di cmdlet, l'attributo OutputType che specifica i tipi di .NET Framework restituiti dal cmdlet, l'attributo Parameter che identifica le proprietà pubbliche come cmdlet. parametri e altro ancora.</span><span class="sxs-lookup"><span data-stu-id="fd500-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="fd500-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="fd500-105">In This Section</span></span>

<span data-ttu-id="fd500-106">[Attributi nel codice del cmdlet](./attributes-in-cmdlet-code.md) Viene descritto il vantaggio dell'utilizzo degli attributi nel codice del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="fd500-107">[Tipi di attributi](./attribute-types.md) Vengono descritti i diversi attributi che possono decorare una classe di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="fd500-108">[Dichiarazione dell'attributo alias](./alias-attribute-declaration.md) Viene descritto come definire gli alias per il nome di un parametro di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="fd500-109">[Dichiarazione dell'attributo cmdlet](./cmdlet-attribute-declaration.md) Viene descritto come definire una classe .NET Framework come cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="fd500-110">[Dichiarazione dell'attributo Credential](./credential-attribute-declaration.md) Viene descritto come aggiungere il supporto per la conversione di un input di stringa in un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="fd500-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="fd500-111">[Dichiarazione dell'attributo OutputType](./outputtype-attribute-declaration.md) Viene descritto come specificare i tipi di .NET Framework restituiti dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="fd500-112">[Dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md) Viene descritto come definire i parametri di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="fd500-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="fd500-113">[Dichiarazione dell'attributo ValidateCount](./validatecount-attribute-declaration.md) Viene descritto come definire il numero di argomenti consentiti per un parametro.</span><span class="sxs-lookup"><span data-stu-id="fd500-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="fd500-114">[Dichiarazione dell'attributo validateLength](./validatelength-attribute-declaration.md) Viene descritto come definire la lunghezza (in caratteri) di un argomento di parametro.</span><span class="sxs-lookup"><span data-stu-id="fd500-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="fd500-115">[Dichiarazione dell'attributo ValidatePattern](./validatepattern-attribute-declaration.md) Viene descritto come definire i modelli validi per un argomento di parametro.</span><span class="sxs-lookup"><span data-stu-id="fd500-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="fd500-116">[Dichiarazione dell'attributo ValidateRange](./validaterange-attribute-declaration.md) Viene descritto come definire l'intervallo valido per un argomento di parametro.</span><span class="sxs-lookup"><span data-stu-id="fd500-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="fd500-117">[Dichiarazione dell'attributo ValidateSet](./validateset-attribute-declaration.md) Viene descritto come definire i valori possibili per un argomento di parametro.</span><span class="sxs-lookup"><span data-stu-id="fd500-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="fd500-118">Riferimento</span><span class="sxs-lookup"><span data-stu-id="fd500-118">Reference</span></span>

[<span data-ttu-id="fd500-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="fd500-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
