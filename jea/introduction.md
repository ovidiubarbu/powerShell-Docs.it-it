---
description: 
manager: dongill
ms.topic: article
author: jpjofre
ms.prod: powershell
keywords: powershell,cmdlet,jea
ms.date: 2016-06-22
title: introduzione
ms.technology: powershell
ms.openlocfilehash: 71264d1001228249d9f2bb0f72473e9761170bf0
ms.sourcegitcommit: c732e3ee6d2e0e9cd8c40105d6fbfd4d207b730d
translationtype: HT
---
# <a name="introduction"></a>Introduzione

##  <a name="motivation"></a>**Motivazione**  
Quando si concede a un utente l'accesso con privilegi ai propri sistemi, si estende il limite di trust a tale utente.
Questo è un rischio: gli amministratori sono una superficie di attacco.
Gli attacchi interni e le credenziali rubate sono sia reali che comuni.

##  <a name="not-a-new-problem"></a>**Non è un problema nuovo**  
Probabilmente si ha familiarità con il principio di privilegio minimo e si può usare una forma di controllo degli accessi in base al ruolo (RBAC) con le applicazioni che la gestiscono.
Tuttavia, l'efficacia e la gestibilità di queste soluzioni spesso sono limitate a causa della vastità dell'ambito dall'imprecisione.
E la copertura RBAC presenta anche delle lacune.
In Windows, ad esempio, l'accesso con privilegi è sostanzialmente un commutatore binario, che forza la concessione di autorizzazioni non necessarie quando si aggiungono utenti al gruppo Administrators.

##  <a name="just-enough-administration-jea"></a>**JEA (Just Enough Administration)** 
Offre una piattaforma di controllo degli accessi in base al ruolo (RBAC) tramite Comunicazione remota di PowerShell.
*Consente a utenti specifici di eseguire attività amministrative specifiche sui server senza concedere loro diritti di amministratore.*
Ciò consente di colmare le lacune tra le soluzioni RBAC esistenti e semplifica la gestione delle impostazioni.

