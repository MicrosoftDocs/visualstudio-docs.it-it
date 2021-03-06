---
title: Esposizione di tipi alle finestre di progettazione visiva | Microsoft Docs
description: Informazioni su come esporre le definizioni di classi e tipi, incluse quelle negli strumenti personalizzati, in modo che Visual Studio possa renderle disponibili per le finestre di progettazione visive.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5208de3af52e4dad5fb9bb59b16f7b59efb72340
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 03/25/2021
ms.locfileid: "105069673"
---
# <a name="expose-types-to-visual-designers"></a>Esporre i tipi alle finestre di progettazione visiva
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per visualizzare una finestra di progettazione visiva, è necessario avere accesso alle definizioni di classe e di tipo in fase di progettazione. Le classi vengono caricate da un set predefinito di assembly che includono il set di dipendenze completo del progetto corrente (riferimenti più le relative dipendenze). Potrebbe inoltre essere necessario per le finestre di progettazione visiva accedere alle classi e ai tipi definiti nei file generati dagli strumenti personalizzati.

 I [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] sistemi di progetto e offrono il supporto per l'accesso alle classi e ai tipi generati tramite file eseguibili portatili temporanei (PES temporaneo). Tutti i file generati da uno strumento personalizzato possono essere compilati in un assembly temporaneo, in modo che i tipi vengano caricati da tali assembly ed esposti ai progettisti. L'output di ogni strumento personalizzato viene compilato in un PE temporaneo separato e l'esito positivo o negativo di questa compilazione temporanea dipende solo dal fatto che il file generato possa essere compilato o meno. Anche se un progetto non può essere compilato nel suo complesso, il singolo PE temporaneo può essere ancora disponibile per le finestre di progettazione.

 Il sistema del progetto fornisce supporto completo per il rilevamento delle modifiche apportate al file di output di uno strumento personalizzato, purché queste modifiche siano il risultato dell'esecuzione dello strumento personalizzato. Ogni volta che viene eseguito lo strumento personalizzato, viene generato un nuovo PE temporaneo e le notifiche appropriate vengono inviate alle finestre di progettazione.

> [!NOTE]
> Poiché il file di generazione eseguibile del programma temporaneo viene eseguito in background, nessun errore viene segnalato all'utente se la compilazione non riesce.

 Gli strumenti personalizzati che sfruttano i vantaggi del supporto PE temporaneo devono rispettare le regole seguenti:

- **GeneratesDesignTimeSource** deve essere impostato su 1 nel registro di sistema.

     Nessun file eseguibile di programma viene compilata senza questa impostazione.

- Il codice generato deve essere nella stessa lingua dell'impostazione del progetto globale.

     Il PE temporaneo viene compilato indipendentemente da ciò che viene segnalato dallo strumento personalizzato come estensione richiesta in, a <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> condizione che **GeneratesDesignTimeSource** sia impostato su 1 nel registro di sistema. Non è necessario che l'estensione sia *. vb*, *. cs* o *. jsl*; può essere qualsiasi estensione.

- Il codice generato dallo strumento personalizzato deve essere valido e deve essere compilato autonomamente utilizzando solo il set di riferimenti presenti nel progetto al termine dell' <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> esecuzione.

     Quando viene compilato un file PE temporaneo, l'unico file di origine fornito al compilatore è l'output dello strumento personalizzato. Uno strumento personalizzato che usa un file PE temporaneo deve pertanto generare file di output che possono essere compilati indipendentemente da altri file nel progetto.

## <a name="see-also"></a>Vedi anche
- [Introduzione all'oggetto BuildManager](/previous-versions/8f9kffa8(v=vs.140))
- [Implementare generatori di file singoli](../../extensibility/internals/implementing-single-file-generators.md)
- [Registrare generatori di file singoli](../../extensibility/internals/registering-single-file-generators.md)