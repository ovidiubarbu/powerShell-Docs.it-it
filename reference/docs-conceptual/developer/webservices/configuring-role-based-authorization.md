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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359770"
---
# <a name="configuring-role-based-authorization"></a>Configurazione dell'autorizzazione basata sui ruoli

In questo argomento viene illustrato come configurare i criteri di autorizzazione basata sui ruoli per l'implementazione di esempio dell'interfaccia [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) descritta in [implementazione dell'autorizzazione personalizzata per la gestione Estensione IIS OData](./implementing-custom-authorization-for-a-management-odata-web-service.md).

In questo esempio verrà configurato un file XML utilizzato dall'applicazione OData di gestione di esempio per definire i criteri di autorizzazione. Si creeranno due ruoli e si associeranno diversi moduli di Windows PowerShell che contengono flussi di lavoro con tali ruoli. Lo schema che definisce il file XML è elencato in [schema di configurazione dell'autorizzazione basata sui ruoli](./role-based-authorization-configuration-schema.md).

## <a name="modifying-the-rbacconfigurationxml-file"></a>Modifica del file RBacConfiguration. XML

Questo file definisce i criteri di autorizzazione per l'applicazione. I ruoli vengono definiti tramite nodi `Group`. Un nodo `Group` definisce i comandi di Windows PowerShell che possono essere eseguiti dagli utenti assegnati a tale gruppo. Gli utenti vengono assegnati ai gruppi usando i nodi `User`.

In questi esempi viene aggiunto un modulo al nodo Administrator `Group` e viene aggiunto un utente a ogni gruppo.

#### <a name="adding-a-module-to-a-group-node"></a>Aggiunta di un modulo a un nodo di gruppo

1. Creare un file denominato **RBacConfiguration. XML** in un editor di testo. Questo file deve essere salvato nella directory principale dell'applicazione per il servizio Web. Inserire il testo seguente nel file.

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

2. Il file contiene due nodi `Group`. Rappresentano i due ruoli usati in questo esempio, i ruoli `NonAdminGroup` e `AdminGroup`.

   Subito dopo il tag di chiusura `Cmdlets` nel primo nodo `Group`, aggiungere il codice XML seguente:

   ```xml
   <Modules>
           <Module>C:\Windows\System32\WindowsPowerShell\v1.0\Modules\ServerManager\ServerManager.psd1</Module>
         </Modules>
   ```

#### <a name="adding-a-user-to-a-group-node"></a>Aggiunta di un utente a un nodo di gruppo

1. Aprire il file **RBacConfiguration. XML** in un editor di testo. Questo file si trova nella cartella C: \\ \ inetpub\wwwroot\Modata se il nome dell'endpoint non è stato modificato prima dell'installazione.

2. Subito dopo il tag di chiusura nel nodo `Users` aggiungere il codice XML seguente:

   ```xml
   <User Name="UserName" GroupName="AdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```

3. Direttamente dopo il codice XML aggiunto nel passaggio precedente, aggiungere il codice XML seguente:

   ```xml
   <User Name="UserName" GroupName="NonAdminGroup" AuthenticationType="Basic" DomainName="DomainName"/>
   ```