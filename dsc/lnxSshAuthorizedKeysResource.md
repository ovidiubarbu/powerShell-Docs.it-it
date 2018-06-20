---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,impostazione
title: Risorsa nxSshAuthorizedKeys DSC per Linux
ms.openlocfilehash: d4cdb727a94a5e89e8401769f24977d49bcf4929
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222038"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="61e32-103">Risorsa nxSshAuthorizedKeys DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="61e32-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="61e32-104">La risorsa **nxSshAuthorizedKeys** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le chiavi ssh autorizzate per un utente specificato.</span><span class="sxs-lookup"><span data-stu-id="61e32-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="61e32-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="61e32-105">Syntax</span></span>

```
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a><span data-ttu-id="61e32-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="61e32-106">Properties</span></span>

|  <span data-ttu-id="61e32-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="61e32-107">Property</span></span> |  <span data-ttu-id="61e32-108">Description</span><span class="sxs-lookup"><span data-stu-id="61e32-108">Description</span></span> |
|---|---|
| <span data-ttu-id="61e32-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="61e32-109">KeyComment</span></span>| <span data-ttu-id="61e32-110">Commento univoco per la chiave.</span><span class="sxs-lookup"><span data-stu-id="61e32-110">A unique comment for the key.</span></span> <span data-ttu-id="61e32-111">Questa proprietà viene usata per identificare in modo univoco la chiave.</span><span class="sxs-lookup"><span data-stu-id="61e32-111">This is used to uniquely identify keys.</span></span>|
| <span data-ttu-id="61e32-112">Ensure</span><span class="sxs-lookup"><span data-stu-id="61e32-112">Ensure</span></span>| <span data-ttu-id="61e32-113">Specifica se la chiave è definita.</span><span class="sxs-lookup"><span data-stu-id="61e32-113">Specifies whether the key is defined.</span></span> <span data-ttu-id="61e32-114">Impostare questa proprietà su "Absent" per specificare che la chiave non esiste nel file delle chiavi autorizzate dell'utente.</span><span class="sxs-lookup"><span data-stu-id="61e32-114">Set this property to "Absent" to ensure the key does not exist in the user’s authorized keys file.</span></span> <span data-ttu-id="61e32-115">Impostarla su "Absent" per specificare che la chiave è definita nel file delle chiavi autorizzate dell'utente.</span><span class="sxs-lookup"><span data-stu-id="61e32-115">Set it to "Present" to ensure the key is defined in the user’s authorized key file.</span></span>|
| <span data-ttu-id="61e32-116">Username</span><span class="sxs-lookup"><span data-stu-id="61e32-116">Username</span></span>| <span data-ttu-id="61e32-117">Nome utente per cui gestire le chiavi ssh autorizzate.</span><span class="sxs-lookup"><span data-stu-id="61e32-117">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="61e32-118">Se questa proprietà non è definita, l'utente predefinito è "root".</span><span class="sxs-lookup"><span data-stu-id="61e32-118">If not defined, the default user is "root".</span></span>|
| <span data-ttu-id="61e32-119">Key</span><span class="sxs-lookup"><span data-stu-id="61e32-119">Key</span></span>| <span data-ttu-id="61e32-120">Contenuto della chiave.</span><span class="sxs-lookup"><span data-stu-id="61e32-120">The contents of the key.</span></span> <span data-ttu-id="61e32-121">Questa proprietà è obbligatoria se la proprietà **Ensure** è impostata su "Present".</span><span class="sxs-lookup"><span data-stu-id="61e32-121">This is required if **Ensure** is set to "Present".</span></span>|
| <span data-ttu-id="61e32-122">DependsOn</span><span class="sxs-lookup"><span data-stu-id="61e32-122">DependsOn</span></span> | <span data-ttu-id="61e32-123">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="61e32-123">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="61e32-124">Ad esempio, se il valore di **ID** del blocco script di configurazione della risorsa che si vuole eseguire per primo è **ResourceName** e il tipo è **ResourceType**, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="61e32-124">For example, if the **ID** of the resource configuration script block that you want to run first is **ResourceName** and its type is **ResourceType**, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span>|

## <a name="example"></a><span data-ttu-id="61e32-125">Esempio</span><span class="sxs-lookup"><span data-stu-id="61e32-125">Example</span></span>

<span data-ttu-id="61e32-126">L'esempio seguente definisce una chiave ssh autorizzata pubblica per l'utente "monuser".</span><span class="sxs-lookup"><span data-stu-id="61e32-126">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```
Import-DSCResource -Module nx

Node $node {

nxSshAuthorizedKeys myKey{
   KeyComment = "myKey"
   Ensure = "Present"
   Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
   UserName = "monuser"
}
}
```