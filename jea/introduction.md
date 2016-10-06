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
translationtype: Human Translation
ms.sourcegitcommit: e6b5107b7222708dcceff14bc26f0e12ef98d728
ms.openlocfilehash: 00d568234b1453b9161b60d20117374ee4111ab3

---

# Introduzione

##  **Motivazione**  
Quando si concede a un utente l'accesso con privilegi ai propri sistemi, si estende il limite di trust a tale utente.
Questo è un rischio: gli amministratori sono una superficie di attacco.
Gli attacchi interni e le credenziali rubate sono sia reali che comuni.

##  **Non è un problema nuovo**  
Probabilmente si ha familiarità con il principio di privilegio minimo e si può usare una forma di controllo degli accessi in base al ruolo (RBAC) con le applicazioni che la gestiscono.
Tuttavia, l'efficacia e la gestibilità di queste soluzioni spesso sono limitate a causa della vastità dell'ambito dall'imprecisione.
E la copertura RBAC presenta anche delle lacune.
In Windows, ad esempio, l'accesso con privilegi è sostanzialmente un commutatore binario, che forza la concessione di autorizzazioni non necessarie quando si aggiungono utenti al gruppo Administrators.

##  **JEA (Just Enough Administration)** 
Offre una piattaforma di controllo degli accessi in base al ruolo (RBAC) tramite Comunicazione remota di PowerShell.
*Consente a utenti specifici di eseguire attività amministrative specifiche sui server senza concedere loro diritti di amministratore.*
Ciò consente di colmare le lacune tra le soluzioni RBAC esistenti e semplifica la gestione delle impostazioni.




<!--HONumber=Aug16_HO3-->


