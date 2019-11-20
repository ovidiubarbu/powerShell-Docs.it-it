---
title: Parametri di formato | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369750"
---
# <a name="format-parameters"></a><span data-ttu-id="ff3fc-102">Parametri di formattazione</span><span class="sxs-lookup"><span data-stu-id="ff3fc-102">Format Parameters</span></span>

<span data-ttu-id="ff3fc-103">Nella tabella seguente sono elencati i nomi e le funzionalità consigliati per i parametri utilizzati per formattare o generare dati.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="ff3fc-104">Parametro</span><span class="sxs-lookup"><span data-stu-id="ff3fc-104">Parameter</span></span>|<span data-ttu-id="ff3fc-105">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="ff3fc-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="ff3fc-106">**Come**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-106">**As**</span></span><br><span data-ttu-id="ff3fc-107">Tipo di dati: parola chiave</span><span class="sxs-lookup"><span data-stu-id="ff3fc-107">Data type: Keyword</span></span>|<span data-ttu-id="ff3fc-108">Implementare questo parametro per specificare il formato di output del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="ff3fc-109">Ad esempio, i valori possibili potrebbero essere testo o script.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="ff3fc-110">**Binario**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-110">**Binary**</span></span><br><span data-ttu-id="ff3fc-111">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff3fc-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="ff3fc-112">Implementare questo parametro per indicare che il cmdlet gestisce i valori binari.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="ff3fc-113">**Codifica**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-113">**Encoding**</span></span><br><span data-ttu-id="ff3fc-114">Tipo di dati: parola chiave</span><span class="sxs-lookup"><span data-stu-id="ff3fc-114">Data type: Keyword</span></span>|<span data-ttu-id="ff3fc-115">Implementare questo parametro per specificare il tipo di codifica supportata.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="ff3fc-116">Ad esempio, i valori possibili sono ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, byte e String.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="ff3fc-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-117">**NewLine**</span></span><br><span data-ttu-id="ff3fc-118">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff3fc-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="ff3fc-119">Implementare questo parametro in modo che i caratteri di nuova riga siano supportati quando si specifica il parametro.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="ff3fc-120">**Nome breve**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-120">**ShortName**</span></span><br><span data-ttu-id="ff3fc-121">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff3fc-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="ff3fc-122">Implementare questo parametro in modo che i nomi brevi siano supportati quando si specifica il parametro.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="ff3fc-123">**Larghezza**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-123">**Width**</span></span><br><span data-ttu-id="ff3fc-124">Tipo di dati: Int32</span><span class="sxs-lookup"><span data-stu-id="ff3fc-124">Data type: Int32</span></span>|<span data-ttu-id="ff3fc-125">Implementare questo parametro in modo che l'utente possa specificare la larghezza del dispositivo di output.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="ff3fc-126">**Avvolgere**</span><span class="sxs-lookup"><span data-stu-id="ff3fc-126">**Wrap**</span></span><br><span data-ttu-id="ff3fc-127">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="ff3fc-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="ff3fc-128">Implementare questo parametro in modo che il ritorno a capo del testo sia supportato quando si specifica il parametro.</span><span class="sxs-lookup"><span data-stu-id="ff3fc-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="ff3fc-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="ff3fc-129">See Also</span></span>

[<span data-ttu-id="ff3fc-130">Parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="ff3fc-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="ff3fc-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ff3fc-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="ff3fc-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="ff3fc-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)