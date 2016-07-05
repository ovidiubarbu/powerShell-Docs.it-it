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
ms.sourcegitcommit: 7504fe496a8913718847e45115d126caf4049bef
ms.openlocfilehash: 46f4e5b231d09952f11387cec7c80fbfce9f9d4b

---

# Introduzione

##  **Motivazione**  
Quando si concede a un utente l'accesso con privilegi ai propri sistemi, si estende il limite di trust a tale utente.
Questo è un rischio: gli amministratori sono una superficie di attacco.
Gli attacchi interni e le credenziali rubate sono sia reali che comuni.

##  **Non è un problema nuovo**  
Probabilmente si ha dimestichezza con il principio di privilegio minimo e si può utilizzare una forma di controllo di accesso basato sui ruoli (RBAC) con le applicazioni che la gestiscono.
Tuttavia, l'efficacia e la gestibilità di queste soluzioni spesso sono limitate a causa della vastità dell'ambito dall'imprecisione.
E la copertura RBAC presenta anche delle lacune.
In Windows, ad esempio, l'accesso con privilegi è sostanzialmente un commutatore binario, che forza la concessione di autorizzazioni non necessarie quando si aggiungono utenti al gruppo Administrators.

##  **JEA (Just Enough Administration)** 
Offre una piattaforma di controllo degli accessi in base al ruolo (RBAC, Role-Based Access Control) tramite Comunicazione remota di PowerShell.
*Consente a utenti specifici di eseguire attività amministrative specifiche sui server senza concedere loro diritti di amministratore.*
Ciò consente di colmare le lacune tra le soluzioni RBAC esistenti e semplifica la gestione delle impostazioni.




<!--HONumber=Jun16_HO4-->


