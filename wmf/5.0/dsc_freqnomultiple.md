---
ms.date: 06/12/2017
keywords: wmf,powershell,installazione
ms.openlocfilehash: a3ac215396206fba62bce303733429d60722ee6b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 05/17/2018
ms.locfileid: "34218383"
---
# <a name="frequencies-for-refreshmode-and-configurationmode-dont-need-to-be-multiples-of-each-other"></a>Non è necessario che le frequenze per RefreshMode e ConfigurationMode siano multipli l'una dell'altra

Nella versione precedente di DSC, Gestione configurazione locale gestisce `RefreshFrequencyMins` e `ConfigurationModeFrequencyMins` come multipli reciproci. In WMF 5.0 RTM, queste proprietà vengono elaborate in modo indipendente.

Per altre informazioni, vedere [Configurazione di Gestione configurazione locale](https://msdn.microsoft.com/powershell/dsc/metaconfig).
