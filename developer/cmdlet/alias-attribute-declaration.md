---
title: Dichiarazione di attributo alias | Microsoft Docs
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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62068716"
---
# <a name="alias-attribute-declaration"></a>Dichiarazione dell'attributo Alias

L'Alias (attributo) consente all'utente di specificare nomi diversi per un parametro del cmdlet. Gli alias possono essere utilizzati per fornire collegamenti per un nome di parametro, o possono fornire nomi diversi essendo appropriati per scenari diversi.

## <a name="syntax"></a>Sintassi

```csharp
[Alias(aliasNames)]
```

#### <a name="parameters"></a>Parametri

`aliasName` (String[]) richiesto. Specifica un set di nomi di alias delimitato da virgole per il parametro del cmdlet.

## <a name="remarks"></a>Osservazioni

- L'Alias (attributo) viene usato con l'attributo di parametro quando si specifica un parametro del cmdlet. Per altre informazioni su come dichiarare questi attributi, vedere [come dichiarare i parametri del Cmdlet](./how-to-declare-cmdlet-parameters.md).

- Ogni nome di alias deve essere univoco all'interno di un cmdlet. Windows PowerShell verifica la presenza di nomi di alias duplicato.

- L'attributo Alias viene usato una sola volta per ogni parametro in un cmdlet.

- L'attributo di Alias è definito per il [System.Management.Automation.Aliasattribute](/dotnet/api/System.Management.Automation.AliasAttribute) classe.

## <a name="see-also"></a>Vedere anche

[Alias dei parametri](./parameter-aliases.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
