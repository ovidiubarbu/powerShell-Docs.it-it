---
title: Supporto di caratteri jolly in parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 296490e4692e72f823be0b00aee90dc8c3dc9131
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56862517"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="c547b-102">Supporto di caratteri jolly nei parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="c547b-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="c547b-103">Spesso, è necessario progettare un cmdlet per l'esecuzione in un gruppo di risorse e non su una singola risorsa.</span><span class="sxs-lookup"><span data-stu-id="c547b-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="c547b-104">Un cmdlet, ad esempio, potrebbe essere necessario individuare tutti i file in un archivio dati che hanno lo stesso nome o l'estensione.</span><span class="sxs-lookup"><span data-stu-id="c547b-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="c547b-105">Quando si progetta un cmdlet che verrà eseguito con un gruppo di risorse, è necessario fornire supporto per i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="c547b-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="c547b-106">Utilizzo di caratteri jolly è talvolta detta *glob*.</span><span class="sxs-lookup"><span data-stu-id="c547b-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="c547b-107">Cmdlet di PowerShell di Windows che usano caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="c547b-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="c547b-108">Molti cmdlet di Windows PowerShell supporta i caratteri jolly per i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="c547b-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="c547b-109">Ad esempio, quasi ogni cmdlet che ha un `Name` o `Path` parametro supporta i caratteri jolly per questi parametri.</span><span class="sxs-lookup"><span data-stu-id="c547b-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="c547b-110">(Anche se la maggior parte dei cmdlet che hanno una `Path` parametro anche avere un `LiteralPath` parametro che non supporta caratteri jolly.) Il comando seguente viene illustrato come un carattere jolly viene utilizzato per restituire tutti i cmdlet nella sessione corrente il cui nome contiene il verbo Get.</span><span class="sxs-lookup"><span data-stu-id="c547b-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 <span data-ttu-id="c547b-111">**PS > get-command get -\***</span><span class="sxs-lookup"><span data-stu-id="c547b-111">**PS>get-command get-\***</span></span>

## <a name="supported-wildcard-characters"></a><span data-ttu-id="c547b-112">Caratteri jolly supportati</span><span class="sxs-lookup"><span data-stu-id="c547b-112">Supported Wildcard Characters</span></span>

<span data-ttu-id="c547b-113">Windows PowerShell supporta i caratteri jolly seguenti.</span><span class="sxs-lookup"><span data-stu-id="c547b-113">Windows PowerShell supports the following wildcard characters.</span></span>

|<span data-ttu-id="c547b-114">carattere jolly</span><span class="sxs-lookup"><span data-stu-id="c547b-114">Wildcard character</span></span>|<span data-ttu-id="c547b-115">Description</span><span class="sxs-lookup"><span data-stu-id="c547b-115">Description</span></span>|<span data-ttu-id="c547b-116">Esempio</span><span class="sxs-lookup"><span data-stu-id="c547b-116">Example</span></span>|<span data-ttu-id="c547b-117">Corrispondenza</span><span class="sxs-lookup"><span data-stu-id="c547b-117">Matches</span></span>|<span data-ttu-id="c547b-118">Non corrisponde</span><span class="sxs-lookup"><span data-stu-id="c547b-118">Does not match</span></span>|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|<span data-ttu-id="c547b-119">Corrisponde a zero o più caratteri, iniziando in corrispondenza della posizione specificata</span><span class="sxs-lookup"><span data-stu-id="c547b-119">Matches zero or more characters, starting at the specified position</span></span>|<span data-ttu-id="c547b-120">a\*</span><span class="sxs-lookup"><span data-stu-id="c547b-120">a\*</span></span>|<span data-ttu-id="c547b-121">A, ag, Apple</span><span class="sxs-lookup"><span data-stu-id="c547b-121">A, ag, Apple</span></span>||
|<span data-ttu-id="c547b-122">?</span><span class="sxs-lookup"><span data-stu-id="c547b-122">?</span></span>|<span data-ttu-id="c547b-123">Corrispondenze di caratteri nella posizione specificata</span><span class="sxs-lookup"><span data-stu-id="c547b-123">Matches anycharacter at the specified position</span></span>|<span data-ttu-id="c547b-124">?n</span><span class="sxs-lookup"><span data-stu-id="c547b-124">?n</span></span>|<span data-ttu-id="c547b-125">Un, in, in</span><span class="sxs-lookup"><span data-stu-id="c547b-125">An, in, on</span></span>|<span data-ttu-id="c547b-126">è stato eseguito</span><span class="sxs-lookup"><span data-stu-id="c547b-126">ran</span></span>|
|<span data-ttu-id="c547b-127">[ ]</span><span class="sxs-lookup"><span data-stu-id="c547b-127">[ ]</span></span>|<span data-ttu-id="c547b-128">Corrisponde a un intervallo di caratteri</span><span class="sxs-lookup"><span data-stu-id="c547b-128">Matches a range of characters</span></span>|<span data-ttu-id="c547b-129">[a-l] ook</span><span class="sxs-lookup"><span data-stu-id="c547b-129">[a-l]ook</span></span>|<span data-ttu-id="c547b-130">libro, cook, aspetto</span><span class="sxs-lookup"><span data-stu-id="c547b-130">book, cook, look</span></span>|<span data-ttu-id="c547b-131">ha impiegato</span><span class="sxs-lookup"><span data-stu-id="c547b-131">took</span></span>|
|<span data-ttu-id="c547b-132">[ ]</span><span class="sxs-lookup"><span data-stu-id="c547b-132">[ ]</span></span>|<span data-ttu-id="c547b-133">Corrisponde ai caratteri specificati</span><span class="sxs-lookup"><span data-stu-id="c547b-133">Matches the specified characters</span></span>|<span data-ttu-id="c547b-134">ook [bc]</span><span class="sxs-lookup"><span data-stu-id="c547b-134">[bc]ook</span></span>|<span data-ttu-id="c547b-135">libro, cook</span><span class="sxs-lookup"><span data-stu-id="c547b-135">book, cook</span></span>|<span data-ttu-id="c547b-136">aspetto</span><span class="sxs-lookup"><span data-stu-id="c547b-136">look</span></span>|

<span data-ttu-id="c547b-137">Quando si progettano i cmdlet che supportano caratteri jolly, consentono alle combinazioni di caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="c547b-137">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="c547b-138">Ad esempio, il comando seguente usa il `Get-ChildItem` cmdlet per recuperare tutti i file. txt che si trovano nella cartella c:\Techdocs e che iniziano con le lettere "a" tramite "l."</span><span class="sxs-lookup"><span data-stu-id="c547b-138">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

<span data-ttu-id="c547b-139">**get-childitem c:\techdocs\\[a-l]\*. txt**</span><span class="sxs-lookup"><span data-stu-id="c547b-139">**get-childitem c:\techdocs\\[a-l]\*.txt**</span></span>

<span data-ttu-id="c547b-140">Il comando precedente Usa il carattere jolly intervallo **[a-l]** per specificare che il nome del file deve iniziare con i caratteri "a" tramite "l."</span><span class="sxs-lookup"><span data-stu-id="c547b-140">The previous command uses the range wildcard **[a-l]** to specify that the file name should begin with the characters "a" through "l."</span></span> <span data-ttu-id="c547b-141">Il comando Usa quindi il \* carattere jolly come segnaposto per qualsiasi carattere compreso tra la prima lettera del nome file e l'estensione. txt.</span><span class="sxs-lookup"><span data-stu-id="c547b-141">The command then uses the \* wildcard character as a placeholder for any characters between the first letter of the file name and the .txt extension.</span></span>

<span data-ttu-id="c547b-142">L'esempio seguente usa un modello con caratteri jolly di intervallo che esclude la lettera "d", ma include tutte le altre lettere da "a" a "f."</span><span class="sxs-lookup"><span data-stu-id="c547b-142">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

<span data-ttu-id="c547b-143">**get-childitem c:\techdocs\\[a-cef]\*. txt**</span><span class="sxs-lookup"><span data-stu-id="c547b-143">**get-childitem c:\techdocs\\[a-cef]\*.txt**</span></span>

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="c547b-144">Gestire i caratteri letterali nei modelli con caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="c547b-144">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="c547b-145">Se il modello con caratteri jolly specificato contiene caratteri letterali, usare il carattere di apice inverso (') come carattere di escape.</span><span class="sxs-lookup"><span data-stu-id="c547b-145">If the wildcard pattern you specify contains literal characters, use the backtick character (\`) as an escape character.</span></span> <span data-ttu-id="c547b-146">Quando si specificano caratteri letterali a livello di codice, usare un apice inverso singolo.</span><span class="sxs-lookup"><span data-stu-id="c547b-146">When you specify literal characters programmatically, use a single backtick.</span></span> <span data-ttu-id="c547b-147">Quando si specificano caratteri letterali al prompt dei comandi, usare due apici.</span><span class="sxs-lookup"><span data-stu-id="c547b-147">When you specify literal characters at the command prompt, use two backticks.</span></span> <span data-ttu-id="c547b-148">Ad esempio, il modello seguente contiene due parentesi quadre che devono essere considerati letteralmente.</span><span class="sxs-lookup"><span data-stu-id="c547b-148">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="c547b-149">"John Smith \`[\*']" (specificato a livello di codice)</span><span class="sxs-lookup"><span data-stu-id="c547b-149">"John Smith \`[\*\`]" (specified programmatically)</span></span>

<span data-ttu-id="c547b-150">"John Smith \` \`[\*\`']" (specificato al prompt dei comandi)</span><span class="sxs-lookup"><span data-stu-id="c547b-150">"John Smith \`\`[\*\`\`]"  (specified at the command prompt)</span></span>

<span data-ttu-id="c547b-151">Questo modello corrisponde a "John Smith [Marketing]" o "John Smith [sviluppo per]".</span><span class="sxs-lookup"><span data-stu-id="c547b-151">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span>

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="c547b-152">Output del cmdlet e i caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="c547b-152">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="c547b-153">Quando i parametri del cmdlet supportano i caratteri jolly, un'operazione di cmdlet genera di norma un output di tipo matrice.</span><span class="sxs-lookup"><span data-stu-id="c547b-153">When cmdlet parameters support wildcard characters, a cmdlet operation usually generates an array output.</span></span> <span data-ttu-id="c547b-154">In alcuni casi, è opportuno non supporta una matrice di output perché l'utente può usare solo un singolo elemento alla volta.</span><span class="sxs-lookup"><span data-stu-id="c547b-154">Occasionally, it makes no sense to support an array output because the user might use only a single item at a time.</span></span> <span data-ttu-id="c547b-155">Ad esempio, il `Set-Location` cmdlet supportano una matrice di output perché l'utente imposta solo un'unica posizione.</span><span class="sxs-lookup"><span data-stu-id="c547b-155">For example, the `Set-Location` cmdlet does support an array output because the user sets only a single location.</span></span> <span data-ttu-id="c547b-156">In questo caso, il cmdlet supporta ancora i caratteri jolly, ma lo forza la risoluzione in un'unica posizione.</span><span class="sxs-lookup"><span data-stu-id="c547b-156">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="c547b-157">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="c547b-157">See Also</span></span>

[<span data-ttu-id="c547b-158">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="c547b-158">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="c547b-159">Classe WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="c547b-159">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
