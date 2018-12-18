---
title: Compilazione e creazione in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 07/14/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- builds [Visual Studio], about building in Visual Studio
- custom build steps, types of builds
ms.assetid: c7958821-285f-4e28-9e7a-b5d8b40336a1
caps.latest.revision: "28"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.workload: multiple
ms.openlocfilehash: 29101e8e82fa9babf553be17414f1330cd6f7e18
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="compiling-and-building-in-visual-studio"></a>Compilazione e creazione in Visual Studio

L'esecuzione di una build determina la creazione di assembly e applicazioni eseguibili dal codice sorgente in qualsiasi fase di un ciclo di sviluppo. A livello generale il processo di compilazione è molto simile tra progetti di tipi diversi, quali Windows, ASP.NET, app per dispositivi mobili e altri ancora. Il processo di compilazione è anche molto simile tra linguaggi di programmazione come C#, Visual Basic, C++ e F#. 

Compilando spesso il codice è possibile identificare rapidamente gli errori in fase di compilazione, ad esempio sintassi non corretta, parole chiave con errori di digitazione e tipi non corrispondenti. È anche possibile rilevare e risolvere rapidamente gli errori di runtime, ad esempio errori logici e semantici, compilando frequentemente il codice ed eseguendo le versioni di debug.  

Una compilazione riuscita conferma che la sintassi del codice sorgente dell'applicazione è corretta e che tutti i riferimenti statici a librerie, assembly e altri componenti sono stati risolti. Il risultato è un file eseguibile dell'applicazione che può essere testato per il funzionamento corretto sia in un [ambiente di debug](../debugger/index.md), sia mediante vari test manuali e automatici per la [convalida della qualità del codice](../test/improve-code-quality.md). Dopo aver testato completamente l'applicazione è quindi possibile compilare una versione di rilascio da distribuire ai clienti. Per un'introduzione a questo processo, vedere [Procedura dettagliata: Compilazione di un'applicazione](../ide/walkthrough-building-an-application.md).  

La famiglia di prodotti Visual Studio include tre metodi per la compilazione di un'applicazione: l'ambiente IDE Visual Studio, gli strumenti della riga di comando MSBuild e Team Foundation Build in Visual Studio Team Services:
 
| Metodo di compilazione | Vantaggi | 
| --- |--- | --- |  
| IDE |- Creazione immediata di build e test in un debugger.<br />- Esecuzione di compilazioni multiprocessore per progetti C++ e C#.<br />- Personalizzazione di vari aspetti del sistema di compilazione. |
| Riga di comando MSBuild| - Compilazione di progetti senza installare Visual Studio.<br />- Esecuzione di compilazioni multiprocessore per tutti i tipi di progetto.<br />- Personalizzazione della maggior parte delle aree del sistema di compilazione.|
| Team Foundation Build | - Automazione della compilazione come parte di un processo di integrazione continua/recapito continuo.<br />- Implementazione di test automatizzati con ogni compilazione.<br />- Uso di risorse di codice praticamente illimitate per i processi di compilazione.<br />- Modifica del flusso di lavoro di compilazione e creazione di attività di compilazione per eseguire attività personalizzate specifiche.|  

La documentazione di questa sezione approfondisce i dettagli del processo di compilazione basato su IDE. Per informazioni sugli altri metodi, vedere rispettivamente [MSBuild](../msbuild/msbuild.md) e [Integrazione e distribuzione continua](https://www.visualstudio.com/docs/build/overview).

## <a name="overview-of-building-from-the-ide"></a>Panoramica della compilazione nell'ambiente IDE  

Quando si crea un progetto, Visual Studio crea configurazioni della build predefinite per il progetto e la soluzione che contiene il progetto.  Queste configurazioni definiscono come vengono compilati e distribuiti i progetti e le soluzioni. Le configurazioni di progetto, in particolare, sono uniche per la piattaforma di destinazione (ad esempio Windows o Linux) e il tipo di build (ad esempio una build di debug o di rilascio). È possibile modificare queste configurazioni come desiderato e anche creare configurazioni personalizzate in base alle esigenze.

Per un'introduzione iniziale alla compilazione nell'ambiente IDE, vedere [Procedura dettagliata: Compilazione di un'applicazione](walkthrough-building-an-application.md).  

Quindi vedere [Compilazione e pulizia di progetti e soluzioni in Visual Studio](building-and-cleaning-projects-and-solutions-in-visual-studio.md) per informazioni sulle personalizzazioni applicabili ai diversi aspetti del processo. Le personalizzazioni includono la [modifica della directory dell'output](how-to-change-the-build-output-directory.md), la [definizione di eventi di compilazione personalizzati](specifying-custom-build-events-in-visual-studio.md), la [gestione delle dipendenze del progetto](how-to-create-and-remove-project-dependencies.md), la [gestione dei file di log di compilazione](how-to-view-save-and-configure-build-log-files.md) e la [disattivazione della visualizzazione degli avvisi del compilatore](how-to-suppress-compiler-warnings.md).

Successivamente è possibile esplorare molte altre attività:
- [Informazioni sulle configurazioni della build](understanding-build-configurations.md)
- [Informazioni sulle piattaforme di compilazione](understanding-build-platforms.md)
- [Gestione delle proprietà di progetti e soluzioni](managing-project-and-solution-properties.md)  
- Definizione degli eventi di compilazione in [C#](how-to-specify-build-events-csharp.md) e [Visual Basic](how-to-specify-build-events-visual-basic.md) 
- [Impostazione delle opzioni di compilazione](reference/options-dialog-box-projects-and-solutions-build-and-run.md)
- [Compilazione di più progetti in parallelo](../msbuild/building-multiple-projects-in-parallel-with-msbuild.md).  
  
## <a name="see-also"></a>Vedere anche  

- [Compilazione di progetti di siti Web](http://msdn.microsoft.com/Library/a9cbb88c-8fff-4c67-848b-98fbfd823193)   
