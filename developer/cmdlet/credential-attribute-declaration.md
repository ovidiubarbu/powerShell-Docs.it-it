---
title: Dichiarazione di attributo di credenziali | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/16/2019
ms.locfileid: "58059253"
---
# <a name="credential-attribute-declaration"></a>Dichiarazione dell'attributo Credential

L'attributo di credenziale è un attributo facoltativo che può essere utilizzato con i parametri delle credenziali di tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa può anche essere passata come argomento al parametro. Quando questo attributo viene aggiunto a una dichiarazione di parametro, Windows PowerShell converte l'input di stringa in un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto. Ad esempio, il [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet Usa questo attributo in modo che Windows PowerShell generi il [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto restituito dal cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Credential]
```

## <a name="remarks"></a>Osservazioni

- In genere questo attributo viene usato dai parametri di tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa può anche essere passata come argomento al parametro. Quando un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto viene passato al parametro, Windows PowerShell non esegue alcuna operazione.

- Quando si crea il [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) dell'oggetto, Windows PowerShell Usa l'Host corrente per visualizzare le istruzioni appropriate per l'utente. Ad esempio, il valore predefinito Host Visualizza una richiesta di nome utente e password quando viene utilizzato questo attributo. Tuttavia, se viene usato un host personalizzato che definisce un prompt dei comandi diverso quindi verrà visualizzato il prompt dei comandi.

- Questo attributo viene usato con l'attributo di parametro. Per altre informazioni su tale attributo, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).

- L'attributo di credenziali è definito per il [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.

## <a name="see-also"></a>Vedere anche

[Alias dei parametri](./parameter-aliases.md)

[Dichiarazione di attributo di parametro](./parameter-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
