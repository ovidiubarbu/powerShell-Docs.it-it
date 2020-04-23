---
ms.date: 09/20/2019
keywords: dsc,powershell,configurazione,installazione
title: Risorsa nxSshAuthorizedKeys DSC per Linux
ms.openlocfilehash: 6e008efcbff2e679650d0bc3d5b8b573f6ef83e0
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 04/22/2020
ms.locfileid: "71953258"
---
# <a name="dsc-for-linux-nxsshauthorizedkeys-resource"></a><span data-ttu-id="aeafa-103">Risorsa nxSshAuthorizedKeys DSC per Linux</span><span class="sxs-lookup"><span data-stu-id="aeafa-103">DSC for Linux nxSshAuthorizedKeys Resource</span></span>

<span data-ttu-id="aeafa-104">La risorsa **nxSshAuthorizedKeys** in PowerShell DSC (Desired State Configuration) fornisce un meccanismo per gestire le chiavi ssh autorizzate per un utente specificato.</span><span class="sxs-lookup"><span data-stu-id="aeafa-104">The **nxAuthorizedKeys** resource in PowerShell Desired State Configuration (DSC) provides a mechanism to manage authorized ssh keys for a specified user.</span></span>

## <a name="syntax"></a><span data-ttu-id="aeafa-105">Sintassi</span><span class="sxs-lookup"><span data-stu-id="aeafa-105">Syntax</span></span>

```Syntax
nxAuthorizedKeys <string> #ResourceName
{
    KeyComment = <string>
    [ Username = <string> ]
    [ Key = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a><span data-ttu-id="aeafa-106">Proprietà</span><span class="sxs-lookup"><span data-stu-id="aeafa-106">Properties</span></span>

|<span data-ttu-id="aeafa-107">Proprietà</span><span class="sxs-lookup"><span data-stu-id="aeafa-107">Property</span></span> |<span data-ttu-id="aeafa-108">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aeafa-108">Description</span></span> |
|---|---|
|<span data-ttu-id="aeafa-109">KeyComment</span><span class="sxs-lookup"><span data-stu-id="aeafa-109">KeyComment</span></span> |<span data-ttu-id="aeafa-110">Commento univoco per la chiave.</span><span class="sxs-lookup"><span data-stu-id="aeafa-110">A unique comment for the key.</span></span> <span data-ttu-id="aeafa-111">Questa proprietà viene usata per identificare in modo univoco la chiave.</span><span class="sxs-lookup"><span data-stu-id="aeafa-111">This is used to uniquely identify keys.</span></span> |
|<span data-ttu-id="aeafa-112">Username</span><span class="sxs-lookup"><span data-stu-id="aeafa-112">Username</span></span> |<span data-ttu-id="aeafa-113">Nome utente per cui gestire le chiavi ssh autorizzate.</span><span class="sxs-lookup"><span data-stu-id="aeafa-113">The username to manage ssh authorized keys for.</span></span> <span data-ttu-id="aeafa-114">Se questa proprietà non è definita, l'utente predefinito è **root**.</span><span class="sxs-lookup"><span data-stu-id="aeafa-114">If not defined, the default user is **root**.</span></span> |
|<span data-ttu-id="aeafa-115">Chiave</span><span class="sxs-lookup"><span data-stu-id="aeafa-115">Key</span></span> |<span data-ttu-id="aeafa-116">Contenuto della chiave.</span><span class="sxs-lookup"><span data-stu-id="aeafa-116">The contents of the key.</span></span> <span data-ttu-id="aeafa-117">Questa proprietà è obbligatoria se la proprietà **Ensure** è impostata su **Present**.</span><span class="sxs-lookup"><span data-stu-id="aeafa-117">This is required if **Ensure** is set to **Present**.</span></span>|

## <a name="common-properties"></a><span data-ttu-id="aeafa-118">Proprietà comuni</span><span class="sxs-lookup"><span data-stu-id="aeafa-118">Common properties</span></span>

|<span data-ttu-id="aeafa-119">Proprietà</span><span class="sxs-lookup"><span data-stu-id="aeafa-119">Property</span></span> |<span data-ttu-id="aeafa-120">Descrizione</span><span class="sxs-lookup"><span data-stu-id="aeafa-120">Description</span></span> |
|---|---|
|<span data-ttu-id="aeafa-121">DependsOn</span><span class="sxs-lookup"><span data-stu-id="aeafa-121">DependsOn</span></span> |<span data-ttu-id="aeafa-122">Indica che prima di configurare la risorsa è necessario eseguire la configurazione di un'altra risorsa.</span><span class="sxs-lookup"><span data-stu-id="aeafa-122">Indicates that the configuration of another resource must run before this resource is configured.</span></span> <span data-ttu-id="aeafa-123">Ad esempio, se il valore di ID del blocco script di configurazione della risorsa che si vuole eseguire per primo è ResourceName e il tipo è ResourceType, la sintassi per usare questa proprietà è `DependsOn = "[ResourceType]ResourceName"`.</span><span class="sxs-lookup"><span data-stu-id="aeafa-123">For example, if the ID of the resource configuration script block that you want to run first is ResourceName and its type is ResourceType, the syntax for using this property is `DependsOn = "[ResourceType]ResourceName"`.</span></span> |
|<span data-ttu-id="aeafa-124">Ensure</span><span class="sxs-lookup"><span data-stu-id="aeafa-124">Ensure</span></span> |<span data-ttu-id="aeafa-125">Specifica se la chiave è definita.</span><span class="sxs-lookup"><span data-stu-id="aeafa-125">Specifies whether the key is defined.</span></span> <span data-ttu-id="aeafa-126">Impostare questa proprietà su **Absent** per assicurarsi che la chiave non esista nel file delle chiavi autorizzate dell'utente.</span><span class="sxs-lookup"><span data-stu-id="aeafa-126">Set this property to **Absent** to ensure the key does not exist in the user's authorized keys file.</span></span> <span data-ttu-id="aeafa-127">Impostarla su **Present** per assicurarsi che la chiave sia definita nel file delle chiavi autorizzate dell'utente.</span><span class="sxs-lookup"><span data-stu-id="aeafa-127">Set it to **Present** to ensure the key is defined in the user's authorized key file.</span></span> |

## <a name="example"></a><span data-ttu-id="aeafa-128">Esempio</span><span class="sxs-lookup"><span data-stu-id="aeafa-128">Example</span></span>

<span data-ttu-id="aeafa-129">L'esempio seguente definisce una chiave ssh autorizzata pubblica per l'utente "monuser".</span><span class="sxs-lookup"><span data-stu-id="aeafa-129">The following example defines a public ssh authorized key for the user "monuser".</span></span>

```powershell
Import-DSCResource -Module nx

Node $node
{
    nxSshAuthorizedKeys myKey
    {
        KeyComment = "myKey"
        Ensure = "Present"
        Key = 'ssh-rsa AAAAB3NzaC1yc2EAAAABJQAAAQEA0b+0xSd07QXRifm3FXj7Pn/DblA6QI5VAkDm6OivFzj3U6qGD1VJ6AAxWPCyMl/qhtpRtxZJDu/TxD8AyZNgc8aN2CljN1hOMbBRvH2q5QPf/nCnnJRaGsrxIqZjyZdYo9ZEEzjZUuMDM5HI1LA9B99k/K6PK2Bc1NLivpu7nbtVG2tLOQs+GefsnHuetsRMwo/+c3LtwYm9M0XfkGjYVCLO4CoFuSQpvX6AB3TedUy6NZ0iuxC0kRGg1rIQTwSRcw+McLhslF0drs33fw6tYdzlLBnnzimShMuiDWiT37WqCRovRGYrGCaEFGTG2e0CN8Co8nryXkyWc6NSDNpMzw== rsa-key-20150401'
        UserName = "monuser"
    }
}
```