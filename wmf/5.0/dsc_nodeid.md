---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: wmf,powershell,installazione
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a>Separazione degli ID per nodi e configurazioni

## <a name="overview"></a>Panoramica

Per garantire un'esperienza più flessibile e semplificata durante l'uso di DSC in modalità Pull, in questa versione sono state aggiunte numerose funzionalità. Queste funzionalità sono progettate in modo da offrire la flessibilità necessaria per configurare e distribuire le configurazioni su più nodi, offrendo allo stesso tempo la possibilità di tenere traccia dello stato e di creare report di informazioni per ogni nodo singolarmente. Queste funzionalità sono le seguenti:

* Un nome di configurazione che identifica la configurazione per un computer. Questo nome può essere condiviso da più nodi di destinazione 
* Un ID di agente che identifica in modo univoco un singolo nodo
* Un passaggio di registrazione che si verifica solo la prima volta che un nodo di destinazione si connette a un server di pull

**Nota:** queste caratteristiche e funzionalità sono state aggiunte e non sostituiscono i concetti e le funzionalità esistenti relativi al pull. È possibile usare queste nuove funzionalità o quelle meno recenti con il nuovo server di pull incluso in questa versione.

Per altre informazioni, vedere [Configurazione di un client di pull con nomi di configurazione](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames).

