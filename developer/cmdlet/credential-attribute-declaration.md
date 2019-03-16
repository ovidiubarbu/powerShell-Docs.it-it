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
# <a name="credential-attribute-declaration"></a><span data-ttu-id="8f4c9-102">Dichiarazione dell'attributo Credential</span><span class="sxs-lookup"><span data-stu-id="8f4c9-102">Credential Attribute Declaration</span></span>

<span data-ttu-id="8f4c9-103">L'attributo di credenziale è un attributo facoltativo che può essere utilizzato con i parametri delle credenziali di tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa può anche essere passata come argomento al parametro.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-103">The Credential attribute is an optional attribute that can be used with credential parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="8f4c9-104">Quando questo attributo viene aggiunto a una dichiarazione di parametro, Windows PowerShell converte l'input di stringa in un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-104">When this attribute is added to a parameter declaration, Windows PowerShell converts the string input into a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object.</span></span> <span data-ttu-id="8f4c9-105">Ad esempio, il [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet Usa questo attributo in modo che Windows PowerShell generi il [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto restituito dal cmdlet.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-105">For example, the [Get-Credential](/powershell/module/Microsoft.PowerShell.Security/Get-Credential) cmdlet uses this attribute to have Windows PowerShell generate the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object that is returned by the cmdlet.</span></span>

## <a name="syntax"></a><span data-ttu-id="8f4c9-106">Sintassi</span><span class="sxs-lookup"><span data-stu-id="8f4c9-106">Syntax</span></span>

```csharp
[Credential]
```

## <a name="remarks"></a><span data-ttu-id="8f4c9-107">Osservazioni</span><span class="sxs-lookup"><span data-stu-id="8f4c9-107">Remarks</span></span>

- <span data-ttu-id="8f4c9-108">In genere questo attributo viene usato dai parametri di tipo [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) in modo che una stringa può anche essere passata come argomento al parametro.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-108">Typically this attribute is used by parameters of type [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) so that a string can also be passed as an argument to the parameter.</span></span> <span data-ttu-id="8f4c9-109">Quando un [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) oggetto viene passato al parametro, Windows PowerShell non esegue alcuna operazione.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-109">When a [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object is passed to the parameter, Windows PowerShell does nothing.</span></span>

- <span data-ttu-id="8f4c9-110">Quando si crea il [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) dell'oggetto, Windows PowerShell Usa l'Host corrente per visualizzare le istruzioni appropriate per l'utente.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-110">When creating the [System.Management.Automation.PSCredential](/dotnet/api/System.Management.Automation.PSCredential) object, Windows PowerShell uses the current Host to display the appropriate prompts to the user.</span></span> <span data-ttu-id="8f4c9-111">Ad esempio, il valore predefinito Host Visualizza una richiesta di nome utente e password quando viene utilizzato questo attributo.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-111">For example, the default Host displays a prompt for a user name and password when this attribute is used.</span></span> <span data-ttu-id="8f4c9-112">Tuttavia, se viene usato un host personalizzato che definisce un prompt dei comandi diverso quindi verrà visualizzato il prompt dei comandi.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-112">However, if a custom host is being used that defines a different prompt then that prompt would be displayed.</span></span>

- <span data-ttu-id="8f4c9-113">Questo attributo viene usato con l'attributo di parametro.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-113">This attribute is used with the Parameter attribute.</span></span> <span data-ttu-id="8f4c9-114">Per altre informazioni su tale attributo, vedere [dichiarazione di attributo parametro](./parameter-attribute-declaration.md).</span><span class="sxs-lookup"><span data-stu-id="8f4c9-114">For more information about that attribute, see [Parameter Attribute Declaration](./parameter-attribute-declaration.md).</span></span>

- <span data-ttu-id="8f4c9-115">L'attributo di credenziali è definito per il [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) classe.</span><span class="sxs-lookup"><span data-stu-id="8f4c9-115">The credential attribute is defined by the [System.Management.Automation.Credentialattribute](/dotnet/api/System.Management.Automation.CredentialAttribute) class.</span></span>

## <a name="see-also"></a><span data-ttu-id="8f4c9-116">Vedere anche</span><span class="sxs-lookup"><span data-stu-id="8f4c9-116">See Also</span></span>

[<span data-ttu-id="8f4c9-117">Alias dei parametri</span><span class="sxs-lookup"><span data-stu-id="8f4c9-117">Parameter Aliases</span></span>](./parameter-aliases.md)

[<span data-ttu-id="8f4c9-118">Dichiarazione di attributo di parametro</span><span class="sxs-lookup"><span data-stu-id="8f4c9-118">Parameter Attribute Declaration</span></span>](./parameter-attribute-declaration.md)

[<span data-ttu-id="8f4c9-119">Scrittura di un cmdlet di Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="8f4c9-119">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
