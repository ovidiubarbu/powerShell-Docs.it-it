---
title: Supporto di caratteri jolly in parametri del Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- wildcards [PowerShell Programmer's Guide]
- parameters [PowerShell Programmer's Guide], wildcards
ms.assetid: 9b26e1e9-9350-4a5a-aad5-ddcece658d93
caps.latest.revision: 12
ms.openlocfilehash: 6c762d3889bc4b649252390625525db4735f4c1d
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059610"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Supporto di caratteri jolly nei parametri dei cmdlet

Spesso, è necessario progettare un cmdlet per l'esecuzione in un gruppo di risorse e non su una singola risorsa. Un cmdlet, ad esempio, potrebbe essere necessario individuare tutti i file in un archivio dati che hanno lo stesso nome o l'estensione. Quando si progetta un cmdlet che verrà eseguito con un gruppo di risorse, è necessario fornire supporto per i caratteri jolly.

> [!NOTE]
> Utilizzo di caratteri jolly è talvolta detta *glob*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlet di PowerShell di Windows che usano caratteri jolly

 Molti cmdlet di Windows PowerShell supporta i caratteri jolly per i valori dei parametri. Ad esempio, quasi ogni cmdlet che ha un `Name` o `Path` parametro supporta i caratteri jolly per questi parametri. (Anche se la maggior parte dei cmdlet che hanno una `Path` parametro anche avere un `LiteralPath` parametro che non supporta caratteri jolly.) Il comando seguente viene illustrato come un carattere jolly viene utilizzato per restituire tutti i cmdlet nella sessione corrente il cui nome contiene il verbo Get.

 **PS > get-command get -\***

## <a name="supported-wildcard-characters"></a>Caratteri jolly supportati

Windows PowerShell supporta i caratteri jolly seguenti.

|carattere jolly|Description|Esempio|Corrispondenza|Non corrisponde|
|------------------------|-----------------|-------------|-------------|--------------------|
|*|Corrisponde a zero o più caratteri, iniziando in corrispondenza della posizione specificata|a*|A, ag, Apple||
|?|Corrispondenze di caratteri nella posizione specificata|?n|Un, in, in|è stato eseguito|
|[ ]|Corrisponde a un intervallo di caratteri|[a-l] ook|libro, cook, aspetto|ha impiegato|
|[ ]|Corrisponde ai caratteri specificati|ook [bc]|libro, cook|aspetto|

Quando si progettano i cmdlet che supportano caratteri jolly, consentono alle combinazioni di caratteri jolly. Ad esempio, il comando seguente usa il `Get-ChildItem` cmdlet per recuperare tutti i file. txt che si trovano nella cartella c:\Techdocs e che iniziano con le lettere "a" tramite "l."

**get-childitem c:\techdocs\\[a-l]\*. txt**

Il comando precedente Usa il carattere jolly intervallo **[a-l]** per specificare che il nome del file deve iniziare con i caratteri "a" tramite "l." Il comando Usa quindi il * carattere jolly come segnaposto per qualsiasi carattere compreso tra la prima lettera del nome file e l'estensione. txt.

L'esempio seguente usa un modello con caratteri jolly di intervallo che esclude la lettera "d", ma include tutte le altre lettere da "a" a "f."

**get-childitem c:\techdocs\\[a-cef]\*. txt**

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Gestire i caratteri letterali nei modelli con caratteri jolly

Se il modello con caratteri jolly specificato contiene caratteri letterali, usare il carattere di apice inverso (') come carattere di escape. Quando si specificano caratteri letterali a livello di codice, usare un apice inverso singolo. Quando si specificano caratteri letterali al prompt dei comandi, usare due apici. Ad esempio, il modello seguente contiene due parentesi quadre che devono essere considerati letteralmente.

"John Smith \`[*']" (specificato a livello di codice)

"John Smith \` \`[*\`']" (specificato al prompt dei comandi)

Questo modello corrisponde a "John Smith [Marketing]" o "John Smith [sviluppo per]".

## <a name="cmdlet-output-and-wildcard-characters"></a>Output del cmdlet e i caratteri jolly

Quando i parametri del cmdlet supportano i caratteri jolly, un'operazione di cmdlet genera di norma un output di tipo matrice. In alcuni casi, è opportuno non supporta una matrice di output perché l'utente può usare solo un singolo elemento alla volta. Ad esempio, il `Set-Location` cmdlet supportano una matrice di output perché l'utente imposta solo un'unica posizione. In questo caso, il cmdlet supporta ancora i caratteri jolly, ma lo forza la risoluzione in un'unica posizione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Classe WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
