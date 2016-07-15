---
title: FullyQuilifiedModuleName per 'uso del modulo'
author: vors
translationtype: Human Translation
ms.sourcegitcommit: cd1d4803497eefad1b5cf476824ec8a2fa263e32
ms.openlocfilehash: ec5a425d17b841f24e94167be946cf9e2daf3316

---

FullyQuilifiedModuleName per 'uso del modulo'
=========================

Ora `using module` si comporta esattamente come altre costruzioni correlate ai moduli di PowerShell.

Problemi di WMF 5.0
----------

* L'utente non può specificare la versione del modulo in `using module`.
* Se nel sistema sono presenti più versioni del modulo, l'utente visualizzerà un errore.

WMF 5.1
----------

* L'utente può usare la [tabella hash](https://msdn.microsoft.com/en-us/library/jj136290(v=vs.85).aspx) `ModuleSpecification`. Questa tabella hash ha lo stesso formato di `Get-Module -FullyQualifiedName`

**Esempio:** `using module @{ModuleName = 'PSReadLine'; RequiredVersion = '1.1'}`

* Se sono presenti più versioni del modulo, PowerShell usa la **stessa logica di risoluzione** di `Import-Module` e non restituisce un errore.

* In questo modo, `using module` è allineato con `Import-Module` e `Import-DscResource`.



<!--HONumber=Jul16_HO1-->


