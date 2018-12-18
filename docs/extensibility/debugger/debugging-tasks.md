---
title: "Attività di debug | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: debugging [Debugging SDK], tasks
ms.assetid: 5d60e9e8-305e-4a48-829f-b9440fc8af7b
caps.latest.revision: "16"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.workload: vssdk
ms.openlocfilehash: d1a6ffff4d3ac0410ca3de7e2cd595119763e88b
ms.sourcegitcommit: 32f1a690fc445f9586d53698fc82c7debd784eeb
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 12/22/2017
---
# <a name="debugging-tasks"></a>Attività di debug
Per eseguire il debug di un programma, deve essere avviato e deve essere associato un motore di debug (DE), altrimenti la Germania deve essere collegato a un programma avviato in precedenza. Una volta collegato, la Germania necessario generare determinati eventi di avvio. In risposta, il pacchetto di debug tenta di associare i punti di interruzione impostati nell'IDE. Quando il programma raggiunge un punto di interruzione associato, interrompe e attende l'input dell'utente.  
  
## <a name="in-this-section"></a>In questa sezione  
 [Problemi di sicurezza](../../extensibility/debugger/security-issues.md)  
 Vengono illustrati i passaggi di sicurezza necessari per eseguire il debug di un programma.  
  
 [Avvio di un programma](../../extensibility/debugger/launching-a-program.md)  
 Vengono fornite istruzioni dettagliate su come specificare un DE, che chiama il sistema operativo per avviare il programma.  
  
 [Collegamento diretto a un programma](../../extensibility/debugger/attaching-directly-to-a-program.md)  
 Descrive il processo per eseguire il debug di un programma in un processo già in esecuzione.  
  
 [Invio degli eventi di avvio dopo un avvio](../../extensibility/debugger/sending-startup-events-after-a-launch.md)  
 Elenca gli eventi che si verificano dopo che la Germania è collegato al programma, fino a quando il programma è in corrispondenza del punto di ingresso principale ed è pronto per il debug.  
  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)  
 Viene illustrato come la Germania invia in genere un evento punto di ingresso, un evento di completamento carico o un evento di arresto, a seconda delle circostanze.  
  
 [Associazione di punti di interruzione](../../extensibility/debugger/binding-breakpoints.md)  
 Viene descritto, se l'utente imposta un punto di interruzione, l'IDE in cui viene creata la richiesta e richiede la sessione di debug per creare il punto di interruzione.  
  
 [Valutazione di espressioni](../../extensibility/debugger/evaluating-expressions.md)  
 Viene illustrato come creare espressioni e cosa accade quando viene valutata un'espressione.  
  
 [Visualizzazione di tipi e dati](../../extensibility/debugger/visualizing-and-viewing-data.md)  
 Viene illustrato come i visualizzatori di tipo e i visualizzatori personalizzati sono supportati dall'analizzatore di espressioni (Java EE).  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
 [Componenti del debugger](../../extensibility/debugger/debugger-components.md)  
 Viene fornita una panoramica dei componenti di debug Visual Studio, che includono la Germania, EE e il gestore di simboli (SH).  
  
 [Contesti del debugger](../../extensibility/debugger/debugger-contexts.md)  
 Viene illustrato come la Germania funziona contemporaneamente all'interno di codice, documentazione e contesti di valutazione di espressione. Viene descritto, per ognuno dei tre contesti, il percorso, posizione o valutazione rilevante a esso.  
  
## <a name="see-also"></a>Vedere anche  
 [Introduzione](../../extensibility/debugger/getting-started-with-debugger-extensibility.md)