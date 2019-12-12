---
title: Dichiarazione dell'attributo alias | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Alias attribute
- attributes, Alias
- Alias attribute, described
ms.assetid: d0df3a46-b1cc-42b9-beb1-e16bce254007
caps.latest.revision: 10
ms.openlocfilehash: 4d20672c5181c994c1b53624f6c42a301db11f26
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72370020"
---
# <a name="alias-attribute-declaration"></a>Dichiarazione dell'attributo Alias

L'attributo Alias consente all'utente di specificare nomi diversi per un parametro del cmdlet. Gli alias possono essere utilizzati per fornire collegamenti per un nome di parametro oppure possono fornire nomi diversi appropriati per scenari diversi.

## <a name="syntax"></a>Sintassi

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametri

è necessario `aliasName` (String []). Specifica un set di nomi di alias delimitati da virgole per il parametro del cmdlet.

## <a name="remarks"></a>Osservazioni

- L'attributo alias viene usato con l'attributo Parameter quando si specifica un parametro del cmdlet. Per ulteriori informazioni su come dichiarare questi attributi, vedere [come dichiarare i parametri dei cmdlet](./how-to-declare-cmdlet-parameters.md).

- Ogni nome di alias deve essere univoco all'interno di un cmdlet. Windows PowerShell non controlla la presenza di nomi di alias duplicati.

- L'attributo alias viene usato una volta per ogni parametro in un cmdlet.

- L'attributo alias è definito dalla classe [System. Management. Automation. AliasAttribute](/dotnet/api/System.Management.Automation.AliasAttribute) .

## <a name="see-also"></a>Vedere anche

[Alias di parametro](./parameter-aliases.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
