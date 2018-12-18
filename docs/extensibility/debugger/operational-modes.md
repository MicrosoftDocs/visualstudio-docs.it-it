---
title: Modalità operative | Documenti Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, modes
ms.assetid: f69972d0-809d-40df-9da3-04738791391c
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 72ae5a36f9f0547635872f5c8ebe30f2f3c53d5a
ms.sourcegitcommit: 6a9d5bd75e50947659fd6c837111a6a547884e2a
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 04/16/2018
---
# <a name="operational-modes"></a>Modalità operative
Sono disponibili tre modalità in cui può operare nell'IDE, come indicato di seguito:  
  
-   [Modalità di progettazione](#vsconoperationalmodesanchor1)  
  
-   [Modalità di esecuzione](#vsconoperationalmodesanchor2)  
  
-   [Modalità di interruzione](#vsconoperationalmodesanchor3)  
  
 La modalità di transizione tra queste modalità del motore di debug personalizzato (DE) è una decisione di implementazione che è necessario avere familiarità con i meccanismi di transizione. La Germania può o non può implementare direttamente queste modalità. Queste modalità sono realmente pacchetto le modalità di debug che passano in base a un'azione utente o gli eventi dalla Germania. Ad esempio, il passaggio dalla modalità di esecuzione alla modalità di interruzione viene attivato da un evento di arresto dalla Germania. Il passaggio dall'interruzione per avviare la modalità o in modalità di passaggio è ha generato dall'utente eseguendo operazioni come passaggio o Execute. Per ulteriori informazioni sulle transizioni DE, vedere [di controllare l'esecuzione](../../extensibility/debugger/control-of-execution.md).  
  
##  <a name="vsconoperationalmodesanchor1"></a> Modalità di progettazione  
 Modalità di progettazione è lo stato nonrunning di debug di Visual Studio, durante i quali è possibile impostare le funzionalità dell'applicazione di debug.  
  
 Solo il debug alcune funzionalità vengono utilizzate durante la modalità progettazione. Uno sviluppatore può scegliere di impostare punti di interruzione o creare espressioni di controllo. La Germania è mai stato caricato o chiamato mentre l'ambiente IDE è in modalità progettazione. L'interazione con il rilevamento ha luogo durante solo le modalità di esecuzione e di interruzione.  
  
##  <a name="vsconoperationalmodesanchor2"></a> Modalità di esecuzione  
 Modalità di esecuzione si verifica quando un programma in esecuzione in una sessione di debug nell'IDE. L'applicazione viene eseguita fino al termine, fino a quando non viene raggiunto un punto di interruzione o fino a quando non viene generata un'eccezione. Quando l'applicazione viene eseguita al completamento, le transizioni DE in modalità progettazione. Quando viene raggiunto un punto di interruzione o viene generata un'eccezione, la Germania assume per modalità di interruzione.  
  
##  <a name="vsconoperationalmodesanchor3"></a> Modalità di interruzione  
 Modalità di interruzione si verifica quando viene sospesa l'esecuzione del programma di debug. Modalità di interruzione offre allo sviluppatore di uno snapshot dell'applicazione al momento dell'interruzione e consente agli sviluppatori di analizzare lo stato dell'applicazione e modificare la modalità con cui l'applicazione verrà eseguita. Lo sviluppatore può visualizzare e modificare il codice, esaminare o modificare i dati, riavviare l'applicazione, fine esecuzione o continuare l'esecuzione dal punto stesso.  
  
 Quando la Germania invia un evento di arresto sincrono è attivata la modalità di interruzione. Eventi di arresto sincrono, denominati anche gli eventi di arresto, inviare una notifica di gestore di sessione di debug (SDM) e l'IDE che l'applicazione in fase di debug ha interrotto l'esecuzione di codice. Il [IDebugBreakpointEvent2](../../extensibility/debugger/reference/idebugbreakpointevent2.md) e [IDebugExceptionEvent2](../../extensibility/debugger/reference/idebugexceptionevent2.md) interfacce sono esempi di eventi di arresto.  
  
 Gli eventi di arresto derivati da una chiamata a uno dei metodi seguenti, a cui passare dalla modalità di interruzione per l'esecuzione o la modalità di passaggio nel debugger:  
  
-   [Eseguire](../../extensibility/debugger/reference/idebugprocess3-execute.md)  
  
-   [Step](../../extensibility/debugger/reference/idebugprocess3-step.md)  
  
-   [Continue](../../extensibility/debugger/reference/idebugprocess3-continue.md)  
  
###  <a name="vsconoperationalmodesanchor4"></a> Modalità di passaggio  
 Modalità di passaggio si verifica quando il programma i passaggi alla riga successiva del codice, nel, in o da una funzione. Un passaggio viene eseguito chiamando il metodo [passaggio](../../extensibility/debugger/reference/idebugprocess3-step.md). Questo metodo richiede `DWORD`s che specificano il [STEPUNIT](../../extensibility/debugger/reference/stepunit.md) e [STEPKIND](../../extensibility/debugger/reference/stepkind.md) enumerazioni come parametri di input.  
  
 Quando il programma completato i passaggi alla riga successiva del codice o in una funzione o viene eseguito fino al cursore o a un punto di interruzione impostato, la Germania passa automaticamente alla modalità di interruzione.  
  
## <a name="see-also"></a>Vedere anche  
 [Controllo dell'esecuzione](../../extensibility/debugger/control-of-execution.md)