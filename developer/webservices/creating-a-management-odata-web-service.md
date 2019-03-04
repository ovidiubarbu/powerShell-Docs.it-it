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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56856627"
---
# <a name="creating-a-management-odata-web-service"></a>Creazione di un servizio Web OData di gestione

Estensione IIS ODATA gestione è un'infrastruttura per la creazione di un endpoint web ASP.NET del servizio che espone i dati di gestione, che si accede tramite i cmdlet di Windows PowerShell e gli script, come entità di servizio OData Web. Che esegue l'elaborazione delle richieste OData e convertendoli in una chiamata di Windows PowerShell. I team dei prodotti possono basarsi su questa infrastruttura per creare endpoint che espongono set di dati di gestione specifici.

Scaricare e installare il [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) esempio. Seguire le istruzioni per distribuire il servizio web. Il servizio web espone i servizi e processi tramite le operazioni di creazione, lettura, aggiornamento ed eliminazione (CRUD). Le richieste CRUD effettuate al servizio web di richiamano i comandi di Windows PowerShell che eseguono le operazioni richieste. Un mapping tra le operazioni CRUD e i comandi di Windows PowerShell sottostanti viene implementato dal file schema. XML, MOF e due file di schema. Il file MOF Usa la [Distributed Management Task Force](https://www.dmtf.org/) standard (DMTF) MOF (Managed Object). Il file di schema. XML viene utilizzato un XML schema descritto in [Schema di Mapping della risorsa](./resource-mapping-schema.md).

> [!IMPORTANT]
> Prima di abilitare estensione IIS ODATA gestione in Windows Server 2008 R2 SP1, è necessario abilitare le funzionalità seguenti.
>
> 1.  IIS-WebServerRole
> 2.  IIS-WebServer
> 3.  IIS-HttpTracing
> 4.  IIS-ManagementOData

## <a name="steps-for-creating-a-management-odata-web-service"></a>Passaggi per la creazione di un servizio web IIS OData gestione

Gli argomenti seguenti descrivono come creare e distribuire un servizio web OData di gestione.

- [Aggiunta di risorse a un servizio Web OData di gestione](./adding-resources-to-a-management-odata-web-service.md)

- [Implementare l'autorizzazione personalizzata per un servizio web IIS OData gestione](./implementing-custom-authorization-for-a-management-odata-web-service.md)

- [Implementazione SessionConfiguration per un servizio web IIS OData gestione](./implementing-sessionconfiguration-for-a-management-odata-web-service.md)

- [Creazione del file di schema MOF per un servizio web IIS OData gestione](./authoring-the-mof-schema-file-for-a-management-odata-web-service.md)

- [Creazione del file di schema XML per un servizio web IIS OData gestione](./authoring-the-xml-schema-file-for-a-management-odata-web-service.md)

- [Creazione del file Web. config per un servizio web IIS OData gestione](./authoring-the-web-config-file-for-a-management-odata-web-service.md)

- [Distribuzione di un servizio web IIS OData gestione](./deploying-a-management-odata-web-service.md)

- [Associare le entità OData di gestione](./associating-management-odata-entities.md)

## <a name="see-also"></a>Vedere anche

[File di Schema di estensione IIS ODATA gestione](./management-odata-iis-extension-schema-files.md)
