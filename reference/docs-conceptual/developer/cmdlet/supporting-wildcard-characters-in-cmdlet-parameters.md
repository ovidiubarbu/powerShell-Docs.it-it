---
title: Supporto di caratteri jolly nei parametri dei cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72365310"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a><span data-ttu-id="e03c8-102">Supporto di caratteri jolly nei parametri dei cmdlet</span><span class="sxs-lookup"><span data-stu-id="e03c8-102">Supporting Wildcard Characters in Cmdlet Parameters</span></span>

<span data-ttu-id="e03c8-103">Spesso è necessario progettare un cmdlet per l'esecuzione su un gruppo di risorse invece che su una singola risorsa.</span><span class="sxs-lookup"><span data-stu-id="e03c8-103">Often, you will have to design a cmdlet to run against a group of resources rather than against a single resource.</span></span> <span data-ttu-id="e03c8-104">Ad esempio, un cmdlet potrebbe dover individuare tutti i file in un archivio dati con lo stesso nome o l'estensione.</span><span class="sxs-lookup"><span data-stu-id="e03c8-104">For example, a cmdlet might need to locate all the files in a data store that have the same name or extension.</span></span> <span data-ttu-id="e03c8-105">Quando si progetta un cmdlet che verrà eseguito su un gruppo di risorse, è necessario fornire supporto per i caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="e03c8-105">You must provide support for wildcard characters when you design a cmdlet that will be run against a group of resources.</span></span>

> [!NOTE]
> <span data-ttu-id="e03c8-106">L'uso di caratteri jolly viene talvolta indicato come *glob*.</span><span class="sxs-lookup"><span data-stu-id="e03c8-106">Using wildcard characters is sometimes referred to as *globbing*.</span></span>

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a><span data-ttu-id="e03c8-107">Cmdlet di Windows PowerShell che usano caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="e03c8-107">Windows PowerShell Cmdlets That Use Wildcards</span></span>

 <span data-ttu-id="e03c8-108">Molti cmdlet di Windows PowerShell supportano i caratteri jolly per i valori dei parametri.</span><span class="sxs-lookup"><span data-stu-id="e03c8-108">Many Windows PowerShell cmdlets support wildcard characters for their parameter values.</span></span> <span data-ttu-id="e03c8-109">Ad esempio, quasi tutti i cmdlet con un parametro `Name` o `Path` supportano i caratteri jolly per questi parametri.</span><span class="sxs-lookup"><span data-stu-id="e03c8-109">For example, almost every cmdlet that has a `Name` or `Path` parameter supports wildcard characters for these parameters.</span></span> <span data-ttu-id="e03c8-110">Sebbene la maggior parte dei cmdlet con un parametro di `Path` disponga anche di un parametro di `LiteralPath` che non supporta caratteri jolly. Il seguente comando Mostra come viene usato un carattere jolly per restituire tutti i cmdlet della sessione corrente il cui nome contiene il verbo Get.</span><span class="sxs-lookup"><span data-stu-id="e03c8-110">(Although most cmdlets that have a `Path` parameter also have a `LiteralPath` parameter that does not support wildcard characters.) The following command shows how a wildcard character is used to return all the cmdlets in the current session whose name contains the Get verb.</span></span>

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a><span data-ttu-id="e03c8-111">Caratteri jolly supportati</span><span class="sxs-lookup"><span data-stu-id="e03c8-111">Supported Wildcard Characters</span></span>

<span data-ttu-id="e03c8-112">Windows PowerShell supporta i caratteri jolly seguenti.</span><span class="sxs-lookup"><span data-stu-id="e03c8-112">Windows PowerShell supports the following wildcard characters.</span></span>

| <span data-ttu-id="e03c8-113">Carattere jolly</span><span class="sxs-lookup"><span data-stu-id="e03c8-113">Wildcard</span></span> |                             <span data-ttu-id="e03c8-114">Description</span><span class="sxs-lookup"><span data-stu-id="e03c8-114">Description</span></span>                             |  <span data-ttu-id="e03c8-115">Esempio</span><span class="sxs-lookup"><span data-stu-id="e03c8-115">Example</span></span>   |     <span data-ttu-id="e03c8-116">Corrispondenza</span><span class="sxs-lookup"><span data-stu-id="e03c8-116">Matches</span></span>      | <span data-ttu-id="e03c8-117">Non corrisponde a</span><span class="sxs-lookup"><span data-stu-id="e03c8-117">Does not match</span></span> |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | <span data-ttu-id="e03c8-118">Trova la corrispondenza di zero o più caratteri, a partire dalla posizione specificata</span><span class="sxs-lookup"><span data-stu-id="e03c8-118">Matches zero or more characters, starting at the specified position</span></span> | `a*`       | <span data-ttu-id="e03c8-119">A, AG, Apple</span><span class="sxs-lookup"><span data-stu-id="e03c8-119">A, ag, Apple</span></span>     |                |
| <span data-ttu-id="e03c8-120">?</span><span class="sxs-lookup"><span data-stu-id="e03c8-120">?</span></span>        | <span data-ttu-id="e03c8-121">Corrisponde a qualsiasi carattere nella posizione specificata</span><span class="sxs-lookup"><span data-stu-id="e03c8-121">Matches any character at the specified position</span></span>                     | `?n`       | <span data-ttu-id="e03c8-122">Un, in, on</span><span class="sxs-lookup"><span data-stu-id="e03c8-122">An, in, on</span></span>       | <span data-ttu-id="e03c8-123">corse</span><span class="sxs-lookup"><span data-stu-id="e03c8-123">ran</span></span>            |
| <span data-ttu-id="e03c8-124">[ ]</span><span class="sxs-lookup"><span data-stu-id="e03c8-124">[ ]</span></span>      | <span data-ttu-id="e03c8-125">Corrisponde a un intervallo di caratteri</span><span class="sxs-lookup"><span data-stu-id="e03c8-125">Matches a range of characters</span></span>                                       | `[a-l]ook` | <span data-ttu-id="e03c8-126">libro, cuoco, aspetto</span><span class="sxs-lookup"><span data-stu-id="e03c8-126">book, cook, look</span></span> | <span data-ttu-id="e03c8-127">Nook, ha preso</span><span class="sxs-lookup"><span data-stu-id="e03c8-127">nook, took</span></span>     |
| <span data-ttu-id="e03c8-128">[ ]</span><span class="sxs-lookup"><span data-stu-id="e03c8-128">[ ]</span></span>      | <span data-ttu-id="e03c8-129">Corrisponde ai caratteri specificati</span><span class="sxs-lookup"><span data-stu-id="e03c8-129">Matches the specified characters</span></span>                                    | `[bn]ook`  | <span data-ttu-id="e03c8-130">libro, Nook</span><span class="sxs-lookup"><span data-stu-id="e03c8-130">book, nook</span></span>       | <span data-ttu-id="e03c8-131">cuoco, aspetto</span><span class="sxs-lookup"><span data-stu-id="e03c8-131">cook, look</span></span>     |

<span data-ttu-id="e03c8-132">Quando si progettano i cmdlet che supportano caratteri jolly, consentire combinazioni di caratteri jolly.</span><span class="sxs-lookup"><span data-stu-id="e03c8-132">When you design cmdlets that support wildcard characters, allow for combinations of wildcard characters.</span></span> <span data-ttu-id="e03c8-133">Ad esempio, il comando seguente usa il cmdlet `Get-ChildItem` per recuperare tutti i file con estensione txt presenti nella cartella c:\Techdocs e che iniziano con le lettere "a" e "l".</span><span class="sxs-lookup"><span data-stu-id="e03c8-133">For example, the following command uses the `Get-ChildItem` cmdlet to retrieve all the .txt files that are in the c:\Techdocs folder and that begin with the letters "a" through "l."</span></span>

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

<span data-ttu-id="e03c8-134">Il comando precedente utilizza il carattere jolly di intervallo `[a-l]` per specificare che il nome file deve iniziare con i caratteri "a" e "l" e utilizza il carattere jolly `*` come segnaposto per qualsiasi carattere tra la prima lettera del nome file e l'estensione **txt** .</span><span class="sxs-lookup"><span data-stu-id="e03c8-134">The previous command uses the range wildcard `[a-l]` to specify that the file name should begin with the characters "a" through "l" and uses the `*` wildcard character as a placeholder for any characters between the first letter of the filename and the **.txt** extension.</span></span>

<span data-ttu-id="e03c8-135">Nell'esempio seguente viene usato un modello di carattere jolly di intervallo che esclude la lettera "d", ma include tutte le altre lettere da "a" a "f".</span><span class="sxs-lookup"><span data-stu-id="e03c8-135">The following example uses a range wildcard pattern that excludes the letter "d" but includes all the other letters from "a" through "f."</span></span>

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a><span data-ttu-id="e03c8-136">Gestione dei caratteri letterali nei modelli con caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="e03c8-136">Handling Literal Characters in Wildcard Patterns</span></span>

<span data-ttu-id="e03c8-137">Se il modello con caratteri jolly specificato contiene caratteri letterali che non devono essere interprettedti come caratteri jolly, usare il carattere di apice inverso (`` ` ``) come carattere di escape.</span><span class="sxs-lookup"><span data-stu-id="e03c8-137">If the wildcard pattern you specify contains literal characters that should not be interpretted as wildcard characters, use the backtick character (`` ` ``) as an escape character.</span></span> <span data-ttu-id="e03c8-138">Quando si specificano caratteri letterali int l'API di PowerShell, usare un singolo apice inverso.</span><span class="sxs-lookup"><span data-stu-id="e03c8-138">When you specify literal characters int the PowerShell API, use a single backtick.</span></span> <span data-ttu-id="e03c8-139">Quando si specificano caratteri letterali al prompt dei comandi di PowerShell, usare due apice inverso.</span><span class="sxs-lookup"><span data-stu-id="e03c8-139">When you specify literal characters at the PowerShell command prompt, use two backticks.</span></span>

<span data-ttu-id="e03c8-140">Il modello seguente, ad esempio, contiene due parentesi quadre che devono essere eseguite letteralmente.</span><span class="sxs-lookup"><span data-stu-id="e03c8-140">For example, the following pattern contains two brackets that must be taken literally.</span></span>

<span data-ttu-id="e03c8-141">Quando usato nell'API PowerShell, usare:</span><span class="sxs-lookup"><span data-stu-id="e03c8-141">When used in the PowerShell API use:</span></span>

- <span data-ttu-id="e03c8-142">"John Smith \`[\*']"</span><span class="sxs-lookup"><span data-stu-id="e03c8-142">"John Smith \`[\*\`]"</span></span>

<span data-ttu-id="e03c8-143">Quando viene usato dal prompt dei comandi di PowerShell:</span><span class="sxs-lookup"><span data-stu-id="e03c8-143">When used from the PowerShell command prompt:</span></span>

- <span data-ttu-id="e03c8-144">"John Smith \`\`[\*\`']"</span><span class="sxs-lookup"><span data-stu-id="e03c8-144">"John Smith \`\`[\*\`\`]"</span></span>

<span data-ttu-id="e03c8-145">Questo modello corrisponde a "John Smith [marketing]" o "John Smith [development]".</span><span class="sxs-lookup"><span data-stu-id="e03c8-145">This pattern matches "John Smith [Marketing]" or "John Smith [Development]".</span></span> <span data-ttu-id="e03c8-146">Ad esempio:</span><span class="sxs-lookup"><span data-stu-id="e03c8-146">For example:</span></span>

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a><span data-ttu-id="e03c8-147">Output del cmdlet e caratteri jolly</span><span class="sxs-lookup"><span data-stu-id="e03c8-147">Cmdlet Output and Wildcard Characters</span></span>

<span data-ttu-id="e03c8-148">Quando i parametri del cmdlet supportano i caratteri jolly, l'operazione genera in genere un output di matrice.</span><span class="sxs-lookup"><span data-stu-id="e03c8-148">When cmdlet parameters support wildcard characters, the operation usually generates an array output.</span></span>
<span data-ttu-id="e03c8-149">In alcuni casi non è consigliabile supportare un output di matrice perché l'utente potrebbe usare un solo elemento.</span><span class="sxs-lookup"><span data-stu-id="e03c8-149">Occasionally, it makes no sense to support an array output because the user might use only a single item.</span></span> <span data-ttu-id="e03c8-150">Ad esempio, il cmdlet `Set-Location` non supporta l'output della matrice perché l'utente imposta una sola posizione.</span><span class="sxs-lookup"><span data-stu-id="e03c8-150">For example, the `Set-Location` cmdlet does not support array output because the user sets only a single location.</span></span> <span data-ttu-id="e03c8-151">In questo caso, il cmdlet supporta ancora caratteri jolly, ma forza la risoluzione in un'unica posizione.</span><span class="sxs-lookup"><span data-stu-id="e03c8-151">In this instance, the cmdlet still supports wildcard characters, but it forces resolution to a single location.</span></span>

## <a name="see-also"></a><span data-ttu-id="e03c8-152">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="e03c8-152">See Also</span></span>

[<span data-ttu-id="e03c8-153">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="e03c8-153">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

[<span data-ttu-id="e03c8-154">Classe WildcardPattern</span><span class="sxs-lookup"><span data-stu-id="e03c8-154">WildcardPattern Class</span></span>](/dotnet/api/system.management.automation.wildcardpattern)
