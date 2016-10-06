---
title: Miglioramenti del debug delle risorse DSC
author: jaimeo
contributor: amitsara
translationtype: Human Translation
ms.sourcegitcommit: e39aa2e5cbda0c83e24e21c4459d957d8baaff25
ms.openlocfilehash: 33c3fcffdeb281b205ecc48f7cdd470b79e9e068

---


## Miglioramenti del debug delle risorse DSC

In WMF 5.0 il debugger di PowerShell non si arrestava direttamente al metodo della risorsa di classe (Get/Set/Test).
Il problema è stato risolto e ora il debugger si arresta al metodo della risorsa di classe, come i metodi delle risorse basati su MOF.



<!--HONumber=Aug16_HO3-->


