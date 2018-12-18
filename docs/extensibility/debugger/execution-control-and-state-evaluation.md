---
title: Controllo di esecuzione e la valutazione dello stato | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], execution control
- expression evaluation, control of execution
ms.assetid: 55adde38-1622-4b51-83cb-ce1b04c1ca7a
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: f5ebc9d78f50454a0b0576c4d339102b08cb3e26
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="execution-control-and-state-evaluation"></a>Controllo di esecuzione e la valutazione dello stato
Debug di un'applicazione richiede l'implementazione di tali funzionalità di controllo di esecuzione come l'esecuzione di funzioni, punti di arresto e continuare l'esecuzione. Debug di base di Visual Studio il controllo dell'esecuzione sugli eventi inviati tra i componenti del debugger.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Controllo del programma](../../extensibility/debugger/program-control.md)  
 Elenca le routine seguenti che si verificano a livello di programma: impostazione dell'istruzione successiva, l'esecuzione, l'esecuzione di istruzioni, continuare, la sospensione e ripresa.  
  
 [Metodi correlati al punto di interruzione](../../extensibility/debugger/breakpoint-related-methods.md)  
 Definisce il limite e in attesa di tipi di punti di interruzione che supporta Visual Studio.  
  
 [Valutazione dello stack di chiamate](../../extensibility/debugger/call-stack-evaluation.md)  
 Viene illustrata l'implementazione dei metodi che consentono la visualizzazione degli stack frame dello stack di chiamate durante la modalità di interruzione.  
  
 [Valutazione dell'espressione](../../extensibility/debugger/expression-evaluation-visual-studio-debugging-sdk.md)  
 Viene descritto il motore di debug (DE), valutazione (Java EE) e sessione di debug di gestione delle espressioni sono coinvolte l'analisi e valutazione di un'espressione immessi in una delle finestre dell'IDE.  
  
 [Eventi di controllo](../../extensibility/debugger/control-events.md)  
 Illustra l'interfaccia utilizzata per inviare eventi durante l'esecuzione controllata del programma.