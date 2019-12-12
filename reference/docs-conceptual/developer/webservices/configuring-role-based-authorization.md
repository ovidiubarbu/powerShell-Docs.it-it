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
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359770"
---
# <a name="configuring-role-based-authorization"></a><span data-ttu-id="5de97-102">Configurazione dell'autorizzazione basata sui ruoli</span><span class="sxs-lookup"><span data-stu-id="5de97-102">Configuring Role-based Authorization</span></span>

<span data-ttu-id="5de97-103">In questo argomento viene illustrato come configurare i criteri di autorizzazione basata sui ruoli per l'implementazione di esempio dell'interfaccia [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) descritta in [implementazione dell'autorizzazione personalizzata per la gestione dell'estensione IIS OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span><span class="sxs-lookup"><span data-stu-id="5de97-103">This topic demonstrates how to configure the role-based authorization policy for the sample implementation of the [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interface described in [Implementing Custom Authorization for Management OData IIS Extension](./implementing-custom-authorization-for-a-management-odata-web-service.md).</span></span>

<span data-ttu-id="5de97-104">In questo esempio verrà configurato un file XML utilizzato dall'applicazione OData di gestione di esempio per definire i criteri di autorizzazione.</span><span class="sxs-lookup"><span data-stu-id="5de97-104">In this example, you will configure an XML file that is used by the sample Management OData application to define the authorization policy.</span></span> <span data-ttu-id="5de97-105">Si creeranno due ruoli e si associeranno diversi moduli di Windows PowerShell che contengono flussi di lavoro con tali ruoli.</span><span class="sxs-lookup"><span data-stu-id="5de97-105">You will create two roles and associate different Windows PowerShell modules that contain workflows with those roles.</span></span> <span data-ttu-id="5de97-106">Lo schema che definisce il file XML è elencato in [schema di configurazione dell'autorizzazione basata sui ruoli](./role-based-authorization-configuration-schema.md).</span><span class="sxs-lookup"><span data-stu-id="5de97-106">The schema that defines the XML file is listed at [Role-Based Authorization Configuration Schema](./role-based-authorization-configuration-schema.md).</span></span>

## <a name="modifying-the-rbacconfigurationxml-file"></a><span data-ttu-id="5de97-107">Modifica del file RBacConfiguration. XML</span><span class="sxs-lookup"><span data-stu-id="5de97-107">Modifying the RBacConfiguration.xml File</span></span>

<span data-ttu-id="5de97-108">Questo file definisce i criteri di autorizzazione per l'applicazione.</span><span class="sxs-lookup"><span data-stu-id="5de97-108">This file defines the authorization policy for the application.</span></span> <span data-ttu-id="5de97-109">I ruoli vengono definiti utilizzando nodi `Group`.</span><span class="sxs-lookup"><span data-stu-id="5de97-109">Roles are defined by using `Group` nodes.</span></span> <span data-ttu-id="5de97-110">Un nodo `Group` definisce i comandi di Windows PowerShell che possono essere eseguiti dagli utenti assegnati a tale gruppo.</span><span class="sxs-lookup"><span data-stu-id="5de97-110">A `Group` node defines the Windows PowerShell commands that users assigned to that group can run.</span></span> <span data-ttu-id="5de97-111">Gli utenti vengono assegnati ai gruppi utilizzando `User` nodi.</span><span class="sxs-lookup"><span data-stu-id="5de97-111">Users are assigned to groups by using `User` nodes.</span></span>

<span data-ttu-id="5de97-112">In questi esempi, si aggiungerà un modulo al nodo Administrator `Group` e si aggiungerà un utente a ogni gruppo.</span><span class="sxs-lookup"><span data-stu-id="5de97-112">In these examples, you will add a module to the Administrator `Group` node, and add a user to each group.</span></span>

#### <a name="adding-a-module-to-a-group-node"></a><span data-ttu-id="5de97-113">Aggiunta di un modulo a un nodo di gruppo</span><span class="sxs-lookup"><span data-stu-id="5de97-113">Adding a Module to a Group Node</span></span>

1. <span data-ttu-id="5de97-114">Creare un file denominato **RBacConfiguration. XML** in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="5de97-114">Create a file named **RBacConfiguration.xml** in a text editor.</span></span> <span data-ttu-id="5de97-115">Questo file deve essere salvato nella directory principale dell'applicazione per il servizio Web.</span><span class="sxs-lookup"><span data-stu-id="5de97-115">This file should be saved to the main application directory for your web service.</span></span> <span data-ttu-id="5de97-116">Inserire il testo seguente nel file.</span><span class="sxs-lookup"><span data-stu-id="5de97-116">Insert the following text in the file.</span></span>

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

2. <span data-ttu-id="5de97-117">Il file contiene due nodi `Group`.</span><span class="sxs-lookup"><span data-stu-id="5de97-117">The file contains two `Group` nodes.</span></span> <span data-ttu-id="5de97-118">Rappresentano i due ruoli usati in questo esempio, il `NonAdminGroup` e i ruoli del `AdminGroup`.</span><span class="sxs-lookup"><span data-stu-id="5de97-118">These represent the two roles used in this example, the `NonAdminGroup` and the `AdminGroup` roles.</span></span>

   <span data-ttu-id="5de97-119">Subito dopo il tag di chiusura `Cmdlets` nel primo nodo `Group` aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="5de97-119">Directly after the closing `Cmdlets` tag in the first `Group` node, add the following XML:</span></span>

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a><span data-ttu-id="5de97-120">Aggiunta di un utente a un nodo di gruppo</span><span class="sxs-lookup"><span data-stu-id="5de97-120">Adding a User to a Group Node</span></span>

1. <span data-ttu-id="5de97-121">Aprire il file **RBacConfiguration. XML** in un editor di testo.</span><span class="sxs-lookup"><span data-stu-id="5de97-121">Open the **RBacConfiguration.xml** file in a text editor.</span></span> <span data-ttu-id="5de97-122">Questo file si trova nella cartella C:\\\inetpub\wwwroot\Modata se il nome dell'endpoint non è stato modificato prima dell'installazione.</span><span class="sxs-lookup"><span data-stu-id="5de97-122">This file is located in the folder C:\\\inetpub\wwwroot\Modata  if you did not change the endpoint name before installation.</span></span>

2. <span data-ttu-id="5de97-123">Subito dopo il tag di chiusura nel nodo `Users` aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="5de97-123">Directly after the closing tag in the `Users` node, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. <span data-ttu-id="5de97-124">Direttamente dopo il codice XML aggiunto nel passaggio precedente, aggiungere il codice XML seguente:</span><span class="sxs-lookup"><span data-stu-id="5de97-124">Directly after the XML added in the previous step, add the following XML:</span></span>

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```