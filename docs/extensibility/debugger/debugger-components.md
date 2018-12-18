---
title: Componenti del debugger | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debugging [Visual Studio], components
- components [Visual Studio SDK], debugging
- debugging [Debugging SDK], components
ms.assetid: 8b8ab77f-a134-495c-be42-3bc51aa62dfb
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: b465772f8d3ddba173ecb406845f978765f63cdc
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="debugger-components"></a>Componenti del debugger
Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger viene implementato come un pacchetto VSPackage e gestisce la sessione di debug intero. La sessione di debug è costituito dai seguenti elementi:  
  
-   **Pacchetto di debug:** il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] debugger fornisce la stessa interfaccia utente indipendentemente da ciò che viene eseguito il debug.  
  
-   **Gestione di debug sessioni (SDM):** offre un'interfaccia coerente a livello di codice per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] Debugger per la gestione di una varietà di motori di debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Gestore di debug di processi (PDM):** gestisce, per tutte le istanze in esecuzione di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)], un elenco di tutti i programmi che possono essere o sottoposti a debug. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
-   **Eseguire il debug del motore (DE):** è responsabile del monitoraggio di un programma in fase di debug, comunica lo stato del programma in esecuzione il SDM e PDM e l'interazione con l'analizzatore di espressioni e il provider di simboli per fornire analisi in tempo reale del stato della memoria e le variabili del programma. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per i linguaggi supportati) e i fornitori di terze parti che desiderano supportare i propri fase di esecuzione.  
  
-   **Analizzatore di espressioni (Java EE):** fornisce il supporto per la valutazione in modo dinamico di variabili ed espressioni fornite dall'utente quando un programma è stato arrestato in un particolare punto. Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per i linguaggi supportati) e i fornitori di terze parti che desiderano supportare la propria lingua.  
  
-   **Provider di simboli (SP):** collettivamente indicati come un gestore di simboli, esegue il mapping i simboli di debug di un programma a un'istanza in esecuzione del programma in modo che è possibile specificare informazioni significative (ad esempio livello di codice sorgente il debug e l'espressione di valutazione). Viene implementato da [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (per Common Language Runtime [CLR] simboli e il DataBase di programma [PDB] dei simboli di formato di file) e da fornitori di terze parti che hanno i propri metodo proprietario dell'archiviazione delle informazioni di debug.  
  
 Nel diagramma seguente viene illustrata la relazione tra questi elementi del debugger di Visual Studio.  
  
 ![Panoramica dei componenti di debug](../../extensibility/debugger/media/dbugcompovrview.gif "DBugCompOvrview")  
  
## <a name="in-this-section"></a>In questa sezione  
 [Pacchetto di debug](../../extensibility/debugger/debug-package.md)  
 Viene descritto il pacchetto di debug, viene eseguito nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] della shell e gestisce tutti dell'interfaccia utente.  
  
 [Gestione del debug dei processi](../../extensibility/debugger/process-debug-manager.md)  
 Viene fornita una panoramica delle funzionalità di PDM, ovvero la gestione dei processi di debug può essere eseguito.  
  
 [Gestione del debug delle sessioni](../../extensibility/debugger/session-debug-manager.md)  
 Definisce il SDM, che fornisce una visualizzazione unificata della sessione di debug all'IDE. Il SDM gestisce la Germania.  
  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)  
 Documenta i servizi di debug che fornisce la Germania.  
  
 [Modalità operative](../../extensibility/debugger/operational-modes.md)  
 Viene fornita una panoramica delle tre modalità in cui può operare nell'IDE: modalità di interruzione, modalità di esecuzione e la modalità di progettazione. Vengono descritte anche i meccanismi di transizione.  
  
 [Analizzatore di espressioni](../../extensibility/debugger/expression-evaluator.md)  
 Viene illustrato lo scopo dell'analizzatore di Espressioni in fase di esecuzione.  
  
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)  
 Viene illustrato come, al momento dell'implementazione, il provider di simboli valuta variabili ed espressioni.  
  
 [Visualizzatore di tipi e visualizzatore personalizzato](../../extensibility/debugger/type-visualizer-and-custom-viewer.md)  
 Vengono illustrate le caratteristiche sono un visualizzatore di tipo e un visualizzatore personalizzato e il ruolo dell'analizzatore di espressioni riproduce nel supporto di entrambi.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come la Germania funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione rilevante a esso.  
  
 [Attività di debug](../../extensibility/debugger/debugging-tasks.md)  
 Contiene collegamenti a numerose attività di debug, ad esempio un programma di avvio e la valutazione di espressioni.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)