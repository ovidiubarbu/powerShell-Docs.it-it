---
title: Dichiarazione dell'attributo Credential | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 96a5dcad-faed-44d8-8c80-321f10499710
caps.latest.revision: 6
ms.openlocfilehash: 49a62ccb09f06f77862d4737199e58293e7fbe0a
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72369890"
---
# <a name="credential-attribute-declaration"></a>Dichiarazione dell'attributo Credential

L'attributo Credential è un attributo facoltativo che può essere usato con i parametri delle credenziali di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa possa essere passata anche come argomento al parametro. Quando questo attributo viene aggiunto a una dichiarazione di parametro, Windows PowerShell converte l'input di stringa in un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) . Ad esempio, il cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) usa questo attributo per generare Windows PowerShell come oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) restituito dal cmdlet.

## <a name="syntax"></a>Sintassi

```csharp
[Credential]
```

## <a name="remarks"></a>Osservazioni

- Questo attributo viene in genere usato da parametri di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa possa essere passata anche come argomento al parametro. Quando un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) viene passato al parametro, Windows PowerShell non esegue alcuna operazione.

- Quando si crea l'oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell usa l'host corrente per visualizzare le richieste appropriate all'utente. L'host predefinito, ad esempio, Visualizza una richiesta di nome utente e password quando viene utilizzato questo attributo. Tuttavia, se viene utilizzato un host personalizzato che definisce un prompt diverso, viene visualizzato il messaggio di richiesta.

- Questo attributo viene utilizzato con l'attributo Parameter. Per ulteriori informazioni su tale attributo, vedere [dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md).

- L'attributo Credential viene definito dalla classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .

## <a name="see-also"></a>Vedere anche

[Alias di parametro](./parameter-aliases.md)

[Dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md)

[Scrittura di un cmdlet di Windows PowerShell](./writing-a-windows-powershell-cmdlet.md)
