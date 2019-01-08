---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Modalità di utilizzo dei profili in Windows PowerShell ISE
ms.assetid: 0219626a-6da5-4acc-b630-d058e8b29cc6
ms.openlocfilehash: b319aa089c2a4a7008acd9850f15342dac70aee2
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 12/14/2018
ms.locfileid: "53401650"
---
# <a name="how-to-use-profiles-in-windows-powershell-ise"></a>Modalità di utilizzo dei profili in Windows PowerShell ISE

Questo argomento illustra come usare i profili in Windows PowerShell® Integrated Scripting Environment (ISE). Prima di eseguire le attività in questa sezione, è consigliabile consultare [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles) oppure digitare `Get-Help about_Profiles` nel riquadro della console e premere **INVIO**.

Un profilo è uno script di Windows PowerShell ISE che viene eseguito automaticamente quando si avvia una nuova sessione.  È possibile creare uno o più profili di Windows PowerShell per Windows PowerShell ISE e usarli per configurare l'ambiente Windows PowerShell o Windows PowerShell ISE, prepararlo per l'uso, con le variabili, gli alias, le funzioni e le preferenze di colore e tipo di carattere che si vuole avere a disposizione. Il profilo interessa ogni sessione di Windows PowerShell ISE avviata.

> [!NOTE]
> I criteri di esecuzione di Windows PowerShell determinano se è possibile eseguire gli script e caricare un profilo. I criteri di esecuzione predefiniti, "Restricted", impediscono l'esecuzione di tutti gli script, inclusi i profili. Se si usano i criteri "Restricted", il profilo non potrà essere caricato. Per altre informazioni sui criteri di esecuzione, vedere [about_Execution_Policies](/powershell/module/microsoft.powershell.core/about/about_execution_policies).

## <a name="selecting-a-profile-to-use-in-the-windows-powershell-ise"></a>Selezione di un profilo da usare in Windows PowerShell ISE

Windows PowerShell ISE supporta i profili per l'utente corrente e per tutti gli utenti. Supporta anche i profili Windows PowerShell che si applicano a tutti gli host.

Il profilo usato dipende da come si usano Windows PowerShell e Windows PowerShell ISE.

- Se si usa solo Windows PowerShell ISE per eseguire Windows PowerShell, salvare tutti gli elementi in uno dei profili ISE specifici, ad esempio il profilo CurrentUserCurrentHost per Windows PowerShell ISE o il profilo AllUsersCurrentHost per Windows PowerShell ISE.

- Se si usano più programmi host per l'esecuzione di Windows PowerShell, salvare funzioni, alias, variabili e comandi in un profilo che interessa tutti i programmi host, ad esempio il profilo CurrentUserAllHosts o il profilo AllUsersAllHosts, e quindi salvare le funzionalità specifiche di ISE, come la personalizzazione di colori e tipi di carattere, nel profilo CurrentUserCurrentHost per il profilo di Windows PowerShell ISE o il profilo AllUsersCurrentHost per Windows PowerShell ISE.

I seguenti profili possono essere creati e usati in Windows PowerShell ISE. Ogni profilo viene salvato nel proprio percorso specifico.

| Tipo di profilo | Percorso del profilo |
| --- | --- |
| **Utente corrente, PowerShell ISE**| `$PROFILE.CurrentUserCurrentHost` o `$PROFILE` |
| **Tutti gli utenti, PowerShell ISE**| `$PROFILE.AllUsersCurrentHost` |
| **Utente corrente, tutti gli host**| `$PROFILE.CurrentUserAllHosts` |
| **Tutti gli utenti, tutti gli host** | `$PROFILE.AllUsersAllHosts` |

## <a name="to-create-a-new-profile"></a>Per creare un nuovo profilo

Per creare un nuovo profilo "Utente corrente, Windows PowerShell ISE", eseguire questo comando:

```powershell
if (!(Test-Path -Path $PROFILE ))
{ New-Item -Type File -Path $PROFILE -Force }
```

Per creare un nuovo profilo "Tutti gli utenti, Windows PowerShell ISE", eseguire questo comando:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersCurrentHost))
{ New-Item -Type File -Path $PROFILE.AllUsersCurrentHost -Force }
```

Per creare un nuovo profilo "Utente corrente, tutti gli host", eseguire questo comando:

```powershell
if (!(Test-Path -Path $PROFILE.CurrentUserAllHosts))
{ New-Item -Type File -Path $PROFILE.CurrentUserAllHosts -Force }
```

Per creare un nuovo profilo "Tutti gli utenti, tutti gli host", digitare:

```powershell
if (!(Test-Path -Path $PROFILE.AllUsersAllHosts))
{ New-Item -Type File -Path $PROFILE.AllUsersAllHosts -Force }
```

## <a name="to-edit-a-profile"></a>Per modificare un profilo

1. Per aprire il profilo, eseguire il comando psedit con la variabile che specifica il profilo da modificare. Ad esempio, per aprire il profilo "Utente corrente, Windows PowerShell ISE", digitare: `psEdit $PROFILE`

2. Aggiungere alcuni elementi al profilo. Di seguito sono riportati alcuni esempi per iniziare:

   - Per modificare il colore di sfondo predefinito del riquadro della console impostandolo sul blu, nel file del profilo digitare: `$psISE.Options.OutputPaneBackground = 'blue'` . Per altre informazioni sulla variabile $psISE, vedere [Riferimenti al modello a oggetti di Windows PowerShell ISE](object-model/The-ISE-Object-Model-Hierarchy.md).

   - Per modificare le dimensioni del carattere impostandole su 20, nel file del profilo digitare: `$psISE.Options.FontSize =20`

3. Per salvare il file del profilo, nel menu **File** fare clic su **Salva**. Le personalizzazioni verranno applicate alla successiva apertura di Windows PowerShell ISE.

## <a name="see-also"></a>Vedere anche

- [about_Profiles](/powershell/module/microsoft.powershell.core/about/about_profiles)
- [Introduzione a Windows PowerShell ISE](Introducing-the-Windows-PowerShell-ISE.md)