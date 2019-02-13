---
ms.date: 06/12/2017
keywords: dsc,powershell,configurazione,installazione
title: Classe MSFT_DSCLocalConfigurationManager
ms.openlocfilehash: 7f6aaf209601e99b0120407eb301d32fcfda9eb8
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 02/03/2019
ms.locfileid: "55678261"
---
# <a name="msftdsclocalconfigurationmanager-class"></a>Classe MSFT_DSCLocalConfigurationManager

Gestione configurazione locale (LCM) che controlla lo stato dei file di configurazione e usa l'agente di configurazione per applicare le configurazioni.

La sintassi seguente è semplificata dal codice MOF (Managed Object Format) e include tutte le proprietà ereditate.

## <a name="syntax"></a>Sintassi

```
[ClassVersion("1.0.0"), dynamic, provider("dsccore"), AMENDMENT]
class MSFT_DSCLocalConfigurationManager
{
};
```

## <a name="members"></a>Members

La classe **MSFT_DSCLocalConfigurationManager** ha i membri seguenti:

- [Metodo][]

### <a name="methods"></a>Metodi

La classe **MSFT_DSCLocalConfigurationManager** dispone di questi metodi.

|Metodo |Description |
|:--- |:---|
| [ApplyConfiguration](msft-dsclocalconfigurationmanager-applyconfiguration.md)| Usa l'agente di configurazione per applicare la configurazione in sospeso.|
| [DisableDebugConfiguration](msft-dsclocalconfigurationmanager-disabledebugconfiguration.md)| Disabilita il debug delle risorse DSC.|
| [EnableDebugConfiguration](msft-dsclocalconfigurationmanager-enabledebugconfiguration.md)| Abilita il debug delle risorse DSC.|
| [GetConfiguration](msft-dsclocalconfigurationmanager-getconfiguration.md)| Invia il documento di configurazione al nodo gestito e usa il metodo **Get** dell'agente di configurazione per applicare la configurazione.|
| [GetConfigurationResultOutput](msft-dsclocalconfigurationmanager-getconfigurationresultoutput.md)| Ottiene l'output dell'agente di configurazione relativo a un processo specifico.|
| [GetConfigurationStatus](msft-dsclocalconfigurationmanager-getconfigurationstatus.md)| Ottenere la cronologia dello stato della configurazione.|
| [GetMetaConfiguration](msft-dsclocalconfigurationmanager-getmetaconfiguration.md)| Ottiene le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.|
| [PerformRequiredConfigurationChecks](msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)| Avvia una verifica di coerenza.|
| [RemoveConfiguration](msft-dsclocalconfigurationmanager-removeconfiguration.md)| Rimuove i file di configurazione.|
| [ResourceGet](msft-dsclocalconfigurationmanager-resourceget.md)| Chiama direttamente il metodo di **Get** di una risorsa DSC.|
| [ResourceSet](msft-dsclocalconfigurationmanager-resourceset.md)| Chiama direttamente il metodo di **Set** di una risorsa DSC.|
| [ResourceTest](msft-dsclocalconfigurationmanager-resourcetest.md)| Chiama direttamente il metodo di **Test** di una risorsa DSC.|
| [RollBack](msft-dsclocalconfigurationmanager-rollback.md)| Esegue il rollback di una configurazione precedente.|
| [SendConfiguration](msft-dsclocalconfigurationmanager-sendconfiguration.md)| Invia il documento di configurazione al nodo gestito e lo salva come modifica in sospeso.|
| [SendConfigurationApply](msft-dsclocalconfigurationmanager-sendconfigurationapply.md)| Invia il documento di configurazione al nodo gestito e usa l'agente di configurazione per applicare la configurazione.|
| [SendConfigurationApplyAsync](msft-dsclocalconfigurationmanager-sendconfigurationapplyasync.md)| Inviare il documento di configurazione per il nodo gestito e iniziare a usare l'agente di configurazione per applicare la configurazione. Usare GetConfigurationResultOutput per recuperare l'output dei risultati.|
| [SendMetaConfigurationApply](msft-dsclocalconfigurationmanager-sendmetaconfigurationapply.md)| Configura le impostazioni di Gestione configurazione locale usate per controllare l'agente di configurazione.|
| [StopConfiguration](msft-dsclocalconfigurationmanager-stopconfiguration.md)| Arresta la configurazione in corso.|
| [TestConfiguration](msft-dsclocalconfigurationmanager-testconfiguration.md)| Consente di inviare il documento di configurazione al nodo gestito e verificare la configurazione corrente sulla base del documento.|

## <a name="requirements"></a>Requisiti

**MOF:** DscCore.mof

**Spazio dei nomi**: Root\Microsoft\Windows\DesiredStateConfiguration