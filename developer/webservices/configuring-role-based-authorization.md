---
title: Configurazione dell'autorizzazione basata sui ruoli | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2933a6ca-fe92-4ba2-97ee-ef0f0d5fdfcf
caps.latest.revision: 8
ms.openlocfilehash: b73284adb4bf228510bf8134aa4c6a10561b7ea2
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080680"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="ecdbb-102">Configurazione dell'autorizzazione basata sui ruoli</span><span class="sxs-lookup"><span data-stu-id="ecdbb-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="ecdbb-103">In questo argomento viene illustrato come configurare i criteri di autorizzazione basata sui ruoli per l'implementazione di esempio del [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interfaccia descritta in [implementazione personalizzata Autorizzazione per l'estensione IIS OData gestione](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="ecdbb-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="ecdbb-104">In questo esempio, si configurerà un file XML che viene usato dall'applicazione di gestione OData di esempio per definire i criteri di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="ecdbb-105">Verranno creati due ruoli e associare diversi moduli di Windows PowerShell che contengono i flussi di lavoro a tali ruoli.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="ecdbb-106">Lo schema che definisce il file XML è elencato in [Schema di configurazione di autorizzazione basata sui ruoli](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="ecdbb-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="ecdbb-107">Modifica del File RBacConfiguration.xml</span><span class="sxs-lookup"><span data-stu-id="ecdbb-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="ecdbb-108">Questo file definisce i criteri di autorizzazione per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="ecdbb-109">I ruoli vengono definiti tramite `Group` nodi.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="ecdbb-110">Oggetto `Group` nodo definisce i comandi di Windows PowerShell che gli utenti assegnati a quel gruppo possono eseguire.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="ecdbb-111">Gli utenti vengono assegnati ai gruppi usando `User` nodi.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="ecdbb-112">In questi esempi, si aggiungerà un modulo all'amministratore `Group` nodo, e aggiungere un utente a ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="ecdbb-113">Aggiunta di un modulo a un nodo di gruppo</span><span class="sxs-lookup"><span data-stu-id="ecdbb-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="ecdbb-114">Creare un file denominato **RBacConfiguration.xml** in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="ecdbb-115">Questo file deve essere salvato nella directory principale dell'applicazione per il servizio web.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="ecdbb-116">Inserire il testo seguente nel file.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-116">Insert the following text in the file.</span></span>

   ```xml
   <?xml version="1.0" encoding="utf-8"?>
   <RbacConfiguration>
     <Groups>
       <!--Group consists of the following:
         Name:  Name of the group
         UserName (Optional): Windows Identity user name
         Password (Optional): Password of the Windows user name
         DomainName (Optional): Domain for the user. For local machine account either do not include them or give the machine name. Do not give empty string
         MapIncomingUser (Optional): Boolean value indicating whether to execute cmdlet in the context of network client.

         User credentials and MapIncomingUser=true are exclusive.
       -->
       <Group Name="NonAdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Set-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
       </Group>
       <Group Name="AdminGroup" MapIncomingUser="true">
         <Cmdlets>
           <Cmdlet>Get-Service</Cmdlet>
           <Cmdlet>Get-Process</Cmdlet>
           <Cmdlet>Get-Item</Cmdlet>
           <Cmdlet>New-Item</Cmdlet>
           <Cmdlet>Get-Command</Cmdlet>
           <Cmdlet>ConvertTo-Xml</Cmdlet>
           <Cmdlet>ConvertTo-Json</Cmdlet>
           <Cmdlet>ConvertFrom-Json</Cmdlet>
         </Cmdlets>
         <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
       </Group>
     </Groups>
     <Users>
       <!-- User consists of the following :
         Name: Name of the user. If a user is from a cer
         AuthenticationType: Authentication type used.
         DomainName (Optional): Domain for the user
       -->
       <User Name="localNonAdmin" AuthenticationType="Basic" GroupName="NonAdminGroup" />
       <User Name="localAdmin" AuthenticationType="Basic" GroupName="AdminGroup" />
     </Users>
   </RbacConfiguration>
   ```

2. <span data-ttu-id="ecdbb-117">Il file contiene due `Group` nodi.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="ecdbb-118">Rappresentano i due ruoli utilizzati in questo esempio, il `NonAdminGroup` e il `AdminGroup` ruoli.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="ecdbb-119">Direttamente dopo la chiusura `Cmdlets` tag nel primo `Group` nodo, aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="ecdbb-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="ecdbb-120">Aggiunta di un utente a un nodo di gruppo</span><span class="sxs-lookup"><span data-stu-id="ecdbb-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="ecdbb-121">Aprire il **RBacConfiguration.xml** file in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="ecdbb-122">Questo file si trova nella cartella c:\\\inetpub\wwwroot\Modata se non è stato modificato il nome dell'endpoint prima dell'installazione.</span><span class="sxs-lookup"><span data-stu-id="ecdbb-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="ecdbb-123">Direttamente dopo il tag di chiusura nel `Users` nodo, aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="ecdbb-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="ecdbb-124">Direttamente dopo il codice XML aggiunto nel passaggio precedente, aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="ecdbb-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```