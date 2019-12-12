---
title: Creazione di un servizio Web OData di gestione | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 06b1b050-0bf7-48f5-ba05-43f489d597c0
caps.latest.revision: 10
ms.openlocfilehash: 476fce9fc087b870bad93a9204a820c5a84df99e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/05/2019
ms.locfileid: "72359720"
---
# <a name="creating-a-management-odata-web-service"></a>Creazione di un servizio Web OData di gestione

Estensione IIS ODATA di gestione è un'infrastruttura per la creazione di un endpoint del servizio Web ASP.NET che espone i dati di gestione, a cui si accede tramite cmdlet e script di Windows PowerShell come entità del servizio Web OData. A tale scopo, elabora le richieste OData e le converte in una chiamata di Windows PowerShell. I team di prodotto possono basarsi su questa infrastruttura per creare endpoint che espongono set di dati di gestione specifici.

Scaricare e installare l'esempio [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) . Seguire le istruzioni per distribuire il servizio Web. Questo servizio Web espone i servizi e i processi mediante operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD). Le richieste CRUD effettuate al servizio Web richiamano i comandi di Windows PowerShell che eseguono le operazioni richieste. Un mapping tra le operazioni CRUD e i comandi di Windows PowerShell sottostanti viene implementato da due file di schema, schema. mof e schema. XML. Il file schema. MOF utilizza lo standard MOF ( [Distributed Management Task Force](https://www.dmtf.org/) ) (DMTF). Nel file schema. XML viene utilizzato un XML Schema descritto in [schema di mapping delle risorse](./resource-mapping-schema.md).

> [!IMPORTANT]
> Prima di abilitare l'estensione IIS ODATA di gestione in Windows Server 2008 R2 SP1, è necessario abilitare le funzionalità seguenti.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Passaggi per la creazione di un servizio Web OData di gestione

Negli argomenti seguenti viene descritto come creare e distribuire un servizio Web OData di gestione.

- [Aggiunta di risorse a un servizio Web OData di gestione](./adding-resources-to-a-management-odata-web-service.md)

- [Implementazione dell'autorizzazione personalizzata per un servizio Web OData di gestione](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementazione di SessionConfiguration per un servizio Web OData di gestione](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Creazione del file di schema MOF per un servizio Web OData di gestione](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Creazione del file di XML Schema per un servizio Web OData di gestione](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Creazione del file Web. config per un servizio Web OData di gestione](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Distribuzione di un servizio Web OData di gestione](./deploying-a-management-odata-web-service.md)

- [Associazione di entità OData di gestione](./associating-management-odata-entities.md)

## <a name="see-also"></a>Vedere anche

[Gestione dei file di schema dell'estensione IIS ODATA](./management-odata-iis-extension-schema-files.md)
