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
# <a name="cmdlet-attributes"></a><span data-ttu-id="70bb2-102">Attributi dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="70bb2-102">Cmdlet Attributes</span></span>

<span data-ttu-id="70bb2-103">Windows PowerShell consente di definire diversi attributi che è possibile usare per aggiungere funzionalità comuni per i cmdlet senza implementare tale funzionalità all'interno del proprio codice.</span><span class="sxs-lookup"><span data-stu-id="70bb2-103">Windows PowerShell defines several attributes that you can use to add common functionality to your cmdlets without implementing that functionality within your own code.</span></span> <span data-ttu-id="70bb2-104">Ciò include l'attributo di Cmdlet che identifica una classe di Microsoft .NET Framework come una classe di cmdlet, l'attributo OutputType che specifica i tipi di .NET Framework restituiti dal cmdlet, l'attributo di parametro che identifica le proprietà pubbliche del cmdlet i parametri e così via.</span><span class="sxs-lookup"><span data-stu-id="70bb2-104">This includes the Cmdlet attribute that identifies a Microsoft .NET Framework class as a cmdlet class, the OutputType attribute that specifies the .NET Framework types returned by the cmdlet, the Parameter attribute that identifies public properties as cmdlet parameters, and more.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="70bb2-105">Contenuto della sezione</span><span class="sxs-lookup"><span data-stu-id="70bb2-105">In This Section</span></span>

<span data-ttu-id="70bb2-106">[Gli attributi nel codice del Cmdlet](./attributes-in-cmdlet-code.md) descrive il vantaggio dell'uso di attributi nel codice del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-106">[Attributes in Cmdlet Code](./attributes-in-cmdlet-code.md) Describes the benefit of using attributes in cmdlet code.</span></span>

<span data-ttu-id="70bb2-107">[Tipi di attributo](./attribute-types.md) descrive i diversi attributi che possono decorare una classe cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-107">[Attribute Types](./attribute-types.md) Describes the different attributes that can decorate a cmdlet class.</span></span>

<span data-ttu-id="70bb2-108">[Dichiarazione di attributo alias](./alias-attribute-declaration.md) viene descritto come definire gli alias per il nome di un parametro di cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-108">[Alias Attribute Declaration](./alias-attribute-declaration.md) Describes how to define aliases for a cmdlet parameter name.</span></span>

<span data-ttu-id="70bb2-109">[Dichiarazione di attributo cmdlet](./cmdlet-attribute-declaration.md) viene descritto come definire una classe .NET Framework come cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-109">[Cmdlet Attribute Declaration](./cmdlet-attribute-declaration.md) Describes how to define a .NET Framework class as a cmdlet.</span></span>

<span data-ttu-id="70bb2-110">[Dichiarazione di attributo di credenziali](./credential-attribute-declaration.md) viene descritto come aggiungere il supporto per la conversione di input di stringa in un [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto.</span><span class="sxs-lookup"><span data-stu-id="70bb2-110">[Credential Attribute Declaration](./credential-attribute-declaration.md) Describes how to add support for converting string input into a [System.Management.Automation.Pscredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span>

<span data-ttu-id="70bb2-111">[Attributo OutputType dichiarazione](./outputtype-attribute-declaration.md) viene descritto come specificare i tipi di .NET Framework restituiti dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-111">[OutputType attribute Declaration](./outputtype-attribute-declaration.md) Describes how to specify the .NET Framework types returned by the cmdlet.</span></span>

<span data-ttu-id="70bb2-112">[Dichiarazione di attributo parametro](./parameter-attribute-declaration.md) viene descritto come definire i parametri di un cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70bb2-112">[Parameter Attribute Declaration](./parameter-attribute-declaration.md) Describes how to define the parameters of a cmdlet.</span></span>

<span data-ttu-id="70bb2-113">[Dichiarazione di attributo ValidateCount](./validatecount-attribute-declaration.md) viene descritto come definire il numero degli argomenti è consentito per un parametro.</span><span class="sxs-lookup"><span data-stu-id="70bb2-113">[ValidateCount Attribute Declaration](./validatecount-attribute-declaration.md) Describes how to define how many arguments are allowed for a parameter.</span></span>

<span data-ttu-id="70bb2-114">[Dichiarazione di attributo ValidateLength](./validatelength-attribute-declaration.md) viene descritto come definire la lunghezza (in caratteri) di un argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="70bb2-114">[ValidateLength Attribute Declaration](./validatelength-attribute-declaration.md) Describes how to define the length (in characters) of a parameter argument.</span></span>

<span data-ttu-id="70bb2-115">[Dichiarazione di attributo ValidatePattern](./validatepattern-attribute-declaration.md) viene descritto come definire i modelli validi per un argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="70bb2-115">[ValidatePattern Attribute Declaration](./validatepattern-attribute-declaration.md) Describes how to define the valid patterns for a parameter argument.</span></span>

<span data-ttu-id="70bb2-116">[Dichiarazione di attributo ValidateRange](./validaterange-attribute-declaration.md) viene descritto come definire l'intervallo valido per un argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="70bb2-116">[ValidateRange Attribute Declaration](./validaterange-attribute-declaration.md) Describes how to define the valid range for a parameter argument.</span></span>

<span data-ttu-id="70bb2-117">[Dichiarazione di attributo ValidateSet](./validateset-attribute-declaration.md) viene descritto come definire i valori possibili per un argomento del parametro.</span><span class="sxs-lookup"><span data-stu-id="70bb2-117">[ValidateSet Attribute Declaration](./validateset-attribute-declaration.md) Describes how to define the possible values for a parameter argument.</span></span>

## <a name="reference"></a><span data-ttu-id="70bb2-118">Riferimento</span><span class="sxs-lookup"><span data-stu-id="70bb2-118">Reference</span></span>

[<span data-ttu-id="70bb2-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="70bb2-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
