---
title: Alias di parametri | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7c9096a1-46fa-48ea-9b8a-a583484b9d68
caps.latest.revision: 13
ms.openlocfilehash: 6545e71ea18d10621ee9c203e70f64dece460ef5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369590"
---
# <a name="parameter-aliases"></a>Alias dei parametri

I parametri cmdlet possono avere anche degli alias. È possibile utilizzare gli alias anziché i nomi dei parametri quando si digita o si specifica il parametro in un comando.

## <a name="benefits-of-using-aliases"></a>Vantaggi dell'utilizzo degli alias

L'aggiunta di alias ai parametri offre i vantaggi seguenti.

- È possibile fornire un collegamento in modo che l'utente non debba usare il nome del parametro completo quando viene chiamato il cmdlet. Ad esempio, è possibile usare l'alias "CN" anziché il nome del parametro "computername".

- È possibile definire più alias se si desidera fornire nomi diversi per lo stesso parametro. Se è necessario utilizzare più gruppi di utenti che fanno riferimento agli stessi dati in modi diversi, potrebbe essere necessario definire più alias.

- È possibile fornire la compatibilità con le versioni precedenti per gli script esistenti se il nome di un parametro viene modificato.

- Utilizzando l'attributo alias insieme all'attributo ValueFromPipelineByName, è possibile definire un parametro che consente al cmdlet di eseguire l'associazione a tipi di oggetti diversi. Si immagini, ad esempio, di avere due oggetti di tipi diversi e che il primo oggetto disponga di una proprietà Writer e che il secondo oggetto disponga di una proprietà Editor. Se il cmdlet dispone di un parametro con alias di writer e di editor e il cmdlet accetta input della pipeline in base ai nomi di proprietà, il cmdlet può essere associato a entrambi gli oggetti usando i due alias di parametro.

Per altre informazioni sugli alias che possono essere usati con parametri specifici, vedere [nomi di parametri comuni](./common-parameter-names.md).

## <a name="defining-parameter-aliases"></a>Definizione degli alias di parametro

Per definire un alias per un parametro, dichiarare l'attributo alias, come illustrato nella dichiarazione di parametro seguente. In questo esempio vengono definiti più alias per lo stesso parametro. Per ulteriori informazioni, vedere[come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).

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

[Nomi di parametro comuni](./common-parameter-names.md)

[Come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
