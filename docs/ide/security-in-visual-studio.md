---
title: Sicurezza in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 02/17/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- code access security, coding errors
- security [.NET Framework], about security
ms.assetid: 318c34ce-f643-468c-83a1-843196f5d845
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload:
- multiple
ms.openlocfilehash: c9d546d4020cb9a8e73efdea77fdb85d77d6146d
ms.sourcegitcommit: a07b789cc41ed72664f2c700c1f114476e7b0ddd
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 02/19/2018
---
# <a name="security-in-visual-studio"></a>Sicurezza in Visual Studio

È opportuno includere considerazioni sulla sicurezza in tutti gli aspetti dello sviluppo di applicazioni, dalla progettazione alla distribuzione. Iniziare eseguendo Visual Studio nel modo più sicuro possibile. Vedere [Autorizzazioni utente](../ide/user-permissions-and-visual-studio.md).  
  
 Per sviluppare applicazioni efficacemente sicure, è necessario acquisire familiarità con i concetti e le funzionalità relative alla sicurezza delle piattaforme per le quali si sviluppano le applicazioni. È inoltre necessario comprendere le tecniche di sicurezza del codice.  
  
## <a name="understanding-security"></a>Informazioni sulla sicurezza  
 [Sicurezza](/dotnet/standard/security/index)  
 Vengono descritte la sicurezza dall'accesso di codice, la sicurezza basata sui ruoli e i criteri e gli strumenti di sicurezza di .NET Framework.  
  
 [Defend Your Code with Top Ten Security Tips Every Developer Must Know](http://go.microsoft.com/fwlink/?LinkId=72877) (Dieci suggerimenti principali per la protezione del codice che ogni sviluppatore dovrebbe conoscere)  
 Vengono descritte le problematiche da tenere in considerazione per non compromettere i dati o il sistema.  
  
## <a name="coding-for-security"></a>Creazione di codice per la sicurezza  
 La maggior parte degli errori di codifica che determinano vulnerabilità nella sicurezza si verificano perché gli sviluppatori compiono valutazioni errate rispetto all'input degli utenti o non hanno una comprensione globale della piattaforma per la quale sviluppano le applicazioni.  
  
 [Linee guida per la generazione di codice sicuro](/dotnet/standard/security/secure-coding-guidelines)  
 Vengono fornite indicazioni per la classificazione dei componenti finalizzata a risolvere i problemi di sicurezza.  
  
 [Procedure di sicurezza consigliate](/cpp/top/security-best-practices-for-cpp)  
 Vengono presi in esame i sovraccarichi del buffer e viene fornita una sintesi completa della funzionalità di controllo della sicurezza di Microsoft Visual C++ resa disponibile dal flag /GS della fase di compilazione.

## <a name="building-for-security"></a>Compilazione di codice per la sicurezza  
 La sicurezza è anche un aspetto importante del processo di compilazione.  Alcuni passaggi aggiuntivi possono migliorare la sicurezza di un'app distribuita e impedire il reverse engineering non autorizzato, lo spoofing o attacchi di altro tipo.

 [Dotfuscator Community Edition (CE)](dotfuscator/index.md)  
 Illustra come configurare e iniziare a usare la versione gratuita di PreEmptive Protection - Dotfuscator Community Edition per proteggere gli assembly .NET da attacchi di reverse engineering e da usi non autorizzati, ad esempio il debug non autorizzato.
  
 [Gestione delle firme di assembly e manifesti](managing-assembly-and-manifest-signing.md)  
 Illustra la firma con nome sicuro, che può essere usata per identificare in modo univoco i componenti software, impedendo così lo spoofing dei nomi.