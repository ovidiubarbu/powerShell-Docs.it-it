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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72369890"
---
# <a name="credential-attribute-declaration"></a><span data-ttu-id="39879-102">Dichiarazione dell'attributo Credential</span><span class="sxs-lookup"><span data-stu-id="39879-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="39879-103">L'attributo Credential è un attributo facoltativo che può essere usato con i parametri delle credenziali di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa possa essere passata anche come argomento al parametro.</span><span class="sxs-lookup"><span data-stu-id="39879-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="39879-104">Quando questo attributo viene aggiunto a una dichiarazione di parametro, Windows PowerShell converte l'input di stringa in un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) .</span><span class="sxs-lookup"><span data-stu-id="39879-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="39879-105">Ad esempio, il cmdlet [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) usa questo attributo per generare Windows PowerShell come oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) restituito dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="39879-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="39879-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="39879-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="39879-107">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="39879-107">Remarks</span></span>

- <span data-ttu-id="39879-108">Questo attributo viene in genere usato da parametri di tipo [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa possa essere passata anche come argomento al parametro.</span><span class="sxs-lookup"><span data-stu-id="39879-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="39879-109">Quando un oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) viene passato al parametro, Windows PowerShell non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="39879-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="39879-110">Quando si crea l'oggetto [System. Management. Automation. PSCredential](/dotnet/api/System.Management.Automation.PSCredential) , Windows PowerShell usa l'host corrente per visualizzare le richieste appropriate all'utente.</span><span class="sxs-lookup"><span data-stu-id="39879-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="39879-111">L'host predefinito, ad esempio, Visualizza una richiesta di nome utente e password quando viene utilizzato questo attributo.</span><span class="sxs-lookup"><span data-stu-id="39879-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="39879-112">Tuttavia, se viene utilizzato un host personalizzato che definisce un prompt diverso, viene visualizzato il messaggio di richiesta.</span><span class="sxs-lookup"><span data-stu-id="39879-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="39879-113">Questo attributo viene utilizzato con l'attributo Parameter.</span><span class="sxs-lookup"><span data-stu-id="39879-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="39879-114">Per ulteriori informazioni su tale attributo, vedere [dichiarazione dell'attributo Parameter](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="39879-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="39879-115">L'attributo Credential viene definito dalla classe [System. Management. Automation. CredentialAttribute](/dotnet/api/System.Management.Automation.CredentialAttribute) .</span><span class="sxs-lookup"><span data-stu-id="39879-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="39879-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="39879-116">See Also</span></span>

[<span data-ttu-id="39879-117">Alias di parametro</span><span class="sxs-lookup"><span data-stu-id="39879-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="39879-118">Dichiarazione dell'attributo Parameter</span><span class="sxs-lookup"><span data-stu-id="39879-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="39879-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="39879-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
