---
title: Supporto di caratteri jolly nei parametri dei cmdlet
ms.custom: ''
ms.date: 08/26/2019
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.openlocfilehash: 19644c5bc186a5554d6b134a67fc7c4d7aa7b64c
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72365310"
---
# <a name="supporting-wildcard-characters-in-cmdlet-parameters"></a>Supporto di caratteri jolly nei parametri dei cmdlet

Spesso è necessario progettare un cmdlet per l'esecuzione su un gruppo di risorse invece che su una singola risorsa. Ad esempio, un cmdlet potrebbe dover individuare tutti i file in un archivio dati con lo stesso nome o l'estensione. Quando si progetta un cmdlet che verrà eseguito su un gruppo di risorse, è necessario fornire supporto per i caratteri jolly.

> [!NOTE]
> L'uso di caratteri jolly viene talvolta indicato come *glob*.

## <a name="windows-powershell-cmdlets-that-use-wildcards"></a>Cmdlet di Windows PowerShell che usano caratteri jolly

 Molti cmdlet di Windows PowerShell supportano i caratteri jolly per i valori dei parametri. Ad esempio, quasi tutti i cmdlet con un parametro `Name` o `Path` supportano i caratteri jolly per questi parametri. Sebbene la maggior parte dei cmdlet con un parametro di `Path` disponga anche di un parametro di `LiteralPath` che non supporta caratteri jolly. Il seguente comando Mostra come viene usato un carattere jolly per restituire tutti i cmdlet della sessione corrente il cui nome contiene il verbo Get.

 `Get-Command get-*`

## <a name="supported-wildcard-characters"></a>Caratteri jolly supportati

Windows PowerShell supporta i caratteri jolly seguenti.

| Jolly |                             Descrizione                             |  Esempio   |     Corrispondenza      | Non corrisponde a |
| -------- | ------------------------------------------------------------------- | ---------- | ---------------- | -------------- |
| *        | Trova la corrispondenza di zero o più caratteri, a partire dalla posizione specificata | `a*`       | A, AG, Apple     |                |
| ?        | Corrisponde a qualsiasi carattere nella posizione specificata                     | `?n`       | Un, in, on       | corse            |
| [ ]      | Corrisponde a un intervallo di caratteri                                       | `[a-l]ook` | libro, cuoco, aspetto | Nook, ha preso     |
| [ ]      | Corrisponde ai caratteri specificati                                    | `[bn]ook`  | libro, Nook       | cuoco, aspetto     |

Quando si progettano i cmdlet che supportano caratteri jolly, consentire combinazioni di caratteri jolly. Ad esempio, il comando seguente usa il cmdlet `Get-ChildItem` per recuperare tutti i file con estensione txt presenti nella cartella c:\Techdocs e che iniziano con le lettere "a" e "l".

`Get-ChildItem c:\techdocs\[a-l]\*.txt`

Il comando precedente utilizza il carattere jolly di intervallo `[a-l]` per specificare che il nome file deve iniziare con i caratteri "a" e "l" e utilizza il carattere jolly `*` come segnaposto per qualsiasi carattere tra la prima lettera del nome file e l'estensione **txt** .

Nell'esempio seguente viene usato un modello di carattere jolly di intervallo che esclude la lettera "d", ma include tutte le altre lettere da "a" a "f".

`Get-ChildItem c:\techdocs\[a-cef]\*.txt`

## <a name="handling-literal-characters-in-wildcard-patterns"></a>Gestione dei caratteri letterali nei modelli con caratteri jolly

Se il modello con caratteri jolly specificato contiene caratteri letterali che non devono essere interprettedti come caratteri jolly, usare il carattere di apice inverso (`` ` ``) come carattere di escape. Quando si specificano caratteri letterali int l'API di PowerShell, usare un singolo apice inverso. Quando si specificano caratteri letterali al prompt dei comandi di PowerShell, usare due apice inverso.

Il modello seguente, ad esempio, contiene due parentesi quadre che devono essere eseguite letteralmente.

Quando usato nell'API PowerShell, usare:

- "John Smith \`[*']"

Quando viene usato dal prompt dei comandi di PowerShell:

- "John Smith \`\`[*\`']"

Questo modello corrisponde a "John Smith [marketing]" o "John Smith [development]". Ad esempio:

```
PS> "John Smith [Marketing]" -like "John Smith ``[*``]"
True

PS> "John Smith [Development]" -like "John Smith ``[*``]"
True
```

## <a name="cmdlet-output-and-wildcard-characters"></a>Output del cmdlet e caratteri jolly

Quando i parametri del cmdlet supportano i caratteri jolly, l'operazione genera in genere un output di matrice.
In alcuni casi non è consigliabile supportare un output di matrice perché l'utente potrebbe usare un solo elemento. Ad esempio, il cmdlet `Set-Location` non supporta l'output della matrice perché l'utente imposta una sola posizione. In questo caso, il cmdlet supporta ancora caratteri jolly, ma forza la risoluzione in un'unica posizione.

## <a name="see-also"></a>Vedere anche

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)

[Classe WildcardPattern](/dotnet/api/system.management.automation.wildcardpattern)
