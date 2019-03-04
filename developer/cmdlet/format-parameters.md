---
title: Formattare i parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 10e025c5-9aa6-45a5-b851-23d14db1f4cc
caps.latest.revision: 7
ms.openlocfilehash: 0bd3888d81aa6d1dde26c0066f7bca9dac8a8bca
ms.sourcegitcommit: ce46e5098786e19d521b4bf948ff62d2b90bc53e
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/02/2019
ms.locfileid: "57251184"
---
# <a name="format-parameters"></a><span data-ttu-id="2b7a6-102">Parametri di formattazione</span><span class="sxs-lookup"><span data-stu-id="2b7a6-102">Format Parameters</span></span>

<span data-ttu-id="2b7a6-103">La tabella seguente elenca i nomi consigliati e funzionalità per i parametri che vengono usate per formattare o per generare i dati.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-103">The following table lists recommended names and functionality for parameters that are used to format or to generate data.</span></span>

|<span data-ttu-id="2b7a6-104">Parametro</span><span class="sxs-lookup"><span data-stu-id="2b7a6-104">Parameter</span></span>|<span data-ttu-id="2b7a6-105">Funzionalità</span><span class="sxs-lookup"><span data-stu-id="2b7a6-105">Functionality</span></span>|
|---|---|
|<span data-ttu-id="2b7a6-106">**come**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-106">**As**</span></span><br><span data-ttu-id="2b7a6-107">Tipo di dati: Parola chiave</span><span class="sxs-lookup"><span data-stu-id="2b7a6-107">Data type: Keyword</span></span>|<span data-ttu-id="2b7a6-108">Implementare questo parametro per specificare il formato di output del cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-108">Implement this parameter to specify the cmdlet output format.</span></span> <span data-ttu-id="2b7a6-109">I valori possibili, ad esempio, potrebbero essere testo o uno Script.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-109">For example, possible values could be Text or Script.</span></span>|
|<span data-ttu-id="2b7a6-110">**file binario**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-110">**Binary**</span></span><br><span data-ttu-id="2b7a6-111">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2b7a6-111">Data type: SwitchParameter</span></span>|<span data-ttu-id="2b7a6-112">Implementare questo parametro per indicare che il cmdlet gestisce i valori binari.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-112">Implement this parameter to indicate that the cmdlet handles binary values.</span></span>|
|<span data-ttu-id="2b7a6-113">**Codifica**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-113">**Encoding**</span></span><br><span data-ttu-id="2b7a6-114">Tipo di dati: Parola chiave</span><span class="sxs-lookup"><span data-stu-id="2b7a6-114">Data type: Keyword</span></span>|<span data-ttu-id="2b7a6-115">Implementare questo parametro per specificare il tipo di codifica supportato.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-115">Implement this parameter to specify the type of encoding that is supported.</span></span> <span data-ttu-id="2b7a6-116">I valori possibili, ad esempio, potrebbero essere ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte e stringa.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-116">For example, possible values could be ASCII, UTF8, Unicode, UTF7, BigEndianUnicode, Byte, and String.</span></span>|
|<span data-ttu-id="2b7a6-117">**NewLine**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-117">**NewLine**</span></span><br><span data-ttu-id="2b7a6-118">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2b7a6-118">Data type: SwitchParameter</span></span>|<span data-ttu-id="2b7a6-119">Implementare questo parametro in modo che i caratteri di nuova riga sono supportati quando il parametro è specificato.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-119">Implement this parameter so that the newline characters are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="2b7a6-120">**ShortName**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-120">**ShortName**</span></span><br><span data-ttu-id="2b7a6-121">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2b7a6-121">Data type: SwitchParameter</span></span>|<span data-ttu-id="2b7a6-122">Implementare questo parametro in modo che i nomi brevi sono supportati quando il parametro è specificato.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-122">Implement this parameter so that short names are supported when the parameter is specified.</span></span>|
|<span data-ttu-id="2b7a6-123">**Width**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-123">**Width**</span></span><br><span data-ttu-id="2b7a6-124">Tipo di dati: Int32</span><span class="sxs-lookup"><span data-stu-id="2b7a6-124">Data type: Int32</span></span>|<span data-ttu-id="2b7a6-125">Implementare questo parametro in modo che l'utente può specificare la larghezza della periferica di output.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-125">Implement this parameter so that the user can specify the width of the output device.</span></span>|
|<span data-ttu-id="2b7a6-126">**Eseguire il wrapping**</span><span class="sxs-lookup"><span data-stu-id="2b7a6-126">**Wrap**</span></span><br><span data-ttu-id="2b7a6-127">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="2b7a6-127">Data type: SwitchParameter</span></span>|<span data-ttu-id="2b7a6-128">Implementare questo parametro in modo che la disposizione del testo è supportato quando viene specificato il parametro.</span><span class="sxs-lookup"><span data-stu-id="2b7a6-128">Implement this parameter so that text wrapping is supported when the parameter is specified.</span></span>|
## <a name="see-also"></a><span data-ttu-id="2b7a6-129">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="2b7a6-129">See Also</span></span>

[<span data-ttu-id="2b7a6-130">Parametri del cmdlet</span><span class="sxs-lookup"><span data-stu-id="2b7a6-130">Cmdlet Parameters</span></span>](./cmdlet-parameters.md)

[<span data-ttu-id="2b7a6-131">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="2b7a6-131">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="2b7a6-132">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="2b7a6-132">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
