---
title: Common Language Runtime e la valutazione di espressioni | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], expression evaluation
- expression evaluation, and common language runtime
ms.assetid: b36c1eb5-1aaf-48a6-b287-ee7a273d2b1c
caps.latest.revision: "15"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f3fe862f0115ae4890bd07e0b4f0171ecafcb4b7
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="common-language-runtime-and-expression-evaluation"></a>Common Language Runtime e valutazione delle espressioni
> [!IMPORTANT]
>  In Visual Studio 2015, questa modalità di implementazione analizzatori di espressioni è deprecata. Per informazioni sull'implementazione analizzatori di espressioni CLR, vedere [analizzatori di espressioni CLR](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) e [gestiti esempio analizzatore di espressioni](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).  
  
 Compilatori, ad esempio Visual Basic e c# (si pronuncia C sharp), destinati a Common Language Runtime (CLR), produrre linguaggio MSIL (Microsoft Intermediate), che è successiva compilate in codice nativo. CLR fornisce un motore di debug (DE) per il debug del codice risulta. Se si prevede di integrare il linguaggio di programmazione proprietario nell'IDE di Visual Studio, è possibile scegliere di eseguire la compilazione in MSIL e pertanto non sarà necessario scrivere la propria DE. Tuttavia, è necessario scrivere un analizzatore di espressioni (Java EE) che è in grado di valutazione di espressioni all'interno del contesto del linguaggio di programmazione.  
  
## <a name="discussion"></a>Discussione  
 Espressioni di linguaggio computer vengono in genere analizzate per produrre un set di oggetti dati e un set di operatori utilizzati per modificarli. L'espressione "A + B" può essere analizzato per applicare l'operatore di addizione (+) per i dati di oggetti, ad esempio, "A" e "B", probabilmente risultante in un altro oggetto dati. Set totale di oggetti dati, operatori e le associazioni sono spesso rappresentati in un programma come una struttura ad albero, con gli operatori ai nodi dell'albero e gli oggetti dati nelle filiali. Un'espressione che è stato suddiviso in formato struttura ad albero è spesso definita una struttura ad albero analizzato.  
  
 Una volta un'espressione è stata analizzata, un provider di simboli (SP) viene chiamato per valutare ogni oggetto dati. Se, ad esempio, "A" è definito sia in più di un metodo, quindi la domanda "Quale A?" è necessario rispondere prima che è possibile ottenere il valore dell'oggetto. La risposta restituita dalla stored procedure è simile al seguente "Il terzo elemento sullo stack frame quinto" o "A 50 byte oltre l'inizio della memoria statica allocata a questo metodo."  
  
 Oltre a produrre codice MSIL per il programma stesso, i compilatori CLR possono inoltre generare informazioni di debug molto descrittive che viene scritto in un file di DataBase di programma (PDB). Fino a quando il compilatore di linguaggio di proprietaria produce informazioni di debug nello stesso formato i compilatori CLR, SP di CLR è in grado di identificare che del linguaggio denominato oggetti dati. Dopo aver individuato un oggetto dati denominato, l'analizzatore di Espressioni utilizza un oggetto di gestore di associazione per associare l'oggetto dati (o associare) nell'area di memoria che contiene il valore di tale oggetto. La Germania possa quindi ottenere o impostare un nuovo valore per l'oggetto dati.  
  
 Un compilatore proprietario può fornire informazioni di debug mediante la chiamata di CLR il `ISymbolWriter` interfaccia (definito in .NET Framework nello spazio dei nomi `System.Diagnostics.SymbolStore`). Compilazione in MSIL e la scrittura delle informazioni di debug tramite queste interfacce, è possibile utilizzare un compilatore proprietario Germania CLR e provider di servizi. Questa operazione semplifica notevolmente l'integrazione di un linguaggio proprietario nell'IDE di Visual Studio.  
  
 Quando la Germania CLR chiama l'analizzatore di Espressioni proprietarie per valutare un'espressione, la Germania fornisce l'analizzatore di Espressioni con interfacce a un Service Pack e un oggetto di gestore di associazione. Di conseguenza, la scrittura di un mezzo di motore di debug basato su CLR è necessario solo implementare le interfacce dell'analizzatore di espressioni espressione appropriata. Common Language Runtime si occupa dell'associazione e il simbolo di gestione per l'utente.  
  
## <a name="see-also"></a>Vedere anche  
 [Scrittura di un analizzatore di espressioni CLR](../../extensibility/debugger/writing-a-common-language-runtime-expression-evaluator.md)