---
ms.date: 07/10/2019
keywords: jea,powershell,sicurezza
title: Prerequisiti di JEA
ms.openlocfilehash: 8fca5c068412e86acfdb8bed400699f721b76191
ms.sourcegitcommit: e894ed833cef57967cdaf002f8c883f66864e836
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 08/25/2019
ms.locfileid: "70017812"
---
# <a name="prerequisites"></a>Prerequisiti

Just Enough Administration (JEA) è una funzionalità inclusa in PowerShell 5.0 e versioni successive. Questo articolo descrive i prerequisiti che devono essere soddisfatti per poter usare JEA.


## <a name="check-which-version-of-powershell-is-installed"></a>Controllare quale versione di PowerShell è installata

Per controllare quale versione di PowerShell è installata nel sistema, verificare la variabile `$PSVersionTable` in un prompt dei comandi di Windows PowerShell.

```powershell
$PSVersionTable.PSVersion
```

```Output
Major  Minor  Build  Revision
-----  -----  -----  --------
5      1      14393  1000
```

JEA è disponibile in PowerShell 5.0 e versioni successive. Per una funzionalità completa, è consigliabile installare la versione più recente di PowerShell disponibile per il sistema. La tabella seguente illustra la disponibilità di JEA in Windows Server:

| Sistema operativo server |                Disponibilità di JEA                |
| ----------------------- | ---------------------------------------------- |
| Windows Server 2016+    | Preinstallato                                   |
| Windows Server 2012 R2  | Funzionalità completa con WMF 5.1                |
| Windows Server 2012     | Funzionalità completa con WMF 5.1                |
| Windows Server 2008 R2  | Funzionalità limitata<sup>1</sup> con WMF 5.1 |

È anche possibile usare JEA nel computer di casa o di lavoro:

| Sistema operativo client |                   Disponibilità di JEA                   |
| ----------------------- | ---------------------------------------------------- |
| Windows 10 1607+        | Preinstallato                                         |
| Windows 10 1603, 1511   | Preinstallato, con funzionalità limitata<sup>2</sup> |
| Windows 10 1507         | Non disponibile                                        |
| Windows 8, 8.1          | Funzionalità completa con WMF 5.1                      |
| Windows 7               | Funzionalità limitata<sup>1</sup> con WMF 5.1       |

- <sup>1</sup> JEA non può essere configurato per l'uso di account del servizio gestito del gruppo in Windows Server 2008 R2 o Windows 7. *Sono* supportati gli account virtuali e le altre funzionalità JEA.

- <sup>2</sup> Le funzionalità JEA seguenti non sono supportate nelle versioni di Windows 10 1511 e 1603:

  - Esecuzione di un account del servizio gestito del gruppo
  - Regole di accesso condizionale in configurazioni di sessione
  - Unità utente
  - Concessione dell'accesso agli account utente locali

  Per ottenere supporto per queste funzionalità, aggiornare Windows alla versione 1607 (Aggiornamento dell'anniversario) o versione successiva.

### <a name="install-windows-management-framework"></a>Installare Windows Management Framework

Se si esegue una versione precedente di PowerShell, può essere necessario aggiornare il sistema con la versione più recente di Windows Management Framework (WMF). Per altre informazioni, vedere la [documentazione di WMF](/powershell/wmf/overview).

È consigliabile testare la compatibilità del carico di lavoro con WMF prima di aggiornare tutti i server.

Gli utenti di Windows 10 devono installare gli aggiornamenti delle funzionalità più recenti per ottenere la versione corrente di Windows PowerShell.

## <a name="enable-powershell-remoting"></a>Comunicazione remota di PowerShell

La comunicazione remota di PowerShell costituisce la base su cui viene compilato JEA. È necessario assicurarsi che la comunicazione remota di PowerShell sia abilitata e adeguatamente protetta prima di usare JEA. Per altre informazioni, vedere [Sicurezza di Gestione remota Windows](/powershell/scripting/learn/remoting/winrmsecurity).

La comunicazione remota di PowerShell è abilitata per impostazione predefinita su Windows Server 2012, 2012 R2 e 2016. È possibile abilitare la comunicazione remota di PowerShell eseguendo il comando seguente in una finestra di PowerShell con privilegi elevati.

```powershell
Enable-PSRemoting
```

## <a name="enable-powershell-module-and-script-block-logging-optional"></a>Abilitare la registrazione del blocco di script e del modulo di PowerShell (facoltativo)

La procedura seguente consente di registrare tutte le azioni di PowerShell nel sistema. Sebbene non sia necessaria la registrazione del modulo di PowerShell per JEA, è consigliabile attivare la registrazione per assicurarsi che i comandi eseguiti dagli utenti siano registrati in una posizione centrale.

È possibile configurare i criteri di registrazione del modulo di PowerShell tramite i criteri di gruppo.

1. Aprire l'Editor Criteri di gruppo locali in una workstation o un oggetto Criteri di gruppo nella Console Gestione Criteri di gruppo in un Controller di dominio Active Directory
2. Passare a **Configurazione computer\\Modelli amministrativi\\Componenti di Windows\\Windows PowerShell**
3. Fare doppio clic su **Attiva registrazione moduli**
4. Fare clic su **Abilitato**
5. Nella sezione Opzioni fare clic su **Mostra** accanto a Nomi moduli
6. Digitare `*` nella finestra popup per registrare i comandi di tutti i moduli.
7. Fare clic su **OK** per impostare i criteri
8. Fare doppio clic su **Attiva registrazione blocco script di PowerShell**
9. Fare clic su **Abilitato**
10. Fare clic su **OK** per impostare i criteri
11. (Solo in computer aggiunti a un dominio) Eseguire `gpupdate` o attendere che i Criteri di gruppo elaborino i criteri aggiornati e applichino le impostazioni

È anche possibile abilitare la trascrizione di PowerShell a livello di sistema con i criteri di gruppo.

## <a name="next-steps"></a>Passaggi successivi

[Creare un file delle funzionalità del ruolo](role-capabilities.md)

[Creare un file di configurazione sessione](session-configurations.md)

## <a name="see-also"></a>Vedere anche

[Sicurezza di Gestione remota Windows](/powershell/scripting/learn/remoting/winrmsecurity)

[PowerShell ♥ the Blue Team](https://devblogs.microsoft.com/powershell/powershell-the-blue-team/)
