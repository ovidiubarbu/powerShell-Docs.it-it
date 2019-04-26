---
title: Gli alias dei parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067587"
---
# <a name="parameter-aliases"></a>Alias dei parametri

Parametri del cmdlet possono avere anche degli alias. È possibile usare gli alias anziché i nomi dei parametri quando si immette o specifica il parametro in un comando.

## <a name="benefits-of-using-aliases"></a>Vantaggi dell'uso di alias

Aggiunta di alias per i parametri offre i vantaggi seguenti.

- È possibile fornire un collegamento in modo che l'utente non dovrà usare il nome del parametro completo quando viene chiamato il cmdlet. Ad esempio, è possibile usare l'alias "CN" anziché il nome del parametro "Nomecomputer".

- Se si desidera fornire nomi diversi per lo stesso parametro, è possibile definire più alias. È possibile definire più alias, se si lavora con più gruppi di utenti che fanno riferimento agli stessi dati in modi diversi.

- È possibile garantire la compatibilità per gli script esistenti se il nome di un parametro viene modificato.

- Usando l'Alias (attributo) con l'attributo ValueFromPipelineByName, è possibile definire un parametro che consente di cmdlet per l'associazione a diversi tipi di oggetto. Ad esempio, si dispone di due oggetti di tipi diversi e il primo oggetto disponeva di una proprietà di writer e il secondo oggetto ha una proprietà dell'editor. Se il cmdlet ha un parametro che ha alias writer e l'editor e il cmdlet accepted input della pipeline basati su nei nomi di proprietà, il cmdlet è stato possibile associare a entrambi gli oggetti usando i due alias di parametro.

Per altre informazioni sugli alias che può essere utilizzato con parametri specifici, vedere [i nomi dei parametri comuni](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definizione di alias di parametro

Per definire un alias per un parametro, dichiarare l'attributo di Alias, come illustrato nella seguente dichiarazione di parametro. In questo esempio, sono definiti più alias per il parametro stesso. (Per altre informazioni, vedere[come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md).)

```csharp
[Alias("UN","Writer","Editor")]
[Parameter()]
public string UserName
{
  get { return userName; }
  set { userName = value; }
}
private string userName;
```

## <a name="see-also"></a>Vedere anche

[Nomi dei parametri comuni](./common-parameter-names.md)

[Come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
