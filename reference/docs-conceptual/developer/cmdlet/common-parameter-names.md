---
title: Nomi di parametro comuni | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0db9f54c-4014-4450-9e81-c9f5fe562a0e
caps.latest.revision: 12
ms.openlocfilehash: c65deeda6b2ef1b52de55035dc606259a7f2d232
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365740"
---
# <a name="common-parameter-names"></a><span data-ttu-id="53f77-102">Nomi dei parametri comuni</span><span class="sxs-lookup"><span data-stu-id="53f77-102">Common Parameter Names</span></span>

<span data-ttu-id="53f77-103">I parametri descritti in questo argomento sono definiti *parametri comuni*.</span><span class="sxs-lookup"><span data-stu-id="53f77-103">The parameters described in this topic are referred to as *common parameters*.</span></span> <span data-ttu-id="53f77-104">Vengono aggiunti ai cmdlet dal runtime di Windows PowerShell e non possono essere dichiarati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53f77-104">They are added to cmdlets by the Windows PowerShell runtime and cannot be declared by the cmdlet.</span></span>

> [!NOTE]
> <span data-ttu-id="53f77-105">Questi parametri vengono inoltre aggiunti ai cmdlet del provider e alle funzioni decorate con l'attributo `CmdletBinding`.</span><span class="sxs-lookup"><span data-stu-id="53f77-105">These parameters are also added to provider cmdlets and to functions that are decorated with the `CmdletBinding` attribute.</span></span>

## <a name="general-common-parameters"></a><span data-ttu-id="53f77-106">Parametri comuni generali</span><span class="sxs-lookup"><span data-stu-id="53f77-106">General Common Parameters</span></span>

<span data-ttu-id="53f77-107">I parametri seguenti vengono aggiunti a tutti i cmdlet ed è possibile accedervi ogni volta che viene eseguito il cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53f77-107">The following parameters are added to all cmdlets and can be accessed whenever the cmdlet is run.</span></span> <span data-ttu-id="53f77-108">Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. parametricomuni](/dotnet/api/System.Management.Automation.Internal.CommonParameters) .</span><span class="sxs-lookup"><span data-stu-id="53f77-108">These parameters are defined by the [System.Management.Automation.Internal.Commonparameters](/dotnet/api/System.Management.Automation.Internal.CommonParameters) class.</span></span>

### <a name="debug-alias-db"></a><span data-ttu-id="53f77-109">Debug (alias: DB)</span><span class="sxs-lookup"><span data-stu-id="53f77-109">Debug (alias: db)</span></span>

<span data-ttu-id="53f77-110">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="53f77-110">Data type: SwitchParameter</span></span>

<span data-ttu-id="53f77-111">Questo parametro specifica se i messaggi di debug a livello di programmatore possono essere visualizzati nella riga di comando.</span><span class="sxs-lookup"><span data-stu-id="53f77-111">This parameter specifies whether programmer-level debugging messages that can be displayed at the command line.</span></span> <span data-ttu-id="53f77-112">Questi messaggi sono intesi per la risoluzione dei problemi relativi al funzionamento del cmdlet e vengono generati dalle chiamate al metodo [System. Management. Automation. cmdlet. WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) .</span><span class="sxs-lookup"><span data-stu-id="53f77-112">These messages are intended for troubleshooting the operation of the cmdlet, and are generated by calls to the [System.Management.Automation.Cmdlet.WriteDebug](/dotnet/api/System.Management.Automation.Cmdlet.WriteDebug) method.</span></span> <span data-ttu-id="53f77-113">Non è necessario localizzare i messaggi di debug.</span><span class="sxs-lookup"><span data-stu-id="53f77-113">Debug messages do not need to be localized.</span></span>

### <a name="erroraction-alias-ea"></a><span data-ttu-id="53f77-114">ErrorAction (alias: EA)</span><span class="sxs-lookup"><span data-stu-id="53f77-114">ErrorAction (alias: ea)</span></span>

<span data-ttu-id="53f77-115">Tipo di dati: enumerazione</span><span class="sxs-lookup"><span data-stu-id="53f77-115">Data type: Enumeration</span></span>

<span data-ttu-id="53f77-116">Questo parametro specifica l'azione che deve essere eseguita quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="53f77-116">This parameter specifies what action should take place when an error occurs.</span></span> <span data-ttu-id="53f77-117">I valori possibili per questo parametro sono definiti dall'enumerazione [System. Management. Automation. preferenzaazione](/dotnet/api/System.Management.Automation.ActionPreference) .</span><span class="sxs-lookup"><span data-stu-id="53f77-117">The possible values for this parameter are defined by the [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeration.</span></span>

### <a name="errorvariable-alias-ev"></a><span data-ttu-id="53f77-118">ErrorVariable (alias: EV)</span><span class="sxs-lookup"><span data-stu-id="53f77-118">ErrorVariable (alias: ev)</span></span>

<span data-ttu-id="53f77-119">Tipo di dati: String</span><span class="sxs-lookup"><span data-stu-id="53f77-119">Data type: String</span></span>

<span data-ttu-id="53f77-120">Questo parametro specifica la variabile in cui inserire gli oggetti quando si verifica un errore.</span><span class="sxs-lookup"><span data-stu-id="53f77-120">This parameter specifies the variable in which to place objects when an error occurs.</span></span> <span data-ttu-id="53f77-121">Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.</span><span class="sxs-lookup"><span data-stu-id="53f77-121">To append to this variable, use +*varname* rather than clearing and setting the variable.</span></span>

### <a name="outvariable-alias-ov"></a><span data-ttu-id="53f77-122">OutVariable (alias: OV)</span><span class="sxs-lookup"><span data-stu-id="53f77-122">OutVariable (alias: ov)</span></span>

<span data-ttu-id="53f77-123">Tipo di dati: String</span><span class="sxs-lookup"><span data-stu-id="53f77-123">Data type: String</span></span>

<span data-ttu-id="53f77-124">Questo parametro specifica la variabile in cui inserire tutti gli oggetti di output generati dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="53f77-124">This parameter specifies the variable in which to place all output objects generated by the cmdlet.</span></span> <span data-ttu-id="53f77-125">Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.</span><span class="sxs-lookup"><span data-stu-id="53f77-125">To append to this variable, use +*varname* rather than clearing and setting the variable.</span></span>

### <a name="outbuffer-alias-ob"></a><span data-ttu-id="53f77-126">OutBuffer (alias: ob)</span><span class="sxs-lookup"><span data-stu-id="53f77-126">OutBuffer (alias: ob)</span></span>

<span data-ttu-id="53f77-127">Tipo di dati: Int32</span><span class="sxs-lookup"><span data-stu-id="53f77-127">Data type: Int32</span></span>

<span data-ttu-id="53f77-128">Questo parametro definisce il numero di oggetti da archiviare nel buffer di output prima che gli oggetti vengano passati alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="53f77-128">This parameter defines the number of objects to store in the output buffer before any objects are passed down the pipeline.</span></span> <span data-ttu-id="53f77-129">Per impostazione predefinita, gli oggetti vengono passati immediatamente alla pipeline.</span><span class="sxs-lookup"><span data-stu-id="53f77-129">By default, objects are passed immediately down the pipeline.</span></span>

### <a name="verbose-alias-vb"></a><span data-ttu-id="53f77-130">Verbose (alias: VB)</span><span class="sxs-lookup"><span data-stu-id="53f77-130">Verbose (alias: vb)</span></span>

<span data-ttu-id="53f77-131">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="53f77-131">Data type: SwitchParameter</span></span>

<span data-ttu-id="53f77-132">Questo parametro specifica se il cmdlet scrive messaggi esplicativi che possono essere visualizzati dalla riga di comando.</span><span class="sxs-lookup"><span data-stu-id="53f77-132">This parameter specifies whether the cmdlet writes explanatory messages that can be displayed at the command line.</span></span> <span data-ttu-id="53f77-133">Questi messaggi hanno lo scopo di fornire ulteriore assistenza all'utente e vengono generati dalle chiamate al metodo [System. Management. Automation. cmdlet. WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) .</span><span class="sxs-lookup"><span data-stu-id="53f77-133">These messages are intended to provide additional help to the user, and are generated by calls to the [System.Management.Automation.Cmdlet.WriteVerbose](/dotnet/api/System.Management.Automation.Cmdlet.WriteVerbose) method.</span></span>

### <a name="warningaction-alias-wa"></a><span data-ttu-id="53f77-134">WarningAction (alias: WA)</span><span class="sxs-lookup"><span data-stu-id="53f77-134">WarningAction (alias: wa)</span></span>

<span data-ttu-id="53f77-135">Tipo di dati: enumerazione</span><span class="sxs-lookup"><span data-stu-id="53f77-135">Data type: Enumeration</span></span>

<span data-ttu-id="53f77-136">Questo parametro specifica l'azione che deve essere eseguita quando il cmdlet scrive un messaggio di avviso.</span><span class="sxs-lookup"><span data-stu-id="53f77-136">This parameter specifies what action should take place when the cmdlet writes a warning message.</span></span> <span data-ttu-id="53f77-137">I valori possibili per questo parametro sono definiti dall'enumerazione [System. Management. Automation. preferenzaazione](/dotnet/api/System.Management.Automation.ActionPreference) .</span><span class="sxs-lookup"><span data-stu-id="53f77-137">The possible values for this parameter are defined by the [System.Management.Automation.Actionpreference](/dotnet/api/System.Management.Automation.ActionPreference) enumeration.</span></span>

### <a name="warningvariable-alias-wv"></a><span data-ttu-id="53f77-138">WarningVariable (alias: WV)</span><span class="sxs-lookup"><span data-stu-id="53f77-138">WarningVariable (alias: wv)</span></span>

<span data-ttu-id="53f77-139">Tipo di dati: String</span><span class="sxs-lookup"><span data-stu-id="53f77-139">Data type: String</span></span>

<span data-ttu-id="53f77-140">Questo parametro specifica la variabile in cui è possibile salvare i messaggi di avviso.</span><span class="sxs-lookup"><span data-stu-id="53f77-140">This parameter specifies the variable in which warning messages can be saved.</span></span> <span data-ttu-id="53f77-141">Per accodare questa variabile, utilizzare +*VarName* anziché cancellare e impostare la variabile.</span><span class="sxs-lookup"><span data-stu-id="53f77-141">To append to this variable, use +*varname* rather than clearing and setting the variable.</span></span>

## <a name="risk-mitigation-parameters"></a><span data-ttu-id="53f77-142">Parametri di mitigazione dei rischi</span><span class="sxs-lookup"><span data-stu-id="53f77-142">Risk-Mitigation Parameters</span></span>

<span data-ttu-id="53f77-143">I parametri seguenti vengono aggiunti ai cmdlet che richiedono la conferma prima di eseguire l'azione.</span><span class="sxs-lookup"><span data-stu-id="53f77-143">The following parameters are added to cmdlets that requests confirmation before they perform their action.</span></span> <span data-ttu-id="53f77-144">Per ulteriori informazioni sulle richieste di conferma, vedere [richiesta di conferma](./requesting-confirmation-from-cmdlets.md).</span><span class="sxs-lookup"><span data-stu-id="53f77-144">For more information about confirmation requests, see [Requesting Confirmation](./requesting-confirmation-from-cmdlets.md).</span></span> <span data-ttu-id="53f77-145">Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) .</span><span class="sxs-lookup"><span data-stu-id="53f77-145">These parameters are defined by the [System.Management.Automation.Internal.Shouldprocessparameters](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters) class.</span></span>

### <a name="confirm-alias-cf"></a><span data-ttu-id="53f77-146">Conferma (alias: CF)</span><span class="sxs-lookup"><span data-stu-id="53f77-146">Confirm (alias: cf)</span></span>

<span data-ttu-id="53f77-147">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="53f77-147">Data type: SwitchParameter</span></span>

<span data-ttu-id="53f77-148">Questo parametro specifica se il cmdlet visualizza un messaggio che chiede se l'utente è sicuro di voler continuare.</span><span class="sxs-lookup"><span data-stu-id="53f77-148">This parameter specifies whether the cmdlet displays a prompt that asks if the user is sure that they want to continue.</span></span>

### <a name="whatif-alias-wi"></a><span data-ttu-id="53f77-149">WhatIf (alias: Wi)</span><span class="sxs-lookup"><span data-stu-id="53f77-149">WhatIf (alias: wi)</span></span>

<span data-ttu-id="53f77-150">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="53f77-150">Data type: SwitchParameter</span></span>

<span data-ttu-id="53f77-151">Questo parametro specifica se il cmdlet scrive un messaggio che descrive gli effetti dell'esecuzione del cmdlet senza eseguire effettivamente alcuna azione.</span><span class="sxs-lookup"><span data-stu-id="53f77-151">This parameter specifies whether the cmdlet writes a message that describes the effects of running the cmdlet without actually performing any action.</span></span>

## <a name="transaction-parameters"></a><span data-ttu-id="53f77-152">Parametri di transazione</span><span class="sxs-lookup"><span data-stu-id="53f77-152">Transaction Parameters</span></span>

<span data-ttu-id="53f77-153">Il parametro seguente viene aggiunto ai cmdlet che supportano le transazioni.</span><span class="sxs-lookup"><span data-stu-id="53f77-153">The following parameter is added to cmdlets that support transactions.</span></span> <span data-ttu-id="53f77-154">Questi parametri sono definiti dalla classe [System. Management. Automation. Internal. Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) .</span><span class="sxs-lookup"><span data-stu-id="53f77-154">These parameters are defined by the [System.Management.Automation.Internal.Transactionparameters](/dotnet/api/System.Management.Automation.Internal.TransactionParameters) class.</span></span>

### <a name="usetransaction-alias-usetx"></a><span data-ttu-id="53f77-155">UseTransaction (alias: UseTx)</span><span class="sxs-lookup"><span data-stu-id="53f77-155">UseTransaction (alias: usetx)</span></span>

<span data-ttu-id="53f77-156">Tipo di dati: SwitchParameter</span><span class="sxs-lookup"><span data-stu-id="53f77-156">Data type: SwitchParameter</span></span>

<span data-ttu-id="53f77-157">Questo parametro specifica se il cmdlet utilizzerà la transazione corrente per eseguire l'azione.</span><span class="sxs-lookup"><span data-stu-id="53f77-157">This parameter specifies whether the cmdlet will use the current transaction to perform its action.</span></span>

## <a name="see-also"></a><span data-ttu-id="53f77-158">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="53f77-158">See Also</span></span>

[<span data-ttu-id="53f77-159">System. Management. Automation. Internal. Parametricomuni</span><span class="sxs-lookup"><span data-stu-id="53f77-159">System.Management.Automation.Internal.Commonparameters</span></span>](/dotnet/api/System.Management.Automation.Internal.CommonParameters)

[<span data-ttu-id="53f77-160">System. Management. Automation. Internal. Shouldprocessparameters</span><span class="sxs-lookup"><span data-stu-id="53f77-160">System.Management.Automation.Internal.Shouldprocessparameters</span></span>](/dotnet/api/System.Management.Automation.Internal.ShouldProcessParameters)

[<span data-ttu-id="53f77-161">System. Management. Automation. Internal. Transactionparameters</span><span class="sxs-lookup"><span data-stu-id="53f77-161">System.Management.Automation.Internal.Transactionparameters</span></span>](/dotnet/api/System.Management.Automation.Internal.TransactionParameters)

[<span data-ttu-id="53f77-162">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="53f77-162">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="53f77-163">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="53f77-163">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)