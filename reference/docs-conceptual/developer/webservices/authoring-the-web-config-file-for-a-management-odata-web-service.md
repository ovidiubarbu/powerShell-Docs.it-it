---
title: Creazione del file Web. config per un servizio Web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d569f5d5-9746-40c0-be5e-f218bc4560f7
caps.latest.revision: 4
ms.openlocfilehash: f52953ee091f05df5f355719ecba788d3d5ee055
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359790"
---
# <a name="authoring-the-webconfig-file-for-a-management-odata-web-service"></a>Creazione del file Web.config per un servizio Web OData di gestione

Prima di poter distribuire il servizio Web OData di gestione, è necessario configurare il file Web. config in modo che punti ai file di XML Schema e alle DLL che implementano [Microsoft. Management. OData. Customauthorization](/dotnet/api/Microsoft.Management.Odata.CustomAuthorization) e [ Interfacce System. Management. Automation. Remoting. PSSessionConfiguration](/dotnet/api/System.Management.Automation.Remoting.PSSessionConfiguration) .

## <a name="sample-config-file"></a>File di configurazione di esempio

Di seguito è riportato un esempio di come appare il file Web. config per il servizio Web.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
   <configSections>
      <section name="managementOdata" type="Microsoft.Management.Odata.Core.DSConfiguration, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35, processorArchitecture=MSIL" />
   </configSections>
   <managementOdata schemaFileName="Schema.mof" resourceMappingFileName="Schema.xml">
      <customAuthorization type="Microsoft.Samples.Management.OData.RoleBasedPlugins.CustomAuthorization" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      <powershell>
         <sessionConfiguration type="Microsoft.Samples.Management.OData.RoleBasedPlugins.SessionConfiguration" assembly=".\Microsoft.Samples.Management.OData.RoleBasedPlugins.dll" />
      </powershell>
      <commandInvocation enabled="true" />
      <wcfDataServicesConfig>
      </wcfDataServicesConfig>
   </managementOdata>
   <system.serviceModel>
      <behaviors>
         <serviceBehaviors>
            <behavior>
                  <serviceAuthorization serviceAuthorizationManagerType="Microsoft.Management.Odata.Core.CustomAuthorizationManager, Microsoft.Management.OData, Version=3.0.0.0, Culture=neutral, PublicKeyToken=31bf3856ad364e35" />
            </behavior>
         </serviceBehaviors>
      </behaviors>
      <serviceHostingEnvironment aspNetCompatibilityEnabled="true" />
   </system.serviceModel>
   <system.webServer>
      <security>
         <authentication>
            <anonymousAuthentication enabled="false" />
            <basicAuthentication enabled="true" />
            <windowsAuthentication enabled="false" />
         </authentication>
      </security>
  </system.webServer>
</configuration>

```

## <a name="see-also"></a>Vedere anche

[Implementazione dell'autorizzazione personalizzata per un servizio Web OData di gestione](./implementing-custom-authorization-for-a-management-odata-web-service.md)

[Implementazione di SessionConfiguration per un servizio Web OData di gestione](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

[Creazione del file di schema MOF per un servizio Web OData di gestione](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

[Creazione del file di XML Schema per un servizio Web OData di gestione](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

[Creazione di un servizio Web OData di gestione](./creating-a-management-odata-web-service.md)