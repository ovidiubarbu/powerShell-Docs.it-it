---
title: Aggiunta di un servizio Web OData di gestione risorse | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e620bf6d-76be-47b0-a7a8-f43418f30c60
caps.latest.revision: 6
ms.openlocfilehash: b81a32b867795ae51c3f5308c2f82c31ed2747fa
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "56858367"
---
# <a name="adding-resources-to-a-management-odata-web-service"></a>Aggiunta di risorse a un servizio Web OData di gestione

In questo esempio viene illustrato come aggiungere una risorsa a un servizio web OData di gestione esistente utilizzando la progettazione Schema OData di gestione. Il [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) esempio crea un servizio web che espone le risorse di processo e il Server. In questo esempio si aggiungerà una risorsa di macchina virtuale (VM) per il servizio web.

## <a name="prerequisites"></a>Prerequisiti

Questo argomento si presuppone di avere scaricato e installato il [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) di esempio come descritto in [creazione di un servizio Web di Windows PowerShell](./creating-a-management-odata-web-service.md), e che è stato scaricato e installato il [Finestra di progettazione di gestione dello Schema di OData](https://marketplace.visualstudio.com/items?itemName=jlisc0.ManagementODataSchemaDesigner). In questo argomento presume anche che il modulo Hyper-V di Windows PowerShell installato nel computer in cui si configura l'endpoint Odata di gestione.

## <a name="adding-vm-as-a-resource-to-the-web-service"></a>Aggiunta della macchina virtuale come risorsa al servizio Web

Il primo passaggio consiste nell'importare lo schema dall'endpoint OData di gestione esistente in Progettazione schema. La procedura seguente descrive come eseguire l'operazione.

#### <a name="importing-an-existing-schema-into-the-schema-designer"></a>Importazione di uno schema esistente in Progettazione schema

1. Aprire la finestra di progettazione di gestione dello Schema di OData.

2. Dal **File** dal menu **File** ; **Nuovo** ; **File**. Il **nuovo File** viene visualizzata la finestra.

3. Fare clic su **modello OData di gestione**, quindi fare clic su **Open**.

4. Fare doppio clic nella finestra principale e fare clic su **file di Schema** ; **Importazione**. Il **aperto** viene visualizzata la finestra.

5. Passare alla cartella in cui è impostato il servizio web OData di gestione per il [PswsRoleBasedPlugins](https://code.msdn.microsoft.com:443/windowsdesktop/PswsRoleBasedPlugins-9c79b75a) esempio. Se lo script di Windows PowerShell fornito con questo esempio è stato usato per configurare l'endpoint senza modificare lo script, tale cartella viene **C:\inetpub\wwwroot\Modata**. Selezionare MOF e fare clic su **aperto**.

   A questo punto, aprire i file MOF e schema. XML in un editor di testo e notare che contengono i mapping per le risorse di processo e il servizio. Usa il file MOF [Distributed Management Task Force](https://www.dmtf.org/) standard (DTMF) MOF (Managed Object). Il file di schema. XML viene utilizzato un XML schema descritto in [Schema di Mapping della risorsa](./resource-mapping-schema.md).

   La procedura seguente viene descritto come importare i cmdlet di Hyper-V in per il modello dello schema.

#### <a name="importing-cmdlets-into-the-schema"></a>Importa i cmdlet all'interno dello schema

1. Fare clic su un'area vuota della finestra di progettazione dello schema e fare clic su **cmdlet di importazione**. Il **importazione guidata dei Cmdlet** viene visualizzata la finestra.

2. Assicurarsi che **Computer locale** sia selezionata e fare clic su **successivo**.

3. Assicurarsi che sia selezionato installati i moduli di Windows PowerShell e selezionare la tecnologia Hyper-V nell'elenco a discesa. Fare clic su **successivo**. Fare clic su **Avanti**.

4. Nel **Cmdlet sostantivo** elenco, selezionare **VM**. Fare clic su **Avanti**.

5. In questo esempio si esegue l'associazione solo i comandi Get e Delete con i cmdlet. Cancella il **CREATE** e **UPDATE** caselle di controllo e assicurarsi che il **ottenere** e **Elimina** vengono controllate le caselle di controllo. Assicurarsi che il `Get-VM` cmdlet sia selezionato per **ottenere**e il `Remove-VM` cmdlet sia selezionato per **Elimina**.

6. Poiché i metadati per i cmdlet di macchina virtuale non viene specificano un tipo di output, è necessario eseguire il cmdlet per specificare il tipo di output. Selezionare **tipo di output forniscono** e fare clic su **eseguire cmdlet**. Il **eseguire Cmdlet** viene visualizzata la finestra. Fare clic su **eseguiti**. Il **tipo CLR** è popolato con il `VirtualMachine` tipo. Fare clic su **OK**, quindi fare clic su **successivo**.

7. Per impostazione predefinita, tutte le proprietà dell'oggetto VirtualMachine sono selezionate. È possibile cancellare le proprietà che non si desidera nell'ambito dei dati restituiti quando si richiede questa risorsa dal servizio web. Fare clic su **Avanti**.

8. È necessario selezionare almeno una proprietà da utilizzare come chiave. Selezionare **Name** nell'elenco e fare clic su **successivo**.

9. Finestra successiva consente di eseguire il mapping di proprietà della risorsa OData di gestione per le proprietà dei cmdlet sottostante. La procedura guidata esegue il mapping delle proprietà con nomi identici per impostazione predefinita. Ad esempio, il `ComputerName` viene eseguito il mapping di proprietà della risorsa per il `ComputerName` proprietà dei cmdlet.  In questo modo è possibile specificare il `ComputerName` proprietà in una richiesta al servizio web e hanno il valore specificato da passare per il `Get-VM` cmdlet. `Id` e `Name` viene anche eseguito il mapping per impostazione predefinita.

   10. Fare clic su **successivo**, quindi fare clic su **fine**.

       La risorsa di macchina virtuale viene ora visualizzato nella finestra di progettazione dello schema. È possibile esaminare le proprietà e le operazioni associate alla risorsa. Successivamente, si esporterà i file di schema aggiornato nella directory virtuale per il servizio web.

#### <a name="exporting-schema-files-from-the-schema-designer"></a>Esportazione di file di schema dalla finestra di progettazione dello schema

1. Fare clic su un'area vuota della finestra di progettazione dello schema e fare clic su **file di Schema** ; **Esportare**. Il **Salva con nome** viene visualizzata la finestra.

2. Passare alla stessa directory da cui è stato importato il file MOF. Denominare il file di quello utilizzato per il file MOF originale (MOF per impostazione predefinita), quindi scegliere **salvare**. Confermare che si desidera sovrascrivere il file esistente.

   Anche se è non è dichiarato in modo esplicito nel **Salva con nome** finestra di dialogo, questa impostazione sostituisce i file MOF sia il file schema. Xml.

## <a name="next-steps"></a>Passaggi successivi

Prima di accedere alla nuova risorsa di macchina virtuale dal servizio web OData di gestione, è necessario aggiornare il file RbacConfiguration.xml per consentire l'accesso al modulo Hyper-V di Windows PowerShell come descritto in [autorizzazione basata sui ruoli di configurazione](./configuring-role-based-authorization.md), e sarà anche necessario riavviare il servizio web.