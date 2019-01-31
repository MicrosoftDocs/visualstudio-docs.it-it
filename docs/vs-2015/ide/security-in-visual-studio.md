---
title: Sicurezza
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
caps.latest.revision: 24
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 40e751fa3edb74df01a9b8a2b0aa4643304f17dc
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MTE95
ms.contentlocale: it-IT
ms.lasthandoff: 01/23/2019
ms.locfileid: "54771011"
---
# <a name="security-in-visual-studio"></a>Sicurezza in Visual Studio
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

È opportuno includere considerazioni sulla sicurezza in tutti gli aspetti dello sviluppo di applicazioni, dalla progettazione alla distribuzione. Iniziare eseguendo Visual Studio nel modo più sicuro possibile. Vedere [Autorizzazioni utente](../ide/user-permissions-and-visual-studio.md).

 Per sviluppare applicazioni efficacemente sicure, è necessario acquisire familiarità con i concetti e le funzionalità relative alla sicurezza delle piattaforme per le quali si sviluppano le applicazioni. È inoltre necessario comprendere le tecniche di sicurezza del codice.

## <a name="understanding-security"></a>Informazioni sulla sicurezza
 [Sicurezza](http://msdn.microsoft.com/library/9a9621d7-8883-4a4f-a874-65e8e09e20a6) Vengono descritte la sicurezza dall'accesso di codice, la sicurezza basata sui ruoli e i criteri e gli strumenti di sicurezza di .NET Framework.

 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Dieci suggerimenti principali per la protezione del codice che ogni sviluppatore dovrebbe conoscere) Vengono descritte le problematiche da tenere in considerazione per non compromettere i dati o il sistema.

## <a name="coding-for-security"></a>Creazione di codice per la sicurezza
 La maggior parte degli errori di codifica che determinano vulnerabilità nella sicurezza si verificano perché gli sviluppatori compiono valutazioni errate rispetto all'input degli utenti o non hanno una comprensione globale della piattaforma per la quale sviluppano le applicazioni.

 [Linee guida per la generazione di codice sicuro](http://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) Vengono fornite indicazioni per la classificazione dei componenti finalizzata a risolvere i problemi di sicurezza.

 [Procedure consigliate per la sicurezza](http://msdn.microsoft.com/library/86acaccf-cdb4-4517-bd58-553618e3ec42) Vengono presi in esame i sovraccarichi del buffer e viene fornita una sintesi completa della funzionalità di controllo della sicurezza di Microsoft Visual C++ resa disponibile dal flag /GS della fase di compilazione.
