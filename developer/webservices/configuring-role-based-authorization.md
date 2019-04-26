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
# <a name="configuring-role-based-authorization"></a>Configurazione dell'autorizzazione basata sui ruoli

In questo argomento viene illustrato come configurare i criteri di autorizzazione basata sui ruoli per l'implementazione di esempio del [Microsoft.Management.Odata.Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) interfaccia descritta in [implementazione personalizzata Autorizzazione per l'estensione IIS OData gestione](./implementing-custom-authorization-for-a-management-odata-web-service.md).

In questo esempio, si configurerà un file XML che viene usato dall'applicazione di gestione OData di esempio per definire i criteri di autorizzazione. Verranno creati due ruoli e associare diversi moduli di Windows PowerShell che contengono i flussi di lavoro a tali ruoli. Lo schema che definisce il file XML è elencato in [Schema di configurazione di autorizzazione basata sui ruoli](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modifica del File RBacConfiguration.xml

Questo file definisce i criteri di autorizzazione per l'applicazione. I ruoli vengono definiti tramite `Group` nodi. Oggetto `Group` nodo definisce i comandi di Windows PowerShell che gli utenti assegnati a quel gruppo possono eseguire. Gli utenti vengono assegnati ai gruppi usando `User` nodi.

In questi esempi, si aggiungerà un modulo all'amministratore `Group` nodo, e aggiungere un utente a ogni gruppo.

#### <a name="adding-a-module-to-a-group-node"></a>Aggiunta di un modulo a un nodo di gruppo

1. Creare un file denominato **RBacConfiguration.xml** in un editor di testo. Questo file deve essere salvato nella directory principale dell'applicazione per il servizio web. Inserire il testo seguente nel file.

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

2. Il file contiene due `Group` nodi. Rappresentano i due ruoli utilizzati in questo esempio, il `NonAdminGroup` e il `AdminGroup` ruoli.

   Direttamente dopo la chiusura `Cmdlets` tag nel primo `Group` nodo, aggiungere il codice XML seguente:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Aggiunta di un utente a un nodo di gruppo

1. Aprire il **RBacConfiguration.xml** file in un editor di testo. Questo file si trova nella cartella c:\\\inetpub\wwwroot\Modata se non è stato modificato il nome dell'endpoint prima dell'installazione.

2. Direttamente dopo il tag di chiusura nel `Users` nodo, aggiungere il codice XML seguente:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Direttamente dopo il codice XML aggiunto nel passaggio precedente, aggiungere il codice XML seguente:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```