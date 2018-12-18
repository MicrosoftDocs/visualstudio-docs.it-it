---
title: Sessione di Debug Manager | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- session debug manager, unifying session views
- session debug manager, broadcasting
- debugging [Debugging SDK], session debug manager
- session debug manager
- session debug manager, debug engine multiplexing
- session debug manager, delegating
ms.assetid: fbb1928d-dddc-43d1-98a4-e23b0ecbae09
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: 7d7acd147fd8d2b73b2172900baf7e1f49808e9a
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="session-debug-manager"></a>Gestione di Debug delle sessioni
Gestore di sessione di debug (SDM) gestisce un numero qualsiasi di motori di debug (DE) il debug di un numero qualsiasi di applicazioni in più processi su qualsiasi numero di macchine. Oltre a essere un motore di debug multiplexer, di SDM fornisce una visualizzazione unificata della sessione di debug all'IDE.  
  
## <a name="session-debug-manager-operation"></a>Operazione sessione di Debug Manager  
 Gestore di sessione di debug (SDM) gestisce la Germania. Potrebbero essere presenti più di un motore di debug in esecuzione in un computer nello stesso momento. Per la crittografia DEs a multiplex avanzato, la SDM esegue il wrapping di un numero di interfacce dalla crittografia DEs e li espone all'IDE come una singola interfaccia.  
  
 Per migliorare le prestazioni, non sono in multiplexing alcune interfacce. Al contrario, vengono utilizzati direttamente dalla Germania e le chiamate a queste interfacce non passano attraverso il SDM. Ad esempio, le interfacce utilizzate con memoria, il codice e i contesti di documento non sono multiplex, perché fanno riferimento a un documento in un programma specifico di debug da un DE specifico, la memoria o l'istruzione specifica. Nessun altro Germania deve essere coinvolti in tale livello di comunicazione.  
  
 Ciò non vale per tutti i contesti. Le chiamate all'interfaccia del contesto di valutazione espressione passano attraverso il SDM. Durante la valutazione dell'espressione, esegue il wrapping di SDM il [IDebugExpression2](../../extensibility/debugger/reference/idebugexpression2.md) interfaccia che fornisce all'IDE perché quando tale espressione viene valutata, potrebbero comportare più DEs che sta eseguendo il debug di programmi nello stesso processo che potrebbero essere in esecuzione sullo stesso thread.  
  
 Il SDM funge in genere da un meccanismo di delega, ma può fungere da un meccanismo di trasmissione. Ad esempio, durante la valutazione dell'espressione, il SDM agisce come un meccanismo di trasmissione per notificare tutti DEs che è possibile eseguire il codice in un thread specificato. Analogamente, quando il SDM riceve un evento di arresto, trasmette tutti i programmi che possono più in esecuzione. Quando viene chiamato un passaggio di SDM trasmette a tutti i programmi che è possibile continuare l'esecuzione. I punti di interruzione vengono inoltre trasmessi a ogni DE.  
  
 Il SDM non rileva il programma corrente, un thread o un frame dello stack. Il processo, un programma e un thread informazioni vengono inviate a SDM in combinazione con eventi di debug specifici.  
  
## <a name="see-also"></a>Vedere anche  
 [Motore di debug](../../extensibility/debugger/debug-engine.md)   
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)   
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)