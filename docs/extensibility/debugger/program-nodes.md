---
title: Programma nodi | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- program nodes, debugging context
- debugging [Debugging SDK], program nodes
- program nodes, adding
- program nodes, superceding
ms.assetid: 1c5a5c13-c14d-42c3-af11-4c63f1032c8d
caps.latest.revision: "12"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 90ec92ad46a850c26e700e9feafa60d291f608ba
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="program-nodes"></a>Nodi di programma
In termini di architettura del debugger, un **nodo programma**:  
  
-   È una descrizione di un programma semplice.  
  
-   Consente di identificare se stesso e il processo è in esecuzione in e deve essere collegata a scollegati da e descrivere il motore di debug (DE) che è stato creato, se presente.  
  
-   È rappresentato da un [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) interfaccia, in genere creato da una porta o Germania. I nodi di programma vengono aggiunti a una porta chiamando [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md). Quando viene aggiunto un nodo di programma a una porta, viene aggiunto al processo che contiene il programma che rappresenta questo nodo del programma.  
  
 Corrisponde a un giorno dopo che viene avviata una sessione di debug, a seconda dell'implementazione del pacchetto di debug, i nodi di programma vengono utilizzati per creare programmi corrispondenti. Quando un processo viene eseguita una query per i programmi, vengono enumerati i programmi, uno per ogni nodo del programma.  
  
 Prima di un programma è collegato, l'IDE deve solo una semplice descrizione del programma. Queste informazioni possono essere ottenute dal nodo del programma. Una volta il programma è collegato, l'IDE deve visualizzare informazioni più dettagliate, ad esempio un elenco di tutti i thread in esecuzione del programma. Queste informazioni vengono ottenute dal programma stesso.  
  
## <a name="see-also"></a>Vedere anche  
 [Programmi](../../extensibility/debugger/programs.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [AddProgramNode](../../extensibility/debugger/reference/idebugportnotify2-addprogramnode.md)