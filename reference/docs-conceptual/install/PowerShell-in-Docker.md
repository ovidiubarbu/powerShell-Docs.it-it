---
title: Uso di PowerShell in Docker
description: Come usare PowerShell preinstallato in un'immagine Docker.
ms.devlang: powershell
ms.topic: conceptual
ms.date: 03/03/2020
ms.openlocfilehash: 771214c719ef01fe2c8bc56a4b26c629fcad3856
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279658"
---
# <a name="using-powershell-in-docker"></a>Uso di PowerShell in Docker

Le immagini Docker vengono pubblicate con PowerShell preinstallato. Questo articolo illustra come iniziare a usare PowerShell nel contenitore Docker.

## <a name="finding-available-images"></a>Individuazione delle immagini disponibili

Le immagini rilasciate richiedono Docker 17.05 o versione successiva. Si presume anche che l'utente sia in grado di eseguire Docker senza `sudo` o diritti amministrativi locali. Seguire le [istruzioni][install] ufficiali di Docker per installare `docker` correttamente.

I contenitori di versione derivano dall'immagine di distribuzione ufficiale, ad esempio `centos:7`, quindi installano le dipendenze e infine installano il pacchetto di PowerShell.

Questi contenitori sono disponibili in [hub.docker.com/r/microsoft/powershell][docker-release].

Per altre informazioni su queste immagini Docker, visitare il repository [PowerShell-Docker][PowerShell-Docker] in GitHub.

## <a name="using-powershell-in-a-container"></a>Uso di PowerShell in un contenitore

I passaggi seguenti descrivono i comandi Docker necessari per scaricare l'immagine e avviare una sessione interattiva di PowerShell.

```console
docker run -it mcr.microsoft.com/powershell
```

### <a name="remove-the-image-when-no-longer-needed"></a>Rimuovere l'immagine quando non è più necessaria

Il comando seguente viene usato per eliminare il contenitore Docker quando non è più necessario.

```console
docker rmi mcr.microsoft.com/powershell
```

## <a name="legal-and-licensing"></a>Informazioni legali e concessione in licenza

PowerShell viene concesso in licenza in base alla [licenza MIT][].

### <a name="windows-docker-file-and-image-licenses"></a>Licenze per file e immagini Docker per Windows

Richiedendo e usando l'immagine del sistema operativo per i contenitori Windows, l'utente conferma di aver compreso e di accettare le condizioni di licenza supplementari disponibili in Docker Hub:

- [Window Server Core][Window Server Core]
- [Nano Server][Nano Server]

### <a name="telemetry"></a>Telemetria

Per impostazione predefinita, PowerShell raccoglie dati di telemetria limitati senza informazioni personali per facilitare lo sviluppo di versioni future di PowerShell. Per rifiutare esplicitamente l'invio di dati di telemetria, creare una variabile di ambiente denominata `POWERSHELL_TELEMETRY_OPTOUT` impostata sul valore `1` prima di avviare PowerShell dal percorso di installazione. I dati di telemetria raccolti rientrano nell'[informativa sulla privacy di Microsoft][privacy].

<!-- link references -->
[install]: https://docs.docker.com/engine/installation/
[docker-release]: https://hub.docker.com/r/microsoft/powershell/
[appinsights]: https://azure.microsoft.com/services/application-insights/
[licenza MIT]: https://github.com/PowerShell/PowerShell/tree/master/LICENSE.txt
[PowerShell-Docker]: https://github.com/PowerShell/PowerShell-Docker
[Window Server Core]: https://hub.docker.com/r/microsoft/windowsservercore/
[Nano Server]: https://hub.docker.com/r/microsoft/nanoserver/
[privacy]: https://privacy.microsoft.com/privacystatement/
